---
title: 'Comment : utiliser un MatrixTransform pour créer des transformations personnalisées'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 4ffbefea498e9a2bdc5546d112f6ff10e12fed67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Comment : utiliser un MatrixTransform pour créer des transformations personnalisées
Cet exemple montre comment utiliser un <xref:System.Windows.Media.MatrixTransform> pour traduire (déplacer) la position, stretch et l’inclinaison d’un <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Utilisez le <xref:System.Windows.Media.MatrixTransform> classe pour créer des transformations personnalisées qui ne sont pas fournies par le <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> classes.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
