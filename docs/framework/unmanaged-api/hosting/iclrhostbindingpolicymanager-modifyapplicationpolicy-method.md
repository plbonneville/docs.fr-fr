---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a221b286ada97c3c03387556cb30ee6ddd2c453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzSourceAssemblyIdentity`  
 [in] L’identité de l’assembly à modifier.  
  
 `pwzTargetAssemblyIdentity`  
 [in] La nouvelle identité de l’assembly modifié.  
  
 `pbApplicationPolicy`  
 [in] Pointeur vers une mémoire tampon qui contient les données de stratégie de liaison pour l’assembly à modifier.  
  
 `cbAppPolicySize`  
 [in] La taille de la stratégie de liaison à remplacer.  
  
 `dwPolicyModifyFlags`  
 [in] Combinaison OR logique de [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) valeurs indiquant le contrôle de la redirection.  
  
 `pbNewApplicationPolicy`  
 [out] Pointeur vers une mémoire tampon qui contient les nouvelles données de stratégie de liaison.  
  
 `pcbNewAppPolicySize`  
 [dans, out] Pointeur vers la taille de la nouvelle mémoire tampon de stratégie de liaison.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La stratégie a été modifiée avec succès.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` ou `pwzTargetAssemblyIdentity` était une référence null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le `ModifyApplicationPolicy` méthode peut être appelée deux fois. Le premier appel doit fournir une valeur null pour le `pbNewApplicationPolicy` paramètre. Cet appel retournera avec la valeur nécessaire pour `pcbNewAppPolicySize`. Le deuxième appel doit fournir cette valeur pour `pcbNewAppPolicySize`et pointer vers un mémoire tampon de cette taille pour `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
