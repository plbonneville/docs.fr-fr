---
title: StrongNameSignatureVerificationEx2, méthode
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d2ac3788b68626eb04a6f2cbac995b8e5b4ebf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2, méthode
Vérifie la signature d’un assembly portant un nom fort et fournit un mappage à partir de la clé ECMA à une clé réelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [in] Le chemin d’accès pour le fichier exécutable portable (.exe ou .dll) pour l’assembly à vérifier.  
  
 `fForceVerification`  
 [in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres de Registre ; sinon, `false`.  
  
 `pbEcmaPublicKey`  
 [in] Un pointeur vers le mappage à partir de la clé publique ECMA à la clé réelle utilisée pour la vérification.  
  
 `cbEcmaPublicKey`  
 [in] La longueur de la clé publique ECMA réelle.  
  
 `pfWasVerified`  
 [out] `true` si la signature de nom fort a été vérifiée ; sinon, `false`. Ce paramètre est également défini sur `false` si la vérification a réussi en raison des paramètres de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la vérification a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameSignatureVerification, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [StrongNameSignatureVerificationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
