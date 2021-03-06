---
title: Bien démarrer avec C# et Visual Studio Code - Guide C#
description: Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: d4ee1c9ef66ef61156453786f65d16470d7a5ea2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Bien démarrer avec C# et Visual Studio Code

.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS. Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).

## <a name="prerequisites"></a>Prérequis

1. Installez [Visual Studio Code](https://code.visualstudio.com/).
2. Installez le [SDK .NET Core](https://www.microsoft.com/net/download/core).
3. Installez l’[extension C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pour Visual Studio Code. Pour plus d’informations sur l’installation d’extensions pour Visual Studio Code, consultez [Place de marché des extensions VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Commençons par un programme « Hello World » simple sur .NET Core :

1. Ouvrez un projet :

    * Ouvrez Visual Studio Code.
    * Cliquez sur l’icône Explorer dans le menu de gauche, puis sur **Ouvrir le dossier**.
    * Sélectionnez **Fichier** > **Ouvrir le dossier** dans le menu principal pour ouvrir le dossier dans lequel vous souhaitez que votre projet C# se trouve et cliquez sur **Sélectionner le dossier**. Dans notre exemple, nous créons un dossier pour notre projet nommé *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Initialiser un projet C# :
    * Ouvrez le terminal intégré à partir de Visual Studio Code en sélectionnant **Vue** > **Terminal intégré** dans le menu principal.
    * Dans la fenêtre de Terminal, tapez `dotnet new console`.
    * Cette commande crée un fichier `Program.cs` dans votre dossier avec un simple programme « Hello World » déjà écrit, ainsi qu’un fichier projet C# nommé `HelloWorld.csproj`.

      ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnetnew.png)

3. Résolution des ressources de génération :

    * Pour **.NET Core 1.x**, tapez `dotnet restore`. Exécuter `dotnet restore` vous donne accès aux packages .NET Core qui sont nécessaires pour générer votre projet.

      ![La commande dotnet restore](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Exécutez le programme Hello World :

    * Tapez `dotnet run`. 

      ![La commande dotnet run](media/with-visual-studio-code/dotnetrun.png)

Vous pouvez également regarder un court didacticiel vidéo pour plus d’informations sur la configuration sur [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Débogage

1. Ouvrez *Program.cs* en cliquant dessus. La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) se charge dans l’éditeur.

    ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code doit vous inviter à ajouter les ressources manquantes pour générer et déboguer votre application. Sélectionnez **Oui**. 

    ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

3. Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.

    ![Ouvrez l'onglet Déboguer](media/with-visual-studio-code/opendebug.png)

4. Cherchez la flèche verte en haut du volet. Assurez-vous que `.NET Core Launch (console)` est sélectionné dans la liste déroulante à côté du volet.

    ![Sélection de .NET Core](media/with-visual-studio-code/selectcore.png)

5. Ajoutez un point d’arrêt à votre projet en cliquant sur la **marge de l’éditeur**, qui est l’espace à gauche des numéros de ligne dans l’éditeur, à côté de la ligne 9.

    ![Définition d'un point d'arrêt](media/with-visual-studio-code/setbreakpoint.png)

6. Pour démarrer le débogage, sélectionnez <kbd>F5</kbd> ou la flèche verte. Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.
    * Pendant le débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.

    ![Exécuter et déboguer](media/with-visual-studio-code/rundebug.png)

7. Cliquez sur la flèche verte en haut pour continuer le débogage, ou sélectionnez le carré rouge en haut pour arrêter.

> [!TIP] 
> Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="see-also"></a>Voir aussi
[Configuration de Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)   
[Débogage dans Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
