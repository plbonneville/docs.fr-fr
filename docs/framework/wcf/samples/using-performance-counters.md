---
title: Using Performance Counters
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 2e25551494a433c53832127fdb0a32cb4eccac47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="using-performance-counters"></a>Using Performance Counters
Cet exemple montre comment accéder aux compteurs de performances de Windows Communication Foundation (WCF) et comment créer des compteurs de performance définis par l’utilisateur. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`. Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur. Le service reste inchangé.  
  
 Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Cette tâche peut également être effectuée à l’aide de la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Lorsque les compteurs de performance sont activés, la suite entière de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est activée pour le service. Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`. Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Pour afficher les données de performances  
  
1.  Démarrez l’outil Analyseur de performances en cliquant sur **Démarrer**, **exécuter...** , entrez `perfmon` et cliquez sur **OK,** ou, dans le panneau de configuration, sélectionnez **outils d’administration** et double-cliquez sur **performances**.  
  
    > [!NOTE]
    >  Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.  
  
2.  Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.  
  
3.  Ajouter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] compteurs en cliquant sur le volet du graphique et en sélectionnant **ajouter des compteurs**. Dans le **ajouter des compteurs** boîte de dialogue, sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** dans l’objet de Performance, faites glisser la zone de liste. Sélectionnez les compteurs que vous souhaitez afficher dans la liste.  
  
    > [!NOTE]
    >  Il n'y a pas de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour un service s'il n'y a pas de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en cours d'exécution sur l'ordinateur.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Pour utiliser l'Éditeur de configuration afin d'activer des compteurs  
  
1.  Ouvrez une instance de SvcConfigEditor.exe.  
  
2.  Dans le menu fichier, cliquez sur **ouvrir** , puis **le fichier de configuration...** .  
  
3.  Naviguez jusqu’au dossier de service de l’exemple d’application et ouvrez le fichier Web.config.  
  
4.  Cliquez sur **Diagnostics** sur l’arborescence de la Configuration.  
  
5.  Activer/désactiver **compteur de Performance** dans les **Diagnostics** fenêtre 'All'.  
  
6.  Enregistrez le fichier de configuration et quittez l'éditeur.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
