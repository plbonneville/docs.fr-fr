---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac495e10be2ec1534dc9d9081aef369773d93e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="-win32resource"></a>-win32resource
Insère un fichier de ressources Win32 dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Le nom du fichier de ressources à ajouter à votre fichier de sortie. Placez le nom de fichier entre guillemets ( » «) si elle contient un espace.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressources (RC) Microsoft Windows.  
  
 Une ressource Win32 peut contenir de version ou les informations de bitmap (icône) qui vous aide à identifier votre application dans **l’Explorateur de fichiers**. Si vous ne spécifiez pas `-win32resource`, le compilateur génère des informations de version en fonction de la version d’assembly. Le `-win32resource` et `-win32icon` options s’excluent mutuellement.  
  
 Consultez [- /linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) référence un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fichier de ressources, ou [-ressources (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fichier de ressources.  
  
> [!NOTE]
>  Le `-win32resource` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et attache un fichier de ressources Win32, `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
