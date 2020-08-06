---
title: 고유 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- unique indexes
- designing indexes [SQL Server], unique
- clustered indexes, unique
- indexes [SQL Server], unique
- nonclustered indexes [SQL Server], unique
- unique indexes, design guidelines
ms.assetid: 56b5982e-cb94-46c0-8fbb-772fc275354a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c96c4e17a8ce0863452db171302d650f6114919
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740943"
---
# <a name="create-unique-indexes"></a><span data-ttu-id="22515-102">고유 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="22515-102">Create Unique Indexes</span></span>
  <span data-ttu-id="22515-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블에 고유 인덱스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-103">This topic describes how to create a unique index on a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="22515-104">고유 인덱스는 인덱스 키에 중복 값을 포함할 수 없으므로 테이블의 모든 행이 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-104">A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique.</span></span> <span data-ttu-id="22515-105">UNIQUE 제약 조건을 만드는 것과 제약 조건의 영향을 받지 않는 고유 인덱스를 만드는 것에는 큰 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-105">There are no significant differences between creating a UNIQUE constraint and creating a unique index that is independent of a constraint.</span></span> <span data-ttu-id="22515-106">데이터 유효성 검사는 이와 동일한 방식으로 수행됩니다. 쿼리 최적화 프로그램에서는 제약 조건에 따라 생성된 고유 인덱스와 수동으로 만든 고유 인덱스를 동일하게 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-106">Data validation occurs in the same manner, and the query optimizer does not differentiate between a unique index created by a constraint or manually created.</span></span> <span data-ttu-id="22515-107">하지만 열에 UNIQUE 제약 조건을 만들면 인덱스의 목표가 명확해집니다.</span><span class="sxs-lookup"><span data-stu-id="22515-107">However, creating a UNIQUE constraint on the column makes the objective of the index clear.</span></span> <span data-ttu-id="22515-108">UNIQUE 제약 조건에 대한 자세한 내용은 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-108">For more information on UNIQUE constraints, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="22515-109">고유 인덱스를 만들 때 중복 키를 무시하도록 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-109">When you create a unique index, you can set an option to ignore duplicate keys.</span></span> <span data-ttu-id="22515-110">이 옵션을 **예** 로 설정하고 INSERT 문을 사용하여 여러 행에 적용되는 데이터 추가 작업을 수행하여 중복 키를 만들려고 하면 중복 키가 포함된 행이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-110">If this option is set to **Yes** and you attempt to create duplicate keys by adding data that affects multiple rows (with the INSERT statement), the row containing a duplicate is not added.</span></span> <span data-ttu-id="22515-111">이 옵션을 **아니요**로 설정하면 삽입 작업이 모두 실패하고 데이터 전체가 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-111">If it is set to **No**, the entire insert operation fails and all the data is rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22515-112">두 개 이상의 행에 NULL이 포함된 열이 있으면 단일 열에 대한 고유 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-112">You cannot create a unique index on a single column if that column contains NULL in more than one row.</span></span> <span data-ttu-id="22515-113">마찬가지로, 두 개 이상의 행에 NULL이 포함된 열 조합이 있으면 여러 열에 대한 고유 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-113">Similarly, you cannot create a unique index on multiple columns if the combination of columns contains NULL in more than one row.</span></span> <span data-ttu-id="22515-114">이러한 경우는 인덱싱과 관련하여 중복 값으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-114">These are treated as duplicate values for indexing purposes.</span></span>  
  
 <span data-ttu-id="22515-115">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="22515-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="22515-116">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="22515-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="22515-117">고유 인덱스의 이점</span><span class="sxs-lookup"><span data-stu-id="22515-117">Benefits of a Unique Index</span></span>](#Benefits)  
  
     [<span data-ttu-id="22515-118">일반적인 구현 방법</span><span class="sxs-lookup"><span data-stu-id="22515-118">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="22515-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="22515-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="22515-120">보안</span><span class="sxs-lookup"><span data-stu-id="22515-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="22515-121">**테이블에 고유 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="22515-121">**To create a unique index on a table, using:**</span></span>  
  
     [<span data-ttu-id="22515-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22515-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="22515-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22515-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22515-124">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="22515-124">Before You Begin</span></span>  
  
###  <a name="benefits-of-a-unique-index"></a><a name="Benefits"></a> <span data-ttu-id="22515-125">고유 인덱스의 이점</span><span class="sxs-lookup"><span data-stu-id="22515-125">Benefits of a Unique Index</span></span>  
  
-   <span data-ttu-id="22515-126">여러 열로 구성된 고유 인덱스를 사용하면 인덱스 키의 각 값 조합이 고유해집니다.</span><span class="sxs-lookup"><span data-stu-id="22515-126">Multicolumn unique indexes guarantee that each combination of values in the index key is unique.</span></span> <span data-ttu-id="22515-127">예를 들어 **LastName**, **FirstName**및 **MiddleName** 열의 조합에 대해 고유 인덱스를 만들면 테이블에 있는 각 행에서 이러한 열의 값 조합이 모두 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="22515-127">For example, if a unique index is created on a combination of **LastName**, **FirstName**, and **MiddleName** columns, no two rows in the table could have the same combination of values for these columns.</span></span>  
  
-   <span data-ttu-id="22515-128">따라서 각 열의 데이터가 고유하면 같은 테이블에서 하나의 고유 클러스터형 인덱스와 여러 개의 고유 비클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-128">Provided that the data in each column is unique, you can create both a unique clustered index and multiple unique nonclustered indexes on the same table.</span></span>  
  
-   <span data-ttu-id="22515-129">고유 인덱스를 사용하면 정의된 열의 데이터 무결성이 보장됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-129">Unique indexes ensure the data integrity of the defined columns.</span></span>  
  
-   <span data-ttu-id="22515-130">고유 인덱스가 제공하는 유용한 추가 정보를 통해 쿼리 최적화 프로그램은 더 효율적인 실행 계획을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-130">Unique indexes provide additional information helpful to the query optimizer that can produce more efficient execution plans.</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="22515-131">일반적인 구현 방법</span><span class="sxs-lookup"><span data-stu-id="22515-131">Typical Implementations</span></span>  
 <span data-ttu-id="22515-132">고유 인덱스는 다음과 같은 방법으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-132">Unique indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="22515-133">**PRIMARY KEY 또는 UNIQUE 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="22515-133">**PRIMARY KEY or UNIQUE constraint**</span></span>  
  
     <span data-ttu-id="22515-134">PRIMARY KEY 제약 조건을 만들 때 테이블에 클러스터형 인덱스가 없으며 고유 비클러스터형 인덱스를 지정하지 않은 경우 열에 고유 클러스터형 인덱스가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-134">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="22515-135">기본 키 열에는 NULL 값이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-135">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="22515-136">UNIQUE 제약 조건을 만들면 고유 비클러스터형 인덱스가 생성되어 기본적으로 UNIQUE 제약 조건을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-136">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="22515-137">테이블에 클러스터형 인덱스가 없는 경우 고유 클러스터형 인덱스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-137">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="22515-138">자세한 내용은 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) 및 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-138">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) and [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).</span></span>  
  
-   <span data-ttu-id="22515-139">**제약 조건의 영향을 받지 않는 인덱스**</span><span class="sxs-lookup"><span data-stu-id="22515-139">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="22515-140">한 테이블에 고유 비클러스터형 인덱스를 여러 개 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-140">Multiple unique nonclustered indexes can be defined on a table.</span></span>  
  
     <span data-ttu-id="22515-141">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-141">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="22515-142">**인덱싱된 뷰**</span><span class="sxs-lookup"><span data-stu-id="22515-142">**Indexed view**</span></span>  
  
     <span data-ttu-id="22515-143">인덱싱된 뷰를 만들기 위해 하나 이상의 뷰 열에 고유 클러스터형 인덱스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-143">To create an indexed view, a unique clustered index is defined on one or more view columns.</span></span> <span data-ttu-id="22515-144">뷰가 실행되고 클러스터형 인덱스에 테이블 데이터가 저장되는 것과 동일한 방법으로 결과 집합이 인덱스의 리프 수준에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="22515-144">The view is executed and the result set is stored in the leaf level of the index in the same way table data is stored in a clustered index.</span></span> <span data-ttu-id="22515-145">자세한 내용은 [인덱싱된 뷰 만들기](../views/views.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-145">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="22515-146">제한 사항</span><span class="sxs-lookup"><span data-stu-id="22515-146">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="22515-147">데이터에 중복된 키 값이 있으면 고유 인덱스, UNIQUE 제약 조건 또는 PRIMARY KEY 제약 조건을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-147">A unique index, UNIQUE constraint, or PRIMARY KEY constraint cannot be created if duplicate key values exist in the data.</span></span>  
  
-   <span data-ttu-id="22515-148">고유 비클러스터형 인덱스에는 키가 아닌 포괄 열이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-148">A unique nonclustered index can contain included nonkey columns.</span></span> <span data-ttu-id="22515-149">자세한 내용은 [Create Indexes with Included Columns](create-indexes-with-included-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-149">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="22515-150">보안</span><span class="sxs-lookup"><span data-stu-id="22515-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="22515-151">권한</span><span class="sxs-lookup"><span data-stu-id="22515-151">Permissions</span></span>  
 <span data-ttu-id="22515-152">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-152">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="22515-153">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-153">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="22515-154">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="22515-154">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-index-by-using-the-table-designer"></a><span data-ttu-id="22515-155">테이블 디자이너를 사용하여 고유 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="22515-155">To create a unique index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="22515-156">개체 탐색기에서 고유 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-156">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="22515-157">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-157">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="22515-158">고유 인덱스를 만들 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-158">Right-click the table on which you want to create a unique index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="22515-159">**테이블 디자이너** 메뉴에서 **인덱스/키**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-159">On the **Table Designer** menu, select **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="22515-160">**인덱스/키** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-160">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="22515-161">**선택한 기본/고유 키 또는 인덱스** 입력란에서 새 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-161">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="22515-162">주 표의 **(일반)** 에서 **유형** 을 선택한 다음 목록에서 **인덱스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-162">In the main grid, under **(General)**, select **Type** and then choose **Index** from the list.</span></span>  
  
8.  <span data-ttu-id="22515-163">**열**을 선택한 다음, 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-163">Select **Columns**, and then click the ellipsis **(...)**.</span></span>  
  
9. <span data-ttu-id="22515-164">**인덱스 열** 대화 상자의 **열 이름**에서 인덱스를 작성할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-164">In the **Index Columns** dialog box, under **Column Name**, select the columns you want to index.</span></span> <span data-ttu-id="22515-165">최대 16개의 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-165">You can select up to 16 columns.</span></span> <span data-ttu-id="22515-166">최상의 성능을 얻으려면 인덱스별로 열을 한두 개만 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="22515-166">For optimal performance, select only one or two columns per index.</span></span> <span data-ttu-id="22515-167">선택한 각 열에 대해 해당 열의 인덱스 값을 오름차순으로 정렬할지 내림차순으로 정렬할지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-167">For each column you select, indicate whether the index arranges values of this column in ascending or descending order.</span></span>  
  
10. <span data-ttu-id="22515-168">인덱스의 모든 열을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-168">When all columns for the index are selected, click **OK**.</span></span>  
  
11. <span data-ttu-id="22515-169">표의 **(일반)** 에서 **고유 여부** 를 선택한 다음 목록에서 **예** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-169">In the grid, under **(General)**, select **Is Unique** and then choose **Yes** from the list.</span></span>  
  
12. <span data-ttu-id="22515-170">선택 사항: 주 표의 **테이블 디자이너**에서 **중복 키 무시** 를 선택한 다음 목록에서 **예** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-170">Optional: In the main grid, under **Table Designer**, select **Ignore Duplicate Keys** and then choose **Yes** from the list.</span></span> <span data-ttu-id="22515-171">고유 인덱스에 중복 키를 만드는 데이터를 추가하려는 시도를 무시하려는 경우 이와 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-171">Do this if you want to ignore attempts to add data that would create a duplicate key in the unique index.</span></span>  
  
13. <span data-ttu-id="22515-172">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-172">Click **Close**.</span></span>  
  
14. <span data-ttu-id="22515-173">**파일** 메뉴에서 _table name_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-173">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="create-a-unique-index-by-using-object-explorer"></a><span data-ttu-id="22515-174">개체 탐색기를 사용하여 고유 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="22515-174">Create a unique index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="22515-175">개체 탐색기에서 고유 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-175">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="22515-176">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-176">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="22515-177">고유 인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-177">Expand the table on which you want to create a unique index.</span></span>  
  
4.  <span data-ttu-id="22515-178">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 가리킨 다음, **비클러스터형 인덱스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-178">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="22515-179">**새 인덱스** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 새 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-179">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="22515-180">**고유** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-180">Select the **Unique** check box.</span></span>  
  
7.  <span data-ttu-id="22515-181">**인덱스 키 열** 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-181">Under **Index key columns**, click **Add...**.</span></span>  
  
8.  <span data-ttu-id="22515-182">_Table_name_ **에서 열 선택**대화 상자에서 고유 인덱스에 추가할 테이블 열의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-182">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
9. <span data-ttu-id="22515-183">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-183">Click **OK**.</span></span>  
  
10. <span data-ttu-id="22515-184">**새 인덱스** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-184">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="22515-185">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="22515-185">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-index-on-a-table"></a><span data-ttu-id="22515-186">테이블에 고유 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="22515-186">To create a unique index on a table</span></span>  
  
1.  <span data-ttu-id="22515-187">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-187">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="22515-188">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-188">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="22515-189">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22515-189">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named AK_UnitMeasure_Name and delete it if found  
    IF EXISTS (SELECT name from sys.indexes  
               WHERE name = N'AK_UnitMeasure_Name')   
       DROP INDEX AK_UnitMeasure_Name ON Production.UnitMeasure;   
    GO  
    -- Create a unique index called AK_UnitMeasure_Name  
    -- on the Production.UnitMeasure table using the Name column.  
    CREATE UNIQUE INDEX AK_UnitMeasure_Name   
       ON Production.UnitMeasure (Name);   
    GO  
    ```  
  
 <span data-ttu-id="22515-190">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22515-190">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
