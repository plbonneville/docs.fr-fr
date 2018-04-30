### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a><span data-ttu-id="6d30b-101">La période de blocage du pool de connexions pour les bases de données Azure SQL Database est supprimée</span><span class="sxs-lookup"><span data-stu-id="6d30b-101">Connection pool blocking period for Azure SQL databases is removed</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6d30b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6d30b-102">Details</span></span>|<span data-ttu-id="6d30b-103">À compter de .NET Framework 4.6.2, pour les demandes d’ouverture de connexion envoyées aux bases de données Azure SQL Database connues (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de), la période de blocage du pool de connexions est supprimée et les erreurs d’ouverture de connexion ne sont pas mises en cache.</span><span class="sxs-lookup"><span data-stu-id="6d30b-103">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de), the connection pool blocking period is removed, and connection open errors are not cached.</span></span> <span data-ttu-id="6d30b-104">Chaque nouvelle tentative de demande d’ouverture de connexion se produira presque immédiatement après les erreurs de connexion temporaires.</span><span class="sxs-lookup"><span data-stu-id="6d30b-104">Attempts to retry connection open requests will occur almost immediately after transient connection errors.</span></span> <span data-ttu-id="6d30b-105">Ce changement permet aux demandes d’ouverture de connexion d’être retentées immédiatement pour les bases de données Azure SQL Database, ce qui améliore les performances des applications cloud.</span><span class="sxs-lookup"><span data-stu-id="6d30b-105">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud- enabled apps.</span></span> <span data-ttu-id="6d30b-106">Pour toutes les autres tentatives de connexion, la période de blocage du pool de connexions continue d’être appliquée. Dans .NET Framework 4.6.1 et les versions antérieures, quand une application rencontre un échec temporaire lors de la connexion à une base de données, la connexion ne peut pas être retentée rapidement, car le pool de connexions met l’erreur en cache, puis l’affiche de nouveau pendant un délai de 5 secondes à 1 minute.</span><span class="sxs-lookup"><span data-stu-id="6d30b-106">For all other connection attempts, the connection pool blocking period continues to be enforced.In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 minute.</span></span> <span data-ttu-id="6d30b-107">Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="6d30b-107">For more information, see [SQL Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="6d30b-108">Ce comportement pose problème pour les connexions aux bases de données SQL Azure, qui échouent souvent avec des erreurs temporaires, généralement rétablies au bout de quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="6d30b-108">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="6d30b-109">La fonctionnalité de blocage du pool de connexions signifie que l’application ne peut pas se connecter à la base de données pendant une période prolongée, même si la base de données est disponible et que l’application doit être affichée en quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="6d30b-109">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available and the app needs to render within a few seconds.</span></span>|
|<span data-ttu-id="6d30b-110">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6d30b-110">Suggestion</span></span>|<span data-ttu-id="6d30b-111">Si ce comportement n’est pas souhaitable, la période de blocage du pool de connexions peut être configurée en définissant la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> introduite dans .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="6d30b-111">If this behavior is undesirable, the connection pool blocking period can be configured by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> property introduced in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="6d30b-112">La valeur de la propriété est un membre de l’énumération <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> qui peut prendre l’une des trois valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d30b-112">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> enumeration that can take either of three values:</span></span><ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul><span data-ttu-id="6d30b-113">Vous pouvez restaurer le comportement précédent en affectant la valeur <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="6d30b-113">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.</span></span>|
|<span data-ttu-id="6d30b-114">Portée</span><span class="sxs-lookup"><span data-stu-id="6d30b-114">Scope</span></span>|<span data-ttu-id="6d30b-115">Mineur</span><span class="sxs-lookup"><span data-stu-id="6d30b-115">Minor</span></span>|
|<span data-ttu-id="6d30b-116">Version</span><span class="sxs-lookup"><span data-stu-id="6d30b-116">Version</span></span>|<span data-ttu-id="6d30b-117">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6d30b-117">4.6.2</span></span>|
|<span data-ttu-id="6d30b-118">Type</span><span class="sxs-lookup"><span data-stu-id="6d30b-118">Type</span></span>|<span data-ttu-id="6d30b-119">Runtime</span><span class="sxs-lookup"><span data-stu-id="6d30b-119">Runtime</span></span>|
|<span data-ttu-id="6d30b-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6d30b-120">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
