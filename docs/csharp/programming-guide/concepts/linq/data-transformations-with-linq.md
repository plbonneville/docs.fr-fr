---
title: "Transformations de données avec LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0633e348c762879caa4e3f72a3662722b3894e4c
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="data-transformations-with-linq-c"></a>Transformations de données avec LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ne gère pas uniquement la récupération des données. C’est également un outil puissant pour la transformation de données. En utilisant une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous pouvez utiliser une séquence source en entrée et la modifier de nombreuses façons pour créer une séquence de sortie. Vous pouvez modifier la séquence elle-même sans modifier les éléments eux-mêmes en les triant et en les regroupant. Mais la fonctionnalité la plus puissante des requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] est peut-être la possibilité de créer des types. Cette opération est effectuée dans la clause [select](../../../../csharp/language-reference/keywords/select-clause.md). Par exemple, il est possible de réaliser les tâches suivantes :  
  
-   Fusionner plusieurs séquences d’entrée en une séquence de sortie unique ayant un nouveau type.  
  
-   Créer des séquences de sortie dont les éléments se composent d’une seule propriété ou de plusieurs propriétés de chaque élément de la séquence source.  
  
-   Créer des séquences de sortie dont les éléments se composent des résultats des opérations effectuées sur les données sources.  
  
-   Créer des séquences de sortie dans un format différent. Par exemple, vous pouvez transformer des données de lignes ou de fichiers texte SQL en données XML.  
  
 Voici une liste non exhaustive d’exemples. Bien sûr, ces transformations peuvent être combinées de plusieurs façons dans la même requête. Par ailleurs, la séquence de sortie d’une requête peut être utilisée comme séquence d’entrée pour une nouvelle requête.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Combinaison de plusieurs entrées en une séquence de sortie  
 Vous pouvez utiliser une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour créer une séquence de sortie qui contient des éléments de plusieurs séquences d’entrée. L’exemple suivant montre comment combiner deux structures de données en mémoire, mais les mêmes principes peuvent être appliqués pour combiner des données provenant de sources XML, SQL ou DataSet. Prenons l’exemple des deux types de classe suivants :  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 L’exemple suivant présente la requête :  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Pour plus d’informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md) et [select, clause](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Sélection d’un sous-ensemble de chaque élément source  
 Pour sélectionner un sous-ensemble de chaque élément de la séquence source, deux méthodes principales s’offrent à vous :  
  
1.  Pour sélectionner un seul membre de l’élément source, utilisez l’opérateur point. Dans l’exemple suivant, supposons qu’un objet `Customer` contienne plusieurs propriétés publiques comprenant une chaîne nommée `City`. Une fois exécutée, cette requête génère une séquence de sortie de chaînes.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Pour créer des éléments qui contiennent plusieurs propriétés de l’élément source, vous pouvez utiliser un initialiseur d’objet avec un objet nommé ou un type anonyme. L’exemple suivant montre comment utiliser un type anonyme pour encapsuler deux propriétés de chaque élément `Customer` :  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Pour plus d’informations, consultez [Initialiseurs d’objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) et [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformation d’objets en mémoire en XML  
 Les requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] permettent de transformer facilement des données entre des structures de données en mémoire, des bases de données SQL, des groupes de données [!INCLUDE[vstecado](~/includes/vstecado-md.md)] et des flux de données ou des documents XML. L’exemple suivant transforme des objets d’une structure de données en mémoire en éléments XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 Le code génère la sortie XML suivante :  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Pour plus d’informations, consultez [Création d’arborescences XML en C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Exécution d’opérations sur les éléments sources  
 Une séquence de sortie ne contient pas toujours des éléments ou des propriétés d’élément de la séquence source. La sortie peut être plutôt une séquence de valeurs calculée en utilisant les éléments sources comme arguments d’entrée. La requête simple suivante, quand elle est exécutée, génère en sortie une séquence de chaînes dont les valeurs représentent un calcul basé sur la séquence source d’éléments de type `double`.  
  
> [!NOTE]
>  Les méthodes d’appel dans les expressions de requête ne sont pas prises en charge si la requête est traduite dans un autre domaine. Par exemple, vous ne pouvez pas appeler une méthode C# ordinaire dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], car SQL Server n’a pas de contexte pour cette méthode. Toutefois, vous pouvez mapper des procédures stockées à des méthodes et appeler celles-ci. Pour plus d’informations, consultez [Procédures stockées](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language-Integrated Query) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [select, clause](../../../../csharp/language-reference/keywords/select-clause.md)
