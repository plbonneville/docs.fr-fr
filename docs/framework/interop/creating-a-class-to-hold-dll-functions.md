---
title: Création d'une classe pour contenir des fonctions DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09088d1ac0a8312ee5832a5f3bc0547e6654de93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Création d'une classe pour contenir des fonctions DLL
L’enveloppement d’une fonction DLL fréquemment utilisée dans une classe managée est une stratégie efficace d’encapsulation des fonctionnalités de la plateforme. Bien que cette opération ne soit pas obligatoire dans tous les cas, un wrapper de classe s’avère pratique, car la définition de fonctions DLL peut être fastidieuse et sujette à erreurs. En cas de programmation en Visual Basic ou C#, vous devez déclarer les fonctions DLL dans une classe ou un module Visual Basic.  
  
 Dans une classe, vous définissez une méthode statique pour chaque fonction DLL que vous souhaitez appeler. La définition peut inclure des informations supplémentaires, telles que le jeu de caractères ou la convention d’appel qui sont utilisés lors du passage des arguments des méthodes. Si vous ne renseignez pas ces informations, les paramètres par défaut sont alors sélectionnés. Pour obtenir une liste complète des options de déclaration et de leurs paramètres par défaut, consultez [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Une fois encapsulée, vous pouvez appeler les méthodes sur la classe que vous appelez des méthodes statiques sur toute autre classe. L’appel de code non managé gère automatiquement la fonction exportée sous-jacente.  
  
 Lors de la conception d’une classe managée pour l’appel de code non managé, tenez compte des relations entre les classes et les fonctions DLL. Par exemple, vous pouvez :  
  
-   déclarer des fonctions DLL dans une classe existante ;  
  
-   créer une classe individuelle pour chaque fonction DLL, en maintenant les fonctions isolées et facilement localisables ;  
  
-   créer une classe pour un ensemble de fonctions DLL associées afin de former des regroupements logiques et réduire la charge mémoire.  
  
 Vous pouvez nommer la classe et ses méthodes à votre convenance. Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Consommation de fonctions DLL non managées](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Identification des fonctions des DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Appel à une fonction DLL](../../../docs/framework/interop/calling-a-dll-function.md)
