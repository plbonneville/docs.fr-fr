---
title: Portée des espaces de noms par défaut en Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: a0c07c1b6ca4fea836bd37e4a311655fcb1d7878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Portée des espaces de noms par défaut en Visual Basic
Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes. Si vous avez du code XML qui est dans un espace de noms par défaut, vous devez déclarer une variable <xref:System.Xml.Linq.XNamespace> et la combiner avec le nom local afin de créer un nom complet utilisable dans la requête.  
  
 L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.  
  
 Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.  
  
 Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.  
  
### <a name="code"></a>Code  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère le résultat suivant :  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.  
  
 Contrairement à l’exemple de code incorrect ci-dessus, la correct lorsque vous utilisez Visual Basic consiste à déclarer et initialiser un espace de noms global par défaut. Cela place toutes les propriétés XML dans l'espace de noms par défaut. Aucune autre modification n'est nécessaire pour que l'exemple fonctionne correctement.  
  
### <a name="code"></a>Code  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère le résultat suivant :  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
