---
title: CreateHistoryReader, fonction
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3a3cc21dbbcfa99ddcecb534bd2e337da005597
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader, fonction
Crée un lecteur de l’historique pour le fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wzFilePath`  
 [in] Le chemin d’accès du fichier.  
  
 `ppHistoryReader`  
 [out] Opération réussie, contient un pointeur vers le lecteur de l’historique.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard, tel que défini dans WinError.h, en plus des valeurs décrites dans le tableau suivant.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|Indique que la méthode a réussi.|  
|E_INVALIDARG|Indique que `wzFilePath` ou `ppHistoryReader` sont définies sur une référence null.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Bibliothèque :** Fusion.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
