---
title: "Comment : créer un service de données à l'aide du fournisseur de réflexion (services de données WCF)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 44ba47deaf803f8a911b5a76d7e93f09b47e677a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Comment : créer un service de données à l'aide du fournisseur de réflexion (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de définir un modèle de données basé sur les classes arbitraires tant que ces classes sont exposées comme des objets qui implémentent l'interface <xref:System.Linq.IQueryable%601>. Pour plus d’informations, consultez [des fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit un modèle de données qui inclut `Orders` et `Items`. La classe de conteneur d'entités  `OrderItemData` a deux méthodes publiques qui retournent des interfaces <xref:System.Linq.IQueryable%601>. Ces interfaces sont les jeux d'entités des types d'entité `Orders` et `Items`. Un `Order` peut inclure plusieurs `Items`, donc le type d'entité `Orders` a une propriété de navigation `Items` qui retourne une collection d'objets `Items`. La classe de conteneur d'entités `OrderItemData` est le type générique de la classe <xref:System.Data.Services.DataService%601> d'où est dérivé le service de données `OrderItems`.  
  
> [!NOTE]
>  Comme cet exemple illustre un fournisseur de données en mémoire et que les modifications ne sont pas persistantes en dehors des instances de l'objet actuelles, l'implémentation de l'interface <xref:System.Data.Services.IUpdatable> n'apporte aucun avantage. Pour obtenir un exemple qui implémente le <xref:System.Data.Services.IUpdatable> l’interface, consultez [Comment : créer un Service de données à l’aide de LINQ vers la Source de données SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer un service de données à l’aide d’une source de données LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [Fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Guide pratique pour créer un service de données à l’aide d’une source de données Entity Framework ADO.NET](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
