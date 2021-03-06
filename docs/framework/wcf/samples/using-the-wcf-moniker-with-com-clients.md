---
title: Using the WCF Moniker with COM Clients
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 79040cd267d354d32b3e957dc70fcc65b09b0fc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Using the WCF Moniker with COM Clients
Cet exemple montre comment utiliser le moniker de service Windows Communication Foundation (WCF) pour intégrer des services Web dans des environnements de développement COM, tels que Microsoft Office Visual Basic pour Applications (Office VBA) ou Visual Basic 6.0. Il se compose d'un client Windows Script Host (.vbs), d'une bibliothèque de client assurant la prise en charge (.dll) et d'une bibliothèque de service (.dll) hébergée par les services IIS (Internet Information Services). Le service correspond à un service de calculatrice et le client COM appelle les opérations mathématiques suivantes sur le service : addition, soustraction, multiplication et division. L'activité du client s'affiche dans les fenêtres de message.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Le service implémente un contrat `ICalculator` tel que défini dans l'exemple de code suivant.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 L'exemple illustre les trois manières d'utiliser le moniker :  
  
-   Contrat typé : le contrat est enregistré sur l'ordinateur client sous la forme d'un type visible par COM.  
  
-   Contrat WSDL : le contrat est fourni sous la forme d'un document WSDL.  
  
-   Contrat MEX : le contrat est récupéré pendant l'exécution depuis un point de terminaison d'échange de métadonnées (Metadata Exchange, MEX).  
  
## <a name="typed-contract"></a>Contrat typé  
 Pour utiliser le moniker avec un contrat typé, les types attribués de manière appropriée au contrat de service doivent être enregistrés à l'aide de COM. Tout d’abord, un client doit être généré à l’aide de la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Cette classe doit être intégrée à un projet, lequel doit être configuré pour générer un assembly visible par COM et signé lors de la compilation. L'attribut suivant doit être intégré au fichier AssemblyInfo.cs :  
  
```  
[assembly: ComVisible(true)]  
```  
  
 Une fois le projet généré, enregistrez les types visibles par COM en utilisant `regasm` tel qu'illustré dans l'exemple suivant.  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 L'assembly créé doit être ajouté au Global Assembly Cache. Bien que cela ne soit pas strictement nécessaire, cela permet de localiser plus facilement l'assembly pendant l'exécution. La commande suivante ajoute l'assembly au Global Assembly Cache :  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Le moniker de service requiert uniquement l'inscription de type et n'utilise pas le proxy pour communiquer avec le service.  
  
 L'application cliente ComCalcClient.vbs utilise la fonction `GetObject` et la syntaxe du moniker de service pour construire un proxy pour le service, notamment pour spécifier ses adresse, liaison et contrat.  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Les paramètres utilisés par le moniker spécifient :  
  
-   Adresse du point de terminaison de service.  
  
-   Liaison à utiliser par le client pour se connecter à ce point de terminaison. Dans ce cas, la liaison wsHttpBinding définie par le système est utilisée bien que des liaisons personnalisées puissent être définies dans les fichiers de configuration du client. Pour une utilisation avec Windows Script Host, les liaisons personnalisées sont définies dans un fichier Cscript.exe.config stocké dans le même répertoire que Cscript.exe.  
  
-   Type du contrat pris en charge au niveau du point de terminaison. Il s'agit du type généré et enregistré plus haut. Le script Visual Basic ne fournissant pas d'environnement COM fortement typé, un identificateur de contrat doit être spécifié. Ce GUID correspond à l'identificateur `interfaceID` issu du CalcProxy.tlb. Il est peut être affiché à l'aide des outils COM tels que l'Explorateur d'objets d'OLE/COM (OleView.exe). Pour les environnements fortement typés tels qu'Office VBA ou Visual Basic 6.0, l'ajout d'une référence explicite à la bibliothèque de types et la déclaration d'un type d'objet de proxy permettent de remplacer le paramètre de contrat. Ceci permet également la prise en charge d'IntelliSense pendant le développement de l'application cliente.  
  
 Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. Ici, un client COM effectue des appels COM à l'aide du moniker typé afin de communiquer avec le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bien que ce client utilise COM, les communications avec le service se composent uniquement d'appels de service Web.  
  
## <a name="wsdl-contract"></a>Contrat WSDL  
 Pour utiliser le moniker à l'aide du contrat WSDL du service, aucune inscription de bibliothèque côté client n'est requise. Ce contrat doit cependant être récupéré via un mécanisme hors bande, par exemple à l'aide d'un navigateur permettant d'accéder au point de terminaison WSDL de ce service. Le moniker peut accéder ensuite à ce contrat pendant l'exécution.  
  
 L'application cliente ComCalcClient.vbs utilise `FileSystemObject` pour accéder au fichier WSDL enregistré localement, puis utilise de nouveau la fonction `GetObject` pour construire un proxy de service.  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 Les paramètres utilisés par le moniker spécifient :  
  
-   Adresse du point de terminaison de service.  
  
-   Liaison que le client doit utiliser pour se connecter à ce point de terminaison et l'espace de noms dans lequel cette liaison est définie. Dans ce cas, `wsHttpBinding_ICalculator` est utilisé.  
  
-   WSDL qui définit le contrat. Dans ce cas, il s'agit de la chaîne lue à partir du fichier serviceWsdl.xml.  
  
-   Nom et espace de noms du contrat. Cette identification est requise, le WSDL étant susceptible de contenir plusieurs contrats.  
  
    > [!NOTE]
    >  Par défaut, les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génèrent des fichiers WSDL distincts pour chaque espace de noms utilisé. Ces espaces sont liés à l'utilisation de la construction d'importation WSDL. Le moniker escomptant une définition WSDL unique, le service doit utiliser un espace de noms unique comme illustré dans cet exemple ou les fichiers distincts doivent être fusionnés manuellement.  
  
 Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. Ici, un client COM effectue des appels COM à l'aide du moniker et du contrat WSDL défini pour communiquer avec le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]  
  
## <a name="metadata-exchange-contract"></a>Contrat d'échange de métadonnées  
 Pour utiliser le moniker avec un contrat MEX, comme avec le contrat WSDL, aucune inscription côté client n'est requise. Le contrat du service est récupéré pendant l'exécution via l'utilisation interne de l'échange de métadonnées.  
  
 L'application cliente ComCalcClient.vbs utilise de nouveau la fonction `GetObject` pour construire un proxy de service.  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Les paramètres utilisés par le moniker spécifient :  
  
-   Adresse du point de terminaison de l'échange de métadonnées du service.  
  
-   Adresse du point de terminaison de service.  
  
-   Liaison que le client doit utiliser pour se connecter à ce point de terminaison et l'espace de noms dans lequel cette liaison est définie. Dans ce cas, `wsHttpBinding_ICalculator` est utilisé.  
  
-   Nom et espace de noms du contrat. Cette identification est requise, le WSDL étant susceptible de contenir plusieurs contrats.  
  
 Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. Ici, un client COM effectue des appels COM à l'aide du moniker et du contrat MEX défini pour communiquer avec le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  À partir d’une invite de commandes Visual Studio, ouvrez le dossier \client\bin, sous le dossier de langue spécifique.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2, veillez à exécuter l'invite de commandes avec des privilèges d'administrateur.  
  
4.  Tapez dans `tlbexp.exe client.dll /out:CalcProxy.tlb` pour exporter le fichier dll vers un fichier tlb. Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.  
  
5.  Tapez dans `regasm.exe /tlb:CalcProxy.tlb client.dll` pour enregistrer les types avec COM. Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.  
  
6.  Tapez dans `gacutil.exe /i client.dll` pour ajouter l’assembly dans le Global Assembly Cache.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1.  Test que vous pouvez accéder au service à l’aide d’un navigateur en tapant l’adresse suivante : `http://localhost/servicemodelsamples/service.svc`. Une page de confirmation doit s'afficher en réponse.  
  
2.  Exécutez ComCalcClient.vbs à partir du dossier \client figurant dans le dossier correspondant à votre langue. L'activité du client est affichée dans les fenêtres de message.  
  
3.  Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Créez un répertoire virtuel nommé ServiceModelSamples sur l'ordinateur de service. Le script Setupvroot.bat inclus dans l'exemple peut être utilisé pour créer le répertoire de disque et le répertoire virtuel.  
  
2.  Copiez les fichiers du programme de service depuis %SystemDrive%\Inetpub\wwwroot\servicemodelsamples vers le répertoire virtuel ServiceModelSamples. Assurez-vous d'intégrer les fichiers au répertoire \bin.  
  
3.  Copiez le fichier script du client depuis le dossier \client figurant dans le dossier correspondant à votre langue sur l'ordinateur client.  
  
4.  Dans le fichier script, modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service. Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.  
  
5.  Copiez le fichier WSDL sur l'ordinateur client. Dans le fichier WSDL nommé serviceWsdl.xml, remplacez toutes les occurrences de localhost par le nom de domaine complet de votre serveur.  
  
6.  Copiez la bibliothèque Client.dll depuis le dossier \client\bin figurant dans le dossier correspondant à votre langue dans un répertoire de l'ordinateur client.  
  
7.  À partir d'une invite de commandes, naviguez jusqu'à ce répertoire de destination. Si vous utilisez [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], assurez-vous d'exécuter l'invite de commandes en tant qu'administrateur.  
  
8.  Tapez dans `tlbexp.exe client.dll /out:CalcProxy.tlb` pour exporter le fichier dll vers un fichier tlb. Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.  
  
9. Tapez dans `regasm.exe /tlb:CalcProxy.tlb client.dll` pour enregistrer les types avec COM. Assurez-vous que le chemin a été défini sur le dossier qui contient `regasm.exe` avant d’exécuter la commande.  
  
10. Tapez dans `gacutil.exe /i client.dll` pour ajouter l’assembly dans le Global Assembly Cache. Assurez-vous que le chemin a été défini sur le dossier qui contient `gacutil.exe` avant d’exécuter la commande.  
  
11. Assurez-vous que le service est accessible depuis l'ordinateur client à l'aide d'un navigateur.  
  
12. Sur l'ordinateur client, lancez ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
-   Pour des raisons de sécurité, supprimez la définition du répertoire virtuel et les autorisations accordées pendant les étapes de l'installation, une fois l'exécution des exemples terminée.  
  
## <a name="see-also"></a>Voir aussi
