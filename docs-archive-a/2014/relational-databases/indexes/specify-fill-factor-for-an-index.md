---
title: 인덱스의 채우기 비율 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- fill factor [SQL Server]
- page splits [SQL Server]
ms.assetid: 237a577e-b42b-4adb-90cf-aa7fb174f3ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac54f2b22de55ed74c4635ec0f86d008c7624a42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739916"
---
# <a name="specify-fill-factor-for-an-index"></a><span data-ttu-id="4bd36-102">인덱스의 채우기 비율 지정</span><span class="sxs-lookup"><span data-stu-id="4bd36-102">Specify Fill Factor for an Index</span></span>
  <span data-ttu-id="4bd36-103">이 항목에서는 채우기 비율의 역할에 대해 설명하고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱스의 채우기 비율 값을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-103">This topic describes what fill factor is and how to specify a fill factor value on an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4bd36-104">채우기 비율 옵션은 미세 조정 인덱스 데이터 스토리지와 성능을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-104">The fill-factor option is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="4bd36-105">인덱스를 만들거나 다시 작성할 때 채우기 비율에 따라 각 리프 수준 페이지에서 데이터로 채울 공간 비율이 결정되므로 각 페이지에서 나머지 부분을 이후 인덱스 증가에 대비한 여유 공간으로 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the remainder on each page as free space for future growth.</span></span> <span data-ttu-id="4bd36-106">예를 들어 채우기 비율 값을 80으로 지정하면 기본 테이블의 데이터 추가에 따른 인덱스 확장을 위해 각 리프 수준 페이지의 20%가 비게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-106">For example, specifying a fill-factor value of 80 means that 20 percent of each leaf-level page will be left empty, providing space for index expansion as data is added to the underlying table.</span></span> <span data-ttu-id="4bd36-107">빈 공간은 인덱스의 끝이 아닌 인덱스 행 간에 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-107">The empty space is reserved between the index rows rather than at the end of the index.</span></span>  
  
 <span data-ttu-id="4bd36-108">채우기 비율 값은 0%에서 100% 사이이며 서버 차원의 기본값은 0입니다. 이 값은 리프 수준 페이지가 꽉 채워짐을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-108">The fill-factor value is a percentage from 1 to 100, and the server-wide default is 0 which means that the leaf-level pages are filled to capacity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bd36-109">채우기 비율 값 0과 100은 모든 면에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-109">Fill-factor values 0 and 100 are the same in all respects.</span></span>  
  
 <span data-ttu-id="4bd36-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4bd36-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4bd36-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4bd36-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4bd36-112">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4bd36-112">Performance Considerations</span></span>](#Performance)  
  
     [<span data-ttu-id="4bd36-113">보안</span><span class="sxs-lookup"><span data-stu-id="4bd36-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4bd36-114">**인덱스의 채우기 비율을 지정하려면:**</span><span class="sxs-lookup"><span data-stu-id="4bd36-114">**To specify a fill factor in an index, using:**</span></span>  
  
     [<span data-ttu-id="4bd36-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4bd36-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4bd36-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4bd36-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4bd36-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4bd36-117">Before You Begin</span></span>  
  
###  <a name="performance-considerations"></a><a name="Performance"></a> <span data-ttu-id="4bd36-118">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4bd36-118">Performance Considerations</span></span>  
  
#### <a name="page-splits"></a><span data-ttu-id="4bd36-119">페이지 분할</span><span class="sxs-lookup"><span data-stu-id="4bd36-119">Page Splits</span></span>  
 <span data-ttu-id="4bd36-120">채우기 비율 값을 적절히 선택하여 기본 테이블에 데이터가 추가될 때 인덱스 확장을 위한 충분한 공간을 제공함으로써 페이지 분할 가능성을 줄일 수 있습니다. 가득찬 인덱스 페이지에 새 행이 추가되면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 행의 절반 정도를 새 페이지로 옮겨 새 행을 위한 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-120">A correctly chosen fill-factor value can reduce potential page splits by providing enough space for index expansion as data is added to the underlying table.When a new row is added to a full index page, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] moves approximately half the rows to a new page to make room for the new row.</span></span> <span data-ttu-id="4bd36-121">이러한 재구성을 페이지 분할이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-121">This reorganization is known as a page split.</span></span> <span data-ttu-id="4bd36-122">페이지 분할은 새 레코드를 위한 공간을 만들지만 수행하는 데 시간이 걸리고 리소스를 많이 사용하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-122">A page split makes room for new records, but can take time to perform and is a resource intensive operation.</span></span> <span data-ttu-id="4bd36-123">또한 I/O 작업을 늘리는 조각화의 원인이 되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-123">Also, it can cause fragmentation that causes increased I/O operations.</span></span> <span data-ttu-id="4bd36-124">페이지가 자주 분할되면 새 채우기 비율 값이나 기존 채우기 비율 값으로 데이터를 재배포하여 인덱스를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-124">When frequent page splits occur, the index can be rebuilt by using a new or existing fill-factor value to redistribute the data.</span></span> <span data-ttu-id="4bd36-125">자세한 내용은 [인덱스 다시 구성 및 다시 작성](reorganize-and-rebuild-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bd36-125">For more information, see [Reorganize and Rebuild Indexes](reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="4bd36-126">채우기 비율 값을 0이 아닌 낮은 값으로 설정하면 인덱스 증가에 따른 페이지 분할을 줄일 수 있지만 인덱스에 더 많은 스토리지 공간이 필요하게 되고 읽기 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-126">Although a low, nonzero fill-factor value may reduce the requirement to split pages as the index grows, the index will require more storage space and can decrease read performance.</span></span> <span data-ttu-id="4bd36-127">삽입 및 업데이트 작업이 많은 애플리케이션에서도 대개 데이터베이스 읽기 횟수가 데이터베이스 쓰기 횟수보다 10 대 5 정도로 훨씬 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-127">Even for an application oriented for many insert and update operations, the number of database reads typically outnumber database writes by a factor of 5 to 10.</span></span> <span data-ttu-id="4bd36-128">따라서 기본값 이외의 채우기 비율을 지정하면 채우기 비율 설정에 반비례하는 양만큼 데이터베이스 읽기 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-128">Therefore, specifying a fill factor other than the default can decrease database read performance by an amount inversely proportional to the fill-factor setting.</span></span> <span data-ttu-id="4bd36-129">예를 들어 채우기 비율 값을 50으로 지정하면 데이터베이스 읽기 성능이 두 배 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-129">For example, a fill-factor value of 50 can cause database read performance to decrease by two times.</span></span> <span data-ttu-id="4bd36-130">인덱스에 더 많은 페이지가 포함되므로 읽기 성능이 저하되어 데이터 검색에 필요한 디스크 IO 작업이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-130">Read performance is decreased because the index contains more pages, therefore increasing the disk IO operations required to retrieve the data.</span></span>  
  
#### <a name="adding-data-to-the-end-of-the-table"></a><span data-ttu-id="4bd36-131">테이블 끝에 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="4bd36-131">Adding Data to the End of the Table</span></span>  
 <span data-ttu-id="4bd36-132">새 데이터가 테이블에 균일하게 분포된 경우 0이나 100이 아닌 채우기 비율을 지정하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-132">A nonzero fill factor other than 0 or 100 can be good for performance if the new data is evenly distributed throughout the table.</span></span> <span data-ttu-id="4bd36-133">그러나 모든 데이터를 테이블 끝에 추가한 경우 인덱스 페이지의 빈 공간이 꽉 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-133">However, if all the data is added to the end of the table, the empty space in the index pages will not be filled.</span></span> <span data-ttu-id="4bd36-134">예를 들어 인덱스 키 열이 IDENTITY 열이면 새 행의 키는 항상 증가하며 인덱스 행은 인덱스 끝에 논리적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-134">For example, if the index key column is an IDENTITY column, the key for new rows is always increasing and the index rows are logically added to the end of the index.</span></span> <span data-ttu-id="4bd36-135">행의 크기를 늘리는 데이터로 기존 행을 업데이트하려는 경우 100 미만의 채우기 비율을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-135">If existing rows will be updated with data that lengthens the size of the rows, use a fill factor of less than 100.</span></span> <span data-ttu-id="4bd36-136">각 페이지에 추가 바이트를 설정하면 길어지는 행으로 인해 발생하는 페이지 분할을 최소화하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-136">The extra bytes on each page will help to minimize page splits caused by extra length in the rows.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4bd36-137">보안</span><span class="sxs-lookup"><span data-stu-id="4bd36-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4bd36-138">권한</span><span class="sxs-lookup"><span data-stu-id="4bd36-138">Permissions</span></span>  
 <span data-ttu-id="4bd36-139">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-139">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="4bd36-140">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-140">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4bd36-141">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4bd36-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-fill-factor-by-using-table-designer"></a><span data-ttu-id="4bd36-142">테이블 디자이너를 사용하여 채우기 비율을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="4bd36-142">To specify a fill factor by using Table Designer</span></span>  
  
1.  <span data-ttu-id="4bd36-143">개체 탐색기에서 더하기 기호를 클릭하여 인덱스의 채우기 비율을 지정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-143">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="4bd36-144">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-144">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4bd36-145">인덱스의 채우기 비율을 지정할 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-145">Right-click the table on which you want to specify an index's fill factor and select **Design**.</span></span>  
  
4.  <span data-ttu-id="4bd36-146">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-146">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="4bd36-147">채우기 비율을 지정할 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-147">Select the index with the fill factor that you want to specify.</span></span>  
  
6.  <span data-ttu-id="4bd36-148">**채우기 사양**을 확장하고 **채우기 비율** 행을 선택한 다음 원하는 채우기 비율을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-148">Expand **Fill Specification**, select the **Fill Factor** row and enter the fill factor you want in the row.</span></span>  
  
7.  <span data-ttu-id="4bd36-149">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-149">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="4bd36-150">**파일** 메뉴에서 _table_name_**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-150">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-index-by-using-object-explorer"></a><span data-ttu-id="4bd36-151">개체 탐색기를 사용하여 인덱스의 채우기 비율을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="4bd36-151">To specify a fill factor in an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="4bd36-152">개체 탐색기에서 더하기 기호를 클릭하여 인덱스의 채우기 비율을 지정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to specify an index's fill factor.</span></span>  
  
2.  <span data-ttu-id="4bd36-153">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4bd36-154">더하기 기호를 클릭하여 인덱스의 채우기 비율을 지정할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-154">Click the plus sign to expand the table on which you want to specify an index's fill factor.</span></span>  
  
4.  <span data-ttu-id="4bd36-155">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="4bd36-156">채우기 비율을 지정할 인덱스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-156">Right-click the index with the fill factor that you want to specify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="4bd36-157">**페이지 선택**아래에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="4bd36-158">**채우기 비율** 행에 원하는 채우기 비율을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-158">In the **Fill factor** row, enter the fill factor that you want.</span></span>  
  
8.  <span data-ttu-id="4bd36-159">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4bd36-160">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4bd36-160">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-fill-factor-in-an-existing-index"></a><span data-ttu-id="4bd36-161">기존 인덱스의 채우기 비율을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="4bd36-161">To specify a fill factor in an existing index</span></span>  
  
1.  <span data-ttu-id="4bd36-162">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4bd36-163">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4bd36-164">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-164">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4bd36-165">이 예에서는 기존 인덱스를 다시 작성하고 다시 작성하는 동안 지정한 채우기 비율을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-165">The example rebuilds an existing index and applies the specified fill factor during the rebuild operation.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Rebuilds the IX_Employee_OrganizationLevel_OrganizationNode index   
    -- with a fill factor of 80 on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD WITH (FILLFACTOR = 80);   
    GO  
    ```  
  
#### <a name="another-way-to-specify-a-fill-factor-in-an-index"></a><span data-ttu-id="4bd36-166">인덱스의 채우기 비율을 지정하는 다른 방법</span><span class="sxs-lookup"><span data-stu-id="4bd36-166">Another way to specify a fill factor in an index</span></span>  
  
1.  <span data-ttu-id="4bd36-167">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4bd36-168">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4bd36-169">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd36-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    /* Drops and re-creates the IX_Employee_OrganizationLevel_OrganizationNode index on the HumanResources.Employee table with a fill factor of 80.  
    */  
  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)   
    WITH (DROP_EXISTING = ON, FILLFACTOR = 80);   
    GO  
    ```  
  
 <span data-ttu-id="4bd36-170">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bd36-170">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
