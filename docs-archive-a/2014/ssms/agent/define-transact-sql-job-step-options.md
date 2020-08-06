---
title: Transact-SQL 작업 단계 옵션 정의 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc1d6412e52e74ce0c6d987d6189c0c72ffd7df7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729011"
---
# <a name="define-transact-sql-job-step-options"></a><span data-ttu-id="964d4-102">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="964d4-102">Define Transact-SQL Job Step Options</span></span>
  <span data-ttu-id="964d4-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 단계에 대 한 옵션을 정의 하는 방법에 대해 설명 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-103">This topic describes how to define options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="964d4-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="964d4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="964d4-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="964d4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="964d4-106">보안</span><span class="sxs-lookup"><span data-stu-id="964d4-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="964d4-107">**다음을 사용하여 Transact-SQL 작업 단계 옵션 정의**</span><span class="sxs-lookup"><span data-stu-id="964d4-107">**To define Transact-SQL job step options, using:** ,</span></span>  
  
     [<span data-ttu-id="964d4-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="964d4-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="964d4-109">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="964d4-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="964d4-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="964d4-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="964d4-111">보안</span><span class="sxs-lookup"><span data-stu-id="964d4-111">Security</span></span>  
 <span data-ttu-id="964d4-112">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="964d4-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="964d4-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="964d4-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-transact-sql-job-step-options"></a><span data-ttu-id="964d4-114">Transact-SQL 작업 단계 옵션을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="964d4-114">To define Transact-SQL job step options</span></span>  
  
1.  <span data-ttu-id="964d4-115">**개체 탐색기**에서 **SQL Server 에이전트**, **작업**을 차례로 확장한 다음 편집할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-115">In **Object Explorer**, expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="964d4-116">**단계** 페이지를 클릭하고 작업 단계를 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-116">Click the **Steps** page, click a job step, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="964d4-117">**작업 단계 속성** 대화 상자에서 작업 유형이 **T-SQL(Transact-SQL) 스크립트**임을 확인한 다음 **고급** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-117">On the **Job Step Properties** dialog, confirm that the job type is **Transact-SQL script (TSQL)**, and then select the **Advanced** page.</span></span>  
  
4.  <span data-ttu-id="964d4-118">**성공한 경우 동작** 목록에서 작업이 성공한 경우에 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-118">Specify an action to take if the job is successful by selecting from the **On success action** list.</span></span>  
  
5.  <span data-ttu-id="964d4-119">**다시 시도 횟수** 입력란에 0~9999 사이의 값을 입력하여 다시 시도 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-119">Specify a number of retry attempts by entering a number from 0 to 9999 into the **Retry attempts** box.</span></span>  
  
6.  <span data-ttu-id="964d4-120">**다시 시도 간격(분)** 입력란에 0~9999 사이의 시간(분)을 입력하여 다시 시도 간격을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-120">Specify a retry interval by entering a number of minutes from 0 to 9999 into the **Retry interval** box.</span></span>  
  
7.  <span data-ttu-id="964d4-121">**실패한 경우 동작** 목록에서 작업이 실패한 경우에 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-121">Specify an action to take if the job fails by choosing from the **On failure action** list.</span></span>  
  
8.  <span data-ttu-id="964d4-122">작업이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트인 경우 다음 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-122">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="964d4-123">**출력 파일**이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-123">Enter the name of an **Output file**.</span></span> <span data-ttu-id="964d4-124">기본적으로 작업 단계가 실행될 때마다 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-124">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="964d4-125">출력 파일을 덮어쓰지 않으려면 **기존 파일에 출력 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-125">If you do not want the output file overwritten, check **Append output to existing file**.</span></span> <span data-ttu-id="964d4-126">이 옵션은 **sysadmin** 고정 서버 역할의 멤버만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-126">This option is only available to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="964d4-127">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 사용자가 파일 시스템의 임의 파일을 볼 수 없으므로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 파일 시스템에 기록된 작업 단계 로그를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-127">Note that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not allow users to view arbitrary files on the file system, so you cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view job step logs that are written to the file system.</span></span>  
  
    -   <span data-ttu-id="964d4-128">작업 단계를 데이터베이스 테이블에 기록하려면 **테이블에 기록** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-128">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="964d4-129">기본적으로 작업 단계가 실행될 때마다 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-129">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="964d4-130">테이블 내용을 덮어쓰지 않으려면 **테이블의 기존 항목에 출력 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-130">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="964d4-131">작업 단계가 실행된 다음에는 **뷰**를 클릭하여 이 테이블의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-131">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="964d4-132">출력을 단계 기록에 포함하려면 **기록에 단계 출력 포함** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-132">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="964d4-133">출력은 오류가 없을 때만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-133">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="964d4-134">또한 출력이 잘릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-134">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="964d4-135">**sysadmin** 고정 서버 역할의 멤버이면서 이 작업 단계를 다른 SQL 로그인으로 실행하려는 경우 **다음 사용자 이름으로 실행** 목록에서 해당 SQL 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-135">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="964d4-136">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="964d4-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="964d4-137">**Transact-SQL 작업 단계 옵션을 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="964d4-137">**To define Transact-SQL job step options**</span></span>  
  
 <span data-ttu-id="964d4-138">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="964d4-138">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
