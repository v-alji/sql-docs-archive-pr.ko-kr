---
title: SQL Server 에이전트 작업 실행 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b997d5144b113102ba0ed2d9d1df59b6707acbee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653351"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a><span data-ttu-id="be36a-102">SQL Server 에이전트 작업 실행 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="be36a-102">Execute SQL Server Agent Job Task (Maintenance Plan)</span></span>
  <span data-ttu-id="be36a-103">**SQL Server 에이전트 작업 실행 태스크** 대화 상자를 사용하여 유지 관리 계획 내의 Microsoft SQL Server 에이전트 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-103">Use the **Execute SQL Server Agent Job Task** dialog to execute Microsoft SQL Server Agent jobs within a maintenance plan.</span></span> <span data-ttu-id="be36a-104">선택한 연결에 SQL Server 에이전트 작업이 없으면 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-104">This option will not be available if you have no SQL Server Agent jobs on the selected connection.</span></span>  
  
 <span data-ttu-id="be36a-105">이 태스크에서는 **sp_start_job** 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-105">This task uses the **.sp_start_job** statement.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="be36a-106">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="be36a-106">UI element list</span></span>  
 <span data-ttu-id="be36a-107">**연결**</span><span class="sxs-lookup"><span data-stu-id="be36a-107">**Connection**</span></span>  
 <span data-ttu-id="be36a-108">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="be36a-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="be36a-109">**New**</span></span>  
 <span data-ttu-id="be36a-110">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="be36a-111">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="be36a-112">**사용 가능한 SQL Server 에이전트 작업**</span><span class="sxs-lookup"><span data-stu-id="be36a-112">**Available SQL Agent jobs**</span></span>  
 <span data-ttu-id="be36a-113">실행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-113">Select the job to execute.</span></span> <span data-ttu-id="be36a-114">표에는 작업을 식별할 수 있는 **작업 이름** 과 **설명** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-114">The grid provides the **Job name** and **Description** to identify the jobs.</span></span>  
  
 <span data-ttu-id="be36a-115">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="be36a-115">**View T-SQL**</span></span>  
 <span data-ttu-id="be36a-116">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-116">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be36a-117">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-117">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="be36a-118">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="be36a-118">New Connection Dialog Box</span></span>  
 <span data-ttu-id="be36a-119">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="be36a-119">**Connection name**</span></span>  
 <span data-ttu-id="be36a-120">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-120">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="be36a-121">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="be36a-121">**Select or enter a server name**</span></span>  
 <span data-ttu-id="be36a-122">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-122">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="be36a-123">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="be36a-123">**Refresh**</span></span>  
 <span data-ttu-id="be36a-124">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-124">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="be36a-125">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="be36a-125">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="be36a-126">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-126">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="be36a-127">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="be36a-127">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="be36a-128">Microsoft Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-128">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="be36a-129">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="be36a-129">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="be36a-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-130">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="be36a-131">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-131">This option is not available.</span></span>  
  
 <span data-ttu-id="be36a-132">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="be36a-132">**User name**</span></span>  
 <span data-ttu-id="be36a-133">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-133">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="be36a-134">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-134">This option is not available.</span></span>  
  
 <span data-ttu-id="be36a-135">**암호**</span><span class="sxs-lookup"><span data-stu-id="be36a-135">**Password**</span></span>  
 <span data-ttu-id="be36a-136">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-136">Provide a password to use when authenticating.</span></span> <span data-ttu-id="be36a-137">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be36a-137">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be36a-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be36a-138">See Also</span></span>  
 <span data-ttu-id="be36a-139">[sp_add_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="be36a-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="be36a-140">[작업 만들기](../../ssms/agent/create-a-job.md) </span><span class="sxs-lookup"><span data-stu-id="be36a-140">[Create a Job](../../ssms/agent/create-a-job.md) </span></span>  
 [<span data-ttu-id="be36a-141">sp_start_job&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="be36a-141">sp_start_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
