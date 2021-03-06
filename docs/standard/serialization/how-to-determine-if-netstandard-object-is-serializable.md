---
title: 'Comment : déterminer si un objet .NET Standard est sérialisable'
description: Montre comment déterminer si un type .NET Standard peut être sérialisé en cours d’exécution.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 247eed2e7091930c6bcfaa524296b45350dd6510
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Comment : déterminer si un objet .NET Standard est sérialisable

.NET Standard est une spécification qui définit les types et membres qui doivent être présents sur des implémentations spécifiques de .NET qui se conforment à cette version de la norme. Toutefois, .NET Standard ne définit pas si un type est sérialisable. Les types définis dans la bibliothèque Standard .NET ne sont pas marqués avec le <xref:System.SerializableAttribute> attribut. Au lieu de cela, les implémentations .NET spécifiques, telles que le .NET Framework et le .NET Core, sont libres de déterminer si un type particulier est sérialisable. 

Si vous avez développé une bibliothèque qui cible .NET Standard, la bibliothèque peut être consommée par une implémentation .NET qui prend en charge .NET Standard. Cela signifie que vous ne pouvez pas savoir à l’avance si un type particulier est sérialisable ; Vous ne pouvez déterminer s’il est sérialisable en cours d’exécution.

Vous pouvez déterminer si un objet est sérialisable lors de l’exécution en récupérant la valeur de la <xref:System.Type.IsSerializable> propriété d’un <xref:System.Type> objet qui représente le type de l’objet. L’exemple suivant fournit une implémentation. Il définit un `IsSerializable(Object)` méthode d’extension qui indique si les <xref:System.Object> instance peut être sérialisée.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Vous pouvez ensuite passer n’importe quel objet à la méthode pour déterminer si elle peut être sérialisé et désérialisé sur l’implémentation actuelle de .NET, comme le montre l’exemple suivant :

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a>Voir aussi

[Sérialisation binaire](binary-serialization.md)   
<xref:System.SerializableAttribute?displayProperty=nameWithType>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
