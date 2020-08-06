---
title: 기본 키 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44fa1271143f813364bfd2109f8147f1d04294a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661596"
---
# <a name="delete-primary-keys"></a><span data-ttu-id="85d04-102">기본 키 삭제</span><span class="sxs-lookup"><span data-stu-id="85d04-102">Delete Primary Keys</span></span>
  <span data-ttu-id="85d04-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 기본 키를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-103">You can delete (drop) a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="85d04-104">기본 키를 삭제하면 해당 인덱스가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-104">When the primary key is deleted, the corresponding index is deleted.</span></span>  
  
 <span data-ttu-id="85d04-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="85d04-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85d04-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="85d04-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="85d04-107">보안</span><span class="sxs-lookup"><span data-stu-id="85d04-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="85d04-108">**기본 키를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="85d04-108">**To delete a primary key using:**</span></span>  
  
     [<span data-ttu-id="85d04-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85d04-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="85d04-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85d04-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="85d04-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="85d04-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="85d04-112">보안</span><span class="sxs-lookup"><span data-stu-id="85d04-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="85d04-113">권한</span><span class="sxs-lookup"><span data-stu-id="85d04-113">Permissions</span></span>  
 <span data-ttu-id="85d04-114">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="85d04-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="85d04-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a><span data-ttu-id="85d04-116">개체 탐색기를 사용하여 PRIMARY KEY 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="85d04-116">To delete a primary key constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="85d04-117">개체 탐색기에서 기본 키가 포함된 테이블을 확장한 후 **키**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-117">In Object Explorer, expand the table that contains the primary key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="85d04-118">키를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="85d04-119">**개체 삭제** 대화 상자에서 올바른 키가 지정되었는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a><span data-ttu-id="85d04-120">테이블 디자이너를 사용하여 PRIMARY KEY 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="85d04-120">To delete a primary key constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="85d04-121">개체 탐색기에서 기본 키가 있는 테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-121">In Object Explorer, right-click the table with the primary key, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="85d04-122">테이블 표에서 기본 키가 있는 행을 마우스 오른쪽 단추로 클릭하고 **기본 키 제거** 를 선택하여 기본 키 설정 또는 해제 여부를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-122">In the table grid, right-click the row with the primary key and choose **Remove Primary Key** to toggle the setting from on to off.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85d04-123">이 동작을 실행 취소하려면 변경 내용을 저장하지 않은 상태로 테이블을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-123">To undo this action, close the table without saving the changes.</span></span> <span data-ttu-id="85d04-124">기본 키 삭제 작업을 취소하면 테이블에 대한 다른 모든 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-124">Deleting a primary key cannot be undone without losing all other changes made to the table.</span></span>  
  
3.  <span data-ttu-id="85d04-125">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="85d04-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="85d04-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-primary-key-constraint"></a><span data-ttu-id="85d04-127">PRIMARY KEY 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="85d04-127">To delete a primary key constraint</span></span>  
  
1.  <span data-ttu-id="85d04-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="85d04-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="85d04-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="85d04-131">이 예에서는 먼저 PRIMARY KEY 제약 조건의 이름을 식별한 후 해당 제약 조건을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="85d04-131">The example first identifies the name of the primary key constraint and then deletes the constraint.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 <span data-ttu-id="85d04-132">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 및 [sys.key_constraints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85d04-132">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)</span></span>  
  
###  <a name="TsqlExample"></a>  
