---
title: "Utilisation d&#39;un programme de r&#233;solution de contrat de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Utilisation d&#39;un programme de r&#233;solution de contrat de donn&#233;es
Un programme de résolution de contrat de données vous permet de configurer des types connus de manière dynamique.Les types connus sont nécessaires lors de la sérialisation ou de la désérialisation d'un type non attendu par un contrat de données.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les types connus, consultez [Types connus de contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).Les types connus sont généralement spécifiés statiquement.Cela signifie que vous devez connaître tous les types possibles qu'une opération peut recevoir pendant son implémentation.Voici les scénarios où cela n'est pas vrai et où il est important de pouvoir spécifier les types connus de façon dynamique.  
  
## Création d'un programme de résolution de contrat de données  
 La création d'un programme de résolution de contrat de données implique l'implémentation de deux méthodes, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> et <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.Ces deux méthodes implémentent des rappels utilisés respectivement lors de la sérialisation et de la désérialisation.La méthode <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> est appelée lors de la sérialisation, prend un type de contrat de données et le mappe à un nom et espace de noms `xsi:type`.La méthode <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> est appelée lors de la désérialisation, prend un nom et espace de noms `xsi:type` et le résout en type de contrat de données.Ces deux méthodes ont un paramètre `knownTypeResolver` qui peut être utilisé pour utiliser le programme de résolution de type connu par défaut dans votre implémentation.  
  
 L'exemple suivant indique comment implémenter un objet <xref:System.Runtime.Serialization.DataContractResolver> pour un mappage sur et à partir d'un type de contrat de données nommé `Customer`, dérivé d'un type de contrat de données `Person`.  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 Une fois que vous avez défini un objet <xref:System.Runtime.Serialization.DataContractResolver>, vous pouvez l'utiliser en le transmettant au constructeur <xref:System.Runtime.Serialization.DataContractSerializer>, comme indiqué dans l'exemple suivant.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Vous pouvez spécifier un objet <xref:System.Runtime.Serialization.DataContractSerializer> dans un appel aux méthodes <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> ou <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A>, comme indiqué dans l'exemple suivant.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
  
```  
  
 Vous pouvez également le définir sur l'objet <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comme le montre l'exemple suivant.  
  
```  
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
  
```  
  
 Vous pouvez spécifier de façon déclarative un programme de résolution de contrat de données en implémentant un attribut qui peut être appliqué à un service.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] l'exemple [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md).Cet exemple implémente un attribut appelé « KnownAssembly » qui ajoute un programme de résolution de contrat de données personnalisé au comportement du service.  
  
## Voir aussi  
 [Types connus de contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [DataContractSerializer, exemple](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)   
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)