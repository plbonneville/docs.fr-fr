---
title: Encodage de message
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: cdfa83b722492a8b2a7b118ff70134916ed824fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="message-encoding"></a>Encodage de message
L'encodage est le processus de transformation d'un jeu de caractères Unicode en une séquence d'octets. Le décodage est le processus inverse. Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).  
  
 La section de configuration `binaryMessageEncoding` spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML binaires. L'encodeur de message binaire encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble. Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS-* est perdue.  
  
 La section de configuration `mtomMessageEncoding` spécifie l'encodage de caractères et le suivi des versions de message utilisés pour un message employant un encodage MTOM (Message Transmission Optimization Mechanism). MTOM est une technologie efficace pour la transmission de données binaires dans les messages de Windows Communication Foundation (WCF). L'encodeur MTOM tente de parvenir à un équilibre entre rendement et interopérabilité. L'encodage MTOM transmet la plupart du XML sous forme textuelle, mais optimise les grands blocs de données binaires en les transmettant tels quels, sans conversion en texte.  
  
 La section de configuration `textMessageEncoding` spécifie un encodeur de texte utilisé pour créer des messages textuels sur le câble. Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-*. Les services Web ou les clients de ces services comprennent généralement le XML textuel. Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Sélection d’un encodeur de message](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
