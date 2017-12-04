---
title: "Gérer les environnements de production Docker"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 5686dcb0932d4a8580fd5ad3daf9e3f5cf52fff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="manage-production-docker-environments"></a><span data-ttu-id="f3445-104">Gérer les environnements de production Docker</span><span class="sxs-lookup"><span data-stu-id="f3445-104">Manage production Docker environments</span></span>

<span data-ttu-id="f3445-105">Gestion du cluster et l’orchestration est le processus de contrôle d’un groupe d’hôtes.</span><span class="sxs-lookup"><span data-stu-id="f3445-105">Cluster management and orchestration is the process of controlling a group of hosts.</span></span> <span data-ttu-id="f3445-106">Ceci peut impliquer un ajout et suppression d’ordinateurs hôtes à partir d’un cluster, l’obtention d’informations sur l’état actuel des hôtes et des conteneurs et de démarrage et arrêt des processus.</span><span class="sxs-lookup"><span data-stu-id="f3445-106">This can involve adding and removing hosts from a cluster, getting information about the current state of hosts and containers, and starting and stopping processes.</span></span> <span data-ttu-id="f3445-107">Gestion du cluster et orchestration sont étroitement liés à la planification, car le planificateur doit avoir accès à chaque hôte du cluster afin de planifier les services.</span><span class="sxs-lookup"><span data-stu-id="f3445-107">Cluster management and orchestration are closely tied to scheduling because the scheduler must have access to each host in the cluster in order to schedule services.</span></span> <span data-ttu-id="f3445-108">Pour cette raison, le même outil est souvent utilisé pour les deux sens.</span><span class="sxs-lookup"><span data-stu-id="f3445-108">For this reason, the same tool is often used for both purposes.</span></span>

## <a name="container-service-and-management-tools"></a><span data-ttu-id="f3445-109">Outils de gestion des services et des conteneurs</span><span class="sxs-lookup"><span data-stu-id="f3445-109">Container Service and management tools</span></span>

<span data-ttu-id="f3445-110">Service de conteneur fournit un déploiement rapide de solutions de clustering et d’orchestration de conteneur d’open source populaires.</span><span class="sxs-lookup"><span data-stu-id="f3445-110">Container Service provides rapid deployment of popular open-source container clustering and orchestration solutions.</span></span> <span data-ttu-id="f3445-111">Il utilise des images de Docker pour vous assurer que vos conteneurs d’applications sont entièrement portables.</span><span class="sxs-lookup"><span data-stu-id="f3445-111">It uses Docker images to ensure that your application containers are fully portable.</span></span> <span data-ttu-id="f3445-112">En utilisant le Service de conteneur, vous pouvez déployer le contrôleur de domaine/système d’exploitation (développé par mésosphère et Apache Mesos) et Docker Swarm clusters avec des modèles Azure Resource Manager ou le portail Azure pour vous assurer que vous pouvez adapter ces applications à des milliers, même des dizaines de milliers, de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f3445-112">By using Container Service, you can deploy DC/OS (powered by Mesosphere and Apache Mesos) and Docker Swarm clusters with Azure Resource Manager templates or the Azure portal to ensure that you can scale these applications to thousands—even tens of thousands—of containers.</span></span>

<span data-ttu-id="f3445-113">Vous déployez ces clusters à l’aide de groupes de mise à l’échelle de machines virtuelles Azure, et les clusters de tirer parti des offres de mise en réseau et de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="f3445-113">You deploy these clusters by using Azure Virtual Machine Scale Sets, and the clusters take advantage of Azure networking and storage offerings.</span></span> <span data-ttu-id="f3445-114">Pour accéder au Service de conteneur, vous avez besoin d’un abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="f3445-114">To access Container Service, you need an Azure subscription.</span></span> <span data-ttu-id="f3445-115">Avec le Service de conteneur, vous pouvez tirer parti des fonctionnalités de niveau entreprise de Azure tout en conservant la portabilité des applications, y compris au niveau des couches d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="f3445-115">With Container Service, you can take advantage of the enterprise-grade features of Azure while still maintaining application portability, including at the orchestration layers.</span></span>

<span data-ttu-id="f3445-116">Le tableau 6-1 répertorie les outils de gestion courants liés à leurs orchestrators, planificateurs et de plateforme de clustering.</span><span class="sxs-lookup"><span data-stu-id="f3445-116">Table 6-1 lists common management tools related to their orchestrators, schedulers, and clustering platform.</span></span>

<span data-ttu-id="f3445-117">Outils de gestion de Docker tableau 6-1 :</span><span class="sxs-lookup"><span data-stu-id="f3445-117">Table 6-1: Docker management tools</span></span>


| <span data-ttu-id="f3445-118">Outils de gestion</span><span class="sxs-lookup"><span data-stu-id="f3445-118">Management tools</span></span>      | <span data-ttu-id="f3445-119">Description</span><span class="sxs-lookup"><span data-stu-id="f3445-119">Description</span></span>           | <span data-ttu-id="f3445-120">Orchestrators connexes</span><span class="sxs-lookup"><span data-stu-id="f3445-120">Related orchestrators</span></span> |
|-----------------------|-----------------------|-----------------------|
| <span data-ttu-id="f3445-121">Service de conteneur\(gestion de l’interface utilisateur dans le portail Azure)</span><span class="sxs-lookup"><span data-stu-id="f3445-121">Container Service\(UI management in Azure portal)</span></span> | <span data-ttu-id="f3445-122">[Service de conteneur](https://azure.microsoft.com/en-us/services/container-service/) fournit une solution simple pour obtenir démarré moyen [déployer un cluster de conteneur dans Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) selon orchestrators populaires tels que mésosphère DC/OS, Kubernetes et Docker Swarm.</span><span class="sxs-lookup"><span data-stu-id="f3445-122">[Container Service](https://azure.microsoft.com/en-us/services/container-service/) provides an easy to get started way to [deploy a container-cluster in Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) based on popular orchestrators like Mesosphere DC/OS, Kubernetes and Docker Swarm.</span></span> <br /><br /> <span data-ttu-id="f3445-123">Service de conteneur permet d’optimiser la configuration de ces plateformes.</span><span class="sxs-lookup"><span data-stu-id="f3445-123">Container Service optimizes the configuration of those platforms.</span></span> <span data-ttu-id="f3445-124">Vous devez simplement sélectionner la taille, le nombre d’hôtes et le choix des outils d’orchestrator et Service de conteneur gère tout le reste.</span><span class="sxs-lookup"><span data-stu-id="f3445-124">You just need to select the size, the number of hosts, and choice of orchestrator tools, and Container Service handles everything else.</span></span> | <span data-ttu-id="f3445-125">Mésosphère contrôleur de domaine/système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f3445-125">Mesosphere DC/OS</span></span> <br /><br /> <span data-ttu-id="f3445-126">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f3445-126">Kubernetes</span></span> <br /><br /> <span data-ttu-id="f3445-127">Docker essaim</span><span class="sxs-lookup"><span data-stu-id="f3445-127">Docker Swarm</span></span> |
| <span data-ttu-id="f3445-128">Plan de contrôle Universal docker\(en local ou cloud)</span><span class="sxs-lookup"><span data-stu-id="f3445-128">Docker Universal Control Plane\(on-premises or cloud)</span></span> | <span data-ttu-id="f3445-129">[Plan de contrôle Universal docker](https://docs.docker.com/v1.11/ucp/overview/) est la solution de gestion de cluster à l’échelle de l’entreprise à partir de Docker.</span><span class="sxs-lookup"><span data-stu-id="f3445-129">[Docker Universal Control Plane](https://docs.docker.com/v1.11/ucp/overview/) is the enterprise-grade cluster management solution from Docker.</span></span> <span data-ttu-id="f3445-130">Il vous permet de gérer votre cluster à partir d’un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="f3445-130">It helps you manage your entire cluster from a single place.</span></span> <br /><br /> <span data-ttu-id="f3445-131">Plan de contrôle Universal docker est inclus dans le cadre du produit commercial nommé Docker de centre de données qui fournit les Docker Swarm, Docker Universal plan de contrôle et du Registre de confiance de Docker.</span><span class="sxs-lookup"><span data-stu-id="f3445-131">Docker Universal Control Plane is included as part of the commercial product named Docker Datacenter which provides Docker Swarm, Docker Universal Control Plane and Docker Trusted Registry.</span></span> <br /><br /> <span data-ttu-id="f3445-132">Centre de données docker peut être installée localement ou configuré à partir d’un cloud public comme Azure.</span><span class="sxs-lookup"><span data-stu-id="f3445-132">Docker Datacenter can be installed on-premises or provisioned from a public cloud like Azure.</span></span> | <span data-ttu-id="f3445-133">Docker Swarm\(pris en charge par le Service de conteneur)</span><span class="sxs-lookup"><span data-stu-id="f3445-133">Docker Swarm\(supported by Container Service)</span></span> |
| <span data-ttu-id="f3445-134">Docker Cloud\(également appelé Tutum ; cloud SaaS)</span><span class="sxs-lookup"><span data-stu-id="f3445-134">Docker Cloud\(also known as Tutum; cloud SaaS)</span></span> | <span data-ttu-id="f3445-135">[Docker Cloud](https://docs.docker.com/docker-cloud/) est un service de gestion hébergé (SaaS) qui fournit des capacités d’orchestration et un Registre Docker avec la build et des fonctions de test pour les images d’application Dockerized, outils pour vous aider à configurer et gérer votre infrastructure d’hôte, fonctionnalités de déploiement et pour vous aider à automatiser le déploiement de vos images à votre infrastructure concrète.</span><span class="sxs-lookup"><span data-stu-id="f3445-135">[Docker Cloud](https://docs.docker.com/docker-cloud/) is a hosted management service (SaaS) that provides orchestration capabilities and a Docker registry with build and testing facilities for Dockerized application images, tools to help you set up and manage your host infrastructure, and deployment features to help you automate deploying your images to your concrete infrastructure.</span></span> <span data-ttu-id="f3445-136">Vous pouvez vous connecter à votre compte SaaS Docker Cloud à votre infrastructure de l’exécution d’un cluster de Docker Swarm de Service de conteneur.</span><span class="sxs-lookup"><span data-stu-id="f3445-136">You can connect your SaaS Docker Cloud account to your infrastructure in Container Service running a Docker Swarm cluster.</span></span> | <span data-ttu-id="f3445-137">Docker Swarm\(pris en charge par le Service de conteneur)</span><span class="sxs-lookup"><span data-stu-id="f3445-137">Docker Swarm\(supported by Container Service)</span></span> |
| <span data-ttu-id="f3445-138">Marathon de mésosphère\(en local ou cloud)</span><span class="sxs-lookup"><span data-stu-id="f3445-138">Mesosphere Marathon\(on-premises or cloud)</span></span> | <span data-ttu-id="f3445-139">[Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) est une plateforme de conteneur à l’échelle de la production d’orchestration et le planificateur pour du mésosphère contrôleur de domaine/système d’exploitation et Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="f3445-139">[Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) is a production-grade container orchestration and scheduler platform for Mesosphere's DC/OS and Apache Mesos.</span></span> <br /><br /> <span data-ttu-id="f3445-140">Il fonctionne avec Mesos (contrôleur de domaine/système d’exploitation est basé sur Apache Mesos) à long terme de contrôle des services et fournit un [l’interface utilisateur web pour la gestion des processus et le conteneur](https://mesosphere.github.io/marathon/docs/marathon-ui.html).</span><span class="sxs-lookup"><span data-stu-id="f3445-140">It works with Mesos (DC/OS is based on Apache Mesos) to control long-running services and provides a [web UI for process and container management](https://mesosphere.github.io/marathon/docs/marathon-ui.html).</span></span> <span data-ttu-id="f3445-141">Il fournit un outil de gestion de l’interface utilisateur web</span><span class="sxs-lookup"><span data-stu-id="f3445-141">It provides a web UI management tool</span></span> | <span data-ttu-id="f3445-142">Contrôleur de domaine/système d’exploitation de mésosphère\(basée sur Apache Mesos ; pris en charge par le Service de conteneur)</span><span class="sxs-lookup"><span data-stu-id="f3445-142">Mesosphere DC/OS\(Based on Apache Mesos; supported by Container Service)</span></span> |
| <span data-ttu-id="f3445-143">Google Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f3445-143">Google Kubernetes</span></span> | <span data-ttu-id="f3445-144">[Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) couvre l’orchestration, la planification et infrastructure de cluster.</span><span class="sxs-lookup"><span data-stu-id="f3445-144">[Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) spans orchestrating, scheduling, and cluster infrastructure.</span></span> <span data-ttu-id="f3445-145">C’est une plate-forme open source pour l’automatisation des opérations de conteneurs d’applications, de mise à l’échelle et de déploiement pour tous les clusters d’ordinateurs hôtes, en fournissant une infrastructure orientée conteneur.</span><span class="sxs-lookup"><span data-stu-id="f3445-145">It is an open-source platform for automating deployment, scaling, and operations of application containers across clusters of hosts, providing container-centric infrastructure.</span></span> | <span data-ttu-id="f3445-146">Google Kubernetes\(pris en charge par le Service de conteneur)</span><span class="sxs-lookup"><span data-stu-id="f3445-146">Google Kubernetes\(supported by Container Service)</span></span> |

## <a name="azure-service-fabric"></a><span data-ttu-id="f3445-147">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f3445-147">Azure Service Fabric</span></span>

<span data-ttu-id="f3445-148">Un autre choix pour la gestion et de déploiement de cluster est Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="f3445-148">Another choice for cluster-deployment and management is Azure Service Fabric.</span></span> <span data-ttu-id="f3445-149">[Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) est une plate-forme de microservices Microsoft qui inclut l’orchestration de conteneur, ainsi que des développeurs de programmation des modèles pour créer des applications hautement évolutives microservices.</span><span class="sxs-lookup"><span data-stu-id="f3445-149">[Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) is a Microsoft microservices platform that includes container orchestration as well as developer programming models to build highly-scalable microservices applications.</span></span> <span data-ttu-id="f3445-150">L’infrastructure de service prend en charge Docker dans les versions preview Linux en cours, comme dans le [aperçu Service Fabric sur Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)et pour les conteneurs Windows [dans la prochaine version](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).</span><span class="sxs-lookup"><span data-stu-id="f3445-150">Service Fabric supports Docker in current Linux preview versions, as in the [Service Fabric preview on Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere), and for Windows Containers [in the next release](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).</span></span>

<span data-ttu-id="f3445-151">Voici les outils de gestion de l’infrastructure de Service :</span><span class="sxs-lookup"><span data-stu-id="f3445-151">Following are Service Fabric management tools:</span></span>

-   <span data-ttu-id="f3445-152">[Portail Azure pour Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) opérations liées au cluster (création/mise à jour/suppression) un cluster ou de configurer son infrastructure (machines virtuelles, équilibrage de charge, la mise en réseau, etc..)</span><span class="sxs-lookup"><span data-stu-id="f3445-152">[Azure portal for Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) cluster-related operations (create/update/delete) a cluster or configure its infrastructure (VMs, load balancer, networking, etc.)</span></span>

-   <span data-ttu-id="f3445-153">[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) est un outil d’interface utilisateur web spécialisées qui fournit des analyses et certaines opérations sur le cluster Service Fabric à partir du point de vue de nœuds/machines virtuelles et à partir de l’application et les services de point de vue.</span><span class="sxs-lookup"><span data-stu-id="f3445-153">[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) is a specialized web UI tool that provides insights and certain operations on the Service Fabric cluster from the nodes/VMs point of view and from the application and services point of view.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f3445-154">[Précédente] (run-microservices-based-applications-in-production.md) [suivant] (analyse-placées dans des conteneurs-application-services.md)</span><span class="sxs-lookup"><span data-stu-id="f3445-154">[Previous] (run-microservices-based-applications-in-production.md) [Next] (monitor-containerized-application-services.md)</span></span>