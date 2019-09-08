---
title: Compilazione di un dataset mediante uno o più oggetti REF CURSOR
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
ms.openlocfilehash: b80edb522d26896d33cacff757390e5a7bf757e6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783868"
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a><span data-ttu-id="14857-102">Compilazione di un dataset mediante uno o più oggetti REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="14857-102">Filling a DataSet Using One or More REF CURSORs</span></span>
<span data-ttu-id="14857-103">Nell'esempio Visual Basic seguente viene eseguita una stored procedure PL/SQL che restituisce due parametri REF CURSOR e consente la compilazione di un tipo <xref:System.Data.DataSet> con le righe restituite.</span><span class="sxs-lookup"><span data-stu-id="14857-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
    "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Dim ds As New DataSet()  
    Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter( _  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
       ParameterDirection.Output  
  
    Dim da As New OracleDataAdapter(cmd)  
    da.TableMappings.Add("Table", "Emp")  
    da.TableMappings.Add("Table1", "Dept")  
    da.Fill(ds)  
  
    ds.Relations.Add("EmpDept", ds.Tables("Dept").Columns("Deptno"), _  
      ds.Tables("Emp").Columns("Deptno"), False)  
  
    DataGrid1.DataSource = ds.Tables("Dept")  
  End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="14857-104">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="14857-104">See also</span></span>

- [<span data-ttu-id="14857-105">Oggetti REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="14857-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="14857-106">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14857-106">ADO.NET Overview</span></span>](ado-net-overview.md)
