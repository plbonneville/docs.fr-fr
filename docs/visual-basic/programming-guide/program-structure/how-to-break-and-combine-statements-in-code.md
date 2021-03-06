---
title: 'Procédure : diviser et combiner des instructions dans le code (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Procédure : diviser et combiner des instructions dans le code (Visual Basic)
Lorsque vous écrivez votre code, vous pouvez parfois créer des longues instructions qui imposent un défilement horizontal dans l’éditeur de Code. Bien que cela n’affecte pas la façon votre code s’exécute, elle rend difficile pour vous ou toute autre personne à lire le code tel qu’il apparaît sur le moniteur. Dans ce cas, vous devez envisager de diviser cette instruction longue en plusieurs lignes.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Arrêt d’une instruction unique en plusieurs lignes  
  
-   Utiliser le caractère de continuation de ligne, qui est un trait de soulignement (`_`), au point auquel vous souhaitez que la saut de ligne. Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne (retour chariot).  
  
    > [!NOTE]
    >  Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic implicitement continue l’instruction sur la ligne de code suivante. Pour obtenir la liste d’éléments de syntaxe pour laquelle vous pouvez omettre le caractère de continuation de ligne, consultez « Continuation de ligne implicite » dans [instructions](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     Dans l’exemple suivant, l’instruction est divisée en quatre lignes avec des caractères de continuation terminant toutes les mais la dernière ligne.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     À l’aide de cette séquence rend votre code plus facile à lire, à la fois en ligne et lorsque imprimé.  
  
     Le caractère de continuation de ligne doit être le dernier caractère d’une ligne. Vous ne peut pas faire suivre avec tout autre élément sur la même ligne.  
  
     Il existe certaines limitations à l’où vous pouvez utiliser le caractère de continuation de ligne ; par exemple, vous ne pouvez pas l’utiliser au milieu d’un nom d’argument. Vous pouvez interrompre une liste d’arguments avec le caractère de continuation de ligne, mais les noms respectifs des arguments doivent rester intactes.  
  
     Vous ne peut pas continuer un commentaire à l’aide d’un caractère de continuation de ligne. Le compilateur n’Examinez les caractères dans un commentaire pour une signification particulière. Pour un commentaire de plusieurs lignes, répétez le symbole de commentaire (`'`) sur chaque ligne.  
  
 Bien que la méthode recommandée consiste à placer chaque instruction sur une ligne distincte, Visual Basic vous permet également de placer plusieurs instructions sur la même ligne.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Pour placer plusieurs instructions sur la même ligne  
  
-   Séparez les instructions par un signe deux-points (`:`), comme dans l’exemple suivant.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
