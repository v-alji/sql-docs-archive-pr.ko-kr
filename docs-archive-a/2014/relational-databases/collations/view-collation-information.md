---
title: 데이터 정렬 정보 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995e559cfd7ca871f5abd90751f2f79167bdf76f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661156"
---
# <a name="view-collation-information"></a><span data-ttu-id="f2c21-102">데이터 정렬 정보 보기</span><span class="sxs-lookup"><span data-stu-id="f2c21-102">View Collation Information</span></span>
    
##  <a name="you-can-view-the-collation-of-a-server-database-or-column-in-ssmanstudiofull-using-object-explorer-menu-options-or-by-using-tsql"></a><a name="Top"></a> <span data-ttu-id="f2c21-103">개체 탐색기 메뉴 옵션을 사용하거나 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 서버, 데이터베이스 또는 열의 데이터 정렬을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-103">You can view the collation of a server, database, or column in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
##  <a name="how-to-view-a-collation-setting"></a><a name="Procedures"></a> <span data-ttu-id="f2c21-104">데이터 정렬 설정을 보는 방법</span><span class="sxs-lookup"><span data-stu-id="f2c21-104">How to View a Collation Setting</span></span>  
 <span data-ttu-id="f2c21-105">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-105">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="f2c21-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f2c21-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="f2c21-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f2c21-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f2c21-108">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f2c21-108">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f2c21-109">**개체 탐색기에서 서버(SQL Server의 인스턴스)에 대한 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-109">**To view a collation setting for a server (instance of SQL Server) in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f2c21-110">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-110">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f2c21-111">인스턴스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-111">Right-click the instance and select **Properties**.</span></span>  
  
 <span data-ttu-id="f2c21-112">**개체 탐색기에서 데이터베이스에 대한 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-112">**To view a collation setting for a database in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f2c21-113">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-113">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f2c21-114">**데이터베이스**를 확장하고 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-114">Expand **Databases**, right-click the database and select **Properties**.</span></span>  
  
 <span data-ttu-id="f2c21-115">**개체 탐색기에서 열에 대한 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-115">**To view a collation setting for a column in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="f2c21-116">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-116">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f2c21-117">**데이터베이스**를 확장하고 데이터베이스를 확장한 다음 **테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-117">Expand **Databases**, expand the database and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="f2c21-118">열이 포함된 테이블을 확장한 다음 **열**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-118">Expand the table that contains the column and then expand **Columns**.</span></span>  
  
4.  <span data-ttu-id="f2c21-119">열을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-119">Right-click the column and select **Properties**.</span></span> <span data-ttu-id="f2c21-120">데이터 정렬 속성이 비어 있는 경우 열은 문자 데이터 유형이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-120">If the collation property is empty, the column is not a character data type.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f2c21-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f2c21-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="f2c21-122">**서버의 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-122">**To view the collation setting of a server**</span></span>  
  
1.  <span data-ttu-id="f2c21-123">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결하고 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-123">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f2c21-124">쿼리 창에서 SERVERPROPERTY 시스템 함수를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-124">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  <span data-ttu-id="f2c21-125">또는 sp_helpsort 시스템 저장 프로시저를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-125">Alternatively, you can use the sp_helpsort system stored procedure.</span></span>  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 <span data-ttu-id="f2c21-126">**지원되는 모든 데이터 정렬을 보려면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="f2c21-126">**To view all collations supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**</span></span>  
  
1.  <span data-ttu-id="f2c21-127">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결하고 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-127">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f2c21-128">쿼리 창에서 SERVERPROPERTY 시스템 함수를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-128">In the query window, enter the following statement that uses the SERVERPROPERTY system function.</span></span>  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 <span data-ttu-id="f2c21-129">**데이터베이스의 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-129">**To view the collation setting of a database**</span></span>  
  
1.  <span data-ttu-id="f2c21-130">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결하고 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-130">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f2c21-131">쿼리 창에서 sys.databases 시스템 카탈로그 뷰를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-131">In the query window, enter the following statement that uses the sys.databases system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  <span data-ttu-id="f2c21-132">또는 DATABASEPROPERTYEX 시스템 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-132">Alternatively, you can use the DATABASEPROPERTYEX system function.</span></span>  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 <span data-ttu-id="f2c21-133">**열의 데이터 정렬 설정을 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2c21-133">**To view the collation setting of a column**</span></span>  
  
1.  <span data-ttu-id="f2c21-134">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결하고 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-134">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and on the toolbar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f2c21-135">쿼리 창에서 sys.columns 시스템 카탈로그 뷰를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c21-135">In the query window, enter the following statement that uses the sys.columns system catalog view.</span></span>  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f2c21-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2c21-136">See Also</span></span>  
 <span data-ttu-id="f2c21-137">[SERVERPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2c21-137">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="f2c21-138">[sys.fn_helpcollations&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2c21-138">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="f2c21-139">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2c21-139">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="f2c21-140">[sys.columns&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2c21-140">[sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) </span></span>  
 <span data-ttu-id="f2c21-141">[데이터 정렬 선행 규칙&#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2c21-141">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 [<span data-ttu-id="f2c21-142">sp_helpsort&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2c21-142">sp_helpsort &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
