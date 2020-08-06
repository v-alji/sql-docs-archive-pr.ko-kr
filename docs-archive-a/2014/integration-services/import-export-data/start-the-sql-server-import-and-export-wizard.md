---
title: SQL Server 가져오기 및 내보내기 마법사 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 008c541b1f1a295057b0ee7cc384982627b9689a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652913"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="a3ef5-102">SQL Server 가져오기 및 내보내기 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="a3ef5-102">Run the SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="a3ef5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 데이터 원본 간에 데이터를 복사하고 기본 패키지를 구성하는 가장 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides the simplest method of copying data between data sources and of constructing basic packages.</span></span> <span data-ttu-id="a3ef5-104">마법사에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-104">For more information about the wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="a3ef5-105">SQL Server 가져오기 및 내보내기 마법사를 사용 하 여 SQL Server 데이터베이스에서 Microsoft Excel 스프레드시트로 데이터를 내보내는 패키지를 만드는 방법을 보여 주는 비디오는 [Excel로 SQL Server 데이터 내보내기 (SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=131024)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-105">For a video that demonstrates how to use the SQL Server Import and Export Wizard to create a package that exports data from a SQL Server database to a Microsoft Excel spreadsheet, see [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131024).</span></span>  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="a3ef5-106">SQL Server 가져오기 및 내보내기 마법사를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="a3ef5-106">To start the SQL Server Import and Export Wizard</span></span>  
  
-   <span data-ttu-id="a3ef5-107">**시작** 메뉴에서 **모든 프로그램**,**Microsoft SQL Server** 을 차례로 가리킨 다음 **데이터 가져오기 및 내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-107">On the **Start** menu, point to **All Programs**, point to**Microsoft SQL Server** , and then click **Import and Export Data**.</span></span>  
  
     <span data-ttu-id="a3ef5-108">또는</span><span class="sxs-lookup"><span data-stu-id="a3ef5-108">-or-</span></span>  
  
     <span data-ttu-id="a3ef5-109">에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **SSIS 패키지** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **SSISImport 및 내보내기 마법사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **SSIS Packages** folder, and then click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="a3ef5-110">또는</span><span class="sxs-lookup"><span data-stu-id="a3ef5-110">-or-</span></span>  
  
     <span data-ttu-id="a3ef5-111">의 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **프로젝트** 메뉴에서 **SSISImport 및 내보내기 마법사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="a3ef5-112">또는</span><span class="sxs-lookup"><span data-stu-id="a3ef5-112">-or-</span></span>  
  
     <span data-ttu-id="a3ef5-113">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 서버 유형에 연결 하 고 데이터베이스 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 를 확장 한 다음 데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **태스크**를 가리킨 다음 **데이터 가져오기** 또는 **데이터 내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] server type, expand Databases, right-click a database, point to **Tasks**, and then click **Import Data** or **Export data**.</span></span>  
  
     <span data-ttu-id="a3ef5-114">또는</span><span class="sxs-lookup"><span data-stu-id="a3ef5-114">-or-</span></span>  
  
     <span data-ttu-id="a3ef5-115">명령 프롬프트 창에서 C:\Program Files\Microsoft SQL Server\100\DTS\Binn에 있는 DTSWizard.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-115">In a command prompt window, run DTSWizard.exe, located in C:\Program Files\Microsoft SQL Server\100\DTS\Binn.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3ef5-116">64비트 컴퓨터의 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 64비트 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사(DTSWizard.exe)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-116">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="a3ef5-117">그러나 Access 또는 Excel 등의 일부 데이터 원본은 32비트 공급자만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-117">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="a3ef5-118">이러한 데이터 원본을 사용하려면 32비트 버전의 마법사를 설치하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-118">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="a3ef5-119">32비트 버전의 마법사를 설치하려면 설치 도중 클라이언트 도구 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-119">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="a3ef5-120">SQL Server 가져오기 및 내보내기 마법사를 사용하여 데이터를 가져오거나 내보내려면</span><span class="sxs-lookup"><span data-stu-id="a3ef5-120">To import or export data by using the SQL Server Import and Export Wizard</span></span>  
  
1.  <span data-ttu-id="a3ef5-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-121">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span>  
  
2.  <span data-ttu-id="a3ef5-122">해당 마법사 페이지에서 데이터 원본 및 데이터 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-122">On the corresponding wizard pages, select a data source and a data destination.</span></span>  
  
     <span data-ttu-id="a3ef5-123">사용 가능한 데이터 원본에는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자, OLE DB 공급자, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 공급자, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 공급자, Microsoft Office Excel, Microsoft Office Access 및 플랫 파일 원본이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-123">The available data sources include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] providers, Microsoft Office Excel, Microsoft Office Access, and the Flat File source.</span></span> <span data-ttu-id="a3ef5-124">원본에 따라 인증 모드, 서버 이름, 데이터베이스 이름 및 파일 형식과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-124">Depending on the source, you set options such as the authentication mode, server name, database name, and file format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3ef5-125">Oracle용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB 공급자는 Oracle BLOB, CLOB, NCLOB, BFILE 및 UROWID 데이터 형식을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-125">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle does not support the Oracle BLOB, CLOB, NCLOB, BFILE, and UROWID data types.</span></span> <span data-ttu-id="a3ef5-126">따라서 OLE DB 원본은 이러한 데이터 형식의 열이 포함된 테이블의 데이터를 추출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-126">Therefore, the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
     <span data-ttu-id="a3ef5-127">사용 가능한 데이터 대상에는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자, OLE DB 공급자, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access 및 플랫 파일 대상이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-127">The available data destinations include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access, and the Flat File destination.</span></span>  
  
3.  <span data-ttu-id="a3ef5-128">선택한 대상 유형에 따라 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-128">Set the options for the type of destination that you selected.</span></span>  
  
     <span data-ttu-id="a3ef5-129">대상이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스인 경우 다음을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-129">If the destination is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database you can specify the following:</span></span>  
  
    -   <span data-ttu-id="a3ef5-130">새 데이터베이스를 만들고 데이터베이스 속성을 설정할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-130">Indicate whether to create a new database and set the database properties.</span></span> <span data-ttu-id="a3ef5-131">다음 속성은 구성할 수 없으며 마법사에서 지정된 기본값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-131">The following properties cannot be configured and the wizard uses the specified default values:</span></span>  
  
        |<span data-ttu-id="a3ef5-132">속성</span><span class="sxs-lookup"><span data-stu-id="a3ef5-132">Property</span></span>|<span data-ttu-id="a3ef5-133">값</span><span class="sxs-lookup"><span data-stu-id="a3ef5-133">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="a3ef5-134">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="a3ef5-134">Collation</span></span>|<span data-ttu-id="a3ef5-135">Latin1_General_CS_AS_KS_WS</span><span class="sxs-lookup"><span data-stu-id="a3ef5-135">Latin1_General_CS_AS_KS_WS</span></span>|  
        |<span data-ttu-id="a3ef5-136">복구 모델</span><span class="sxs-lookup"><span data-stu-id="a3ef5-136">Recovery model</span></span>|<span data-ttu-id="a3ef5-137">전체</span><span class="sxs-lookup"><span data-stu-id="a3ef5-137">Full</span></span>|  
        |<span data-ttu-id="a3ef5-138">전체 텍스트 인덱싱 사용</span><span class="sxs-lookup"><span data-stu-id="a3ef5-138">Use full-text indexing</span></span>|<span data-ttu-id="a3ef5-139">True</span><span class="sxs-lookup"><span data-stu-id="a3ef5-139">True</span></span>|  
  
    -   <span data-ttu-id="a3ef5-140">테이블 또는 뷰에서 데이터를 복사할지, 아니면 쿼리 결과를 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-140">Select whether to copy data from tables or views, or to copy query results.</span></span>  
  
         <span data-ttu-id="a3ef5-141">원본 데이터를 쿼리하고 결과를 복사하려는 경우 Transact-SQL 쿼리를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-141">If you want to query the source data and copy the results, you can construct a Transact-SQL query.</span></span> <span data-ttu-id="a3ef5-142">Transact-SQL 쿼리를 수동으로 입력하거나 파일에 저장된 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-142">You can enter the Transact-SQL query manually or use a query saved to a file.</span></span> <span data-ttu-id="a3ef5-143">마법사에는 파일을 찾기 위한 찾아보기 기능이 있으며, 파일을 선택하면 마법사가 자동으로 파일을 열고 파일 내용을 마법사 페이지에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-143">The wizard includes a browse feature for locating the file, and the wizard automatically opens the file and pastes its content into the wizard page when you select the file.</span></span>  
  
         <span data-ttu-id="a3ef5-144">원본이 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 공급자인 경우 쿼리 결과를 복사하는 옵션을 사용하여 DBCommand 문자열을 쿼리로 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-144">If the source is an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider you can also use the option to copy query results, providing the DBCommand string as the query.</span></span>  
  
         <span data-ttu-id="a3ef5-145">원본 데이터가 뷰이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기/내보내기 마법사가 자동으로 뷰를 대상의 테이블로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-145">If the source data is a view, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically converts the view to a table in the destination.</span></span>  
  
    -   <span data-ttu-id="a3ef5-146">대상 테이블을 삭제한 다음 다시 만들지 여부와 ID 삽입을 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-146">Indicate whether the destination table is dropped and then re-created, and whether to enable identity inserts.</span></span>  
  
    -   <span data-ttu-id="a3ef5-147">기존 대상 테이블에서 행을 삭제하거나 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-147">Indicate whether to delete rows or append rows in an existing destination table.</span></span> <span data-ttu-id="a3ef5-148">테이블이 없으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사가 테이블을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-148">If the table does not exist, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically creates it.</span></span>  
  
     <span data-ttu-id="a3ef5-149">대상이 플랫 파일 대상인 경우에는 다음을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-149">If the destination is a Flat File destination you can specify the following:</span></span>  
  
    -   <span data-ttu-id="a3ef5-150">대상 파일의 행 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-150">Specify the row delimiter in the destination file.</span></span>  
  
    -   <span data-ttu-id="a3ef5-151">대상 파일의 열 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-151">Specify the column delimiter in the destination file.</span></span>  
  
4.  <span data-ttu-id="a3ef5-152">필요에 따라 테이블 한 개를 선택하고 원본 열과 대상 열 사이의 매핑을 변경하거나 대상 열의 메타데이터를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-152">(Optional) Select one table and change the mappings between source and destination columns, or change the metadata of destination columns:</span></span>  
  
    -   <span data-ttu-id="a3ef5-153">원본 열을 다른 대상 열로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-153">Map source columns to different destination columns.</span></span>  
  
    -   <span data-ttu-id="a3ef5-154">대상 열의 데이터 형식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-154">Change the data type in the destination column.</span></span>  
  
    -   <span data-ttu-id="a3ef5-155">문자 데이터 형식이 포함된 열의 길이를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-155">Set the length of columns with character data types.</span></span>  
  
    -   <span data-ttu-id="a3ef5-156">숫자 데이터 형식이 포함된 열의 전체 자릿수와 소수 자릿수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-156">Set the precision and scale of columns with numeric data types.</span></span>  
  
    -   <span data-ttu-id="a3ef5-157">열에 대한 Null 값 허용 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-157">Specify whether the column can contain null values.</span></span>  
  
5.  <span data-ttu-id="a3ef5-158">필요에 따라 여러 테이블을 선택하고 메타데이터 및 옵션을 업데이트하여 해당 테이블에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-158">(Optional) Select multiple tables, and update the metadata and options to apply to those tables:</span></span>  
  
    -   <span data-ttu-id="a3ef5-159">기존 대상 스키마를 선택하거나 테이블을 할당할 새 스키마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-159">Select an existing destination schema or provide a new schema to which to assign tables.</span></span>  
  
    -   <span data-ttu-id="a3ef5-160">대상 테이블에 ID를 삽입할 수 있도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-160">Specify whether to enable identity inserts in destination tables.</span></span>  
  
    -   <span data-ttu-id="a3ef5-161">대상 테이블을 삭제하고 다시 만들지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-161">Specify whether to drop and re-create destination tables.</span></span>  
  
    -   <span data-ttu-id="a3ef5-162">기존 대상 테이블을 자를지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-162">Specify whether to truncate existing destination tables.</span></span>  
  
6.  <span data-ttu-id="a3ef5-163">패키지를 저장하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-163">Save and run a package.</span></span>  
  
     <span data-ttu-id="a3ef5-164">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 명령 프롬프트에서 마법사를 시작한 경우 패키지를 즉시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-164">If the wizard is started from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the command prompt, the package can run immediately.</span></span> <span data-ttu-id="a3ef5-165">필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** 데이터베이스 또는 파일 시스템에 패키지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-165">You can optionally save the package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database or to the file system.</span></span> <span data-ttu-id="a3ef5-166">**Msdb** 데이터베이스에 대 한 자세한 내용은 [SSIS 서비스&#41;패키지 관리 &#40;](../service/package-management-ssis-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-166">For more information about the **msdb** database, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
     <span data-ttu-id="a3ef5-167">패키지를 저장할 때 패키지 보호 수준을 설정할 수 있으며 설정한 보호 수준에서 암호가 사용되는 경우 암호를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-167">When you save the package you can set the package protection level, and if the protection level uses a password, provide the password.</span></span> <span data-ttu-id="a3ef5-168">패키지 보호 수준에 대 한 자세한 내용은 [패키지의 중요 한 데이터에 대 한 Access Control](../security/access-control-for-sensitive-data-in-packages.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-168">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="a3ef5-169">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 프로젝트에서 마법사를 시작한 경우 마법사에서 패키지를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-169">If the wizard is started from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you cannot run the package from the wizard.</span></span> <span data-ttu-id="a3ef5-170">대신 마법사를 시작한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에 패키지가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-170">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="a3ef5-171">그런 다음 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-171">You can then run the package in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3ef5-172">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서는 마법사가 만든 패키지를 저장하는 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ef5-172">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ef5-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3ef5-173">See Also</span></span>  
 <span data-ttu-id="a3ef5-174">[SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef5-174">[SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span></span>  
 [<span data-ttu-id="a3ef5-175">SQL Server Data Tools에서 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="a3ef5-175">Create Packages in SQL Server Data Tools</span></span>](../create-packages-in-sql-server-data-tools.md)  
  
  
