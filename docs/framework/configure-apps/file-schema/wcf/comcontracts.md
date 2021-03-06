---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: b44c09e7e32129ba21834f7fbb8dc4699904e46b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
La section de configuration `comContracts` contient des éléments qui vous permettent de spécifier différentes propriétés d'un contrat de service d'intégration COM+.  
  
## <a name="specifying-namespace-and-contract"></a>Spécification d'espace de noms et de contrat  
 Contrats de service d’intégration COM + sont actuellement restreints à le «http://tempuri.org« espace de noms, et le nom de contrat est dérivé de l’interface COM de prise en charge. Toutefois, vous pouvez en spécifier d'autres à l'aide de la section `comContracts` du fichier de configuration.  
  
 Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms et le nom du contrat de service, aussi bien qu'une option pour mettre en vigueur l'utilisation sur les liaisons de session.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.  
  
 Lorsque cette section est vide, l'initialisation de service applique un espace de noms et un nom de contrat par défaut à partir de l'ID d'interface COM de prise en charge.  
  
 En outre, vous pouvez utiliser la [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) élément pour spécifier les méthodes COM + exposées lorsque l’interface sur un composant COM + est exposée comme un service Web. Vous pouvez également utiliser le [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) pour spécifier les types persistants utilisés dans l’intégration. Enfin, vous pouvez utiliser la [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) élément à inclure défini Types utilisateur (UDT) qui doivent être inclus dans le contrat de service.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Intégration à des applications COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Guide pratique pour configurer des paramètres de service COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
