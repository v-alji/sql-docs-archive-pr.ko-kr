---
title: XML 문서 대량 가져오기 및 내보내기 예제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d72c84a7ed84503e0c88d2a46c808196903900b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653387"
---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a><span data-ttu-id="db79d-102">XML 문서 대량 가져오기 및 내보내기 예(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db79d-102">Examples of Bulk Import and Export of XML Documents (SQL Server)</span></span>
    
##  <a name="you-can-bulk-import-xml-documents-into-a-ssnoversion-database-or-bulk-export-them-from-a-ssnoversion-database-this-topic-provides-examples-of-both"></a><a name="top"></a><span data-ttu-id="db79d-103">XML 문서를 데이터베이스로 대량 가져오거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 대량으로 내보낼 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="db79d-103">You can bulk import XML documents into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or bulk export them from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="db79d-104">이 항목에서는 이 두 가지 경우에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-104">This topic provides examples of both.</span></span>  
  
 <span data-ttu-id="db79d-105">다음을 사용하여 데이터 파일의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 또는 분할되지 않은 뷰로 대량 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-105">To bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or non-partitioned view, you can use the following:</span></span>  
  
-   <span data-ttu-id="db79d-106">**bcp** 유틸리티</span><span class="sxs-lookup"><span data-stu-id="db79d-106">**bcp** utility</span></span>  
  
     <span data-ttu-id="db79d-107">**bcp** 유틸리티를 사용하면 분할된 뷰를 포함하여 SELECT 문이 작동하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 모든 위치에서 데이터를 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-107">You can also use the **bcp** utility to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that a SELECT statement works, including partitioned views.</span></span>  
  
-   <span data-ttu-id="db79d-108">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="db79d-108">BULK INSERT</span></span>  
  
-   <span data-ttu-id="db79d-109">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="db79d-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="db79d-110">자세한 내용은 [Bcp 유틸리티를 사용 하 여 대량 데이터 가져오기 및 내보내기 &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) 을 사용 하 여 대량 데이터 가져오기 및 내보내기 [BULK INSERT 또는 OPENROWSET&#40;bulk ... &#41; &#40;SQL Server&#41;를 사용 하 여 대량 데이터 가져오기 ](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db79d-110">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) and [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="db79d-111">예</span><span class="sxs-lookup"><span data-stu-id="db79d-111">Examples</span></span>  
 <span data-ttu-id="db79d-112">다음과 같은 예가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-112">The examples are the following:</span></span>  
  
-   <span data-ttu-id="db79d-113">A.</span><span class="sxs-lookup"><span data-stu-id="db79d-113">A.</span></span> [<span data-ttu-id="db79d-114">XML 데이터를 이진 바이트 스트림으로 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-114">BULK importing XML data as a binary byte stream</span></span>](#binary_byte_stream)  
  
-   <span data-ttu-id="db79d-115">B.</span><span class="sxs-lookup"><span data-stu-id="db79d-115">B.</span></span> [<span data-ttu-id="db79d-116">기존 행에 XML 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-116">Bulk importing XML data in an existing row</span></span>](#existing_row)  
  
-   <span data-ttu-id="db79d-117">C.</span><span class="sxs-lookup"><span data-stu-id="db79d-117">C.</span></span> [<span data-ttu-id="db79d-118">DTD가 포함 된 파일에서 XML 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-118">Bulk importing XML data from a file that contains a DTD</span></span>](#file_contains_dtd)  
  
-   <span data-ttu-id="db79d-119">D.</span><span class="sxs-lookup"><span data-stu-id="db79d-119">D.</span></span> [<span data-ttu-id="db79d-120">서식 파일을 사용 하 여 명시적으로 필드 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="db79d-120">Specifying the field terminator explicitly using a format file</span></span>](#field_terminator_in_format_file)  
  
-   <span data-ttu-id="db79d-121">E.</span><span class="sxs-lookup"><span data-stu-id="db79d-121">E.</span></span> [<span data-ttu-id="db79d-122">XML 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="db79d-122">Bulk exporting XML data</span></span>](#bulk_export_xml_data)  
  
###  <a name="a-bulk-importing-xml-data-as-a-binary-byte-stream"></a><a name="binary_byte_stream"></a> <span data-ttu-id="db79d-123">1.</span><span class="sxs-lookup"><span data-stu-id="db79d-123">A.</span></span> <span data-ttu-id="db79d-124">XML 데이터를 이진 바이트 스트림으로 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-124">Bulk importing XML data as a binary byte stream</span></span>  
 <span data-ttu-id="db79d-125">적용할 인코딩 선언이 있는 파일에서 XML 데이터를 대량으로 가져오는 경우 OPENROWSET(BULK…) 절에 SINGLE_BLOB 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-125">When you bulk import XML data from a file that contains an encoding declaration that you want to apply, specify the SINGLE_BLOB option in the OPENROWSET(BULK...) clause.</span></span> <span data-ttu-id="db79d-126">SINGLE_BLOB 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XML 파서가 XML 선언에 지정된 인코딩 체계에 따라 데이터를 가져오도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-126">The SINGLE_BLOB option makes sure that the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imports the data according to the encoding scheme specified in the XML declaration.</span></span>  
  
#### <a name="sample-table"></a><span data-ttu-id="db79d-127">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="db79d-127">Sample Table</span></span>  
 <span data-ttu-id="db79d-128">예 1을 테스트하려면 `T`예제 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-128">To test example A, you must create sample table `T`.</span></span>  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a><span data-ttu-id="db79d-129">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="db79d-129">Sample Data File</span></span>  
 <span data-ttu-id="db79d-130">예제 A를 실행하려면 먼저`C:\SampleFolder\SampleData3.txt`인코딩 체계를 지정하는 다음 예제 인스턴스가 포함된 UTF-8 인코딩 파일( `UTF-8` )을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-130">Before you can run example A, you must create a UTF-8 encoded file (`C:\SampleFolder\SampleData3.txt`) that contains the following sample instance that specifies the `UTF-8` encoding scheme.</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a><span data-ttu-id="db79d-131">예 1</span><span class="sxs-lookup"><span data-stu-id="db79d-131">Example A</span></span>  
 <span data-ttu-id="db79d-132">이 예에서는 `SINGLE_BLOB` 문에 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 옵션을 사용하여 `SampleData3.txt` 라는 파일에서 데이터를 가져오고 단일 열 테이블( `T`예제 테이블)에 XML 인스턴스를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-132">This example uses the `SINGLE_BLOB` option in an `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement to import data from a file named `SampleData3.txt` and insert an XML instance in the single-column table, sample table `T`.</span></span>  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a><span data-ttu-id="db79d-133">설명</span><span class="sxs-lookup"><span data-stu-id="db79d-133">Remarks</span></span>  
 <span data-ttu-id="db79d-134">이 경우 SINGLE_BLOB을 사용하면 XML 인코딩 선언에 지정된 XML 문서의 인코딩과 서버가 적용한 문자열 코드 페이지 간 불일치를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-134">By using SINGLE_BLOB in this case, you can avoid a mismatch between the encoding of the XML document (as specified by the XML encoding declaration) and the string codepage implied by the server.</span></span>  
  
 <span data-ttu-id="db79d-135">NCLOB 또는 CLOB 데이터 형식을 사용할 경우 코드 페이지 또는 인코딩 충돌이 발생하면 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-135">If you use NCLOB or CLOB data types and run into a codepage or encoding conflict, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="db79d-136">XML 데이터 파일의 내용을 성공적으로 가져오기 위해 XML 선언을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-136">Remove the XML declaration to successfully import the contents of the XML data file.</span></span>  
  
-   <span data-ttu-id="db79d-137">XML 선언에 사용된 인코딩 체계와 일치하는 쿼리의 CODEPAGE 옵션에 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-137">Specify a code page in the CODEPAGE option of the query that matches the encoding scheme that is used in the XML declaration.</span></span>  
  
-   <span data-ttu-id="db79d-138">데이터베이스 데이터 정렬 설정을 비유니코드 XML 인코딩 체계에 맞추거나 불일치를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-138">Match, or resolve, the database collation settings with a non-Unicode XML encoding scheme.</span></span>  
  
 [<span data-ttu-id="db79d-139">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="db79d-139">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="b-bulk-importing-xml-data-in-an-existing-row"></a><a name="existing_row"></a> <span data-ttu-id="db79d-140">2.</span><span class="sxs-lookup"><span data-stu-id="db79d-140">B.</span></span> <span data-ttu-id="db79d-141">기존 행에 XML 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-141">Bulk importing XML data in an existing row</span></span>  
 <span data-ttu-id="db79d-142">이 예에서는 `OPENROWSET` 대량 행 집합 공급자를 사용하여 `T`예제 테이블의 기존 행에 XML 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-142">This example uses the `OPENROWSET` bulk rowset provider to add an XML instance to an existing row or rows in sample table `T`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db79d-143">이 예를 실행하려면 예 1에서 제공한 테스트 스크립트를 먼저 완료해야 합니다. 해당 예는 `tempdb.dbo.T` 테이블을 만들고 `SampleData3.txt`에서 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-143">To run this example, you must first complete the test script provided in example A. That example creates the `tempdb.dbo.T` table and bulk imports data from `SampleData3.txt`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="db79d-144">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="db79d-144">Sample Data File</span></span>  
 <span data-ttu-id="db79d-145">예 2에서는 앞의 예에서 사용된 `SampleData3.txt` 예제 데이터 파일의 수정된 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-145">Example B uses a modified version of the `SampleData3.txt` sample data file from the preceding example.</span></span> <span data-ttu-id="db79d-146">이 예를 실행하려면 다음과 같이 이 파일의 내용을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-146">To run this example, modify the content of this file as follows:</span></span>  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a><span data-ttu-id="db79d-147">예 2</span><span class="sxs-lookup"><span data-stu-id="db79d-147">Example B</span></span>  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 [<span data-ttu-id="db79d-148">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="db79d-148">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="c-bulk-importing-xml-data-from-a-file-that-contains-a-dtd"></a><a name="file_contains_dtd"></a> <span data-ttu-id="db79d-149">3.</span><span class="sxs-lookup"><span data-stu-id="db79d-149">C.</span></span> <span data-ttu-id="db79d-150">DTD가 포함된 파일에 있는 XML 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="db79d-150">Bulk importing XML data from a file that contains a DTD</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db79d-151">XML 환경에서 반드시 필요한 경우가 아니면 DTD(문서 유형 정의)에 대한 지원을 설정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-151">We recommended that you not enable support for Document Type Definitions (DTDs) if it is not required in your XML environment.</span></span> <span data-ttu-id="db79d-152">DTD 지원을 설정하면 서버가 공격 받을 수 있는 노출 영역이 증가하며 서비스 거부 공격에 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-152">Turning on DTD support increases the attackable surface area of your server, and may expose it to a denial-of-service attack.</span></span> <span data-ttu-id="db79d-153">DTD 지원을 설정해야 할 경우에는 신뢰할 수 있는 XML 문서만 처리하여 이러한 보안 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-153">If you must enable DTD support, you can reduce this security risk by processing only trusted XML documents.</span></span>  
  
 <span data-ttu-id="db79d-154">[bcp](../../tools/bcp-utility.md) 명령을 사용하여 DTD가 들어 있는 파일에서 XML 데이터를 가져오려고 하면 다음과 유사한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-154">During an attempt to use a [bcp](../../tools/bcp-utility.md) command to import XML data from a file that contains a DTD, an error similar to the following can occur:</span></span>  
  
 <span data-ttu-id="db79d-155">"SQLState = 42000, NativeError = 6359"</span><span class="sxs-lookup"><span data-stu-id="db79d-155">"SQLState = 42000, NativeError = 6359"</span></span>  
  
 <span data-ttu-id="db79d-156">"오류 = [Microsoft][SQL Server Native Client][ SQL Server]내부 하위 집합 DTD를 사용하여 XML 구문 분석을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-156">"Error = [Microsoft][SQL Server Native Client][ SQL Server]Parsing XML with internal subset DTDs not allowed.</span></span> <span data-ttu-id="db79d-157">CONVERT에 스타일 옵션 2를 사용하여 제한된 내부 하위 집합 DTD 지원을 활성화하십시오."</span><span class="sxs-lookup"><span data-stu-id="db79d-157">Use CONVERT with style option 2 to enable limited internal subset DTD support."</span></span>  
  
 <span data-ttu-id="db79d-158">"BCP 복사 %s이(가) 실패했습니다."</span><span class="sxs-lookup"><span data-stu-id="db79d-158">"BCP copy %s failed"</span></span>  
  
 <span data-ttu-id="db79d-159">이 문제를 해결하려면 `OPENROWSET(BULK...)` 함수를 사용한 다음, 명령의 `CONVERT` 절에 `SELECT` 옵션을 지정하여 DTD가 포함된 데이터 파일에서 XML 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-159">To work around this problem, you can import XML data from a data file that contains a DTD by using the `OPENROWSET(BULK...)` function and then specifying the `CONVERT` option in the `SELECT` clause of the command.</span></span> <span data-ttu-id="db79d-160">명령의 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-160">The basic syntax for the command is:</span></span>  
  
 `INSERT ... SELECT CONVERT(...) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a><span data-ttu-id="db79d-161">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="db79d-161">Sample Data File</span></span>  
 <span data-ttu-id="db79d-162">이 대량 가져오기 예를 테스트하려면 먼저 다음 예제 인스턴스를 포함하는 파일(`C:\temp\Dtdfile.xml`)을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-162">Before you can test this bulk import example, create a file (`C:\temp\Dtdfile.xml`) that contains the following sample instance:</span></span>  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="db79d-163">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="db79d-163">Sample Table</span></span>  
 <span data-ttu-id="db79d-164">예 3에서는 다음 `T1` 문에 의해 생성된 `CREATE TABLE` 예제 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-164">Example C uses the `T1` sample table that is created by the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a><span data-ttu-id="db79d-165">예 3</span><span class="sxs-lookup"><span data-stu-id="db79d-165">Example C</span></span>  
 <span data-ttu-id="db79d-166">이 예에서는 `OPENROWSET(BULK...)` 을 사용하고 `CONVERT` 절에 `SELECT` 옵션을 지정하여 `Dtdfile.xml` 의 XML 데이터를 `T1`예제 테이블로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-166">This example uses `OPENROWSET(BULK...)` and specifies the `CONVERT` option in the `SELECT` clause to import the XML data from `Dtdfile.xml` into sample table `T1`.</span></span>  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 <span data-ttu-id="db79d-167">`INSERT` 문을 실행하면 XML에서 DTD가 잘리고 `T1` 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-167">After the `INSERT` statement executes, the DTD is stripped from the XML and stored in the `T1` table.</span></span>  
  
 [<span data-ttu-id="db79d-168">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="db79d-168">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="d-specifying-the-field-terminator-explicitly-using-a-format-file"></a><a name="field_terminator_in_format_file"></a> <span data-ttu-id="db79d-169">4.</span><span class="sxs-lookup"><span data-stu-id="db79d-169">D.</span></span> <span data-ttu-id="db79d-170">서식 파일을 사용하여 명시적으로 필드 종결자 지정</span><span class="sxs-lookup"><span data-stu-id="db79d-170">Specifying the field terminator explicitly using a format file</span></span>  
 <span data-ttu-id="db79d-171">다음 예에서는 XML 문서 `Xmltable.dat`를 대량으로 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-171">The following example shows how to bulk import the following XML document, `Xmltable.dat`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="db79d-172">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="db79d-172">Sample Data File</span></span>  
 <span data-ttu-id="db79d-173">`Xmltable.dat` 의 문서에는 두 개의 XML 값이 있으며 각 행마다 하나의 XML 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-173">The document in `Xmltable.dat` contains two XML values, one for each row.</span></span> <span data-ttu-id="db79d-174">첫 번째 XML 값은 UTF-16으로 인코딩되고 두 번째 값은 UTF-8로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-174">The first XML value is encoded with UTF-16, and the second value is encoded with UTF-8.</span></span>  
  
 <span data-ttu-id="db79d-175">이 데이터 파일의 내용은 다음과 같은 16진수 덤프로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-175">The contents of this data file are shown in the following Hex dump:</span></span>  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="db79d-176">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="db79d-176">Sample Table</span></span>  
 <span data-ttu-id="db79d-177">XML 문서를 대량으로 가져오거나 내보낼 때는 문서에 나타날 가능성이 없는 [필드 종결자](specify-field-and-row-terminators-sql-server.md) 를 사용해야 합니다. 예를 들어 다음과 같이`\0`: `z`문자 앞에 오는 일련의 Null( `\0\0\0\0z`) 4개를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-177">When you bulk import or export an XML document, you should use a [field terminator](specify-field-and-row-terminators-sql-server.md) that cannot possibly appear in any of the documents; for example, a series of four nulls (`\0`) followed by the letter `z`: `\0\0\0\0z`.</span></span>  
  
 <span data-ttu-id="db79d-178">이 예에서는 `xTable` 예제 테이블에 대해 이 필드 종결자를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-178">This example shows how to use this field terminator for the `xTable` sample table.</span></span> <span data-ttu-id="db79d-179">이 예제 테이블을 만들려면 다음 `CREATE TABLE` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-179">To create this sample table, use the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a><span data-ttu-id="db79d-180">예제 서식 파일</span><span class="sxs-lookup"><span data-stu-id="db79d-180">Sample Format File</span></span>  
 <span data-ttu-id="db79d-181">필드 종결자는 서식 파일에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-181">The field terminator must be specified in the format file.</span></span> <span data-ttu-id="db79d-182">예 4에서는 다음을 포함하는 `Xmltable.fmt` 라는 비 XML 서식 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-182">Example D uses a non-XML format file named `Xmltable.fmt` that contains the following:</span></span>  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 <span data-ttu-id="db79d-183">이 서식 파일을 사용하면 `xTable` 명령이나 `bcp` 또는 `BULK INSERT` 문을 사용하여 XML 문서를 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 테이블로 대량 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-183">You can use this format file to bulk import XML documents into the `xTable` table by using a `bcp` command or a `BULK INSERT` or `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="db79d-184">예 4</span><span class="sxs-lookup"><span data-stu-id="db79d-184">Example D</span></span>  
 <span data-ttu-id="db79d-185">이 예에서는 `Xmltable.fmt` 문에 `BULK INSERT` 서식 파일을 사용하여 `Xmltable.dat`라는 XML 데이터 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-185">This example uses the `Xmltable.fmt` format file in a `BULK INSERT` statement to import the contents of an XML data file named `Xmltable.dat`.</span></span>  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 [<span data-ttu-id="db79d-186">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="db79d-186">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="e-bulk-exporting-xml-data"></a><a name="bulk_export_xml_data"></a> <span data-ttu-id="db79d-187">5.</span><span class="sxs-lookup"><span data-stu-id="db79d-187">E.</span></span> <span data-ttu-id="db79d-188">XML 데이터 대량 내보내기</span><span class="sxs-lookup"><span data-stu-id="db79d-188">Bulk exporting XML data</span></span>  
 <span data-ttu-id="db79d-189">다음 예에서는 `bcp` 를 사용하여 동일한 XML 서식 파일로 앞의 예에서 만든 테이블에서 XML 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-189">The following example uses `bcp` to bulk export XML data from the table that is created in the preceding example by using the same XML format file.</span></span> <span data-ttu-id="db79d-190">다음 `bcp` 명령에서 `<server_name>` 및 `<instance_name>` 은 적절한 값으로 바꿔야 하는 자리 표시자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-190">In the following `bcp` command, `<server_name>` and `<instance_name>` represent placeholders that must be replaced with appropriate values:</span></span>  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db79d-191">에서는 XML 데이터가 데이터베이스에 유지되면 XML 인코딩을 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-191">does not save the XML encoding when XML data is persisted in the database.</span></span> <span data-ttu-id="db79d-192">그러므로 XML 필드의 원래 인코딩은 XML 데이터를 내보내면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-192">Therefore, the original encoding of XML fields is not available when XML data is exported.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db79d-193">에서는 XML 데이터를 내보낼 때 UTF-16 인코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db79d-193">uses UTF-16 encoding when exporting XML data.</span></span>  
  
 [<span data-ttu-id="db79d-194">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="db79d-194">&#91;Top&#93;</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="db79d-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db79d-195">See Also</span></span>  
 <span data-ttu-id="db79d-196">[INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db79d-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="db79d-197">[SELECT 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db79d-197">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="db79d-198">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="db79d-198">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="db79d-199">[데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db79d-199">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="db79d-200">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db79d-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="db79d-201">OPENROWSET&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="db79d-201">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
