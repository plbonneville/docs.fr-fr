---
title: ICorDebugController::Continue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529a65285203ac831e1bcab9dc1bea69ac28a282
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue, méthode
Reprend l’exécution de threads managés après un appel à [méthode Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fIsOutOfBand`  
 [in] La valeur `true` s’il continue à partir d’un événement hors-bande ; sinon, valeur `false`.  
  
## <a name="remarks"></a>Notes  
 `Continue` continue le processus après un appel à la `ICorDebugController::Stop` (méthode).  
  
 Lorsque vous effectuez un débogage en mode mixte, n’appelez pas `Continue` sur Win32 thread d’événement, sauf si vous continuez à partir d’un événement hors-bande.  
  
 Un *événement dans la bande* est un événement managé ou un événement non managé normal pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus. Dans ce cas, le débogueur reçoit le [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) rappel avec son `fOutOfBand` paramètre la valeur `false`.  
  
 Un *out-of-band événement* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible pendant que le processus est arrêté en raison de l’événement. Dans ce cas, le débogueur reçoit le `ICorDebugUnmanagedCallback::DebugEvent` rappel avec son `fOutOfBand` paramètre la valeur `true`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
