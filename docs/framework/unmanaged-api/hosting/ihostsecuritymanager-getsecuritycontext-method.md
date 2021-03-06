---
title: IHostSecurityManager::GetSecurityContext, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8b6c110a4e7754a6bcca326b659599ffa2caedf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a>IHostSecurityManager::GetSecurityContext, méthode
Obtient l’élément demandé [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) à partir de l’ordinateur hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `eContextType`  
 [in] Parmi les [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valeurs indiquant le type de contexte de sécurité à retourner.  
  
 `ppSecurityContext`  
 [out] L’adresse du pointeur d’interface vers le `IHostSecurityContext` de `eContextType`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetSecurityContext` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut contrôler tous les accès du code aux jetons de threads par le CLR et l’utilisateur du code. Il peut également garantir que la sécurité complète les informations de contexte sont passées aux opérations asynchrones ou des points de code avec accès restreint au code. `IHostSecurityContext` encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR. Le CLR intercepte ces informations et les déplace dans la répartition d’élément de travail de pool de threads, l’exécution du finaliseur et la construction de module et de classe.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [EContextType, énumération](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [IHostSecurityContext, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
