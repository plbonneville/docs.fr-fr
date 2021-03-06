---
title: Construction de types (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 91ed123132965353ff354282f6850e9ef9cba3d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="constructing-types-entity-sql"></a>Construction de types (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit trois types de constructeurs : constructeurs de ligne, constructeurs de type nommé et constructeurs de collection.  
  
## <a name="row-constructors"></a>Constructeurs de ligne  
 Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs. Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champs correspondent aux types des valeurs qui ont servi à construire la ligne. Par exemple, l’expression suivante construit une valeur de type `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un. Pour plus d’informations, consultez la section « Règles d’alias » dans [identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :  
  
-   les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;  
  
-   deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.  
  
 Pour plus d’informations sur les constructeurs de ligne, consultez [ligne](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Constructeurs de collection  
 Les constructeurs de collection d'[!INCLUDE[esql](../../../../../../includes/esql-md.md)] permettent de créer une instance d'un multiensemble à partir d'une liste de valeurs. Toutes les valeurs du constructeur doivent être de type `T` mutuellement compatible et le constructeur produit une collection de type `Multiset<T>`. Par exemple, l'expression suivante crée une collection d'entiers :  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Les constructeurs multiensembles vides ne sont pas autorisés, car le type des éléments ne peut pas être déterminé. L'exemple suivant n'est pas valide :  
  
 `multiset() {}`  
  
 Pour plus d’informations, consultez [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Constructeurs de type nommé (initialiseurs NamedType)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permet aux constructeurs de type (initialiseurs) de créer des instances de types complexes nommés et de types d'entités. Par exemple, l'expression suivante crée une instance d'un type `Person`.  
  
 `Person("abc", 12)`  
  
 L'expression suivante crée une instance d'un type complexe.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 L'expression suivante crée une instance d'un type complexe imbriqué.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 L'expression suivante crée une instance d'une entité avec un type complexe imbriqué.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur Null. `MyModel.ZipCode(‘98118’, null)`  
  
 Les arguments passés au constructeur sont supposés se trouver dans le même ordre que dans la déclaration des attributs du type.  
  
 Pour plus d’informations, consultez [constructeur de Type nommé](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Vue d’ensemble d’Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Système de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
