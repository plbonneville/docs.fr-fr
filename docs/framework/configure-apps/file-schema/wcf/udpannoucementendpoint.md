---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: a6dbec19beb3800603bd745bacbd6cbcbcdaa739
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltudpannoucementendpointgt"></a>&lt;udpAnnoucementEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard utilisé par les services pour envoyer des messages d’annonce via une liaison UDP. Il a un contrat fixe et prend en charge deux versions de découverte. De plus, il possède une liaison UDP fixe et une valeur d'adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery version 1.1). Vous pouvez spécifier l'adresse de multidiffusion à utiliser pour l'envoi et la réception de messages d'annonce.  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|discoveryVersion|Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery. Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005. Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello. Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés. Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.|  
|multicastAddress|URI qui spécifie une adresse de multidiffusion à utiliser pour l'envoi et la réception des messages de découverte. La valeur par défaut est représentée par l'adresse de multidiffusion conforme à la spécification du protocole.|  
|name|Chaîne qui spécifie le nom de la configuration du point de terminaison standard. Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Collection de paramètres qui vous permettent de configurer le transport UDP pour le point de terminaison UDP.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre un client à l'écoute d'une annonce sur un transport de multidiffusion UDP avec adresse de multidiffusion par défaut, et sur un transport de multidiffusion UDP avec l'adresse de multidiffusion spécifiée.  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
