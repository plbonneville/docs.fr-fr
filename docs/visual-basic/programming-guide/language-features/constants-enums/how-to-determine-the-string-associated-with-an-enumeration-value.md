---
title: "Comment : déterminer la chaîne associée à une valeur d'énumération (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c14ea61feba7d7d85f9a4fc377aefdd8fa240c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Comment : déterminer la chaîne associée à une valeur d'énumération (Visual Basic)
Le <xref:System.Enum.GetValues%2A> et <xref:System.Enum.GetNames%2A> méthodes permettent de déterminer les chaînes et les valeurs associées aux membres de l’énumération.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Pour déterminer la chaîne associée à une énumération  
  
-   Utilisez la <xref:System.Enum.GetNames%2A> méthode pour récupérer les chaînes associées aux membres de l’énumération. Cet exemple déclare une énumération, `flavorEnum`, puis utilise la <xref:System.Enum.GetNames%2A> méthode pour afficher les chaînes associées à chaque membre.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Enum (instruction)](../../../../visual-basic/language-reference/statements/enum-statement.md)
