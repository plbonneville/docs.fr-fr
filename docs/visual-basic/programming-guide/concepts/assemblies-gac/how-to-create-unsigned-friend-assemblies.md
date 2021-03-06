---
title: 'Comment : créer des assemblys Friend non signés (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 873a5bf235b43b4460a1489a964539c4e4c18de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Comment : créer des assemblys Friend non signés (Visual Basic)
Cet exemple montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Pour créer un assembly et un assembly friend  
  
1.  Ouvrez une invite de commandes.  
  
2.  Créez un fichier Visual Basic nommé `friend_signed_A.` qui contient le code suivant. Le code utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour déclarer friend_signed_B comme assembly friend.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Compilez et signez friend_signed_A à l’aide de la commande suivante.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Créez un fichier Visual Basic nommé `friend_unsigned_B` qui contient le code suivant. Étant donné que friend_unsigned_A spécifie friend_unsigned_B comme assembly friend, le code de friend_unsigned_B peut accéder aux membres et aux types `Friend` de friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Compilez friend_signed_B à l’aide de la commande suivante.  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Le nom de l’assembly qui est généré par le compilateur doit correspondre au nom de l’assembly friend qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Vous pouvez définir explicitement l’assembly à l’aide de la `/out` option du compilateur.  
  
6.  Exécutez le fichier friend_signed_B.exe.  
  
     Le programme affiche deux chaînes : « Class1.Test » et « Class2.Test ».  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, tandis que l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contrôle la visibilité des membres et types `Friend`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Assemblys friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Comment : créer des assemblys Friend signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Concepts de Guide de programmation](../../../../visual-basic/programming-guide/concepts/index.md)
