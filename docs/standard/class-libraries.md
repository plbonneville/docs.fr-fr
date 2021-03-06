---
title: Bibliothèques de classes .NET
description: Découvrez dans quelle mesure les bibliothèques de classes .NET vous permettent de grouper des fonctionnalités utiles en modules utilisables par plusieurs applications.
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 44d5745daed8539c5dd48b08f9f73edce4da939f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="net-class-libraries"></a>Bibliothèques de classes .NET

Les bibliothèques de classes représentent le concept de [bibliothèque partagée](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pour .NET. Elles vous permettent d’inclure des fonctionnalités utiles dans des modules utilisables par plusieurs applications. Elles peuvent également servir à charger des fonctionnalités qui ne sont pas nécessaires ou connues au démarrage de l’application. Les bibliothèques de classes sont décrites à l’aide du [format de fichier d’assembly .NET](assembly-format.md).

Il existe trois types de bibliothèques de classes que vous pouvez utiliser :

*   Les bibliothèques de classes **spécifiques d’une plateforme** ont accès à toutes les API dans une plateforme donnée (par exemple, .NET Framework, Xamarin iOS), mais sont utilisables uniquement par les applications et les bibliothèques qui ciblent cette plateforme.
*   Les bibliothèques de classes **portables** ont accès à un sous-ensemble d’API et sont utilisables par les applications et les bibliothèques qui ciblent plusieurs plateformes.
*   Les bibliothèques de classes **.NET Standard** sont une fusion du concept de bibliothèques spécifiques d’une plateforme et portables en un seul modèle qui offre le meilleur des deux.

## <a name="platform-specific-class-libraries"></a>Bibliothèques de classes spécifiques d’une plateforme

Les bibliothèques spécifiques d’une plateforme sont liées à une seule implémentation .NET (par exemple, .NET Framework sur Windows) et peuvent donc accepter des dépendances significatives sur un environnement d’exécution connu. Un tel environnement expose un ensemble connu d’API (API .NET et de système d’exploitation), et maintient et expose l’état attendu (par exemple, le Registre Windows).

Les développeurs qui créent des bibliothèques spécifiques d’une plateforme peuvent exploiter pleinement la plateforme sous-jacente. Les bibliothèques ne s’exécutent que sur cette plateforme donnée, ce qui rend inutile les vérifications de plateforme ou d’autres formes de code conditionnel (code d’approvisionnement modulo unique pour plusieurs plateformes).

Les bibliothèques spécifiques d’une plateforme ont été le type de bibliothèque de classes principal du .NET Framework. Même si d’autres implémentations .NET sont apparues, les bibliothèques spécifiques d’une plateforme sont restées le type de bibliothèque prédominant.

## <a name="portable-class-libraries"></a>Bibliothèques de classes portables

Les bibliothèques portables sont prises en charge sur plusieurs implémentations .NET. Elles peuvent toujours accepter des dépendances sur un environnement d’exécution connu, toutefois, il s’agit d’un environnement synthétique généré par l’intersection d’un ensemble d’implémentations .NET concrètes. Cela signifie que les API exposées et les hypothèses de plateformes sont un sous-ensemble de ce qui est disponible pour une bibliothèque spécifique d’une plateforme.

Vous choisissez une configuration de plateforme quand vous créez une bibliothèque portable. Il s’agit de l’ensemble des plateformes que vous devez prendre en charge (par exemple, .NET Framework 4.5+, Windows Phone 8.0+). Plus vous avez de plateformes à prendre en charge, moins vous avez d’API et moins vous pouvez faire d’hypothèses de plateforme, selon le plus petit dénominateur commun. Cette caractéristique peut porter à confusion dans un premier temps, car on pense souvent que « plus, c’est mieux », mais ici plus vous prenez en charge des plateformes et moins vous avez d’API disponibles.

De nombreux développeurs de bibliothèques ont abandonné la production de plusieurs bibliothèques spécifiques d’une plateforme à partir d’une seule source (à l’aide de directives de compilation conditionnelle) au profit des bibliothèques portables. Il existe [plusieurs approches](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) permettant d’accéder à une fonctionnalité spécifique d’une plateforme dans les bibliothèques portables, [bait-and-switch](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) étant la technique la plus répandue à ce stade.

### <a name="net-standard-class-libraries"></a>Bibliothèques de classes .NET Standard

Les bibliothèques .NET Standard remplacent les concepts de bibliothèques spécifiques d’une plateforme et portables. Elles sont spécifiques d’une plateforme en ce sens qu’elles exposent toutes les fonctionnalités de la plateforme sous-jacente (pas de plateforme synthétique ni d’intersection de plateformes). Elles sont portables en ce sens qu’elles fonctionnent sur toutes les plateformes de prise en charge.

.NET Standard expose un ensemble de _contrats_ de bibliothèque. Les implémentations .NET doivent prendre en charge chaque contrat dans son intégralité ou pas du tout. Ainsi, chaque implémentation prend en charge un ensemble de contrats .NET Standard. Le corollaire est que chaque bibliothèque de classes .NET Standard est prise en charge sur les plateformes qui prennent en charge les dépendances de son contrat.

.NET Standard n’expose pas toutes les fonctionnalités du .NET Framework (ce n’est d’ailleurs pas son objectif), toutefois, il expose bien plus d’API que les bibliothèques de classes portables. D’autres API seront ajoutées au fil du temps.

Les plateformes suivantes prennent en charge les bibliothèques .NET Standard :

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Plateforme Windows universelle (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Pour plus d’informations, consultez la rubrique [.NET Standard](net-standard.md).

### <a name="mono-class-libraries"></a>Bibliothèques de classes Mono

Les bibliothèques de classes sont prises en charge sur Mono, y compris les trois types de bibliothèques décrits ci-dessus. Mono a souvent été considéré (à juste titre) comme une implémentation multiplateforme de Microsoft .NET Framework. C’est en partie parce que les bibliothèques .NET Framework spécifiques d’une plateforme peuvent s’exécuter sur le runtime Mono sans modification ou recompilation. Cette caractéristique existait avant la création des bibliothèques de classes portables, elle était donc choisie en priorité pour permettre la portabilité binaire entre le .NET Framework et Mono (même si cela ne fonctionnait que dans un sens).
