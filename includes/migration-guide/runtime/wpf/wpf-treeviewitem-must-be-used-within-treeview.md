### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a><span data-ttu-id="c731d-101">Les éléments TreeViewItem WPF doivent être utilisés dans un contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="c731d-101">WPF TreeViewItem must be used within a TreeView</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c731d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c731d-102">Details</span></span>|<span data-ttu-id="c731d-103">Une modification a été introduite dans 4.5, qui limite l’utilisation des éléments <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> en dehors d’un <xref:System.Windows.Controls.TreeView?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c731d-103">A change was introduced in 4.5 that restricts usage of <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> elements outside of a <xref:System.Windows.Controls.TreeView?displayProperty=name>.</span></span> <span data-ttu-id="c731d-104">Cette restriction est applicable dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c731d-104">This manifests under the following conditions:</span></span><ul><li><span data-ttu-id="c731d-105">L’objet visuel parent de <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> n’est pas un panneau.</span><span class="sxs-lookup"><span data-stu-id="c731d-105"><xref:System.Windows.Controls.TreeViewItem?displayProperty=name>'s visual parent is not a panel.</span></span> <span data-ttu-id="c731d-106">(Un <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> généré pour un <xref:System.Windows.Controls.TreeView?displayProperty=name> aura un panneau comme parent)</span><span class="sxs-lookup"><span data-stu-id="c731d-106">(A <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> generated for a <xref:System.Windows.Controls.TreeView?displayProperty=name> will have a panel as its parent)</span></span></li><li><span data-ttu-id="c731d-107">Le <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> est un descendant d’un <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> agissant comme « hôte des éléments » pour un contrôle de liste (ListBox, DataGrid, ListView, etc.).</span><span class="sxs-lookup"><span data-stu-id="c731d-107">The <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> is a descendant of a <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> acting as the &quot;items host&quot; for a list control (ListBox, DataGrid, ListView, etc.).</span></span> <span data-ttu-id="c731d-108">Il n’est pas nécessaire d’activer la virtualisation.</span><span class="sxs-lookup"><span data-stu-id="c731d-108">Virtualization doesn't need to be enabled.</span></span></li><li><span data-ttu-id="c731d-109">Le <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> peut faire défiler les éléments (<code>ScrollUnit=&quot;Item&quot;</code>).</span><span class="sxs-lookup"><span data-stu-id="c731d-109">The <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> is item-scrolling (<code>ScrollUnit=&quot;Item&quot;</code>).</span></span></li><li><span data-ttu-id="c731d-110"><code>VirtualizingStackPanel.MakeVisible(v)</code> est appelé pour faire défiler un élément <code>v</code> dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="c731d-110">Someone calls <code>VirtualizingStackPanel.MakeVisible(v)</code> to scroll an element <code>v</code> into view.</span></span> <span data-ttu-id="c731d-111">Vous pouvez faire ceci de manière explicite ou implicite de différentes façons. Le moyen le plus courant est de cliquer sur <code>v</code> pour lui donner le focus clavier.</span><span class="sxs-lookup"><span data-stu-id="c731d-111">This can be done explicitly, or implicitly in a number of ways; perhaps the most common way is simply clicking on <code>v</code> to give it the keyboard focus.</span></span></li><li><span data-ttu-id="c731d-112">La chaîne du parent visuel de <code>v</code> à <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> passe par <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c731d-112">The visual-parent chain from <code>v</code> to the <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> passes through the <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</span></span></li></ul><span data-ttu-id="c731d-113">En d’autres termes, cela se produit quand un <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> est utilisé en dehors d’un <xref:System.Windows.Controls.TreeView?displayProperty=name>, et que l’utilisateur clique sur un descendant du <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> pour l’afficher.</span><span class="sxs-lookup"><span data-stu-id="c731d-113">In other words, this is seen when a <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> is used outside of a <xref:System.Windows.Controls.TreeView?displayProperty=name>, and the user clicks on a descendant of the <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> to bring it into view.</span></span> <span data-ttu-id="c731d-114">Si le <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> n’a pas de descendant pouvant recevoir le focus, vous ne rencontrez jamais ce problème.</span><span class="sxs-lookup"><span data-stu-id="c731d-114">If the <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> has no focusable descendants, you'll never see this issue.</span></span> <span data-ttu-id="c731d-115">Cela peut se produire quand un <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> est la racine d’un DataTemplate.</span><span class="sxs-lookup"><span data-stu-id="c731d-115">An example of a situation where this is hit is when a <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> is the root of a DataTemplate.</span></span> <span data-ttu-id="c731d-116">Une exception InvalidCastException est alors levée dans le cadre de WPF.</span><span class="sxs-lookup"><span data-stu-id="c731d-116">When this issue is hit, there is an InvalidCastException that occurs within the WPF framework.</span></span>|
|<span data-ttu-id="c731d-117">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c731d-117">Suggestion</span></span>|<span data-ttu-id="c731d-118">Un correctif sera mis à disposition pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="c731d-118">A hotfix will be made available for this.</span></span>|
|<span data-ttu-id="c731d-119">Portée</span><span class="sxs-lookup"><span data-stu-id="c731d-119">Scope</span></span>|<span data-ttu-id="c731d-120">Mineur</span><span class="sxs-lookup"><span data-stu-id="c731d-120">Minor</span></span>|
|<span data-ttu-id="c731d-121">Version</span><span class="sxs-lookup"><span data-stu-id="c731d-121">Version</span></span>|<span data-ttu-id="c731d-122">4.5</span><span class="sxs-lookup"><span data-stu-id="c731d-122">4.5</span></span>|
|<span data-ttu-id="c731d-123">Type</span><span class="sxs-lookup"><span data-stu-id="c731d-123">Type</span></span>|<span data-ttu-id="c731d-124">Runtime</span><span class="sxs-lookup"><span data-stu-id="c731d-124">Runtime</span></span>|
