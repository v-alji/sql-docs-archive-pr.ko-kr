---
title: 서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7de0b5ce486f187a1bdd27197984aa3c411f4a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648386"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a><span data-ttu-id="d52e3-102">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d52e3-102">Use a Format File to Map Table Columns to Data-File Fields (SQL Server)</span></span>
  <span data-ttu-id="d52e3-103">데이터 파일은 테이블의 해당 열에서 서로 다른 순서로 정렬된 필드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-103">A data file can contain fields arranged in a different order from the corresponding columns in the table.</span></span> <span data-ttu-id="d52e3-104">이 항목에서는 테이블 열과 서로 다른 순서로 필드가 정렬된 데이터 파일에 맞게 수정된 비 XML 및 XML 서식 파일에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-104">This topic presents both non-XML and XML format files that have been modified to accommodate a data file whose fields are arranged in a different order from the table columns.</span></span> <span data-ttu-id="d52e3-105">수정된 서식 파일은 데이터 필드를 해당 테이블 열로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-105">The modified format file maps the data fields to their corresponding table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d52e3-106">비 XML 서식 파일 또는 XML 서식 파일을 사용 하 여 데이터 파일을 테이블에 대량으로 가져올 수 있습니다. **bcp** 명령, BULK INSERT 문 또는 INSERT ... SELECT \* FROM OPENROWSET (BULK ...) 문</span><span class="sxs-lookup"><span data-stu-id="d52e3-106">Either a non-XML format file or an XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="d52e3-107">자세한 내용은 [서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d52e3-107">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="d52e3-108">예제 테이블 및 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="d52e3-108">Sample Table and Data File</span></span>  
 <span data-ttu-id="d52e3-109">이 항목의 수정된 서식 파일의 예는 다음 테이블 및 데이터 파일을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-109">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="d52e3-110">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="d52e3-110">Sample Table</span></span>  
 <span data-ttu-id="d52e3-111">이 항목의 예에서는 `myTestOrder` 스키마의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 생성된 `dbo` 라는 테이블이 필요하며</span><span class="sxs-lookup"><span data-stu-id="d52e3-111">The examples in this topic require that a table named `myTestOrder` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="d52e3-112">이 테이블을 만들려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-112">To create this table, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a><span data-ttu-id="d52e3-113">데이터 파일</span><span class="sxs-lookup"><span data-stu-id="d52e3-113">Data File</span></span>  
 <span data-ttu-id="d52e3-114">`myTestOrder-c.txt`데이터 파일에는 다음 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-114">The data file, `myTestOrder-c.txt`, contains the following records:</span></span>  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 <span data-ttu-id="d52e3-115">`myTestSkipCol2-c.dat`에서 `myTestSkipCol` 테이블로 데이터를 대량으로 가져오려면 서식 파일은 첫 번째 데이터 필드를 `Col3`으로, 두 번째 데이터 필드를 `Col2`로, 세 번째 데이터 필드를 `Col1`로, 네 번째 데이터 필드를 `Col4`로 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-115">To bulk import data from `myTestSkipCol2-c.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col3`, the second data field to `Col2`, the third data field to `Col1`, and the fourth data field to `Col4`.</span></span>  
  
## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="d52e3-116">비 XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="d52e3-116">Using a Non-XML Format File</span></span>  
 <span data-ttu-id="d52e3-117">해당 데이터 필드의 위치를 나타내는 열의 순서 값을 변경하면 열 매핑 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-117">You can change the order of a column mapping by changing the order value for the column to indicate the position of the corresponding data field.</span></span>  
  
 <span data-ttu-id="d52e3-118">다음 비 XML 서식 파일 예제에서는 `myTestOrder.fmt`의 필드를 `myTestOrder-c.txt` 테이블의 열에 매핑하는 `myTestOrder` 서식 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-118">The following sample non-XML format file presents a format file, `myTestOrder.fmt`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table.</span></span> <span data-ttu-id="d52e3-119">데이터 파일 및 테이블을 만드는 방법은 이 항목의 앞부분에 나오는 "예제 테이블 및 데이터 파일"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d52e3-119">For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="d52e3-120">서식 파일은 문자 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-120">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="d52e3-121">서식 파일에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-121">The format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d52e3-122">비 XML 서식 파일의 레이아웃에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d52e3-122">For more information about the layout of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="d52e3-123">예제</span><span class="sxs-lookup"><span data-stu-id="d52e3-123">Example</span></span>  
 <span data-ttu-id="d52e3-124">다음 예에서는 `BULK INSERT` 문에서 비 XML 서식 파일인 `myTestOrder-c.txt`를 사용하여 `myTestOrder` 데이터 파일에서 `myTestOrder.fmt` 예제 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-124">The following example uses a `BULK INSERT` statement to bulk import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.fmt` non-XML format file.</span></span>  
  
 <span data-ttu-id="d52e3-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a><span data-ttu-id="d52e3-126">XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="d52e3-126">Using an XML Format File</span></span>  
 <span data-ttu-id="d52e3-127">다음 비 XML 서식 파일 예제에서는 `myTestOrder.xml`의 필드를 `myTestOrder-c.txt` 테이블의 열에 매핑하는 서식 파일인 `myTestOrder`을 보여 줍니다. 데이터 파일 및 테이블을 만드는 방법은 이 항목의 앞부분에 나오는 "예제 테이블 및 데이터 파일"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d52e3-127">The following sample non-XML format file presents a format file, `myTestOrder.xml`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="d52e3-128">`myTestOrder.xml` 서식 파일에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-128">The `myTestOrder.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d52e3-129">XML 스키마의 구문 및 추가 XML 서식 파일 예제에 대한 내용은 [XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d52e3-129">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="d52e3-130">예제</span><span class="sxs-lookup"><span data-stu-id="d52e3-130">Example</span></span>  
 <span data-ttu-id="d52e3-131">다음 예에서는 `OPENROWSET` 대량 행 집합 공급자에서 XML 서식 파일인 `myTestOrder-c.txt` 을 사용하여 `myTestOrder` 데이터 파일에서 `myTestOrder.xml` 예제 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-131">The following example uses the `OPENROWSET` bulk rowset provider to import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.xml` XML format file.</span></span> <span data-ttu-id="d52e3-132">`INSERT... SELECT` 문은 SELECT 목록에서 열 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-132">The `INSERT... SELECT` statement specifies the column list in the select list.</span></span>  
  
 <span data-ttu-id="d52e3-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d52e3-133">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d52e3-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d52e3-134">See Also</span></span>  
 <span data-ttu-id="d52e3-135">[서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d52e3-135">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="d52e3-136">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d52e3-136">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
