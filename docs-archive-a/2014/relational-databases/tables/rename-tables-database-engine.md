---
title: 테이블 이름 바꾸기(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e73bbb92d8fd3fdcaa7756ce1dcb74d8cd598b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653754"
---
# <a name="rename-tables-database-engine"></a><span data-ttu-id="80c1b-102">테이블 이름 바꾸기(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="80c1b-102">Rename Tables (Database Engine)</span></span>
  <span data-ttu-id="80c1b-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-103">You can rename a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="80c1b-104">테이블 이름을 바꿀 때는 신중한 검토가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-104">Think carefully before you rename a table.</span></span> <span data-ttu-id="80c1b-105">기존의 쿼리, 뷰, 사용자 정의 함수, 저장 프로시저 또는 프로그램에서 해당 테이블을 참조하는 경우 이름 수정으로 인해 이러한 개체가 유효하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="80c1b-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="80c1b-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="80c1b-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="80c1b-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="80c1b-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="80c1b-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="80c1b-109">보안</span><span class="sxs-lookup"><span data-stu-id="80c1b-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="80c1b-110">**테이블 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="80c1b-110">**To rename a table, using:**</span></span>  
  
     [<span data-ttu-id="80c1b-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="80c1b-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="80c1b-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="80c1b-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="80c1b-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="80c1b-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="80c1b-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="80c1b-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="80c1b-115">테이블 이름을 변경해도 해당 테이블에 대한 참조 이름은 자동으로 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-115">Renaming a table will not automatically rename references to that table.</span></span> <span data-ttu-id="80c1b-116">이름을 바꾼 테이블을 참조하는 개체는 수동으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-116">You must manually modify any objects that reference the renamed table.</span></span> <span data-ttu-id="80c1b-117">예를 들어 테이블 이름을 바꿨고 해당 테이블이 트리거에서 참조되는 경우 트리거를 수정하여 새로운 테이블 이름을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-117">For example, if you rename a table and that table is referenced in a trigger, you must modify the trigger to reflect the new table name.</span></span> <span data-ttu-id="80c1b-118">테이블 이름을 바꾸기 전에 테이블에 대한 종속성을 나열하려면 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-118">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the table before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="80c1b-119">보안</span><span class="sxs-lookup"><span data-stu-id="80c1b-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="80c1b-120">권한</span><span class="sxs-lookup"><span data-stu-id="80c1b-120">Permissions</span></span>  
 <span data-ttu-id="80c1b-121">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="80c1b-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="80c1b-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="80c1b-123">테이블 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="80c1b-123">To rename a table</span></span>  
  
1.  <span data-ttu-id="80c1b-124">개체 탐색기에서 이름을 바꾸려는 테이블을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **디자인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-124">In Object Explorer, right-click the table you want to rename and choose **Design** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="80c1b-125">**보기** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-125">From the **View** menu, choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="80c1b-126">**속성** 창의 **이름** 값 필드에 테이블의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-126">In the field for the **Name** value in the **Properties** window, type a new name for the table.</span></span>  
  
4.  <span data-ttu-id="80c1b-127">이 동작을 취소하려면 이 필드를 나가기 전에 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-127">To cancel this action, press the ESC key before leaving this field.</span></span>  
  
5.  <span data-ttu-id="80c1b-128">**파일** 메뉴에서_테이블 이름_ **저장**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-128">From the **File** menu choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="80c1b-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="80c1b-129">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="80c1b-130">테이블 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="80c1b-130">To rename a table</span></span>  
  
1.  <span data-ttu-id="80c1b-131">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="80c1b-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="80c1b-133">다음 예에서는 `SalesTerritory` 스키마에 있는 `SalesTerr` 테이블의 이름을 `Sales` 로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-133">The following example renames the `SalesTerritory` table to `SalesTerr` in the `Sales` schema.</span></span> <span data-ttu-id="80c1b-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80c1b-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 <span data-ttu-id="80c1b-135">추가 예제를 보려면 [sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80c1b-135">For additional examples, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
