---
title: "Comment : animer une propriété à l'aide d'un AnimationClock"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: b8c64586d0dc5dc2e565fe4cb002e0f9cd4109af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Comment : animer une propriété à l'aide d'un AnimationClock
Cet exemple montre comment utiliser <xref:System.Windows.Media.Animation.Clock> objets pour animer une propriété.  
  
 Il existe trois façons d’animer une propriété de dépendance :  
  
-   Créer un <xref:System.Windows.Media.Animation.AnimationTimeline> et l’associer à cette propriété en utilisant un <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Utilisez l’objet <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> pour appliquer une seule méthode <xref:System.Windows.Media.Animation.AnimationTimeline> à une propriété cible.  
  
-   Créer un <xref:System.Windows.Media.Animation.AnimationClock> d’un <xref:System.Windows.Media.Animation.AnimationTimeline> et appliquez-le à une propriété.  
  
 <xref:System.Windows.Media.Animation.Storyboard> objets et la <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode permettent d’animer des propriétés sans créer et distribuer des horloges directement (pour obtenir des exemples, consultez [animer une propriété à l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) et [animer une propriété sans À l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)) ; horloges sont créés et distribués automatiquement pour vous.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à deux propriétés similaires.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Pour obtenir un exemple montrant comment contrôler de façon interactive une <xref:System.Windows.Media.Animation.Clock> après son démarrage, consultez [contrôler de façon interactive une horloge au format](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Animer une propriété à l’aide d’une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
