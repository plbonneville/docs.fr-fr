---
title: 'Comment : référencer des certificats X.509 de manière cohérente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: efc4fb399224de7f03c6bffb606178184de1d467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Comment : référencer des certificats X.509 de manière cohérente
Vous pouvez identifier un certificat de plusieurs manières : par le hachage du certificat, par l'émetteur et le numéro de série ou par l'identificateur de la clé du sujet. L'identificateur de la clé du sujet fournit une identification unique de la clé publique du sujet du certificat et sert souvent dans le cadre des signatures numériques XML. La valeur de cet identificateur fait habituellement partie du certificat X.509 sous une *extension de certificat X.509*. Windows Communication Foundation (WCF) a une valeur par défaut *style de référencement* qui utilise l’émetteur et le numéro de série si l’extension SKI est manquante sur le certificat. Si le certificat contient l’extension de l’identificateur, le style de référencement utilise par défaut l’identificateur pour pointer vers le certificat. Si à mi-chemin via le développement d’une application, vous passez de certificats qui n’utilisent pas l’extension SKI pour les certificats qui utilisent l’extension SKI, le style de référencement utilisé dans les messages générés par WCF change également.  
  
 Si un style de référencement cohérent est requis indépendamment de la présence de l’extension de l’identificateur de la clé du sujet, il est possible de configurer ce style de référencement souhaité comme l’illustre le code suivant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un élément de liaison de sécurité personnalisé qui utilise un seul style de référencement cohérent, le nom de l’émetteur et le numéro de série.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les espaces de noms suivants sont requis pour compiler le code :  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
