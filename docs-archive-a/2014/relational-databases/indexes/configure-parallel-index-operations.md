---
title: 병렬 인덱스 작업 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index parallel operations [SQL Server]
- processors [SQL Server], parallel index operations
- max degree of parallelism option
- MAXDOP index option, parallel index operations
- parallel index operations [SQL Server]
ms.assetid: 8ec8c71e-5fc1-443a-92da-136ee3fc7f88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8831aadae15af03a05f4ab03cfe514e54566df1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646436"
---
# <a name="configure-parallel-index-operations"></a><span data-ttu-id="24da8-102">병렬 인덱스 작업 구성</span><span class="sxs-lookup"><span data-stu-id="24da8-102">Configure Parallel Index Operations</span></span>
  <span data-ttu-id="24da8-103">이 항목에서는 최대 병렬 처리 수준을 정의하고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 이 설정을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-103">This topic defines max degree of parallelism and explains how to modify this setting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="24da8-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 이상을 실행하는 다중 프로세서 컴퓨터에서는 다른 쿼리와 마찬가지로 인덱스 문이 여러 프로세서를 사용하여 인덱스 문과 관련된 검색, 정렬 및 인덱스 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-104">On multiprocessor computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise or higher, index statements may use multiple processors to perform the scan, sort, and index operations associated with the index statement just like other queries do.</span></span> <span data-ttu-id="24da8-105">단일 인덱스 문 실행에 사용되는 프로세서 수는 [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) 구성 옵션, 현재 작업 및 인덱스 통계에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-105">The number of processors used to run a single index statement is determined by the [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) configuration option, the current workload, and the index statistics.</span></span> <span data-ttu-id="24da8-106">max degree of parallelism 옵션은 병렬 계획 실행에 사용할 프로세서의 최대 개수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-106">The max degree of parallelism option determines the maximum number of processors to use in parallel plan execution.</span></span> <span data-ttu-id="24da8-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 시스템에서 진행 중인 작업이 많음을 감지하면 문이 실행되기 전에 인덱스 작업의 병렬 처리 수준이 자동으로 감소됩니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-107">If the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] detects that the system is busy, the degree of parallelism of the index operation is automatically reduced before statement execution starts.</span></span> <span data-ttu-id="24da8-108">분할되지 않은 인덱스의 선행 키 열의 고유 값 수가 제한되거나 각 고유 값의 빈도가 상당히 다양한 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 병렬 처리 수준을 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-108">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can also reduce the degree of parallelism if the leading key column of a non-partitioned index has a limited number of distinct values or the frequency of each distinct value varies significantly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24da8-109">병렬 인덱스 작업은 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-109">Parallel index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="24da8-110">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24da8-110">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="24da8-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="24da8-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="24da8-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="24da8-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="24da8-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="24da8-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="24da8-114">보안</span><span class="sxs-lookup"><span data-stu-id="24da8-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="24da8-115">**최대 병렬 처리 수준을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="24da8-115">**To set the max degree of parallelism, using:**</span></span>  
  
     [<span data-ttu-id="24da8-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="24da8-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="24da8-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="24da8-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24da8-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="24da8-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="24da8-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="24da8-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="24da8-120">쿼리 최적화 프로그램에서 사용하는 프로세서 수는 대개 최적의 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-120">The number of processors that are used by the query optimizer typically provides optimal performance.</span></span> <span data-ttu-id="24da8-121">그러나 매우 큰 인덱스를 생성, 다시 작성 및 삭제하는 작업에서는 리소스가 많이 소모되므로 인덱스 작업 중 다른 애플리케이션 및 데이터베이스 작업에 사용할 리소스가 부족할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-121">However, operations such as creating, rebuilding, or dropping very large indexes are resource intensive and can cause insufficient resources for other applications and database operations for the duration of the index operation.</span></span> <span data-ttu-id="24da8-122">이 문제가 발생하면 인덱스 작업에 사용할 프로세서 수를 제한하여 인덱스 문 실행에 사용되는 최대 프로세서 수를 직접 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-122">When this problem occurs, you can manually configure the maximum number of processors that are used to run the index statement by limiting the number of processors to use for the index operation.</span></span>  
  
-   <span data-ttu-id="24da8-123">MAXDOP 인덱스 옵션을 지정한 쿼리에 대해서만 max degree of parallelism 구성 옵션이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-123">The MAXDOP index option overrides the max degree of parallelism configuration option only for the query specifying this option.</span></span> <span data-ttu-id="24da8-124">다음 표에서는 최대 병렬 처리 수준 구성 옵션 및 MAXDOP 인덱스 옵션에 지정할 수 있는 유효한 정수 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-124">The following table lists the valid integer values that can be specified with the max degree of parallelism configuration option and the MAXDOP index option.</span></span>  
  
    |<span data-ttu-id="24da8-125">값</span><span class="sxs-lookup"><span data-stu-id="24da8-125">Value</span></span>|<span data-ttu-id="24da8-126">설명</span><span class="sxs-lookup"><span data-stu-id="24da8-126">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="24da8-127">0</span><span class="sxs-lookup"><span data-stu-id="24da8-127">0</span></span>|<span data-ttu-id="24da8-128">서버가 현재 시스템 작업에 따라 사용되는 CPU의 수를 결정하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-128">Specifies that the server determines the number of CPUs that are used, depending on the current system workload.</span></span> <span data-ttu-id="24da8-129">이 값은 기본값이며 권장 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-129">This is the default value and recommended setting.</span></span>|  
    |<span data-ttu-id="24da8-130">1</span><span class="sxs-lookup"><span data-stu-id="24da8-130">1</span></span>|<span data-ttu-id="24da8-131">병렬 계획이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-131">Suppresses parallel plan generation.</span></span> <span data-ttu-id="24da8-132">작업이 직렬로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-132">The operation will be executed serially.</span></span>|  
    |<span data-ttu-id="24da8-133">2-64</span><span class="sxs-lookup"><span data-stu-id="24da8-133">2-64</span></span>|<span data-ttu-id="24da8-134">지정된 값으로 프로세서 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-134">Limits the number of processors to the specified value.</span></span> <span data-ttu-id="24da8-135">현재 작업에 따라 지정된 것보다 적은 수의 프로세서가 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-135">Fewer processors may be used depending on the current workload.</span></span> <span data-ttu-id="24da8-136">사용 가능한 CPU 수보다 더 큰 수를 지정하면 사용 가능한 실제 CPU 수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-136">If a value larger than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>|  
  
-   <span data-ttu-id="24da8-137">다음은 병렬 인덱스 실행 및 MAXDOP 인덱스 옵션이 적용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-137">Parallel index execution and the MAXDOP index option apply to the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    -   <span data-ttu-id="24da8-138">CREATE  INDEX</span><span class="sxs-lookup"><span data-stu-id="24da8-138">CREATE INDEX</span></span>  
  
    -   <span data-ttu-id="24da8-139">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="24da8-139">ALTER INDEX REBUILD</span></span>  
  
    -   <span data-ttu-id="24da8-140">DROP INDEX(클러스터형 인덱스에만 해당)</span><span class="sxs-lookup"><span data-stu-id="24da8-140">DROP INDEX (This applies to clustered indexes only.)</span></span>  
  
    -   <span data-ttu-id="24da8-141">ALTER TABLE ADD (인덱스) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="24da8-141">ALTER TABLE ADD (index) CONSTRAINT</span></span>  
  
    -   <span data-ttu-id="24da8-142">ALTER TABLE DROP (클러스터형 인덱스) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="24da8-142">ALTER TABLE DROP (clustered index) CONSTRAINT</span></span>  
  
-   <span data-ttu-id="24da8-143">ALTER INDEX REORGANIZE 문에서 MAXDOP 인덱스 옵션을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-143">The MAXDOP index option cannot be specified in the ALTER INDEX REORGANIZE statement.</span></span>  
  
-   <span data-ttu-id="24da8-144">쿼리 최적화 프로그램에서 작성 작업에 병렬 처리 수준을 적용할 경우 정렬이 필요한 분할 인덱스 작업의 메모리 요구 사항이 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-144">Memory requirements for partitioned index operations that require sorting can be greater if the query optimizer applies degrees of parallelism to the build operation.</span></span> <span data-ttu-id="24da8-145">병렬 처리 수준이 높을수록 메모리 요구 사항이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-145">The higher the degrees of parallelism, the greater the memory requirement is.</span></span> <span data-ttu-id="24da8-146">자세한 내용은 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24da8-146">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="24da8-147">보안</span><span class="sxs-lookup"><span data-stu-id="24da8-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="24da8-148">권한</span><span class="sxs-lookup"><span data-stu-id="24da8-148">Permissions</span></span>  
 <span data-ttu-id="24da8-149">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-149">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="24da8-150">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="24da8-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-index"></a><span data-ttu-id="24da8-151">인덱스에 대한 최대 병렬 처리 수준을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="24da8-151">To set max degree of parallelism on an index</span></span>  
  
1.  <span data-ttu-id="24da8-152">개체 탐색기에서 더하기 기호를 클릭하여 인덱스에 대한 최대 병렬 처리 수준을 설정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to set max degree of parallelism for an index.</span></span>  
  
2.  <span data-ttu-id="24da8-153">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-153">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="24da8-154">더하기 기호를 클릭하여 인덱스에 대한 최대 병렬 처리 수준을 설정할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-154">Click the plus sign to expand the table on which you want to set max degree of parallelism for an index.</span></span>  
  
4.  <span data-ttu-id="24da8-155">**인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-155">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="24da8-156">최대 병렬 처리 수준을 설정할 인덱스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-156">Right-click the index for which you want to set the max degree of parallelism and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="24da8-157">**페이지 선택**아래에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="24da8-158">**최대 병렬 처리 수준**을 선택하고 1에서 64 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-158">Select **Maximum degree of parallelism**, and then enter some value between 1 and 64.</span></span>  
  
8.  <span data-ttu-id="24da8-159">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="24da8-160">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="24da8-160">Using Transact-SQL</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-existing-index"></a><span data-ttu-id="24da8-161">기존 인덱스에 대한 최대 병렬 처리 수준을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="24da8-161">To set max degree of parallelism on an existing index</span></span>  
  
1.  <span data-ttu-id="24da8-162">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="24da8-163">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="24da8-164">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-164">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Alters the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table so that, if the server has eight or more processors, the Database Engine will limit the execution of the index operation to eight or fewer processors.  
    */  
    ALTER INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor  
    REBUILD WITH (MAXDOP=8);   
    GO  
    ```  
  
 <span data-ttu-id="24da8-165">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24da8-165">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
#### <a name="set-max-degree-of-parallelism-on-a-new-index"></a><span data-ttu-id="24da8-166">새 인덱스에 대한 최대 병렬 처리 수준 설정</span><span class="sxs-lookup"><span data-stu-id="24da8-166">Set max degree of parallelism on a new index</span></span>  
  
1.  <span data-ttu-id="24da8-167">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="24da8-168">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="24da8-169">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24da8-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE INDEX IX_ProductVendor_NewVendorID   
    ON Purchasing.ProductVendor (BusinessEntityID)  
    WITH (MAXDOP=8);  
    GO  
    ```  
  
 <span data-ttu-id="24da8-170">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24da8-170">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
