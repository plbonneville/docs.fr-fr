---
title: Fiabilité
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="reliability"></a>Fiabilité
Il est important que l’exécution de code dans les environnements serveur tels que SQL Server puisse vous protéger des exceptions asynchrones. La fiabilité, comme nous allons le voir ici, ne se rapporte pas à SQL Server, mais à l’écriture de code pour tout hôte se trouvant dans un environnement .NET Framework 2.0. Toutefois, étant donné que SQL Server est le premier service qui recourt autant aux nouvelles fonctionnalités de fiabilité de la version 2.0, nous l’avons utilisé comme exemple.  
  
 Les consignes d’exécution de code sont plus strictes pour SQL Server que pour les autres environnements serveur, en raison de l’opération stable de SQL Server relative à la consommation de ressources.  Les exceptions <xref:System.OutOfMemoryException> et <xref:System.Threading.ThreadAbortException> ne sont pas rares dans l’environnement SQL Server. Ces instructions sont globalement moins axées sur la fiabilité que sur la possibilité, pour du code managé entièrement fiable, d’échouer normalement lors d’un recyclage au niveau d’<xref:System.AppDomain>, qui constitue le principal moyen de maintenir la cohérence et la disponibilité du serveur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Attributs de programmation et de protection des hôtes SQL Server](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Explique comment l’attribut <xref:System.Security.Permissions.HostProtectionAttribute> est utilisé par SQL Server pour limiter l’exécution du code managé.  
  
 [Bonnes pratiques relatives à la fiabilité](../../../docs/framework/performance/reliability-best-practices.md)  
 Fournit des instructions pour l’écriture d’un code répondant aux exigences de fiabilité.  
  
 [Régions d’exécution limitée](../../../docs/framework/performance/constrained-execution-regions.md)  
 Décrit la fonction et le comportement des régions d’exécution limitée (CER).  
  
## <a name="reference"></a>Référence  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
