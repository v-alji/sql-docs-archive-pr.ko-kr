---
title: 데이터 대량 가져오기 및 내보내기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b4e7611270135735cf3f7aada808a0a27ba927c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649995"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a><span data-ttu-id="3bf90-102">데이터 대량 가져오기 및 내보내기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3bf90-102">Bulk Import and Export of Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3bf90-103">에서는*테이블에서 대량으로 데이터(* 대량 데이터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )를 내보내고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블이나 분할되지 않은 뷰로 대량의 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-103">supports exporting data in bulk (*bulk data*) from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="3bf90-104">대량 가져오기 및 대량 내보내기는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 다른 데이터 원본 간에 데이터를 효과적으로 전송하는 데 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-104">Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and heterogeneous data sources.</span></span> <span data-ttu-id="3bf90-105">*대량 내보내기* 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 데이터를 데이터 파일로 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-105">*Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file.</span></span> <span data-ttu-id="3bf90-106">*대량 가져오기* 는 데이터 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 데이터를 로드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-106">*Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="3bf90-107">예를 들어 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 애플리케이션의 데이터를 데이터 파일로 내보낸 다음 해당 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 대량으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-107">For example, you can export data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="3bf90-108">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="3bf90-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="3bf90-109">대량 가져오기 및 내보내기 작업 소개</span><span class="sxs-lookup"><span data-stu-id="3bf90-109">Introduction to Bulk Import and Bulk Export Operations</span></span>](#Intro)  
  
-   [<span data-ttu-id="3bf90-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3bf90-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bulk-import-and-bulk-export-overview"></a><a name="Intro"></a><span data-ttu-id="3bf90-111">대량 가져오기 및 대량 내보내기 개요</span><span class="sxs-lookup"><span data-stu-id="3bf90-111">Bulk Import and Bulk Export Overview</span></span>  
 <span data-ttu-id="3bf90-112">이 섹션에서는 데이터 대량 가져오기 및 내보내기에 사용할 수 있는 여러 방법을 나열하고 간단하게 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-112">This section lists and briefly compares the various methods that are available for bulk importing and exporting data.</span></span> <span data-ttu-id="3bf90-113">또한 서식 파일을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-113">The section also introduces format files.</span></span>  
  
 <span data-ttu-id="3bf90-114">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="3bf90-114">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="3bf90-115">데이터 대량 가져오기 및 내보내기 방법</span><span class="sxs-lookup"><span data-stu-id="3bf90-115">Methods for Bulk Importing and Exporting Data</span></span>](#MethodsForBuliIE)  
  
-   [<span data-ttu-id="3bf90-116">서식 파일</span><span class="sxs-lookup"><span data-stu-id="3bf90-116">Format Files</span></span>](#FFs)  
  
###  <a name="methods-for-bulk-importing-and-exporting-data"></a><a name="MethodsForBuliIE"></a><span data-ttu-id="3bf90-117">데이터 대량 가져오기 및 내보내기 방법</span><span class="sxs-lookup"><span data-stu-id="3bf90-117">Methods for Bulk Importing and Exporting Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3bf90-118">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 대량의 데이터를 내보내고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블이나 분할되지 않은 뷰로 대량의 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-118">supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="3bf90-119">다음과 같은 기본 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-119">The following basic methods are available.</span></span>  
  
|<span data-ttu-id="3bf90-120">방법</span><span class="sxs-lookup"><span data-stu-id="3bf90-120">Method</span></span>|<span data-ttu-id="3bf90-121">Description</span><span class="sxs-lookup"><span data-stu-id="3bf90-121">Description</span></span>|<span data-ttu-id="3bf90-122">데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="3bf90-122">Imports data</span></span>|<span data-ttu-id="3bf90-123">데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="3bf90-123">Exports data</span></span>|  
|------------|-----------------|------------------|------------------|  
|[<span data-ttu-id="3bf90-124">bcp 유틸리티</span><span class="sxs-lookup"><span data-stu-id="3bf90-124">bcp utility</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|<span data-ttu-id="3bf90-125">데이터를 대량으로 내보내고 가져오며 서식 파일을 생성하는 명령줄 유틸리티(Bcp.exe)입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-125">A command-line utility (Bcp.exe) that bulk exports and bulk imports data and generates format files.</span></span>|<span data-ttu-id="3bf90-126">예</span><span class="sxs-lookup"><span data-stu-id="3bf90-126">Yes</span></span>|<span data-ttu-id="3bf90-127">예</span><span class="sxs-lookup"><span data-stu-id="3bf90-127">Yes</span></span>|  
|[<span data-ttu-id="3bf90-128">BULK INSERT 문</span><span class="sxs-lookup"><span data-stu-id="3bf90-128">BULK INSERT statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="3bf90-129">데이터 파일에서 데이터베이스 테이블이나 분할되지 않은 뷰로 직접 데이터를 가져오는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-129">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.</span></span>|<span data-ttu-id="3bf90-130">예</span><span class="sxs-lookup"><span data-stu-id="3bf90-130">Yes</span></span>|<span data-ttu-id="3bf90-131">예</span><span class="sxs-lookup"><span data-stu-id="3bf90-131">No</span></span>|  
|[<span data-ttu-id="3bf90-132">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문</span><span class="sxs-lookup"><span data-stu-id="3bf90-132">INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="3bf90-133">INSERT 문의 데이터를 선택하는 OPENROWSET(BULK…) 함수를 지정하여 대량의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 가져오기 위해 OPENROWSET 대량 행 집합 공급 기업을 사용하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-133">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table by specifying the OPENROWSET(BULK...) function to select data in an INSERT statement.</span></span>|<span data-ttu-id="3bf90-134">예</span><span class="sxs-lookup"><span data-stu-id="3bf90-134">Yes</span></span>|<span data-ttu-id="3bf90-135">아니요</span><span class="sxs-lookup"><span data-stu-id="3bf90-135">No</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3bf90-136">CSV(쉼표로 구분된 값) 파일은 SQL Server 대량 가져오기 작업에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-136">Comma-separated value (CSV) files are not supported by SQL Server bulk-import operations.</span></span> <span data-ttu-id="3bf90-137">그러나 경우에 따라 데이터를 SQL Server로 대량으로 가져오기 위한 데이터 파일로 CSV(쉼표로 구분된 값) 파일이 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-137">However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server.</span></span> <span data-ttu-id="3bf90-138">CSV 파일의 필드 종결자로는 쉼표 이외에 다른 문자도 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-138">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="3bf90-139">자세한 내용은 [대량 내보내기 또는 가져오기를 위한 데이터 준비&#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bf90-139">For more information, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
###  <a name="format-files"></a><a name="FFs"></a><span data-ttu-id="3bf90-140">서식 파일</span><span class="sxs-lookup"><span data-stu-id="3bf90-140">Format Files</span></span>  
 <span data-ttu-id="3bf90-141">**Bcp** 유틸리티, BULK INSERT 및 INSERT ... SELECT \* FROM OPENROWSET (BULK ...)은 모두 데이터 파일의 각 필드에 대 한 서식 정보를 저장 하는 특수 *서식 파일* 의 사용을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-141">The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) all support the use of a specialized *format file* that stores format information for each field in a data file.</span></span> <span data-ttu-id="3bf90-142">또한 서식 파일에는 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-142">A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="3bf90-143">서식 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스로 데이터를 대량으로 내보내거나 SQL Server 인스턴스에서 데이터를 대량으로 가져올 때 필요한 모든 서식 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-143">The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3bf90-144">서식 파일을 사용하면 가져오기 작업 중 데이터 파일에 있는 데이터의 해석뿐만 아니라 내보내기 작업 중 데이터 파일에 있는 데이터의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-144">Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export.</span></span> <span data-ttu-id="3bf90-145">이와 같이 융통성이 있기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 외부 애플리케이션에 대한 특정 요구 사항에 따라 데이터를 해석하거나 데이터의 서식을 다시 지정하기 위해 특수한 목적의 코드를 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-145">This flexibility eliminates the need to write special-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the external application.</span></span> <span data-ttu-id="3bf90-146">예를 들어 대량으로 내보낸 데이터를 쉼표로 값을 구분해야 하는 애플리케이션으로 로드해야 할 경우 서식 파일을 사용하여 내보낸 데이터에서 쉼표를 필드 종결자로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-146">For example, if you are bulk exporting data to be loaded into an application that requires comma-separated values, you can use a format file to insert commas as field terminators in the exported data.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3bf90-147">에서는 다음과 같은 두 종류의 서식 파일을 지원합니다. XML 서식 파일 및 비 XML 서식 파일.</span><span class="sxs-lookup"><span data-stu-id="3bf90-147">supports two kinds of format files: XML format files and non-XML format files.</span></span>  
  
 <span data-ttu-id="3bf90-148">**Bcp** 유틸리티는 서식 파일을 생성할 수 있는 유일한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-148">The **bcp** utility is the only tool that can generate a format file.</span></span> <span data-ttu-id="3bf90-149">자세한 내용은 [서식 파일 만들기&#40;SQL Server&#41;](create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bf90-149">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="3bf90-150">서식 파일에 대한 자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bf90-150">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bf90-151">대량 내보내기 또는 가져오기 작업 동안 서식 파일이 제공되지 않는 경우 사용자는 명령줄에서 기본 서식 지정을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf90-151">In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3bf90-152">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3bf90-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3bf90-153">bcp 유틸리티를 사용하여 대량 데이터 가져오기 및 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-153">Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-154">BULK INSERT 또는 OPENROWSET&#40;BULK...&#41;를 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-154">Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-155">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-155">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-156">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-156">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-157">대량 내보내기 또는 가져오기를 위한 데이터 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-157">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="3bf90-158">**서식 파일을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="3bf90-158">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="3bf90-159">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-159">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-160">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-160">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-161">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-161">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-162">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-162">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-163">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-163">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="3bf90-164">**대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="3bf90-164">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="3bf90-165">SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="3bf90-165">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-166">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-166">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-167">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-167">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-168">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-168">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3bf90-169">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-169">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="3bf90-170">**bcp를 사용할 때 데이터 형식의 호환 가능성을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="3bf90-170">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="3bf90-171">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-171">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="3bf90-172">bcp를 사용하여 데이터 파일에 접두사 길이 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-172">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="3bf90-173">bcp를 사용하여 파일 스토리지 유형 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-173">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bf90-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3bf90-174">See Also</span></span>  
 <span data-ttu-id="3bf90-175">[대량 가져오기의 최소 로깅을 위한 선행 조건](prerequisites-for-minimal-logging-in-bulk-import.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-175">[Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md) </span></span>  
 <span data-ttu-id="3bf90-176">[데이터를 가져오거나 내보내기 위한 서식 파일 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-176">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 <span data-ttu-id="3bf90-177">[XML 문서 대량 가져오기 및 내보내기 예 &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-177">[Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span></span>  
 <span data-ttu-id="3bf90-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span></span>  
 <span data-ttu-id="3bf90-179">[데이터베이스를 다른 서버로 복사](../databases/copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-179">[Copy Databases to Other Servers](../databases/copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="3bf90-180">[SQLXML 4.0&#41;&#40;XML 데이터 대량 로드를 수행 하는 중](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-180">[Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="3bf90-181">[대량 복사 작업 수행](../native-client/features/performing-bulk-copy-operations.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-181">[Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md) </span></span>  
 <span data-ttu-id="3bf90-182">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="3bf90-183">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3bf90-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="3bf90-184">[데이터를 가져오거나 내보내기 위한 서식 파일 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3bf90-184">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 [<span data-ttu-id="3bf90-185">OPENROWSET&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf90-185">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
