---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Cet exemple montre comment insérer des métadonnées XML personnalisées dans les métadonnées de découverte pour un point de terminaison détectable exposé par un service. Il montre ensuite comment un client peut rechercher le service et extraire ces données personnalisées. Cet exemple se compose de deux projets : service et client.  
  
## <a name="service"></a>Service  
 Dans la méthode `main`, l'exemple montre qu'un objet de type <xref:System.Xml.Linq.XElement> est rempli avec les champs voulus et ajouté au <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Ce <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est ajouté à un point de terminaison particulier. Lorsque ce point de terminaison particulier est découvert, les métadonnées de découverte contiennent les données personnalisées ajoutées ici.  
  
## <a name="client"></a>Client  
 L'exemple illustre la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> qui est appelée sur un <xref:System.ServiceModel.Discovery.DiscoveryClient>. Le <xref:System.ServiceModel.Discovery.FindResponse> obtenu est alors interrogé pour déterminer s'il contient les éléments XML appropriés et attendus. Ces éléments sont ensuite affichés dans la console.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] et générez le projet.  
  
2.  Exécutez d'abord l'application Service, générée dans [répertoire de base de la solution]\service\bin\debug, puis l'application Client, générée dans [répertoire de base de la solution]\Client\bin\debug.  
  
3.  Notez que le service est mis en ligne, et que le client trouve le service et imprime les métadonnées publiées dans le point de terminaison.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Voir aussi
