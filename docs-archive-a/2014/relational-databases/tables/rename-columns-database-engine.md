---
title: 열 이름 바꾸기(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6871ab82eaa17aa5e392e6b2bb3f5c60058f9af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653757"
---
# <a name="rename-columns-database-engine"></a><span data-ttu-id="2bf0a-102">열 이름 바꾸기(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="2bf0a-102">Rename Columns (Database Engine)</span></span>
  <span data-ttu-id="2bf0a-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블 열의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-103">You can rename a table column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2bf0a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2bf0a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2bf0a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2bf0a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2bf0a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2bf0a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2bf0a-107">보안</span><span class="sxs-lookup"><span data-stu-id="2bf0a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2bf0a-108">**다음을 사용하여 열 이름을 바꿉니다.**</span><span class="sxs-lookup"><span data-stu-id="2bf0a-108">**To rename columns, using:**</span></span>  
  
     [<span data-ttu-id="2bf0a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2bf0a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2bf0a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2bf0a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2bf0a-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2bf0a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2bf0a-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2bf0a-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2bf0a-113">열 이름을 변경해도 해당 열에 대한 참조 이름은 자동으로 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-113">Renaming a column will not automatically rename references to that column.</span></span> <span data-ttu-id="2bf0a-114">이름을 변경한 열을 참조하는 개체는 수동으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-114">You must modify any objects that reference the renamed column manually.</span></span> <span data-ttu-id="2bf0a-115">예를 들어 테이블 열의 이름을 변경하고 이 열이 트리거에서 참조되는 경우 트리거를 수정하여 새로운 열 이름을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-115">For example, if you rename a table column and that column is referenced in a trigger, you must modify the trigger to reflect the new column name.</span></span> <span data-ttu-id="2bf0a-116">[sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 를 사용하여 이 개체에 종속된 개체를 나열한 다음 개체의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-116">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the object before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2bf0a-117">보안</span><span class="sxs-lookup"><span data-stu-id="2bf0a-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2bf0a-118">권한</span><span class="sxs-lookup"><span data-stu-id="2bf0a-118">Permissions</span></span>  
 <span data-ttu-id="2bf0a-119">개체에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-119">Requires ALTER permission on the object.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2bf0a-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2bf0a-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-column-using-object-explorer"></a><span data-ttu-id="2bf0a-121">개체 탐색기를 사용하여 열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="2bf0a-121">To rename a column using Object Explorer</span></span>  
  
1.  <span data-ttu-id="2bf0a-122">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bf0a-123">**개체 탐색기**에서 열 이름을 바꾸려는 테이블을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-123">In **Object Explorer**, right-click the table in which you want to rename columns and choose **Rename**.</span></span>  
  
3.  <span data-ttu-id="2bf0a-124">새 열 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-124">Type a new column name.</span></span>  
  
#### <a name="to-rename-a-column-using-table-designer"></a><span data-ttu-id="2bf0a-125">테이블 디자이너를 사용하여 열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="2bf0a-125">To rename a column using Table Designer</span></span>  
  
1.  <span data-ttu-id="2bf0a-126">**개체 탐색기**에서 열 이름을 바꾸려는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-126">In **Object Explorer**, right-click the table to which you want to rename columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="2bf0a-127">**열 이름**아래에서 변경하려는 이름을 선택하고 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-127">Under **Column Name**, select the name you want to change and type a new one.</span></span>  
  
3.  <span data-ttu-id="2bf0a-128">**파일** 메뉴에서 ‘테이블 이름’ **저장**을 클릭합니다.__</span><span class="sxs-lookup"><span data-stu-id="2bf0a-128">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2bf0a-129">**열 속성** 탭에서 열 이름을 변경할 수도 있습니다. 이름을 변경하려는 열을 선택하고 **이름**에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-129">You can also change the name of a column in the **Column Properties** tab. Select the column whose name you want to change and type a new value for **Name**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2bf0a-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="2bf0a-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="2bf0a-131">**열 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="2bf0a-131">**To rename a column**</span></span>  
  
#### <a name="to-rename-a-column"></a><span data-ttu-id="2bf0a-132">열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="2bf0a-132">To rename a column</span></span>  
  
1.  <span data-ttu-id="2bf0a-133">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bf0a-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2bf0a-135">다음 예에서는 `TerritoryID` 테이블의 `Sales.SalesTerritory` 열 이름을 `TerrID`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-135">The following example renames the column `TerritoryID` in the table `Sales.SalesTerritory` to `TerrID`.</span></span> <span data-ttu-id="2bf0a-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 <span data-ttu-id="2bf0a-137">자세한 내용은 [sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2bf0a-137">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
