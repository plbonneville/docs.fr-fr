---
title: Minuteries de threads (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
ms.openlocfilehash: 019b8372be63b9a9fdbcee134834a34f6bef2b74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="thread-timers-visual-basic"></a>Minuteries de threads (Visual Basic)
La classe <xref:System.Threading.Timer?displayProperty=nameWithType> est utile pour exécuter périodiquement une tâche sur un thread séparé. Par exemple, vous pouvez utiliser un minuteur de thread pour vérifier l’état et l’intégrité d’une base de données ou pour sauvegarder des fichiers essentiels.  
  
## <a name="thread-timer-example"></a>Exemple de minuteur de thread  
 L’exemple suivant démarre une tâche toutes les deux secondes et utilise un indicateur pour lancer la méthode <xref:System.IDisposable.Dispose%2A> qui arrête le minuteur. Cet exemple publie l’état dans la fenêtre de sortie.  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 Les minuteurs de thread sont particulièrement utiles quand l’objet <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> n’est pas disponible, par exemple quand vous développez des applications console.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading>  
 [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
