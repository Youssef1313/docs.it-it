---
title: Generazione di codice in LINQ to SQL
ms.date: 03/30/2017
ms.assetid: ddcbdaa1-e7fa-4d85-a379-313b49965c07
ms.openlocfilehash: 551322637e6e04b9be7d558c51e063fead7f84f4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247964"
---
# <a name="code-generation-in-linq-to-sql"></a><span data-ttu-id="ea5be-102">Generazione di codice in LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ea5be-102">Code Generation in LINQ to SQL</span></span>
<span data-ttu-id="ea5be-103">È possibile generare codice per rappresentare un database usando il Object Relational Designer o lo strumento da riga di comando SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="ea5be-103">You can generate code to represent a database by using either the Object Relational Designer or the SQLMetal command-line tool.</span></span> <span data-ttu-id="ea5be-104">In entrambi i casi, si verifica la generazione di codice end-to-end in tre fasi:</span><span class="sxs-lookup"><span data-stu-id="ea5be-104">In either case, end-to-end code generation occurs in three stages:</span></span>  
  
1. <span data-ttu-id="ea5be-105">L' *estrattore DBML* estrae le informazioni sullo schema dal database e riassembla le informazioni in un file DBML in formato XML.</span><span class="sxs-lookup"><span data-stu-id="ea5be-105">The *DBML Extractor* extracts schema information from the database and reassembles the information into an XML-formatted DBML file.</span></span>  
  
2. <span data-ttu-id="ea5be-106">Il file DBML viene sottoposta a scansione dal *validator dbml* per individuare eventuali errori.</span><span class="sxs-lookup"><span data-stu-id="ea5be-106">The DBML file is scanned by the *DBML Validator* for errors.</span></span>  
  
3. <span data-ttu-id="ea5be-107">Se non sono presenti errori di convalida, il file viene passato al generatore di codice.</span><span class="sxs-lookup"><span data-stu-id="ea5be-107">If no validation errors appear, the file is passed to the Code Generator.</span></span>  
  
 <span data-ttu-id="ea5be-108">Per altre informazioni, vedere [SqlMetal.exe (strumento per la generazione del codice)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ea5be-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="ea5be-109">Gli sviluppatori che usano Visual Studio possono anche usare la Object Relational Designer per generare il codice.</span><span class="sxs-lookup"><span data-stu-id="ea5be-109">Developers using Visual Studio can also use the Object Relational Designer to generate code.</span></span> <span data-ttu-id="ea5be-110">Vedere [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="ea5be-110">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
## <a name="dbml-extractor"></a><span data-ttu-id="ea5be-111">Estrattore DBML</span><span class="sxs-lookup"><span data-stu-id="ea5be-111">DBML Extractor</span></span>  
 <span data-ttu-id="ea5be-112">L'estrattore DBML è [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un componente che accetta i metadati del database come input e produce un file DBML come output.</span><span class="sxs-lookup"><span data-stu-id="ea5be-112">The DBML Extractor is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that takes database metadata as input and produces a DBML file as output.</span></span>  
  
## <a name="code-generator"></a><span data-ttu-id="ea5be-113">Generatore di codice</span><span class="sxs-lookup"><span data-stu-id="ea5be-113">Code Generator</span></span>  
 <span data-ttu-id="ea5be-114">Il generatore di codice è [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un componente che converte i file DBML in Visual Basic, C#o file di mapping XML.</span><span class="sxs-lookup"><span data-stu-id="ea5be-114">The Code Generator is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that translates DBML files to Visual Basic, C#, or XML mapping files.</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="ea5be-115">File di definizione di XML Schema</span><span class="sxs-lookup"><span data-stu-id="ea5be-115">XML Schema Definition File</span></span>  
 <span data-ttu-id="ea5be-116">Il file di mapping DBML deve essere convalidato in base alla seguente definizione dello schema come file XSD.</span><span class="sxs-lookup"><span data-stu-id="ea5be-116">The DBML file must be valid against the following schema definition as an XSD file.</span></span>  
  
 <span data-ttu-id="ea5be-117">È necessario distinguere questo file di definizione dello schema dal file di definizione dello schema usato per convalidare un file di mapping esterno.</span><span class="sxs-lookup"><span data-stu-id="ea5be-117">Distinguish this schema definition file from the schema definition file that is used to validate an external mapping file.</span></span> <span data-ttu-id="ea5be-118">Per ulteriori informazioni, vedere [mapping esterno](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="ea5be-118">For more information, see [External Mapping](external-mapping.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea5be-119">Gli utenti di Visual Studio troveranno inoltre questo file XSD nella finestra di dialogo XML Schema come "DbmlSchema. xsd".</span><span class="sxs-lookup"><span data-stu-id="ea5be-119">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "DbmlSchema.xsd".</span></span> <span data-ttu-id="ea5be-120">Per usare correttamente il file XSD per la convalida di un file dbml [, vedere Procedura: Convalidare file](how-to-validate-dbml-and-external-mapping-files.md)di mapping esterni e dbml.</span><span class="sxs-lookup"><span data-stu-id="ea5be-120">To use the XSD file correctly for validating a DBML file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/dbml/2007" xmlns="http://schemas.microsoft.com/linqtosql/dbml/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Connection" type="Connection" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="EntityNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="ContextNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="Class" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
    <xs:attribute name="BaseType" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
    <xs:attribute name="ExternalMapping" type="xs:boolean" use="optional" />  
    <xs:attribute name="Serialization" type="SerializationMode" use="optional" />  
    <xs:attribute name="EntityBase" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:all>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
      <xs:element name="InsertFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="UpdateFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="DeleteFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
    </xs:all>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="IdRef" type="xs:IDREF" use="optional" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsReadOnly" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDelayLoaded" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="Cardinality" type="Cardinality" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="HasMultipleResults" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunction">  
    <xs:sequence>  
      <xs:element name="Argument" type="TableFunctionParameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Return" type="TableFunctionReturn" minOccurs="0" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="FunctionId" type="xs:IDREF" use="required" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Parameter" type="xs:string" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionParameter">  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Version" type="Version" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionReturn">  
    <xs:attribute name="Member" type="xs:string" use="required" />  
  </xs:complexType>  
  <xs:complexType name="Connection">  
    <xs:attribute name="Provider" type="xs:string" use="required" />  
    <xs:attribute name="Mode" type="ConnectionMode" use="optional" />  
    <xs:attribute name="ConnectionString" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsObjectName" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsPropertyName" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="ConnectionMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ConnectionString" />  
      <xs:enumeration value="AppSettings" />  
      <xs:enumeration value="WebSettings" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AccessModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Public" />  
      <xs:enumeration value="Internal" />  
      <xs:enumeration value="Protected" />  
      <xs:enumeration value="ProtectedInternal" />  
      <xs:enumeration value="Private" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="SerializationMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="None" />  
      <xs:enumeration value="Unidirectional" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Version">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Current" />  
      <xs:enumeration value="Original" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ClassModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Sealed" />  
      <xs:enumeration value="Abstract" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="MemberModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Virtual" />  
      <xs:enumeration value="Override" />  
      <xs:enumeration value="New" />  
      <xs:enumeration value="NewVirtual" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Cardinality">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="One" />  
      <xs:enumeration value="Many" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="sample-dbml-file"></a><span data-ttu-id="ea5be-121">File DBML di esempio</span><span class="sxs-lookup"><span data-stu-id="ea5be-121">Sample DBML File</span></span>  
 <span data-ttu-id="ea5be-122">Il codice seguente è un estratto dal file DBML creato dal database di esempio Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea5be-122">The following code is an excerpt from the DBML file created from the Northwind sample database.</span></span> <span data-ttu-id="ea5be-123">È possibile generare l'intero file usando SQLMetal con l'opzione **/XML** .</span><span class="sxs-lookup"><span data-stu-id="ea5be-123">You can generate the whole file by using SQLMetal with the **/xml** option.</span></span> <span data-ttu-id="ea5be-124">Per altre informazioni, vedere [SqlMetal.exe (strumento per la generazione del codice)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ea5be-124">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<Database Name="northwnd" Class="Northwnd" xmlns="http://schemas.microsoft.com/dsltools/DLinqML">  
  
  <Table Name="Customers">  
    <Type Name="Customer">  
      <Column Name="CustomerID" Type="System.String" DbType="NChar(5) NOT NULL" IsPrimaryKey="True" CanBeNull="False" />  
      <Column Name="CompanyName" Type="System.String" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="ContactTitle" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="Address" Type="System.String" DbType="NVarChar(60)" CanBeNull="True" />  
      <Column Name="City" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Region" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="PostalCode" Type="System.String" DbType="NVarChar(10)" CanBeNull="True" />  
      <Column Name="Country" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Phone" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Column Name="Fax" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="CustomerCustomerDemo" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="Orders" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea5be-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea5be-125">See also</span></span>

- [<span data-ttu-id="ea5be-126">Informazioni di base</span><span class="sxs-lookup"><span data-stu-id="ea5be-126">Background Information</span></span>](background-information.md)
- <span data-ttu-id="ea5be-127">[External Mapping](external-mapping.md) (Mapping esterno)</span><span class="sxs-lookup"><span data-stu-id="ea5be-127">[External Mapping](external-mapping.md)</span></span>
- [<span data-ttu-id="ea5be-128">Procedura: Generare il modello a oggetti come file esterno</span><span class="sxs-lookup"><span data-stu-id="ea5be-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
- [<span data-ttu-id="ea5be-129">Download di database di esempio</span><span class="sxs-lookup"><span data-stu-id="ea5be-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="ea5be-130">Riferimento</span><span class="sxs-lookup"><span data-stu-id="ea5be-130">Reference</span></span>](reference.md)
