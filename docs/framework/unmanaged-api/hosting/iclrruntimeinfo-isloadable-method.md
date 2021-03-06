---
title: ICLRRuntimeInfo::IsLoadable, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable, méthode
Indique si le runtime associé à cette interface peut être chargé dans le processus actuel, en tenant compte autres exécutions qui peuvent déjà être chargées dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbLoadable`  
 [out] `true` si ce runtime a pu être chargé dans le processus actuel ; sinon, `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pbLoadable` a la valeur null.|  
  
## <a name="remarks"></a>Notes  
 Si un autre runtime est déjà chargé dans le processus et que le runtime associé à cette interface peut être chargé pour l’exécution de côte à côte in-process, `pbLoadable` retourne `true`. Si les deux runtimes ne peut pas exécuter côte à côte in-process, `pbLoadable` retourne `false`. Par exemple, le common language runtime (CLR) version 4 peut s’exécuter côte à côte dans le même processus avec le CLR version 2.0 ou CLR version 1.1. Toutefois, la version 1.1 et CLR version 2.0 ne peut pas exécuter de côte à côte in-process.  
  
 Si aucun runtime n’est chargées dans le processus, cette méthode retourne toujours `true`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRRuntimeInfo, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
