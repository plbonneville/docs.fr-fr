---
title: Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel elle est déclarée. Par conséquent, une classe ne peut pas déclencher d’événements à partir de toute autre classe, même si celle-ci à partir de laquelle elle est dérivée.  
  
 **ID d’erreur :** BC30029  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Déplacer le `Event` instruction ou la `RaiseEvent` instruction afin qu’ils soient dans la même classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent (instruction)](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
