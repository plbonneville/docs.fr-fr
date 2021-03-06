---
title: 'Comment : créer une scène 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-3-d-scene"></a>Comment : créer une scène 3D
Cet exemple montre comment créer un objet 3D qui ressemble à une feuille de papier ayant subi une rotation. A <xref:System.Windows.Controls.Viewport3D> , ainsi que les composants suivants sont utilisés pour créer cette scène 3D simple :  
  
-   Une caméra est créée à l’aide un <xref:System.Windows.Media.Media3D.PerspectiveCamera>. L’appareil photo spécifie quelle partie de la scène 3D est visible.  
  
-   Un maillage est créé pour spécifier la forme de l’objet 3D (feuille de papier) à l’aide du <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriété du <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Un matériau est spécifié pour être affiché sur la surface de l’objet (dégradé linéaire dans cet exemple) en utilisant le <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriété du <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Un éclairage est créé pour éclairer sur l’objet à l’aide de <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous montre comment créer une scène 3D en XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous montre comment créer la même scène 3D en code procédural.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
