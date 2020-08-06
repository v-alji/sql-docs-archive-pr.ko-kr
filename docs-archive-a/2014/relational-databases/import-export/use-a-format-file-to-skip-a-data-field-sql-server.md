---
title: 서식 파일을 사용하여 데이터 필드 건너뛰기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d3f78c3c97c5bbe862867d5f51ff35f57d147df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661663"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a><span data-ttu-id="1aa9e-102">서식 파일을 사용하여 데이터 필드 건너뛰기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1aa9e-102">Use a Format File to Skip a Data Field (SQL Server)</span></span>
  <span data-ttu-id="1aa9e-103">데이터 파일에는 테이블의 열 수보다 많은 필드를 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-103">A data file can contain more fields than the number of columns in the table.</span></span> <span data-ttu-id="1aa9e-104">이 항목에서는 테이블 열을 해당 데이터 필드에 매핑하고 나머지 필드는 무시하는 방법으로 데이터 파일에 더 많은 필드를 수용하도록 비 XML 서식 파일과 XML 서식 파일 모두를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-104">This topic describes modifying both non-XML and XML format files to accommodate a data file with more fields by mapping the table columns to the corresponding data fields and ignoring the extra fields.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1aa9e-105">비 XML 서식 파일 또는 XML 서식 파일은 **bcp** 명령, BULK INSERT 문 또는 INSERT ...를 사용 하 여 데이터 파일을 테이블에 대량으로 가져오는 데 사용할 수 있습니다. SELECT \* FROM OPENROWSET (BULK ...) 문</span><span class="sxs-lookup"><span data-stu-id="1aa9e-105">Either a non-XML or XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="1aa9e-106">자세한 내용은 [서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-106">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-data-file-and-table"></a><span data-ttu-id="1aa9e-107">예제 데이터 파일 및 테이블</span><span class="sxs-lookup"><span data-stu-id="1aa9e-107">Sample Data File and Table</span></span>  
 <span data-ttu-id="1aa9e-108">이 항목의 수정된 서식 파일의 예는 다음 테이블 및 데이터 파일을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-108">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="1aa9e-109">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="1aa9e-109">Sample Table</span></span>  
 <span data-ttu-id="1aa9e-110">이 예에서는 `myTestSkipField` 스키마의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 생성된 `dbo` 라는 테이블이 필요하며</span><span class="sxs-lookup"><span data-stu-id="1aa9e-110">The examples require that a table named `myTestSkipField` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="1aa9e-111">이 테이블을 만들려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-111">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="1aa9e-112">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="1aa9e-112">Sample Data File</span></span>  
 <span data-ttu-id="1aa9e-113">`myTestSkipField-c.dat`데이터 파일에는 다음 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-113">The data file, `myTestSkipField-c.dat`, contains the following records:</span></span>  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 <span data-ttu-id="1aa9e-114">`myTestSkipField-c.dat` 의 데이터를 `myTestSkipField` 테이블로 대량으로 가져오려면 서식 파일에서 다음과 같은 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-114">To bulk import data from `myTestSkipField-c.dat` into the `myTestSkipField` table, the format file must do the following:</span></span>  
  
-   <span data-ttu-id="1aa9e-115">첫 번째 데이터 필드를 첫 번째 열인 `PersonID`에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-115">Map the first data field to the first column, `PersonID`.</span></span>  
  
-   <span data-ttu-id="1aa9e-116">두 번째 데이터 필드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-116">Skip the second data field.</span></span>  
  
-   <span data-ttu-id="1aa9e-117">세 번째 데이터 필드를 두 번째 열인 `FirstName`에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-117">Map the third data field to the second column, `FirstName`.</span></span>  
  
-   <span data-ttu-id="1aa9e-118">네 번째 데이터 필드를 세 번째 열인 `LastName`에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-118">Map the fourth data field to the third column, `LastName`.</span></span>  
  
## <a name="non-xml-format-file-for-more-data-fields"></a><span data-ttu-id="1aa9e-119">더 많은 데이터 필드에 사용되는 비 XML 서식 파일</span><span class="sxs-lookup"><span data-stu-id="1aa9e-119">Non-XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="1aa9e-120">다음 `myTestSkipField.fmt` 서식 파일은 `myTestSkipField-c.dat`의 필드를 `myTestSkipField` 테이블의 열로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-120">The following format file, `myTestSkipField.fmt`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="1aa9e-121">서식 파일은 문자 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-121">The format file uses character data format.</span></span> <span data-ttu-id="1aa9e-122">이때 열 매핑을 건너뛰려면 해당 서식 파일의 `ExtraField` 열에서와 같이 열 순서 값을 0으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-122">Skipping a column mapping requires changing its column order value to 0, as shown for the `ExtraField` column in the format file.</span></span>  
  
 <span data-ttu-id="1aa9e-123">`myTestSkipField.fmt` 서식 파일에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-123">The `myTestSkipField.fmt` format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1aa9e-124">비 XML 서식 파일 구문에 대한 자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-124">For information about the syntax of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aa9e-125">예</span><span class="sxs-lookup"><span data-stu-id="1aa9e-125">Examples</span></span>  
 <span data-ttu-id="1aa9e-126">다음 예에서는 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 서식 파일을 사용하는 `myTestSkipField.fmt` 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-126">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.fmt` format file.</span></span> <span data-ttu-id="1aa9e-127">또한 `myTestSkipField-c.dat` 데이터 파일을 `myTestSkipField` 테이블로 대량 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-127">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="1aa9e-128">예제 테이블 및 데이터 파일을 만들려면 이 항목의 앞부분에 나오는 "예제 데이터 파일 및 테이블"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-128">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="1aa9e-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-129">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a><span data-ttu-id="1aa9e-130">더 많은 데이터 필드에 사용되는 XML 서식 파일</span><span class="sxs-lookup"><span data-stu-id="1aa9e-130">XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="1aa9e-131">이 예에서 제공하는 서식 파일은 `myTestSkipField.xml`이라는 다른 서식 파일을 기반으로 합니다. 이 서식 파일은 문자 데이터 형식 전체를 사용하며 해당 필드는 `myTestSkipField` 테이블 열의 수와 순서에 정확히 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-131">The format file presented in this example is based on another format file, `myTestSkipField.xml`, which uses character data format throughout and whose fields correspond exactly in number and order to the columns in the `myTestSkipField` table.</span></span> <span data-ttu-id="1aa9e-132">서식 파일의 내용을 보려면 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-132">To view the contents of that format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
 <span data-ttu-id="1aa9e-133">다음 `myTestSkipField.xml` 서식 파일은 `myTestSkipField-c.dat`의 필드를 `myTestSkipField` 테이블의 열로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-133">The following format file, `myTestSkipField.xml`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="1aa9e-134">서식 파일은 문자 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-134">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="1aa9e-135">`myTestSkipField.xml` 서식 파일에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-135">The `myTestSkipField.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a><span data-ttu-id="1aa9e-136">예</span><span class="sxs-lookup"><span data-stu-id="1aa9e-136">Examples</span></span>  
 <span data-ttu-id="1aa9e-137">다음 예에서는 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 서식 파일을 사용하는 `myTestSkipField.Xml` 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-137">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.Xml` format file.</span></span> <span data-ttu-id="1aa9e-138">또한 `myTestSkipField-c.dat` 데이터 파일을 `myTestSkipField` 테이블로 대량 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-138">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="1aa9e-139">예제 테이블 및 데이터 파일을 만들려면 이 항목의 앞부분에 나오는 "예제 데이터 파일 및 테이블"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-139">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="1aa9e-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-140">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1aa9e-141">XML 스키마의 구문 및 추가 XML 서식 파일 예제에 대한 내용은 [XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa9e-141">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa9e-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1aa9e-142">See Also</span></span>  
 <span data-ttu-id="1aa9e-143">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1aa9e-143">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="1aa9e-144">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1aa9e-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="1aa9e-145">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1aa9e-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="1aa9e-146">[서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1aa9e-146">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="1aa9e-147">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1aa9e-147">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
