---
title: 'Comment : détecter la modification du texte figurant dans un TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Comment : détecter la modification du texte figurant dans un TextBox
Cet exemple montre une manière d’utiliser la <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte dans un <xref:System.Windows.Controls.TextBox> contrôle a changé.  
  
 Dans la classe code-behind pour la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle que vous souhaitez analyser pour les modifications, insérez une méthode à appeler lorsque le <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche des événements.  Cette méthode doit avoir une signature qui correspond à celle attendue par le <xref:System.Windows.Controls.TextChangedEventHandler> déléguer.  
  
 Le Gestionnaire d’événements est appelé chaque fois que le contenu de la <xref:System.Windows.Controls.TextBox> contrôle sont modifiés par un utilisateur ou par programme.  
  
 **Remarque :** cet événement déclenche lorsque la <xref:System.Windows.Controls.TextBox> contrôle est créée et remplie initialement avec le texte.  
  
## <a name="example"></a>Exemple  
 Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôler, spécifiez la <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribut avec une valeur qui correspond au nom méthode du Gestionnaire d’événements.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Exemple  
 Dans la classe code-behind pour la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle que vous souhaitez analyser pour les modifications, insérez une méthode à appeler lorsque le <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche des événements.  Cette méthode doit avoir une signature qui correspond à celle attendue par le <xref:System.Windows.Controls.TextChangedEventHandler> déléguer.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Le Gestionnaire d’événements est appelé chaque fois que le contenu de la <xref:System.Windows.Controls.TextBox> contrôle sont modifiés par un utilisateur ou par programme.  
  
 **Remarque :** cet événement déclenche lorsque la <xref:System.Windows.Controls.TextBox> contrôle est créée et remplie initialement avec le texte.  
  
 Commentaires  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [Vue d’ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Vue d’ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
