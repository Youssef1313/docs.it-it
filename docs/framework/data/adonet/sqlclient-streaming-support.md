---
title: Supporto del flusso SqlClient
ms.date: 03/30/2017
ms.assetid: c449365b-470b-4edb-9d61-8353149f5531
ms.openlocfilehash: 9dc7ee573bd011bd18d6c4b8bbd2d147b1fe907f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791404"
---
# <a name="sqlclient-streaming-support"></a>Supporto del flusso SqlClient

Il supporto dello streaming tra SQL Server e un'applicazione (novità di .NET Framework 4,5) supporta i dati non strutturati nel server (documenti, immagini e file multimediali). Un database SQL Server può archiviare oggetti binari di grandi dimensioni (BLOB), ma il recupero di BLOB può utilizzare una grande quantità di memoria.

Il supporto dello streaming da e verso SQL Server semplifica la scrittura di applicazioni che generano flussi di dati, senza dover caricare completamente i dati in memoria, con un minor numero di eccezioni di overflow della memoria.

Il supporto del flusso consentirà inoltre una migliore scalabilità delle applicazioni di livello intermedio, specialmente negli scenari in cui gli oggetti business si connettono a SQL Azure per inviare, recupera e modificare BLOB di grandi dimensioni.

> [!WARNING]
> Le chiamate asincrone non sono supportate se in un'applicazione viene inoltre usata la parola chiave della stringa di connessione `Context Connection`.
>
> I membri aggiunti per supportare il flusso sono usati per recuperare i dati dalle query e per passare parametri a query e stored procedure. La funzionalità di flusso è destinata a scenari di migrazione dei dati e OLTP di base ed è applicabile agli ambienti di migrazione dei dati on-premise e off-premise.

## <a name="streaming-support-from-sql-server"></a>Supporto del flusso da SQL Server

Il supporto del flusso da SQL Server introduce nuove funzionalità <xref:System.Data.Common.DbDataReader> in e <xref:System.Data.SqlClient.SqlDataReader> nelle classi per ottenere <xref:System.IO.Stream>gli oggetti, <xref:System.Xml.XmlReader>e <xref:System.IO.TextReader> e reagire a essi. Queste classi vengono usate per recuperare i dati dalle query. Di conseguenza, il supporto del flusso da SQL Server risolve scenari OLTP e si applica agli ambienti locali e non locali.

I membri seguenti sono stati aggiunti <xref:System.Data.SqlClient.SqlDataReader> a per abilitare il supporto del flusso da SQL Server:

1. <xref:System.Data.SqlClient.SqlDataReader.IsDBNullAsync%2A>

2. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValue%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValueAsync%2A>

4. <xref:System.Data.SqlClient.SqlDataReader.GetStream%2A>

5. <xref:System.Data.SqlClient.SqlDataReader.GetTextReader%2A>

6. <xref:System.Data.SqlClient.SqlDataReader.GetXmlReader%2A>

I membri seguenti sono stati aggiunti <xref:System.Data.Common.DbDataReader> a per abilitare il supporto del flusso da SQL Server:

1. <xref:System.Data.Common.DbDataReader.GetFieldValue%2A>

2. <xref:System.Data.Common.DbDataReader.GetStream%2A>

3. <xref:System.Data.Common.DbDataReader.GetTextReader%2A>

## <a name="streaming-support-to-sql-server"></a>Supporto dello streaming per SQL Server

Il <xref:System.Data.SqlClient.SqlParameter> supporto del flusso per SQL Server introduce nuove funzionalità nella classe in modo che possa accettare e <xref:System.Xml.XmlReader>reagire agli <xref:System.IO.TextReader> oggetti, <xref:System.IO.Stream>e. <xref:System.Data.SqlClient.SqlParameter> viene usato per passare i parametri a query e stored procedure.

L'eliminazione di un oggetto <xref:System.Data.SqlClient.SqlCommand> o la chiamata di <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> deve annullare qualsiasi operazione di flusso. Se un'applicazione invia <xref:System.Threading.CancellationToken>, l'annullamento non è garantito.

I seguenti tipi <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> accetteranno <xref:System.Data.SqlClient.SqlParameter.Value%2A> di <xref:System.IO.Stream>:

- **Binary**

- **VarBinary**

I seguenti tipi <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> accetteranno <xref:System.Data.SqlClient.SqlParameter.Value%2A> di <xref:System.IO.TextReader>:

- **Char**

- **NChar**

- **NVarChar**

- **Xml**

Il tipo **XML** <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> accetterà un <xref:System.Data.SqlClient.SqlParameter.Value%2A> di <xref:System.Xml.XmlReader>.

<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> può accettare valori di tipo <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> e <xref:System.IO.Stream>.

Gli oggetti <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> e <xref:System.IO.Stream> verranno trasferiti fino al valore definito da <xref:System.Data.SqlClient.SqlParameter.Size%2A>.

## <a name="sample----streaming-from-sql-server"></a>Esempio: flusso da SQL Server

Usare il codice Transact-SQL seguente per creare il database di esempio:

```sql
CREATE DATABASE [Demo]
GO
USE [Demo]
GO
CREATE TABLE [Streams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX),
[bindata] VARBINARY(MAX),
[xmldata] XML)
GO
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'This is a test', 0x48656C6C6F, N'<test>value</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Hello, World!', 0x54657374696E67, N'<test>value2</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Another row', 0x666F6F626172, N'<fff>bbb</fff><fff>bbc</fff>')
GO
```

Nell'esempio vengono descritte le operazioni seguenti:

- Evitare di bloccare un thread di interfaccia utente fornendo una modalità asincrona per recuperare i file di grandi dimensioni.

- Trasferire un file di testo di grandi dimensioni da SQL Server .NET Framework 4,5.

- Trasferire un file XML di grandi dimensioni da SQL Server .NET Framework 4,5.

- Recuperare i dati da SQL Server.

- Trasferire file di grandi dimensioni (BLOB) da un database SQL Server a un altro senza esaurire la memoria.

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading.Tasks;
using System.Xml;

namespace StreamingFromServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo";

      static void Main(string[] args) {
         CopyBinaryValueToFile().Wait();
         PrintTextValues().Wait();
         PrintXmlValues().Wait();
         PrintXmlValuesViaNVarChar().Wait();

         Console.WriteLine("Done");
      }

      // Application retrieving a large BLOB from SQL Server in .NET 4.5 using the new asynchronous capability
      private static async Task CopyBinaryValueToFile() {
         string filePath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "binarydata.bin");

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [bindata] FROM [Streams] WHERE [id]=@id", connection)) {
               command.Parameters.AddWithValue("id", 1);

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  if (await reader.ReadAsync()) {
                     if (!(await reader.IsDBNullAsync(0))) {
                        using (FileStream file = new FileStream(filePath, FileMode.Create, FileAccess.Write)) {
                           using (Stream data = reader.GetStream(0)) {

                              // Asynchronously copy the stream from the server to the file we just created
                              await data.CopyToAsync(file);
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Text File from SQL Server in .NET 4.5
      private static async Task PrintTextValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [textdata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire text document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.Write("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.Write("(NULL)");
                     }
                     else {
                        char[] buffer = new char[4096];
                        int charsRead = 0;
                        using (TextReader data = reader.GetTextReader(1)) {
                           do {
                              // Grab each chunk of text and write it to the console
                              // If you are writing to a TextWriter you should use WriteAsync or WriteLineAsync
                              charsRead = await data.ReadAsync(buffer, 0, buffer.Length);
                              Console.Write(buffer, 0, charsRead);
                           } while (charsRead > 0);
                        }
                     }

                     Console.WriteLine();
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      private static async Task PrintXmlValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [xmldata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        using (XmlReader xmlReader = reader.GetXmlReader(1)) {
                           int depth = 1;
                           // NOTE: The XmlReader returned by GetXmlReader does NOT support async operations
                           // See the example below (PrintXmlValuesViaNVarChar) for how to get an XmlReader with asynchronous capabilities
                           while (xmlReader.Read()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    Console.WriteLine("{0}{1}", new string('\t', depth), xmlReader.Value);
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      // This goes via NVarChar and TextReader to enable asynchronous reading
      private static async Task PrintXmlValuesViaNVarChar() {
         XmlReaderSettings xmlSettings = new XmlReaderSettings() {
            // Async must be explicitly enabled in the XmlReaderSettings otherwise the XmlReader will throw exceptions when async methods are called
            Async = true,
            // Since we will immediately wrap the TextReader we are creating in an XmlReader, we will permit the XmlReader to take care of closing\disposing it
            CloseInput = true,
            // If the Xml you are reading is not a valid document (as per <https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6bts1x50(v=vs.100)>) you will need to set the conformance level to Fragment
            ConformanceLevel = ConformanceLevel.Fragment
         };

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();

            // Cast the XML into NVarChar to enable GetTextReader - trying to use GetTextReader on an XML type will throw an exception
            using (SqlCommand command = new SqlCommand("SELECT [id], CAST([xmldata] AS NVARCHAR(MAX)) FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}:", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        // Grab the row as a TextReader, then create an XmlReader on top of it
                        // We are not keeping a reference to the TextReader since the XmlReader is created with the "CloseInput" setting (so it will close the TextReader when needed)
                        using (XmlReader xmlReader = XmlReader.Create(reader.GetTextReader(1), xmlSettings)) {
                           int depth = 1;
                           // The XmlReader above now supports asynchronous operations, so we can use ReadAsync here
                           while (await xmlReader.ReadAsync()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    // Depending on what your data looks like, you should either use Value or GetValueAsync
                                    // Value has less overhead (since it doesn't create a Task), but it may also block if additional data is required
                                    Console.WriteLine("{0}{1}", new string('\t', depth), await xmlReader.GetValueAsync());
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-to-sql-server"></a>Esempio--flusso a SQL Server

Usare il codice Transact-SQL seguente per creare il database di esempio:

```sql
CREATE DATABASE [Demo2]
GO
USE [Demo2]
GO
CREATE TABLE [BinaryStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
CREATE TABLE [TextStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX))
GO
CREATE TABLE [BinaryStreamsCopy] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
```

Nell'esempio vengono descritte le operazioni seguenti:

- Trasferimento di un BLOB di grandi dimensioni a SQL Server in .NET Framework 4,5.

- Trasferimento di un file di testo di grandi dimensioni in SQL Server .NET Framework 4,5.

- Utilizzo della nuova funzionalità asincrona per trasferire un BLOB di grandi dimensioni.

- Uso della nuova funzionalità asincrona e della parola chiave await per trasferire un BLOB di grandi dimensioni.

- Annullamento del trasferimento di un BLOB di grandi dimensioni.

- Flusso da un SQL Server a un altro tramite la nuova funzionalità asincrona.

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingToServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         CreateDemoFiles();

         StreamBLOBToServer().Wait();
         StreamTextToServer().Wait();

         // Create a CancellationTokenSource that will be cancelled after 100ms
         // Typically this token source will be cancelled by a user request (e.g. a Cancel button)
         CancellationTokenSource tokenSource = new CancellationTokenSource();
         tokenSource.CancelAfter(100);
         try {
            CancelBLOBStream(tokenSource.Token).Wait();
         }
         catch (AggregateException ex) {
            // Cancelling an async operation will throw an exception
            // Since we are using the Task's Wait method, this exception will be wrapped in an AggregateException
            // If you were using the 'await' keyword, the compiler would take care of unwrapping the AggregateException
            // Depending on when the cancellation occurs, you can either get an error from SQL Server or from .Net
            if ((ex.InnerException is SqlException) || (ex.InnerException is TaskCanceledException)) {
               // This is an expected exception
               Console.WriteLine("Got expected exception: {0}", ex.InnerException.Message);
            }
            else {
               // Did not expect this exception - re-throw it
               throw;
            }
         }

         Console.WriteLine("Done");
      }

      // This is used to generate the files which are used by the other sample methods
      private static void CreateDemoFiles() {
         Random rand = new Random();
         byte[] data = new byte[1024];
         rand.NextBytes(data);

         using (FileStream file = File.Open("binarydata.bin", FileMode.Create)) {
            file.Write(data, 0, data.Length);
         }

         using (StreamWriter writer = new StreamWriter(File.Open("textdata.txt", FileMode.Create))) {
            writer.Write(Convert.ToBase64String(data));
         }
      }

      // Application transferring a large BLOB to SQL Server in .NET 4.5
      private static async Task StreamBLOBToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Application transferring a large Text File to SQL Server in .NET 4.5
      private static async Task StreamTextToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [TextStreams] (textdata) VALUES (@textdata)", conn)) {
               using (StreamReader file = File.OpenText("textdata.txt")) {

                  // Add a parameter which uses the StreamReader we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@textdata", SqlDbType.NVarChar, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Cancelling the transfer of a large BLOB
      private static async Task CancelBLOBStream(CancellationToken cancellationToken) {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            // We can cancel not only sending the data to the server, but also opening the connection
            await conn.OpenAsync(cancellationToken);

            // Artificially delay the command by 100ms
            using (SqlCommand cmd = new SqlCommand("WAITFOR DELAY '00:00:00:100';INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  // Pass the cancellation token such that the command will be cancelled if needed
                  await cmd.ExecuteNonQueryAsync(cancellationToken);
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-from-one-sql-server-to-another-sql-server"></a>Esempio: streaming da un SQL Server a un altro SQL Server

In questo esempio viene illustrato come trasmettere in modo asincrono un BLOB di grandi dimensioni da un SQL Server a un altro, con supporto per l'annullamento.

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingFromServerToAnother {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         // For this example, we don't want to cancel
         // So we can pass in a "blank" cancellation token
         E2EStream(CancellationToken.None).Wait();

         Console.WriteLine("Done");
      }

      // Streaming from one SQL Server to Another One using the new Async.NET
      private static async Task E2EStream(CancellationToken cancellationToken) {
         using (SqlConnection readConn = new SqlConnection(connectionString)) {
            using (SqlConnection writeConn = new SqlConnection(connectionString)) {

               // Note that we are using the same cancellation token for calls to both connections\commands
               // Also we can start both the connection opening asynchronously, and then wait for both to complete
               Task openReadConn = readConn.OpenAsync(cancellationToken);
               Task openWriteConn = writeConn.OpenAsync(cancellationToken);
               await Task.WhenAll(openReadConn, openWriteConn);

               using (SqlCommand readCmd = new SqlCommand("SELECT [bindata] FROM [BinaryStreams]", readConn)) {
                  using (SqlCommand writeCmd = new SqlCommand("INSERT INTO [BinaryStreamsCopy] (bindata) VALUES (@bindata)", writeConn)) {

                     // Add an empty parameter to the write command which will be used for the streams we are copying
                     // Size is set to -1 to indicate "MAX"
                     SqlParameter streamParameter = writeCmd.Parameters.Add("@bindata", SqlDbType.Binary, -1);

                     // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
                     // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
                     using (SqlDataReader reader = await readCmd.ExecuteReaderAsync(CommandBehavior.SequentialAccess, cancellationToken)) {
                        while (await reader.ReadAsync(cancellationToken)) {
                           // Grab a stream to the binary data in the source database
                           using (Stream dataStream = reader.GetStream(0)) {

                              // Set the parameter value to the stream source that was opened
                              streamParameter.Value = dataStream;

                              // Asynchronously send data from one database to another
                              await writeCmd.ExecuteNonQueryAsync(cancellationToken);
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="see-also"></a>Vedere anche

- [Recupero e modifica di dati in ADO.NET](retrieving-and-modifying-data.md)
