---
title: 'Dans CustomPeerResolverService : Inscriptions des clients'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 1f8b6f5ac3a41fdc7f817553693b0621ee0ea3de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Dans CustomPeerResolverService : Inscriptions des clients
Chaque nœud de la maille publie ses informations sur le point de terminaison sur le service de résolution par le biais de la fonction `Register`. Le service de résolution stocke ces informations comme un enregistrement d'inscription. Cet enregistrement contient un identificateur unique (RegistrationID) et les informations sur le point de terminaison (PeerNodeAddress) concernant le nœud.  
  
## <a name="stale-records-and-expiration-time"></a>Enregistrements périmés et heure d'expiration  
 Dans l'idéal, lorsqu'un nœud quitte la maille, il appelle la fonction `Unregister`, qui entraîne la suppression de l'entrée de l'inscription par le service de résolution. Quelquefois, les nœuds sont arrêtés ou deviennent inaccessibles avant l'appel de `Unregister`, laissant derrière un enregistrement d'inscription périmé.  
  
 Les enregistrements périmés dans votre service de résolution peuvent entraîner l'échec des connexions. Si un nœud qui essaie de se connecter à une maille reçoit des informations de connexion périmées du service de résolution, l'établissement de la liaison avec la maille peut prendre plus de temps. Les enregistrements périmés occupent également de l'espace en mémoire. Sans un processus de nettoyage efficace, le cache dans lequel sont stockées les inscriptions pourrait finir par être saturé, entraînant alors l'échec du service de résolution.  
  
 Le <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> marque chaque enregistrement avec une heure d'expiration (DateTime) et stocke cette information dans le cadre de l'enregistrement. Le service utilise cette heure d'expiration pour identifier les enregistrements périmés. Les implémentations personnalisées devraient se comporter de manière semblable.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval et CleanupInterval  
 La propriété `RefreshInterval` du <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> définit le délai de validité des enregistrements d'inscription longs dans la table de recherche d'inscription du service. Lorsque le délai défini par cette propriété pour un enregistrement donné a expiré, l'enregistrement en question est périmé et est marqué en vue de sa suppression.  
  
 La propriété `CleanupInterval` du <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> indique au service l'intervalle de recherche et de suppression des enregistrements d'inscription périmés. La valeur de `CleanupInterval` doit être supérieure ou égale à la valeur `RefreshInterval` définie sur le service.  
  
 Pour implémenter votre propre service de résolution, vous devez écrire une fonction de maintenance qui supprime les enregistrements d'inscription périmés. Pour ce faire, plusieurs méthodes sont possibles :  
  
-   **Maintenance périodique**: définir une minuterie périodique et parcourez votre magasin de données à supprimer les anciens enregistrements. Le <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> utilise cette approche.  
  
-   **Suppression passive**: au lieu de rechercher activement les enregistrements périmés à intervalles réguliers, vous pouvez identifier et supprimer les enregistrements obsolètes lorsque votre service exécute déjà une autre fonction. Cela peut ralentir potentiellement le temps de réponse aux demandes des clients de programme de résolution, mais il élimine la nécessité de définir une minuterie, et peut être plus efficace si peu de nœuds sont supposés quitter la maille sans appeler `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime et Refresh  
 Lorsqu'un nœud s'inscrit auprès d'un service de résolution, il reçoit de ce dernier un objet <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo>. Cet objet a une propriété `RegistrationLifetime` qui indique au nœud combien de temps il reste avant que l'inscription expire et sa suppression par le service de résolution. Par exemple, si `RegistrationLifetime` est égal à 2 minutes, le nœud doit appeler `Refresh` dans moins de 2 minutes afin de garantir que l'enregistrement reste actualisé et ne soit pas supprimé. Lorsque le service de résolution reçoit une demande `Refresh`, il examine l'enregistrement et réinitialise l'heure d'expiration. Refresh retourne un objet <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> avec une propriété `RegistrationLifetime`.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes de résolution d’homologue](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
