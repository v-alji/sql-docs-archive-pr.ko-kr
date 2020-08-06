---
title: 인덱스 옵션 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9f2d7f0bbbf0d152d3f510ae9ddbe3168634ef96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739963"
---
# <a name="set-index-options"></a><span data-ttu-id="629b3-102">인덱스 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="629b3-102">Set Index Options</span></span>
  <span data-ttu-id="629b3-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱스 속성을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-103">This topic describes how to modify the properties of an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="629b3-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="629b3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="629b3-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="629b3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="629b3-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="629b3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="629b3-107">보안</span><span class="sxs-lookup"><span data-stu-id="629b3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="629b3-108">**인덱스 속성을 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="629b3-108">**To modify the properties of an index, using:**</span></span>  
  
     [<span data-ttu-id="629b3-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="629b3-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="629b3-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="629b3-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="629b3-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="629b3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="629b3-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="629b3-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="629b3-113">ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY 및 STATISTICS_NORECOMPUTE 옵션은 ALTER INDEX 문에서 SET 절을 사용하면 즉시 인덱스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-113">The following options are immediately applied to the index by using the SET clause in the ALTER INDEX statement: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY, and STATISTICS_NORECOMPUTE.</span></span>  
  
-   <span data-ttu-id="629b3-114">PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP 및 DROP_EXISTING(CREATE INDEX의 경우에만) 옵션은 ALTER INDEX REBUILD 또는 CREATE INDEX WITH DROP_EXISTING 중 하나를 사용하여 인덱스를 다시 작성할 때 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-114">The following options can be set when you rebuild an index by using either ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP, and DROP_EXISTING (CREATE INDEX only).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="629b3-115">보안</span><span class="sxs-lookup"><span data-stu-id="629b3-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="629b3-116">권한</span><span class="sxs-lookup"><span data-stu-id="629b3-116">Permissions</span></span>  
 <span data-ttu-id="629b3-117">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-117">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="629b3-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="629b3-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a><span data-ttu-id="629b3-119">테이블 디자이너에서 인덱스 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="629b3-119">To modify the properties of an index in Table Designer</span></span>  
  
1.  <span data-ttu-id="629b3-120">개체 탐색기에서 더하기 기호를 클릭하여 인덱스 속성을 수정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-120">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="629b3-121">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-121">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="629b3-122">인덱스 속성을 수정할 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-122">Right-click the table on which you want to modify an index's properties and select **Design**.</span></span>  
  
4.  <span data-ttu-id="629b3-123">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-123">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="629b3-124">수정할 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-124">Select the index that you want to modify.</span></span> <span data-ttu-id="629b3-125">주 표에 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-125">Its properties will show up in the main grid.</span></span>  
  
6.  <span data-ttu-id="629b3-126">속성의 설정을 변경하여 인덱스를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-126">Change the settings of any and all properties to customize the index.</span></span>  
  
7.  <span data-ttu-id="629b3-127">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-127">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="629b3-128">**파일** 메뉴에서 _table_name_**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-128">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a><span data-ttu-id="629b3-129">개체 탐색기에서 인덱스 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="629b3-129">To modify the properties of an index in Object Explorer</span></span>  
  
1.  <span data-ttu-id="629b3-130">개체 탐색기에서 더하기 기호를 클릭하여 인덱스 속성을 수정할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-130">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="629b3-131">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-131">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="629b3-132">더하기 기호를 클릭하여 인덱스 속성을 수정할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-132">Click the plus sign to expand the table on which you want to modify an index's properties.</span></span>  
  
4.  <span data-ttu-id="629b3-133">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-133">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="629b3-134">속성을 수정할 인덱스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-134">Right-click the index of which you want to modify the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="629b3-135">**페이지 선택**아래에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-135">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="629b3-136">속성의 설정을 변경하여 인덱스를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-136">Change the settings of any and all properties to customize the index.</span></span>  
  
8.  <span data-ttu-id="629b3-137">인덱스 열을 추가 또는 제거하거나 그 위치를 변경하려면 **인덱스 속성 -** _index_name_ 대화 상자의 **일반** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-137">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties -** _index_name_ dialog box.</span></span> <span data-ttu-id="629b3-138">자세한 내용은 [Index Properties F1 Help](index-properties-f1-help.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="629b3-138">For more information, see [Index Properties F1 Help](index-properties-f1-help.md)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="629b3-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="629b3-139">Using Transact-SQL</span></span>  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a><span data-ttu-id="629b3-140">테이블에 있는 모든 인덱스의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="629b3-140">To see the properties of all the indexes in a table</span></span>  
  
1.  <span data-ttu-id="629b3-141">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="629b3-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="629b3-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a><span data-ttu-id="629b3-144">인덱스의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="629b3-144">To set the properties of an index</span></span>  
  
1.  <span data-ttu-id="629b3-145">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="629b3-146">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="629b3-147">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="629b3-147">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="629b3-148">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="629b3-148">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
