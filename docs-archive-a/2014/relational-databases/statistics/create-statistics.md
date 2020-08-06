---
title: 통계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.propertis.f1
- sql12.swb.statistics.filter.f1
- sql12.swb.stat.properties.f1
- sql12.swb.stat.columns.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 230bd4d840c3d59dc1267dd6801754b68386cb32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659885"
---
# <a name="create-statistics"></a><span data-ttu-id="4431c-102">통계 만들기</span><span class="sxs-lookup"><span data-stu-id="4431c-102">Create Statistics</span></span>
  <span data-ttu-id="4431c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블 또는 인덱싱된 뷰의 하나 이상의 열에 대한 쿼리 최적화 통계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-103">You can create query optimization statistics on one or more columns of a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4431c-104">대부분의 쿼리에서 쿼리 최적화 프로그램은 고품질의 쿼리 계획에 필요한 통계를 이미 생성하므로 경우에 따라서 추가 통계를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-104">For most queries, the query optimizer already generates the necessary statistics for a high-quality query plan; in a few cases, you need to create additional statistics.</span></span>  
  
 <span data-ttu-id="4431c-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4431c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4431c-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4431c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4431c-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4431c-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4431c-108">보안</span><span class="sxs-lookup"><span data-stu-id="4431c-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4431c-109">**다음을 사용하여 통계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="4431c-109">**To create statistics, using:**</span></span>  
  
     [<span data-ttu-id="4431c-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4431c-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4431c-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4431c-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4431c-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4431c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4431c-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4431c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4431c-114">CREATE STATISTICS 문을 사용하여 통계를 만들기 전에 AUTO_CREATE_STATISTICS 옵션이 데이터베이스 수준에서 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-114">Before creating statistics with the CREATE STATISTICS statement, verify that the AUTO_CREATE_STATISTICS option is set at the database level.</span></span> <span data-ttu-id="4431c-115">이렇게 하면 쿼리 최적화 프로그램이 정기적으로 쿼리 조건자 열에 대한 단일 열 통계를 계속 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-115">This will ensure that the query optimizer continues to routinely create single-column statistics for query predicate columns.</span></span>  
  
-   <span data-ttu-id="4431c-116">정적 개체당 최대 32개의 열을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-116">You can list up to 32 columns per statistics object.</span></span>  
  
-   <span data-ttu-id="4431c-117">필터링된 통계 조건자에 정의된 테이블 열의 정의에 대해 삭제, 이름 변경 또는 변경을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-117">You cannot drop, rename, or alter the definition of a table column that is defined in a filtered statistics predicate.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4431c-118">보안</span><span class="sxs-lookup"><span data-stu-id="4431c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4431c-119">권한</span><span class="sxs-lookup"><span data-stu-id="4431c-119">Permissions</span></span>  
 <span data-ttu-id="4431c-120">사용자가 테이블 또는 인덱싱된 뷰의 소유자이거나 **sysadmin** 고정 서버 역할, **db_owner** 고정 데이터베이스 역할 또는 **db_ddladmin** 고정 데이터베이스 역할 중 하나의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-120">Requires that the user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4431c-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4431c-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="4431c-122">통계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4431c-122">To create statistics</span></span>  
  
1.  <span data-ttu-id="4431c-123">**개체 탐색기**에서 더하기 기호를 클릭하여 새 통계를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-123">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="4431c-124">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="4431c-125">더하기 기호를 클릭하여 새 통계를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-125">Click the plus sign to expand the table in which you want to create a new statistic.</span></span>  
  
4.  <span data-ttu-id="4431c-126">**통계** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 통계...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-126">Right-click the **Statistics** folder and select **New Statistics...**.</span></span>  
  
     <span data-ttu-id="4431c-127">테이블_table_name_ **에 대 한 새 통계**대화 상자의 **일반** 페이지에 다음 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-127">The following properties show on the **General** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="4431c-128">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="4431c-128">**Table Name**</span></span>  
     <span data-ttu-id="4431c-129">통계에서 설명하는 테이블 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-129">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="4431c-130">**통계 이름**</span><span class="sxs-lookup"><span data-stu-id="4431c-130">**Statistics Name**</span></span>  
     <span data-ttu-id="4431c-131">통계가 저장되는 데이터베이스 개체 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-131">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="4431c-132">**통계 열**</span><span class="sxs-lookup"><span data-stu-id="4431c-132">**Statistics Columns**</span></span>  
     <span data-ttu-id="4431c-133">이 통계 집합에서 설명하는 열을 보여 주는 표입니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-133">This grid shows the columns described by this set of statistics.</span></span> <span data-ttu-id="4431c-134">표의 모든 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-134">All values in the grid are read-only.</span></span>  
  
     <span data-ttu-id="4431c-135">**이름**</span><span class="sxs-lookup"><span data-stu-id="4431c-135">**Name**</span></span>  
     <span data-ttu-id="4431c-136">통계에서 설명하는 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-136">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="4431c-137">하나의 열일 수도 있고 단일 테이블의 열 조합일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-137">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="4431c-138">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="4431c-138">**Data Type**</span></span>  
     <span data-ttu-id="4431c-139">통계에서 설명하는 열의 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-139">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="4431c-140">**크기**</span><span class="sxs-lookup"><span data-stu-id="4431c-140">**Size**</span></span>  
     <span data-ttu-id="4431c-141">각 열에 대한 데이터 형식의 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-141">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="4431c-142">**ID**</span><span class="sxs-lookup"><span data-stu-id="4431c-142">**Identity**</span></span>  
     <span data-ttu-id="4431c-143">선택 시 ID 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-143">Indicates an identity column when it is checked.</span></span>  
  
     <span data-ttu-id="4431c-144">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="4431c-144">**Allow Nulls**</span></span>  
     <span data-ttu-id="4431c-145">열에 NULL 값을 사용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-145">Indicates whether the column accepts NULL values.</span></span>  
  
     <span data-ttu-id="4431c-146">**추가**</span><span class="sxs-lookup"><span data-stu-id="4431c-146">**Add**</span></span>  
     <span data-ttu-id="4431c-147">테이블의 추가 열을 통계 표에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-147">Add additional columns from the table to the statistics grid.</span></span>  
  
     <span data-ttu-id="4431c-148">**제거**</span><span class="sxs-lookup"><span data-stu-id="4431c-148">**Remove**</span></span>  
     <span data-ttu-id="4431c-149">선택한 열을 통계 표에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-149">Remove the selected column from the statistics grid.</span></span>  
  
     <span data-ttu-id="4431c-150">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="4431c-150">**Move Up**</span></span>  
     <span data-ttu-id="4431c-151">선택한 열을 통계 표에서 이전 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-151">Move the selected column to an earlier location in the statistics grid.</span></span> <span data-ttu-id="4431c-152">표에서의 위치는 통계 유용성에 큰 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-152">The location in the grid can substantially impact the usefulness of the statistics.</span></span>  
  
     <span data-ttu-id="4431c-153">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="4431c-153">**Move Down**</span></span>  
     <span data-ttu-id="4431c-154">선택한 열을 통계 표에서 이후 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-154">Move the selected column to a later location in the statistics grid.</span></span>  
  
     <span data-ttu-id="4431c-155">**이 열에 대한 통계 마지막 업데이트:**</span><span class="sxs-lookup"><span data-stu-id="4431c-155">**Statistics for these columns were last updated:**</span></span>  
     <span data-ttu-id="4431c-156">통계가 얼마나 오래되었는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-156">Indicates how old the statistics are.</span></span> <span data-ttu-id="4431c-157">통계는 최신 상태일 때 더욱 가치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-157">Statistics are more valuable when they are current.</span></span> <span data-ttu-id="4431c-158">데이터가 크게 변경되거나 부정형 데이터를 추가한 후에는 통계를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-158">Update statistics after large changes to the data or after adding atypical data.</span></span> <span data-ttu-id="4431c-159">데이터가 일관성 있게 배포된 테이블 통계는 자주 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-159">Statistics for tables that have a consistent distribution of data need to be updated less frequently.</span></span>  
  
     <span data-ttu-id="4431c-160">**이 열에 대한 통계 업데이트**</span><span class="sxs-lookup"><span data-stu-id="4431c-160">**Update statistics for these columns**</span></span>  
     <span data-ttu-id="4431c-161">대화 상자를 닫을 때 통계를 업데이트하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-161">Check to update the statistics when the dialog box is closed.</span></span>  
  
     <span data-ttu-id="4431c-162">다음 속성은 **테이블에 대 한 새 통계**_Table_name_ 대화 상자의 **필터** 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-162">The following property shows on the **Filter** page in the **New Statistics on Table**_table_name_ dialog box.</span></span>  
  
     <span data-ttu-id="4431c-163">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="4431c-163">**Filter Expression**</span></span>  
     <span data-ttu-id="4431c-164">필터링된 통계에 포함할 데이터 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-164">Defines which data rows to include in the filtered statistics.</span></span> <span data-ttu-id="4431c-165">예를 들어 `Production.ProductSubcategoryID IN ( 1,2,3 )`</span><span class="sxs-lookup"><span data-stu-id="4431c-165">For example, `Production.ProductSubcategoryID IN ( 1,2,3 )`</span></span>  
  
5.  <span data-ttu-id="4431c-166">테이블 table_name **에 대 한 새 통계**_table_name_ 대화 상자의 **일반** 페이지에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-166">In the **New Statistics on Table**_table_name_ dialog box, on the **General** page, click **Add**.</span></span>  
  
     <span data-ttu-id="4431c-167">**열 선택** 대화 상자에 표시되는 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-167">The following properties show in the **Select Columns** dialog box.</span></span> <span data-ttu-id="4431c-168">이 정보는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-168">This information is read-only.</span></span>  
  
     <span data-ttu-id="4431c-169">**이름**</span><span class="sxs-lookup"><span data-stu-id="4431c-169">**Name**</span></span>  
     <span data-ttu-id="4431c-170">통계에서 설명하는 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-170">Displays the name of the column described by the statistics.</span></span> <span data-ttu-id="4431c-171">하나의 열일 수도 있고 단일 테이블의 열 조합일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-171">This can be a single column or a combination of columns in a single table.</span></span>  
  
     <span data-ttu-id="4431c-172">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="4431c-172">**Data Type**</span></span>  
     <span data-ttu-id="4431c-173">통계에서 설명하는 열의 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-173">Indicates the data type of the columns described by the statistics.</span></span>  
  
     <span data-ttu-id="4431c-174">**크기**</span><span class="sxs-lookup"><span data-stu-id="4431c-174">**Size**</span></span>  
     <span data-ttu-id="4431c-175">각 열에 대한 데이터 형식의 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-175">Displays the size of the data type for each column.</span></span>  
  
     <span data-ttu-id="4431c-176">**ID**</span><span class="sxs-lookup"><span data-stu-id="4431c-176">**Identity**</span></span>  
     <span data-ttu-id="4431c-177">선택 시 ID 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-177">Indicates an identity column when checked.</span></span>  
  
     <span data-ttu-id="4431c-178">**NULL 허용**</span><span class="sxs-lookup"><span data-stu-id="4431c-178">**Allow NULLs**</span></span>  
     <span data-ttu-id="4431c-179">열에 NULL 값을 사용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-179">Indicates whether the column accepts NULL values.</span></span>  
  
6.  <span data-ttu-id="4431c-180">**열 선택** 대화 상자에서 통계를 만들려는 각 열의 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-180">In the **Select Columns** dialog box, select the check box or check boxes of each column for which you want to create a statistic and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4431c-181">테이블 table_name **에 대 한 새 통계**_table_name_ 대화 상자에서 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-181">In the **New Statistics on Table**_table_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4431c-182">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4431c-182">Using Transact-SQL</span></span>  
  
#### <a name="to-create-statistics"></a><span data-ttu-id="4431c-183">통계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4431c-183">To create statistics</span></span>  
  
1.  <span data-ttu-id="4431c-184">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4431c-185">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4431c-186">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  <span data-ttu-id="4431c-187">위에서 만든 통계는 다음 쿼리의 결과를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4431c-187">The statistic created above potentially improves the results for the following query.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 <span data-ttu-id="4431c-188">자세한 내용은 [CREATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4431c-188">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
