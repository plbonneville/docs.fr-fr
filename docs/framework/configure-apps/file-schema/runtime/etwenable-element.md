---
title: '&lt;etwEnable&gt; élément'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 267a4a29282881d18201d0cb2062e91b4ff974a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt; élément
Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.  
  
 \<configuration > élément  
\<runtime > élément  
\<etwEnabled >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si ETW doit être activé.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Activer ETW. Il s’agit de la valeur par défaut pour les versions de Windows qui commence avec les systèmes d’exploitation Windows Vista et Windows Server 2008.|  
|False|Désactiver ETW. Il s’agit de la valeur par défaut pour les versions antérieures de Windows.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À compter de Windows Vista, ETW est activé par défaut. Utilisez cet élément pour désactiver ETW pour une application. Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.  
  
> [!NOTE]
>  ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre du Registre. Consultez [contrôle de l’enregistrement .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer le suivi ETW pour une application.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Contrôle de l’enregistrement .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
