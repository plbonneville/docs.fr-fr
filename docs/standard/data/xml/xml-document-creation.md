---
title: "Création d'un document XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea67841e44d8d88d2effec92eb1668142c1510f2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-creation"></a>Création d'un document XML
Il existe deux façons de créer un document XML. L'une consiste à créer un objet **XmlDocument**, sans paramètre. L'autre consiste à créer un objet **XmlDocument** et à le passer à XmlNameTable sous la forme d'un paramètre. L'exemple suivant indique comment créer un nouveau **XmlDocument** vide dépourvu de paramètre.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Une fois le document créé, vous pouvez y charger des données à partir d'une chaîne, d'un flux, d'une URL, d'un lecteur de texte ou d'une classe dérivée **XmlReader** à l'aide de la méthode **Load**. Il existe également une autre méthode de chargement, appelée **LoadXML**, qui lit le contenu XML d'une chaîne. Pour plus d'informations sur les diverses méthodes **Load**, consultez [Lecture d'un document XML vers le DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Il existe une classe appelée **XmlNameTable**. Cette classe est une table d'objets chaîne atomisés. Cette table constitue un moyen efficace pour que l'analyseur XML utilise le même objet chaîne pour tous les noms d'éléments et d'attributs répétés dans un document XML. Un objet **XmlNameTable** est créé automatiquement lors de la création d'un document, comme le montre l'exemple ci-avant, et est chargé avec des noms d'attributs et d'éléments lors du chargement du document. Si vous disposez déjà d'un document possédant une table de noms, et que ces noms pourraient être employés utilement dans un autre document, vous pouvez créer un nouveau document à l'aide de la méthode **Load** qui prend **XmlNameTable** comme paramètre. Lorsque le document est créé avec cette méthode, il utilise le **XmlNameTable** existant avec tous les attributs et éléments déjà chargés en son sein à partir de l'autre document. Celui-ci peut être employé pour comparer efficacement des noms d'éléments et d'attributs. Pour plus d'informations sur **XmlNameTable**, consultez [Comparaison d'objets à l'aide de XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Pour référence, consultez <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Voir aussi  
 [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
