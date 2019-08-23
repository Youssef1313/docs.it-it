---
title: 'Procedura: Creare una tabella a livello di codice'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964165"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="0a1be-102">Procedura: Creare una tabella a livello di codice</span><span class="sxs-lookup"><span data-stu-id="0a1be-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="0a1be-103">Negli esempi seguenti viene illustrato come creare un oggetto a <xref:System.Windows.Documents.Table> livello di codice e compilarlo con il contenuto.</span><span class="sxs-lookup"><span data-stu-id="0a1be-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="0a1be-104">Il contenuto della tabella è ripartito in cinque righe (rappresentate da <xref:System.Windows.Documents.TableRow> oggetti contenuti in un <xref:System.Windows.Documents.Table.RowGroups%2A> oggetto) e sei colonne ( <xref:System.Windows.Documents.TableColumn> rappresentate da oggetti).</span><span class="sxs-lookup"><span data-stu-id="0a1be-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="0a1be-105">Le righe vengono usate per scopi di presentazione diversi, ad esempio una riga è destinata a contenere il titolo dell'intera tabella, una riga di intestazione a descrivere le colonne di dati nella tabella e una riga di piè di pagina a fornire informazioni di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="0a1be-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="0a1be-106">Si noti che i concetti di righe di "titolo", "intestazione" e "piè di pagina" non sono inerenti alla tabella, ma fanno semplicemente riferimento a righe con caratteristiche diverse.</span><span class="sxs-lookup"><span data-stu-id="0a1be-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="0a1be-107">Le celle della tabella contengono il contenuto effettivo, che può essere costituito da testo, immagini o quasi tutti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gli altri elementi.</span><span class="sxs-lookup"><span data-stu-id="0a1be-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a1be-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-108">Example</span></span>  
 <span data-ttu-id="0a1be-109">Viene innanzitutto creato <xref:System.Windows.Documents.FlowDocument> un oggetto per ospitare l' <xref:System.Windows.Documents.Table>oggetto e viene <xref:System.Windows.Documents.FlowDocument>creato <xref:System.Windows.Documents.Table> un nuovo oggetto che viene aggiunto al contenuto di.</span><span class="sxs-lookup"><span data-stu-id="0a1be-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="0a1be-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-110">Example</span></span>  
 <span data-ttu-id="0a1be-111">Successivamente, vengono <xref:System.Windows.Documents.TableColumn> creati sei oggetti e aggiunti alla <xref:System.Windows.Documents.Table.Columns%2A> raccolta della tabella, con una formattazione applicata.</span><span class="sxs-lookup"><span data-stu-id="0a1be-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a1be-112">Si noti che la <xref:System.Windows.Documents.Table.Columns%2A> raccolta della tabella usa l'indicizzazione standard in base zero.</span><span class="sxs-lookup"><span data-stu-id="0a1be-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="0a1be-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-113">Example</span></span>  
 <span data-ttu-id="0a1be-114">Viene quindi creata una riga del titolo che viene aggiunta alla tabella con l'applicazione di alcuni elementi di formattazione.</span><span class="sxs-lookup"><span data-stu-id="0a1be-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="0a1be-115">La riga del titolo può contenere una sola cella che si estende su tutte e sei le colonne della tabella.</span><span class="sxs-lookup"><span data-stu-id="0a1be-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="0a1be-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-116">Example</span></span>  
 <span data-ttu-id="0a1be-117">Successivamente, viene creata e aggiunta alla tabella una riga di intestazione, per la quale vengono create celle in cui viene inserito contenuto.</span><span class="sxs-lookup"><span data-stu-id="0a1be-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="0a1be-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-118">Example</span></span>  
 <span data-ttu-id="0a1be-119">Successivamente, viene creata e aggiunta alla tabella una riga per i dati, per la quale vengono create celle in cui viene inserito contenuto.</span><span class="sxs-lookup"><span data-stu-id="0a1be-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="0a1be-120">La compilazione di questa riga è simile alla compilazione della riga di intestazione, con l'applicazione di una formattazione leggermente diversa.</span><span class="sxs-lookup"><span data-stu-id="0a1be-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="0a1be-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a1be-121">Example</span></span>  
 <span data-ttu-id="0a1be-122">Infine, viene creata, aggiunta e formattata una riga di piè di pagina.</span><span class="sxs-lookup"><span data-stu-id="0a1be-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="0a1be-123">Analogamente alla riga del titolo, il piè di pagina contiene una sola cella che si estende su tutte e sei le colonne della tabella.</span><span class="sxs-lookup"><span data-stu-id="0a1be-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="0a1be-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0a1be-124">See also</span></span>

- [<span data-ttu-id="0a1be-125">Cenni preliminari sull'elemento Table</span><span class="sxs-lookup"><span data-stu-id="0a1be-125">Table Overview</span></span>](table-overview.md)
