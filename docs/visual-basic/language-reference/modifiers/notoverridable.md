---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Spécifie qu’une propriété ou procédure ne peut pas être substituée dans une classe dérivée.  
  
## <a name="remarks"></a>Notes  
 Le `NotOverridable` modificateur empêche une propriété ou méthode d’être substituée dans une classe dérivée.  Le [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modificateur permet à une propriété ou une méthode dans une classe de substitution dans une classe dérivée. Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si le `Overridable` ou `NotOverridable` modificateur n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou méthode se substitue à une méthode ou propriété de classe de base. Si la propriété ou méthode substitue une méthode ou propriété de classe de base, le paramètre par défaut est `Overridable`; sinon, elle est `NotOverridable`.  
  
 Un élément qui ne peut pas être substitué est parfois appelé un *sealed* élément.  
  
 Vous pouvez utiliser `NotOverridable` uniquement dans une instruction de déclaration de propriété ou de procédure. Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui substitue une autre propriété ou procédure, c'est-à-dire, uniquement en association avec `Overrides`.  
  
## <a name="combined-modifiers"></a>Modificateurs combinés  
 Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour un `Private` (méthode).  
  
 Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride`, `Overridable`, ou `Shared` dans la même déclaration.  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modificateurs](../../../visual-basic/language-reference/modifiers/index.md)  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)  
 [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
