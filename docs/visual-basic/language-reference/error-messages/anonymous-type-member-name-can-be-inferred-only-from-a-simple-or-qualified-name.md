---
title: Le nom du membre de type anonyme ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Le nom du membre de type anonyme ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument
Impossible de déduire un nom de membre de type anonyme à partir d’une expression complexe.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Pour plus d’informations sur les sources à partir de laquelle les types anonymes peuvent et ne peut pas déduire les types et les noms de membres, consultez [Comment : déduire les noms de propriétés et les Types dans les déclarations de Type anonyme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **ID d’erreur :** BC36556  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assignez l’expression à un nom de membre, comme indiqué dans le code suivant :  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Guide pratique : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
