---
title: IHostSyncManager::CreateAutoEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe1b685f50f793f7451187f17adc848ec9d4422f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagercreateautoevent-method"></a>IHostSyncManager::CreateAutoEvent, méthode
Crée un objet d’événement de réinitialisation automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEvent`  
 [out] Un pointeur vers l’adresse d’un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implémentée par l’hôte, ou null si l’objet d’événement n’a pas pu être créé.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateAutoEvent` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pas assez de mémoire n’était disponible pour créer l’objet de l’événement demandé.|  
  
## <a name="remarks"></a>Notes  
 `CreateAutoEvent` Crée un objet événement automatique dont l’état est modifié automatiquement en non signalé une fois que le thread en attente a été publié. Cette méthode reflète Win32 `CreateEvent` fonction avec la valeur `false` spécifié pour le `bManualReset` paramètre  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostAutoEvent, interface](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [IHostSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
