---
title: 'Comment : ajouter une référence de services de données (services de données WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Comment : ajouter une référence de services de données (services de données WCF)
Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. De cette manière, vous pouvez accéder plus facilement à un service de données dans une application cliente que vous développez dans Visual Studio. Lorsque vous complétez cette procédure, les classes de données sont générées selon les métadonnées obtenues auprès du service de données. Pour plus d’informations, consultez [génération de la bibliothèque de Client de Service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
### <a name="to-add-a-data-service-reference"></a>Pour ajouter une référence de service de données  
  
1.  (Facultatif) Si le service de données n'appartient pas à la solution et n'est pas déjà en cours d'exécution, démarrez le service de données et notez l'URI du service de données.  
  
2.  Cliquez sur le projet client, puis sélectionnez **ajouter une référence de Service**.  
  
3.  Si le service de données fait partie de la solution actuelle, cliquez sur **Discover**.  
  
     - ou -  
  
     Dans le **adresse** zone de texte, tapez l’URL de base du service de données, telles que `http://localhost:1234/Northwind.svc`, puis cliquez sur **accédez**.  
  
4.  Cliquez sur **OK**.  
  
     Cette opération ajoute un nouveau fichier de code qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service des données sous la forme d'objets.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
