---
title: 컨트롤러 및 클라이언트 서비스 계정 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a054749f1d53323bde5c9d05a1e7632b1dda85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734820"
---
# <a name="modify-the-controller-and-client-services-accounts"></a><span data-ttu-id="b40e2-102">컨트롤러 및 클라이언트 서비스 계정 수정</span><span class="sxs-lookup"><span data-stu-id="b40e2-102">Modify the Controller and Client Services Accounts</span></span>
  <span data-ttu-id="b40e2-103">이 항목에서는 Distributed Replay Controller 및 Distributed Replay Client 서비스 계정을 수정한 후 ACL(액세스 제어 목록)을 다시 적용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-103">In this topic, you will learn how to modify the Distributed Replay controller and client service accounts, and then reapply the access control lists (ACLs).</span></span>  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a><span data-ttu-id="b40e2-104">컴퓨터 관리를 사용하여 Distributed Replay 서비스를 시작 또는 중지하려면</span><span class="sxs-lookup"><span data-stu-id="b40e2-104">To start or stop the Distributed Replay services using Computer Management</span></span>  
  
1.  <span data-ttu-id="b40e2-105">Distributed Replay 서비스가 설치된 컴퓨터에서 명령 프롬프트에 `dcomcnfg`을(를) 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-105">On the computer on which the Distributed Replay services are installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
2.  <span data-ttu-id="b40e2-106">**서비스**를 두 번 클릭 하 고 아래로 스크롤한 다음 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name> \*\*를 마우스 오른쪽 단추로 클릭 하 고 **시작** 또는 **중지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-106">Double-click **Services**, scroll down and right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name>**, and then click **Start** or **Stop**.</span></span>  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a><span data-ttu-id="b40e2-107">Distributed Replay Controller 서비스를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b40e2-107">To modify the Distributed Replay controller service</span></span>  
  
1.  <span data-ttu-id="b40e2-108">컨트롤러 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-108">On the controller computer, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="b40e2-109">**서비스**에서 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-109">Under **Services**, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**, and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="b40e2-110">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller Properties** 창의 **로그온** 탭에서 **계정 지정**을 선택하거나 **찾아보기** 를 클릭하고 새 로그온 계정을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-110">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b40e2-111">**중요**: Distributed Replay Controller를 구성할 때 Distributed Replay Client 서비스를 실행하는 데 사용할 사용자 계정을 하나 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-111">**Important**: When you configure Distributed Replay Controller, you can specify one or more user accounts that will be used to run the Distributed Replay Client services.</span></span> <span data-ttu-id="b40e2-112">다음은 지원되는 계정 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-112">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="b40e2-113">도메인 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="b40e2-113">Domain user account</span></span>  
  
    -   <span data-ttu-id="b40e2-114">사용자가 만든 로컬 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="b40e2-114">User created local user account</span></span>  
  
    -   <span data-ttu-id="b40e2-115">관리자</span><span class="sxs-lookup"><span data-stu-id="b40e2-115">Administrator</span></span>  
  
    -   <span data-ttu-id="b40e2-116">가상 계정 및 MSA(관리 서비스 계정)</span><span class="sxs-lookup"><span data-stu-id="b40e2-116">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="b40e2-117">Network Services, 로컬 서비스 및 시스템</span><span class="sxs-lookup"><span data-stu-id="b40e2-117">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="b40e2-118">그룹 계정(로컬 또는 도메인) 및 다른 기본 제공 계정(예: Everyone)은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-118">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
4.  <span data-ttu-id="b40e2-119">Distributed Replay Controller 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-119">Start the Distributed Replay controller service.</span></span>  
  
### <a name="to-modify-the-distributed-replay-client-service"></a><span data-ttu-id="b40e2-120">Distributed Replay Client 서비스를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b40e2-120">To modify the Distributed Replay client service</span></span>  
  
1.  <span data-ttu-id="b40e2-121">클라이언트 서비스를 수정하기 전에 변경할 Distributed Replay Client 서비스 계정이 설치 중 컨트롤러 컴퓨터의 CTLRUSERS 매개 변수에 지정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-121">Before you modify the Distributed Replay client service, make sure the client service account you are changing was specified during setup (in the CTLRUSERS parameter on the controller computer).</span></span> <span data-ttu-id="b40e2-122">변경하려는 클라이언트 서비스 계정이 설치 중 지정되지 않은 경우 다음 단계를 먼저 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-122">If the client service account you are changing was not specified during setup, you must perform the following steps first:</span></span>  
  
    1.  <span data-ttu-id="b40e2-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller service.</span></span>  
  
    2.  <span data-ttu-id="b40e2-124">Controller 서비스가 설치된 컨트롤러 컴퓨터에서 명령 프롬프트에 `dcomcnfg`을(를) 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-124">On the controller computer on which the controller service is installed, from the command prompt, type `dcomcnfg`.</span></span>  
  
    3.  <span data-ttu-id="b40e2-125">**구성 요소 서비스** 창에서 **콘솔 루트 -> 구성 요소 서비스 -> 컴퓨터 -> 내 컴퓨터 -> DCOM Config ->DReplayController**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-125">In the **Component Services** window, navigate to **Console Root -> Component Services -> Computers -> My Computer -> DCOM Config ->DReplayController**.</span></span>  
  
    4.  <span data-ttu-id="b40e2-126">**DReplayController**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-126">Right-click **DReplayController**, and then click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="b40e2-127">**DReplayController 속성** 창의 **보안** 탭에 있는 **시작 및 활성화 권한** 섹션에서 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-127">In the **DReplayController Properties** window, on the **Security** tab, click **Edit** in the **Launch and Activation Permissions** section.</span></span>  
  
    6.  <span data-ttu-id="b40e2-128">새 클라이언트 서비스 로그온 계정에 **로컬 및 원격 활성화** 권한을 부여한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-128">Grant the new client service logon account **Local and Remote activation** permissions, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="b40e2-129">**액세스 권한** 섹션에서 **편집** 을 클릭하고 새 클라이언트 서비스 로그온 계정에 **로컬 및 원격 액세스** 권한을 부여한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-129">Click **Edit** in the **Access Permissions** section, and grant the new client service logon account **Local and Remote access** permissions, and then click **OK**.</span></span>  
  
    8.  <span data-ttu-id="b40e2-130">**확인** 을 클릭하여 **DReplayController 속성** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-130">Click **OK** to close the **DReplayController Properties** window.</span></span>  
  
    9. <span data-ttu-id="b40e2-131">컨트롤러 컴퓨터에서 변경한 클라이언트 서비스 로그온 계정을 **Distributed COM Users** 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-131">On the controller computer, add the changed client service logon account to the **Distributed COM Users** group.</span></span>  
  
    10. <span data-ttu-id="b40e2-132">SQL Server Distributed Replay Controller 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-132">Start the SQL Server Distributed Replay controller service.</span></span>  
  
2.  <span data-ttu-id="b40e2-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-133">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service.</span></span>  
  
3.  <span data-ttu-id="b40e2-134">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 속성** 창의 **로그온** 탭에서 **계정 지정**을 선택하거나 **찾아보기** 를 클릭하고 새 로그온 계정을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-134">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client Properties** window, on the **Log On** tab, select **This account**, type or click **Browse** to enter the new logon account, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b40e2-135">Distributed Replay Client 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b40e2-135">Start the Distributed Replay client service.</span></span>  
  
  
