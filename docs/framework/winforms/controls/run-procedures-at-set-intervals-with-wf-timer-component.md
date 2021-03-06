---
title: "Comment : exécuter des procédures à intervalles définis à l'aide du composant Timer Windows Forms"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: 58ad0578f478b5cbc1d2a263fdf6b14b4555a339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Comment : exécuter des procédures à intervalles définis à l'aide du composant Timer Windows Forms
Il peut arriver que vous souhaitiez créer une procédure qui s'exécute à intervalles réguliers jusqu'à ce qu'une boucle soit terminée ou qu'un intervalle de temps spécifique soit écoulé. Vous pouvez pour cela utiliser le composant <xref:System.Windows.Forms.Timer>.  
  
 Ce composant est conçu pour un environnement Windows Forms. Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Il existe certaines limitations quand vous utilisez le composant <xref:System.Windows.Forms.Timer>. Pour plus d’informations, consultez [Limitations de la propriété d’intervalle du composant Timer Windows Forms](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Pour exécuter une procédure à intervalles spécifiques avec le composant Timer  
  
1.  Ajoutez un <xref:System.Windows.Forms.Timer> à votre formulaire. Pour savoir comment effectuer cette tâche par programmation, consultez la section suivante. Visual Studio prend également en charge l’ajout de composants à un formulaire. Consultez également [Comment : ajouter aux Windows Forms de contrôles sans Interface utilisateur](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Définissez la propriété <xref:System.Windows.Forms.Timer.Interval%2A> (en millisecondes) du minuteur. Cette propriété détermine combien de temps s'écoulera avant la réexécution de la procédure.  
  
    > [!NOTE]
    >  Plus un événement de minuteur se produit souvent, plus il faut de temps processeur pour y répondre. Cela peut ralentir les performances globales. Ne définissez pas un intervalle plus petit que ce qui est nécessaire.  
  
3.  Écrivez le code approprié dans le gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick>. Le code que vous écrivez dans cet événement s'exécutera à l'intervalle spécifié dans la propriété <xref:System.Windows.Forms.Timer.Interval%2A>.  
  
4.  Affectez la valeur <xref:System.Windows.Forms.Timer.Enabled%2A> à la propriété `true` pour démarrer le minuteur. L'événement <xref:System.Windows.Forms.Timer.Tick> commencera à se produire et à exécuter votre procédure à l'intervalle indiqué.  
  
5.  Au moment opportun, affectez la valeur `false` à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> pour empêcher que la procédure soit réexécutée. Si l’intervalle `0` n’entraîne pas l’arrêt du minuteur.  
  
## <a name="example"></a>Exemple  
 Ce premier exemple de code effectue le suivi de l'heure par incréments d'une seconde. Il utilise un <xref:System.Windows.Forms.Button>, un <xref:System.Windows.Forms.Label> et un composant <xref:System.Windows.Forms.Timer> sur un formulaire. La propriété <xref:System.Windows.Forms.Timer.Interval%2A> prend la valeur 1 000 (égal à une seconde). Dans l'événement <xref:System.Windows.Forms.Timer.Tick>, la légende de l'étiquette prend comme valeur l'heure actuelle. En cas de clic sur le bouton, la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> prend la valeur `false` et le minuteur cesse de mettre à jour la légende de l'étiquette. L’exemple de code suivant requiert que vous disposez d’un formulaire avec un <xref:System.Windows.Forms.Button> contrôle nommé `Button1`, un <xref:System.Windows.Forms.Timer> contrôle nommé `Timer1`et un <xref:System.Windows.Forms.Label> contrôle nommé `Label1`.  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>Exemple  
 Ce deuxième exemple de code exécute une procédure toutes les 600 millisecondes jusqu'à ce qu'une boucle soit terminée. L’exemple de code suivant requiert que vous disposez d’un formulaire avec un <xref:System.Windows.Forms.Button> contrôle nommé `Button1`, un <xref:System.Windows.Forms.Timer> contrôle nommé `Timer1`et un <xref:System.Windows.Forms.Label> contrôle nommé `Label1`.  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Timer>  
 [Timer, composant](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Vue d’ensemble du composant Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
