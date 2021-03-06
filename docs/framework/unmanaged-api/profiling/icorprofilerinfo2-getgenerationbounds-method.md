---
title: ICorProfilerInfo2::GetGenerationBounds, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cfac1304a3d60a418065e4fc2994705548eeac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds, méthode
Obtient les régions de la mémoire, qui sont des segments du tas, composant les différentes générations de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cObjectRanges`  
 [in] Nombre d'éléments alloués par l'appelant pour le tableau `ranges`.  
  
 `pcObjectRanges`  
 [out] Pointeur vers un entier qui spécifie le nombre total de plages, dont une partie ou la totalité sera retournée dans le tableau `ranges`.  
  
 `ranges`  
 [out] Un tableau de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, qui décrivent chacune une plage (autrement dit, un bloc) de mémoire dans la génération qui subit le garbage collection.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetGenerationBounds` peut être appelée à partir de tout rappel de profileur, à condition que le garbage collection ne soit pas en cours d'exécution. Autrement dit, elle peut être appelée à partir de tout rappel, à l’exception de ceux qui interviennent entre [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) et [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 La plupart des décalages de générations ont lieu pendant les opérations de garbage collection. Les générations peuvent devenir plus volumineuses entre les collections, mais elles ne se déplacent généralement pas. Par conséquent, les endroits les plus intéressants pour appeler `GetGenerationBounds` sont dans `ICorProfilerCallback2::GarbageCollectionStarted` et `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Pendant le démarrage du programme, certains objets sont alloués par le Common Language Runtime (CLR) lui-même, en général dans les générations 3 et 0. Ainsi, quand le code managé commence à s'exécuter, ces générations contiennent déjà des objets. Normalement, les générations 1 et 2 sont vides, à l'exception des objets factices qui sont générés par le garbage collector. (La taille des objets factices est de 12 octets dans les implémentations 32 bits du CLR ; elle est plus importante dans les implémentations 64 bits.) Vous verrez peut-être également des plages de génération 2 qui sont contenues dans les modules générés par le générateur d'images natives (NGen.exe). Dans ce cas, les objets de génération 2 sont *objets figés*, qui sont alloués quand NGen.exe s’exécute, plutôt que par le garbage collector.  
  
 Cette fonction utilise des mémoires tampons allouées par l'appelant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
