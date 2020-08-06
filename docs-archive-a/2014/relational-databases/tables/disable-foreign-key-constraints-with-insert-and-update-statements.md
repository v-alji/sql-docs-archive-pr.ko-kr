---
title: INSERT 및 UPDATE 문에서 FOREIGN KEY 제약 조건 사용 안 함 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: e91328f4f12f2a0a27f397c7bd95390a505f3998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649958"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a><span data-ttu-id="ad85d-102">NSERT 및 UPDATE 문에서 FOREIGN KEY 제약 조건 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="ad85d-102">Disable Foreign Key Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="ad85d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 INSERT 및 UPDATE 트랜잭션 중 FOREIGN KEY 제약 조건을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-103">You can disable a foreign key constraint during INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ad85d-104">새 데이터가 기존 제약 조건을 위반할지를 알고 있는 경우 또는 제약 조건이 데이터베이스에 이미 있는 데이터에만 적용될 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-104">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="ad85d-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ad85d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad85d-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ad85d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad85d-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ad85d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ad85d-108">보안</span><span class="sxs-lookup"><span data-stu-id="ad85d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad85d-109">**INSERT 및 UPDATE 문에 대한 FOREIGN KEY 제약 조건을 사용하지 않으려면:**</span><span class="sxs-lookup"><span data-stu-id="ad85d-109">**To disable a foreign key constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="ad85d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad85d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad85d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad85d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad85d-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ad85d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ad85d-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ad85d-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ad85d-114">이러한 제약 조건을 해제한 후에는 해당 열에 대한 이후 삽입 또는 업데이트 작업의 유효성을 해당 제약 조건에 따라 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-114">After you disable these constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad85d-115">보안</span><span class="sxs-lookup"><span data-stu-id="ad85d-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad85d-116">권한</span><span class="sxs-lookup"><span data-stu-id="ad85d-116">Permissions</span></span>  
 <span data-ttu-id="ad85d-117">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad85d-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ad85d-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="ad85d-119">INSERT 및 UPDATE 문에 대한 FOREIGN KEY 제약 조건을 사용하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="ad85d-119">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="ad85d-120">**개체 탐색기**에서 제약 조건을 포함하는 테이블을 확장한 다음 **키** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-120">In **Object Explorer**, expand the table with the constraint and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="ad85d-121">제약 조건을 마우스 오른쪽 단추로 클릭하고 **수정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-121">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="ad85d-122">**테이블 디자이너**아래의 표에서 **FOREIGN KEY 제약 조건 적용** 을 클릭하고 드롭다운 메뉴에서 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-122">In the grid under **Table Designer**, click **Enforce Foreign Key Constraint** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="ad85d-123">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad85d-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ad85d-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="ad85d-125">INSERT 및 UPDATE 문에 대한 FOREIGN KEY 제약 조건을 사용하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="ad85d-125">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="ad85d-126">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad85d-127">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad85d-128">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad85d-128">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 <span data-ttu-id="ad85d-129">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad85d-129">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
