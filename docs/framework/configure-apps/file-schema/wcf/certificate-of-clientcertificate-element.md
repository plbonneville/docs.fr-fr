---
title: Élément &lt;certificate&gt; de &lt;clientCertificate&gt;
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 07885f8f1a575ef5b6ccb8d5f91f38a561261183
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a>Élément &lt;certificate&gt; de &lt;clientCertificate&gt;
Spécifie un certificat X.509 utilisé pour signer et chiffrer des messages.  
  
 \<system.ServiceModel>  
\<comportements >  
\<serviceBehaviors>  
\<comportement >  
\<serviceCredentials>  
\<clientCertificate >  
\<certificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509. Le type contenu dans l'attribut doit satisfaire les spécifications du X509FindType spécifié. La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur. Les valeurs valides sont les suivantes :<br /><br /> -LocalMachine : magasin de certificats assigné à l’ordinateur local.<br />-CurrentUser : magasin de certificats assigné à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir. Les valeurs valides sont les suivantes :<br /><br /> -AddressBook : Magasin de certificats pour d’autres utilisateurs.<br />-AuthRoot : Magasin de certificats pour autorités de certification tierces (CAs).<br />-CertificationAuthority : Magasin de certificats pour les autorités de certification intermédiaires (CAs).<br />-Disallowed : Magasin de certificats pour les certificats révoqués.<br />-My : Magasin de certificats pour les certificats personnels.<br />-Root : Magasin de certificats pour autorités de certification racine de confiance (CA).<br />-TrustedPeople : Magasin de certificats pour les personnes de confiance directement et de ressources.<br />-TrustedPublisher : Magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`X509FindType`|Définit le type de recherche X.509 à exécuter. Les valeurs valides sont les suivantes :<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Notes  
 L'élément `<certificate>` est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client. Cela se produit lors de l'utilisation du modèle de communication duplex. Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client. Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client. C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément. Pour plus d’informations sur les services duplex, consultez [Comment : créer un contrat Duplex](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant indique comment rechercher un certificat X.509 approprié ainsi qu'un type de validation personnalisé dans l'élément `<authentication>`.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Guide pratique pour créer un service qui utilise un validateur de certificat personnalisé](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
