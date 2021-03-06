---
title: 'Comment : convertir une chaîne en tableau de caractères en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Comment : convertir une chaîne en tableau de caractères en Visual Basic
Il est parfois utile de disposer de données sur les caractères de votre chaîne ainsi que les positions de ces caractères dans la chaîne, telles que lorsque vous analysez une chaîne. Cet exemple montre comment vous pouvez obtenir un tableau de caractères dans une chaîne en appelant la chaîne <xref:System.String.ToCharArray%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment fractionner une chaîne en un `Char` tableau et comment fractionner une chaîne en un `String` tableau de caractères Unicode texte. La raison de cette distinction est que les caractères de texte Unicode peuvent être composés de deux ou plusieurs `Char` caractères (par exemple une paire de substitution ou une combinaison séquence de caractères). Pour plus d’informations, consultez <xref:System.Globalization.TextElementEnumerator> et « La norme Unicode » sur http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Exemple  
 Il est plus difficile de fractionner une chaîne en ses caractères de texte Unicode, mais cette opération est nécessaire si vous avez besoin d’informations sur la représentation visuelle d’une chaîne. Cet exemple utilise la <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> méthode pour obtenir des informations sur les caractères de texte Unicode qui composent une chaîne.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Guide pratique : accéder aux caractères dans les chaînes](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Conversion entre chaînes et d’autres types de données en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)
