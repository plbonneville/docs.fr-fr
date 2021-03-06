---
title: Informations système et Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: 727bcc53750081ae2d957527332ed3199c7d8e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="system-information-and-windows-forms"></a>Informations système et Windows Forms
Il est parfois nécessaire de rassembler des informations sur l’ordinateur de votre application est exécuté afin de prendre des décisions dans votre code. Par exemple, vous pouvez avoir une fonction qui est uniquement applicable lorsqu’il est connecté à un domaine de réseau particulier ; Dans ce cas, vous devez un moyen de déterminer le domaine et de désactiver la fonction si le domaine n’est pas présent.  
  
 Les applications Windows Forms peuvent utiliser la <xref:System.Windows.Forms.SystemInformation> classe pour déterminer un certain nombre de choses sur un ordinateur en cours d’exécution. L’exemple suivant montre comment utiliser le <xref:System.Windows.Forms.SystemInformation> classe pour récupérer le <xref:System.Windows.Forms.SystemInformation.UserName%2A> et <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 Tous les membres de la <xref:System.Windows.Forms.SystemInformation> classe sont en lecture seule ; vous ne pouvez pas modifier les paramètres d’un utilisateur. Il existe plus de 100 membres de la classe, en retournant des informations sur tous les éléments à partir du nombre d’écrans connectés à l’ordinateur (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) à l’espacement des icônes dans l’Explorateur Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> et <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Parmi les membres les plus utiles de la <xref:System.Windows.Forms.SystemInformation> classe inclure <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, et <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.SystemInformation>  
 [Gestion de l'alimentation dans Windows Forms](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
