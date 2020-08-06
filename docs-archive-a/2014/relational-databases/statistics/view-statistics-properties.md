---
title: 통계 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.details.f1
helpviewer_keywords:
- viewing statistics properties
- statistics [SQL Server], viewing properties
ms.assetid: 0eaa2101-006e-4015-9979-3468b50e0aaa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63cabc5d8844982604993acac6a791317ee36925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659871"
---
# <a name="view-statistics-properties"></a><span data-ttu-id="6c284-102">통계 속성 보기</span><span class="sxs-lookup"><span data-stu-id="6c284-102">View Statistics Properties</span></span>
  <span data-ttu-id="6c284-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블 또는 인덱싱된 뷰에 대한 현재 쿼리 최적화 통계를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-103">You can display current query optimization statistics for a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6c284-104">통계 개체에는 통계에 대한 메타데이터가 있는 헤더, 통계 개체의 첫 번째 키 열에 있는 값의 분포에 대한 히스토그램, 그리고 열 간 상관 관계를 측정하는 밀도 벡터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-104">Statistics objects include a header with metadata about the statistics, a histogram with the distribution of values in the first key column of the statistics object, and a density vector to measure cross-column correlation.</span></span> <span data-ttu-id="6c284-105">히스토그램 및 밀도 벡터에 대한 자세한 내용은 [DBCC SHOW_STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c284-105">For more information about histograms and density vectors, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span></span>  
  
 <span data-ttu-id="6c284-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6c284-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6c284-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6c284-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6c284-108">보안</span><span class="sxs-lookup"><span data-stu-id="6c284-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6c284-109">**다음을 사용하여 통계 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="6c284-109">**To view statistics properties, using:**</span></span>  
  
     [<span data-ttu-id="6c284-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c284-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6c284-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c284-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c284-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6c284-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c284-113">보안</span><span class="sxs-lookup"><span data-stu-id="6c284-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c284-114">권한</span><span class="sxs-lookup"><span data-stu-id="6c284-114">Permissions</span></span>  
 <span data-ttu-id="6c284-115">통계 개체를 보려면 테이블의 소유자이거나 `sysadmin` 고정 서버 역할, `db_owner` 고정 데이터베이스 역할 또는 `db_ddladmin` 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-115">In order to view the statistics object, the user must own the table or the user must be a member of the `sysadmin` fixed server role, the `db_owner` fixed database role, or the `db_ddladmin` fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6c284-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6c284-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="6c284-117">통계 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="6c284-117">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="6c284-118">**개체 탐색기**에서 더하기 기호를 클릭하여 새 통계를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-118">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="6c284-119">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="6c284-120">더하기 기호를 클릭하여 통계 속성을 보려는 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-120">Click the plus sign to expand the table in which you want to view the statistic's properties.</span></span>  
  
4.  <span data-ttu-id="6c284-121">더하기 기호를 클릭하여 **통계** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="6c284-122">속성을 보려는 통계 개체를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-122">Right-click the Statistics object of which you want to view the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="6c284-123">**통계 속성 -** _statistics_name_ 대화 상자의 **페이지 선택** 창에서 **자세히**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-123">In the **Statistics Properties -** _statistics_name_ dialog box, in the **Select a page** pane, select **Details**.</span></span>  
  
     <span data-ttu-id="6c284-124">**통계 속성 -** _statistics_name_ 대화 상자의 **자세히** 페이지에 다음 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-124">The following properties show on the **Details** page in the **Statistics Properties -** _statistics_name_ dialog box.</span></span>  
  
     <span data-ttu-id="6c284-125">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="6c284-125">**Table Name**</span></span>  
     <span data-ttu-id="6c284-126">통계에서 설명하는 테이블 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-126">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="6c284-127">**통계 이름**</span><span class="sxs-lookup"><span data-stu-id="6c284-127">**Statistics Name**</span></span>  
     <span data-ttu-id="6c284-128">통계가 저장되는 데이터베이스 개체 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-128">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="6c284-129">**인덱스 statistics_name에 대한 통계**</span><span class="sxs-lookup"><span data-stu-id="6c284-129">**Statistics for INDEXstatistics_name**</span></span>  
     <span data-ttu-id="6c284-130">이 텍스트 상자에는 통계 개체에서 반환되는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-130">This text box shows the properties returned from the statistics object.</span></span> <span data-ttu-id="6c284-131">이 속성은 통계 헤더, 밀도 벡터 및 히스토그램의 세 가지 섹션으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-131">This properties are divided into three sections: Stats Header, Density Vector, and Histogram.</span></span>  
  
     <span data-ttu-id="6c284-132">다음 정보는 통계 헤더의 결과 집합에 반환되는 열에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-132">The following information describes the columns returned in the result set for the Stats Header.</span></span>  
  
     <span data-ttu-id="6c284-133">**이름**</span><span class="sxs-lookup"><span data-stu-id="6c284-133">**Name**</span></span>  
     <span data-ttu-id="6c284-134">통계 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-134">Name of the statistics object.</span></span>  
  
     <span data-ttu-id="6c284-135">**업데이트됨**</span><span class="sxs-lookup"><span data-stu-id="6c284-135">**Updated**</span></span>  
     <span data-ttu-id="6c284-136">통계가 마지막으로 업데이트된 날짜와 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-136">Date and time the statistics were last updated.</span></span>  
  
     <span data-ttu-id="6c284-137">**행**</span><span class="sxs-lookup"><span data-stu-id="6c284-137">**Rows**</span></span>  
     <span data-ttu-id="6c284-138">통계가 마지막으로 업데이트되었을 때 테이블 또는 인덱싱된 뷰의 전체 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-138">Total number of rows in the table or indexed view when the statistics were last updated.</span></span> <span data-ttu-id="6c284-139">통계가 필터링되거나 필터링된 인덱스에 해당하는 경우 행 수가 테이블의 행 수보다 적을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-139">If the statistics are filtered or correspond to a filtered index, the number of rows might be less than the number of rows in the table.</span></span>  
  
     <span data-ttu-id="6c284-140">**샘플링한 행**</span><span class="sxs-lookup"><span data-stu-id="6c284-140">**Rows Sampled**</span></span>  
     <span data-ttu-id="6c284-141">통계 계산을 위해 샘플링된 전체 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-141">Total number of rows sampled for statistics calculations.</span></span> <span data-ttu-id="6c284-142">샘플링된 행 수가 전체 행 수보다 적은 경우 표시되는 히스토그램과 밀도 결과는 샘플링된 행을 기준으로 하는 예상치입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-142">If Rows Sampled < Rows, the displayed histogram and density results are estimates based on the sampled rows.</span></span>  
  
     <span data-ttu-id="6c284-143">**단계**</span><span class="sxs-lookup"><span data-stu-id="6c284-143">**Steps**</span></span>  
     <span data-ttu-id="6c284-144">히스토그램의 총 단계 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-144">Number of steps in the histogram.</span></span> <span data-ttu-id="6c284-145">각 단계의 범위는 열 값에서 상한 열 값까지입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-145">Each step spans a range of column values followed by an upper bound column value.</span></span> <span data-ttu-id="6c284-146">히스토그램 단계는 통계의 첫 번째 키 열에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-146">The histogram steps are defined on the first key column in the statistics.</span></span> <span data-ttu-id="6c284-147">최대 단계 수는 200개입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-147">The maximum number of steps is 200.</span></span>  
  
     <span data-ttu-id="6c284-148">**밀도**</span><span class="sxs-lookup"><span data-stu-id="6c284-148">**Density**</span></span>  
     <span data-ttu-id="6c284-149">히스토그램 경계 값을 제외하고 통계 개체의 첫 번째 키 열에 있는 모든 값에 대해 1/ *고유 값* 으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-149">Calculated as 1 / *distinct values* for all values in the first key column of the statistics object, excluding the histogram boundary values.</span></span> <span data-ttu-id="6c284-150">이 밀도 값은 쿼리 최적화 프로그램에서 사용되지 않으며 SQL Server 2008 이전 버전과의 호환성을 위해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-150">This Density value is not used by the query optimizer and is displayed for backward compatibility with versions before SQL Server 2008.</span></span>  
  
     <span data-ttu-id="6c284-151">**평균 키 길이**</span><span class="sxs-lookup"><span data-stu-id="6c284-151">**Average Key Length**</span></span>  
     <span data-ttu-id="6c284-152">통계 개체의 키 열에 있는 모든 값에 대한 값당 평균 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-152">Average number of bytes per value for all of the key columns in the statistics object.</span></span>  
  
     <span data-ttu-id="6c284-153">**문자열 인덱스**</span><span class="sxs-lookup"><span data-stu-id="6c284-153">**String Index**</span></span>  
     <span data-ttu-id="6c284-154">'예'는 통계 개체에 LIKE 연산자를 사용하는 쿼리 조건자(예: `WHERE ProductName LIKE '%Bike'`)의 카디널리티 예상치 정확도를 높이기 위한 문자열 요약 통계가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-154">Yes indicates the statistics object contains string summary statistics to improve the cardinality estimates for query predicates that use the LIKE operator; for example, `WHERE ProductName LIKE '%Bike'`.</span></span> <span data-ttu-id="6c284-155">문자열 요약 통계는 히스토그램과는 별도로 저장되며 통계 개체에서 **char**, **varchar**, **nchar**, **nvarchar**, **varchar(max)** , **nvarchar(max)** , **text**또는 **ntext**형식인 첫 번째 키 열에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-155">String summary statistics are stored separately from the histogram and are created on the first key column of the statistics object when it is of type **char**, **varchar**, **nchar**, **nvarchar**, **varchar(max)**, **nvarchar(max)**, **text**, or **ntext**.</span></span>  
  
     <span data-ttu-id="6c284-156">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="6c284-156">**Filter Expression**</span></span>  
     <span data-ttu-id="6c284-157">통계 개체에 포함된 테이블 행의 하위 집합에 대한 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-157">Predicate for the subset of table rows included in the statistics object.</span></span> <span data-ttu-id="6c284-158">NULL = 필터링되지 않은 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-158">NULL = non-filtered statistics.</span></span>  
  
     <span data-ttu-id="6c284-159">**필터링되지 않은 행**</span><span class="sxs-lookup"><span data-stu-id="6c284-159">**Unfiltered Rows**</span></span>  
     <span data-ttu-id="6c284-160">필터 식을 적용하기 전 테이블에 있는 전체 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-160">Total number of rows in the table before applying the filter expression.</span></span> <span data-ttu-id="6c284-161">필터 식이 NULL이면 필터링되지 않은 행과 행이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-161">If Filter Expression is NULL, Unfiltered Rows is equal to Rows.</span></span>  
  
     <span data-ttu-id="6c284-162">다음 정보는 밀도 벡터의 결과 집합에 반환되는 열에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-162">The following information describes the columns returned in the result set for the Density Vector.</span></span>  
  
     <span data-ttu-id="6c284-163">**모든 밀도**</span><span class="sxs-lookup"><span data-stu-id="6c284-163">**All Density**</span></span>  
     <span data-ttu-id="6c284-164">밀도는 1/ *고유 값*입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-164">Density is 1 / *distinct values*.</span></span> <span data-ttu-id="6c284-165">결과에는 통계 개체에 있는 각 열 접두사의 밀도가 한 행씩 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-165">Results display density for each prefix of columns in the statistics object, one row per density.</span></span> <span data-ttu-id="6c284-166">고유 값은 행별 및 열 접두사별 열 값의 고유한 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-166">A distinct value is a distinct list of the column values per row and per columns prefix.</span></span> <span data-ttu-id="6c284-167">예를 들어 통계 개체가 키 열 (A, B, C)를 포함하는 경우 결과에서 밀도는 이러한 각 열 접두사의 고유 값 목록인 (A), (A,B) 및 (A, B, C)로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-167">For example, if the statistics object contains key columns (A, B, C), the results report the density of the distinct lists of values in each of these column prefixes: (A), (A,B), and (A, B, C).</span></span> <span data-ttu-id="6c284-168">접두사 (A, B, C)를 사용하면 이러한 각 목록은 다음과 같은 고유 값 목록입니다. (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7).</span><span class="sxs-lookup"><span data-stu-id="6c284-168">Using the prefix (A, B, C), each of these lists is a distinct value list: (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7).</span></span> <span data-ttu-id="6c284-169">접두사 (A, B)를 사용하면 동일한 열 값은 고유 값 목록 (3, 5), (4, 4) 및 (4, 5)입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-169">Using the prefix (A, B) the same column values have these distinct value lists: (3, 5), (4, 4), and (4, 5).</span></span>  
  
     <span data-ttu-id="6c284-170">**평균 길이**</span><span class="sxs-lookup"><span data-stu-id="6c284-170">**Average Length**</span></span>  
     <span data-ttu-id="6c284-171">열 접두사의 열 값 목록을 저장하기 위한 평균 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-171">Average length, in bytes, to store a list of the column values for the column prefix.</span></span> <span data-ttu-id="6c284-172">예를 들어 목록 (3, 5, 6)의 각 값에 4바이트가 필요한 경우 길이는 12바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-172">For example, if the values in the list (3, 5, 6) each require 4 bytes the length is 12 bytes.</span></span>  
  
     <span data-ttu-id="6c284-173">**열**</span><span class="sxs-lookup"><span data-stu-id="6c284-173">**Columns**</span></span>  
     <span data-ttu-id="6c284-174">모든 밀도 및 평균 길이가 표시되는 접두사의 열 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-174">Names of columns in the prefix for which All density and Average length are displayed.</span></span>  
  
     <span data-ttu-id="6c284-175">다음 정보는 히스토그램의 결과 집합에 반환되는 열에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-175">The following information describes the columns returned in the result set for the Histogram.</span></span>  
  
     <span data-ttu-id="6c284-176">**RANGE_HI_KEY**</span><span class="sxs-lookup"><span data-stu-id="6c284-176">**RANGE_HI_KEY**</span></span>  
     <span data-ttu-id="6c284-177">히스토그램 단계의 상한 열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-177">Upper bound column value for a histogram step.</span></span> <span data-ttu-id="6c284-178">열 값은 키 값이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-178">The column value is also called a key value.</span></span>  
  
     <span data-ttu-id="6c284-179">**RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="6c284-179">**RANGE_ROWS**</span></span>  
     <span data-ttu-id="6c284-180">상한을 제외한 히스토그램 단계 내에 열 값이 있는 예상 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-180">Estimated number of rows whose column value falls within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="6c284-181">**EQ_ROWS**</span><span class="sxs-lookup"><span data-stu-id="6c284-181">**EQ_ROWS**</span></span>  
     <span data-ttu-id="6c284-182">히스토그램 단계에서 상한과 열 값이 동일한 예상 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-182">Estimated number of rows whose column value equals the upper bound of the histogram step.</span></span>  
  
     <span data-ttu-id="6c284-183">**DISTINCT_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="6c284-183">**DISTINCT_RANGE_ROWS**</span></span>  
     <span data-ttu-id="6c284-184">상한을 제외한 히스토그램 단계 내에 고유한 열 값이 있는 예상 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-184">Estimated number of rows with a distinct column value within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="6c284-185">**AVG_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="6c284-185">**AVG_RANGE_ROWS**</span></span>  
     <span data-ttu-id="6c284-186">상한을 제외한 히스토그램 단계 내에 중복 열 값이 있는 평균 행 수입니다(DISTINCT_RANGE_ROWS > 0인 경우 RANGE_ROWS/DISTINCT_RANGE_ROWS).</span><span class="sxs-lookup"><span data-stu-id="6c284-186">Average number of rows with duplicate column values within a histogram step, excluding the upper bound (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0).</span></span>  
  
7.  <span data-ttu-id="6c284-187">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-187">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6c284-188">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6c284-188">Using Transact-SQL</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="6c284-189">통계 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="6c284-189">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="6c284-190">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-190">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c284-191">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-191">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c284-192">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-192">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example displays all statistics information for the AK_Address_rowguid index of the Person.Address table.   
    DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);   
    GO  
    ```  
  
 <span data-ttu-id="6c284-193">자세한 내용은 [DBCC SHOW_STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c284-193">For more information, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).</span></span>  
  
#### <a name="to-find-all-of-the-statistics-on-a-table-or-view"></a><span data-ttu-id="6c284-194">테이블 또는 뷰에서 모든 통계를 찾으려면</span><span class="sxs-lookup"><span data-stu-id="6c284-194">To find all of the statistics on a table or view</span></span>  
  
1.  <span data-ttu-id="6c284-195">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-195">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c284-196">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-196">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c284-197">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c284-197">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Gets the following information: name and ID of the statistics, whether the statistics were created automatically or by the user, whether the statistics were created with the NORECOMPUTE option, and whether the statistics have a filter and, if so, what that filter is.  
    */  
    SELECT name AS statistics_name  
        ,stats_id  
        ,auto_created  
        ,user_created  
        ,no_recompute  
        ,has_filter  
        ,filter_definition  
    -- using the sys.stats catalog view  
    FROM sys.stats  
    -- for the Sales.SpecialOffer table  
    WHERE object_id = OBJECT_ID('Sales.SpecialOffer');  
    GO  
    ```  
  
 <span data-ttu-id="6c284-198">자세한 내용은 [sys.stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c284-198">For more information, see [sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql).</span></span>  
  
  
