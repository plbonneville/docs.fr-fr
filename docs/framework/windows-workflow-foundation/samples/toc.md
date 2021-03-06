# [Exemples Windows Workflow](index.md)
## [Application](application.md)
### [Processus d’approbation des documents](document-approval-process.md)
### [Processus d’achat d’entreprise](corporate-purchase-process.md)
### [Processus d’embauche](hiring-process.md)
### [Suivi de workflow visuel](visual-workflow-tracking.md)
### [Gestion de l’instance interrompue](suspended-instance-management.md)
## [Basic](basic.md)
### [Activités intégrées](built-in-activities.md)
#### [Gestion des erreurs dans une activité Flowchart à l’aide de TryCatch](fault-handling-in-a-flowchart-activity-using-trycatch.md)
#### [Émulation de l’interruption dans une activité While](emulating-breaking-in-a-while-activity.md)
#### [Création avec DynamicActivity](dynamicactivity-creation.md)
#### [Utilisation de variables avec un ensemble de règles .NET Framework 3.5](using-variables-with-dotnet-ruleset.md)
#### [Charger à partir de XAML](load-from-xaml.md)
#### [Utilisation d’activités de collection](using-collection-activities.md)
#### [Utilisation de l’activité InvokeMethod](using-the-invokemethod-activity.md)
#### [Utilisation de l’activité Pick](using-the-pick-activity.md)
#### [Utilisation d’activités procédurales](using-procedural-activities.md)
#### [Utilisation de CancellationScope](using-cancellationscope.md)
#### [InvokeMethod](invokemethod.md)
#### [Utilisation de l’activité Switch avec des types personnalisés](usage-of-the-switch-activity-with-custom-types.md)
#### [Interopérabilité avec l’ensemble de règles 3.5](interop-with-3-5-rule-set.md)
### [Compensation](compensation-samples.md)
#### [Activité compensable](compensable-activity-sample.md)
#### [Compensation personnalisée](custom-compensation-sample.md)
#### [Confirmation](confirmation.md)
#### [Gestionnaire d’annulation sur une activité compensable](cancellation-handler-on-compensable-activity.md)
### [Activités personnalisées](custom-activities.md)
#### [Code-Bodied](code-bodied.md)
##### [Signets](bookmarks.md)
##### [Composite personnalisé à l’aide de NativeActivity](custom-composite-using-native-activity.md)
##### [Propriétés d’exécution](execution-properties.md)
##### [Exposition et appel d’ActivityActions](exposing-and-invoking-activityactions.md)
##### [Utilisation d’AsyncOperationContext dans une activité](using-asyncoperationcontext-in-an-activity-sample.md)
##### [Activité personnalisée Hello World](hello-world-custom-activity.md)
##### [Arguments dynamiques](dynamic-arguments.md)
#### [Composite](composite.md)
##### [Composition de l’activité de base](basic-activity-composition.md)
##### [Bien démarrer avec l’écriture d’une activité personnalisée](getting-started-writing-a-custom-activity.md)
#### [Concepteurs d’activités personnalisées](custom-activity-designers.md)
##### [Concepteurs composites personnalisés : présentateur d’élément de workflow](custom-composite-designers-workflow-item-presenter.md)
##### [Concepteurs composites personnalisés : présentateur d’éléments de workflow](custom-composite-designers-workflow-items-presenter.md)
##### [Programmabilité du magasin des métadonnées](metadata-store-programmability.md)
##### [Utilisation d’ExpressionTextBox dans un concepteur d’activités personnalisées](using-the-expressiontextbox-in-a-custom-activity-designer.md)
##### [Utilisation de la portée d’édition](using-editing-scope.md)
#### [Validation](validation.md)
##### [Types de contraintes](constraint-types.md)
### [Concepteur](designer.md)
#### [Suppression de l’état d’affichage que le concepteur ajoute à un fichier XAML](removing-the-view-state-the-designer-adds-to-an-xaml-file.md)
#### [Programmation de l’arborescence des éléments de modèle](programming-model-item-tree.md)
#### [Extensibilité de la grille des propriétés](property-grid-extensibliity.md)
#### [Service de boîte à outils](toolbox-service.md)
### [Réhébergement du concepteur](designer-rehosting.md)
### [Exécution](execution.md)
#### [Exemple de point de terminaison de gestion de workflow](workflow-management-endpoint-sample.md)
#### [Utilisation de la classe WorkflowInvoker](using-the-workflowinvoker-class.md)
#### [Hôte ReadLine WorkflowApplication](workflowapplication-readline-host.md)
#### [Création et exécution d’une instance de workflow](creating-and-running-a-workflow-instance.md)
#### [Reprise de signet WorkflowHostingEndpoint](workflowhostingendpoint-resume-bookmark.md)
#### [Programme de résolution de signets pour WorkflowHostingEndpoint](bookmark-resolver-for-workflowhostingendpoint.md)
### [Expressions](expressions.md)
### [Migration](migration.md)
#### [Utilisation d’une activité .NET Framework 3.0 ou .NET Framework 3.5 dans un workflow .NET Framework 4.5](using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)
#### [Utilisation d’Interop avec l’échange de données externe](using-interop-with-external-data-exchange.md)
### [Persistance](persistence.md)
#### [Persistance d’une application de workflow](persisting-a-workflow-application.md)
#### [Configuration intégrée](built-in-configuration.md)
#### [SQLStoreExtensibility](sqlstoreextensibility.md)
#### [Activité de promotion de propriétés](property-promotion-activity.md)
### [Exemples de règles](rules-samples.md)
#### [Stratégie avancée](advanced-policy.md)
#### [Stratégie simple](simple-policy.md)
#### [IfElse With Rules](ifelse-with-rules.md)
#### [Groupe d’activités sous conditions](conditioned-activity-group.md)
#### [Traitement des commandes avec une stratégie](order-processing-with-policy.md)
### [Services](services.md)
#### [Report absolu](absolute-delay.md)
#### [Délai durable](durable-delay.md)
#### [Envoi et gestion des erreurs](sending-and-handling-faults.md)
#### [Utilisation de base des activités SendParameters et ReceiveParameters](basic-usage-of-sendparameters-and-receiveparameters-activities.md)
#### [Service uniquement en XAML de base](basic-xaml-only-service.md)
#### [Mise en forme des messages dans les services de workflow](formatting-messages-in-workflow-services.md)
#### [Durable Duplex](durable-duplex.md)
#### [Corrélation basée sur le contenu](content-based-correlation.md)
#### [Mise en cache des canaux avec Send](channel-caching-with-send.md)
#### [Délai durable en XAMLX](durable-delay-in-xamlx.md)
#### [Mise en mémoire tampon de la réception](buffered-receive.md)
#### [Activation XAML](xaml-activation.md)
### [Suivi](tracking.md)
#### [Suivi personnalisé](custom-tracking.md)
#### [Événements de suivi dans Event Tracing for Windows](tracking-events-into-event-tracing-in-windows.md)
#### [Suivi SQL](sql-tracking.md)
#### [Extraire des données WF à l’aide du suivi](extract-wf-data-using-tracking.md)
#### [Suivi à l’aide d’un fichier texte](tracking-using-a-text-file.md)
### [Transactions](transactions.md)
#### [Bases de TransactionScope](basic-transactionscope.md)
#### [Utilisation de TransactedReceiveScope](use-of-transactedreceivescope.md)
#### [Imbrication de TransactionScope dans un service](nesting-of-transactionscope-within-a-service.md)
### [Validation](validation.md)
#### [Validation d’activité externe](external-activity-validation.md)
#### [Validation de base](basic-validation.md)
#### [OverloadGroups](overloadgroups.md)
#### [Validation des relations des activités](activity-relationships-validation.md)
## [Scénario](scenario.md)
### [Bibliothèque d’activités](activity-library.md)
#### [Activité de stratégie dans .NET Framework 4.5](policy-activity-in-net-framework-4-5.md)
#### [Activité personnalisée pour commuter une plage de valeurs](custom-activity-to-switch-on-a-range-of-values.md)
#### [Activité LINQ to Objects](linq-to-objects-activity.md)
#### [Exemple LINQ to SQL](linq-to-sql-sample.md)
#### [Utilisation de l’activité InvokePowerShell](using-the-invokepowershell-activity.md)
#### [Activité RangeEnumeration](rangeenumeration-activity.md)
#### [Activités d’expression régulière](regular-expression-activities.md)
#### [Activité personnalisée SendMail](sendmail-custom-activity.md)
#### [Activité For](for-activity.md)
#### [Activité Wait For Input](wait-for-input-activity.md)
#### [ParallelForEach limité](throttled-parallel-foreach.md)
#### [Activités d’entités](entity-activities.md)
#### [Activités d’accès aux bases de données](database-access-activities.md)
#### [Activité CommentOut](commentout-activity.md)
#### [Activité de stratégie externalisée dans .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)
#### [Activité NoPersistScope](nopersistscope-activity.md)
#### [ForEach non générique](non-generic-foreach.md)
#### [ParallelForEach non générique](non-generic-parallelforeach.md)
#### [Obtenir WorkflowInstanceId](get-workflowinstanceid.md)
### [Services](services.md)
#### [OperationScope](operationscope.md)
#### [Accès à OperationContext](accessing-operationcontext.md)
#### [Corrélation de requête de message LINQ](linq-message-query-correlation.md)
#### [Calculatrice corrélée](correlated-calculator.md)
#### [Sécurisation des services de workflow](securing-workflow-services.md)
#### [Communication asynchrone](asynchronous-communication.md)
### [Transactions](transactions.md)
#### [Exécuter un workflow dans un TransactionScope impératif](execute-a-workflow-in-an-imperative-transactionscope.md)
#### [Étendue du convoi des transactions](transaction-convoy-scope.md)
#### [Restauration de transaction](transaction-rollback.md)
#### [Supprimer l’étendue des transactions](suppress-transaction-scope.md)
#### [Files d’attente avec transaction](transacted-queues.md)
### [Modèle de confirmation automatique](auto-confirm-pattern.md)
### [Scénario StateMachine à l’aide d’une combinaison de FlowChart et de Pick](statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)
### [Intégration de WPF et WF en XAML](wpf-and-wf-integration-in-xaml.md)
### [Boîte à outils de l’ensemble de règles externe](external-ruleset-toolkit.md)
