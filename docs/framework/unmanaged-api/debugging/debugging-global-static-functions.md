---
title: Fonctions statiques globales du débogage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-global-static-functions"></a>Fonctions statiques globales du débogage
Cette section décrit les fonctions statiques globales non managées utilisées par l'API de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [_EFN_GetManagedExcepStack, fonction](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.  
  
 [_EFN_GetManagedObjectFieldInfo, fonction](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.  
  
 [_EFN_GetManagedObjectName, fonction](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Obtient le nom d'un type à l'aide du pointeur d'objet managé fourni.  
  
 [_EFN_StackTrace, fonction](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.  
  
 [CLRDataCreateInstance, fonction](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Appelé par les services d'accès aux données du Common Language Runtime (CLR) pour créer l'objet d'interface spécifié pour le processus cible spécifié.  
  
 [PFN_CLRDataCreateInstance, pointeur fonction](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Pointe vers une fonction qui est appelée par les services d'accès aux données du CLR pour créer l'objet d'interface indiqué pour le processus cible spécifié.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
