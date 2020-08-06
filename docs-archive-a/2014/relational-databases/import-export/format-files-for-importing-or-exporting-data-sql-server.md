---
title: 데이터를 가져오거나 내보내기 위한 서식 파일(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], format files
- bulk importing [SQL Server], format files
- format files [SQL Server]
ms.assetid: b7b97d68-4336-4091-aee4-1941fab568e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1143690f0322fef2612fde51eebcb7427ee237ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653381"
---
# <a name="format-files-for-importing-or-exporting-data-sql-server"></a><span data-ttu-id="59a9a-102">데이터를 가져오거나 내보내기 위한 서식 파일(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="59a9a-102">Format Files for Importing or Exporting Data (SQL Server)</span></span>
  <span data-ttu-id="59a9a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 데이터를 대량으로 가져오거나 테이블의 데이터를 대량으로 내보내는 경우 *서식 파일* 을 사용하여 데이터를 대량으로 내보내거나 가져오는 데 필요한 모든 서식 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-103">When you bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or bulk export data from a table, you can use a *format file* to store all the format information that is required to bulk export or bulk import data.</span></span> <span data-ttu-id="59a9a-104">여기에는 해당 테이블을 기준으로 하는 데이터 파일의 각 필드에 대한 서식 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-104">This includes format information for each field in a data file relative to that table.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="59a9a-105">에서는 다음과 같은 두 가지 유형의 형식 파일을 지원합니다. XML 서식 및 비 XML 서식 파일.</span><span class="sxs-lookup"><span data-stu-id="59a9a-105">supports two types of format files: XML formats and non-XML format files.</span></span> <span data-ttu-id="59a9a-106">비 XML 서식 파일과 XML 서식 파일은 모두 데이터 파일의 각 필드에 대한 설명을 포함하며, XML 서식 파일의 경우에는 해당하는 테이블 열에 대한 설명도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-106">Both non-XML format files and XML format files contain descriptions of every field in a data file, and XML format files also contain descriptions of the corresponding table columns.</span></span> <span data-ttu-id="59a9a-107">일반적으로 XML 서식 파일과 비 XML 서식 파일은 서로 전환이 가능하지만</span><span class="sxs-lookup"><span data-stu-id="59a9a-107">Generally, XML and non-XML format files are interchangeable.</span></span> <span data-ttu-id="59a9a-108">새 서식 파일에는 비 XML 서식 파일에 비해 여러 가지 장점이 있는 XML 구문을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-108">However, we recommend that you use the XML syntax for new format files because they provide several advantages over non-XML format files.</span></span> <span data-ttu-id="59a9a-109">자세한 내용은 [XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)의 두 가지 서식 파일 유형을 대량으로 내보내고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-109">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 
  
##  <a name="benefits-of-format-files"></a><a name="Benefits"></a> <span data-ttu-id="59a9a-110">서식 파일의 이점</span><span class="sxs-lookup"><span data-stu-id="59a9a-110">Benefits of Format Files</span></span>  
  
-   <span data-ttu-id="59a9a-111">다른 데이터 형식과 맞추기 위한 편집 작업이 거의 필요 없는 데이터 파일을 작성하거나 다른 소프트웨어의 데이터 파일을 읽는 작업을 유연하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-111">Provides a flexible system for writing data files that requires little or no editing to comply with other data formats or to read data files from other software.</span></span>  
  
-   <span data-ttu-id="59a9a-112">불필요한 데이터를 추가 또는 삭제하거나 데이터 파일에 있는 기존 데이터를 다시 정렬하지 않고도 대량의 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-112">Enables you to bulk import data without having to add or delete unnecessary data or to reorder existing data in the data file.</span></span> <span data-ttu-id="59a9a-113">서식 파일은 데이터 파일의 필드와 테이블의 열이 일치하지 않을 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-113">Format files are particularly useful when a mismatch exists between fields in the data file and columns in the table.</span></span>  
  
##  <a name="examples-of-format-files"></a><a name="ExamplesOfFFs"></a> <span data-ttu-id="59a9a-114">서식 파일의 예</span><span class="sxs-lookup"><span data-stu-id="59a9a-114">Examples of Format Files</span></span>  
 <span data-ttu-id="59a9a-115">다음 예에서는 비 XML 서식 파일 및 XML 서식 파일의 레이아웃을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-115">The following examples show the layout of a non-XML format file and of an XML format file.</span></span> <span data-ttu-id="59a9a-116">이러한 서식 파일은 `HumanResources.myTeam` 예제 데이터베이스의 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 테이블에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-116">These format files correspond to the `HumanResources.myTeam` table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="59a9a-117">이 테이블에는 네 개의 열, 즉 `EmployeeID`, `Name`, `Title`및 `ModifiedDate`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-117">This table contains four columns: `EmployeeID`, `Name`, `Title`, and `ModifiedDate`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59a9a-118">이 테이블을 만드는 방법은 [HumanResources.myTeam 예제 테이블&#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59a9a-118">For information about this table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
### <a name="a-using-a-non-xml-format-file"></a><span data-ttu-id="59a9a-119">A.</span><span class="sxs-lookup"><span data-stu-id="59a9a-119">A.</span></span> <span data-ttu-id="59a9a-120">비 XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="59a9a-120">Using a non-XML format file</span></span>  
 <span data-ttu-id="59a9a-121">다음 비 XML 서식 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 `HumanResources.myTeam` 네이티브 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-121">The following non-XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="59a9a-122">이 서식 파일은 다음 `bcp` 명령을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-122">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Fmt -n -T   
The contents of this format file are as follows: 9.0  
4  
1       SQLSMALLINT   0       2       ""   1     EmployeeID               ""  
2       SQLNCHAR      2       100     ""   2     Name                     SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     Title                    SQL_Latin1_General_CP1_CI_AS  
4       SQLNCHAR      2       100     ""   4     Background               SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="59a9a-123">자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](non-xml-format-files-sql-server.md)에서 원래 지원했던 서식 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-123">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md).</span></span>  
  
 
  
### <a name="b-using-an-xml-format-file"></a><span data-ttu-id="59a9a-124">B.</span><span class="sxs-lookup"><span data-stu-id="59a9a-124">B.</span></span> <span data-ttu-id="59a9a-125">XML 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="59a9a-125">Using an XML format file</span></span>  
 <span data-ttu-id="59a9a-126">다음 XML 서식 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 `HumanResources.myTeam` 네이티브 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-126">The following XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="59a9a-127">이 서식 파일은 다음 `bcp` 명령을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-127">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Xml -x -n -T   
```  
  
 <span data-ttu-id="59a9a-128">서식 파일은 다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-128">The format file contains:</span></span>  
  
```  
 <?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="EmployeeID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Title" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Background" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="59a9a-129">자세한 내용은 [XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md)의 두 가지 서식 파일 유형을 대량으로 내보내고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-129">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="when-is-a-format-file-required"></a><a name="WhenFFrequired"></a> <span data-ttu-id="59a9a-130">서식 파일이 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-130">When Is a Format File Required?</span></span>  
 <span data-ttu-id="59a9a-131">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문을 사용하는 경우에는 항상 서식 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-131">An INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement always requires a format file.</span></span>  
  
-   <span data-ttu-id="59a9a-132">**bcp** 또는 BULK INSERT의 경우 단순한 상황에서는 필요에 따라 서식 파일을 사용할 수 있으며 필수적인 경우는 많지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-132">For **bcp** or BULK INSERT, in simple situations, using a format file is optional and rarely necessary.</span></span> <span data-ttu-id="59a9a-133">그러나 복잡한 대량 가져오기 상황에서는 서식 파일이 필요한 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-133">However, for complex bulk-import situations, a format file is frequently required.</span></span>  
  
 <span data-ttu-id="59a9a-134">다음과 같은 경우에 서식 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-134">Format files are required if:</span></span>  
  
-   <span data-ttu-id="59a9a-135">동일한 데이터 파일이 스키마가 다른 여러 테이블의 원본으로 사용되는 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-135">The same data file is used as a source for multiple tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="59a9a-136">대상 테이블의 열과 데이터 파일의 필드 개수가 다른 경우. 예를 들면 다음과 같은 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-136">The data file has a different number of fields that the target table has columns; for example:</span></span>  
  
    -   <span data-ttu-id="59a9a-137">대상 테이블에 기본값이 정의되었거나 NULL이 허용된 열이 최소 하나 이상 포함되어 있는 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-137">The target table contains at least one column for which either a default value is defined or NULL is allowed.</span></span>  
  
    -   <span data-ttu-id="59a9a-138">사용자에게 테이블에 있는 하나 이상의 열에 대한 SELECT/INSERT 권한이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-138">The users do not have SELECT/INSERT permissions on one or more columns in the table.</span></span>  
  
    -   <span data-ttu-id="59a9a-139">하나의 데이터 파일이 스키마가 다른 둘 이상의 테이블에 사용되는 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-139">A single data file is used with two or more tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="59a9a-140">데이터 파일과 테이블의 열 순서가 다른 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-140">The column order is different for the data file and table.</span></span>  
  
-   <span data-ttu-id="59a9a-141">데이터 파일의 열 간에 종결 문자나 접두사 길이가 다른 경우</span><span class="sxs-lookup"><span data-stu-id="59a9a-141">The terminating characters or prefix lengths differ among the columns of the data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59a9a-142">서식 파일이 없는 경우 **bcp** 명령이 지정한 데이터 형식 스위치( **-n**, **-c**, **-w**또는 **-N**) 또는 BULK INSERT 연산에 지정된 DATAFILETYPE 옵션의 데이터 형식을 데이터 파일의 필드를 해석하는 기본 방법으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59a9a-142">In the absence of a format file, if a **bcp** command specifies a data-format switch (**-n**, **-c**, **-w**, or **-N**) or a BULK INSERT operation specifies the DATAFILETYPE option, the specified data format is used as the default method of interpreting the fields of the data file.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="59a9a-143">관련 작업</span><span class="sxs-lookup"><span data-stu-id="59a9a-143">Related Tasks</span></span>  
  
-   [<span data-ttu-id="59a9a-144">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-144">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="59a9a-145">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-145">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="59a9a-146">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-146">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="59a9a-147">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-147">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="59a9a-148">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-148">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="59a9a-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59a9a-149">See Also</span></span>  
 <span data-ttu-id="59a9a-150">[비 XML 서식 파일&#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="59a9a-150">[Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span></span>  
 <span data-ttu-id="59a9a-151">[XML 서식 파일&#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="59a9a-151">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="59a9a-152">대량 가져오기 또는 대량 내보내기를 위한 데이터 형식&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59a9a-152">Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;</span></span>](data-formats-for-bulk-import-or-bulk-export-sql-server.md)  
  
  
