---
title: CHECK 제약 조건 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7795ee6eca85a22bdd4e84c90ce49a9449ddff28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661608"
---
# <a name="create-check-constraints"></a><span data-ttu-id="a839f-102">CHECK 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="a839f-102">Create Check Constraints</span></span>
  <span data-ttu-id="a839f-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 하나 이상의 열에 사용할 수 있는 데이터 값을 지정할 수 있도록 테이블에 CHECK 제약 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-103">You can create a check constraint in a table to specify the data values that are acceptable in one or more columns in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a839f-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a839f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a839f-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a839f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a839f-106">보안</span><span class="sxs-lookup"><span data-stu-id="a839f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a839f-107">**새 CHECK 제약 조건을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a839f-107">**To create a new check constraint using:**</span></span>  
  
     [<span data-ttu-id="a839f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a839f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a839f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a839f-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a839f-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a839f-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a839f-111">보안</span><span class="sxs-lookup"><span data-stu-id="a839f-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a839f-112">권한</span><span class="sxs-lookup"><span data-stu-id="a839f-112">Permissions</span></span>  
 <span data-ttu-id="a839f-113">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-113">Requires ALTER permissions on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a839f-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a839f-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="a839f-115">새 CHECK 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="a839f-115">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="a839f-116">**개체 탐색기**에서 CHECK 제약 조건을 추가하려는 테이블을 확장하고, **제약 조건** 을 마우스 오른쪽 단추로 클릭한 후 **새 제약 조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-116">In **Object Explorer**, expand the table to which you want to add a check constraint, right-click **Constraints** and click **New Constraint**.</span></span>  
  
2.  <span data-ttu-id="a839f-117">**CHECK 제약 조건** 대화 상자에서 **식** 필드를 클릭한 후, 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-117">In the **Check Constraints** dialog box, click in the **Expression** field and then click the ellipses **(...)**.</span></span>  
  
3.  <span data-ttu-id="a839f-118">**CHECK 제약 조건 식** 대화 상자에서 CHECK 제약 조건에 대한 SQL 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-118">In the **Check Constraint Expression** dialog box, type the SQL expressions for the check constraint.</span></span> <span data-ttu-id="a839f-119">예를 들어 `SellEndDate` 테이블의 `Product` 열에 있는 항목을 `SellStartDate` 열에 있는 날짜보다 크거나 같은 값 또는 NULL 값으로 제한하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-119">For example, to limit the entries in the `SellEndDate` column of the `Product` table to a value that is either greater than or equal to the date in the `SellStartDate` column or is a NULL value, type:</span></span>  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     <span data-ttu-id="a839f-120">또는, `zip` 열의 항목을 다섯 자리 숫자로 입력하도록 하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-120">Or, to require entries in the `zip` column to be 5 digits, type:</span></span>  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="a839f-121">숫자가 아닌 제약 조건 값은 모두 작은따옴표(')로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-121">Make sure to enclose any non-numeric constraint values in single quotation marks (').</span></span>  
  
4.  <span data-ttu-id="a839f-122">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a839f-123">**ID** 범주에서는 CHECK 제약 조건의 이름을 변경하고 해당 제약 조건에 대한 설명(확장 속성)을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-123">In the **Identity** category, you can change the name of the check constraint and add a description (extended property) for the constraint.</span></span>  
  
6.  <span data-ttu-id="a839f-124">**테이블 디자이너** 범주에서는 제약 조건을 적용하는 경우를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-124">In the **Table Designer** category, you can set when the constraint is enforced.</span></span>  
  
    |<span data-ttu-id="a839f-125">**받는 사람:**</span><span class="sxs-lookup"><span data-stu-id="a839f-125">**To:**</span></span>|<span data-ttu-id="a839f-126">**다음 필드에서 예 선택:**</span><span class="sxs-lookup"><span data-stu-id="a839f-126">**Select Yes in the Following Fields:**</span></span>|  
    |-------------|---------------------------------------------|  
    |<span data-ttu-id="a839f-127">제약 조건을 만들기 전에 존재한 데이터에 대한 제약 조건 테스트</span><span class="sxs-lookup"><span data-stu-id="a839f-127">Test the constraint on data that existed before you created the constraint</span></span>|<span data-ttu-id="a839f-128">**만들거나 활성화할 때 기존 데이터 검사**</span><span class="sxs-lookup"><span data-stu-id="a839f-128">**Check Existing Data On Creation Or Enabling**</span></span>|  
    |<span data-ttu-id="a839f-129">이 테이블에서 복제 작업이 수행될 때마다 제약 조건 적용</span><span class="sxs-lookup"><span data-stu-id="a839f-129">Enforce the constraint whenever a replication operation occurs on this table</span></span>|<span data-ttu-id="a839f-130">**복제에 적용**</span><span class="sxs-lookup"><span data-stu-id="a839f-130">**Enforce For Replication**</span></span>|  
    |<span data-ttu-id="a839f-131">이 테이블의 행을 삽입하거나 업데이트할 때마다 제약 조건 적용</span><span class="sxs-lookup"><span data-stu-id="a839f-131">Enforce the constraint whenever a row of this table is inserted or updated</span></span>|<span data-ttu-id="a839f-132">**INSERT 및 UPDATE에 적용**</span><span class="sxs-lookup"><span data-stu-id="a839f-132">**Enforce For INSERTs And UPDATEs**</span></span>|  
  
7.  <span data-ttu-id="a839f-133">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-133">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a839f-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a839f-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-check-constraint"></a><span data-ttu-id="a839f-135">새 CHECK 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="a839f-135">To create a new check constraint</span></span>  
  
1.  <span data-ttu-id="a839f-136">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a839f-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a839f-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a839f-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 <span data-ttu-id="a839f-139">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a839f-139">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
