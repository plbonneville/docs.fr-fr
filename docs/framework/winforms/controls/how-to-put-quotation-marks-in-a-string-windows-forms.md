---
title: 'Comment : insérer des guillemets dans une chaîne (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 7fcc2e8692880f1e5c2b8df807cf7943a5575c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Comment : insérer des guillemets dans une chaîne (Windows Forms)
Il se peut que vous souhaitiez placer une chaîne de texte entre guillemets (« »). Par exemple :  
  
 Elle lui dit : « Cela vaut bien une récompense ! »  
  
 En guise d’alternative, vous pouvez également utiliser le <xref:Microsoft.VisualBasic.ControlChars.Quote> champ en tant que constante.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Pour placer une chaîne entre guillemets dans votre code  
  
1.  En Visual Basic, insérez deux guillemets sur une ligne comme un guillemet incorporé. En Visual c# et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insérez la séquence d’échappement \\« comme un guillemet incorporé. Par exemple, pour créer la chaîne précédente, utilisez le code suivant.  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     - ou -  
  
2.  Insérez le caractère ASCII ou Unicode d’un guillemet. En Visual Basic, utilisez le caractère ASCII (34). Dans Visual c#, utilisez le caractère Unicode (\u0022).  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  Dans cet exemple, vous ne pouvez pas utiliser \u0022, car vous ne pouvez pas utiliser un nom de caractère universel qui désigne un caractère dans le jeu de caractères de base. Sinon, vous générez l’erreur C3851. Pour plus d’informations, consultez [Erreur du compilateur C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     - ou -  
  
3.  Vous pouvez également définir une constante pour le caractère et l’utiliser lorsque cela est nécessaire.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [Vue d’ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Guide pratique pour créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
