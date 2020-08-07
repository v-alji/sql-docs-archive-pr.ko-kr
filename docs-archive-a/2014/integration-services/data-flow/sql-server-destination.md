---
title: SQL Server 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcd65007e1e6af36386cb2ceba1f7242305b81a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729672"
---
# <a name="sql-server-destination"></a><span data-ttu-id="d3e8c-102">SQL Server 대상</span><span class="sxs-lookup"><span data-stu-id="d3e8c-102">SQL Server Destination</span></span>
  <span data-ttu-id="d3e8c-103">SQL Server 대상은 로컬 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 및 뷰로 데이터를 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-103">The SQL Server destination connects to a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and bulk loads data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and views.</span></span> <span data-ttu-id="d3e8c-104">원격 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 액세스하는 패키지에서는 SQL Server 대상을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-104">You cannot use the SQL Server destination in packages that access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a remote server.</span></span> <span data-ttu-id="d3e8c-105">이러한 패키지에서는 대신 OLE DB 대상을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-105">Instead, the packages should use the OLE DB destination.</span></span> <span data-ttu-id="d3e8c-106">자세한 내용은 [OLE DB Destination](ole-db-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-106">For more information, see [OLE DB Destination](ole-db-destination.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="d3e8c-107">사용 권한</span><span class="sxs-lookup"><span data-stu-id="d3e8c-107">Permissions</span></span>  
 <span data-ttu-id="d3e8c-108">SQL Server 대상이 포함된 패키지를 실행하는 사용자는 "전역 개체 만들기" 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-108">Users who execute packages that include the SQL Server destination require the "Create global objects" permission.</span></span> <span data-ttu-id="d3e8c-109">**관리 도구** 메뉴에서 연 로컬 보안 정책 도구를 사용하여 사용자에게 이 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-109">You can grant this permission to users by using the Local Security Policy tool opened from the **Administrative Tools** menu.</span></span> <span data-ttu-id="d3e8c-110">SQL Server 대상을 사용하는 패키지를 실행할 때 오류 메시지가 표시되면 패키지를 실행 중인 계정에 "전역 개체 만들기" 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-110">If you receive an error message when executing a package that uses the SQL Server destination, make sure that the account running the package has the "Create global objects" permission.</span></span>  
  
## <a name="bulk-inserts"></a><span data-ttu-id="d3e8c-111">대량 삽입</span><span class="sxs-lookup"><span data-stu-id="d3e8c-111">Bulk Inserts</span></span>  
 <span data-ttu-id="d3e8c-112">SQL Server 대상을 사용하여 원격 SQL Server 데이터베이스에 데이터를 대량으로 로드하려고 하면 "OLE DB 레코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-112">If you attempt to use the SQL Server destination to bulk load data into a remote SQL Server database, you may see an error message similar to the following: "An OLE DB record is available.</span></span> <span data-ttu-id="d3e8c-113">원본: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 설명: "SSIS 파일 매핑 개체 'Global\DTSQLIMPORT'을(를) 열 수 없으므로 대량 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-113">Source: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Description: "Could not bulk load because SSIS file mapping object 'Global\DTSQLIMPORT ' could not be opened.</span></span> <span data-ttu-id="d3e8c-114">운영 체제 오류 코드 2(시스템에서 지정한 파일을 찾을 수 없습니다.)입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-114">Operating system error code 2 (The system cannot find the file specified.).</span></span> <span data-ttu-id="d3e8c-115">Windows 보안을 통해 로컬 서버에 액세스하고 있는지 확인하십시오.""와 유사한 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-115">Make sure you are accessing a local server via Windows security.""</span></span>  
  
 <span data-ttu-id="d3e8c-116">SQL Server 대상은 대량 삽입 태스크가 제공하는 것과 동일하게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 고속 데이터 삽입 기능을 제공하지만 SQL Server 대상을 사용하면 데이터가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 로드되기 전에 패키지에서 열 데이터에 변환을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-116">The SQL Server destination offers the same high-speed insertion of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that the Bulk Insert task provides; however, by using the SQL Server destination, a package can apply transformations to column data before the data is loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d3e8c-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 데이터를 로드하려면 OLE DB 대상 대신 SQL Server 대상을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-117">For loading data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should consider using the SQL Server destination instead of the OLE DB destination.</span></span>  
  
### <a name="bulk-insert-options"></a><span data-ttu-id="d3e8c-118">대량 삽입 옵션</span><span class="sxs-lookup"><span data-stu-id="d3e8c-118">Bulk Insert Options</span></span>  
 <span data-ttu-id="d3e8c-119">SQL Server 대상이 빠른 로드 데이터 액세스 모드를 사용할 경우 다음과 같은 빠른 로드 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-119">If the SQL Server destination uses a fast-load data access mode, you can specify the following fast load options:</span></span>  
  
-   <span data-ttu-id="d3e8c-120">가져온 데이터 파일에서 ID 값을 유지하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 할당된 고유 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-120">Retain identity values from the imported data file, or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d3e8c-121">대량 로드 작업 중에 발생한 Null 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-121">Retain null values during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-122">대량 가져오기 작업 중에 대상 테이블 또는 뷰의 제약 조건을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-122">Verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-123">대량 로드 작업이 지속되는 동안 테이블 수준 잠금을 획득합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-123">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-124">대량 로드 작업 중에 대상 테이블에 정의된 삽입 트리거를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-124">Execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-125">대량 삽입 작업 중에 입력에서 로드할 첫 번째 행의 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-125">Specify the number of the first row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-126">대량 삽입 작업 중에 입력에서 로드할 마지막 행의 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-126">Specify the number of the last row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-127">대량 삽입 작업을 취소하기 전에 허용되는 최대 오류 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-127">Specify the maximum number of errors allowed before the bulk load operation is canceled.</span></span> <span data-ttu-id="d3e8c-128">가져올 수 없는 행은 각각 하나의 오류로 카운트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-128">Each row that cannot be imported is counted as one error.</span></span>  
  
-   <span data-ttu-id="d3e8c-129">입력에서 정렬된 데이터가 포함된 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-129">Specify the columns in the input that contain sorted data.</span></span>  
  
 <span data-ttu-id="d3e8c-130">대량 로드 옵션에 대한 자세한 내용은 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-130">For more information about bulk load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
#### <a name="performance-improvements"></a><span data-ttu-id="d3e8c-131">성능 향상</span><span class="sxs-lookup"><span data-stu-id="d3e8c-131">Performance Improvements</span></span>  
 <span data-ttu-id="d3e8c-132">대량 삽입의 성능과 대량 삽입 작업 중의 테이블 액세스를 향상시키려면 기본 옵션을 다음과 같이 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-132">To improve the performance of a bulk insert and the access to table data during the bulk insert operation, you should change the default options as follows:</span></span>  
  
-   <span data-ttu-id="d3e8c-133">대량 가져오기 작업 중에 대상 테이블 또는 뷰의 제약 조건을 검사하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-133">Do not verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-134">대량 로드 작업 중에 대상 테이블에서 정의된 삽입 트리거를 실행하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-134">Do not execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="d3e8c-135">테이블에 잠금을 적용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-135">Do not apply a lock to the table.</span></span> <span data-ttu-id="d3e8c-136">이렇게 하면 대량 삽입 작업 중에 다른 사용자 및 애플리케이션이 테이블을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-136">That way, the table remains available to other users and applications during the bulk insert operation.</span></span>  
  
## <a name="configuration-of-the-sql-server-destination"></a><span data-ttu-id="d3e8c-137">SQL Server 대상 구성</span><span class="sxs-lookup"><span data-stu-id="d3e8c-137">Configuration of the SQL Server Destination</span></span>  
 <span data-ttu-id="d3e8c-138">다음과 같은 방법으로 SQL Server 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-138">You can configure the SQL Server destination in the following ways:</span></span>  
  
-   <span data-ttu-id="d3e8c-139">데이터를 대량 로드할 테이블 또는 뷰를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-139">Specify the table or view into which to bulk load the data.</span></span>  
  
-   <span data-ttu-id="d3e8c-140">제약 조건 검사 여부와 같은 옵션을 지정하여 대량 로드 작업을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-140">Customize the bulk load operation by specifying options such as whether to check constraints.</span></span>  
  
-   <span data-ttu-id="d3e8c-141">한 일괄 처리의 모든 행을 커밋할지 지정하거나 한 일괄 처리로 커밋할 행의 최대 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-141">Specify whether all rows commit in one batch or set the maximum number of rows to commit as a batch.</span></span>  
  
-   <span data-ttu-id="d3e8c-142">대량 로드 작업에 대한 제한 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-142">Specify a time-out for the bulk load operation.</span></span>  
  
 <span data-ttu-id="d3e8c-143">이 대상은 OLE DB 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자가 사용할 OLE DB Provider를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-143">This destination uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="d3e8c-144">자세한 내용은 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-144">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d3e8c-145">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트는 또한 OLE DB 연결 관리자를 만들 수 있는 데이터 원본 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-145">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager.</span></span> <span data-ttu-id="d3e8c-146">그러면 SQL Server 대상에서 데이터 원본과 데이터 원본 뷰를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-146">This makes data sources and data source views available to the SQL Server destination.</span></span>  
  
 <span data-ttu-id="d3e8c-147">SQL Server 대상은 하나의 입력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-147">The SQL Server destination has one input.</span></span> <span data-ttu-id="d3e8c-148">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-148">It does not support an error output.</span></span>  
  
 <span data-ttu-id="d3e8c-149">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-149">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d3e8c-150">**SQL Server 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-150">For more information about the properties that you can set in the **SQL Server Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d3e8c-151">SQL 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e8c-151">SQL Destination Editor &#40;Connection Manager Page&#41;</span></span>](../sql-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="d3e8c-152">SQL 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e8c-152">SQL Destination Editor &#40;Mappings Page&#41;</span></span>](../sql-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="d3e8c-153">SQL 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e8c-153">SQL Destination Editor &#40;Advanced Page&#41;</span></span>](../sql-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="d3e8c-154">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-154">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="d3e8c-155">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-155">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d3e8c-156">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d3e8c-156">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="d3e8c-157">SQL Server 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="d3e8c-157">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
 <span data-ttu-id="d3e8c-158">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-158">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d3e8c-159">SQL Server 대상을 사용하여 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="d3e8c-159">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="d3e8c-160">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d3e8c-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="d3e8c-161">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d3e8c-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d3e8c-162">SQL Server 대상을 사용하여 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="d3e8c-162">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="d3e8c-163">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d3e8c-163">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="d3e8c-164">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d3e8c-164">Related Content</span></span>  
  
-   <span data-ttu-id="d3e8c-165">support.microsoft.com의 기술 문서 - [UAC 사용 시스템에서 "데이터 삽입을 위해 SSIS 대량 삽입을 준비할 수 없습니다." 오류가 발생할 수 있습니다.](https://go.microsoft.com/fwlink/?LinkId=199482)</span><span class="sxs-lookup"><span data-stu-id="d3e8c-165">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=199482), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="d3e8c-166">msdn.microsoft.com의 기술 문서 - [데이터 로드 성능 가이드](https://go.microsoft.com/fwlink/?LinkId=233700)</span><span class="sxs-lookup"><span data-stu-id="d3e8c-166">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="d3e8c-167">simple-talk.com의 기술 문서, [SQL Server Integration Services를 사용하여 데이터 대량 로드](https://go.microsoft.com/fwlink/?LinkId=233701)</span><span class="sxs-lookup"><span data-stu-id="d3e8c-167">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e8c-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3e8c-168">See Also</span></span>  
 [<span data-ttu-id="d3e8c-169">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="d3e8c-169">Data Flow</span></span>](data-flow.md)  
  
  
