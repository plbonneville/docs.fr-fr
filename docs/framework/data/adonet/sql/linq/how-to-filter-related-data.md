---
title: 'Comment : filtrer des données liées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: b40de7201610c58b9b8e86045afe5869d958bdf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-filter-related-data"></a>Comment : filtrer des données liées
Utilisez la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> pour spécifier des sous-requêtes afin de limiter la quantité de données récupérées.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limite les `Orders` récupérées à celles qui n'ont pas encore été expédiées aujourd'hui. Sans cette approche, toutes les `Orders` auraient été récupérées bien que seul un sous-ensemble soit désiré.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
