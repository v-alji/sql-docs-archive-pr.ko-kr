---
title: 복제할 때 CHECK 제약 조건 해제 | Microsoft 문서
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
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98b6ca7c3525edeffdb47f294db568d3c115b2c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638616"
---
# <a name="disable-check-constraints-for-replication"></a><span data-ttu-id="ba5c0-102">복제할 때 CHECK 제약 조건 해제</span><span class="sxs-lookup"><span data-stu-id="ba5c0-102">Disable Check Constraints for Replication</span></span>
  <span data-ttu-id="ba5c0-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 CHECK 제약 조건을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-103">You can disable check constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ba5c0-104">명시적으로 복제에 대한 CHECK 제약 조건을 비활성화할 수도 있습니다. 이는 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터를 게시하는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-104">You can also explicitly disable check constraints for replication, which can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba5c0-105">테이블이 복제를 사용하여 게시된 경우 복제 에이전트에서 수행하는 작업에 대한 CHECK 제약 조건은 자동으로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-105">If a table is published using replication, check constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="ba5c0-106">복제 에이전트가 구독자에서 삽입, 업데이트 또는 삭제를 수행하면 제약 조건이 확인되지 않지만 사용자가 삽입, 업데이트 또는 삭제를 수행하면 제약 조건이 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="ba5c0-107">데이터가 원래 삽입, 업데이트 또는 삭제될 때 제약 조건이 게시자에 이미 확인되었으므로 복제 에이전트에 대한 제약 조건이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span> <span data-ttu-id="ba5c0-108">자세한 내용은 [스키마 옵션 지정](../replication/publish/specify-schema-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-108">For more information, see [Specify Schema Options](../replication/publish/specify-schema-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ba5c0-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ba5c0-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ba5c0-110">보안</span><span class="sxs-lookup"><span data-stu-id="ba5c0-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba5c0-111">권한</span><span class="sxs-lookup"><span data-stu-id="ba5c0-111">Permissions</span></span>  
 <span data-ttu-id="ba5c0-112">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-112">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba5c0-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ba5c0-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="ba5c0-114">복제할 때 CHECK 제약 조건을 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="ba5c0-114">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="ba5c0-115">**개체 탐색기**에서 수정하려는 CHECK 제약 조건을 포함하는 테이블을 확장하고 **제약 조건** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-115">In **Object Explorer**, expand the table with the check constraint you want to modify, and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="ba5c0-116">수정할 CHECK 제약 조건을 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-116">Right-click the check constraint you wish to modify and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="ba5c0-117">**CHECK 제약 조건** 대화 상자의 **테이블 디자이너**에서 **복제에 적용** 에 대해 **아니요**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-117">In the **Check Constraints** dialog box, under **Table Designer**, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="ba5c0-118">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-118">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba5c0-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ba5c0-119">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="ba5c0-120">복제할 때 CHECK 제약 조건을 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="ba5c0-120">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="ba5c0-121">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba5c0-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba5c0-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ba5c0-124">이 예에서는 IDENTITY 열이 있는 테이블과 테이블에 대한 CHECK 제약 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-124">The example creates a table with an IDENTITY column and a CHECK constraint on the table.</span></span> <span data-ttu-id="ba5c0-125">그런 다음 제약 조건을 삭제하고 NOT FOR REPLICATION 절을 지정하여 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-125">The example then drops the constraint and recreates it specifying the NOT FOR REPLICATION clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 <span data-ttu-id="ba5c0-126">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5c0-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>   
## <a name="see-also"></a><span data-ttu-id="ba5c0-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba5c0-127">See Also</span></span>  
 [<span data-ttu-id="ba5c0-128">스키마 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="ba5c0-128">Specify Schema Options</span></span>](../replication/publish/specify-schema-options.md)  
  
  
