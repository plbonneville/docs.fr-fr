---
title: 'Comment : utiliser les méthodes de défilement du contenu de ScrollViewer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: b4da666934be7dd182838d870e54e496b2646901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Comment : utiliser les méthodes de défilement du contenu de ScrollViewer
Cet exemple montre comment utiliser les méthodes de défilement de la <xref:System.Windows.Controls.ScrollViewer> élément. Ces méthodes fournissent un défilement incrémentiel du contenu, par ligne ou par page, dans un <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> nommé `sv1`, qui héberge un enfant <xref:System.Windows.Controls.TextBlock> élément. Étant donné que la <xref:System.Windows.Controls.TextBlock> est plus grand que le parent <xref:System.Windows.Controls.ScrollViewer>, barres de défilement s’affichent pour permettre le défilement. <xref:System.Windows.Controls.Button> les éléments qui représentent les différentes méthodes de défilement sont ancrés sur la gauche dans une fonction <xref:System.Windows.Controls.StackPanel>. Chaque <xref:System.Windows.Controls.Button> dans les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier appelle une méthode personnalisée associée qui contrôle le comportement de défilement dans <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 L’exemple suivant utilise le <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> et <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> méthodes.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
