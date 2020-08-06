---
title: 테이블의 종속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f54b913124cdaa8a7dfeebac01ba070cc37d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661590"
---
# <a name="view-the-dependencies-of-a-table"></a><span data-ttu-id="c9a3c-102">테이블의 종속성 보기</span><span class="sxs-lookup"><span data-stu-id="c9a3c-102">View the Dependencies of a Table</span></span>
  <span data-ttu-id="c9a3c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을(를) 사용하여 테이블 종속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-103">You can view a table's dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c9a3c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c9a3c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c9a3c-106">보안</span><span class="sxs-lookup"><span data-stu-id="c9a3c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c9a3c-107">**테이블의 종속성을 보려면 다음을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-107">**To view a table's dependencies, using:**</span></span>  
  
     [<span data-ttu-id="c9a3c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c9a3c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c9a3c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c9a3c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c9a3c-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c9a3c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c9a3c-111">보안</span><span class="sxs-lookup"><span data-stu-id="c9a3c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c9a3c-112">권한</span><span class="sxs-lookup"><span data-stu-id="c9a3c-112">Permissions</span></span>  
 <span data-ttu-id="c9a3c-113">데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 sys.sql_expression_dependencies에 대한 SELECT 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-113">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="c9a3c-114">기본적으로 SELECT 권한은 db_owner 고정 데이터베이스 역할의 멤버에게만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-114">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="c9a3c-115">SELECT와 VIEW DEFINITION 권한을 다른 사용자에게 부여하면 피부여자는 데이터베이스의 모든 종속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-115">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c9a3c-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c9a3c-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-table"></a><span data-ttu-id="c9a3c-117">테이블의 종속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="c9a3c-117">To view the dependencies of a table</span></span>  
  
1.  <span data-ttu-id="c9a3c-118">**개체 탐색기**에서 **데이터베이스**를 확장하고, 특정 데이터베이스를 확장한 후 **테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-118">In **Object Explorer**, expand **Databases**, expand a database, and then expand **Tables**.</span></span>  
  
2.  <span data-ttu-id="c9a3c-119">테이블을 마우스 오른쪽 단추로 클릭한 다음 **종속성 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-119">Right-click a table, and then click **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="c9a3c-120">**개체 종속성** _\<object name>_ 대화 상자에서 **에 종속된 개체** _\<object name>_ 또는 _\<object name>_ **이(가) 종속된** **개체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-120">In the **Object Dependencies**_\<object name>_ dialog box, select either **Objects that depend on** _\<object name>_, or **Objects on which**_\<object name>_**depends**.</span></span>  
  
4.  <span data-ttu-id="c9a3c-121">**종속성** 표에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-121">Select an object in the **Dependencies** grid.</span></span> <span data-ttu-id="c9a3c-122">개체 유형(예: "트리거" 또는 "저장 프로시저")이 **유형** 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-122">The type of object (such as "Trigger" or "Stored Procedure"), appears in the **Type** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c9a3c-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c9a3c-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a><span data-ttu-id="c9a3c-124">테이블에 종속된 개체를 보려면</span><span class="sxs-lookup"><span data-stu-id="c9a3c-124">To view the objects that depend on a table</span></span>  
  
1.  <span data-ttu-id="c9a3c-125">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c9a3c-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c9a3c-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a><span data-ttu-id="c9a3c-128">테이블이 종속된 개체를 보려면</span><span class="sxs-lookup"><span data-stu-id="c9a3c-128">To view the objects on which a table depends</span></span>  
  
1.  <span data-ttu-id="c9a3c-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c9a3c-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c9a3c-131">다음 예에서는 `Production.Product`테이블에 종속된 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-131">The following example returns the objects that depend on the table `Production.Product`.</span></span> <span data-ttu-id="c9a3c-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 <span data-ttu-id="c9a3c-133">자세한 내용은 [sys.sql_expression_dependencies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-133">For additional information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span></span>  
  
  
