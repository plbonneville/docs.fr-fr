---
title: Commande dotnet-add reference - Interface CLI .NET Core
description: La commande dotnet add reference est une option pratique pour ajouter des références entre projets.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a>dotnet-add reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet add reference` : ajoute des références entre projets (P2P).

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet. Une fois que vous avez exécuté la commande, les éléments [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) sont ajoutés au fichier projet.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

`PROJECT_REFERENCES`

Références entre projets (P2P) à ajouter. Spécifiez un ou plusieurs projets. Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-f|--framework <FRAMEWORK>`

Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

## <a name="examples"></a>Exemples

Ajouter une référence de projet :

`dotnet add app/app.csproj reference lib/lib.csproj`

Ajouter plusieurs références de projet au projet dans le répertoire actuel :

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :

`dotnet add app/app.csproj reference **/*.csproj`
