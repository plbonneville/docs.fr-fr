---
title: Regroupement de connexions OLE DB, ODBC et Oracle Connection
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 2e42b52bb75008fd34f3e4bef1788626d96368bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Regroupement de connexions OLE DB, ODBC et Oracle Connection
Le regroupement de connexions peut considérablement améliorer les performances et l'évolutivité de votre application. Cette section traite du regroupement de connexions pour les fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Regroupement de connexions pour OleDb  
 Le fournisseur de données .NET Framework pour OLE DB regroupe automatiquement les connexions utilisant le regroupement de sessions OLE DB. Les arguments string de connexion peuvent être utilisés pour activer ou désactiver les services OLE DB et notamment le regroupement. La chaîne de connexion suivante, par exemple, désactive le regroupement de sessions OLE DB et l'inscription automatique des transactions.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Il est recommandé de toujours fermer ou supprimer une connexion lorsque vous avez fini de l'utiliser afin de retourner la connexion au pool. Les connexions qui ne sont pas explicitement fermées risquent de ne pas être retournées au pool. Par exemple, une connexion devenue hors de portée mais qui n'a pas été explicitement fermée sera retournée au pool de connexion seulement si la taille maximale de celui-ci a été atteinte et si la connexion est toujours valide.  
  
 Pour plus d’informations sur la session OLE DB ou le regroupement des ressources, ainsi que comment désactiver le regroupement par substitution des services par défaut du fournisseur OLE DB, consultez le [Guide du programmeur OLE DB](http://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Regroupement de connexions pour Odbc  
 Le regroupement de connexions du fournisseur de données .NET Framework pour ODBC est géré par le gestionnaire de pilotes ODBC utilisé pour la connexion et n'est pas affecté par le fournisseur de données .NET Framework pour ODBC.  
  
 Pour activer ou désactiver le regroupement de connexions, ouvrez **administrateur de sources de données ODBC** dans le dossier Outils d’administration du Panneau de configuration. Le **le regroupement de connexions** onglet vous permet de spécifier des paramètres pour chaque pilote ODBC installé de regroupement de connexions. Notez que les modifications apportées au regroupement de connexions d'un pilote ODBC affectent toutes les applications qui utilisent ce pilote.  
  
 Pour plus d’informations sur le regroupement de connexions ODBC, consultez [INFO : Forum aux Questions sur regroupement de connexions ODBC](http://support.microsoft.com/kb/169470).  
  
## <a name="connection-pooling-for-oracleclient"></a>Regroupement de connexions pour OracleClient  
 Le fournisseur de données .NET Framework pour Oracle assure automatiquement le regroupement de connexions pour votre application cliente ADO.NET. Vous pouvez aussi fournir plusieurs modificateurs de chaîne de connexion afin de contrôler le comportement du pool de connexions (voir la section sur le contrôle des pools de connexions avec les mots clés des chaînes de connexion, plus loin dans cette rubrique).  
  
### <a name="pool-creation-and-assignment"></a>Création et assignation d'un pool  
 Lorsqu'une connexion est ouverte, un pool de connexions est créé sur la base d'un algorithme à correspondance exacte qui associe le pool à la chaîne de connexion dans la connexion. Chaque pool de connexions est associé à une chaîne de connexion distincte. Lorsqu'une nouvelle connexion est ouverte, si la chaîne de connexion ne correspond pas exactement à un pool existant, un nouveau pool est créé.  
  
 Une fois créés, les pools de connexions ne sont détruits qu'à la fin du processus actif. La maintenance des pools inactifs ou vides requiert très peu de ressources système.  
  
### <a name="connection-addition"></a>Ajout de connexions  
 Un pool de connexions est créé pour chaque chaîne de connexion unique. Lorsqu'un pool est créé, plusieurs objets de connexion sont créés et ajoutés au pool de sorte que l'exigence de taille minimale du pool soit remplie. Les connexions sont ajoutées au pool jusqu'à ce que sa taille maximale soit atteinte.  
  
 Quand un objet <xref:System.Data.OracleClient.OracleConnection> est demandé, il est obtenu du pool si une connexion utilisable est disponible. Pour être utilisable, la connexion ne doit pas être en cours d'utilisation, avoir un contexte de transaction correspondant ou ne pas être associée à un contexte de transaction et avoir un lien valide vers le serveur.  
  
 Si la taille maximale du pool est atteinte et qu'aucune connexion utilisable n'est disponible, la requête est mise en attente. Le dispositif de regroupement répond à ces requêtes en réallouant les connexions à mesure qu'elles se libèrent. Les connexions sont libérées et retournées au pool en cas de fermeture ou de suppression.  
  
### <a name="connection-removal"></a>Suppression des connexions  
 Le dispositif de regroupement de connexions supprime une connexion du pool restée inactive pendant une période prolongée ou s'il détecte que la connexion au serveur a été interrompue. Notez que cela ne peut être détecté qu'après une tentative de communication avec le serveur. Si une connexion n'est plus reliée au serveur, elle est marquée comme étant non valide. Le dispositif de regroupement analyse périodiquement les pools de connexions à la recherche d'objets qui ont été libérés vers le pool et sont marqués comme étant non valides. Ces connexions sont alors définitivement supprimées.  
  
 Si une connexion existante à un serveur a disparu, il est possible de la retirer du pool si le dispositif de regroupement n'a pas détecté d'interruption de la connexion et ne l'a pas marquée comme non valide. Dans ce cas, une exception est générée. Vous devez cependant toujours fermer la connexion afin de la libérer à nouveau vers le pool.  
  
 N'appelez pas une commande `Close` ou `Dispose` sur une `Connection`, un `DataReader` ou tout autre objet managé dans la méthode `Finalize` de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe. Pour plus d’informations, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Prise en charge des transactions  
 Les connexions sont retirées du pool et assignées en fonction du contexte de transaction. Le contexte du thread de requête et la connexion assignée doivent correspondre. Par conséquent, chaque pool de connexions est en fait sous-divisé en connexions aucun contexte de transaction associé avec eux et dans *N* sous-divisions qui contiennent chacune des connexions avec un contexte de transaction particulier.  
  
 Lorsqu’une connexion est fermée, elle est libérée à nouveau vers le pool et dans la sous-division appropriée en fonction de son contexte de transaction. Par conséquent, vous pouvez fermer la connexion sans générer d'erreur, même si une transaction distribuée est toujours en attente. Cela vous permet de valider ou d'abandonner ultérieurement la transaction distribuée.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Contrôle des pools de connexions avec les mots clés des chaînes de connexion  
 La propriété <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> de l'objet <xref:System.Data.OracleClient.OracleConnection> prend en charge les paires clé-valeur des chaînes de connexion qui peuvent être utilisées pour ajuster le comportement de la logique de regroupement des connexions.  
  
 Le tableau suivant décrit les valeurs <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> que vous pouvez utiliser pour ajuster le comportement de regroupement des connexions.  
  
|Nom|Par défaut|Description|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Lorsqu'une connexion est retournée au pool, l'heure de sa création est comparée à l'heure actuelle et la connexion est détruite si cet intervalle de temps (en secondes) excède la valeur spécifiée par `Connection Lifetime`. Cela est utile dans les configurations en clusters pour forcer l'équilibrage de la charge entre un serveur en cours d'exécution et un serveur qui vient d'être mis en ligne.<br /><br /> La valeur zéro (0) aura pour conséquence un délai d'attente maximal pour les connexions regroupées.|  
|`Enlist`|'true'|Si la valeur est `true`, le dispositif de regroupement inscrit automatiquement la connexion dans le contexte de transaction en cours du thread de création si un contexte de transaction existe.|  
|`Max Pool Size`|100|Nombre maximal de connexions autorisées dans le pool.|  
|`Min Pool Size`|0|Nombre minimal de connexions conservées dans le pool.|  
|`Pooling`|'true'|Si la valeur est `true`, la connexion est retirée du pool approprié ou, si nécessaire, créée et ajoutée au pool approprié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Regroupement de connexions](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Compteurs de performance](../../../../docs/framework/data/adonet/performance-counters.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
