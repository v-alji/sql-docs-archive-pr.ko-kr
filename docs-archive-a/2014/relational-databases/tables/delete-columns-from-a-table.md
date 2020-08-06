---
title: 테이블에서 열 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 62f9bca8ee53ae97bb1ac7f37e597b7814a0c370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652029"
---
# <a name="delete-columns-from-a-table"></a><span data-ttu-id="b2b07-102">테이블에서 열 삭제</span><span class="sxs-lookup"><span data-stu-id="b2b07-102">Delete Columns from a Table</span></span>
  <span data-ttu-id="b2b07-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블 열을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-103">This topic describes how to delete table columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b2b07-104">테이블에서 열을 삭제하면 여기에 포함된 모든 데이터가 데이터베이스에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-104">When you delete a column from a table, it and all the data it contains are deleted from the database.</span></span> <span data-ttu-id="b2b07-105">이 작업은 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-105">This action cannot be undone.</span></span>  
  
 <span data-ttu-id="b2b07-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b2b07-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b2b07-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b2b07-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b2b07-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b2b07-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b2b07-109">보안</span><span class="sxs-lookup"><span data-stu-id="b2b07-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b2b07-110">**테이블에서 열을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="b2b07-110">**To delete a column from a table, using:**</span></span>  
  
     [<span data-ttu-id="b2b07-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2b07-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b2b07-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2b07-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b2b07-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b2b07-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b2b07-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b2b07-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b2b07-115">CHECK 제약 조건이 있는 열은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-115">You cannot delete a column that has a CHECK constraint.</span></span> <span data-ttu-id="b2b07-116">먼저 제약 조건을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-116">You must first delete the constraint.</span></span>  
  
 <span data-ttu-id="b2b07-117">테이블 디자이너를 사용할 때를 제외하고는 PRIMARY KEY 또는 FOREIGN KEY 제약 조건이나 기타 종속성이 있는 열을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-117">You cannot delete a column that has PRIMARY KEY or FOREIGN KEY constraints or other dependencies except when using the Table Designer.</span></span> <span data-ttu-id="b2b07-118">개체 탐색기 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용할 때는 먼저 열에서 모든 종속성을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-118">When using Object Explorer or [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first remove all dependencies on the column.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b2b07-119">보안</span><span class="sxs-lookup"><span data-stu-id="b2b07-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b2b07-120">권한</span><span class="sxs-lookup"><span data-stu-id="b2b07-120">Permissions</span></span>  
 <span data-ttu-id="b2b07-121">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b2b07-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b2b07-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a><span data-ttu-id="b2b07-123">개체 탐색기를 사용하여 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b2b07-123">To delete columns by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="b2b07-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b07-125">**개체 탐색기**에서 열을 삭제하려는 테이블을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-125">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Delete**.</span></span>  
  
3.  <span data-ttu-id="b2b07-126">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-126">In **Delete Object** dialog box, click **OK**.</span></span>  
  
 <span data-ttu-id="b2b07-127">열에 제약 조건 또는 기타 종속성이 포함된 경우 **개체 삭제** 대화 상자에 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-127">If the column contains constraints or other dependencies, an error message will display in the **Delete Object** dialog box.</span></span> <span data-ttu-id="b2b07-128">참조된 제약 조건을 삭제하여 오류를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-128">Resolve the error by deleting the referenced constraints.</span></span>  
  
#### <a name="to-delete-columns-by-using-table-designer"></a><span data-ttu-id="b2b07-129">테이블 디자이너를 사용하여 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b2b07-129">To delete columns by using Table Designer</span></span>  
  
1.  <span data-ttu-id="b2b07-130">**개체 탐색기**에서 열을 삭제하려는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-130">In **Object Explorer**, right-click the table from which you want to delete columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="b2b07-131">삭제하려는 열을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **열 삭제** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-131">Right-click the column you want to delete and choose **Delete Column** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="b2b07-132">관계에 참여하는 열(FOREIGN KEY 또는 PRIMARY KEY)인 경우에는 선택한 열과 해당 관계의 삭제를 확인하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-132">If the column participates in a relationship (FOREIGN KEY or PRIMARY KEY), a message prompts you to confirm the deletion of the selected columns and their relationships.</span></span> <span data-ttu-id="b2b07-133">**예**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-133">Choose **Yes**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b2b07-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b2b07-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-columns"></a><span data-ttu-id="b2b07-135">열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b2b07-135">To delete columns</span></span>  
  
1.  <span data-ttu-id="b2b07-136">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b07-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b07-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 <span data-ttu-id="b2b07-139">열에 제약 조건 또는 기타 종속성이 포함된 경우 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-139">If the column contains constraints or other dependencies, an error message will be returned.</span></span> <span data-ttu-id="b2b07-140">참조된 제약 조건을 삭제하여 오류를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b07-140">Resolve the error by deleting the referenced constraints.</span></span>  
  
 <span data-ttu-id="b2b07-141">추가 예제를 보려면 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2b07-141">For additional examples, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
##  <a name="FollowUp"></a>  
