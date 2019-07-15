---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802452"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="b029f-101">La persistenza SQL del flusso di lavoro aggiunge cluster della chiave primaria e non consente i valori null in alcune colonne</span><span class="sxs-lookup"><span data-stu-id="b029f-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b029f-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="b029f-102">Details</span></span>|<span data-ttu-id="b029f-103">A partire da .NET Framework 4.7 le tabelle create per SQL Workflow Instance Store (SWIS) dallo script SqlWorkflowInstanceStoreSchema.sql usano chiavi primarie cluster.</span><span class="sxs-lookup"><span data-stu-id="b029f-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="b029f-104">Per questo motivo le identità non supportano i valori <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="b029f-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="b029f-105">Questa modifica non altera il funzionamento di SWIS.</span><span class="sxs-lookup"><span data-stu-id="b029f-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="b029f-106">Gli aggiornamenti sono stati apportati per supportare la replica transazionale di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b029f-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="b029f-107">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="b029f-107">Suggestion</span></span>|<span data-ttu-id="b029f-108">Per l'applicazione di questa modifica è necessario applicare il file con estensione sql SqlWorkflowInstanceStoreSchemaUpgrade.sql alle installazioni esistenti.</span><span class="sxs-lookup"><span data-stu-id="b029f-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="b029f-109">Le nuove installazioni del database dispongono automaticamente della modifica.</span><span class="sxs-lookup"><span data-stu-id="b029f-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="b029f-110">Ambito</span><span class="sxs-lookup"><span data-stu-id="b029f-110">Scope</span></span>|<span data-ttu-id="b029f-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b029f-111">Edge</span></span>|
|<span data-ttu-id="b029f-112">Versione</span><span class="sxs-lookup"><span data-stu-id="b029f-112">Version</span></span>|<span data-ttu-id="b029f-113">4.7</span><span class="sxs-lookup"><span data-stu-id="b029f-113">4.7</span></span>|
|<span data-ttu-id="b029f-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="b029f-114">Type</span></span>|<span data-ttu-id="b029f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b029f-115">Runtime</span></span>|

