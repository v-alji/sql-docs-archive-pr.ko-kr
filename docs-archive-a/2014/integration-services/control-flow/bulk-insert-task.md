---
title: 대량 삽입 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.f1
helpviewer_keywords:
- Bulk Insert task
- copying data [Integration Services]
ms.assetid: c5166156-6b4c-4369-81ed-27c4ce7040ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8f0b306af7a067e4dbd46bc8df7ca689770a3ce2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647798"
---
# <a name="bulk-insert-task"></a><span data-ttu-id="d6f10-102">대량 삽입 태스크</span><span class="sxs-lookup"><span data-stu-id="d6f10-102">Bulk Insert Task</span></span>
  <span data-ttu-id="d6f10-103">대량 삽입 태스크는 많은 양의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 또는 뷰에 복사할 수 있는 효율적인 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-103">The Bulk Insert task provides an efficient way to copy large amounts of data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="d6f10-104">예를 들어 회사에서 백만 개 행으로 구성된 제품 목록을 메인프레임 시스템에 저장하지만 회사의 전자 상거래 시스템이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 웹 페이지를 채운다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-104">For example, suppose your company stores its million-row product list on a mainframe system, but the company's e-commerce system uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to populate Web pages.</span></span> <span data-ttu-id="d6f10-105">또한 메인프레임의 마스터 제품 목록을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 제품 테이블을 매일 밤 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-105">You must update the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product table nightly with the master product list from the mainframe.</span></span> <span data-ttu-id="d6f10-106">테이블을 업데이트하려면 제품 목록을 탭 구분 형식으로 저장하고 대량 삽입 태스크를 사용하여 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 직접 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-106">To update the table, you save the product list in a tab-delimited format and use the Bulk Insert task to copy the data directly into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="d6f10-107">데이터를 고속으로 복사하려면 원본 파일에서 테이블 또는 뷰로 데이터가 이동하는 동안 데이터 변환을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-107">To ensure high-speed data copying, transformations cannot be performed on the data while it is moving from the source file to the table or view.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="d6f10-108">사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="d6f10-108">Usage Considerations</span></span>  
 <span data-ttu-id="d6f10-109">대량 삽입 태스크를 사용하기 전에 다음을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-109">Before you use the Bulk Insert task, consider the following:</span></span>  
  
-   <span data-ttu-id="d6f10-110">대량 삽입 태스크는 텍스트 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 또는 뷰로만 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-110">The Bulk Insert task can transfer data only from a text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="d6f10-111">대량 삽입 태스크를 사용하여 DBMS(데이터베이스 관리 시스템)에서 데이터를 전송하려면 원본 데이터를 텍스트 파일로 내보낸 다음 텍스트 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 또는 뷰로 데이터를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-111">To use the Bulk Insert task to transfer data from other database management systems (DBMSs), you must export the data from the source to a text file and then import the data from the text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
-   <span data-ttu-id="d6f10-112">대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 테이블 또는 뷰여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-112">The destination must be a table or view in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="d6f10-113">대상 테이블 또는 뷰에 이미 데이터가 포함되어 있으면 대량 삽입 태스크가 실행될 때 새 데이터가 기존 데이터에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-113">If the destination table or view already contains data, the new data is appended to the existing data when the Bulk Insert task runs.</span></span> <span data-ttu-id="d6f10-114">데이터를 대체하려면 대량 삽입 태스크를 실행하기 전에 DELETE 또는 TRUNCATE 문을 실행하는 SQL 실행 태스크를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-114">If you want to replace the data, run an Execute SQL task that runs a DELETE or TRUNCATE statement before you run the Bulk Insert task.</span></span> <span data-ttu-id="d6f10-115">자세한 내용은 [Execute SQL Task](execute-sql-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6f10-115">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
-   <span data-ttu-id="d6f10-116">대량 삽입 태스크 개체에 서식 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-116">You can use a format file in the Bulk Insert task object.</span></span> <span data-ttu-id="d6f10-117">**bcp** 유틸리티로 만든 서식 파일이 있으면 대량 삽입 태스크에 해당 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-117">If you have a format file that was created by the **bcp** utility, you can specify its path in the Bulk Insert task.</span></span> <span data-ttu-id="d6f10-118">대량 삽입 태스크는 XML 서식 파일과 비XML 서식 파일을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-118">The Bulk Insert task supports both XML and nonXML format files.</span></span> <span data-ttu-id="d6f10-119">서식 파일에 대한 자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6f10-119">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="d6f10-120">대량 삽입 태스크가 포함된 패키지는 sysadmin 고정 서버 역할의 멤버만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-120">Only members of the sysadmin fixed server role can run a package that contains a Bulk Insert task.</span></span>  
  
## <a name="bulk-insert-task-with-transactions"></a><span data-ttu-id="d6f10-121">트랜잭션의 대량 삽입 태스크</span><span class="sxs-lookup"><span data-stu-id="d6f10-121">Bulk Insert Task with Transactions</span></span>  
 <span data-ttu-id="d6f10-122">일괄 처리 크기를 설정하지 않으면 전체 대량 복사 작업이 하나의 트랜잭션으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-122">If a batch size is not set, the complete bulk copy operation is treated as one transaction.</span></span> <span data-ttu-id="d6f10-123">일괄 처리 크기가 **0** 이면 데이터는 하나의 일괄 처리로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-123">A batch size of **0** indicates that the data is inserted in one batch.</span></span> <span data-ttu-id="d6f10-124">일괄 처리 크기를 설정한 경우 각 일괄 처리는 일괄 처리 실행이 완료될 때 커밋되는 트랜잭션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-124">If a batch size is set, each batch represents a transaction that is committed when the batch finishes running.</span></span>  
  
 <span data-ttu-id="d6f10-125">트랜잭션과 관련이 있으므로 대량 삽입 태스크의 동작은 태스크의 패키지 트랜잭션 조인 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-125">The behavior of the Bulk Insert task, as it relates to transactions, depends on whether the task joins the package transaction.</span></span> <span data-ttu-id="d6f10-126">대량 삽입 태스크가 패키지 트랜잭션을 조인하지 않으면 오류가 없는 각 일괄 처리는 다음 일괄 처리가 시도되기 전에 하나의 단위로 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-126">If the Bulk Insert task does not join the package transaction, each error-free batch is committed as a unit before the next batch is tried.</span></span> <span data-ttu-id="d6f10-127">대량 삽입 태스크가 패키지 트랜잭션을 조인하면 오류가 없는 일괄 처리는 태스크의 마지막에 트랜잭션에 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-127">If the Bulk Insert task joins the package transaction, error-free batches remain in the transaction at the conclusion of the task.</span></span> <span data-ttu-id="d6f10-128">이러한 일괄 처리는 패키지의 커밋 또는 롤백 작업에 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-128">These batches are subject to the commit or rollback operation of the package.</span></span>  
  
 <span data-ttu-id="d6f10-129">대량 삽입 태스크가 실패해도 성공적으로 로드된 일괄 처리는 자동으로 롤백되지 않습니다. 이와 마찬가지로 태스크가 성공해도 일괄 처리가 자동으로 커밋되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-129">A failure in the Bulk Insert task does not automatically roll back successfully loaded batches; similarly, if the task succeeds, batches are not automatically committed.</span></span> <span data-ttu-id="d6f10-130">커밋 및 롤백 작업은 패키지 및 워크플로 속성 설정에 대한 응답으로만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-130">Commit and rollback operations occur only in response to package and workflow property settings.</span></span>  
  
## <a name="source-and-destination"></a><span data-ttu-id="d6f10-131">원본 및 대상</span><span class="sxs-lookup"><span data-stu-id="d6f10-131">Source and Destination</span></span>  
 <span data-ttu-id="d6f10-132">텍스트 원본 파일의 위치를 지정하는 경우 다음을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-132">When you specify the location of the text source file, consider the following:</span></span>  
  
-   <span data-ttu-id="d6f10-133">서버에 파일과 대상 데이터베이스에 모두 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-133">The server must have permission to access both the file and the destination database.</span></span>  
  
-   <span data-ttu-id="d6f10-134">대량 삽입 태스크는 서버에서 실행되므로</span><span class="sxs-lookup"><span data-stu-id="d6f10-134">The server runs the Bulk Insert task.</span></span> <span data-ttu-id="d6f10-135">태스크에 사용되는 모든 서식 파일이 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-135">Therefore, any format file that the task uses must be located on the server.</span></span>  
  
-   <span data-ttu-id="d6f10-136">대량 삽입 태스크가 로드하는 원본 파일은 데이터가 삽입될 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 동일한 서버나 원격 서버에 위치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-136">The source file that the Bulk Insert task loads can be on the same server as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, or on a remote server.</span></span> <span data-ttu-id="d6f10-137">원본 파일이 원격 서버에 있을 경우 경로에 UNC(Universal Naming Convention) 이름을 사용하여 파일 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-137">If the file is on a remote server, you must specify the file name using the Universal Naming Convention (UNC) name in the path.</span></span>  
  
## <a name="performance-optimization"></a><span data-ttu-id="d6f10-138">성능 최적화</span><span class="sxs-lookup"><span data-stu-id="d6f10-138">Performance Optimization</span></span>  
 <span data-ttu-id="d6f10-139">성능을 최적화하려면 다음을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-139">To optimize performance, consider the following:</span></span>  
  
-   <span data-ttu-id="d6f10-140">데이터가 삽입될 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 동일한 컴퓨터에 텍스트 파일이 있으면 데이터가 네트워크를 통해 이동하지 않으므로 복사 작업이 훨씬 빠른 속도로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-140">If the text file is located on the same computer as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, the copy operation occurs at an even faster rate because the data is not moved over the network.</span></span>  
  
-   <span data-ttu-id="d6f10-141">대량 삽입 태스크는 오류를 일으키는 행을 로깅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-141">The Bulk Insert task does not log error-causing rows.</span></span> <span data-ttu-id="d6f10-142">이 정보를 캡처해야 하는 경우 데이터 흐름 구성 요소의 오류 출력을 사용하여 오류를 일으키는 행을 예외 파일에 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-142">If you must capture this information, use the error outputs of data flow components to capture error-causing rows in an exception file.</span></span>  
  
## <a name="custom-log-entries-available-on-the-bulk-insert-task"></a><span data-ttu-id="d6f10-143">대량 삽입 태스크에 사용할 수 있는 사용자 지정 로그 항목</span><span class="sxs-lookup"><span data-stu-id="d6f10-143">Custom Log Entries Available on the Bulk Insert Task</span></span>  
 <span data-ttu-id="d6f10-144">다음 표에서는 대량 삽입 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-144">The following table lists the custom log entries for the Bulk Insert task.</span></span> <span data-ttu-id="d6f10-145">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6f10-145">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="d6f10-146">로그 항목</span><span class="sxs-lookup"><span data-stu-id="d6f10-146">Log entry</span></span>|<span data-ttu-id="d6f10-147">Description</span><span class="sxs-lookup"><span data-stu-id="d6f10-147">Description</span></span>|  
|---------------|-----------------|  
|`BulkInsertTaskBegin`|<span data-ttu-id="d6f10-148">대량 삽입이 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-148">Indicates that the bulk insert began.</span></span>|  
|`BulkInsertTaskEnd`|<span data-ttu-id="d6f10-149">대량 삽입이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-149">Indicates that the bulk insert finished.</span></span>|  
|`BulkInsertTaskInfos`|<span data-ttu-id="d6f10-150">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-150">Provides descriptive information about the task.</span></span>|  
  
## <a name="bulk-insert-task-configuration"></a><span data-ttu-id="d6f10-151">대량 삽입 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="d6f10-151">Bulk Insert Task Configuration</span></span>  
 <span data-ttu-id="d6f10-152">다음과 같은 방법으로 대량 삽입 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-152">You can configure the Bulk Insert task in the following ways:</span></span>  
  
-   <span data-ttu-id="d6f10-153">OLE DB 연결 관리자에서 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 및 데이터가 삽입될 테이블 또는 뷰에 연결하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-153">Specify the OLE DB connection manager to connect to the destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and the table or view into which data is inserted.</span></span> <span data-ttu-id="d6f10-154">대량 삽입 태스크에서는 대상 데이터베이스에 대한 OLE DB 연결만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-154">The Bulk Insert task supports only OLE DB connections for the destination database.</span></span>  
  
-   <span data-ttu-id="d6f10-155">파일 또는 플랫 파일 연결 관리자를 지정하여 원본 파일에 액세스하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6f10-155">Specify the File or Flat File connection manager to access the source file.</span></span> <span data-ttu-id="d6f10-156">대량 삽입 태스크의 경우 원본 파일의 위치에 대해서만 연결 관리자를 사용하고</span><span class="sxs-lookup"><span data-stu-id="d6f10-156">The Bulk Insert task uses the connection manager only for the location of the source file.</span></span> <span data-ttu-id="d6f10-157">연결 관리자 편집기에서 선택한 다른 옵션은 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-157">The task ignores other options that you select in the connection manager editor.</span></span>  
  
-   <span data-ttu-id="d6f10-158">서식 파일을 사용하거나 원본 데이터의 열 및 행 구분 기호를 정의하여 대량 삽입 태스크에 사용되는 서식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-158">Define the format that is used by the Bulk Insert task, either by using a format file or by defining the column and row delimiters of the source data.</span></span> <span data-ttu-id="d6f10-159">서식 파일을 사용하는 경우 파일 연결 관리자에서 서식 파일에 액세스하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-159">If using a format file, specify the File connection manager to access the format file.</span></span>  
  
-   <span data-ttu-id="d6f10-160">태스크에서 데이터를 삽입할 때 대상 테이블 또는 뷰에 대해 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-160">Specify actions to perform on the destination table or view when the task inserts the data.</span></span> <span data-ttu-id="d6f10-161">제약 조건 확인, ID 삽입 가능, Null 유지, 트리거 발생 또는 테이블 잠금 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-161">The options include whether to check constraints, enable identity inserts, keep nulls, fire triggers, or lock the table.</span></span>  
  
-   <span data-ttu-id="d6f10-162">일괄 처리 크기, 파일에서 삽입할 첫 번째 행과 마지막 행, 태스크가 행 삽입을 중지하기까지 발생할 수 있는 삽입 오류 수, 정렬될 열 이름 등 삽입할 일괄 처리 데이터에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-162">Provide information about the batch of data to insert, such as the batch size, the first and last row from the file to insert, the number of insert errors that can occur before the task stops inserting rows, and the names of the columns that will be sorted.</span></span>  
  
 <span data-ttu-id="d6f10-163">대량 삽입 태스크에서 플랫 파일 연결 관리자를 사용하여 원본 파일에 액세스하는 경우 태스크는 플랫 파일 연결 관리자에서 지정한 서식을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-163">If the Bulk Insert task uses a Flat File connection manager to access the source file, the task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="d6f10-164">대신 대량 삽입 태스크에서는 서식 파일에 지정된 서식이나 태스크의 RowDelimiter 및 ColumnDelimiter 속성 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-164">Instead, the Bulk Insert task uses either the format specified in a format file, or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="d6f10-165">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f10-165">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d6f10-166">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6f10-166">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d6f10-167">대량 삽입 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d6f10-167">Bulk Insert Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="d6f10-168">대량 삽입 태스크 편집기&#40;연결 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d6f10-168">Bulk Insert Task Editor &#40;Connection Page&#41;</span></span>](../bulk-insert-task-editor-connection-page.md)  
  
-   [<span data-ttu-id="d6f10-169">대량 삽입 태스크 편집기&#40;옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d6f10-169">Bulk Insert Task Editor &#40;Options Page&#41;</span></span>](../bulk-insert-task-editor-options-page.md)  
  
-   [<span data-ttu-id="d6f10-170">식 페이지</span><span class="sxs-lookup"><span data-stu-id="d6f10-170">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="d6f10-171">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6f10-171">For more information about how to setthese properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d6f10-172">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d6f10-172">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="programmatic-configuration-of-the-bulk-insert-task"></a><span data-ttu-id="d6f10-173">대량 삽입 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="d6f10-173">Programmatic Configuration of the Bulk Insert Task</span></span>  
 <span data-ttu-id="d6f10-174">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6f10-174">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="d6f10-175">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d6f10-175">Related Tasks</span></span>  
 [<span data-ttu-id="d6f10-176">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d6f10-176">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="d6f10-177">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d6f10-177">Related Content</span></span>  
  
-   <span data-ttu-id="d6f10-178">support.microsoft.com의 기술 문서 - [UAC 사용 시스템에서 "데이터 삽입을 위해 SSIS 대량 삽입을 준비할 수 없습니다." 오류가 발생할 수 있습니다.](https://go.microsoft.com/fwlink/?LinkId=233693)</span><span class="sxs-lookup"><span data-stu-id="d6f10-178">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=233693), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="d6f10-179">msdn.microsoft.com의 기술 문서 - [데이터 로드 성능 가이드](https://go.microsoft.com/fwlink/?LinkId=233700)</span><span class="sxs-lookup"><span data-stu-id="d6f10-179">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="d6f10-180">simple-talk.com의 기술 문서, [SQL Server Integration Services를 사용하여 데이터 대량 로드](https://go.microsoft.com/fwlink/?LinkId=233701)</span><span class="sxs-lookup"><span data-stu-id="d6f10-180">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
  
