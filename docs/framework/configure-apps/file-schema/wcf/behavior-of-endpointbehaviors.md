---
title: '&lt;behavior&gt; de &lt;endpointBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: e275fbc1b14469553094a4df838930be53937de2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a>&lt;behavior&gt; de &lt;endpointBehaviors&gt;
L'élément `behavior` contient une collection de paramètres concernant le comportement d'un point de terminaison. Chaque comportement est indexé en fonction de son `name`. Les points de terminaison peuvent être liés à chaque comportement à travers ce nom. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom. Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <endpointBehaviors>  
       <behavior name="String" />  
    </endpointBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement. Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom. Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|Spécifie le débogage de service pour un objet de rappel Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|Spécifie le délai d'attente pour le rappel du client.|  
|[\<clientVia >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|Spécifie l'itinéraire qu'un message doit suivre.|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|Contient les données de configuration pour DataContractSerializer.|  
|[\<dispatcherSynchronization >](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.|  
|[\<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|Active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX. Le comportement doit uniquement être utilisé conjointement avec l’option le \<webHttpBinding > liaison standard, ou le \<webMessageEncoding > élément de liaison.|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.|  
|[\<soapProcessing >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|Spécifie le comportement au moment de l'exécution pour la réception de messages dans une application de service ou cliente. Il n'a aucun attribut ou élément enfant.|  
|[\<transactedBatching >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.|  
|[\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|Spécifie le WebHttpBehavior d'un point de terminaison via la configuration. Ce comportement est utilisé conjointement avec le \<webHttpBinding > permet de liaison standard, le modèle de programmation Web pour un service WCF.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Collection d’éléments de comportement de point de terminaison.|
