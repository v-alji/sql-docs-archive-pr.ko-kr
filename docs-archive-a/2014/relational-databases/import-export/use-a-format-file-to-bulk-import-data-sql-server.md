---
title: 서식 파일을 사용하여 데이터 대량 가져오기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6d9779209b3ffb317658243c168d74740f6731b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661664"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a><span data-ttu-id="8a00a-102">서식 파일을 사용하여 데이터 대량 가져오기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8a00a-102">Use a Format File to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="8a00a-103">이 항목에서는 대량 가져오기 작업에서 서식 파일을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-103">This topic illustrates the use of a format file in bulk-import operations.</span></span> <span data-ttu-id="8a00a-104">서식 파일은 데이터 파일의 필드를 테이블 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-104">The format file maps the fields of the data file to the columns of the table.</span></span>  <span data-ttu-id="8a00a-105">비 XML 서식 파일 또는 XML 서식 파일을 사용 하 여 **bcp** 명령을 사용 하거나 BULK INSERT 하거나 INSERT ...를 사용 하 여 데이터를 대량으로 가져올 수 있습니다. SELECT \* FROM OPENROWSET (BULK ...) [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령.</span><span class="sxs-lookup"><span data-stu-id="8a00a-105">You can use a non-XML or XML format file to bulk import data when using a **bcp** command or a BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a00a-106">유니코드 문자 데이터 파일에 서식 파일을 사용하려면 모든 입력 필드가 유니코드 텍스트 문자열(고정 크기 또는 문자 종료 유니코드 문자열)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-106">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a00a-107">서식 파일에 익숙하지 않은 경우 [비 Xml 서식 파일 &#40;SQL Server&#41;](xml-format-files-sql-server.md) 및 [xml 서식 파일 &#40;SQL Server&#41;](xml-format-files-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8a00a-107">If you are unfamiliar with format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) and [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="format-file-options-for-bulk-import-commands"></a><span data-ttu-id="8a00a-108">대량 가져오기 명령의 서식 파일 옵션</span><span class="sxs-lookup"><span data-stu-id="8a00a-108">Format File Options for Bulk-Import Commands</span></span>  
 <span data-ttu-id="8a00a-109">다음 표에서는 대량 가져오기 명령 각각에 대한 서식 파일 옵션을 요약하여 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-109">The following table summarizes the format-file option of for each of the bulk-import commands.</span></span>  
  
|<span data-ttu-id="8a00a-110">대량 로드 명령</span><span class="sxs-lookup"><span data-stu-id="8a00a-110">Bulk-load Command</span></span>|<span data-ttu-id="8a00a-111">서식 파일 옵션 사용</span><span class="sxs-lookup"><span data-stu-id="8a00a-111">Using the Format-File Option</span></span>|  
|------------------------|-----------------------------------|  
|<span data-ttu-id="8a00a-112">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="8a00a-112">BULK INSERT</span></span>|<span data-ttu-id="8a00a-113">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="8a00a-113">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="8a00a-114">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="8a00a-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="8a00a-115">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="8a00a-115">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="8a00a-116">**bcp** ... **에서**</span><span class="sxs-lookup"><span data-stu-id="8a00a-116">**bcp** ... **in**</span></span>|<span data-ttu-id="8a00a-117">**-f** *format_file*</span><span class="sxs-lookup"><span data-stu-id="8a00a-117">**-f** *format_file*</span></span>|  
  
 <span data-ttu-id="8a00a-118">자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 또는 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a00a-118">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a00a-119">SQLXML 데이터를 대량으로 내보내거나 가져오려면 서식 파일에서 다음 데이터 형식 중 하나를 사용합니다. SQLCHAR 또는 SQLVARYCHAR(데이터 정렬에 의해 포함된 코드 페이지나 클라이언트 코드 페이지로 데이터가 전송됨), SQLNCHAR 또는 SQLNVARCHAR(데이터가 유니코드로 전송됨), SQLBINARY 또는 SQLVARYBIN(데이터가 변환되지 않고 전송됨) 데이터 형식 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-119">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8a00a-120">예</span><span class="sxs-lookup"><span data-stu-id="8a00a-120">Examples</span></span>  
 <span data-ttu-id="8a00a-121">이 섹션의 예에서는 **bcp** 명령과 BULK INSERT를 사용 하 여 데이터를 대량으로 가져오기 위해 서식 파일을 사용 하는 방법을 보여 줍니다. SELECT \* FROM OPENROWSET (BULK ...) 문</span><span class="sxs-lookup"><span data-stu-id="8a00a-121">The examples in this section illustrate how to use format files to bulk-import data by using the **bcp** command and the BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) statements.</span></span> <span data-ttu-id="8a00a-122">대량 가져오기 예를 실행하려면 먼저 예제 테이블, 데이터 파일 및 서식 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-122">Before you can run one of the bulk-import examples, you need to create a sample table, data file, and a format file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="8a00a-123">예제 테이블</span><span class="sxs-lookup"><span data-stu-id="8a00a-123">Sample Table</span></span>  
 <span data-ttu-id="8a00a-124">이 예에서는 **dbo** 스키마의 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 **myTestFormatFiles** 라는 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-124">The examples require that a table named **myTestFormatFiles** table be created in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="8a00a-125">이 테이블을 만들려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-125">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="8a00a-126">예제 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="8a00a-126">Sample Data File</span></span>  
 <span data-ttu-id="8a00a-127">예에서는 다음 레코드가 들어 있는 `myTestFormatFiles-c.Dat`예제 데이터 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-127">The examples use a sample data file, `myTestFormatFiles-c.Dat`, which contains the following records.</span></span> <span data-ttu-id="8a00a-128">데이터 파일을 만들려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-128">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a><span data-ttu-id="8a00a-129">예제 서식 파일</span><span class="sxs-lookup"><span data-stu-id="8a00a-129">Sample Format Files</span></span>  
 <span data-ttu-id="8a00a-130">이 섹션의 일부 예에서는 XML 서식 파일 `myTestFormatFiles-f-x-c.Xml`을 사용하고 다른 예에서는 비 XML 서식 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-130">Some of the examples in this section use an XML format file, `myTestFormatFiles-f-x-c.Xml`, and other examples use a non-XML format file.</span></span> <span data-ttu-id="8a00a-131">두 서식 파일은 모두 문자 데이터 형식과 비기본 필드 종결자(,)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-131">Both format files use character data formats and a non-default field terminator (,).</span></span>  
  
#### <a name="the-sample-non-xml-format-file"></a><span data-ttu-id="8a00a-132">예제 비 XML 서식 파일</span><span class="sxs-lookup"><span data-stu-id="8a00a-132">The Sample Non-XML Format File</span></span>  
 <span data-ttu-id="8a00a-133">다음 예에서는 **bcp** 를 사용하여 `myTestFormatFiles` 테이블에서 XML 서식 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-133">The following example uses **bcp** to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="8a00a-134">`myTestFormatFiles.Fmt` 파일은 다음 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-134">The `myTestFormatFiles.Fmt` file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="8a00a-135">**bcp** 에 **format** 옵션을 사용하여 이러한 서식 파일을 만들려면 Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-135">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 <span data-ttu-id="8a00a-136">서식 파일을 만드는 방법은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a00a-136">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
#### <a name="the-sample-xml-format-file"></a><span data-ttu-id="8a00a-137">예제 XML 서식 파일</span><span class="sxs-lookup"><span data-stu-id="8a00a-137">The Sample XML Format File</span></span>  
 <span data-ttu-id="8a00a-138">다음 예에서는 **bcp** 를 사용하여 `myTestFormatFiles` 테이블에서 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-138">The following example uses **bcp** to create to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="8a00a-139">`myTestFormatFiles.Xml` 파일은 다음 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-139">The `myTestFormatFiles.Xml` file contains the following information:</span></span>  
  
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
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="8a00a-140">**bcp** 에 **format** 옵션을 사용하여 이러한 서식 파일을 만들려면 Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-140">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a><span data-ttu-id="8a00a-141">bcp 사용</span><span class="sxs-lookup"><span data-stu-id="8a00a-141">Using bcp</span></span>  
 <span data-ttu-id="8a00a-142">다음 예에서는 **bcp** 을 사용하여 `myTestFormatFiles-c.Dat` 데이터 파일에서 예제 데이터베이스의 `HumanResources.myTestFormatFiles` 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-142">The following example uses **bcp** to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the  sample database.</span></span> <span data-ttu-id="8a00a-143">이 예에서는 XML 서식 파일인 `MyTestFormatFiles.Xml`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-143">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="8a00a-144">또한 데이터 파일을 가져오기 전에 기존 테이블 행을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-144">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="8a00a-145">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-145">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8a00a-146">이 명령에 대한 자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a00a-146">For more information about this command, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
### <a name="using-bulk-insert"></a><span data-ttu-id="8a00a-147">BULK INSERT 사용</span><span class="sxs-lookup"><span data-stu-id="8a00a-147">Using BULK INSERT</span></span>  
 <span data-ttu-id="8a00a-148">다음 예에서는 BULK INSERT를 사용하여 `myTestFormatFiles-c.Dat` 데이터 파일에서 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 예제 데이터베이스의 `HumanResources.myTestFormatFiles` 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-148">The following example uses BULK INSERT to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="8a00a-149">이 예에서는 비 XML 서식 파일인 `MyTestFormatFiles.Fmt`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-149">This example uses a non-XML format file, `MyTestFormatFiles.Fmt`.</span></span> <span data-ttu-id="8a00a-150">또한 데이터 파일을 가져오기 전에 기존 테이블 행을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-150">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="8a00a-151">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-151">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8a00a-152">이 문에 대한 자세한 내용은 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a00a-152">For more information about this statement, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a><span data-ttu-id="8a00a-153">OPENROWSET 대량 행 집합 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="8a00a-153">Using the OPENROWSET Bulk Rowset Provider</span></span>  
 <span data-ttu-id="8a00a-154">다음 예에서는 `INSERT ... SELECT * FROM OPENROWSET(BULK...)`을 사용하여 `myTestFormatFiles-c.Dat` 데이터 파일에서 `HumanResources.myTestFormatFiles` 예제 데이터베이스의 `AdventureWorks` 테이블로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-154">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the `AdventureWorks` sample database.</span></span> <span data-ttu-id="8a00a-155">이 예에서는 XML 서식 파일인 `MyTestFormatFiles.Xml`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-155">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="8a00a-156">또한 데이터 파일을 가져오기 전에 기존 테이블 행을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-156">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="8a00a-157">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-157">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 <span data-ttu-id="8a00a-158">예제 테이블의 사용을 완료하면 다음 문을 사용하여 해당 테이블을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-158">When you finish using the sample table, you can drop it using the following statement:</span></span>  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8a00a-159">OPENROWSET BULK 절에 대한 자세한 내용은 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 사용해 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a00a-159">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="8a00a-160">추가 예</span><span class="sxs-lookup"><span data-stu-id="8a00a-160">Additional Examples</span></span>  
 [<span data-ttu-id="8a00a-161">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a00a-161">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
 [<span data-ttu-id="8a00a-162">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a00a-162">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [<span data-ttu-id="8a00a-163">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a00a-163">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [<span data-ttu-id="8a00a-164">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a00a-164">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a00a-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a00a-165">See Also</span></span>  
 <span data-ttu-id="8a00a-166">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8a00a-166">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="8a00a-167">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a00a-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="8a00a-168">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a00a-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="8a00a-169">[비 XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8a00a-169">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="8a00a-170">XML 서식 파일&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8a00a-170">XML Format Files &#40;SQL Server&#41;</span></span>](xml-format-files-sql-server.md)  
  
  
