---
title: "Comment : définir des info-bulles pour les contrôles d'un Windows Form au moment du design"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 4e4623c1c0fe7d082e4d1a1f404ddaa94e79fc2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Comment : définir des info-bulles pour les contrôles d'un Windows Form au moment du design
Vous pouvez définir un <xref:System.Windows.Forms.ToolTip> chaîne dans le code ou dans le Concepteur Windows Forms. Pour plus d’informations sur la <xref:System.Windows.Forms.ToolTip> composant, consultez [vue d’ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Pour définir une info-bulle par programmation  
  
1.  Ajoutez le contrôle qui affiche l’info-bulle.  
  
2.  Utilisez le <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> méthode de la <xref:System.Windows.Forms.ToolTip> composant.  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Pour définir une info-bulle dans le Concepteur  
  
1.  Ajoutez un composant <xref:System.Windows.Forms.ToolTip> au formulaire.  
  
2.  Sélectionnez le contrôle qui affiche l’info-bulle, ou ajoutez-le au formulaire.  
  
3.  Dans le **propriétés** , configurez la **info-bulle sur ToolTip1** valeur à une chaîne de texte appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Guide pratique pour modifier la durée avant affichage du composant ToolTip Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [ToolTip, composant](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
