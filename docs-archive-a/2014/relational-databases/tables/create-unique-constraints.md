---
title: UNIQUE 제약 조건 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 252de63f965f98734a6d62d94bfff9dc5774cab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738169"
---
# <a name="create-unique-constraints"></a><span data-ttu-id="f52a1-102">UNIQUE 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="f52a1-102">Create Unique Constraints</span></span>
  <span data-ttu-id="f52a1-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 UNIQUE 제약 조건을 만들어서 기본 키에 참여하지 않는 특정 열에 입력하는 값이 중복되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-103">You can create a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] to ensure no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="f52a1-104">UNIQUE 제약 조건을 만들면 해당하는 고유 인덱스가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-104">Creating a unique constraint automatically creates a corresponding unique index.</span></span>  
  
 <span data-ttu-id="f52a1-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f52a1-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f52a1-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f52a1-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f52a1-107">보안</span><span class="sxs-lookup"><span data-stu-id="f52a1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f52a1-108">**UNIQUE 제약 조건을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="f52a1-108">**To create a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="f52a1-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f52a1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f52a1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f52a1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f52a1-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f52a1-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f52a1-112">보안</span><span class="sxs-lookup"><span data-stu-id="f52a1-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f52a1-113">권한</span><span class="sxs-lookup"><span data-stu-id="f52a1-113">Permissions</span></span>  
 <span data-ttu-id="f52a1-114">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f52a1-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f52a1-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="f52a1-116">UNIQUE 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f52a1-116">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="f52a1-117">**개체 탐색기**에서 UNIQUE 제약 조건을 추가하려는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-117">In **Object Explorer**, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="f52a1-118">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-118">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="f52a1-119">**인덱스/키** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-119">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="f52a1-120">**일반**아래의 표에서 **형식** 을 선택하고 속성 오른쪽에 있는 드롭다운 목록 상자에서 **고유 키** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-120">In the grid under **General**, click **Type** and choose **Unique Key** from the drop-down list box to the right of the property.</span></span>  
  
5.  <span data-ttu-id="f52a1-121">**파일** 메뉴에서 ‘테이블 이름’ **저장**을 클릭합니다.__</span><span class="sxs-lookup"><span data-stu-id="f52a1-121">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f52a1-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f52a1-122">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="f52a1-123">UNIQUE 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f52a1-123">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="f52a1-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f52a1-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f52a1-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-126">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f52a1-127">이 예에서는 `TransactionHistoryArchive4` 테이블을 만들고 `TransactionID`열에 UNIQUE 제약 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-127">The example creates the table `TransactionHistoryArchive4` and creates a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a><span data-ttu-id="f52a1-128">기존 테이블에 UNIQUE 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f52a1-128">To create a unique constraint on an existing table</span></span>  
  
1.  <span data-ttu-id="f52a1-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f52a1-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f52a1-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-131">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f52a1-132">이 예에서는 `PasswordHash` 테이블에서 `PasswordSalt` 및 `Person.Password`열에 UNIQUE 제약 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-132">The example creates a unique constraint on the columns `PasswordHash` and `PasswordSalt` in the table `Person.Password`.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a><span data-ttu-id="f52a1-133">새 테이블에 UNIQUE 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f52a1-133">To create a unique constraint in an new table</span></span>  
  
1.  <span data-ttu-id="f52a1-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f52a1-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f52a1-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f52a1-137">이 예에서는 테이블을 만들고 `TransactionID`열에 UNIQUE 제약 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f52a1-137">The example creates a table and defines a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="f52a1-138">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 및 [table_constraint&#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f52a1-138">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
