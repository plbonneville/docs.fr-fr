---
title: '!= (différent de) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 4ed09b0c5f10ef1ac77c4b374619508d714f1dc3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="-not-equal-to-entity-sql"></a>!= (différent de) (Entity SQL)
Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite. L'opérateur != (différent de) est d'un point de vue fonctionnel équivalent à l'opérateur <>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide. Les deux expressions doivent posséder des types de données implicitement convertibles.  
  
## <a name="result-types"></a>Types de résultats  
 `true` si l'expression de gauche est différente de l'expression de droite ; sinon, `false`.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur != pour comparer deux expressions afin de déterminer si l'expression de gauche est différente de l'expression de droite. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
