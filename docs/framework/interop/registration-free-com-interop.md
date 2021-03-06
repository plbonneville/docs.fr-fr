---
title: COM Interop sans inscription
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32ee3babe054d55a45cc8826843252dba6aa2be7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="registration-free-com-interop"></a>COM Interop sans inscription
COM Interop sans inscription active un composant sans utiliser le Registre Windows pour stocker les informations d'assembly. Au lieu d'inscrire un composant sur un ordinateur pendant le déploiement, vous créez des fichiers manifeste de type Win32 au moment du design qui contiennent des informations sur la liaison et l'activation. Ces fichiers manifeste, plutôt que les clés de Registre, dirigent l'activation d'un objet.  
  
 L'activation sans inscription de vos assemblys pendant le déploiement offre deux avantages :  
  
-   Vous pouvez contrôler la version DLL qui est activée quand plusieurs versions sont installées sur un ordinateur.  
  
-   Les utilisateurs finaux peuvent utiliser XCOPY ou un outil FTP pour copier votre application vers un répertoire de leur ordinateur. L'application peut ensuite être exécutée à partir de ce répertoire.  
  
 Cette section décrit les deux types de manifestes nécessaires pour l'activation de COM Interop sans inscription : les manifestes d'application et de composant. Ces manifestes sont des fichiers XML. Un manifeste d'application, qui est créé par un développeur d'applications, contient des métadonnées qui décrivent des assemblys et des dépendances d'assembly. Un manifeste de composant, créé par un développeur de composants, contient des informations qui résident dans le Registre Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Configuration requise pour COM Interop sans inscription  
  
1.  La prise en charge de COM Interop sans inscription varie légèrement selon le type d'assembly de bibliothèque, plus précisément, si l'assembly est non managé (côte à côte COM) ou managé ( basé sur .NET). Le tableau suivant présente les conditions requises concernant le système d'exploitation et la version de .NET Framework pour chaque type d'assembly.  
  
    |Type d'assembly|Système d'exploitation|Version du .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |Côte à côte COM|Microsoft Windows XP|Non requis|  
    |Basé sur .NET|Windows XP SP2|.NET Framework version 1.1 ou ultérieure|  
  
     La famille Windows Server 2003 prend également en charge COM Interop sans inscription pour les assemblys .NET.  
  
     Pour qu'une classe .NET soit compatible avec l'activation de COM sans inscription, elle doit avoir un constructeur par défaut et doit être publique.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Configuration des composants COM pour l'activation sans inscription  
  
1.  Pour qu'un composant COM participe à l'activation sans inscription, il doit être déployé comme un assembly côte à côte. Les assemblys côte à côte sont non managés.  Pour plus d’informations, consultez [utilisation d’assemblys côte à côte](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
     Pour utiliser des assemblys COM côte à côte, un développeur d’applications .NET doit fournir un manifeste d’application contenant des informations de liaison et d’activation. La prise en charge des assemblys côte à côte non managés est intégrée au système d'exploitation Windows XP. Le runtime COM, pris en charge par le système d'exploitation, recherche les informations d'activation du manifeste d'application quand le composant en cours d'activation n'est pas dans le Registre.  
  
     L’activation sans inscription est facultative pour les composants COM installés sur Windows XP. Pour obtenir des instructions détaillées sur l’ajout d’un assembly côte à côte dans une application, consultez [utilisation d’assemblys côte à côte](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
    > [!NOTE]
    >  L’exécution côte à côte est une fonctionnalité de .NET Framework qui permet à plusieurs versions du runtime et à plusieurs versions d’applications et de composants qui utilisent une version du runtime, de s’exécuter sur le même ordinateur en même temps. L'exécution côte à côte et les assemblys côte à côte sont deux mécanismes différents de la fonctionnalité de côte à côte.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour configurer les composants COM .NET Framework pour l’activation sans inscription](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
