---
title: Streaming Feeds, exemple
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 2c420bad9ad96107f56b5435efa6fffd6941cdaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="streaming-feeds-sample"></a>Streaming Feeds, exemple
Cet exemple indique comment gérer des flux de syndication qui contiennent de grandes quantités d'éléments. Sur le serveur, l'exemple décrit comment différer la création d'objets <xref:System.ServiceModel.Syndication.SyndicationItem> individuels dans le flux jusqu'au moment précédant immédiatement l'écriture de l'élément dans le flux de données réseau.  
  
 Sur le client, l'exemple décrit comment un module de formatage de flux de syndication personnalisé peut être utilisé pour lire des éléments du flux de réseau, afin que le flux qui est lu ne soit jamais complètement mis en mémoire tampon.  
  
 Pour mieux illustrer la fonction de diffusion en continu de l'API de syndication, cet exemple utilise un scénario quelque peu improbable dans lequel le serveur expose un flux qui contient un nombre infini d'éléments. Dans ce cas, le serveur continue à générer de nouveaux éléments dans le flux jusqu'à ce qu'il détermine que le client a lu un nombre spécifié d'éléments du flux (10 par défaut). Pour plus de simplicité, le client et le serveur sont tous deux implémentés dans le même processus et utilisent un objet `ItemCounter` partagé pour assurer le suivi du nombre d'éléments que le client a générés. Le type `ItemCounter` existe uniquement pour permettre à l'exemple de scénario de se terminer convenablement et n'est pas un élément essentiel du modèle qui est illustré.  
  
 La démonstration se sert de Visual C# itérateurs (à l’aide de la `yield``return` mot clé). Pour plus d’informations sur les itérateurs, consultez la rubrique « Utilisation d’itérateurs » sur MSDN.  
  
## <a name="service"></a>Service  
 Le service implémente un contrat <xref:System.ServiceModel.Web.WebGetAttribute> de base qui se compose d'une opération, comme l'illustre le code suivant.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Le service implémente ce contrat en utilisant une classe `ItemGenerator` pour créer un flux potentiellement infini d'instances <xref:System.ServiceModel.Syndication.SyndicationItem> à l'aide d'un itérateur, comme l'illustre le code suivant.  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 Lorsque l'implémentation de service crée le flux, la sortie de `ItemGenerator.GenerateItems()` est utilisée à la place d'une collection d'éléments mise en mémoire tampon.  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 En conséquence, le flux d'éléments n'est jamais complètement mis en mémoire tampon. Vous pouvez observer ce comportement en définissant un point d’arrêt sur la `yield``return` instruction à l’intérieur de la `ItemGenerator.GenerateItems()` (méthode) et noter que ce point d’arrêt est rencontré pour la première fois, une fois que le service a renvoyé les résultats de la `StreamedFeed()` (méthode).  
  
## <a name="client"></a>Client  
 Le client de cet exemple utilise une implémentation <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> personnalisée qui diffère la matérialisation d'éléments individuels dans le flux au lieu de les mettre en mémoire tampon. L'instance `StreamedAtom10FeedFormatter` personnalisée est utilisée comme suit.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalement, un appel à <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> ne retourne rien jusqu'à ce que le contenu entier du flux ait été lu depuis le réseau et mis en mémoire tampon. Toutefois, l'objet `StreamedAtom10FeedFormatter` substitue <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> pour retourner un itérateur au lieu d'une collection mise en mémoire tampon, comme l'illustre le code suivant.  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 En conséquence, aucun élément n'est lu depuis le réseau avant que l'application cliente qui parcourt les résultats de `ReadItems()` ne soit prête à l'utiliser. Vous pouvez observer ce comportement en définissant un point d’arrêt sur la `yield``return` instruction à l’intérieur de `StreamedAtom10FeedFormatter.DelayReadItems()` et en remarquant que ce point d’arrêt est rencontré pour la première fois après l’appel à `ReadFrom()` se termine.  
  
 Les instructions suivantes indiquent comment générer et exécuter l'exemple. Notez que bien que le serveur cesse de générer des éléments après que le client a lu 10 éléments, la sortie indique que le client lit bien plus que 10 éléments. Cela est dû au fait que la liaison de mise en réseau utilisée par l’exemple transmet les données dans des segments de quatre kilo-octets (Ko). Le client reçoit donc 4 Ko de données d’éléments avant qu’il ait la possibilité de lire ne serait-ce qu’un élément. Il s'agit du comportement normal (l'envoi de données HTTP diffusées en continu dans des segments de taille raisonnable améliore les performances).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de diagnostics autonome](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
