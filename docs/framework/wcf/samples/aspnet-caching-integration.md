---
title: ASP.NET Caching Integration
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 420ff192caf41a37b6229bf36e32124f3646d69c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="aspnet-caching-integration"></a>ASP.NET Caching Integration
Cet exemple montre comment utiliser le cache de sortie ASP.NET avec le modèle de programmation HTTP Web WCF. Consultez le [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample pour une version autonome de ce scénario présente l’implémentation de service en profondeur. Cette rubrique met l’accent sur la fonctionnalité d’intégration du cache de sortie ASP.NET.  
  
## <a name="demonstrates"></a>Démonstrations  
 Intégration au cache de sortie ASP.NET  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Discussion  
 L’exemple utilise le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pour utiliser ASP.NET la sortie mise en cache avec le service Windows Communication Foundation (WCF). L'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est appliqué aux opérations de service et fournit le nom d'un profil de cache dans un fichier de configuration qui doit être appliqué aux réponses de l'opération donnée.  
  
 Dans le fichier Service.cs de l’exemple de projet de Service, à la fois le `GetCustomer` et `GetCustomers` opérations sont marquées avec le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, qui fournit le nom de profil de cache « CacheFor60Seconds ». Dans le fichier Web.config du projet de Service, le profil de cache « CacheFor60Seconds » est fourni sous la <`caching`> élément de <`system.web`>. Pour ce profil de cache, la valeur de la `duration` attribut étant « 60 », les réponses associées à ce profil sont mises en cache dans le cache de sortie ASP.NET pendant 60 secondes. En outre, pour ce profil de cache, le `varmByParam` attribut est défini sur « format » demande avec des valeurs différentes pour le `format` requête paramètre de chaîne ont leurs réponses mises en cache séparément. D’Enfin, le profil de cache `varyByHeader` attribut est défini sur « Accepter », pour que les demandes avec différentes valeurs d’en-tête Accept aient leurs réponses mises en cache séparément.  
  
 Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>. Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF. Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme la fabrique de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et <xref:System.Net.WebClient>. Autres exemples du SDK (telles que la [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) exemple et [la sélection automatique du Format](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemple) illustrent l’utilisation de ces classes pour communiquer avec un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
## <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
 Cet exemple est composé de trois projets :  
  
-   **Service**: projet d’Application Web qui inclut un service HTTP WCF hébergé dans ASP.NET.  
  
-   **Client**: un projet d’application console qui passe des appels au service.  
  
-   **Common**: une bibliothèque partagée qui contient le type de client utilisé par le client et le service.  
  
 Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution de l'exemple ASP.NET Caching Integration.  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Si le **l’Explorateur de solutions** fenêtre n’est pas déjà ouverte, appuyez sur CTRL + W + S.  
  
4.  À partir de la **l’Explorateur de solutions** fenêtre, le bouton droit sur le **Service** de projet et sélectionnez **démarrer une nouvelle Instance**. Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5.  À partir de la **l’Explorateur de solutions** fenêtre, le bouton droit sur le **Client** de projet et sélectionnez **démarrer une nouvelle Instance**.  
  
6.  La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.  
  
7.  Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
8.  Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
9. Appuyez sur MAJ+F5 pour arrêter le débogage du service.  
  
10. Dans la zone de Notification Windows, cliquez avec le bouton droit sur l’icône serveur de développement ASP.NET et sélectionnez **arrêter**.
