---
title: CorDebugMappingResult, énumération
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult, énumération
Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Le code natif est dans le prologue, la valeur de l’adresse IP est 0.|  
|`MAPPING_EPILOG`|Le code natif est dans un épilogue, la valeur de l’adresse IP est l’adresse de la dernière instruction de la méthode.|  
|`MAPPING_NO_INFO`|Aucune information de mappage n’est disponible pour la méthode, la valeur de l’adresse IP est 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Bien qu’il existe des informations de mappage pour la méthode, l’adresse actuelle ne peut pas être mappé au code Microsoft intermediate language (MSIL). La valeur de l’adresse IP est 0.|  
|`MAPPING_EXACT`|La méthode correspond exactement au code MSIL soit le frame a été interprété, donc la valeur de l’adresse IP est précise.|  
|`MAPPING_APPROXIMATE`|La méthode a été correctement mappée, mais la valeur de l’adresse IP peut être approximative.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) méthode pour obtenir la valeur du pointeur d’instruction.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
