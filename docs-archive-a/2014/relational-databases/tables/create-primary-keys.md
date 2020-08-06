---
title: 기본 키 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
ms.openlocfilehash: c515ef8f978b41225ff45e87646b0aa7a9706a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661605"
---
# <a name="create-primary-keys"></a><span data-ttu-id="8d678-102">기본 키 만들기</span><span class="sxs-lookup"><span data-stu-id="8d678-102">Create Primary Keys</span></span>
  <span data-ttu-id="8d678-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 기본 키를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-103">You can define a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8d678-104">기본 키를 만들면 해당하는 고유 클러스터형 또는 비클러스터형 인덱스가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-104">Creating a primary key automatically creates a corresponding unique, clustered or nonclustered index.</span></span>  
  
 <span data-ttu-id="8d678-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8d678-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8d678-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8d678-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8d678-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8d678-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8d678-108">보안</span><span class="sxs-lookup"><span data-stu-id="8d678-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8d678-109">**기본 키를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="8d678-109">**To create a primary key, using:**</span></span>  
  
     [<span data-ttu-id="8d678-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8d678-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8d678-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8d678-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8d678-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8d678-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8d678-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8d678-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8d678-114">테이블은 하나의 PRIMARY KEY 제약 조건만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-114">A table can contain only one PRIMARY KEY constraint.</span></span>  
  
-   <span data-ttu-id="8d678-115">PRIMARY KEY 제약 조건 내에서 정의된 모든 열은 NOT NULL로 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-115">All columns defined within a PRIMARY KEY constraint must be defined as NOT NULL.</span></span> <span data-ttu-id="8d678-116">NULL 허용 여부를 지정하지 않은 경우에는 PRIMARY KEY 제약 조건에 참여하는 모든 열의 NULL 허용 여부가 NOT NULL로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-116">If nullability is not specified, all columns participating in a PRIMARY KEY constraint have their nullability set to NOT NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8d678-117">보안</span><span class="sxs-lookup"><span data-stu-id="8d678-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8d678-118">권한</span><span class="sxs-lookup"><span data-stu-id="8d678-118">Permissions</span></span>  
 <span data-ttu-id="8d678-119">기본 키가 포함된 새 테이블을 만들려면 데이터베이스에서 CREATE TABLE 권한이 필요하고 테이블을 만들려는 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-119">Creating a new table with a primary key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="8d678-120">기존 테이블에서 기본 키를 만들려면 해당 테이블에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-120">Creating a primary key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8d678-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8d678-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-primary-key"></a><span data-ttu-id="8d678-122">기본 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8d678-122">To create a primary key</span></span>  
  
1.  <span data-ttu-id="8d678-123">개체 탐색기에서 unique 제약 조건을 추가 하려는 테이블을 마우스 오른쪽 단추로 클릭 하 고 **디자인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-123">In Object Explorer, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="8d678-124">**테이블 디자이너**에서 기본 키로 정의하려는 데이터베이스 열의 행 선택기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-124">In **Table Designer**, click the row selector for the database column you want to define as the primary key.</span></span> <span data-ttu-id="8d678-125">여러 열을 선택하려면 Ctrl 키를 누른 상태로 다른 열의 행 선택기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-125">If you want to select multiple columns, hold down the CTRL key while you click the row selectors for the other columns.</span></span>  
  
3.  <span data-ttu-id="8d678-126">열의 행 선택기를 마우스 오른쪽 단추로 클릭하고 **기본 키 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-126">Right-click the row selector for the column and select **Set Primary Key**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8d678-127">기본 키를 다시 정의하려면 기존의 기본 키에 대한 관계를 모두 삭제한 다음 기본 키를 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-127">If you want to redefine the primary key, any relationships to the existing primary key must be deleted before the new primary key can be created.</span></span> <span data-ttu-id="8d678-128">이 과정에서 기존의 관계가 자동으로 삭제된다는 경고 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-128">A message will warn you that existing relationships will be automatically deleted as part of this process.</span></span>  
  
 <span data-ttu-id="8d678-129">기본 키 열을 구분하기 위해 해당 행 선택기에 기본 키 기호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-129">A primary key column is identified by a primary key symbol in its row selector.</span></span>  
  
 <span data-ttu-id="8d678-130">기본 키가 두 개 이상의 열로 구성되어 있는 경우 한 열에는 중복 값이 허용되지만 기본 키의 모든 열에 있는 값의 각 조합은 중복되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-130">If a primary key consists of more than one column, duplicate values are allowed in one column, but each combination of values from all the columns in the primary key must be unique.</span></span>  
  
 <span data-ttu-id="8d678-131">복합 키를 정의하는 경우 기본 키의 열 순서는 테이블에 표시되는 열 순서와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-131">If you define a compound key, the order of columns in the primary key matches the order of columns as shown in the table.</span></span> <span data-ttu-id="8d678-132">기본 키를 만든 후에 이러한 열 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-132">However, you can change the order of columns after the primary key is created.</span></span> <span data-ttu-id="8d678-133">자세한 내용은 [기본 키 수정](modify-primary-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d678-133">For more information, see [Modify Primary Keys](modify-primary-keys.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8d678-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8d678-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a><span data-ttu-id="8d678-135">기존 테이블에 고유 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8d678-135">To create a primary key in an existing table</span></span>  
  
1.  <span data-ttu-id="8d678-136">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d678-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8d678-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8d678-139">이 예에서는 `TransactionID`열에 기본 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-139">The example creates a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a><span data-ttu-id="8d678-140">새 테이블에 고유 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8d678-140">To create a primary key in a new table</span></span>  
  
1.  <span data-ttu-id="8d678-141">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d678-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8d678-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8d678-144">이 예에서는 테이블을 만들고 `TransactionID`열에 고유 키를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8d678-144">The example creates a table and defines a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="8d678-145">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 및 [table_constraint&#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d678-145">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
