---
title: "await (référence C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23a3299492c538963e9a5dceaadc81a44d386b19
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="await-c-reference"></a>await (référence C#)
L’opérateur `await` est appliqué à une tâche dans une méthode asynchrone pour insérer un point d’interruption dans l’exécution de la méthode jusqu’à ce que la tâche attendue se termine. La tâche représente un travail en cours.  
  
`await` peut uniquement être utilisé dans une méthode asynchrone modifiée par le mot clé [async](../../../csharp/language-reference/keywords/async.md). Une telle méthode, définie à l’aide du modificateur `async` et contenant généralement une ou plusieurs expressions `await`, est appelée *méthode async*.  
  
> [!NOTE]
>  Les mots clés `async` et `await` ont été introduits dans C# 5. Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).  
  
La tâche à laquelle l’opérateur `await` est appliqué est généralement retournée par un appel à une méthode qui implémente le [modèle asynchrone basé sur des tâches](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Cela inclut des méthodes qui retournent des objets <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> et `System.Threading.Tasks.ValueType<TResult>`.  

  
 Dans l’exemple suivant, la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retourne un `Task<byte[]>`. La tâche est une promesse de produire le tableau d’octets réel quand la tâche est terminée. L’opérateur `await` suspend l’exécution jusqu’à ce que le travail de la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> soit terminé. Entre-temps, le contrôle revient à l'appelant de `GetPageSizeAsync`. Une fois l’exécution de la tâche terminée, l’expression `await` prend comme valeur un tableau d’octets.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Pour obtenir un exemple complet, consultez [Procédure pas à pas : accès au web avec async et await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Vous pouvez télécharger l’exemple à partir des [exemples de code pour les développeurs](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) sur le site web de Microsoft. L'exemple est dans le projet AsyncWalkthrough_HttpClient.  
  
Comme indiqué dans l’exemple précédent, si `await` est appliqué au résultat d’un appel de méthode qui retourne un `Task<TResult>`, le type de l’expression `await` est `TResult`. Si `await` est appliqué au résultat d’un appel de méthode qui retourne un `Task`, le type de l’expression `await` est `void`. L'exemple suivant illustre la différence.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
Une expression `await` ne bloque pas le thread sur lequel elle s'exécute. Elle indique plutôt au compilateur de signer le reste de la méthode async comme une continuation sur la tâche attendue. Le contrôle revient alors à l'appelant de la méthode async. Quand la tâche est terminée, elle appelle sa continuation et l'exécution de la méthode async reprend là où elle s'était arrêtée.  
  
Une expression `await` peut se produire uniquement dans le corps de sa méthode englobante, une expression lambda ou une méthode anonyme, qui doit être marquée avec un modificateur `async`. Le terme *await* sert de mot clé uniquement dans ce contexte. Partout ailleurs, il est interprété en tant qu'identificateur. Dans la méthode, l’expression lambda ou la méthode anonyme, une expression `await` ne peut pas se produire dans le corps d’une fonction synchrone, dans une expression de requête, dans le bloc d’une [instruction lock](../../../csharp/language-reference/keywords/lock-statement.md) ou dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exceptions"></a>Exceptions  
La plupart des méthodes async retournent un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Les propriétés de la tâche retournée comportent des informations sur son état et son historique. Celles-ci indiquent notamment si la tâche est terminée ou non, si la méthode async a levé une exception ou a été annulée et quel est le résultat final. L’opérateur `await` accède à ces propriétés en appelant des méthodes sur l’objet retourné par la méthode `GetAwaiter`.  
  
Si vous attendez une méthode async retournant des tâches qui lève une exception, l’opérateur `await` lève de nouveau l’exception.  
  
Si vous attendez une méthode async retournant des tâches qui est annulée, l'opérateur `await` lève de nouveau une exception <xref:System.OperationCanceledException>.  
  
Une tâche qui se trouve dans un état d'erreur peut refléter plusieurs exceptions. Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quand vous attendez une telle tâche, l'opération await lève à nouveau une seule des exceptions. Toutefois, vous ne pouvez pas prédire laquelle de ces exceptions est de nouveau levée.  
  
Pour obtenir des exemples de gestion des erreurs dans les méthodes asynchrones, consultez [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Exemple  
L’exemple suivant retourne le nombre total de caractères dans les pages dont les URL lui sont passées comme arguments de ligne de commande. L’exemple appelle la méthode `GetPageLengthsAsync`, qui est marquée avec le mot clé `async`. La méthode `GetPageLengthsAsync` utilise à son tour le mot clé `await` pour attendre des appels à la méthode <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType>.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Étant donné que l’utilisation de `async` et de `await` dans un point d’entrée d’application n’est pas prise en charge, nous ne pouvons pas appliquer l’attribut `async` à la méthode `Main` ni attendre l’appel à la méthode `GetPageLengthsAsync`. Nous pouvons garantir que la méthode `Main` attend la fin de l’opération asynchrone en récupérant la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>. Pour les tâches qui ne retournent pas de valeur, vous pouvez appeler la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. 

## <a name="see-also"></a>Voir aussi  
[Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md)   
[Procédure pas à pas : accès au web avec async et await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[async](../../../csharp/language-reference/keywords/async.md)
