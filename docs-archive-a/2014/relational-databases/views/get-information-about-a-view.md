---
title: 뷰 정보 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.viewproperties.general.f1
helpviewer_keywords:
- views [SQL Server], status information
- metadata [SQL Server], views
- dependencies [SQL Server], views
- displaying view information
- views [SQL Server], metadata
- viewing view information
- status information [SQL Server], views
- view dependencies
ms.assetid: 05a73e33-8f85-4fb6-80c1-1b659e753403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4277aad4c1de0140606575c7ba437408518b3c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646260"
---
# <a name="get-information-about-a-view"></a><span data-ttu-id="824bf-102">뷰 정보 보기</span><span class="sxs-lookup"><span data-stu-id="824bf-102">Get Information About a View</span></span>
  <span data-ttu-id="824bf-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을(를) 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 뷰 정의 또는 속성에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-103">You can gain information about a view's definition or properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="824bf-104">뷰 정의를 보면 어떻게 데이터가 원본 테이블에서 파생되었는지 알 수 있고 뷰에서 정의한 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-104">You may need to see the definition of the view to understand how its data is derived from the source tables or to see the data defined by the view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="824bf-105">뷰가 참조하는 개체의 이름을 변경하려면 뷰를 수정하여 뷰의 텍스트에 새 이름이 적용되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-105">If you change the name of an object referenced by a view, you must modify the view so that its text reflects the new name.</span></span> <span data-ttu-id="824bf-106">따라서 개체 이름을 바꾸기 전에는 개체의 종속 관계를 먼저 표시하여 변경으로 인해 영향을 받는 뷰가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any views are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="824bf-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="824bf-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="824bf-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="824bf-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="824bf-109">보안</span><span class="sxs-lookup"><span data-stu-id="824bf-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="824bf-110">**뷰에 대한 정보를 얻으려면:**</span><span class="sxs-lookup"><span data-stu-id="824bf-110">**To get information about a view, using:**</span></span>  
  
     [<span data-ttu-id="824bf-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="824bf-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="824bf-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="824bf-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="824bf-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="824bf-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="824bf-114">보안</span><span class="sxs-lookup"><span data-stu-id="824bf-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="824bf-115">권한</span><span class="sxs-lookup"><span data-stu-id="824bf-115">Permissions</span></span>  
 <span data-ttu-id="824bf-116">`sp_helptext` 를 사용하여 뷰의 정의를 반환하려면 **공용** 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-116">Using `sp_helptext` to return the definition of a view requires membership in the **public** role.</span></span> <span data-ttu-id="824bf-117">`sys.sql_expression_dependencies` 를 사용하여 뷰의 모든 종속성을 찾으려면 데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 `sys.sql_expression_dependencies` 에 대한 SELECT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-117">Using `sys.sql_expression_dependencies` to find all the dependencies on a view requires VIEW DEFINITION permission on the database and SELECT permission on `sys.sql_expression_dependencies` for the database.</span></span> <span data-ttu-id="824bf-118">SELECT OBJECT_DEFINITION에 반환되는 정의와 같은 시스템 개체 정의는 모두에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-118">System object definitions, like the ones returned in SELECT OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="824bf-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="824bf-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="get-view-properties-by-using-object-explorer"></a><span data-ttu-id="824bf-120">개체 탐색기를 사용하여 뷰 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="824bf-120">Get view properties by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="824bf-121">**개체 탐색기**에서 속성을 볼 뷰가 포함된 데이터베이스 옆의 더하기 기호를 클릭한 다음 더하기 기호를 클릭하여 **뷰** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-121">In **Object Explorer**, click the plus sign next to the database that contains the view to which you want to view the properties, and then click the plus sign to expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="824bf-122">속성을 볼 뷰를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-122">Right-click the view of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="824bf-123">**속성 보기** 대화 상자에 표시되는 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-123">The following properties show in the **View Properties** dialog box.</span></span>  
  
     <span data-ttu-id="824bf-124">**Database**</span><span class="sxs-lookup"><span data-stu-id="824bf-124">**Database**</span></span>  
     <span data-ttu-id="824bf-125">이 뷰를 포함하는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-125">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="824bf-126">**Server**</span><span class="sxs-lookup"><span data-stu-id="824bf-126">**Server**</span></span>  
     <span data-ttu-id="824bf-127">현재 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-127">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="824bf-128">**사용자**</span><span class="sxs-lookup"><span data-stu-id="824bf-128">**User**</span></span>  
     <span data-ttu-id="824bf-129">이 연결을 사용하는 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-129">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="824bf-130">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="824bf-130">**Created date**</span></span>  
     <span data-ttu-id="824bf-131">뷰를 만든 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-131">Displays the date the view was created.</span></span>  
  
     <span data-ttu-id="824bf-132">**이름**</span><span class="sxs-lookup"><span data-stu-id="824bf-132">**Name**</span></span>  
     <span data-ttu-id="824bf-133">현재 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-133">The name of the current view.</span></span>  
  
     <span data-ttu-id="824bf-134">**스키마**</span><span class="sxs-lookup"><span data-stu-id="824bf-134">**Schema**</span></span>  
     <span data-ttu-id="824bf-135">뷰를 소유하는 스키마를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-135">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="824bf-136">**시스템 개체**</span><span class="sxs-lookup"><span data-stu-id="824bf-136">**System object**</span></span>  
     <span data-ttu-id="824bf-137">뷰가 시스템 개체인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-137">Indicates whether the view is a system object.</span></span> <span data-ttu-id="824bf-138">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-138">Values are True and False.</span></span>  
  
     <span data-ttu-id="824bf-139">**ANSI NULL**</span><span class="sxs-lookup"><span data-stu-id="824bf-139">**ANSI NULLs**</span></span>  
     <span data-ttu-id="824bf-140">개체가 ANSI NULL 옵션으로 생성되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-140">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="824bf-141">**암호화됨**</span><span class="sxs-lookup"><span data-stu-id="824bf-141">**Encrypted**</span></span>  
     <span data-ttu-id="824bf-142">뷰가 암호화되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-142">Indicates whether the view is encrypted.</span></span> <span data-ttu-id="824bf-143">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-143">Values are True and False.</span></span>  
  
     <span data-ttu-id="824bf-144">**따옴표 붙은 식별자**</span><span class="sxs-lookup"><span data-stu-id="824bf-144">**Quoted identifier**</span></span>  
     <span data-ttu-id="824bf-145">개체가 따옴표 붙은 식별자 옵션으로 생성되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-145">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="824bf-146">**스키마 바운드**</span><span class="sxs-lookup"><span data-stu-id="824bf-146">**Schema bound**</span></span>  
     <span data-ttu-id="824bf-147">뷰가 스키마 바운드 개체인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-147">Indicates whether the view is schema-bound.</span></span> <span data-ttu-id="824bf-148">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-148">Values are True and False.</span></span> <span data-ttu-id="824bf-149">스키마 바운드 뷰에 대한 자세한 내용은 [CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)의 SCHEMABINDING 부분을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824bf-149">For information about schema-bound views, see the SCHEMABINDING portion of [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
#### <a name="getting-view-properties-by-using-the-view-designer-tool"></a><span data-ttu-id="824bf-150">뷰 디자이너 도구를 사용하여 뷰 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="824bf-150">Getting view properties by using the View Designer tool</span></span>  
  
1.  <span data-ttu-id="824bf-151">**개체 탐색기**에서 속성을 볼 뷰가 포함된 데이터베이스를 확장한 다음 **뷰** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-151">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="824bf-152">속성을 볼 뷰를 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-152">Right-click the view of which you want to view the properties and select **Design**.</span></span>  
  
3.  <span data-ttu-id="824bf-153">다이어그램 창에서 빈 공간을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-153">Right-click in the blank space of the Diagram pane and click **Properties**.</span></span>  
  
     <span data-ttu-id="824bf-154">**속성** 창에 다음 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-154">The following properties show in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="824bf-155">**(이름)**</span><span class="sxs-lookup"><span data-stu-id="824bf-155">**(Name)**</span></span>  
     <span data-ttu-id="824bf-156">현재 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-156">The name of the current view.</span></span>  
  
     <span data-ttu-id="824bf-157">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="824bf-157">**Database Name**</span></span>  
     <span data-ttu-id="824bf-158">이 뷰를 포함하는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-158">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="824bf-159">**설명**</span><span class="sxs-lookup"><span data-stu-id="824bf-159">**Description**</span></span>  
     <span data-ttu-id="824bf-160">현재 뷰에 대한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-160">A brief description of the current view.</span></span>  
  
     <span data-ttu-id="824bf-161">**스키마**</span><span class="sxs-lookup"><span data-stu-id="824bf-161">**Schema**</span></span>  
     <span data-ttu-id="824bf-162">뷰를 소유하는 스키마를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-162">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="824bf-163">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="824bf-163">**Server Name**</span></span>  
     <span data-ttu-id="824bf-164">현재 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-164">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="824bf-165">**스키마에 바인딩**</span><span class="sxs-lookup"><span data-stu-id="824bf-165">**Bind to Schema**</span></span>  
     <span data-ttu-id="824bf-166">사용자가 이 뷰에 영향을 미치는 기본 개체를 수정하여 뷰 정의가 무효화되는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-166">Prevents users from modifying the underlying objects that contribute to this view in any way that would invalidate the view definition.</span></span>  
  
     <span data-ttu-id="824bf-167">**결정적**</span><span class="sxs-lookup"><span data-stu-id="824bf-167">**Deterministic**</span></span>  
     <span data-ttu-id="824bf-168">선택한 열의 데이터 형식을 확실하게 결정할 수 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-168">Shows whether the data type of the selected column can be determined with certainty</span></span>  
  
     <span data-ttu-id="824bf-169">**고유 값**</span><span class="sxs-lookup"><span data-stu-id="824bf-169">**Distinct Values**</span></span>  
     <span data-ttu-id="824bf-170">뷰에서 중복 항목을 필터링하도록 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-170">Specifies that the query will filter out duplicates in the view.</span></span> <span data-ttu-id="824bf-171">이 옵션은 테이블에 있는 열 중 일부만 사용하고 이 열에 중복 값이 포함될 수 있는 경우 또는 둘 이상의 테이블을 조인하는 과정에서 결과 집합에 중복 행이 만들어지는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-171">This option is useful when you are using only some of the columns from a table and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="824bf-172">이 옵션을 선택하면 SQL 창에서 키워드 DISTINCT를 문에 삽입하는 것과 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-172">Choosing this option is equivalent to inserting the keyword DISTINCT into the statement in the SQL pane.</span></span>  
  
     <span data-ttu-id="824bf-173">**GROUP BY 확장**</span><span class="sxs-lookup"><span data-stu-id="824bf-173">**GROUP BY Extension**</span></span>  
     <span data-ttu-id="824bf-174">집계 쿼리를 기반으로 하는 뷰에 대한 추가 옵션을 사용할 수 있음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-174">Specifies that additional options for views based on aggregate queries are available.</span></span>  
  
     <span data-ttu-id="824bf-175">**모든 열 출력**</span><span class="sxs-lookup"><span data-stu-id="824bf-175">**Output All Columns**</span></span>  
     <span data-ttu-id="824bf-176">선택한 뷰에서 모든 열이 반환되는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-176">Shows whether all columns are returned by the selected view.</span></span> <span data-ttu-id="824bf-177">이 옵션은 뷰가 만들어질 때 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-177">This is set at the time the view is created.</span></span>  
  
     <span data-ttu-id="824bf-178">**SQL 주석**</span><span class="sxs-lookup"><span data-stu-id="824bf-178">**SQL Comment**</span></span>  
     <span data-ttu-id="824bf-179">SQL 문에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-179">Shows a description of the SQL statements.</span></span> <span data-ttu-id="824bf-180">전체 설명을 보거나 편집하려면 설명을 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-180">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="824bf-181">뷰의 사용자나 사용 시기 등과 같은 정보를 주석에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-181">Your comments might include information such as who uses the view and when they use it.</span></span>  
  
     <span data-ttu-id="824bf-182">**Top 사양**</span><span class="sxs-lookup"><span data-stu-id="824bf-182">**Top Specification**</span></span>  
     <span data-ttu-id="824bf-183">확장하면 **상위**, **식**, **백분율**및 **동률** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-183">Expands to show properties for the **Top**, **Expression**, **Percent**, and **With Ties** properties.</span></span>  
  
     <span data-ttu-id="824bf-184">**(Top)**</span><span class="sxs-lookup"><span data-stu-id="824bf-184">**(Top)**</span></span>  
     <span data-ttu-id="824bf-185">결과 집합에 처음 n개 행 또는 처음 n%에 해당하는 행만 반환하는 TOP 절이 뷰에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-185">Specifies that the view will include a TOP clause, which returns only the first n rows or first n percentage of rows in the result set.</span></span> <span data-ttu-id="824bf-186">기본값은 뷰가 결과 집합에서 처음 10개 행을 반환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-186">The default is that the view returns the first 10 rows in the result set.</span></span> <span data-ttu-id="824bf-187">이 옵션은 반환할 행 수를 변경하거나 백분율을 다르게 지정하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-187">Use this to change the number of rows to return or to specify a different percentage</span></span>  
  
     <span data-ttu-id="824bf-188">**식**</span><span class="sxs-lookup"><span data-stu-id="824bf-188">**Expression**</span></span>  
     <span data-ttu-id="824bf-189">뷰가 반환할 백분율( **백분율** 이 **예**로 설정된 경우) 또는 레코드( **백분율** 이 **아니요**로 설정된 경우)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-189">Shows what percent (if **Percent** is set to **Yes**) or records (if **Percent** is set to **No**) that the view will return.</span></span>  
  
     <span data-ttu-id="824bf-190">**백분율**</span><span class="sxs-lookup"><span data-stu-id="824bf-190">**Percent**</span></span>  
     <span data-ttu-id="824bf-191">결과 집합에서 처음 n%에 해당하는 행만 반환하는 **TOP** 절이 쿼리에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-191">Specifies that the query will include a **TOP** clause, returning only the first n percentage of rows in the result set</span></span>  
  
     <span data-ttu-id="824bf-192">**With Ties**</span><span class="sxs-lookup"><span data-stu-id="824bf-192">**With Ties**</span></span>  
     <span data-ttu-id="824bf-193">뷰에 **WITH TIES** 절이 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-193">Specifies that the view will include a **WITH TIES** clause.</span></span> <span data-ttu-id="824bf-194">**WITH TIES** 는 백분율을 기반으로 하는 **TOP** 절 및 **ORDER BY** 절이 뷰에 포함되어 있을 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-194">**WITH TIES** is useful if a view includes an **ORDER BY** clause and a **TOP** clause based on percentage.</span></span> <span data-ttu-id="824bf-195">이 옵션을 설정하는 경우 백분율이 나뉘는 위치가 **ORDER BY** 절에서 동일한 값을 가진 행 집합의 중간에 놓이는 경우 동일한 값을 가진 행을 모두 포함할 수 있도록 뷰가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-195">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the **ORDER BY** clause, the view is extended to include all such rows.</span></span>  
  
     <span data-ttu-id="824bf-196">**업데이트 사양**</span><span class="sxs-lookup"><span data-stu-id="824bf-196">**Update Specification**</span></span>  
     <span data-ttu-id="824bf-197">**뷰 규칙 사용 업데이트** 및 **CHECK 옵션** 속성을 표시하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-197">Expands to show properties for the **Update Using View Rules** and **Check Option** properties.</span></span>  
  
     <span data-ttu-id="824bf-198">**(뷰 규칙 사용 업데이트)**</span><span class="sxs-lookup"><span data-stu-id="824bf-198">**(Update Using View Rules)**</span></span>  
     <span data-ttu-id="824bf-199">뷰에 대한 모든 업데이트 및 삽입이 MDAC(Microsoft Data Access Components)에 의해 뷰의 기본 테이블을 직접 참조하는 SQL 문이 아니라 뷰를 참조하는 SQL 문으로 변환됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-199">Indicates that all updates and insertions to the view will be translated by Microsoft Data Access Components (MDAC) into SQL statements that refer to the view, rather than into SQL statements that refer directly to the view's base tables.</span></span>  
  
     <span data-ttu-id="824bf-200">경우에 따라 MDAC는 뷰 업데이트 및 뷰 삽입 작업을 뷰의 기본 테이블에 대한 업데이트 및 삽입으로 매니페스트합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-200">In some cases, MDAC manifests view update and view insert operations as updates and inserts against the view's underlying base tables.</span></span> <span data-ttu-id="824bf-201">**뷰 규칙 사용 업데이트**를 선택하면 MDAC가 뷰 자체에 대한 업데이트 및 삽입 작업을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-201">By selecting **Update Using View Rules**, you can ensure that MDAC generates update and insert operations against the view itself.</span></span>  
  
     <span data-ttu-id="824bf-202">**CHECK 옵션**</span><span class="sxs-lookup"><span data-stu-id="824bf-202">**Check Option**</span></span>  
     <span data-ttu-id="824bf-203">이 뷰를 열고 **결과** 창을 수정하는 경우 추가되거나 수정된 데이터가 뷰 정의의 **WHERE** 절을 충족하는지 데이터 원본에서 확인하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-203">Indicates that when you open this view and modify the **Results** pane, the data source checks whether the added or modified data satisfies the **WHERE** clause of the view definition.</span></span> <span data-ttu-id="824bf-204">수정 내용이 **WHERE** 절을 충족하지 않는 경우 자세한 정보와 함께 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-204">If your modification do not satisfy the **WHERE** clause, you will see an error with more information.</span></span>  
  
#### <a name="to-get-dependencies-on-the-view"></a><span data-ttu-id="824bf-205">뷰의 종속성을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="824bf-205">To get dependencies on the view</span></span>  
  
1.  <span data-ttu-id="824bf-206">**개체 탐색기**에서 속성을 볼 뷰가 포함된 데이터베이스를 확장한 다음 **뷰** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-206">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="824bf-207">속성을 볼 뷰를 마우스 오른쪽 단추로 클릭하고 **종속성 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-207">Right-click the view of which you want to view the properties and select **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="824bf-208">**[뷰 이름]에 종속된 개체** 를 선택하여 뷰를 참조하는 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-208">Select **Objects that depend on [view name]** to display the objects that refer to the view.</span></span>  
  
4.  <span data-ttu-id="824bf-209">**[뷰 이름]이(가) 종속된 개체** 를 선택하여 뷰가 참조하는 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-209">Select **Objects on which [view name] depends** to display the objects that are referenced by the view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="824bf-210">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="824bf-210">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-view"></a><span data-ttu-id="824bf-211">뷰의 정의 및 속성을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="824bf-211">To get the definition and properties of a view</span></span>  
  
1.  <span data-ttu-id="824bf-212">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-212">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="824bf-213">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-213">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="824bf-214">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-214">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition, uses_ansi_nulls, uses_quoted_identifier, is_schema_bound  
    FROM sys.sql_modules  
    WHERE object_id = OBJECT_ID('HumanResources.vEmployee');   
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID('HumanResources.vEmployee')) AS ObjectDefinition;   
    GO  
    ```  
  
    ```  
    EXEC sp_helptext 'HumanResources.vEmployee';  
    ```  
  
 <span data-ttu-id="824bf-215">자세한 내용은 [sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql), [OBJECT_DEFINITION&#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) 및 [sp_helptext&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824bf-215">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql), [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) and [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-view"></a><span data-ttu-id="824bf-216">뷰의 종속성을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="824bf-216">To get the dependencies of a view</span></span>  
  
1.  <span data-ttu-id="824bf-217">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-217">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="824bf-218">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-218">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="824bf-219">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824bf-219">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
    GO  
    ```  
  
 <span data-ttu-id="824bf-220">자세한 내용은 [sys.sql_expression_dependencies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 및 [sys.objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824bf-220">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
