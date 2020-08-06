---
title: 대상 서버의 폴링 간격 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742732"
---
# <a name="set-the-polling-interval-for-target-servers"></a><span data-ttu-id="0fca4-102">Set the Polling Interval for Target Servers</span><span class="sxs-lookup"><span data-stu-id="0fca4-102">Set the Polling Interval for Target Servers</span></span>
  <span data-ttu-id="0fca4-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 마스터에서 대상 서버로 정보를 새로 고치는 빈도를 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-103">This topic describes how to set the frequency that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refreshes information from the master to the target servers.</span></span> <span data-ttu-id="0fca4-104">작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행하도록 지정된 일련의 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="0fca4-105">다중 서버 작업은 마스터 서버가 하나 이상의 대상 서버에서 실행하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-105">A multiserver job is a job that a master server runs on one or more target servers.</span></span>  
  
-   <span data-ttu-id="0fca4-106">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="0fca4-106">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="0fca4-107">**다음을 사용하여 대상 서버 폴링 간격 설정**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)</span><span class="sxs-lookup"><span data-stu-id="0fca4-107">**To set the polling interval for target servers, using:**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0fca4-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0fca4-108">Before You Begin</span></span>  
 <span data-ttu-id="0fca4-109">각 대상 서버는 같은 작업의 한 인스턴스를 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-109">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="0fca4-110">각 대상 서버는 주기적으로 마스터 서버를 폴링하여 해당 대상 서버에 새로 할당된 작업의 복사본을 다운로드한 다음 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-110">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="0fca4-111">대상 서버는 로컬에서 작업을 실행한 다음 마스터 서버에 다시 연결하여 작업 결과 상태를 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-111">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fca4-112">대상 서버에서 작업 상태 업로드를 시도할 때 마스터 서버가 액세스 가능하지 않은 경우 작업 상태는 마스터 서버가 액세스 가능해질 때까지 스풀링됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-112">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0fca4-113">보안</span><span class="sxs-lookup"><span data-stu-id="0fca4-113">Security</span></span>  
 <span data-ttu-id="0fca4-114">자세한 내용은 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 및 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fca4-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0fca4-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0fca4-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0fca4-116">**대상 서버의 폴링 간격을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="0fca4-116">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="0fca4-117">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0fca4-118">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="0fca4-119">**대상 서버 상태** 탭에서 **명령 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-119">On the **Target Server Status** tab, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="0fca4-120">**명령 유형** 목록에서 **폴링 간격 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-120">In the **Instruction type** list, select **Set polling interval**.</span></span>  
  
5.  <span data-ttu-id="0fca4-121">**폴링 간격** 상자에 대상 서버가 마스터 서버를 폴링하기 전에 경과해야 하는 시간(초)을 10부터 28,800까지 범위에서 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-121">In the **Polling interval** box, enter the number of seconds from 10 through 28,800 that must pass before the target server polls the master server.</span></span>  
  
6.  <span data-ttu-id="0fca4-122">**받는 사람**에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-122">Under **Recipients**, do one of the following:</span></span>  
  
    1.  <span data-ttu-id="0fca4-123">모든 대상 서버가 같은 폴링 간격을 공유할 경우 **모든 대상 서버** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-123">Click **All target servers** if all target servers share the same polling interval.</span></span>  
  
    2.  <span data-ttu-id="0fca4-124">모든 대상 서버가 같은 폴링 간격을 공유하지는 않는 경우 **대상 서버 지정** 을 클릭한 다음 이 폴링 간격을 사용할 대상 서버를 각각 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-124">Click **These target servers** if not all target servers share the same polling interval, and then select each target server that will use this polling interval.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0fca4-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0fca4-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="0fca4-126">**대상 서버의 폴링 간격을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="0fca4-126">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="0fca4-127">개체 탐색기에서 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-127">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0fca4-128">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-128">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0fca4-129">쿼리 창에서 [sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) 시스템 저장 프로시저를 사용 하 여 대상 서버의 폴링 간격을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fca4-129">In the query window, use the [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) system stored procedure to set the polling interval for target servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fca4-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fca4-130">See Also</span></span>  
 [<span data-ttu-id="0fca4-131">dbo.sysdownloadlist &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0fca4-131">dbo.sysdownloadlist &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
