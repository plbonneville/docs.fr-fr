---
title: '##Const (directive)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="const-directive"></a>#Const, directive
Définit des constantes conditionnelles du compilateur pour Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Composants  
 `constname`  
 Obligatoire. Nom de la constante définie.  
  
 `expression`  
 Obligatoire. Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques à l’exception `Is`.  
  
## <a name="remarks"></a>Notes  
 Constantes de compilation conditionnelle sont toujours privées pour le fichier dans lequel elles apparaissent. Vous ne pouvez pas créer de constantes de compilation publiques à l’aide de la `#Const` directive ; vous pouvez les créer que dans l’interface utilisateur ou avec la `/define` option du compilateur.  
  
 Vous pouvez utiliser uniquement des constantes de compilation conditionnelle et des littéraux dans `expression`. À l’aide d’une constante standard définie avec `Const` provoque une erreur. À l’inverse, vous pouvez utiliser des constantes définies avec le `#Const` mot clé uniquement pour la compilation conditionnelle. Les constantes peuvent également être non, auquel cas ils ont une valeur de `Nothing`.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la directive `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
