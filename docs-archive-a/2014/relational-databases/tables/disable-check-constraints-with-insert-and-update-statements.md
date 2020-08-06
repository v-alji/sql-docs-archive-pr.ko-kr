---
title: INSERT 및 UPDATE 문에서 CHECK 제약 조건 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 780a2c1bfd9f21c71367ad61f200ec19ab44a608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650864"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a><span data-ttu-id="34096-102">INSERT 및 UPDATE 문에서 CHECK 제약 조건 해제</span><span class="sxs-lookup"><span data-stu-id="34096-102">Disable Check Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="34096-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 INSERT 및 UPDATE 트랜잭션에 대해 CHECK 제약 조건을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34096-103">You can disable a check constraint for INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="34096-104">CHECK 제약 조건을 해제한 후에는 해당 열에 대한 이후 삽입 또는 업데이트 작업의 유효성을 해당 제약 조건에 따라 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34096-104">After you disable the check constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span> <span data-ttu-id="34096-105">새 데이터가 기존 제약 조건을 위반할지를 알고 있는 경우 또는 제약 조건이 데이터베이스에 이미 있는 데이터에만 적용될 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-105">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="34096-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="34096-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34096-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="34096-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="34096-108">보안</span><span class="sxs-lookup"><span data-stu-id="34096-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="34096-109">**INSERT 및 UPDATE 문에 대해 CHECK 제약 조건을 해제하려면**</span><span class="sxs-lookup"><span data-stu-id="34096-109">**To disable a check constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="34096-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34096-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="34096-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34096-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34096-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="34096-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34096-113">보안</span><span class="sxs-lookup"><span data-stu-id="34096-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34096-114">권한</span><span class="sxs-lookup"><span data-stu-id="34096-114">Permissions</span></span>  
 <span data-ttu-id="34096-115">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-115">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="34096-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="34096-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="34096-117">INSERT 및 UPDATE 문에 대해 CHECK 제약 조건을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="34096-117">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="34096-118">**개체 탐색기**에서 제약 조건을 포함하는 테이블을 확장하고 **제약 조건** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-118">In **Object Explorer**, expand the table with the constraint and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="34096-119">제약 조건을 마우스 오른쪽 단추로 클릭하고 **수정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-119">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="34096-120">**테이블 디자이너**아래의 표에서 **INSERT 및 UPDATE에 적용** 을 클릭하고 드롭다운 메뉴에서 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-120">In the grid under **Table Designer**, click **Enforce For INSERTs And UPDATEs** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="34096-121">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-121">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="34096-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="34096-122">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="34096-123">INSERT 및 UPDATE 문에 대해 CHECK 제약 조건을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="34096-123">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="34096-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34096-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34096-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34096-126">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 <span data-ttu-id="34096-127">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34096-127">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
