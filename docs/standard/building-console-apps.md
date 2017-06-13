---
title: "G&#233;n&#233;ration d&#39;applications de console dans le .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, générer des applications console"
  - "développement d'applications (.NET Framework), console"
  - "applications console"
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# G&#233;n&#233;ration d&#39;applications de console dans le .NET Framework
Les applications dans le .NET Framework peuvent utiliser la classe <xref:System.Console?displayProperty=fullName> pour lire et écrire des caractères en provenance ou à destination de la console.  Les données provenant de la console sont lues dans le flux d'entrée standard, les données à destination de la console sont écrites dans le flux de sortie standard et les données d'erreur à destination de la console sont écrites dans le flux de sortie standard des erreurs.  Ces flux de données, associés automatiquement à la console au démarrage de l'application, sont présentés respectivement en tant que propriétés <xref:System.Console.In%2A>, <xref:System.Console.Out%2A> et <xref:System.Console.Error%2A>.  
  
 La valeur de la propriété <xref:System.Console.In%2A?displayProperty=fullName> est un objet <xref:System.IO.TextReader?displayProperty=fullName>, alors que les valeurs des propriétés <xref:System.Console.Out%2A?displayProperty=fullName> et <xref:System.Console.Error%2A?displayProperty=fullName> sont des objets <xref:System.IO.TextWriter?displayProperty=fullName>.  Vous pouvez associer ces propriétés à des flux qui ne représentent pas la console, ce qui vous permet de désigner un autre emplacement pour les entrées ou les sorties.  Par exemple, vous pouvez rediriger la sortie vers un fichier en définissant la propriété <xref:System.Console.Out%2A?displayProperty=fullName> sur un objet <xref:System.IO.StreamWriter?displayProperty=fullName>, qui encapsule un <xref:System.IO.FileStream?displayProperty=fullName> au moyen de la méthode <xref:System.Console.SetOut%2A?displayProperty=fullName>.  Il n'est pas nécessaire que les propriétés <xref:System.Console.In%2A?displayProperty=fullName> et <xref:System.Console.Out%2A?displayProperty=fullName> fassent référence au même flux.  
  
> [!NOTE]
>  Pour plus d'informations sur la génération d'applications de console, notamment des exemples dans C\#, Visual Basic et C\+\+, consultez la documentation relative à la classe <xref:System.Console>.  
  
 Si la console n'existe pas, comme c'est le cas dans une application Windows, la sortie écrite dans le flux de sortie standard ne sera pas visible, puisqu'il n'existe pas de console sur laquelle écrire les informations.  L'écriture d'informations sur une console inaccessible ne déclenche pas d'exception.  
  
 Par ailleurs, pour activer la console pour la lecture et l'écriture dans une application Windows développée à l'aide de Visual Studio, ouvrez la boîte de dialogue **Propriétés** du projet, cliquez sur l'onglet **Application** et définissez le **Type d'application** sur **Application console.**  
  
 Les applications console ne disposent pas de pompe de messages démarrant par défaut.  Par conséquent, les appels de console aux minuteries Microsoft Win32 peuvent échouer.  
  
 La classe **System.Console** possède des méthodes qui peuvent lire des caractères ou des lignes complètes à partir de la console.  D'autres méthodes convertissent des données et mettent en forme des chaînes, puis écrivent les chaînes mises en forme sur la console.  Pour plus d'informations sur la mise en forme des chaînes, consultez [Mise en forme des types](../../docs/standard/base-types/formatting-types.md).  
  
## Voir aussi  
 <xref:System.Console?displayProperty=fullName>   
 [Mise en forme des types](../../docs/standard/base-types/formatting-types.md)