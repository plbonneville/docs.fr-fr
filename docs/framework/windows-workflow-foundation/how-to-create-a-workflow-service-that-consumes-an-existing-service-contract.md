---
title: 'Procédure : créer un service de workflow qui utilise un contrat de service existant'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 146b3bba3a880c780644eecd277827823793b5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Procédure : créer un service de workflow qui utilise un contrat de service existant
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] offre une meilleure intégration entre les services Web et les workflows sous la forme du développement de workflow contrat en premier. L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier. L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat.  
  
> [!NOTE]
>  Cette rubrique fournit des instructions pas à pas pour créer un service de workflow contrat en premier. Pour plus d’informations sur le développement de service de workflow contrat en premier, consultez [contrat premier Workflow Service développement](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Création du projet de workflow  
  
1.  Dans Visual Studio, sélectionnez **fichier**, **nouveau projet**. Sélectionnez le **WCF** nœud sous la **c#** nœud dans le **modèles** d’arborescence, puis sélectionnez le **Application de Service de Workflow WCF** modèle.  
  
2.  Nommez le nouveau projet `ContractFirst` et cliquez sur **Ok**.  
  
### <a name="creating-the-service-contract"></a>Création du contrat de service  
  
1.  Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** . Sélectionnez le **Code** nœud sur la gauche et le **classe** modèle situé à droite. Nommez la nouvelle classe `IBookService` et cliquez sur **Ok**.  
  
2.  En haut de la fenêtre de code qui apparaît, ajoutez une instruction Using à `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Remplacez la définition d'exemple de classe par la définition d'interface suivante.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  Générez le projet en appuyant sur **Ctrl + Maj + B**.  
  
### <a name="importing-the-service-contract"></a>Importation du contrat de service  
  
1.  Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **contrat de Service d’importation**. Sous  **\<projet actif >**, ouvrez tous les sous-nœuds et sélectionnez **IBookService**. Cliquez sur **OK**.  
  
2.  Une boîte de dialogue s'ouvre indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées s'afficheront dans la boîte à outils une fois le projet construit. Cliquez sur **OK**.  
  
3.  Générez le projet en appuyant sur **Ctrl + Maj + B**, de sorte que les activités importées s’affichent dans la boîte à outils.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez Service1.xamlx. Le service de workflow apparaît dans le concepteur.  
  
5.  Sélectionnez le **séquence** activité. Dans la fenêtre Propriétés, cliquez sur le **...** bouton dans le **ImplementedContract** propriété. Dans le **éditeur de collections Type** fenêtre qui s’affiche, cliquez sur le **Type** liste déroulante, puis sélectionnez le **rechercher des Types...** entrée. Dans le **rechercher et sélectionner un .net Type** boîte de dialogue, sous  **\<projet actif >**, ouvrez tous les sous-nœuds et sélectionnez **IBookService**. Cliquez sur **OK**. Dans le **éditeur de collections Type** boîte de dialogue, cliquez sur **OK**.  
  
6.  Sélectionnez et supprimez le **ReceiveRequest** et **SendResponse** activités.  
  
7.  Dans la boîte à outils, faites glisser un **Buy_ReceiveAndSendReply** et un **Checkout_Receive** activité sur le **Service séquentiel** activité.
