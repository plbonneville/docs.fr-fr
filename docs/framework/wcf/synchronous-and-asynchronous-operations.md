---
title: Opérations synchrones et asynchrones
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 0b64d45797babff2da1649fb7469684342e65d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="synchronous-and-asynchronous-operations"></a>Opérations synchrones et asynchrones
Cette rubrique traite de l'implémentation et de l'appel des opérations de service asynchrones.  
  
 De nombreuses applications appellent des méthodes de façon asynchrone, car elles peuvent ainsi continuer à effectuer un travail utile pendant que l'appel de méthode s'exécute. Les services Windows Communication Foundation (WCF) et les clients peuvent participer à des appels d’opération asynchrone à deux niveaux distincts de l’application, qui fournissent [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] encore plus de souplesse pour optimiser le débit est évaluée par rapport à des applications interactivité.  
  
## <a name="types-of-asynchronous-operations"></a>Types d'opérations asynchrones  
 Tous les contrats de service dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], indépendamment des types de paramètres et des valeurs de retour, utilisent des attributs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour spécifier un modèle d'échange de messages particulier entre le client et le service. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] route automatiquement les messages SOAP entrants et sortants vers l'opération de service appropriée ou le code client exécuté.  
  
 Le client possède uniquement le contrat de service qui spécifie le modèle d'échange de messages pour une opération particulière. Les clients peuvent offrir au développeur un modèle de programmation de leur choix, tant que le modèle d'échange de messages sous-jacent est respecté. De même, les services peuvent implémenter des opérations de quelque manière que ce soit, à condition que le modèle de message spécifié soit respecté.  
  
 L'indépendance du contrat de service vis à vis de l'implémentation du service ou du client autorise les types d'exécutions asynchrones suivants dans les applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] :  
  
-   Les clients peuvent appeler de façon asynchrone des opérations de demande/réponse à l'aide d'un échange de messages synchrone.  
  
-   Les services peuvent implémenter de façon asynchrone une opération de demande/réponse à l'aide d'un échange de messages synchrone.  
  
-   Les échanges de messages peuvent être unidirectionnels, indépendamment de l'implémentation du client ou service.  
  
### <a name="suggested-asynchronous-scenarios"></a>Scénarios asynchrones suggérés  
 Utilisez une approche asynchrone dans une implémentation de l'opération de service si celle-ci passe un appel bloquant, par exemple une tâche en E/S. Lorsque vous êtes dans une implémentation d'opération asynchrone, essayez d'appeler des méthodes et des opérations asynchrones pour étendre le chemin d'appel asynchrone aussi loin que possible. Par exemple, appelez `BeginOperationTwo()` à partir d'un `BeginOperationOne()`.  
  
-   Utilisez une approche asynchrone dans une application cliente ou appelante dans les cas suivants :  
  
-   Si vous appelez des opérations à partir d'une application intermédiaire. (Pour plus d’informations sur ces scénarios, consultez [Applications clientes de niveau intermédiaire](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Si vous appelez des opérations à partir d'une page ASP.NET, utiliser des pages asynchrones.  
  
-   Si vous appelez des opérations à partir de n’importe quelle application qui est unique monothread, telle que Windows Forms ou Windows Presentation Foundation (WPF). Lorsque vous utilisez le modèle d'appel asynchrone basé sur des événements, l'événement résultant est déclenché sur le thread d'interface utilisateur, ce qui accroît la réactivité de l'application sans exiger la gestion de plusieurs threads.  
  
-   En général, si vous avez le choix entre un appel synchrone et asynchrone, choisissez l'appel asynchrone.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implémentation d'une opération de service asynchrone  
 Les opérations asynchrones peuvent être implémentées à l'aide d'une des trois méthodes suivantes :  
  
1.  Modèle asynchrone basé sur des tâches  
  
2.  Modèle asynchrone basé sur des événements  
  
3.  Modèle asynchrone IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)  
 Le modèle asynchrone basé sur des tâches constitue le meilleur moyen d’implémenter des opérations asynchrones, car il est le plus facile et le plus simple. Pour utiliser cette méthode, implémentez votre opération de service simplement et spécifiez un type de retour de tâche\<T >, où T est le type retourné par l’opération logique. Par exemple :  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 L’opération SampleMethodTaskAsync retourne Task\<chaîne >, car l’opération logique retourne une chaîne. Pour plus d’informations sur le modèle asynchrone basé sur des tâches, consultez [les modèle asynchrone basé sur les tâches](http://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Lorsque vous utilisez le modèle asynchrone basé sur des tâches, une exception T:System.AggregateException peut être levée si une exception se produit lors de l’attente de la fin de l’opération. Cette exception peut se produire sur le client ou les services.  
  
#### <a name="event-based-asynchronous-pattern"></a>Modèle asynchrone basé sur des événements  
 Un service prenant en charge le modèle asynchrone basé sur des événements possédera une ou plusieurs opérations nommées MethodNameAsync. Ces méthodes peuvent refléter des versions synchrones qui exécutent la même opération sur le thread actuel. La classe peut également posséder un événement MethodNameCompleted et une méthode MethodNameAsyncCancel (ou simplement CancelAsync). Un client souhaitant appeler l'opération définira un gestionnaire d'événements à appeler lorsque l'opération se termine.  
  
 L’extrait de code suivant montre comment déclarer des opérations asynchrones à l’aide du modèle asynchrone basé sur des événements.  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Pour plus d’informations sur le modèle asynchrone basé sur des événements, consultez [les modèle asynchrone basé sur les événements](http://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Modèle asynchrone IAsyncResult  
 Une opération de service peut être implémentée de manière asynchrone à l'aide du modèle de programmation asynchrone [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] et en marquant la méthode `<Begin>` avec la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ayant la valeur `true`. Dans ce cas, l'opération asynchrone est exposée dans les métadonnées sous la forme d'une opération synchrone: Elle est exposée comme une seule opération avec un message de demande et un message de réponse corrélé. Les modèles de programmation clients doivent ensuite choisir entre deux options. Ils peuvent représenter ce modèle comme une opération synchrone ou asynchrone, tant qu'un échange de messages de réponse-demande a lieu lorsque le service est appelé.  
  
 En général, avec la nature asynchrone des systèmes, vous ne devez pas exploiter de dépendance sur les threads.  La méthode la plus fiable pour transmettre des données à différentes étapes du traitement de la distribution des opérations consiste à utiliser les extensions.  
  
 Pour obtenir un exemple, consultez [Comment : implémenter une opération de Service asynchrone](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 Pour définir une opération de contrat `X` exécutée de façon asynchrone quelle que soit la manière dont elle est appelée dans l'application cliente :  
  
-   Définissez deux méthodes à l'aide du modèle `BeginOperation` et `EndOperation`.  
  
-   La méthode `BeginOperation` inclut les paramètres `in` et `ref` pour l'opération et retourne un type <xref:System.IAsyncResult>.  
  
-   La méthode `EndOperation` inclut un paramètre <xref:System.IAsyncResult> ainsi que les paramètres `out` et `ref` et elle retourne le type de retour des opérations.  
  
 Par exemple, reportez-vous à la méthode suivante :  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Voici les deux méthodes pour créer une opération asynchrone :  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  L'attribut <xref:System.ServiceModel.OperationContractAttribute> est appliqué uniquement à la méthode `BeginDoWork`. Le contrat obtenu a une opération WSDL nommée `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Appels asynchrones côté client  
 Une application cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut utiliser un des modèles d'appel asynchrone décrits précédemment.  
  
 Lors de l'utilisation du modèle basé sur des tâches, appelez simplement l'opération en utilisant le mot clé await comme indiqué dans l'extrait de code suivant.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 L’utilisation du modèle asynchrone basé sur des événements ne nécessite que l’ajout d’un gestionnaire d’événements pour recevoir une notification de la réponse, et l’événement résultant est déclenché automatiquement sur le thread d’interface utilisateur. Pour utiliser cette approche, spécifiez à la fois le **/async** et **/tcv:Version35** commande options avec les [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), comme dans les éléments suivants exemple.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Au terme de cette opération, l'outil Svcutil.exe génère une classe cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec l'infrastructure d'événement qui permet à l'application appelante d'implémenter et d'affecter un gestionnaire d'événements de recevoir la réponse et prendre la mesure appropriée. Pour obtenir un exemple complet, consultez [Comment : appeler les opérations de Service asynchrone](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Cependant, le modèle asynchrone basé sur les événements n'est disponible que dans le [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. De plus, il n'est pas pris en charge dans le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lorsqu'un canal client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est créé à l'aide d'un <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Avec les objets de canal client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous devez utiliser des objets <xref:System.IAsyncResult?displayProperty=nameWithType> pour appeler vos opérations de manière asynchrone. Pour utiliser cette approche, vous devez spécifier le **/async** commande option avec la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), comme dans l’exemple suivant.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Vous générez ainsi un contrat de service dans lequel chaque opération est modelée comme une méthode `<Begin>` et où la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> a la valeur `true` et une méthode correspondante `<End>`. Pour un exemple complet utilisant un <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : appeler opérations de façon asynchrone en utilisant une fabrique de canaux](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 Dans l’un ou l’autre cas, les applications peuvent appeler une opération de façon asynchrone même si le service est implémenté de façon synchrone, de la même façon qu’une application peut utiliser le même modèle pour appeler une méthode synchrone locale de façon asynchrone. La méthode d'implémentation de l'opération n'a pas d'importance pour le client. Quand le message de réponse arrive, son contenu est distribué à la méthode <`End`> asynchrone du client et ce dernier récupère les informations.  
  
### <a name="one-way-message-exchange-patterns"></a>Modèles d'échange de messages unidirectionnels  
 Vous pouvez également créer un modèle d'échange de messages asynchrone dans lequel les opérations unidirectionnelles (les opérations pour lesquelles <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> a la valeur `true` n'ont aucune réponse corrélée) peuvent être envoyées dans chaque direction par le client ou le service, indépendamment du côté opposé. (Cette méthode utilise le modèle d'échange de messages duplex avec des messages unidirectionnels.) Ainsi, le contrat de service spécifie un échange de messages unidirectionnels que chaque côté peut mettre en œuvre comme des appels ou implémentations asynchrones, ou synchrones, selon le cas. En général, lorsque le contrat est un échange de messages unidirectionnels, les implémentations sont en grande partie asynchrones car, après l'envoi d'un message, l'application n'attend pas de réponse et peut continuer à effectuer d'autres tâches.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Contrats de message et clients asynchrones basés sur les événements  
 Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>. Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>.  
  
 Si vous souhaitez recevoir l’objet de message en tant que le `Result` propriété et ont les valeurs retournées comme propriétés sur cet objet, utilisez le **/messageContract** option de commande. Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>. Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
