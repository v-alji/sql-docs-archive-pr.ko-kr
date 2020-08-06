---
title: 비즈니스 논리 처리기 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b255407783b1e52a376e562ec910f8b123e42c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646937"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a><span data-ttu-id="2836d-102">비즈니스 논리 처리기 디버깅(복제 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="2836d-102">Debug a Business Logic Handler (Replication Programming)</span></span>
  <span data-ttu-id="2836d-103">비즈니스 논리 처리기를 사용하여 병합 구독이 동기화될 때 사용자 지정 비즈니스 논리를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-103">Use a business logic handler to invoke custom business logic when a merge subscription is synchronized.</span></span> <span data-ttu-id="2836d-104">자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](merge/execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2836d-104">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="2836d-105">병합 복제 조정자(replrec.dll)는 비즈니스 논리가 포함된 관리 코드 어셈블리를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-105">The Merge Replication Reconciler (replrec.dll) calls the managed code assembly containing the business logic.</span></span> <span data-ttu-id="2836d-106">대부분의 경우 replrec.dll과 사용자 지정 비즈니스 논리는 병합 에이전트가 실행되는 컴퓨터(끌어오기 구독의 경우 구독자, 밀어넣기 구독의 경우 배포자)에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-106">In most cases, replrec.dll and the custom business logic is executed on the computer where the Merge Agent runs (at the Subscriber for a pull subscription or at the Distributor for a push subscription).</span></span> <span data-ttu-id="2836d-107">웹 동기화 또는 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 구독자의 경우 조정자와 사용자 지정 비즈니스 논리는 웹 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-107">In the case of Web synchronization, or in the case of a [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscriber, the reconciler and the custom business logic is executed on the Web server.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a><span data-ttu-id="2836d-108">로컬 컴퓨터의 비즈니스 논리 처리기를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="2836d-108">To debug a business logic handler on a local computer</span></span>  
  
1.  <span data-ttu-id="2836d-109">게시 및 배포를 구성하고 게시를 만들고 게시에 대한 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-109">Configure publishing and distribution, create a publication, and create a subscription to the publication.</span></span> <span data-ttu-id="2836d-110">자세한 내용은 [게시 및 배포 구성](configure-publishing-and-distribution.md) 및 [게시 만들기](publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2836d-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [Create a Publication](publish/create-a-publication.md).</span></span>  
  
2.  <span data-ttu-id="2836d-111">비즈니스 논리 처리기를 만들고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-111">Create and register a business logic handler.</span></span> <span data-ttu-id="2836d-112">자세한 내용은 [병합 아티클에 대한 비즈니스 논리 처리기 구현](implement-a-business-logic-handler-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2836d-112">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="2836d-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio에서 프로그래밍 방식으로 병합 에이전트를 동기적으로 시작하는 RMO(복제 관리 개체) 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-113">Create a Replication Management Objects (RMO) project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio that programmatically starts the Merge Agent synchronously.</span></span> <span data-ttu-id="2836d-114">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2836d-114">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
4.  <span data-ttu-id="2836d-115">비즈니스 논리 처리기 코드에서 디버깅 대상 메서드 또는 클래스 생성자 내에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-115">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="2836d-116">비즈니스 논리 처리기에 구현할 수 있는 메서드에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 메서드 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2836d-116">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
5.  <span data-ttu-id="2836d-117">비즈니스 논리 처리기를 디버그 모드로 빌드하고 어셈블리와 디버깅 기호 파일(.pdb)을 1단계에서 등록한 위치에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-117">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2836d-118">디버깅을 간소화하기 위해 비즈니스 논리 처리기 프로젝트와 구독을 동기화하는 프로젝트를 모두 포함하는 단일 Visual Studio .NET 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-118">To simplify debugging, create a single Visual Studio .NET solution that contains both the business logic handler project and the project that synchronizes the subscription.</span></span> <span data-ttu-id="2836d-119">이 경우에 동기화 프로젝트를 시작 프로젝트로 설정하고, 디버깅 중에 1단계에서 등록한 위치에 비즈니스 논리 어셈블리를 배포하도록 빌드 환경을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-119">In this case, set the synchronization project as the startup project, and configure the build environment to deploy the business logic assembly to the location registered in step 1 during debugging.</span></span>  
  
6.  <span data-ttu-id="2836d-120">구독 또는 게시 데이터베이스를 대상으로 삽입, 업데이트 또는 삭제 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-120">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="2836d-121">명령 및 실행 위치는 디버깅 대상 메서드에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-121">The command and execution location depends on the method being debugged.</span></span>  
  
7.  <span data-ttu-id="2836d-122">3단계의 프로젝트를 디버그 모드로 시작하여 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-122">Start the project from step 3 in debug mode to synchronize the subscription.</span></span>  
  
8.  <span data-ttu-id="2836d-123">설정된 다른 중단점이 없고 올바른 명령이 복제된 경우 비즈니스 논리 처리기에 설정한 중단점에 도달하면 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-123">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a><span data-ttu-id="2836d-124">웹 동기화를 사용하는 웹 서버 또는 SQL Server Compact 구독자의 비즈니스 논리 처리기를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="2836d-124">To debug a business logic handler on a Web server using Web synchronization, or for a SQL Server Compact Subscriber</span></span>  
  
1.  <span data-ttu-id="2836d-125">게시 및 배포를 구성하고 게시를 만들고 게시에 대한 끌어오기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-125">Configure publishing and distribution, create a publication, and create a pull subscription to the publication.</span></span> <span data-ttu-id="2836d-126">게시는 웹 동기화 또는 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 구독자를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-126">The publication must support Web synchronization or [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
2.  <span data-ttu-id="2836d-127">비즈니스 논리 처리기를 만들고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-127">Create and register a business logic handler.</span></span> <span data-ttu-id="2836d-128">자세한 내용은 [병합 아티클에 대한 비즈니스 논리 처리기 구현](implement-a-business-logic-handler-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2836d-128">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="2836d-129">비즈니스 논리 처리기 코드에서 디버깅 대상 메서드 또는 클래스 생성자 내에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-129">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="2836d-130">비즈니스 논리 처리기에 구현할 수 있는 메서드에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 메서드 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2836d-130">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
4.  <span data-ttu-id="2836d-131">비즈니스 논리 처리기를 디버그 모드로 빌드하고 웹 서버에서 어셈블리와 디버깅 기호 파일(.pdb)을 1단계에서 등록한 위치에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-131">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) at the Web server in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2836d-132">어셈블리가 사용 중이어서 비즈니스 논리 처리기 빌드가 실패하는 경우에는 웹 서버의 명령 프롬프트에서 `iisreset` 명령을 입력하여 웹 서버를 다시 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="2836d-132">If the business logic handler fails to build because the assembly is in use, type the command `iisreset` on the Web server at the command prompt to reset the Web server.</span></span>  
  
5.  <span data-ttu-id="2836d-133">웹 동기화를 설정하고 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-133">Synchronize the subscription with Web synchronization enabled.</span></span> <span data-ttu-id="2836d-134">동기화 중에 웹 서버는 등록된 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-134">During synchronization, the Web server loads the registered assembly.</span></span>  
  
6.  <span data-ttu-id="2836d-135">Visual Studio .NET 디버거를 사용하여 웹 서버의 다음 프로세스 중 하나에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-135">Using the Visual Studio .NET debugger, attach to the one of the following processes on the Web server:</span></span>  
  
    -   <span data-ttu-id="2836d-136">w3wp.exe - Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2836d-136">w3wp.exe - Windows Server 2003.</span></span>  
  
    -   <span data-ttu-id="2836d-137">inetinfo.exe - Windows 2000 및 Windows XP</span><span class="sxs-lookup"><span data-stu-id="2836d-137">inetinfo.exe - Windows 2000 and Windows XP.</span></span>  
  
7.  <span data-ttu-id="2836d-138">**출력** 창의 디버그 출력에서 등록된 어셈블리에 대한 기호가 올바르게 로드되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-138">In the **Output** window, check the debug output to verify that the symbols for the registered assembly loaded properly.</span></span> <span data-ttu-id="2836d-139">기호가 로드되지 않은 경우 4단계에서 올바른 .pdb 파일을 복사했는지 확인하고 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-139">If the symbols were not loaded, ensure that the correct .pdb file was copied in step 4, and repeat step 5.</span></span>  
  
8.  <span data-ttu-id="2836d-140">구독 또는 게시 데이터베이스를 대상으로 삽입, 업데이트 또는 삭제 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-140">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="2836d-141">명령 및 실행 위치는 디버깅 대상 메서드에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-141">The command and execution location depends on the method being debugged.</span></span>  
  
9. <span data-ttu-id="2836d-142">Visual Studio 디버거를 사용하여 w3wp.exe 프로세스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-142">Using the Visual Studio debugger, attach to the w3wp.exe process.</span></span>  
  
10. <span data-ttu-id="2836d-143">웹 동기화를 사용하여 구독을 다시 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-143">Synchronize the subscription again, using Web synchronization.</span></span>  
  
11. <span data-ttu-id="2836d-144">설정된 다른 중단점이 없고 올바른 명령이 복제된 경우 비즈니스 논리 처리기에 설정한 중단점에 도달하면 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2836d-144">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2836d-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2836d-145">See Also</span></span>  
 [<span data-ttu-id="2836d-146">병합 아티클에 대한 비즈니스 논리 처리기 구현</span><span class="sxs-lookup"><span data-stu-id="2836d-146">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
