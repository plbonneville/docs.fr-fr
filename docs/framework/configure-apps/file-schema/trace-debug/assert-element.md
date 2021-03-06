---
title: '&lt;Assert&gt; élément'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ab1644d23e4d6d78b62e701902e5ec39e134b38b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltassertgt-element"></a>&lt;Assert&gt; élément
Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.  
  
 \<configuration>  
\<System.Diagnostics >  
\<Assert >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`assertuienabled`|Attribut facultatif.<br /><br /> Spécifie si pour afficher un boîte de message lorsque le **Debug.Assert** prend la valeur de méthode **false**.|  
|`logfilename`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier à écrire le message se **Debug.Assert** prend la valeur de **false**.|  
  
## <a name="assertuienabled-attribute"></a>Attribut d’AssertUiEnabled  
  
|Value|Description|  
|-----------|-----------------|  
|`true`|Affiche la boîte de message. Il s'agit de la valeur par défaut.|  
|`false`|Ne pas afficher la boîte de message.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="remarks"></a>Notes  
 Les deux attributs dans le  **\<assert >** élément sont facultatifs. Vous pouvez désactiver les boîtes de message sans spécifier de fichier pour écrire les messages, ou vous pouvez spécifier un fichier pour écrire des messages tout en laissant les messages activés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver l’affichage des messages lorsque vous appelez **Debug.Assert** et écrire les messages dans `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.Debug>  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
