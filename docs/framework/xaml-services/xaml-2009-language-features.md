---
title: "Fonctionnalités de langage XAML 2009"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447ba37330e8027d86fd24239a8aca2461dce8d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-2009-language-features"></a>Fonctionnalités de langage XAML 2009
XAML 2009 est l'abréviation désignant les nouvelles fonctionnalités du langage XAML qui étendent la spécification du langage XAML existante. XAML 2009 introduit plusieurs nouvelles directives et constructions. Il s’agit notamment des éléments suivants :[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md); [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md); ainsi que les types intégrés pour les primitives de langage courantes (par exemple, `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Prise en charge de XAML 2009 dans WPF et Visual Studio  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage WPF. Le code XAML compilé par balisage et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés de langage et fonctionnalités XAML 2009.  
  
 Notez que les techniques existantes de chargement du code XAML libre dans WPF peuvent également avoir des restrictions de sécurité et d'accès aux types CLR et au système de type qui sont plus restrictives que pour le code XAML compilé par balisage. Pour plus d'informations, consultez [Sécurité (WPF)](../../../docs/framework/wpf/security-wpf.md) ou [Stratégie de sécurité de WPF - ingénierie de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 introduit également des fonctionnalités supplémentaires qui modifient les constructions XAML 2006 précédentes ou les formes de balisage de base.  
  
### <a name="xkey-as-an-object-element"></a>x:Key en tant qu'élément objet  
 XAML 2009 peut prendre en charge `x:Key` en tant qu'objet (élément de propriété qui a une valeur d'élément objet) ; toutefois, XAML 2006 prenait uniquement en charge `x:Key` en tant qu'attribut. Consultez la section « XAML 2009 » de la rubrique [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns sur les éléments de propriété  
 XAML 2009 peut prendre en charge les définitions d'espace de noms (xmlns) XAML sur les éléments de propriété ; toutefois, XAML 2006 prend uniquement en charge les définitions xmlns sur les éléments objet.  
  
### <a name="event-attributes"></a>Attributs d'événement  
 Pour les attributs qui sont soutenus par des événements, XAML 2006 suppose que la compilation du balisage est impliquée et soumet les événements à la compilation du balisage. XAML 2009 prend en charge une forme de balisage ressemblant à une extension de balisage, ce qui diffère la connexion d'événements jusqu'au moment de l'analyse à l'exécution et du chargement du code XAML. Toutefois, les applications WPF et les scénarios XAML pour l'interface utilisateur WPF n'utilisent généralement pas cette fonction. WPF et son implémentation de XAML 2006 utilisent la combinaison de la connexion du gestionnaire d'événements pour les événements routés définis au niveau d' <xref:System.Windows.UIElement> et de l'étape de son compilateur de balisage pour une grande partie du traitement de ses attributs d'événement. Le compilateur de balisage prétraite également les attributs d'événement se trouvant dans le code XAML où les actions de génération déclarent que le compilateur de balisage est utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
