---
title: 'Champs explicites : mot clé val (F#)'
description: "En savoir plus sur F # 'val' mot clé, qui est utilisé pour déclarer un emplacement pour stocker une valeur dans un type classe ou structure sans l’initialisation du type."
ms.date: 05/16/2016
ms.openlocfilehash: 2bd1aae24a5823ddcd6bb8f121d8110f4a211a6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-fields-the-val-keyword"></a>Champs explicites : mot clé val

Le mot clé `val` est utilisé pour déclarer un emplacement pour stocker une valeur dans un type de classe ou de structure sans l'initialiser. Les emplacements de stockage déclarés de cette manière sont appelés *champs explicites*. Une autre utilisation du mot clé `val` consiste à l'associer avec le mot clé `member` pour déclarer une propriété implémentée automatiquement. Pour plus d’informations sur les propriétés implémentées automatiquement, consultez [propriétés](properties.md).


## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Notes
La façon habituelle de définir des champs dans un type de classe ou de structure consiste à utiliser une liaison `let`. Toutefois, les liaisons `let` doivent être initialisées dans le cadre du constructeur de classe, ce qui n'est pas toujours possible, nécessaire ou souhaitable. Vous pouvez utiliser le mot clé `val` quand vous voulez un champ qui n'est pas initialisé.

Les champs explicites peuvent être statiques ou non statiques. Le *modificateur d’accès* peut être `public`, `private`, ou `internal`. Par défaut, les champs explicites sont publics. À la différence des liaisons `let` dans les classes, qui elles sont toujours privées.

Le [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) l’attribut est nécessaire pour les champs explicites dans les types de classe qui ont un constructeur principal. Cet attribut spécifie que le champ est initialisé à zéro. Le type du champ doit prendre en charge l'initialisation à zéro. Un type prend en charge l'initialisation à zéro s'il s'agit d'un type suivant :

- Type primitif qui a une valeur zéro.

- Type qui prend en charge une valeur null, en tant que valeur normale, en tant que valeur anormale ou en tant que représentation d'une valeur. Sont inclus les classes, les tuples, les enregistrements, les fonctions, les interfaces, les types référence .NET, le type `unit` et les types union discriminée.

- Type valeur .NET.

- Structure dont les champs prennent tous en charge une valeur zéro par défaut.


Par exemple, un champ immuable appelé `someField` a un champ de stockage dans la représentation compilée .NET portant le nom `someField@` et vous accédez à la valeur stockée à l'aide d'une propriété nommée `someField`.

Pour un champ mutable, la représentation compilée .NET est un champ .NET.


>[!WARNING] 
`Note` L’espace de noms .NET Framework `System.ComponentModel` contient un attribut qui porte le même nom. Pour plus d'informations sur cet attribut, consultez `System.ComponentModel.DefaultValueAttribute`.


Le code suivant illustre l'utilisation de champs explicites et, à titre de comparaison, d'une liaison `let` dans une classe qui a un constructeur principal. Notez que le champ lié à `let` `myInt1` est privé. Quand le champ lié à `let` `myInt1` est référencé à partir d'une méthode membre, l'auto-identificateur `this` n'est pas requis. Mais quand vous référencez les champs explicites `myInt2` et `myString`, l'auto-identificateur est requis.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

La sortie est la suivante :

```
11 12 abc
30 def
```

Le code suivant illustre l'utilisation de champs explicites dans une classe qui n'a pas de constructeur principal. Dans ce cas, l'attribut `DefaultValue` n'est pas requis, mais tous les champs doivent être initialisés dans les constructeurs définis pour le type.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Le résultat est `35 22`.

Le code suivant illustre l'utilisation de champs explicites dans une structure. Comme une structure est un type valeur, elle a automatiquement un constructeur par défaut qui définit les valeurs de ses champs à zéro. Ainsi, l'attribut `DefaultValue` n'est pas requis.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Le résultat est `11 xyz`.

Les champs explicites n'ont pas vocation à être utilisés dans le cadre d'une routine. En général, quand cela est possible, vous devez utiliser une liaison `let` dans une classe au lieu d'un champ explicite. Les champs explicites s'avèrent utiles dans certains scénarios d'interopérabilité, notamment quand vous devez définir une structure qui sera utilisée dans un appel de code non managé à une API native ou dans des scénarios COM interop. Pour plus d’informations, consultez [fonctions externes](../functions/external-functions.md). Une autre situation dans laquelle un champ explicite peut s'avérer nécessaire est liée à l'utilisation d'un générateur de code F# qui émet des classes sans constructeur principal. Les champs explicites s'avèrent également utiles pour les variables static de thread ou les constructions similaires. Pour plus d'informations, consultez `System.ThreadStaticAttribute`.

Quand les mots clés `member val` apparaissent ensemble dans une définition de type, il s'agit de la définition d'une propriété implémentée automatiquement. Pour plus d’informations, consultez [propriétés](properties.md).


## <a name="see-also"></a>Voir aussi
[Propriétés](properties.md)

[Membres](index.md)

[Liaisons `let` dans des classes](let-bindings-in-classes.md)
