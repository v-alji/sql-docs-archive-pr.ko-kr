---
title: 메모리 내 OLTP에 대한 SQL Server Management Studio 지원 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ee847b5f-6a1a-448e-a746-d61a023881ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 644ba0cfdbe2f0043364c633676bbc536c641efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646444"
---
# <a name="sql-server-management-studio-support-for-in-memory-oltp"></a><span data-ttu-id="c31cd-102">메모리 내 OLTP에 대한 SQL Server Management Studio 지원</span><span class="sxs-lookup"><span data-stu-id="c31cd-102">SQL Server Management Studio Support for In-Memory OLTP</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c31cd-103">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인프라를 관리하기 위한 통합 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-103">is an integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c31cd-104">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 구성, 모니터링 및 관리하는 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-104">provides tools to configure, monitor, and administer instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c31cd-105">자세한 내용은 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31cd-105">For more information, see [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span></span>  
  
 <span data-ttu-id="c31cd-106">이 항목의 태스크에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 메모리 최적화 테이블, 메모리 최적화 테이블의 인덱스, 고유하게 컴파일된 저장 프로시저, 사용자 정의 메모리 최적화 테이블 형식을 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-106">The tasks in this topic describe how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage memory-optimized tables; indexes on memory-optimized tables; natively compiled stored procedures; and user-defined, memory-optimized table types.</span></span>  
  
 <span data-ttu-id="c31cd-107">프로그래밍 방식으로 메모리 최적화 테이블을 만드는 방법은 [메모리 최적화 테이블 및 고유하게 컴파일된 저장 프로시저 만들기](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31cd-107">For information on how to programmatically create memory-optimized tables, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-database-with-a-memory-optimized-data-filegroup"></a><span data-ttu-id="c31cd-108">메모리 최적화 데이터 파일 그룹이 포함된 데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c31cd-108">To create a database with a memory-optimized data filegroup</span></span>  
  
1.  <span data-ttu-id="c31cd-109">**개체 탐색기**에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-109">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c31cd-110">**데이터베이스**를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-110">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="c31cd-111">새 메모리 최적화 데이터 파일 그룹을 추가하려면 **파일 그룹** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-111">To add a new memory-optimized data filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="c31cd-112">**MEMORY OPTIMIZED DATA**아래에서 **파일 그룹 추가** 를 클릭한 다음 메모리 최적화 데이터 파일 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-112">Under **MEMORY OPTIMIZED DATA**, click **Add filegroup** and then enter the name of the memory-optimized data filegroup.</span></span>  <span data-ttu-id="c31cd-113">**FILESTREAM 파일** 이라는 열에는 파일 그룹에 있는 컨테이너 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-113">The column labeled **FILESTREAM Files** represents the number of containers in the filegroup.</span></span> <span data-ttu-id="c31cd-114">컨테이너는 **일반** 페이지에서 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-114">Containers are added on the **General** page.</span></span>  
  
4.  <span data-ttu-id="c31cd-115">파일(컨테이너)를 파일 그룹에 추가하려면 **일반** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-115">To add a file (container) to the filegroup, click the **General** page.</span></span> <span data-ttu-id="c31cd-116">**데이터베이스 파일**아래에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-116">Under **Database files**, click **Add**.</span></span> <span data-ttu-id="c31cd-117">**파일 형식** 을 **FILESTREAM 데이터**로 선택하고 컨테이너의 논리적 이름을 지정한 다음 메모리 최적화 파일 그룹을 선택하고 **자동 증가/최대 크기** 가 **제한 없음**으로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-117">Select **File Type** as **FILESTREAM Data**, specify the logical name of the container, select the memory-optimized filegroup, and make sure that **Autogrowth / Maxsize** is set to **Unlimited**.</span></span>  
  
     <span data-ttu-id="c31cd-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 새 데이터베이스를 만드는 방법은 [데이터베이스 만들기](../databases/create-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31cd-118">For more information on how to create a new database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Create a Database](../databases/create-a-database.md).</span></span>  
  
### <a name="to-create-a-memory-optimized-table"></a><span data-ttu-id="c31cd-119">메모리 최적화 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c31cd-119">To create a memory-optimized table</span></span>  
  
1.  <span data-ttu-id="c31cd-120">**개체 탐색기**에서 데이터베이스의 **테이블** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 클릭한 다음 **메모리 액세스에 최적화된 테이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-120">In **Object Explorer**, right-click the **Tables** node of your database, click **New**, and then click **Memory Optimized Table**.</span></span>  
  
     <span data-ttu-id="c31cd-121">메모리 최적화 테이블을 만들기 위한 템플릿이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-121">A template for creating memory-optimized tables is displayed.</span></span>  
  
2.  <span data-ttu-id="c31cd-122">템플릿 매개 변수를 바꾸려면 **쿼리** 메뉴에서 **템플릿 매개 변수 값 지정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-122">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="c31cd-123">템플릿을 사용하는 방법은 [Template Explorer](../../ssms/template/template-explorer.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c31cd-123">For more information on how to use templates, see [Template Explorer](../../ssms/template/template-explorer.md).</span></span>  
  
3.  <span data-ttu-id="c31cd-124">**개체 탐색기**에서 테이블은 먼저 디스크 기반 테이블에 따라 정렬된 다음, 메모리 최적화 테이블에 따라 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-124">In **Object Explorer**, tables will be ordered first by disk-based tables followed by memory-optimized tables.</span></span> <span data-ttu-id="c31cd-125">**개체 탐색기 정보** 를 사용하여 모든 테이블을 이름순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-125">Use **Object Explorer Details** to see all tables ordered by name.</span></span>  
  
### <a name="to-create-a-natively-compiled-stored-procedure"></a><span data-ttu-id="c31cd-126">고유하게 컴파일된 저장 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c31cd-126">To create a natively compiled stored procedure</span></span>  
  
1.  <span data-ttu-id="c31cd-127">**개체 탐색기**에서 데이터베이스의 **저장 프로시저** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 클릭한 다음 **고유하게 컴파일된 저장 프로시저**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-127">In **Object Explorer**, right-click the **Stored Procedures** node of your database, click **New**, and then click **Natively Compiled Stored Procedure**.</span></span>  
  
     <span data-ttu-id="c31cd-128">고유하게 컴파일된 저장 프로시저를 만들기 위한 템플릿이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-128">A template for creating natively compiled stored procedures is displayed.</span></span>  
  
2.  <span data-ttu-id="c31cd-129">템플릿 매개 변수를 바꾸려면 **쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-129">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query menu**.</span></span>  
  
     <span data-ttu-id="c31cd-130">새 저장 프로시저를 만드는 방법은 [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c31cd-130">For more information on how to create a new stored procedure, see [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-user-defined-memory-optimized-table-type"></a><span data-ttu-id="c31cd-131">사용자 정의 메모리 최적화 테이블 형식을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c31cd-131">To create a user-defined memory-optimized table type</span></span>  
  
1.  <span data-ttu-id="c31cd-132">**개체 탐색기**에서 데이터베이스의 **형식** 노드를 확장하고 **사용자 정의 테이블 형식** 노드를 마우스 오른쪽 단추로 클릭한 다음 **새로 만들기**를 클릭하고 **사용자 정의 메모리 액세스에 최적화된 테이블 형식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-132">In **Object Explorer**, expand the **Types** node of your database, right-click the **User-Defined Table Types** node, click **New**, and then click **User-Defined Memory Optimized Table Type**.</span></span>  
  
     <span data-ttu-id="c31cd-133">사용자 정의 메모리 최적화 테이블 형식을 만들기 위한 템플릿이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-133">A template for creating user-defined memory-optimized table type is displayed.</span></span>  
  
2.  <span data-ttu-id="c31cd-134">템플릿 매개 변수를 바꾸려면 **쿼리** 메뉴에서 **템플릿 매개 변수 값 지정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-134">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="c31cd-135">새 저장 프로시저를 만드는 방법은 [CREATE TYPE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31cd-135">For more information on how to create a new stored procedure, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
## <a name="memory-monitoring"></a><span data-ttu-id="c31cd-136">메모리 모니터링</span><span class="sxs-lookup"><span data-stu-id="c31cd-136">Memory Monitoring</span></span>  
  
#### <a name="view-memory-usage-by-memory-optimized-objects-report"></a><span data-ttu-id="c31cd-137">메모리 액세스에 최적화된 개체별 메모리 사용량 보고서 보기</span><span class="sxs-lookup"><span data-stu-id="c31cd-137">View Memory Usage by Memory-Optimized Objects Report</span></span>  
  
-   <span data-ttu-id="c31cd-138">**개체 탐색기**에서 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **보고서**, **표준 보고서**, **메모리 액세스에 최적화된 개체별 메모리 사용량**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-138">In **Object Explorer**, right-click your database, click **Reports**, click **Standard Reports**, and then click **Memory Usage By Memory Optimized Objects**.</span></span>  
  
     <span data-ttu-id="c31cd-139">이 보고서는 데이터베이스에 있는 메모리 최적화 개체의 메모리 공간 사용률에 대한 자세한 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-139">This report provides detailed data on the utilization of memory space by memory-optimized objects within the database.</span></span>  
  
#### <a name="view-properties-for-allocated-and-used-memory-for-a-table-database"></a><span data-ttu-id="c31cd-140">테이블 또는 데이터베이스에 대해 할당되고 사용된 메모리에 대한 속성 보기</span><span class="sxs-lookup"><span data-stu-id="c31cd-140">View Properties for Allocated and Used Memory for a Table, Database</span></span>  
  
1.  <span data-ttu-id="c31cd-141">메모리 내 사용량에 대한 정보를 가져오려면 다음과 같이 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c31cd-141">To get information about in-memory usage:</span></span>  
  
    -   <span data-ttu-id="c31cd-142">**개체 탐색기**에서 메모리 최적화 테이블을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 **스토리지** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-142">In **Object Explorer**, right-click on your memory-optimized table, click **Properties**, and then the **Storage** page.</span></span> <span data-ttu-id="c31cd-143">**데이터 공간** 속성에 대한 값은 테이블에 있는 데이터가 사용하는 메모리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-143">The value for the **Data Space** property indicates the memory used by the data in the table.</span></span> <span data-ttu-id="c31cd-144">**인덱스 공간** 속성에 대한 값은 테이블의 인덱스가 사용하는 메모리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-144">The value for the **Index Space** property indicates the memory used by the indexes on table.</span></span>  
  
    -   <span data-ttu-id="c31cd-145">**개체 탐색기**에서 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 **일반** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-145">In **Object Explorer**, right-click on your database, click **Properties**, and then click the **General** page.</span></span> <span data-ttu-id="c31cd-146">**메모리 최적화 개체에 할당된 메모리** 속성에 대한 값은 데이터베이스에 있는 메모리 최적화 개체에 할당된 메모리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-146">The value for the **Memory Allocated To Memory Optimized Objects** property indicates the memory allocated to memory-optimized objects in the database.</span></span> <span data-ttu-id="c31cd-147">**메모리 최적화 개체가 사용하는 메모리** 속성에 대한 값은 데이터베이스에 있는 메모리 최적화 개체가 사용하는 메모리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-147">The value for the **Memory Used By Memory Optimized Objects** property indicates the memory used by memory-optimized objects in the database.</span></span>  
  
## <a name="supported-features-in-ssmanstudiofull"></a><span data-ttu-id="c31cd-148">다음에서 지원되는 기능 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c31cd-148">Supported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="c31cd-149">는 메모리 최적화 데이터 파일 그룹, 메모리 최적화 테이블, 인덱스 및 고유하게 컴파일된 저장 프로시저가 포함된 데이터베이스에서 데이터베이스 엔진이 지원하는 기능과 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-149">supports features and operations that are supported by the database engine on databases with memory-optimized data filegroup, memory-optimized tables, indexes, and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="c31cd-150">데이터베이스, 테이블, 저장 프로시저, 사용자 정의 테이블 형식 또는 인덱스 개체에 대해 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 기능이 메모리 내 OLTP를 지원하도록 업데이트되었거나 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-150">For database, table, stored procedure, user-defined table type, or index objects, the following [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] features have been updated or extended to support In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="c31cd-151">개체 탐색기</span><span class="sxs-lookup"><span data-stu-id="c31cd-151">Object Explorer</span></span>  
  
    -   <span data-ttu-id="c31cd-152">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="c31cd-152">Context menus</span></span>  
  
    -   <span data-ttu-id="c31cd-153">필터 설정</span><span class="sxs-lookup"><span data-stu-id="c31cd-153">Filter settings</span></span>  
  
    -   <span data-ttu-id="c31cd-154">스크립팅</span><span class="sxs-lookup"><span data-stu-id="c31cd-154">Script As</span></span>  
  
    -   <span data-ttu-id="c31cd-155">작업</span><span class="sxs-lookup"><span data-stu-id="c31cd-155">Tasks</span></span>  
  
    -   <span data-ttu-id="c31cd-156">보고서</span><span class="sxs-lookup"><span data-stu-id="c31cd-156">Reports</span></span>  
  
    -   <span data-ttu-id="c31cd-157">속성</span><span class="sxs-lookup"><span data-stu-id="c31cd-157">Properties</span></span>  
  
    -   <span data-ttu-id="c31cd-158">데이터베이스 태스크:</span><span class="sxs-lookup"><span data-stu-id="c31cd-158">Database tasks:</span></span>  
  
        -   <span data-ttu-id="c31cd-159">메모리 최적화 테이블이 포함된 데이터베이스 연결 및 분리</span><span class="sxs-lookup"><span data-stu-id="c31cd-159">Attach and detach a database that contains memory-optimized tables.</span></span>  
  
             <span data-ttu-id="c31cd-160">**데이터베이스 연결** 사용자 인터페이스는 메모리 최적화 데이터 파일 그룹을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-160">The **Attach Databases** user interface does not display the memory-optimized data filegroup.</span></span> <span data-ttu-id="c31cd-161">그러나 데이터베이스 연결은 계속 진행할 수 있으며 데이터베이스는 올바르게 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-161">However, you can proceed with attaching the database and the database will be attached correctly.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="c31cd-162">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 메모리 최적화 데이터 파일 그룹 컨테이너가 있는 데이터베이스를 연결하려고 하는데 데이터베이스의 메모리 최적화 데이터 파일 그룹 컨테이너가 다른 컴퓨터에서 만든 것이라면 메모리 최적화 데이터 파일 그룹 컨테이너의 위치가 두 컴퓨터에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-162">If you want to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to attach a database that has a memory-optimized data filegroup container, and if the database's memory-optimized data filegroup container was created on another computer, the location of the memory-optimized data filegroup container must be the same on both computers.</span></span> <span data-ttu-id="c31cd-163">데이터베이스의 메모리 최적화 데이터 파일 그룹 컨테이너 위치를 새 컴퓨터에서 다르게 지정하려는 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-163">If you want the location of the database's memory-optimized data filegroup container to be different on the new computer, you can, use [!INCLUDE[tsql](../../includes/tsql-md.md)] to attach the database.</span></span> <span data-ttu-id="c31cd-164">다음 예에서 새 컴퓨터의 메모리 최적화 데이터 파일 그룹 컨테이너 위치는 C:\Folder2입니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-164">In the following example, the location of the memory-optimized data filegroup container on the new computer is C:\Folder2.</span></span> <span data-ttu-id="c31cd-165">그러나 첫 번째 컴퓨터에서 메모리 최적화 데이터 파일 그룹 컨테이너가 생성된 위치는 C:\Folder1입니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-165">But when the memory-optimized data filegroup container was created, on the first computer, the location was C:\Folder1.</span></span>  
            >   
            >  `CREATE DATABASE[imoltp] ON`  
            >   
            >  `(NAME =N'imoltp',FILENAME=N'C:\Folder2\imoltp.mdf'),`  
            >   
            >  `(NAME =N'imoltp_mod1',FILENAME=N'C:\Folder2\imoltp_mod1'),`  
            >   
            >  `(NAME =N'imoltp_log',FILENAME=N'C:\Folder2\imoltp_log.ldf')`  
            >   
            >  `FOR ATTACH`  
            >   
            >  `GO`  
  
        -   <span data-ttu-id="c31cd-166">스크립트 생성</span><span class="sxs-lookup"><span data-stu-id="c31cd-166">Generate scripts.</span></span>  
  
             <span data-ttu-id="c31cd-167">**스크립트 생성 및 게시 마법사**에서 **개체의 존재 여부 확인** 스크립팅 옵션의 기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-167">In the **Generate and Publish Scripts Wizard**, the default value for **Check for object existence** scripting option is FALSE.</span></span> <span data-ttu-id="c31cd-168">**개체의 존재 여부 확인** 스크립팅 옵션의 값을 마법사의 **스크립팅 옵션 설정** 화면에서 TRUE로 설정하면 생성되는 스크립트에는 "CREATE PROCEDURE <procedure_name> AS" 및 "ALTER PROCEDURE <procedure_name> <procedure_definition>"이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-168">If the value of **Check for object existence** scripting option is set to TRUE in the **Set Scripting Options** screen of the wizard, the script generated would contain "CREATE PROCEDURE <procedure_name> AS" and "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span> <span data-ttu-id="c31cd-169">고유하게 컴파일된 저장 프로시저에서는 ALTER PROCEDURE가 지원되지 않으므로 생성된 스크립트를 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-169">When executed, the generated script will return an error as ALTER PROCEDURE is not supported on natively compiled stored procedures.</span></span>  
  
             <span data-ttu-id="c31cd-170">각각의 고유하게 컴파일된 저장 프로시저에 대해 생성되는 스크립트를 변경하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-170">To change the generated script for each natively compiled stored procedure:</span></span>  
  
            1.  <span data-ttu-id="c31cd-171">"CREATE PROCEDURE <procedure_name> AS"에서 "AS"를 "<procedure_definition>"으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-171">In "CREATE PROCEDURE <procedure_name> AS", replace "AS" with "<procedure_definition>".</span></span>  
  
            2.  <span data-ttu-id="c31cd-172">"ALTER PROCEDURE <procedure_name> <procedure_definition>"을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-172">Delete "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span>  
  
        -   <span data-ttu-id="c31cd-173">데이터베이스 복사.</span><span class="sxs-lookup"><span data-stu-id="c31cd-173">Copy databases.</span></span> <span data-ttu-id="c31cd-174">메모리 최적화 개체가 포함된 데이터베이스의 경우 대상 서버에서 데이터베이스 만들기 및 데이터 전송이 트랜잭션 내에서 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-174">For databases with memory-optimized objects, the creation of the database on the destination server and transfer of data will not be executed within a transaction.</span></span>  
  
        -   <span data-ttu-id="c31cd-175">데이터 가져오기 및 내보내기.</span><span class="sxs-lookup"><span data-stu-id="c31cd-175">Import and export data.</span></span> <span data-ttu-id="c31cd-176">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 하나 이상의 테이블 또는 뷰에서 데이터 복사** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-176">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export WizardCopy data from one or more tables or views** option.</span></span> <span data-ttu-id="c31cd-177">대상 테이블이 대상 데이터베이스에 존재하지 않는 메모리 최적화 테이블인 경우:</span><span class="sxs-lookup"><span data-stu-id="c31cd-177">If the destination table is a memory-optimized table that does not exist in the destination database:</span></span>  
  
            1.  <span data-ttu-id="c31cd-178">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사**의 **테이블 복사 또는 쿼리 지정** 화면에서 **하나 이상의 테이블 또는 뷰에서 데이터 복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-178">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard**, in the **Specify Table Copy or Query** screen, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="c31cd-179">그런 후 **Next** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-179">Then click **Next**.</span></span>  
  
            2.  <span data-ttu-id="c31cd-180">**매핑 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-180">Click **Edit Mappings**.</span></span> <span data-ttu-id="c31cd-181">그런 다음 **대상 테이블 만들기** 를 선택하고 **SQL 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-181">Then select **Create destination table** and click **Edit SQL**.</span></span> <span data-ttu-id="c31cd-182">대상 데이터베이스에서 메모리 최적화 테이블을 만드는 CREATE TABLE 구문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-182">Enter the CREATE TABLE syntax for creating a memory-optimized table on the destination database.</span></span> <span data-ttu-id="c31cd-183">**확인** 을 클릭하고 마법사의 나머지 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-183">Click **OK** and complete the remaining steps in the wizard.</span></span>  
  
        -   <span data-ttu-id="c31cd-184">유지 관리 계획.</span><span class="sxs-lookup"><span data-stu-id="c31cd-184">Maintenance plans.</span></span> <span data-ttu-id="c31cd-185">유지 관리 태스크인 인덱스 다시 구성 및 인덱스 다시 작성은 메모리 최적화 테이블과 해당 인덱스에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-185">The maintenance tasks reorganize index and rebuild index are not supported on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="c31cd-186">따라서 인덱스 다시 작성 및 인덱스 다시 구성에 대한 유지 관리 계획을 실행하면 선택한 데이터베이스에서 메모리 최적화 테이블과 해당 인덱스가 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-186">Therefore, when a maintenance plan for rebuild index and reorganize index are executed, the memory-optimized tables and their indexes in the selected databases are omitted.</span></span>  
  
             <span data-ttu-id="c31cd-187">유지 관리 태스크 업데이트 통계는 메모리 최적화 테이블과 해당 인덱스에 대한 예제 검사에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-187">The maintenance task update statistics are not supported with a sample scan on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="c31cd-188">따라서 통계 업데이트에 대한 유지 관리 계획을 실행하면 메모리 최적화 테이블과 해당 인덱스에 대한 통계는 항상 `WITH FULLSCAN, NORECOMPUTE`로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-188">Therefore, when a maintenance plan for update statistics is executed, the statistics for memory-optimized tables and their indexes are always updated to `WITH FULLSCAN, NORECOMPUTE`.</span></span>  
  
-   <span data-ttu-id="c31cd-189">개체 탐색기 정보 창</span><span class="sxs-lookup"><span data-stu-id="c31cd-189">Object Explorer details pane</span></span>  
  
-   <span data-ttu-id="c31cd-190">Template Explorer</span><span class="sxs-lookup"><span data-stu-id="c31cd-190">Template Explorer</span></span>  
  
## <a name="unsupported-features-in-ssmanstudiofull"></a><span data-ttu-id="c31cd-191">다음에서 지원되지 않는 기능 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c31cd-191">Unsupported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="c31cd-192">메모리 내 OLTP 개체의 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 는 데이터베이스 엔진이 지원하지 않는 기능과 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31cd-192">For In-Memory OLTP objects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not support features and operations that are also not supported by the database engine.</span></span>  
  
 <span data-ttu-id="c31cd-193">지원 되지 않는 기능에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [지원 되는 SQL Server 기능](unsupported-sql-server-features-for-in-memory-oltp.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c31cd-193">For more information on unsupported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features, see [Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c31cd-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c31cd-194">See Also</span></span>  
 [<span data-ttu-id="c31cd-195">메모리 내 OLTP에 대한 SQL Server 지원</span><span class="sxs-lookup"><span data-stu-id="c31cd-195">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  
