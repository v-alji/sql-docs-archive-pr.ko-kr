---
title: 복제할 때 FOREIGN KEY 제약 조건 비활성화 | Microsoft 문서
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
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ee7f2fb7b0a27870a09a9d99b723b7faf739aeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649962"
---
# <a name="disable-foreign-key-constraints-for-replication"></a><span data-ttu-id="70a1c-102">복제할 때 FOREIGN KEY 제약 조건 비활성화</span><span class="sxs-lookup"><span data-stu-id="70a1c-102">Disable Foreign Key Constraints for Replication</span></span>
  <span data-ttu-id="70a1c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 복제에 대한 FOREIGN KEY 제약 조건을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-103">You can disable foreign key constraints for replication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="70a1c-104">이 기능은 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전의 데이터를 게시하는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-104">This can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70a1c-105">테이블이 복제를 사용하여 게시된 경우 복제 에이전트에 의해 수행된 작업의 FOREIGN KEY 제약 조건은 자동으로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-105">If a table is published using replication, foreign key constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="70a1c-106">복제 에이전트가 구독자에서 삽입, 업데이트 또는 삭제를 수행하면 제약 조건이 확인되지 않지만 사용자가 삽입, 업데이트 또는 삭제를 수행하면 제약 조건이 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="70a1c-107">데이터가 원래 삽입, 업데이트 또는 삭제될 때 제약 조건이 게시자에 이미 확인되었으므로 복제 에이전트에 대한 제약 조건이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span>  
  
 <span data-ttu-id="70a1c-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="70a1c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="70a1c-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="70a1c-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="70a1c-110">보안</span><span class="sxs-lookup"><span data-stu-id="70a1c-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="70a1c-111">**복제에 대한 FOREIGN KEY 제약 조건을 비활성화하려면:**</span><span class="sxs-lookup"><span data-stu-id="70a1c-111">**To disable a foreign key constraint for replication, using:**</span></span>  
  
     [<span data-ttu-id="70a1c-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="70a1c-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="70a1c-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="70a1c-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="70a1c-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="70a1c-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="70a1c-115">보안</span><span class="sxs-lookup"><span data-stu-id="70a1c-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="70a1c-116">권한</span><span class="sxs-lookup"><span data-stu-id="70a1c-116">Permissions</span></span>  
 <span data-ttu-id="70a1c-117">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="70a1c-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="70a1c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="70a1c-119">복제할 때 FOREIGN KEY 제약 조건을 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="70a1c-119">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="70a1c-120">**개체 탐색기**에서 수정할 FOREIGN KEY 제약 조건을 포함하는 테이블을 확장한 다음 **키** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-120">In **Object Explorer**, expand the table with the foreign key constraint you want to modify, and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="70a1c-121">외래 키 제약 조건을 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-121">Right-click the foreign key constraint and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="70a1c-122">**외래 키 관계** 대화 상자에서 **복제에 적용** 값으로 **아니요**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-122">In the **Foreign Key Relationships** dialog box, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="70a1c-123">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="70a1c-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="70a1c-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="70a1c-125">복제할 때 FOREIGN KEY 제약 조건을 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="70a1c-125">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="70a1c-126">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 이 태스크를 수행하려면 FOREIGN KEY 제약 조건을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-126">To perform this task in [!INCLUDE[tsql](../../includes/tsql-md.md)], drop the foreign key constraint.</span></span> <span data-ttu-id="70a1c-127">그런 다음 새 FOREIGN KEY 제약 조건을 추가하고 NOT FOR REPLICATION 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70a1c-127">Then add a new foreign key constraint and specify the NOT FOR REPLICATION option.</span></span>  
  
 <span data-ttu-id="70a1c-128">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70a1c-128">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
