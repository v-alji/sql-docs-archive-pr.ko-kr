---
title: XML 대량 로드 소개 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f3e0e78edd967e5fcb7377312c1811d34cb1ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728140"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="841ae-102">XML 대량 로드 소개(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="841ae-102">Introduction to XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="841ae-103">XML 대량 로드는 반구조화된 XML 데이터를 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 로드할 수 있게 해주는 독립 실행형 COM 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-103">XML Bulk Load is a stand-alone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="841ae-104">INSERT 문과 OPENXML 함수를 사용하여 XML 데이터를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 삽입할 수 있습니다. 하지만 많은 양의 XML 데이터를 삽입해야 하는 경우 대량 로드 유틸리티가 더 나은 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-104">You can insert XML data into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database by using an INSERT statement and the OPENXML function; however, the Bulk Load utility provides better performance when you need to insert large amounts of XML data.</span></span>  
  
 <span data-ttu-id="841ae-105">XML 대량 로드 개체 모델의 Execute 메서드는 두 개의 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-105">The Execute method of the XML Bulk Load object model takes two parameters:</span></span>  
  
-   <span data-ttu-id="841ae-106">주석이 추가된 XSD(XML 스키마 정의) 또는 XDR(XML-Data Reduced) 스키마.</span><span class="sxs-lookup"><span data-stu-id="841ae-106">An annotated XML Schema Definition (XSD) or XML-Data Reduced (XDR) schema.</span></span> <span data-ttu-id="841ae-107">XML 대량 로드 유틸리티는 XML 데이터를 삽입할 SQL Server 테이블을 식별할 때 스키마에 지정된 주석과 이 매핑 스키마를 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-107">The XML Bulk Load utility interprets this mapping schema and the annotations that are specified in the schema in identifying the SQL Server tables into which the XML data is to be inserted.</span></span>  
  
-   <span data-ttu-id="841ae-108">XML 문서 또는 문서 조각(문서 조각은 단일 최상위 요소가 없는 문서임).</span><span class="sxs-lookup"><span data-stu-id="841ae-108">An XML document or document fragment (a document fragment is a document without a single top-level element).</span></span> <span data-ttu-id="841ae-109">XML 대량 로드에서 읽을 수 있는 파일 이름이나 스트림을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-109">A file name or a stream from which XML Bulk Load can read can be specified.</span></span>  
  
 <span data-ttu-id="841ae-110">XML 대량 로드는 매핑 스키마를 해석하고 XML 데이터를 삽입할 테이블을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-110">XML Bulk Load interprets the mapping schema and identifies the table(s) into which the XML data is to be inserted.</span></span>  
  
 <span data-ttu-id="841ae-111">사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능에 대해 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-111">It is assumed that you are familiar with the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="841ae-112">주석이 추가된 XSD 및 XDR 스키마.</span><span class="sxs-lookup"><span data-stu-id="841ae-112">Annotated XSD and XDR schemas.</span></span> <span data-ttu-id="841ae-113">주석이 추가 된 XSD 스키마에 대 한 자세한 내용은 주석이 추가 된 [Xsd 스키마 &#40;SQLXML 4.0&#41;를 ](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="841ae-113">For more information about annotated XSD schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="841ae-114">주석이 추가 된 XDR 스키마에 대 한 자세한 내용은 [SQLXML 4.0&#41;에서 사용 되지 &#40;주석이 추가 된 Xdr 스키마 ](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="841ae-114">For information about annotated XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="841ae-115">BULK INSERT 문, bcp 유틸리티와 같은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 대량 삽입 메커니즘.</span><span class="sxs-lookup"><span data-stu-id="841ae-115">bulk insert mechanisms, such as the [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement and the bcp utility.</span></span> <span data-ttu-id="841ae-116">자세한 내용은 [BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 및 [bcp 유틸리티](../../../tools/bcp-utility.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="841ae-116">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) and [bcp Utility](../../../tools/bcp-utility.md).</span></span>  
  
## <a name="streaming-of-xml-data"></a><span data-ttu-id="841ae-117">XML 데이터 스트리밍</span><span class="sxs-lookup"><span data-stu-id="841ae-117">Streaming of XML Data</span></span>  
 <span data-ttu-id="841ae-118">원본 XML 문서가 클 수 있으므로 대량 로드 처리를 위해 전체 문서를 메모리로 읽어 오지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-118">Because the source XML document can be large, the entire document is not read into memory for bulk load processing.</span></span> <span data-ttu-id="841ae-119">대신 XML 대량 로드에서 XML 데이터를 스트림으로 해석하고 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-119">Instead, XML Bulk Load interprets the XML data as a stream and reads it.</span></span> <span data-ttu-id="841ae-120">유틸리티는 데이터를 읽는 동안 데이터베이스 테이블을 식별하고, XML 데이터 원본에서 적절한 레코드를 생성한 다음 삽입을 위해 해당 레코드를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-120">As the utility reads the data, it identifies the database table(s), generates the appropriate record(s) from the XML data source, and then sends the record(s) to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="841ae-121">예를 들어 다음 소스 XML 문서는 **\<Customer>** 요소와 **\<Order>** 자식 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-121">For example, the following source XML document consists of **\<Customer>** elements and **\<Order>** child elements:</span></span>  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 <span data-ttu-id="841ae-122">XML 대량 로드는 요소를 읽을 때 **\<Customer>** Customertable에 대 한 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-122">As XML Bulk Load reads the **\<Customer>** element, it generates a record for the Customertable.</span></span> <span data-ttu-id="841ae-123">**\</Customer>** XML 대량 로드는 끝 태그를 읽을 때 해당 레코드를의 테이블에 삽입 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="841ae-123">When it reads the **\</Customer>** end tag, XML Bulk Load inserts that record into the table in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="841ae-124">동일한 방식으로 요소를 읽을 때 **\<Order>** XML 대량 로드는 Ordertable에 대 한 레코드를 생성 한 다음 끝 태그를 읽을 때 해당 레코드를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 삽입 합니다 **\</Order>** .</span><span class="sxs-lookup"><span data-stu-id="841ae-124">In the same way, when it reads the **\<Order>** element, XML Bulk Load generates a record for the Ordertable, and then inserts that record into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table upon reading the **\</Order>** end tag.</span></span>  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a><span data-ttu-id="841ae-125">트랜잭션 및 비트랜잭션 XML 대량 로드 작업</span><span class="sxs-lookup"><span data-stu-id="841ae-125">Transacted and Nontransacted XML Bulk Load Operations</span></span>  
 <span data-ttu-id="841ae-126">XML 대량 로드는 트랜잭션 또는 비트랜잭션 모드로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-126">XML Bulk Load can operate in either a transacted or a nontransacted mode.</span></span> <span data-ttu-id="841ae-127">일반적으로 트랜잭션이 아닌 모드에서 대량 로드 하는 경우 (즉, 트랜잭션 속성이 FALSE로 설정 됨) 다음 조건 중 하나가 true 인 경우 성능이 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-127">Performance is usually optimal if you are bulk loading in a nontransacted mode: that is, the Transaction property is set to FALSE) and either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="841ae-128">데이터를 대량 로드되는 테이블이 인덱스 없이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-128">The tables into which the data is bulk loaded are empty with no indexes.</span></span>  
  
-   <span data-ttu-id="841ae-129">테이블에 데이터와 고유한 인덱스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-129">The tables have data and unique indexes.</span></span>  
  
 <span data-ttu-id="841ae-130">트랜잭션이 아닌 방법을 사용하면 대량 로드 프로세스에서 문제가 발생할 경우 부분 롤백은 발생할 수 있어도 롤백이 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-130">The nontransacted approach does not guarantee a rollback if something goes wrong in the bulk load process (although partial rollbacks can happen).</span></span> <span data-ttu-id="841ae-131">트랜잭션이 아닌 대량 로드는 데이터베이스가 비어 있을 때 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-131">The nontransacted bulk load is appropriate when the database is empty.</span></span> <span data-ttu-id="841ae-132">따라서 문제가 발생할 경우 데이터베이스를 지우고 XML 대량 로드를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-132">Therefore, if something does go wrong, you can clean the database and start XML Bulk Load again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="841ae-133">트랜잭션이 아닌 모드에서 XML 대량 로드는 기본 내부 트랜잭션을 사용하고 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-133">In nontransacted mode, XML Bulk Load uses a default internal transaction and commits it.</span></span> <span data-ttu-id="841ae-134">Transaction 속성이 TRUE로 설정 된 경우 XML 대량 로드는이 트랜잭션에서 commit을 호출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-134">When the Transaction property is set to TRUE, XML Bulk Load does not call commit on this transaction.</span></span>  
  
 <span data-ttu-id="841ae-135">Transaction 속성이 TRUE로 설정 된 경우 XML 대량 로드는 매핑 스키마에서 식별 되는 각 테이블에 대해 하나씩 임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-135">If the Transaction property is set to TRUE, XML Bulk Load creates temporary files, one for each table that is identified in the mapping schema.</span></span> <span data-ttu-id="841ae-136">XML 대량 로드는 먼저 원본 XML 문서의 레코드를 이러한 임시 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-136">XML Bulk Load first stores the records from the source XML document in these temporary files.</span></span> <span data-ttu-id="841ae-137">그런 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT 문이 파일에서 이러한 레코드를 검색하여 해당 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-137">Then, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement retrieves these records from the files and stores them in the corresponding tables.</span></span> <span data-ttu-id="841ae-138">TempFilePath 속성을 사용 하 여 이러한 임시 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-138">You can specify the location for these temporary files by using the TempFilePath property.</span></span> <span data-ttu-id="841ae-139">XML 대량 로드에 사용하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 계정에 이 경로에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-139">You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account used with XML Bulk Load has access to this path.</span></span> <span data-ttu-id="841ae-140">TempFilePath 속성이 지정 되지 않은 경우 TEMP 환경 변수에 지정 된 기본 파일 경로를 사용 하 여 임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-140">If the TempFilePath property is not specified, the default file path that is specified in the TEMP environment variable is used to create the temporary files.</span></span>  
  
 <span data-ttu-id="841ae-141">Transaction 속성이 FALSE (기본 설정)로 설정 된 경우 XML 대량 로드는 OLE DB 인터페이스 IRowsetFastLoad를 사용 하 여 데이터를 대량 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-141">If the Transaction property is set to FALSE (the default setting), XML Bulk Load uses the OLE DB interface IRowsetFastLoad to bulk load the data.</span></span>  
  
 <span data-ttu-id="841ae-142">ConnectionString 속성이 연결 문자열을 설정 하 고 Transaction 속성이 TRUE로 설정 된 경우 XML 대량 로드는 자체 트랜잭션 컨텍스트에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-142">If the ConnectionString property sets the connection string, and the Transaction property is set to TRUE, XML Bulk Load operates in its own transaction context.</span></span> <span data-ttu-id="841ae-143">예를 들어 XML 대량 로드에서 해당 트랜잭션을 시작하고 필요에 따라 커밋 또는 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-143">(For example, XML Bulk Load starts its own transaction, and commits or rolls back as appropriate.)</span></span>  
  
 <span data-ttu-id="841ae-144">ConnectionCommand 속성이 기존 연결 개체와의 연결을 설정 하 고 Transaction 속성이 TRUE로 설정 되 면, XML 대량 로드는 각각 성공 또는 실패 하는 경우 COMMIT 또는 ROLLBACK 문을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-144">If the ConnectionCommand property sets the connection with an existing connection object and the Transaction property is set to TRUE, XML Bulk Load does not issue a COMMIT or ROLLBACK statement in the case of a success or a failure, respectively.</span></span> <span data-ttu-id="841ae-145">오류가 있으면 XML 대량 로드는 해당 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-145">If there is an error, XML Bulk Load returns the appropriate error message.</span></span> <span data-ttu-id="841ae-146">COMMIT 또는 ROLLBACK 문의 사용 여부는 대량 로드를 시작한 클라이언트에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-146">The decision to issue a COMMIT or ROLLBACK statement is left to the client that initiated the bulk load.</span></span> <span data-ttu-id="841ae-147">XML 대량 로드에 사용 되는 연결 개체는 ICommand 형식 이거나 ADO 명령 개체 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-147">The connection object that is used for XML Bulk Load should be of type ICommand or be an ADO command object.</span></span>  
  
 <span data-ttu-id="841ae-148">SQLXML 4.0에서 ConnectionObject는 Transaction 속성이 FALSE로 설정 된 상태에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-148">In SQLXML 4.0, a ConnectionObject cannot be used with the Transaction property set to FALSE.</span></span> <span data-ttu-id="841ae-149">전달 된 세션에서 두 개 이상의 IRowsetFastLoad 인터페이스를 열 수 없기 때문에 비 트랜잭션 모드는 ConnectionObject에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="841ae-149">The nontransacted mode is not supported with a ConnectionObject because it is impossible to open more than one IRowsetFastLoad interface on a passed-in session.</span></span>  
  
  
