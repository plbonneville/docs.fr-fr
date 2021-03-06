---
title: Empaquetage de la distribution de .NET Core
description: Découvrez comment empaqueter, nommer et versionner .NET Core pour la distribution.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 63ff542dbde30f8ff72a2d257a16a18b2a9e71b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-distribution-packaging"></a>Empaquetage de la distribution de .NET Core

.NET Core est disponible sur de plus en plus de plateformes ; il est donc utile de savoir comment l’empaqueter, le nommer et le versionner. De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET.

## <a name="disk-layout"></a>Disposition du disque

Une fois installé, .NET Core est constitué de plusieurs composants qui sont présentés comme suit dans le système de fichiers :

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** L’hôte (également appelé « muxer ») a deux rôles distincts : activer un runtime pour lancer une application, et un SDK pour lui distribuer des commandes. L’hôte est un fichier exécutable natif (`dotnet.exe`).

Alors qu’il n’y a qu’un seul hôte, la plupart des autres composants sont dans des répertoires avec version (2,3,5,6). Cela signifie que plusieurs versions peuvent être présentes sur le système, car elles sont installées côte à côte.

- (2) **host/fxr/\<version fxr>** contient la logique de résolution du framework utilisé par l’hôte. L’hôte utilise la dernière version de hostfxr qui est installée. hostfxr est chargé de sélectionner le runtime approprié lors de l’exécution d’une application .NET Core. Par exemple, une application générée pour .NET Core 2.0.0 utilise le runtime 2.0.5 quand il est disponible. De même, hostfxr sélectionne le SDK approprié au cours du développement.

- (3) **sdk/\<version sdk>** Le SDK (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à générer des bibliothèques et des applications .NET Core. Il inclut l’interface CLI, le compilateur Roslyn, MSBuild et les cibles et tâches de génération associées, NuGet, de nouveaux modèles de projet, etc.

- (4) **sdk/NuGetFallbackFolder** contient un cache de packages NuGet utilisés par un SDK lors de l’étape `dotnet restore`.

Le dossier **shared** contient des frameworks. Un framework partagé fournit un ensemble de bibliothèques à un emplacement central, ce qui permet à différentes applications de les utiliser.

- (5) **shared/Microsoft.NETCore.App/\<version runtime>** Ce framework contient le runtime .NET Core et des bibliothèques managées qui le prennent en charge.

- (6,7) **shared/Microsoft.AspNetCore.{App,All}/\<version aspnetcore>** Contient les bibliothèques ASP.NET Core. Les bibliothèques sous `Microsoft.AspNetCore.App` sont développées et prises en charge dans le cadre du projet .NET Core. Les bibliothèques sous `Microsoft.AspNetCore.All` sont un sur-ensemble qui contient également des bibliothèques de tiers.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** sont la licence .NET Core et les licences des bibliothèques de tiers utilisées dans .NET Core.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` est la page man de dotnet. `dotnet` est un lien symbolique vers l’hôte dotnet (1). Ces fichiers sont installés aux emplacements habituels pour l’intégration du système.

## <a name="recommended-packages"></a>Packages recommandés

Le contrôle de version de .NET Core est basé sur les numéros de version `[major].[minor]` du composant runtime.
La version du SDK utilise les mêmes numéros `[major].[minor]` et a un `[patch]` indépendant qui combine la sémantique des fonctionnalités et des correctifs pour le SDK.
Par exemple, SDK version 2.2.302 est la deuxième version du correctif de la troisième version des fonctionnalités du SDK qui prend en charge le runtime 2.2.

Le nom de certains packages inclut une partie du numéro de version. Ceci permet à l’utilisateur final d’installer une version spécifique.
Le reste de la version n’est pas inclus dans le nom de la version. Ceci permet au Gestionnaire de package du système d’exploitation de mettre à jour les packages (par exemple d’installer automatiquement des correctifs de sécurité).

Le tableau suivant indique les packages recommandés.

| Name                                    | Exemple                | Cas d’usage : Installer...           | Contient           | Dépendances                                   | Version            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Dernier SDK pour la version majeure du runtime    |                    | dotnet-sdk-[major].[latestminor]               | \<version sdk>     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | Dernier SDK pour un runtime spécifique |                    | dotnet-sdk-[major].[minor].[latest sdk feat]xx | \<version sdk>     |
| dotnet-sdk-[major].[minor].[sdk feat]xx | dotnet-sdk-2.1.3xx     | Version des fonctionnalités spécifique du SDK    | (3),(4)            | aspnetcore-runtime-[major].[minor]             | \<version sdk>     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | Runtime ASP.NET Core spécifique   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<version du runtime> |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | Runtime spécifique                | (5)                | host-fxr :\<version du runtime>+                   | \<version du runtime> |
| dotnet-host-fxr                         | dotnet-host-fxr        | _dépendance_                    | (2)                | host :\<version du runtime>+                       | \<version du runtime> |
| dotnet-host                             | dotnet-host            | _dépendance_                    | (1),(8),(9),(10)   |                                                | \<version du runtime> |

La plupart des distributions nécessitent que tous les artefacts soient générés à partir de la source. Ceci a un certain impact sur les packages :

- Les bibliothèques de tiers sous `shared/Microsoft.AspNetCore.All` ne peuvent pas être facilement générées à partir de la source. Ce dossier est donc omis du package `aspnetcore-runtime`.

- `NuGetFallbackFolder` est rempli avec des artefacts binaires provenant de `nuget.org`. Il doit rester vide.

Plusieurs packages `dotnet-sdk` peuvent fournir les mêmes fichiers pour le `NuGetFallbackFolder`. Pour éviter des problèmes avec le Gestionnaire de package, ces fichiers doivent être identiques (somme de contrôle, date de modification, etc.).

#### <a name="preview-versions"></a>Préversions

Les chargés de maintenance de packages peuvent décider d’inclure des préversions du framework partagé et du SDK. Les préversions peuvent être fournies avec les packages `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]`. Pour les préversions, la version majeure du package doit être définie sur zéro. De cette façon, la version finale sera installée comme une mise à niveau du package.

#### <a name="patch-packages"></a>Packages de correctifs

Comme une version des correctifs d’un package peut introduire un changement majeur, un chargé de maintenance de packages peut fournir des _packages de correctifs_. Ces packages permettent d’installer une version de correctifs spécifique qui n’est pas automatiquement mise à niveau. Les packages de correctifs doivent être utilisés seulement dans de rares circonstances, car ils ne seront pas mis à niveau avec des correctifs (de sécurité).

Le tableau suivant indique les packages et les **packages de correctifs** recommandés.

| Name                                           | Exemple                  | Contient         | Dépendances                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | dotnet-sdk-[major].[latest sdk minor]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | dotnet-sdk-[major].[minor].[latest sdk feat]xx            |
| dotnet-sdk-[major].[minor].[sdk feat]xx        | dotnet-sdk-2.1.3xx       |                  | dotnet-sdk-[major].[minor].[latest sdk patch]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore-runtime-[major].[minor].[sdk runtime patch]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore-runtime-[majeur].[mineur].[dernier correctif du runtime] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | dotnet-runtime-[majeur].[mineur].[dernier correctif du runtime]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr :\<version du runtime>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | host :\<version du runtime>+                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

Une alternative à l’utilisation de packages de correctifs est _l’épinglage_ des packages à une version spécifique à l’aide du Gestionnaire de package. Pour éviter d’affecter d’autres applications/utilisateurs, de telles applications peuvent être générées et déployées dans un conteneur.

## <a name="building-packages"></a>Génération des packages

Le dépôt https://github.com/dotnet/source-build fournit des instructions sur la création d’un tarball source du SDK .NET Core et de tous ses composants. La sortie du dépôt de builds sources correspond à la disposition décrite dans la première section de cet article.