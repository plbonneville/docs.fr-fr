---
title: COR_PRF_GC_ROOT_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d5dcb089074b52fc87a0bb83c7e062e7ef07b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS, énumération
Indique une propriété d’une racine de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|La racine empêche un garbage collection de déplacer l’objet.|  
|`COR_PRF_GC_ROOT_WEAKREF`|La racine n’empêche pas le garbage collection.|  
|`COR_PRF_GC_ROOT_INTERIOR`|La racine fait référence à un champ de l’objet plutôt que l’objet lui-même.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|La racine empêche le garbage collection si le décompte de références de l’objet est une certaine valeur.|  
  
## <a name="remarks"></a>Notes  
 `COR_PRF_GC_ROOT_FLAGS` est un masque de bits qui fournit des informations supplémentaires à propos des racines spéciales. Toutefois, pas toutes les racines sont spéciales. Par exemple, certaines racines ne sont pas des références faibles, des pointeurs intérieurs, épinglés ou comptés par référence. Pour de telles racines, il n’existe aucun indicateur pour transmettre. Par conséquent, les méthodes qui utilisent cette énumération, telles que la [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) (méthode), envoi 0 pour le masque de bits d’indicateurs, indiquant que tous les indicateurs sont désactivés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
