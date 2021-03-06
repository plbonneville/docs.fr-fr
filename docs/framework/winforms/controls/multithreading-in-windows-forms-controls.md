---
title: Multithreading dans les contrôles Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 68822c62a1a195ce3128d51c765cfeba2056955d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithreading dans les contrôles Windows Forms
Dans de nombreuses applications, vous pouvez rendre votre interface utilisateur (IU) plus réactive en effectuant les opérations de longue durée sur un autre thread. Un certain nombre d’outils est disponible pour le multithreading vos contrôles Windows Forms, y compris le <xref:System.Threading> espace de noms, le <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> (méthode) et le `BackgroundWorker` composant.  
  
> [!NOTE]
>  Le `BackgroundWorker` composant remplace et ajoute des fonctionnalités à la <xref:System.Threading> espace de noms et le <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> méthode ; Toutefois, ceux-ci sont conservés pour la compatibilité descendante et une utilisation ultérieure, si vous choisissez. Pour plus d’informations, consultez [vue d’ensemble du composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour faire des appels thread-safe aux contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Montre comment effectuer des appels thread-safe aux contrôles Windows Forms.  
  
 [Guide pratique pour utiliser un thread d'arrière-plan pour rechercher des fichiers](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Montre comment utiliser le <xref:System.Threading> espace de noms et le <xref:System.Windows.Forms.Control.BeginInvoke%2A> méthode pour rechercher des fichiers de façon asynchrone.  
  
## <a name="reference"></a>Référence  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documente un composant qui encapsule un thread de travail pour les opérations asynchrones.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Explique comment charger un son de façon asynchrone.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Explique comment charger une image de façon asynchrone.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour exécuter une opération en arrière-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Montre comment effectuer une opération longue avec le <xref:System.ComponentModel.BackgroundWorker> composant.  
  
 [Vue d'ensemble du composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Fournit des rubriques qui décrivent comment utiliser le <xref:System.ComponentModel.BackgroundWorker> composant pour les opérations asynchrones.
