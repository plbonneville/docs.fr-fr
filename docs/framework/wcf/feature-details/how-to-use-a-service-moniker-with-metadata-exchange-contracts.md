---
title: "Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées"
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées
Après avoir développé des nouveaux services WCF, vous pouvez décider que vous voulez être en mesure d’appeler ces services à partir d’un script ou une application Visual Basic 6.0. Une méthode consisterait à générer un assembly de client WCF, inscrire l’assembly avec COM, installez l’assembly dans le GAC et ensuite référencer les types COM à partir de votre code Visual Basic. Lorsque vous distribuez l’application, vous devrez distribuer également l’assembly Client WCF. L'utilisateur devra ensuite inscrire l'assembly client WCF avec COM et le placer dans le GAC. WCF COM Interop permet également à effectuer les mêmes appels de service sans se baser sur un assembly de client WCF. Le moniker WCF vous permet d’appeler un service WCF à partir de n’importe quel langage compatible COM (Visual Basic, VBScript, Visual Basic pour Applications (VBA) et ainsi de suite) en spécifiant un point de terminaison (Mex) d’exchange métadonnées URI que le moniker de service utilise pour extraire le type informations sur le service. Cette rubrique décrit comment appeler l’exemple de mise en route de WCF a démarré à l’aide d’un moniker WCF qui spécifie un point de terminaison Mex.  
  
> [!NOTE]
>  Les types définis par l’assembly client WCF ne sont jamais réellement instanciés. L'assembly est utilisé uniquement pour les métadonnées.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Utilisation du moniker de service avec une adresse Mex  
  
1.  Générez l’exemple de mise en route et utilisez Internet Explorer pour naviguer jusqu'à son URL (http://localhost/ServiceModelSamples/Service.svc) pour vous assurer que le service fonctionne.  
  
2.  Créez un script Visual Basic ou une application Visual Basic qui contient le code suivant :  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Exécutez l'application ou le script Visual Basic.  
  
    > [!NOTE]
    >  Le service que vous appelez doit exposer un point de terminaison Mex pour que le moniker soit en mesure de lire les métadonnées du service. Pour plus d’informations, consultez [Comment : publier les métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.  Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser le moniker de service Windows Communication Foundation sans inscription](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Guide pratique pour utiliser un moniker de service avec des contrats WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
