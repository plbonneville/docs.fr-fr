### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="3592a-101">L’analyse des objets System.Uri respecte la norme RFC 3987</span><span class="sxs-lookup"><span data-stu-id="3592a-101">System.Uri parsing adheres to RFC 3987</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3592a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3592a-102">Details</span></span>|<span data-ttu-id="3592a-103">L’analyse URI a changé à différents niveaux dans le .NET 4.5.</span><span class="sxs-lookup"><span data-stu-id="3592a-103">URI parsing has changed in several ways in .NET 4.5.</span></span> <span data-ttu-id="3592a-104">Notez, cependant, que ces changements affectent uniquement le code qui cible le .NET 4.5.</span><span class="sxs-lookup"><span data-stu-id="3592a-104">Note, however, that these changes only affect code targeting .NET 4.5.</span></span> <span data-ttu-id="3592a-105">Si un fichier binaire cible le .NET 4.0, l’ancien comportement est appliqué.</span><span class="sxs-lookup"><span data-stu-id="3592a-105">If a binary targets .NET 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="3592a-106">Les changements appliqués à l’analyse URI dans le .NET 4.5 sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="3592a-106">Changes to URI parsing in .NET 4.5 include:</span></span><ul><li><span data-ttu-id="3592a-107">L’analyse des URI effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="3592a-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span></li><li><span data-ttu-id="3592a-108">Le formulaire C de normalisation Unicode n’est appliqué que sur la partie hôte de l’URI.</span><span class="sxs-lookup"><span data-stu-id="3592a-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span></li><li><span data-ttu-id="3592a-109">Les URI mailto: non valides génèrent désormais une exception.</span><span class="sxs-lookup"><span data-stu-id="3592a-109">Invalid mailto: URIs will now cause an exception.</span></span></li><li><span data-ttu-id="3592a-110">Les espaces à la fin d’un segment de chemin sont désormais conservés.</span><span class="sxs-lookup"><span data-stu-id="3592a-110">Trailing dots at the end of a path segment are now preserved.</span></span></li><li><span data-ttu-id="3592a-111">Les URI <code>file://</code> n’échappent pas le caractère <code>?</code>.</span><span class="sxs-lookup"><span data-stu-id="3592a-111"><code>file://</code> URIs do not escape the <code>?</code> character.</span></span></li><li><span data-ttu-id="3592a-112">Les caractères de contrôle Unicode allant de <code>U+0080</code> à <code>U+009F</code> ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3592a-112">Unicode control characters <code>U+0080</code> through <code>U+009F</code> are not supported.</span></span></li><li><span data-ttu-id="3592a-113">Les virgules <code>,</code> ou <code>%2c</code> ne sont pas automatiquement sans séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="3592a-113">Comma characters <code>,</code> or <code>%2c</code> are not automatically unescaped.</span></span></li></ul>|
|<span data-ttu-id="3592a-114">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3592a-114">Suggestion</span></span>|<span data-ttu-id="3592a-115">Si l’ancienne sémantique d’analyse URI du .NET 4.0 est nécessaire (et c’est souvent le cas), elle peut être utilisée en ciblant le .NET 4.0.</span><span class="sxs-lookup"><span data-stu-id="3592a-115">If the old .NET 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET 4.0.</span></span> <span data-ttu-id="3592a-116">Pour cela, utilisez un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> sur l’assembly ou modifiez les propriétés du projet dans l’interface utilisateur du système de projet de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3592a-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>|
|<span data-ttu-id="3592a-117">Portée</span><span class="sxs-lookup"><span data-stu-id="3592a-117">Scope</span></span>|<span data-ttu-id="3592a-118">Majeur</span><span class="sxs-lookup"><span data-stu-id="3592a-118">Major</span></span>|
|<span data-ttu-id="3592a-119">Version</span><span class="sxs-lookup"><span data-stu-id="3592a-119">Version</span></span>|<span data-ttu-id="3592a-120">4.5</span><span class="sxs-lookup"><span data-stu-id="3592a-120">4.5</span></span>|
|<span data-ttu-id="3592a-121">Type</span><span class="sxs-lookup"><span data-stu-id="3592a-121">Type</span></span>|<span data-ttu-id="3592a-122">Reciblage</span><span class="sxs-lookup"><span data-stu-id="3592a-122">Retargeting</span></span>|
|<span data-ttu-id="3592a-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="3592a-123">Affected APIs</span></span>|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|
