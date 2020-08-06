---
title: 전체 텍스트 인덱스 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 92eb3669930407b359b8eeed4d3df2e802bdacdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661285"
---
# <a name="manage-full-text-indexes"></a><span data-ttu-id="8c6e7-102">전체 텍스트 인덱스 관리</span><span class="sxs-lookup"><span data-stu-id="8c6e7-102">Manage Full-Text Indexes</span></span>
     
##  <a name="viewing-and-changing-the-properties-of-a-full-text-index"></a><a name="view"></a><span data-ttu-id="8c6e7-103">전체 텍스트 인덱스의 속성 보기 및 변경</span><span class="sxs-lookup"><span data-stu-id="8c6e7-103">Viewing and Changing the Properties of a Full-Text Index</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a><span data-ttu-id="8c6e7-104">Management Studio에서 전체 텍스트 인덱스의 속성을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8c6e7-104">To view or change the properties of a full-text index in Management Studio</span></span>  
  
1.  <span data-ttu-id="8c6e7-105">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-105">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="8c6e7-106">**데이터베이스**를 확장한 다음 전체 텍스트 인덱스가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-106">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="8c6e7-107">**테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-107">Expand **Tables**.</span></span>  
  
4.  <span data-ttu-id="8c6e7-108">전체 텍스트 인덱스가 정의된 테이블을 마우스 오른쪽 단추로 클릭하고 **전체 텍스트 인덱스**를 선택한 다음 **전체 텍스트 인덱스** 상황에 맞는 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-108">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="8c6e7-109">그러면 **전체 텍스트 인덱스 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-109">This opens the **Full-text index Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="8c6e7-110">**페이지 선택** 창에서 다음 페이지 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-110">In the **Select a page** pane, you can select any of the following pages:</span></span>  
  
    |<span data-ttu-id="8c6e7-111">호출</span><span class="sxs-lookup"><span data-stu-id="8c6e7-111">Page</span></span>|<span data-ttu-id="8c6e7-112">Description</span><span class="sxs-lookup"><span data-stu-id="8c6e7-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="8c6e7-113">**일반**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-113">**General**</span></span>|<span data-ttu-id="8c6e7-114">전체 텍스트 인덱스의 기본 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-114">Displays basic properties of the full-text index.</span></span> <span data-ttu-id="8c6e7-115">이러한 속성으로는 데이터베이스 이름, 테이블 이름 및 전체 텍스트 키 열의 이름과 같이 변경할 수 없는 많은 속성과 여러 가지 수정 가능한 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-115">These include several modifiable properties and a number of unchangeable properties such as database name, table name, and the name of full-text key column.</span></span> <span data-ttu-id="8c6e7-116">수정 가능한 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-116">The modifiable properties are:</span></span><br /><br /> <span data-ttu-id="8c6e7-117">**전체 텍스트 인덱스 중지 목록**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-117">**Full-Text Index Stoplist**</span></span><br /><br /> <span data-ttu-id="8c6e7-118">**전체 텍스트 인덱싱 설정**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-118">**Full-Text Indexing Enabled**</span></span><br /><br /> <span data-ttu-id="8c6e7-119">**변경 내용 추적**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-119">**Change Tracking**</span></span><br /><br /> <span data-ttu-id="8c6e7-120">**검색 속성 목록**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-120">**Search Property List**</span></span><br /><br /> <br /><br /> <span data-ttu-id="8c6e7-121">자세한 내용은 [전체 텍스트 인덱스 속성&#40;일반 페이지&#41;](full-text-index-properties-general-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-121">For more information, see [Full-Text Index Properties &#40;General Page&#41;](full-text-index-properties-general-page.md).</span></span>|  
    |<span data-ttu-id="8c6e7-122">**열**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-122">**Columns**</span></span>|<span data-ttu-id="8c6e7-123">전체 텍스트 인덱싱에 사용할 수 있는 테이블 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-123">Displays the table columns that are available for full-text indexing.</span></span> <span data-ttu-id="8c6e7-124">열을 선택하면 선택한 열이 전체 텍스트 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-124">The selected column or columns are full-text indexed.</span></span> <span data-ttu-id="8c6e7-125">이때 전체 텍스트 인덱스에 포함하려는 만큼 사용 가능한 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-125">You can select as many of the available columns as you want to include in the full-text index.</span></span> <span data-ttu-id="8c6e7-126">자세한 내용은 [전체 텍스트 인덱스 속성&#40;열 페이지&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-126">For more information, see [Full-Text Index Properties &#40;Columns Page&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).</span></span>|  
    |<span data-ttu-id="8c6e7-127">**일정**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-127">**Schedules**</span></span>|<span data-ttu-id="8c6e7-128">이 페이지를 사용하여 전체 텍스트 인덱스 채우기에 대한 증분 테이블 채우기를 시작하는 SQL Server 에이전트 작업의 일정을 만들거나 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-128">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population for the full-text index populations.</span></span> <span data-ttu-id="8c6e7-129">자세한 내용은 [전체 텍스트 인덱스 채우기](../relational-databases/indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-129">For more information, see [Populate Full-Text Indexes](../relational-databases/indexes/indexes.md).</span></span><br /><br /> <span data-ttu-id="8c6e7-130"><strong> \* \* 중요 \* 전체 \* </strong> **텍스트 인덱스 속성** 대화 상자를 종료 한 후 새로 만든 일정은 SQL Server 에이전트 작업과 연결 됩니다 ( *database_name*의 증분 테이블 채우기 시작).\* table_name\*).</span><span class="sxs-lookup"><span data-stu-id="8c6e7-130"><strong>\*\* Important \*\*</strong> After you exit the **Full-Text Index Properties** dialog box, any newly created schedule is associated with a SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*).</span></span>|  
  
6.  <span data-ttu-id="8c6e7-131">변경 내용을 저장하고 **전체 텍스트 인덱스 속성** 대화 상자를 닫으려면 [!INCLUDE[clickOK](../includes/clickok-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6e7-131">[!INCLUDE[clickOK](../includes/clickok-md.md)] to save any changes and exit the **Full-text index Properties** dialog box.</span></span>  
  
##  <a name="viewing-the-properties-of-indexed-tables-and-columns"></a><a name="props"></a><span data-ttu-id="8c6e7-132">인덱싱된 테이블 및 열 속성 보기</span><span class="sxs-lookup"><span data-stu-id="8c6e7-132">Viewing the Properties of Indexed Tables and Columns</span></span>  
 <span data-ttu-id="8c6e7-133">OBJECTPROPERTYEX와 같은 여러 가지 [!INCLUDE[tsql](../includes/tsql-md.md)] 함수를 사용하여 다양한 전체 텍스트 인덱싱 속성 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-133">Several [!INCLUDE[tsql](../includes/tsql-md.md)] functions such as OBJECTPROPERTYEX can be used to obtain the value of various full-text indexing properties.</span></span> <span data-ttu-id="8c6e7-134">이 정보는 전체 텍스트 검색을 관리하고 이러한 검색에서 발생하는 문제를 해결하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-134">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="8c6e7-135">다음 표에서는 인덱싱된 테이블 및 열과 관련한 전체 텍스트 속성과 관련 [!INCLUDE[tsql](../includes/tsql-md.md)] 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-135">The following table lists the full-text properties related to indexed tables and columns and their related [!INCLUDE[tsql](../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="8c6e7-136">속성</span><span class="sxs-lookup"><span data-stu-id="8c6e7-136">Property</span></span>|<span data-ttu-id="8c6e7-137">Description</span><span class="sxs-lookup"><span data-stu-id="8c6e7-137">Description</span></span>|<span data-ttu-id="8c6e7-138">함수</span><span class="sxs-lookup"><span data-stu-id="8c6e7-138">Function</span></span>|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|<span data-ttu-id="8c6e7-139">열의 문서 유형 정보를 보관하는 테이블의 TYPE COLUMN입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-139">TYPE COLUMN in the table that holds the document type information of the column.</span></span>|[<span data-ttu-id="8c6e7-140">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="8c6e7-140">COLUMNPROPERTY</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|<span data-ttu-id="8c6e7-141">열에 대한 전체 텍스트 인덱싱 설정 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-141">Whether a column has been enabled for full-text indexing.</span></span>|<span data-ttu-id="8c6e7-142">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="8c6e7-142">COLUMNPROPERTY</span></span>|  
|`IsFulltextKey`|<span data-ttu-id="8c6e7-143">인덱스가 테이블에 대한 전체 텍스트 키인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-143">Whether the index is the full-text key for a table.</span></span>|[<span data-ttu-id="8c6e7-144">INDEXPROPERTY</span><span class="sxs-lookup"><span data-stu-id="8c6e7-144">INDEXPROPERTY</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|  
|<span data-ttu-id="8c6e7-145">**TableFulltextBackgroundUpdateIndexOn**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-145">**TableFulltextBackgroundUpdateIndexOn**</span></span>|<span data-ttu-id="8c6e7-146">테이블에 대한 전체 텍스트 백그라운드 업데이트 인덱싱 설정 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-146">Whether a table has full-text background update indexing.</span></span>|[<span data-ttu-id="8c6e7-147">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-147">OBJECTPROPERTYEX</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|<span data-ttu-id="8c6e7-148">테이블에 대한 전체 텍스트 인덱스 데이터가 상주하는 전체 텍스트 카탈로그 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-148">Full-text catalog ID in which the full-text index data for the table resides.</span></span>|<span data-ttu-id="8c6e7-149">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-149">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextChangeTrackingOn`|<span data-ttu-id="8c6e7-150">테이블에 전체 텍스트 변경 내용 추적이 설정되어 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-150">Whether a table has full-text change-tracking enabled.</span></span>|<span data-ttu-id="8c6e7-151">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-151">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextDocsProcessed`|<span data-ttu-id="8c6e7-152">전체 텍스트 인덱싱이 시작된 이후에 처리된 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-152">Number of rows processed since the start of full-text indexing.</span></span>|<span data-ttu-id="8c6e7-153">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-153">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="8c6e7-154">**TableFulltextFailCount**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-154">**TableFulltextFailCount**</span></span>|<span data-ttu-id="8c6e7-155">전체 텍스트 검색이 인덱싱하지 않은 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-155">Number of rows Full-Text Search did not index.</span></span>|<span data-ttu-id="8c6e7-156">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-156">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="8c6e7-157">**TableFulltextItemCount**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-157">**TableFulltextItemCount**</span></span>|<span data-ttu-id="8c6e7-158">성공적으로 전체 텍스트 인덱싱된 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-158">Number of rows that were successfully full-text indexed.</span></span>|<span data-ttu-id="8c6e7-159">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-159">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextKeyColumn`|<span data-ttu-id="8c6e7-160">전체 텍스트 고유 키 열의 열 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-160">The column ID of the full-text unique key column.</span></span>|<span data-ttu-id="8c6e7-161">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-161">OBJECTPROPERTYEX</span></span>|  
|`TableFullTextMergeStatus`|<span data-ttu-id="8c6e7-162">전체 텍스트 인덱스가 있는 테이블이 현재 병합 중인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-162">Whether a table that has a full-text index is currently in merging.</span></span>|<span data-ttu-id="8c6e7-163">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-163">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="8c6e7-164">**TableFulltextPendingChanges**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-164">**TableFulltextPendingChanges**</span></span>|<span data-ttu-id="8c6e7-165">처리할 보류 중인 변경 내용 추적 항목의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-165">Number of pending change tracking entries to process.</span></span>|<span data-ttu-id="8c6e7-166">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-166">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextPopulateStatus`|<span data-ttu-id="8c6e7-167">전체 텍스트 테이블의 채우기 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-167">Population status of a full-text table.</span></span>|<span data-ttu-id="8c6e7-168">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-168">OBJECTPROPERTYEX</span></span>|  
|`TableHasActiveFulltextIndex`|<span data-ttu-id="8c6e7-169">테이블에 활성화된 전체 텍스트 인덱스가 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-169">Whether a table has an active full-text index.</span></span>|<span data-ttu-id="8c6e7-170">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="8c6e7-170">OBJECTPROPERTYEX</span></span>|  
  
##  <a name="getting-information-about-the-full-text-key-column"></a><a name="key"></a><span data-ttu-id="8c6e7-171">전체 텍스트 키 열에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="8c6e7-171">Getting Information about the Full-Text Key Column</span></span>  
 <span data-ttu-id="8c6e7-172">일반적으로 CONTAINSTABLE 또는 FREETEXTTABLE 행 집합 반환 함수의 결과는 기본 테이블과 조인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-172">Typically, the result of CONTAINSTABLE or FREETEXTTABLE rowset-valued functions need to be joined with the base table.</span></span> <span data-ttu-id="8c6e7-173">이러한 경우 고유 키 열 이름을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-173">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="8c6e7-174">그러면 지정된 고유 인덱스가 전체 텍스트 키로 사용되는지 여부를 확인하고 전체 텍스트 키 열의 식별자를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-174">You can inquire whether a given unique index is used as the full-text key, and you can obtain the identifier of the full-text key column.</span></span>  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a><span data-ttu-id="8c6e7-175">지정된 고유 인덱스가 전체 텍스트 키 열로 사용되는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="8c6e7-175">To inquire whether a given unique index is used as the full-text key column</span></span>  
  
1.  <span data-ttu-id="8c6e7-176">[SELECT](/sql/t-sql/queries/select-transact-sql) 문을 사용하여 [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-176">Use a [SELECT](/sql/t-sql/queries/select-transact-sql) statement to call the [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) function.</span></span> <span data-ttu-id="8c6e7-177">함수 호출에서 OBJECT_ID 함수를 사용 하 여 테이블 이름 (*table_name*)을 테이블 ID로 변환 하 고, 테이블에 대 한 고유 인덱스의 이름을 지정 하 고, 다음과 `IsFulltextKey` 같이 인덱스 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-177">In the function call use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID, specify the name of a unique index for the table, and specify the `IsFulltextKey` index property, as follows:</span></span>  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     <span data-ttu-id="8c6e7-178">이 문은 전체 텍스트 키 열의 고유성을 강제 적용하기 위해 인덱스가 사용되면 1을 반환하고, 그렇지 않으면 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-178">This statement returns 1 if the index is used to enforce uniqueness of the full-text key column and 0 if it is not.</span></span>  
  
 <span data-ttu-id="8c6e7-179">**예제**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-179">**Example**</span></span>  
  
 <span data-ttu-id="8c6e7-180">다음 예에서는 `PK_Document_DocumentID` 인덱스가 전체 텍스트 키 열의 고유성을 강제 적용하는 데 사용되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-180">The following example inquires whether the `PK_Document_DocumentID` index is used to enforce the uniqueness of the full-text key column, as follows:</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 <span data-ttu-id="8c6e7-181">이 예에서는 전체 텍스트 키 열의 고유성을 강제 적용하기 위해 `PK_Document_DocumentID` 인덱스가 사용되면 1을 반환하고,</span><span class="sxs-lookup"><span data-stu-id="8c6e7-181">This example returns 1 if the `PK_Document_DocumentID` index is used to enforce uniqueness of the full-text key column.</span></span> <span data-ttu-id="8c6e7-182">그렇지 않으면 0 또는 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-182">Otherwise, it returns 0 or NULL.</span></span> <span data-ttu-id="8c6e7-183">NULL은 잘못된 인덱스 이름이 사용 중이거나, 인덱스 이름이 테이블과 일치하지 않거나, 테이블이 존재하지 않음 등을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-183">NULL implies you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a><span data-ttu-id="8c6e7-184">전체 텍스트 키 열의 식별자를 찾으려면</span><span class="sxs-lookup"><span data-stu-id="8c6e7-184">To find the identifier of the full-text key column</span></span>  
  
1.  <span data-ttu-id="8c6e7-185">전체 텍스트를 사용하도록 설정된 테이블에는 해당 테이블에 고유 행을 강제 적용하는 데 사용되는 열(*고유\*\*키 열*)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-185">Each full-text enabled table has a column that is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="8c6e7-186">OBJECTPROPERTYEX 함수에서 얻을 수 있는 `TableFulltextKeyColumn` 속성에는 고유 키 열의 열 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-186">The `TableFulltextKeyColumn` property, obtained from the OBJECTPROPERTYEX function, contains the column ID of the unique key column.</span></span>  
  
     <span data-ttu-id="8c6e7-187">이 식별자를 가져오려면 SELECT 문을 사용하여 OBJECTPROPERTYEX 함수를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-187">To obtain this identifier, you can use a SELECT statement to call the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="8c6e7-188">OBJECT_ID 함수를 사용 하 여 테이블 이름 (*table_name*)을 테이블 ID로 변환 하 고 다음과 `TableFulltextKeyColumn` 같이 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-188">Use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID and specify the `TableFulltextKeyColumn` property, as follows:</span></span>  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 <span data-ttu-id="8c6e7-189">**예**</span><span class="sxs-lookup"><span data-stu-id="8c6e7-189">**Examples**</span></span>  
  
 <span data-ttu-id="8c6e7-190">다음 예에서는 전체 텍스트 키 열의 식별자나 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-190">The following example returns the identifier of the full-text key column or NULL.</span></span> <span data-ttu-id="8c6e7-191">NULL은 잘못된 인덱스 이름이 사용 중이거나, 인덱스 이름이 테이블과 일치하지 않거나, 테이블이 존재하지 않음 등을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-191">NULL implies that you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 <span data-ttu-id="8c6e7-192">다음 예에서는 고유 키 열의 식별자를 사용하여 열의 이름을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-192">The following example shows how to use the identifier of the unique key column to obtain the name of the column.</span></span>  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 <span data-ttu-id="8c6e7-193">이 예에서는 Document 테이블의 고유 키 열 이름인 DocumentID가 포함된 단일 행을 표시하는 `Unique Key Column`라는 결과 집합 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-193">This example returns a result set column named `Unique Key Column`, which displays a single row containing the name of the unique key column of the Document table, DocumentID.</span></span> <span data-ttu-id="8c6e7-194">이 쿼리에 잘못된 인덱스 이름이 포함되어 있거나, 인덱스 이름이 테이블과 일치하지 않거나, 테이블이 존재하지 않는 경우에는 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-194">Note that if this query contained an invalid index name, the index name did not correspond to the table, the table did not exist, and so forth, it would return NULL.</span></span>  
  
##  <a name="disabling-or-re-enabling-a-table-for-full-text-indexing"></a><a name="disable"></a><span data-ttu-id="8c6e7-195">테이블에서 전체 텍스트 인덱싱을 사용 하지 않도록 설정 또는 다시 설정</span><span class="sxs-lookup"><span data-stu-id="8c6e7-195">Disabling or Re-enabling a Table for Full-Text Indexing</span></span>  
 <span data-ttu-id="8c6e7-196">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 사용자가 만든 모든 데이터베이스에서 기본적으로 전체 텍스트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-196">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all user-created databases are full-text enabled by default.</span></span> <span data-ttu-id="8c6e7-197">또한 개별 테이블에 전체 텍스트 인덱스를 만들고 이 인덱스에 열을 추가하는 즉시 자동으로 개별 테이블에서 전체 텍스트 인덱싱을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-197">Additionally, an individual table is automatically enabled for full-text indexing as soon as a full-text index is created on it and a column is added to the index.</span></span> <span data-ttu-id="8c6e7-198">해당 전체 텍스트 인덱스에서 마지막 열을 삭제하면 자동으로 테이블에서 전체 텍스트 인덱싱을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-198">A table is automatically disabled for full-text indexing when the last column is dropped from its full-text index.</span></span>  
  
 <span data-ttu-id="8c6e7-199">전체 텍스트 인덱스가 있는 테이블에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 테이블에서의 전체 텍스트 인덱싱을 수동으로 해제하거나 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-199">On a table that has a full-text index, you can manually disable or re-enable a table for full-text indexing using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a><span data-ttu-id="8c6e7-200">테이블에 전체 텍스트 인덱싱을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="8c6e7-200">To enable a table for full-text indexing</span></span>  
  
1.  <span data-ttu-id="8c6e7-201">서버 그룹, **데이터베이스**를 차례로 확장한 다음 전체 텍스트 인덱싱을 설정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-201">Expand the server group, expand **Databases**, and expand the database that contains the table you want to enable for full-text indexing.</span></span>  
  
2.  <span data-ttu-id="8c6e7-202">**테이블**을 확장하고 전체 텍스트 인덱싱을 해제하거나 다시 설정할 테이블을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-202">Expand **Tables**, and right-click the table that you want to disable or re-enable for full-text indexing.</span></span>  
  
3.  <span data-ttu-id="8c6e7-203">**전체 텍스트 인덱스**를 선택한 다음 **전체 텍스트 인덱스 사용 안 함** 또는 **전체 텍스트 인덱스 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-203">Select **Full-Text index**, and then click **Disable Full-Text index** or **Enable Full-Text index**.</span></span>  
  
##  <a name="removing-a-full-text-index-from-a-table"></a><a name="remove"></a><span data-ttu-id="8c6e7-204">테이블에서 전체 텍스트 인덱스 제거</span><span class="sxs-lookup"><span data-stu-id="8c6e7-204">Removing a Full-Text Index from a Table</span></span>  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a><span data-ttu-id="8c6e7-205">테이블에서 전체 텍스트 인덱스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="8c6e7-205">To remove a full-text index from a table</span></span>  
  
1.  <span data-ttu-id="8c6e7-206">개체 탐색기에서 삭제할 전체 텍스트 인덱스가 포함된 테이블을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-206">In Object Explorer, right-click the table that has the full-text index that you want to delete.</span></span>  
  
2.  <span data-ttu-id="8c6e7-207">**전체 텍스트 인덱스 삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-207">Select **Delete Full-Text index**.</span></span>  
  
3.  <span data-ttu-id="8c6e7-208">전체 텍스트 인덱스를 삭제할 것인지 확인하는 메시지가 표시되면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c6e7-208">When prompted, click **OK** to confirm that you want to delete the full-text index.</span></span>  
  
  
