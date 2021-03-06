---
title: Fédération
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: d69de8c01a23eff5314220a10a51f6487080df41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="federation"></a>Fédération
Cette rubrique fournit une brève vue d'ensemble du concept de sécurité fédérée. Elle décrit également la prise en charge de Windows Communication Foundation (WCF) pour déployer des architectures de sécurité fédérée. Pour un exemple d’application qui illustre la fédération, consultez [Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Définition de sécurité fédérée  
 La sécurité fédérée permet une séparation nette entre le service auquel un client accède et les procédures d'authentification et d'autorisation associées. La sécurité fédérée permet également la collaboration sur plusieurs systèmes, réseaux et organisations dans les différents domaines de confiance.  
  
 WCF fournit la prise en charge pour la création et déploiement de systèmes distribués qui utilisent la sécurité fédérée.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Éléments d'une architecture de sécurité fédérée  
 L'architecture de sécurité fédérée a trois éléments clés, tel qu'indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|Domaine|Unité unique de confiance ou d'administration de sécurité. Un domaine classique peut inclure une organisation unique.|  
|Fédération|Collection de domaines qui ont établi la confiance. Le niveau de confiance peut varier, mais il inclut en général l’authentification et presque toujours l’autorisation. Une fédération classique peut inclure un certain nombre d'organisations qui ont établi la confiance pour l'accès partagé à un ensemble de ressources.|  
|Service d'émission de jeton de sécurité (STS, Security Token Service)|Service Web qui émet des jetons de sécurité ; autrement dit, fait des assertions en fonction de la preuve qu'il approuve, à quiconque l'approuve. Il constitue la base de l'échange de confiance entre les domaines.|  
  
### <a name="example-scenario"></a>Exemple de scénario  
 L'illustration suivante présente un exemple de sécurité fédérée.  
  
 ![Fédération](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Ce scénario inclut deux organisations : A et B. L'organisation B a une ressource Web (un service Web) que certains utilisateurs de l'organisation A trouvent utile.  
  
> [!NOTE]
>  Cette section utilise les termes du contrat *ressource*, *service*, et *service Web* indifféremment.  
  
 En général, l'organisation B requiert qu'un utilisateur de l'organisation A fournisse des formulaires d'authentification valides avant d'accéder au service. De plus, l'organisation peut également requérir que l'utilisateur soit autorisé à accéder à la ressource spécifique en question. L'une des méthodes pour résoudre ce problème et permettre aux utilisateurs de l'organisation A d'accéder à la ressource de l'organisation B est la suivante :  
  
-   Les utilisateurs de l'organisation A enregistrent leurs informations d'identification (nom d'utilisateur et mot de passe) auprès de l'organisation B.  
  
-   Pendant l'accès aux ressources, les utilisateurs de l'organisation A présentent leurs informations d'identification à l'organisation B et sont authentifiés avant d'accéder à la ressource.  
  
 Cette approche a trois inconvénients significatifs :  
  
-   L'organisation B doit gérer les informations d'identification des utilisateurs de l'organisation A, outre la gestion de ses utilisateurs internes.  
  
-   Les utilisateurs de l'organisation A doivent gérer un ensemble d'informations d'identification supplémentaire (autrement dit, se souvenir d'un nom d'utilisateur et d'un mot de passe supplémentaires) outre les informations d'identification qu'ils utilisent habituellement pour accéder aux ressources dans l'organisation A. Cela favorise la pratique qui consiste à utiliser des noms d'utilisateur et mots de passe identiques au niveau de plusieurs sites de service, ce qui est une mesure de sécurité faible.  
  
-   L'architecture n'évolue pas car plusieurs organisations perçoivent la ressource de l'organisation B comme étant utile.  
  
 L'autre approche, qui résout les inconvénients précédemment mentionnés, consiste à utiliser la sécurité fédérée. Dans cette approche, les organisations A et B établissent une relation de confiance et utilisent le STS pour permettre l'échange de la confiance établie.  
  
 Dans une architecture de sécurité fédérée, les utilisateurs de l'organisation A savent que s'ils souhaitent accéder au service Web de l'organisation B, ils doivent présenter un jeton de sécurité valide provenant du STS à l'organisation B, qui authentifie et autorise leur accès au service spécifique.  
  
 Lorsqu'ils contactent le STS B, les utilisateurs reçoivent un autre niveau d'indirection de la stratégie associée au STS. Ils doivent présenter un jeton de sécurité valide provenant du STS A (autrement dit, le domaine de confiance client) pour que le STS B puisse leur délivrer un jeton de sécurité. C'est un corollaire de la relation de confiance établie entre les deux organisations et cela implique que l'organisation B n'a pas à gérer des identités pour les utilisateurs de l'organisation A. Dans la pratique, le STS B a en général un `issuerAddress` et un `issuerMetadataAddress` null. Pour plus d’informations, consultez [Comment : configurer un émetteur Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Dans ce cas, le client consulte une stratégie locale pour localiser STS A. Cette configuration est appelée *fédération de domaine d’accueil* et elle évolue mieux car STS B n’a pas à mettre à jour les informations sur le STS A.  
  
 Les utilisateurs contactent ensuite le STS de l'organisation A et obtiennent un jeton de sécurité en présentant les informations d'identification qu'ils utilisent habituellement pour accéder aux autres ressources de l'organisation A. Cela évite aux utilisateurs d'avoir à gérer plusieurs ensembles d'informations d'identification ou à utiliser le même ensemble au niveau de plusieurs sites de service.  
  
 Une fois que les utilisateurs obtiennent un jeton de sécurité du STS A, ils présentent le jeton au STS B. L'organisation B continue à procéder à l'autorisation des demandes des utilisateurs et leur envoie un jeton de sécurité provenant de son propre jeu. Les utilisateurs peuvent ensuite présenter leur jeton à la ressource de l'organisation B et accéder au service.  
  
## <a name="support-for-federated-security-in-wcf"></a>Prise en charge de la sécurité fédérée dans WCF  
 WCF fournit la prise en charge des clés en main pour déployer des architectures de sécurité fédérée via la [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Le [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) élément fournit pour une liaison sécurisée, fiable et interopérable qui implique l’utilisation de HTTP comme mécanisme de transport sous-jacent pour le style de communication demande-réponse, emploi en tant que le format de câble d’encodage de texte et XML.  
  
 L’utilisation de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) dans la sécurité fédérée scénario peut être dissocié en deux phases logiquement indépendantes, comme décrit dans les sections suivantes.  
  
### <a name="phase-1-design-phase"></a>Phase 1 : phase de conception  
 Pendant la phase de conception, le client utilise le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour lire la stratégie de point de terminaison de service expose et rassembler des exigences d’authentification et d’autorisation du service. Les proxys appropriés sont construits pour créer le modèle de communication de sécurité fédérée suivant au niveau du client :  
  
-   Procurez-vous un jeton de sécurité auprès du STS du domaine de confiance du client.  
  
-   Présentez le jeton au STS du domaine de confiance du service.  
  
-   Procurez-vous un jeton de sécurité auprès du STS du domaine de confiance du service.  
  
-   Présentez le jeton au service pour accéder au service.  
  
### <a name="phase-2-run-time-phase"></a>Phase 2 : phase d'exécution  
 Pendant la phase d’exécution, le client instancie un objet de la classe de client WCF et effectue un appel à l’aide du client WCF. L’infrastructure sous-jacente de WCF gère les étapes précédemment mentionnées dans le modèle de communication de sécurité fédérée et permet au client de consommer le service de façon transparente.  
  
## <a name="sample-implementation-using-wcf"></a>Exemple d'implémentation à l'aide de WCF  
 L’illustration suivante montre un exemple d’implémentation d’une architecture de sécurité fédérée à l’aide de la prise en charge native de WCF.  
  
 ![Sécurité fédérée dans WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Exemple MyService  
 Le service `MyService` expose un point de terminaison unique via `MyServiceEndpoint`. L’illustration suivante présente l’adresse, la liaison et le contrat associés au point de terminaison.  
  
 ![Fédération](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")  
  
 Le point de terminaison de service `MyServiceEndpoint` utilise le [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et nécessite un jeton de sécurité Assertions Markup Language (SAML) valide avec un `accessAuthorized` revendication émise par le STS B. Cela est spécifié de façon déclarative dans la configuration du service.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Un point subtil doit être noté concernant les revendications requises par `MyService`. La deuxième figure indique que `MyService` requiert un jeton SAML avec la revendication `accessAuthorized`. Pour être plus précis, cela spécifie le type de revendication que `MyService` requiert. Le nom qualifié complet de ce type de revendication est http://tempuri.org:accessAuthorized (ainsi que l’espace de noms associé), qui est utilisé dans le fichier de configuration de service. La valeur de cette revendication indique sa présence et elle est supposée être définie à `true` par le STS B.  
  
 Pendant l'exécution, cette stratégie est appliquée par la classe `MyServiceOperationRequirement` implémentée dans le cadre de `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 L'illustration suivante présente le STS B. Comme indiqué précédemment, un service d'émission de jeton de sécurité (STS) est également un service Web et peut avoir ses points de terminaison associés, sa stratégie, etc.  
  
 ![Fédération](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B expose un point de terminaison unique appelé `STSEndpoint` qui permet de demander des jetons de sécurité. Plus précisément, le STS B émet des jetons SAML avec la revendication `accessAuthorized`, qui peuvent être présentés au niveau du site de service `MyService` permettant d'accéder au service. Toutefois, le STS B requiert que les utilisateurs présentent un jeton SAML valide émis par le STS A qui contient la revendication `userAuthenticated`. Cela est spécifié de façon déclarative dans la configuration de STS.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Là encore, la `userAuthenticated` revendication est le type de revendication est requis par STS B. Le nom qualifié complet de ce type de revendication est http://tempuri.org:userAuthenticated (ainsi que l’espace de noms associé), qui est utilisé dans le fichier de configuration STS. La valeur de cette revendication indique sa présence et elle est supposée être définie à `true` par le STS A.  
  
 Pendant l'exécution, la classe `STS_B_OperationRequirement` applique cette stratégie, qui est implémentée dans le cadre du STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Si le contrôle d'accès est clair, le STS B émet un jeton SAML avec la revendication `accessAuthorized`.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 L'illustration suivante présente le STS A.  
  
 ![Fédération](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 À l'instar du STS B, le STS A est également un service Web qui émet des jetons de sécurité et expose un point de terminaison unique à cette fin. Toutefois, il utilise une liaison différente (`wsHttpBinding`) et requiert que les utilisateurs présentent un [!INCLUDE[infocard](../../../../includes/infocard-md.md)] valide avec une revendication `emailAddress`. En réponse, il émet des jetons SAML avec la revendication `userAuthenticated`. Cela est spécifié de façon déclarative dans la configuration de service.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Pendant l'exécution, la classe `STS_A_OperationRequirement` applique cette stratégie, qui est implémentée dans le cadre du STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Si l'accès est `true`, le STS A émet un jeton SAML avec la revendication `userAuthenticated`.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Client au niveau de l'organisation A  
 L'illustration suivante présente le client au niveau de l'organisation A, ainsi que les étapes impliquées dans le lancement d'un appel de service `MyService`. Les autres composants fonctionnels sont également inclus par souci d'exhaustivité.  
  
 ![Fédération](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Récapitulatif  
 La sécurité fédérée fournit une division nette de la responsabilité et permet de générer des architectures de service sécurisées et évolutives. En tant que plateforme de générer et déployer des applications distribuées, WCF fournit la prise en charge native pour implémenter la sécurité fédérée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)
