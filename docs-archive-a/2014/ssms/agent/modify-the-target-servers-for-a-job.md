---
title: 작업의 대상 서버 수정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246a5bb59a681a70734cc8cabef4f724cda1b52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649333"
---
# <a name="modify-the-target-servers-for-a-job"></a><span data-ttu-id="b86ac-102">Modify the Target Servers for a Job</span><span class="sxs-lookup"><span data-stu-id="b86ac-102">Modify the Target Servers for a Job</span></span>
  <span data-ttu-id="b86ac-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는을 사용 하 여에서 에이전트 작업의 대상 서버를 변경 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b86ac-103">This topic describes how to change the target servers for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b86ac-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b86ac-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b86ac-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b86ac-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b86ac-106">보안</span><span class="sxs-lookup"><span data-stu-id="b86ac-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b86ac-107">**작업의 대상 서버를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="b86ac-107">**To modify the target servers for a job, using:**</span></span>  
  
     [<span data-ttu-id="b86ac-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b86ac-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b86ac-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b86ac-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b86ac-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b86ac-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b86ac-111">보안</span><span class="sxs-lookup"><span data-stu-id="b86ac-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b86ac-112">권한</span><span class="sxs-lookup"><span data-stu-id="b86ac-112">Permissions</span></span>  
 <span data-ttu-id="b86ac-113">sysadmin 고정 서버 역할의 멤버는 기본적으로 이 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-113">By default, members of the sysadmin fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="b86ac-114">다른 사용자는 msdb 데이터베이스의 다음 SQL Server 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-114">Other users must be granted one of the following SQL Server Agent fixed database roles in the msdb database:</span></span>  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  <span data-ttu-id="b86ac-115">SQLAgentOperatorRole</span><span class="sxs-lookup"><span data-stu-id="b86ac-115">SQLAgentOperatorRole</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b86ac-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b86ac-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="b86ac-117">작업의 대상 서버를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b86ac-117">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="b86ac-118">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b86ac-119">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-119">Expand **SQL Server Agent**, expand **Jobs**, right-click a job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b86ac-120">**작업 속성** 대화 상자에서 **대상**페이지를 선택하고 **대상 로컬 서버**또는 **대상 다중 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-120">In the **Job Properties** dialog, select the **Targets**page, and click **Target local server**, or **Target multiple servers**.</span></span>  
  
     <span data-ttu-id="b86ac-121">**대상 다중 서버**를 선택한 경우 서버 이름 왼쪽에 있는 확인란을 선택하여 작업 대상으로 사용할 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-121">If you choose **Target multiple servers**, designate the servers that will be targets for the job by checking the box to the left of the server name.</span></span> <span data-ttu-id="b86ac-122">작업 대상으로 지정하지 않을 서버의 확인란 선택이 취소되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-122">Verify that the check boxes for servers that will not be targets of the job are unchecked.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b86ac-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b86ac-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="b86ac-124">작업의 대상 서버를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b86ac-124">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="b86ac-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b86ac-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b86ac-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b86ac-128">이 예에서는 다중 서버 작업 Weekly Sales Backups를 SEATTLE2 서버에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b86ac-128">This example assigns the multiserver job Weekly Sales Backups to the server SEATTLE2.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 <span data-ttu-id="b86ac-129">자세한 내용은 [sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b86ac-129">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86ac-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b86ac-130">See Also</span></span>  
 [<span data-ttu-id="b86ac-131">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="b86ac-131">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
