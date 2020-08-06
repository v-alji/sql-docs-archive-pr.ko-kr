---
title: 인덱스 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739969"
---
# <a name="modify-an-index"></a><span data-ttu-id="de5a6-102">인덱스 수정</span><span class="sxs-lookup"><span data-stu-id="de5a6-102">Modify an Index</span></span>
  <span data-ttu-id="de5a6-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 인덱스를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-103">This topic describes how to modify an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de5a6-104">PRIMARY KEY 또는 UNIQUE 제약 조건의 결과로 생성된 인덱스는 이 방법으로 수정할 수 없으며</span><span class="sxs-lookup"><span data-stu-id="de5a6-104">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be modified by using this method.</span></span> <span data-ttu-id="de5a6-105">대신 제약 조건을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-105">Instead, the constraint must be modified.</span></span>  
  
 <span data-ttu-id="de5a6-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="de5a6-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="de5a6-107">**인덱스를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="de5a6-107">**To modify an index, using:**</span></span>  
  
     [<span data-ttu-id="de5a6-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="de5a6-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="de5a6-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="de5a6-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="de5a6-110">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="de5a6-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="de5a6-111">인덱스를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="de5a6-111">To modify an index</span></span>  
  
1.  <span data-ttu-id="de5a6-112">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-112">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="de5a6-113">**데이터베이스**를 확장하고 해당 테이블이 속한 데이터베이스를 확장한 다음 **테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-113">Expand **Databases**, expand the database in which the table belongs, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="de5a6-114">인덱스가 속한 테이블을 확장하고 **인덱스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-114">Expand the table in which the index belongs and then expand **Indexes**.</span></span>  
  
4.  <span data-ttu-id="de5a6-115">수정할 인덱스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-115">Right-click the index that you want to modify and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="de5a6-116">**인덱스 속성** 대화 상자에서 원하는 대로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-116">In the **Index Properties** dialog box, make the desired changes.</span></span> <span data-ttu-id="de5a6-117">예를 들어 인덱스 키에서 열을 추가 또는 제거하거나 인덱스 옵션의 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-117">For example, you can add or remove a column from the index key, or change the setting of an index option.</span></span>  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="de5a6-118">인덱스 열을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="de5a6-118">To modify index columns</span></span>  
  
1.  <span data-ttu-id="de5a6-119">인덱스 열을 추가 또는 제거하거나 그 위치를 변경하려면 **인덱스 속성** 대화 상자에서 **일반** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-119">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="de5a6-120">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="de5a6-120">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="de5a6-121">인덱스를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="de5a6-121">To modify an index</span></span>  
  
1.  <span data-ttu-id="de5a6-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="de5a6-123">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="de5a6-124">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="de5a6-125">이 예에서는 `ProductID` 옵션을 사용하여 `Production.WorkOrder` 테이블의 `DROP_EXISTING` 열에서 기존 인덱스를 삭제하고 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-125">This example drops and re-creates an existing index on the `ProductID` column of the `Production.WorkOrder` table by using the `DROP_EXISTING` option.</span></span> <span data-ttu-id="de5a6-126">`FILLFACTOR` 및 `PAD_INDEX` 옵션도 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-126">The options `FILLFACTOR` and `PAD_INDEX` are also set.</span></span>  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     <span data-ttu-id="de5a6-127">다음 예에서는 ALTER INDEX를 사용하여 `AK_SalesOrderHeader_SalesOrderNumber`인덱스에 몇 가지 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-127">The following example uses ALTER INDEX to set several options on the index `AK_SalesOrderHeader_SalesOrderNumber`.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="de5a6-128">인덱스 열을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="de5a6-128">To modify index columns</span></span>  
  
1.  <span data-ttu-id="de5a6-129">인덱스 열을 추가 또는 제거하거나 그 위치를 변경하려면 인덱스를 삭제하고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5a6-129">To add, remove, or change the position of an index column, you must drop and recreate the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5a6-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de5a6-130">See Also</span></span>  
 <span data-ttu-id="de5a6-131">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de5a6-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="de5a6-132">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de5a6-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="de5a6-133">[INDEXPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de5a6-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 <span data-ttu-id="de5a6-134">[sys.indexes&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de5a6-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span></span>  
 <span data-ttu-id="de5a6-135">[sys.index_columns&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de5a6-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span></span>  
 <span data-ttu-id="de5a6-136">[인덱스 옵션 설정](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="de5a6-136">[Set Index Options](set-index-options.md) </span></span>  
 [<span data-ttu-id="de5a6-137">인덱스 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="de5a6-137">Rename Indexes</span></span>](indexes.md)  
  
  
