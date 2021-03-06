---
title: 'Comment : choisir entre StackPanel et DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: c9bfb8d29051a9cfa61d3fcb93b8bb9a68d14e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Comment : choisir entre StackPanel et DockPanel
Cet exemple montre comment choisir entre l’utilisation d’un <xref:System.Windows.Controls.StackPanel> ou un <xref:System.Windows.Controls.DockPanel> pour empiler du contenu dans un <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemple  
 Bien que vous pouvez utiliser <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> pour empiler des éléments enfants, les deux contrôles ne produisent pas toujours les mêmes résultats. Par exemple, l’ordre que vous placez des éléments enfants peut affecter la taille des éléments enfants dans un <xref:System.Windows.Controls.DockPanel> , mais pas dans un <xref:System.Windows.Controls.StackPanel>. Cette différence de comportement se produit parce que <xref:System.Windows.Controls.StackPanel> mesure dans le sens de l’empilement jusqu'à <xref:System.Double>.<xref:System.Double.PositiveInfinity>; Toutefois, <xref:System.Windows.Controls.DockPanel> mesure uniquement la taille disponible.  
  
 L’exemple suivant illustre cette différence essentielle entre <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)
