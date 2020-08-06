---
title: '1단원: 복제용 Windows 계정 만들기 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: rothja
ms.author: jroth
ms.openlocfilehash: 29f1008338b3ba728066ed611108477586a4c899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646863"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a><span data-ttu-id="f4580-102">1단원: 복제용 Windows 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="f4580-102">Lesson 1: Creating Windows Accounts for Replication</span></span>
  <span data-ttu-id="f4580-103">이 단원에서는 복제 에이전트를 실행할 Windows 계정을 만들며</span><span class="sxs-lookup"><span data-stu-id="f4580-103">In this lesson, you will create Windows accounts to run replication agents.</span></span> <span data-ttu-id="f4580-104">다음 에이전트에 대해 로컬 서버에 별도의 Windows 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-104">You will create a separate Windows account on the local server for the following agents:</span></span>  
  
|<span data-ttu-id="f4580-105">에이전트</span><span class="sxs-lookup"><span data-stu-id="f4580-105">Agent</span></span>|<span data-ttu-id="f4580-106">위치</span><span class="sxs-lookup"><span data-stu-id="f4580-106">Location</span></span>|<span data-ttu-id="f4580-107">계정 이름</span><span class="sxs-lookup"><span data-stu-id="f4580-107">Account name</span></span>|  
|-----------|--------------|------------------|  
|<span data-ttu-id="f4580-108">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="f4580-108">Snapshot Agent</span></span>|<span data-ttu-id="f4580-109">Publisher</span><span class="sxs-lookup"><span data-stu-id="f4580-109">Publisher</span></span>|<span data-ttu-id="f4580-110">\<*machine_name*>\ repl_snapshot</span><span class="sxs-lookup"><span data-stu-id="f4580-110">\<*machine_name*>\repl_snapshot</span></span>|  
|<span data-ttu-id="f4580-111">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="f4580-111">Log Reader Agent</span></span>|<span data-ttu-id="f4580-112">Publisher</span><span class="sxs-lookup"><span data-stu-id="f4580-112">Publisher</span></span>|<span data-ttu-id="f4580-113">\<*machine_name*>\ repl_logreader</span><span class="sxs-lookup"><span data-stu-id="f4580-113">\<*machine_name*>\repl_logreader</span></span>|  
|<span data-ttu-id="f4580-114">배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="f4580-114">Distribution Agent</span></span>|<span data-ttu-id="f4580-115">게시자 및 구독자</span><span class="sxs-lookup"><span data-stu-id="f4580-115">Publisher and Subscriber</span></span>|<span data-ttu-id="f4580-116">\<*machine_name*>\ repl_distribution</span><span class="sxs-lookup"><span data-stu-id="f4580-116">\<*machine_name*>\repl_distribution</span></span>|  
|<span data-ttu-id="f4580-117">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="f4580-117">Merge Agent</span></span>|<span data-ttu-id="f4580-118">게시자 및 구독자</span><span class="sxs-lookup"><span data-stu-id="f4580-118">Publisher and Subscriber</span></span>|<span data-ttu-id="f4580-119">\<*machine_name*>\ repl_merge</span><span class="sxs-lookup"><span data-stu-id="f4580-119">\<*machine_name*>\repl_merge</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f4580-120">복제 자습서에서는 게시자 및 배포자가 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-120">In the replication tutorials, the Publisher and Distributor share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f4580-121">게시자와 구독자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 같은 인스턴스를 공유할 수 있지만 반드시 이렇게 해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-121">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="f4580-122">게시자와 구독자가 같은 인스턴스를 공유하는 경우 구독자에서는 계정을 만드는 단계를 수행하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-122">If the Publisher and Subscriber share the same instance, the steps that are used to create accounts at the Subscriber are not required.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a><span data-ttu-id="f4580-123">게시자에서 복제 에이전트에 대한 로컬 Windows 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f4580-123">To create local Windows accounts for replication agents at the Publisher</span></span>  
  
1.  <span data-ttu-id="f4580-124">게시자에서 제어판의 **관리 도구**에 있는 **컴퓨터 관리**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-124">At the Publisher, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="f4580-125">**시스템 도구**에서 **로컬 사용자 및 그룹**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-125">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="f4580-126">**사용자** 를 마우스 오른쪽 단추로 클릭 한 다음 **새 사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-126">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="f4580-127">`repl_snapshot` **사용자 이름** 상자에를 입력 하 고 암호 및 기타 관련 정보를 입력 한 다음 **만들기** 를 클릭 하 여 repl_snapshot 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-127">Enter `repl_snapshot` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_snapshot account.</span></span>  
  
5.  <span data-ttu-id="f4580-128">이전 단계를 반복하여 repl_logreader, repl_distribution 및 repl_merge 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-128">Repeat the previous step to create the repl_logreader, repl_distribution, and repl_merge accounts.</span></span>  
  
6.  <span data-ttu-id="f4580-129">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-129">Click **Close**.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a><span data-ttu-id="f4580-130">구독자에서 복제 에이전트에 대한 로컬 Windows 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f4580-130">To create local Windows accounts for replication agents at the Subscriber</span></span>  
  
1.  <span data-ttu-id="f4580-131">구독자에서 제어판의 **관리 도구**에 있는 **컴퓨터 관리**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-131">At the Subscriber, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="f4580-132">**시스템 도구**에서 **로컬 사용자 및 그룹**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-132">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="f4580-133">**사용자** 를 마우스 오른쪽 단추로 클릭 한 다음 **새 사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-133">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="f4580-134">`repl_distribution` **사용자 이름** 상자에를 입력 하 고 암호 및 기타 관련 정보를 입력 한 다음 **만들기** 를 클릭 하 여 repl_distribution 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-134">Enter `repl_distribution` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_distribution account.</span></span>  
  
5.  <span data-ttu-id="f4580-135">이전 단계를 반복하여 repl_merge 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-135">Repeat the previous step to create the repl_merge account.</span></span>  
  
6.  <span data-ttu-id="f4580-136">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-136">Click **Close**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f4580-137">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f4580-137">Next Steps</span></span>  
 <span data-ttu-id="f4580-138">복제 에이전트에 대한 Windows 계정을 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-138">You have successfully created Windows accounts for replication agents.</span></span> <span data-ttu-id="f4580-139">다음 단원에서는 스냅샷 폴더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f4580-139">Next, you will configure the snapshot folder.</span></span> <span data-ttu-id="f4580-140">[2단원: 스냅샷 폴더 준비](lesson-2-preparing-the-snapshot-folder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4580-140">See [Lesson 2: Preparing the Snapshot Folder](lesson-2-preparing-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4580-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4580-141">See Also</span></span>  
 [<span data-ttu-id="f4580-142">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="f4580-142">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
