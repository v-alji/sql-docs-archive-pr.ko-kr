---
title: 대상 서버 클럭 동기화(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e7150cd42699503ab22cdd89fb6206194bd64e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727884"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a><span data-ttu-id="75499-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="75499-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span></span>
  <span data-ttu-id="75499-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 대상 서버 클럭을 마스터 서버 클럭과 동기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-103">This topic describes how to synchronize target server clocks in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] with the master server clock by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="75499-104">이러한 시스템 클럭의 동기화는 사용자의 작업 일정을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-104">Synchronizing these system clocks supports your job schedules.</span></span>  
  
 <span data-ttu-id="75499-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="75499-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="75499-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="75499-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="75499-107">보안</span><span class="sxs-lookup"><span data-stu-id="75499-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="75499-108">**다음을 사용하여 대상 서버 클럭을 동기화합니다.**</span><span class="sxs-lookup"><span data-stu-id="75499-108">**To synchronize target server clocks, using:**</span></span>  
  
     [<span data-ttu-id="75499-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75499-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="75499-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="75499-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="75499-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="75499-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="75499-112">보안</span><span class="sxs-lookup"><span data-stu-id="75499-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="75499-113">권한</span><span class="sxs-lookup"><span data-stu-id="75499-113">Permissions</span></span>  
 <span data-ttu-id="75499-114">**sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="75499-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="75499-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="75499-116">대상 서버 클럭을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="75499-116">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="75499-117">**개체 탐색기** 에서 더하기 기호를 클릭하여 대상 서버 클럭을 마스터 서버 클럭과 동기화하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-117">In **Object Explorer,** click the plus sign to expand the server where you want to synchronize the target server clocks with the master server clock.</span></span>  
  
2.  <span data-ttu-id="75499-118">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="75499-119">**대상 서버 관리** 대화 상자에서 **명령 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-119">In the **Manage Target Servers** dialog box, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="75499-120">**명령 유형** 목록에서 **클럭 동기화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-120">In the **Instruction type** list, select **Synchronize clocks**.</span></span>  
  
5.  <span data-ttu-id="75499-121">**받는 사람**에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-121">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="75499-122">모든 대상 서버 클럭을 마스터 서버 클럭과 동기화하려면 **모든 대상 서버** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-122">Click **All target servers** to synchronize all target server clocks with the master server clock.</span></span>  
  
    -   <span data-ttu-id="75499-123">**대상 서버 지정** 을 클릭하여 특정 서버 클럭을 동기화하고 마스터 서버 클럭과 동기화할 클럭의 대상 서버를 각각 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-123">Click **These target servers** to synchronize certain server clocks, and then select each target server whose clock you want to synchronize with the master server clock.</span></span>  
  
6.  <span data-ttu-id="75499-124">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-124">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="75499-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="75499-125">Using Transact-SQL</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="75499-126">대상 서버 클럭을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="75499-126">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="75499-127">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="75499-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="75499-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="75499-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 <span data-ttu-id="75499-130">자세한 내용은 [sp_resync_targetserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="75499-130">For more information, see [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).</span></span>  
  
  
