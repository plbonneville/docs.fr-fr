---
title: Événement ETW de pile
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 073622c22b957975ed799cf5b3bc3826473114b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="stack-etw-event"></a>Événement ETW de pile
L’événement de pile doit être utilisé conjointement avec d’autres événements pour générer des arborescences d’appels de procédure après le déclenchement d’un événement. Il est enregistré quand le fournisseur du runtime est activé. Il s’agit d’un événement très fréquent, car il est déclenché à chaque déclenchement d’un autre événement runtime. Pour cette raison, nous vous recommandons d’utiliser cet événement avec précaution.  
  
 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Conjointement avec d’autres événements pour générer les arborescences des appels de procédure après un événement.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:Uint16|Identificateur de runtime unique.|  
|Reserved1|win:UInt8|Réservé.|  
|Reserved2|win:UInt8|Réservé.|  
|FrameCount|win:UInt32|Nombre de frames dans l’arborescence des appels de procédure.|  
|Stack|win:Pointer|Colonnes de pointeurs d’instruction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
