---
title: CorDebugStepReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason, énumération
Indique le résultat d'une étape individuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`STEP_NORMAL`|Exécution pas à pas s’est terminée normalement, dans la même fonction.|  
|`STEP_RETURN`|Exécution pas à pas a continué normalement, une fois que la fonction a renvoyé.|  
|`STEP_CALL`|Exécution pas à pas a continué normalement, au début d’une fonction qui vient d’être appelée.|  
|`STEP_EXCEPTION_FILTER`|Une exception a été générée et le contrôle a été passé à un filtre d’exception.|  
|`STEP_EXCEPTION_HANDLER`|Une exception a été générée et le contrôle a été passé à un gestionnaire d’exceptions.|  
|`STEP_INTERCEPT`|Contrôle a été passé à un intercepteur.|  
|`STEP_EXIT`|Le thread est arrêté avant la fin de l’étape.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StepComplete, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
