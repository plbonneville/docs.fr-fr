---
title: GetVersionFromProcess, fonction
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b57d04a8a49371872c679a331b5ae9c45dce797
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess, fonction
Obtient le numéro de version du common language runtime (CLR) qui est associé au handle de processus spécifié.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hProcess`  
 [in] Un handle d’un processus.  
  
 `pVersion`  
 [out] Une mémoire tampon qui contient la chaîne de numéro de version à l’achèvement réussi de la méthode.  
  
 `cchBuffer`  
 [in] La longueur de la mémoire tampon de version.  
  
 `pdwLength`  
 [out] Pointeur vers la longueur de la chaîne de numéro de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de modèle COM (Component Object) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`pVersion` a la valeur null et `cchBuffer` n’est pas null, ou vice versa.<br /><br /> - ou -<br /><br /> `hProcess` n’est pas un handle valide d’un processus.<br /><br /> - ou -<br /><br /> Le CLR n’est pas chargé.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` est null ou inférieur à la longueur de la chaîne de version.|  
|E_NOTIMPL|Cette méthode n’est pas disponible sur le système d’exploitation Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetRequestedRuntimeInfo, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetRequestedRuntimeVersion, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
