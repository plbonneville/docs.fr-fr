---
title: '&lt;Routage&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt"></a>&lt;Routage&gt;

Représente une section de configuration pour définir un ensemble de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que le routage des tables qui définissent les points de terminaison cible à envoyer des messages lorsqu’un filtre correspond.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<routage >**

## <a name="syntax"></a>Syntaxe

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun

### <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<filtres >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Contient un ensemble de filtres de routage qui déterminent que le type de MessageFilter de Windows Communication Foundation (WCF) sera utilisé lors de l’évaluation des messages entrants. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond. |

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| **\<système. ServiceModel >** | Élément racine de tous les éléments de configuration WCF. |

## <a name="see-also"></a>Voir aussi

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
