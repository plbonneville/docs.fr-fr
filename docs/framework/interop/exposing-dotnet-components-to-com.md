---
title: Exposition de composants .NET Framework à COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f11928388dba9b0e9b442578bfb7b6f751c2e172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="exposing-net-framework-components-to-com"></a>Exposition de composants .NET Framework à COM
L’écriture d’un type .NET et l’utilisation de ce type à partir de code non managé sont deux activités distinctes pour les développeurs. Cette section contient plusieurs conseils pour l’écriture de code managé interagissant avec des clients COM :  
  
-   [Qualification des types .NET pour l’interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Tous les types, méthodes, propriétés, champs et événements managés que vous voulez exposer à COM doivent être publics. Les types doivent avoir un constructeur public par défaut, qui est le seul constructeur pouvant être appelé dans COM.  
  
-   [Application d’attributs d’interopérabilité](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Les attributs personnalisés dans du code managé peuvent améliorer l’interopérabilité d’un composant.  
  
-   [Empaquetage d’un assembly pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Les développeurs COM peuvent vous demander de résumer les étapes impliquées dans le référencement et le déploiement de vos assemblys.  
  
 De plus, cette section identifie les tâches relatives à la consommation d’un type managé à partir d’un client COM.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Pour consommer un type managé à partir de COM  
  
1.  [Inscription d’assemblys auprès de COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Les types d’un assembly (et des bibliothèques de types) doivent être inscrits au moment du design. Si un programme d’installation n’inscrit pas l’assembly, indiquez aux développeurs COM qu’ils doivent utiliser Regasm.exe.  
  
2.  [Référencer des types .NET à partir de COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
  
     Les développeurs COM peuvent référencer des types dans un assembly en utilisant les mêmes outils et techniques que ceux qu’ils utilisent aujourd’hui.  
  
3.  [Appel d’un objet .NET](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).  
  
     Les développeurs COM peuvent appeler des méthodes sur l’objet .NET de la même façon qu’ils appellent des méthodes sur un type non managé. Par exemple, l’API **CoCreateInstance** de COM active des objets .NET.  
  
4.  [Déploiement d’une application pour accéder à COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).  
  
     Un assembly avec nom fort peut être installé dans le Global Assembly Cache et nécessite une signature de son éditeur. Les assemblys qui n’ont pas de nom fort doivent être installés dans le répertoire de l’application du client.  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du code non managé](../../../docs/framework/interop/index.md)  
 [COM Interop, exemple : client COM et serveur .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
