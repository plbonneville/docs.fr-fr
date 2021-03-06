---
title: Configuration Channel Factory
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 3d439fb17d676ce337207a726fb9e491cf0a0ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="configuration-channel-factory"></a>Configuration Channel Factory
Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. Le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet une gestion centralisée de la configuration du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.  
  
## <a name="demonstrates"></a>Démonstrations  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.  
  
 Cet exemple est composé de deux projets. Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients. Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service. Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.  
  
 Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec les privilèges d'administrateur.  
  
2.  Avec le bouton droit de la solution ConfigurationChannelFactory (2 projets), puis sélectionnez **propriétés**.  
  
3.  Dans **propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **plusieurs projets de démarrage**.  
  
4.  Déplacer le **Service** de projet vers le début de la liste, avec la **Action 'Start'**, puis déplacez le **Client** projet après le **Service**projet, également avec la **Action 'Start'**, donc le **Client** projet est exécuté après le **Service** projet.  
  
5.  Cliquez sur **OK**, puis appuyez sur F5 (ou CTRL + F5) pour exécuter l’exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
