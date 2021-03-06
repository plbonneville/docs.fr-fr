---
title: Configuration de la sérialisation dans un service de workflow
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configuration de la sérialisation dans un service de workflow
Services de workflow sont des services Windows Communication Foundation (WCF) et avoir la possibilité d’utiliser soit le <xref:System.Runtime.Serialization.DataContractSerializer> (la valeur par défaut) ou le <xref:System.Xml.Serialization.XmlSerializer>. Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération. Lors de la création de services de workflow WCF vous ne spécifiez pas ces contrats dans le code, mais ils sont générés lors de l’exécution par inférence de contrat. Pour plus d’informations sur l’inférence de contrat, consultez [à l’aide de contrats dans le Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>. Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.  
  
 ![Définition du sérialiseur](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Les types connus peuvent également être spécifiés dans des services de workflow. Pour plus d’informations sur les Types connus, consultez [Types connus de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Les types connus peuvent être spécifiés dans le concepteur ou dans du code. Pour spécifier les types courants dans le concepteur, cliquez sur le bouton de sélection en regard de la propriété KnownTypes dans la fenêtre Propriétés pour une activité <xref:System.ServiceModel.Activities.Receive>, comme le montre l'illustration suivante.  
  
 ![Propriété KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 L’Éditeur de collections de types s’affiche et vous permet de rechercher et de spécifier des types connus.  
  
 ![Ajout de Types connus](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Cliquez sur le **ajouter le nouveau type** lien et utilisez la liste déroulante pour sélectionner ou rechercher un type à ajouter à la collection de types connus. Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 Pour voir un exemple de code complet illustrant comment configurer la sérialisation pour un service de flux de travail voir [mise en forme des messages dans les Services de Workflow](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
