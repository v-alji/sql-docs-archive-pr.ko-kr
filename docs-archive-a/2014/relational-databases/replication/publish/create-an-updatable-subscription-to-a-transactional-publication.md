---
title: 트랜잭션 게시에 대해 업데이트할 수 있는 구독 만들기 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741788"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a><span data-ttu-id="42f66-102">트랜잭션 게시에 업데이트할 수 있는 구독 만들기(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="42f66-102">Create an Updatable Subscription to a Transactional Publication (Management Studio)</span></span>

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
<span data-ttu-id="42f66-103">트랜잭션 복제에서는 즉시 업데이트 구독 또는 지연 업데이트 구독을 사용하여 구독자에서 변경된 내용을 게시자에 다시 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-103">Transactional replication enables changes made at a Subscriber to be propagated back to the Publisher using either immediate or queued updating subscriptions.</span></span> <span data-ttu-id="42f66-104">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 업데이트 구독을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-104">You can create an updating subscription programmatically using replication stored procedures.</span></span>

<span data-ttu-id="42f66-105">**새 구독 마법사**의 **업데이트할 수 있는 구독** 페이지에서 업데이트할 수 있는 구독을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-105">Configure updatable subscriptions on the **Updatable Subscriptions** page of the **New Subscription Wizard**.</span></span> <span data-ttu-id="42f66-106">이 페이지는 업데이트할 수 있는 구독에 대해 트랜잭션 게시를 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-106">This page is only available if you have enabled a transactional publication for updatable subscriptions.</span></span> <span data-ttu-id="42f66-107">업데이트할 수 있는 구독을 사용하도록 설정하는 방법에 대한 자세한 내용은 [트랜잭션 게시에 대해 업데이트할 수 있는 구독 설정](enable-updating-subscriptions-for-transactional-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-107">For more information about enabling updatable subscriptions, see [Enable Updating Subscriptions for Transactional Publications](enable-updating-subscriptions-for-transactional-publications.md).</span></span>   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a><span data-ttu-id="42f66-108">게시자에서 업데이트할 수 있는 구독 구성</span><span class="sxs-lookup"><span data-stu-id="42f66-108">Configure an updatable subscription from the Publisher</span></span>  

1. <span data-ttu-id="42f66-109">Microsoft SQL Server Management Studio에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-109">Connect to the Publisher in Microsoft SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="42f66-110">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-110">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>
3. <span data-ttu-id="42f66-111">구독 업데이트에 대해 설정된 트랜잭션 게시를 마우스 오른쪽 단추로 클릭한 다음 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-111">Right-click a transactional publication enabled for updating subscriptions, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="42f66-112">마법사의 페이지에 따라 배포 에이전트의 실행 위치 같은 구독 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-112">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
5. <span data-ttu-id="42f66-113">**새 구독 마법사**의 **업데이트할 수 있는 구독** 페이지에서 **복제**가 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-113">On the **Updatable Subscriptions** page of the **New Subscription Wizard**, ensure **Replicate** is selected.</span></span>
6. <span data-ttu-id="42f66-114">**게시자에서 커밋** 드롭다운 목록에서 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-114">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    *  <span data-ttu-id="42f66-115">즉시 업데이트 구독을 사용하려면 **동시에 변경 내용 커밋**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-115">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="42f66-116">이 옵션을 선택하고 게시에서 지연 업데이트 구독을 허용하면(새 게시 마법사로 만든 게시의 기본 설정) 구독 속성 **update_mode**가 **failover**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-116">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="42f66-117">이 모드에서는 필요하면 나중에 지연 업데이트로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-117">This mode allows you to switch to queued updating later if necessary.</span></span>
    *  <span data-ttu-id="42f66-118">지연 업데이트 구독을 사용하려면 **변경 내용 대기 및 가능 시 커밋**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-118">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="42f66-119">이 옵션을 선택하고 게시에서 즉시 업데이트 구독을 허용하며(새 게시 마법사로 만든 게시의 기본 설정) 구독자에서 SQL Server 2005 이상 버전이 실행될 경우 구독 속성 **update_mode**가 queued failover로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-119">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued failover.</span></span> <span data-ttu-id="42f66-120">이 모드에서는 나중에 필요에 맞게 즉시 업데이트로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-120">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="42f66-121">업데이트 모드를 전환하는 방법에 대한 자세한 내용은 [업데이트 가능한 트랜잭션 구독에 대한 업데이트 모드 전환](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-121">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

7. <span data-ttu-id="42f66-122">즉시 업데이트를 사용하거나 **update_mode**가 **queued failover**로 설정된 구독에 대해 **업데이트할 수 있는 구독에 대한 로그인** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-122">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to **queued failover**.</span></span> <span data-ttu-id="42f66-123">**업데이트할 수 있는 구독에 대한 로그인** 페이지에서 즉시 업데이트 구독을 위해 게시자로의 연결이 설정된 연결된 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-123">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="42f66-124">이 연결은 구독자에서 발생되는 트리거에 사용되고 게시자로 변경 내용을 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-124">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="42f66-125">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-125">Select one of the following options:</span></span>

    * <span data-ttu-id="42f66-126">**다음 SQL Server 인증을 사용하여 연결되는 연결된 서버 만들기.**</span><span class="sxs-lookup"><span data-stu-id="42f66-126">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="42f66-127">구독자와 게시자 간에 원격 서버 또는 연결된 서버를 정의하지 않은 경우 이 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-127">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="42f66-128">복제 시 연결된 서버가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-128">Replication creates a linked server for you.</span></span> <span data-ttu-id="42f66-129">지정한 계정은 게시자에 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-129">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="42f66-130">**이미 정의한 연결된 서버나 원격 서버 사용**</span><span class="sxs-lookup"><span data-stu-id="42f66-130">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="42f66-131">[sp_addserver(Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver(Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio 또는 다른 메서드를 사용하여 구독자와 게시자 간에 원격 서버 또는 연결된 서버를 정의한 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-131">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="42f66-132">연결된 서버 계정에 필요한 사용 권한에 대한 자세한 내용은 [여기에 링크 설명 입력](../security/secure-the-subscriber.md)의 **지연 업데이트 구독**을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-132">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

8. <span data-ttu-id="42f66-133">마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-133">Complete the wizard.</span></span>

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a><span data-ttu-id="42f66-134">구독자에서 업데이트할 수 있는 구독 구성</span><span class="sxs-lookup"><span data-stu-id="42f66-134">Configure an updatable subscription from the Subscriber</span></span>


1. <span data-ttu-id="42f66-135">SQL Server Management Studio에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-135">Connect to the Subscriber in SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="42f66-136">**복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-136">Expand the **Replication** folder.</span></span>
3. <span data-ttu-id="42f66-137">**로컬 구독** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-137">Right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="42f66-138">**새 구독 마법사**의 **게시** 페이지에 있는 **게시자** 드롭다운 목록에서 **SQL Server 게시자 찾기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-138">On the **Publication** page of the **New Subscription Wizard**, select **Find SQL Server Publisher** from the **Publisher** drop-down list.</span></span>
5. <span data-ttu-id="42f66-139">**서버에 연결** 대화 상자에서 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-139">Connect to the Publisher in the **Connect to Server** dialog box.</span></span>
6. <span data-ttu-id="42f66-140">**게시** 페이지에서 구독 업데이트에 대해 설정된 트랜잭션 게시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-140">Select a transactional publication enabled for updating subscriptions on the **Publication** page.</span></span>
7. <span data-ttu-id="42f66-141">마법사의 페이지에 따라 배포 에이전트의 실행 위치 같은 구독 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-141">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
8. <span data-ttu-id="42f66-142">새 구독 마법사의 **업데이트할 수 있는 구독** 페이지에서 **복제**가 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-142">On the **Updatable Subscriptions** page of the New Subscription Wizard, ensure **Replicate** is selected.</span></span>
9. <span data-ttu-id="42f66-143">**게시자에서 커밋** 드롭다운 목록에서 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-143">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    * <span data-ttu-id="42f66-144">즉시 업데이트 구독을 사용하려면 **동시에 변경 내용 커밋**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-144">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="42f66-145">이 옵션을 선택하고 게시에서 지연 업데이트 구독을 허용하면(새 게시 마법사로 만든 게시의 기본 설정) 구독 속성 **update_mode**가 **failover**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-145">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="42f66-146">이 모드에서는 필요하면 나중에 지연 업데이트로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-146">This mode allows you to switch to queued updating later if necessary.</span></span>
    * <span data-ttu-id="42f66-147">지연 업데이트 구독을 사용하려면 **변경 내용 대기 및 가능 시 커밋**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-147">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="42f66-148">이 옵션을 선택하고 게시에서 즉시 업데이트 구독을 허용하며(새 게시 마법사로 만든 게시의 기본 설정) 구독자에서 SQL Server 2005 이상 버전이 실행될 경우 구독 속성 **update_mode**가 queued **failover**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-148">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued **failover**.</span></span> <span data-ttu-id="42f66-149">이 모드에서는 나중에 필요에 맞게 즉시 업데이트로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-149">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="42f66-150">업데이트 모드를 전환하는 방법에 대한 자세한 내용은 [업데이트 가능한 트랜잭션 구독에 대한 업데이트 모드 전환](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-150">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

10. <span data-ttu-id="42f66-151">즉시 업데이트를 사용하거나 **update_mode**가 **queued failover**로 설정된 구독에 대해 **업데이트할 수 있는 구독에 대한 로그인** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-151">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to queued **failover**.</span></span> <span data-ttu-id="42f66-152">**업데이트할 수 있는 구독에 대한 로그인** 페이지에서 즉시 업데이트 구독을 위해 게시자로의 연결이 설정된 연결된 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-152">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="42f66-153">이 연결은 구독자에서 발생되는 트리거에 사용되고 게시자로 변경 내용을 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-153">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="42f66-154">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-154">Select one of the following options:</span></span>

    * <span data-ttu-id="42f66-155">**다음 SQL Server 인증을 사용하여 연결되는 연결된 서버 만들기.**</span><span class="sxs-lookup"><span data-stu-id="42f66-155">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="42f66-156">구독자와 게시자 간에 원격 서버 또는 연결된 서버를 정의하지 않은 경우 이 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-156">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="42f66-157">복제 시 연결된 서버가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-157">Replication creates a linked server for you.</span></span> <span data-ttu-id="42f66-158">지정한 계정은 게시자에 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-158">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="42f66-159">**이미 정의한 연결된 서버나 원격 서버 사용**</span><span class="sxs-lookup"><span data-stu-id="42f66-159">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="42f66-160">[sp_addserver(Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver(Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio 또는 다른 메서드를 사용하여 구독자와 게시자 간에 원격 서버 또는 연결된 서버를 정의한 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-160">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="42f66-161">연결된 서버 계정에 필요한 사용 권한에 대한 자세한 내용은 [여기에 링크 설명 입력](../security/secure-the-subscriber.md)의 **지연 업데이트 구독**을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-161">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

11. <span data-ttu-id="42f66-162">마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-162">Complete the wizard.</span></span>

## <a name="create-an-immediate-updating-pull-subscription"></a><span data-ttu-id="42f66-163">즉시 업데이트 끌어오기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="42f66-163">Create an immediate updating pull subscription</span></span>

1. <span data-ttu-id="42f66-164">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 즉시 업데이트 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-164">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-165">결과 집합의 `allow_sync_tran` 값이 `1`이면 게시는 즉시 업데이트 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-165">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="42f66-166">결과 집합의 `allow_sync_tran` 값이 `0`이면 즉시 업데이트 구독을 설정하여 게시를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-166">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="42f66-167">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 끌어오기 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-167">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-168">결과 집합의 `allow_pull` 값이 `1`이면 게시에서 끌어오기 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-168">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="42f66-169">`allow_pull` 값이 `0`이면 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행하여 `allow_pull` 에 대해 `@property` 을, `true` 에 대해 `@value`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-169">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="42f66-170">구독자에서 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-170">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="42f66-171">`@publisher` 및 `@publication`를 지정하고 `@update_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-171">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="42f66-172">`sync tran` - 구독에서 즉시 업데이트를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-172">`sync tran` - enables the subscription for immediate updating.</span></span>
    * <span data-ttu-id="42f66-173">`failover` - 즉시 업데이트 구독을 사용하고 지연 업데이트를 장애 조치(Failover) 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-173">`failover` - enables the subscription for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="42f66-174">`failover` 를 사용하려면 게시에서 지연 업데이트 구독도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-174">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="42f66-175">구독자에서 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-175">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="42f66-176">다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-176">Specify the following:</span></span>

    * <span data-ttu-id="42f66-177">`@publisher`, `@publisher_db`및 `@publication` 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="42f66-177">The `@publisher`, `@publisher_db`, and `@publication` parameters.</span></span> 
    * <span data-ttu-id="42f66-178">`@job_login` 및 `@job_password`에 대해 구독자에서 배포 에이전트가 실행되는 Microsoft Windows 자격 증명.</span><span class="sxs-lookup"><span data-stu-id="42f66-178">The Microsoft Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="42f66-179">Windows 통합 인증을 사용하여 만든 연결은 항상 `@job_login` 및 `@job_password`로 지정한 Windows 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-179">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="42f66-180">배포 에이전트는 항상 Windows 통합 인증을 사용하여 구독자에 대한 로컬 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-180">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="42f66-181">기본적으로 에이전트는 Windows 통합 인증을 사용하여 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-181">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="42f66-182">(선택 사항) `0` 에 대한 `@distributor_security_mode` 값과, `@distributor_login` 및 `@distributor_password`에 대한 Microsoft SQL Server 로그인 정보(배포자에 연결할 때 SQL Server 인증을 사용 해야하는 경우).</span><span class="sxs-lookup"><span data-stu-id="42f66-182">(Optional) A value of `0` for `@distributor_security_mode` and the Microsoft SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="42f66-183">이 구독에 대한 배포 에이전트 작업 일정.</span><span class="sxs-lookup"><span data-stu-id="42f66-183">A schedule for the Distribution Agent job for this subscription.</span></span> 

5. <span data-ttu-id="42f66-184">구독 데이터베이스의 구독자에서 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-184">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="42f66-185">`@publisher`, `@publication`그리고 `@publisher_db`에 대한 게시 데이터베이스 이름을 지정하고 `@security_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-185">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

    * <span data-ttu-id="42f66-186">`0` - 게시자에서 업데이트할 때 SQL Server 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-186">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="42f66-187">이 옵션을 사용하려면 `@login` 및 `@password`에 대해 게시자에 유효한 로그인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-187">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
    * <span data-ttu-id="42f66-188">`1` - 게시자에 연결할 때 구독자에서 변경 작업을 수행하는 사용자의 보안 컨텍스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-188">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="42f66-189">이 보안 모드에 관한 제한 사항에 대해서는 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-189">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
    * <span data-ttu-id="42f66-190">`2`[sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 사용하여 만든 기존의 사용자 정의 연결된 서버 로그인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-190">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>

6. <span data-ttu-id="42f66-191">게시자에서 [,](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) , `@publication`를 지정하고 `@subscriber`에 대한 가져오기 값, `@destination_db`에 대해 3단계에서 지정한 동일한 값을 지정하여 `@subscription_type`sp_addsubscription `@update_mode`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-191">At the publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="42f66-192">이렇게 하면 게시자에서 끌어오기 구독이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-192">This registers the pull subscription at the Publisher.</span></span> 


## <a name="create-an-immediate-updating-push-subscription"></a><span data-ttu-id="42f66-193">즉시 업데이트 밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="42f66-193">Create an immediate updating push subscription</span></span> 

1. <span data-ttu-id="42f66-194">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 즉시 업데이트 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-194">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-195">결과 집합의 `allow_sync_tran` 값이 `1`이면 게시는 즉시 업데이트 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-195">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="42f66-196">결과 집합의 `allow_sync_tran` 값이 `0`이면 즉시 업데이트 구독을 설정하여 게시를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-196">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="42f66-197">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 밀어넣기 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-197">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-198">결과 집합의 `allow_push` 값이 `1`이면 게시에서 밀어넣기 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-198">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="42f66-199">`allow_push` 값이 `0`이면 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행하여 `allow_push` 에 대해 `@property` 을, `true` 에 대해 `@value`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-199">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_push` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="42f66-200">게시자에서 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-200">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="42f66-201">`@publication`, `@subscriber`, `@destination_db`를 지정하고 `@update_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-201">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="42f66-202">`sync tran` - 즉시 업데이트 지원을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-202">`sync tran` - enables support for immediate updating.</span></span>
    * <span data-ttu-id="42f66-203">`failover` - 즉시 업데이트 지원을 설정하고 지연 업데이트를 장애 조치 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-203">`failover` - enables support for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="42f66-204">`failover` 를 사용하려면 게시에서 지연 업데이트 구독도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-204">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="42f66-205">게시자에서 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-205">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="42f66-206">다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-206">Specify the following parameters:</span></span>

    * <span data-ttu-id="42f66-207">`@subscriber`, `@subscriber_db`및 `@publication`.</span><span class="sxs-lookup"><span data-stu-id="42f66-207">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="42f66-208">`@job_login` 및 `@job_password`에 대해 배포자에서 배포 에이전트가 실행되는 Windows 자격 증명</span><span class="sxs-lookup"><span data-stu-id="42f66-208">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="42f66-209">Windows 통합 인증을 사용하여 만든 연결은 항상 `@job_login` 및 `@job_password`로 지정한 Windows 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-209">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="42f66-210">배포 에이전트는 항상 Windows 통합 인증을 사용하여 배포자에 대한 로컬 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-210">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="42f66-211">기본적으로 에이전트는 Windows 통합 인증을 사용하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-211">By default, the agent will connect to the Subscriber using Windows Integrated Authentication.</span></span> 

    * <span data-ttu-id="42f66-212">(선택 사항) `0` 에 대한 `@subscriber_security_mode` 값과, `@subscriber_login` 및 `@subscriber_password`에 대한 SQL Server 로그인 정보(구독자에 연결할 때 SQL Server 인증을 사용 해야하는 경우).</span><span class="sxs-lookup"><span data-stu-id="42f66-212">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="42f66-213">이 구독에 대한 배포 에이전트 작업 일정.</span><span class="sxs-lookup"><span data-stu-id="42f66-213">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="42f66-214">구독 데이터베이스의 구독자에서 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-214">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="42f66-215">`@publisher`, `@publication`그리고 `@publisher_db`에 대한 게시 데이터베이스 이름을 지정하고 `@security_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-215">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

     * <span data-ttu-id="42f66-216">`0` - 게시자에서 업데이트할 때 SQL Server 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-216">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="42f66-217">이 옵션을 사용하려면 `@login` 및 `@password`에 대해 게시자에 유효한 로그인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-217">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
     * <span data-ttu-id="42f66-218">`1` - 게시자에 연결할 때 구독자에서 변경 작업을 수행하는 사용자의 보안 컨텍스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-218">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="42f66-219">이 보안 모드에 관한 제한 사항에 대해서는 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-219">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
     * <span data-ttu-id="42f66-220">`2`[sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 사용하여 만든 기존의 사용자 정의 연결된 서버 로그인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-220">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>


## <a name="create-a-queued-updating-pull-subscription"></a><span data-ttu-id="42f66-221">지연 업데이트 끌어오기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="42f66-221">Create a queued updating pull subscription</span></span> ##

1. <span data-ttu-id="42f66-222">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 지연 업데이트 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-222">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-223">결과 집합의 `allow_queued_tran` 값이 `1`이면 게시는 즉시 업데이트 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-223">If the value of `allow_queued_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="42f66-224">결과 집합의 `allow_queued_tran` 값이 `0`이면 지연 업데이트 구독을 설정하여 게시를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-224">If the value of `allow_queued_tran` in the result set is `0`, the publication must be recreated with queued updating subscriptions enabled.</span></span>

2. <span data-ttu-id="42f66-225">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 끌어오기 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-225">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-226">결과 집합의 `allow_pull` 값이 `1`이면 게시에서 끌어오기 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-226">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="42f66-227">`allow_pull` 값이 `0`이면 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행하여 `allow_pull` 에 대해 `@property` 을, `true` 에 대해 `@value`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-227">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="42f66-228">구독자에서 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-228">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="42f66-229">`@publisher` 및 `@publication`를 지정하고 `@update_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-229">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="42f66-230">`queued tran` - 지연 업데이트 구독을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-230">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="42f66-231">`queued failover` - 지연 업데이트 지원을 설정하고 즉시 업데이트를 장애 조치 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-231">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="42f66-232">`queued failover` 를 사용하려면 게시에서 즉시 업데이트 구독도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-232">`queued failover` requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="42f66-233">즉시 업데이트로 장애 조치를 수행하려면 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 을 사용하여 구독자의 변경 내용을 게시자에 복제할 때 사용할 자격 증명을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-233">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>
 
4. <span data-ttu-id="42f66-234">구독자에서 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-234">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="42f66-235">다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-235">Specify the following parameters:</span></span>

    * <span data-ttu-id="42f66-236">@publisher, `@publisher_db`및 `@publication`.</span><span class="sxs-lookup"><span data-stu-id="42f66-236">@publisher, `@publisher_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="42f66-237">`@job_login` 및 `@job_password`에 대해 구독자에서 배포 에이전트가 실행되는 Windows 자격 증명</span><span class="sxs-lookup"><span data-stu-id="42f66-237">The Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="42f66-238">Windows 통합 인증을 사용하여 만든 연결은 항상 `@job_login` 및 `@job_password`로 지정한 Windows 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-238">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="42f66-239">배포 에이전트는 항상 Windows 통합 인증을 사용하여 구독자에 대한 로컬 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-239">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="42f66-240">기본적으로 에이전트는 Windows 통합 인증을 사용하여 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-240">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="42f66-241">(선택 사항) `0` 에 대한 `@distributor_security_mode` 값과, `@distributor_login` 및 `@distributor_password`에 대한 SQL Server 로그인 정보(배포자에 연결할 때 SQL Server 인증을 사용 해야하는 경우).</span><span class="sxs-lookup"><span data-stu-id="42f66-241">(Optional) A value of `0` for `@distributor_security_mode` and the SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="42f66-242">이 구독에 대한 배포 에이전트 작업 일정.</span><span class="sxs-lookup"><span data-stu-id="42f66-242">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="42f66-243">게시자에서 [,](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) , `@publication`를 지정하고 `@subscriber`에 대한 가져오기 값, `@destination_db`에 대해 3단계에서 지정한 동일한 값을 지정하여 `@subscription_type`sp_addsubscription `@update_mode`을 실행하고 게시자에서 구독자를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-243">At the publisher, execute [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) to register the Subscriber at the Publisher, specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="42f66-244">이렇게 하면 게시자에서 끌어오기 구독이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-244">This registers the pull subscription at the Publisher.</span></span> 


## <a name="to-create-a-queued-updating-push-subscription"></a><span data-ttu-id="42f66-245">지연 업데이트 밀어넣기 구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f66-245">To create a queued updating push subscription</span></span> ##

1. <span data-ttu-id="42f66-246">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 지연 업데이트 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-246">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-247">결과 집합의 allow_queued_tran 값이 1이면 게시는 즉시 업데이트 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-247">If the value of allow_queued_tran in the result set is 1, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="42f66-248">결과 집합의 allow_queued_tran 값이 0이면 지연 업데이트 구독을 설정하여 게시를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-248">If the value of allow_queued_tran in the result set is 0, the publication must be recreated with queued updating subscriptions enabled.</span></span> <span data-ttu-id="42f66-249">자세한 내용은 방법: 트랜잭션 게시에 대한 구독 업데이트를 설정합니다(복제 Transact-SQL 프로그래밍).</span><span class="sxs-lookup"><span data-stu-id="42f66-249">For more information, see How to: Enable Updating Subscriptions for Transactional Publications (Replication Transact-SQL Programming).</span></span>

2. <span data-ttu-id="42f66-250">게시자에서 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시에서 밀어넣기 구독을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-250">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="42f66-251">결과 집합의 `allow_push` 값이 `1`이면 게시에서 밀어넣기 구독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-251">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="42f66-252">`allow_push` 값이 `0`이면 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행하여 `@property` 에 대해 allow_push를, `true` 에 대해 `@value`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-252">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying allow_push for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="42f66-253">게시자에서 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-253">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="42f66-254">`@publication`, `@subscriber`, `@destination_db`를 지정하고 `@update_mode`에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-254">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="42f66-255">`queued tran` - 지연 업데이트 구독을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-255">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="42f66-256">`queued failover` - 지연 업데이트 지원을 설정하고 즉시 업데이트를 장애 조치 옵션으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-256">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="42f66-257">queued failover 옵션을 사용하려면 게시에서 즉시 업데이트 구독도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-257">The queued failover option requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="42f66-258">즉시 업데이트로 장애 조치를 수행하려면 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 을 사용하여 구독자의 변경 내용을 게시자에 복제할 때 사용할 자격 증명을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-258">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>

4. <span data-ttu-id="42f66-259">게시자에서 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-259">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="42f66-260">다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-260">Specify the following parameters:</span></span>

    * <span data-ttu-id="42f66-261">`@subscriber`, `@subscriber_db`및 `@publication`.</span><span class="sxs-lookup"><span data-stu-id="42f66-261">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="42f66-262">`@job_login` 및 `@job_password`에 대해 배포자에서 배포 에이전트가 실행되는 Windows 자격 증명</span><span class="sxs-lookup"><span data-stu-id="42f66-262">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="42f66-263">Windows 통합 인증을 사용하여 만든 연결은 항상 `@job_login` 및 `@job_password`로 지정한 Windows 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-263">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="42f66-264">배포 에이전트는 항상 Windows 통합 인증을 사용하여 배포자에 대한 로컬 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-264">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="42f66-265">기본적으로 에이전트는 Windows 통합 인증을 사용하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-265">By default, the agent connects to the Subscriber using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="42f66-266">(선택 사항) `0` 에 대한 `@subscriber_security_mode` 값과, `@subscriber_login` 및 `@subscriber_password`에 대한 SQL Server 로그인 정보(구독자에 연결할 때 SQL Server 인증을 사용 해야하는 경우).</span><span class="sxs-lookup"><span data-stu-id="42f66-266">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="42f66-267">이 구독에 대한 배포 에이전트 작업 일정.</span><span class="sxs-lookup"><span data-stu-id="42f66-267">A schedule for the Distribution Agent job for this subscription.</span></span>


## <a name="example"></a><span data-ttu-id="42f66-268">예제</span><span class="sxs-lookup"><span data-stu-id="42f66-268">Example</span></span> ##

<span data-ttu-id="42f66-269">이 예에서는 즉시 업데이트 구독을 지원하는 게시에 대해 즉시 업데이트 끌어오기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-269">This example creates an immediate updating pull subscription to a publication that supports immediate updating subscriptions.</span></span> <span data-ttu-id="42f66-270">로그인 및 암호 값은 sqlcmd 스크립팅 변수를 사용하여 런타임에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-270">Login and password values are supplied at runtime using sqlcmd scripting variables.</span></span>

> [!NOTE]  
>  <span data-ttu-id="42f66-271">이 스크립트는 sqlcmd 스크립팅 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-271">This script uses sqlcmd scripting variables.</span></span> <span data-ttu-id="42f66-272">형식은 `$(MyVariable)`입니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-272">They are in the form `$(MyVariable)`.</span></span> <span data-ttu-id="42f66-273">SQL Server Management Studio와 명령줄에서 스크립팅 변수를 사용하는 방법에 대한 내용은 **복제 시스템 저장 프로시저 개념** 항목의 [복제 스크립트 실행](../concepts/replication-system-stored-procedures-concepts.md)섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-273">For information about how to use scripting variables on the command line and in SQL Server Management Studio, see the **Executing Replication Scripts** section in the topic [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md).</span></span>

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a><span data-ttu-id="42f66-274">지연 업데이트 충돌 해결 옵션 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="42f66-274">Set Queued Updating Conflict Resolution Options (SQL Server Management Studio)</span></span>
  <span data-ttu-id="42f66-275">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 지연 업데이트 구독을 지원하는 게시에 대한 충돌 해결 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-275">Set conflict resolution options for publications that support queued updating subscriptions on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="42f66-276">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f66-276">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a><span data-ttu-id="42f66-277">지연 업데이트 충돌 해결 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="42f66-277">To set queued updating conflict resolution options</span></span>  
  
1.  <span data-ttu-id="42f66-278">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 **충돌 해결 정책** 옵션에 대해 다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f66-278">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select one of the following values for the **Conflict resolution policy** option:</span></span>    
    -   <span data-ttu-id="42f66-279">**게시자 변경 내용 유지**</span><span class="sxs-lookup"><span data-stu-id="42f66-279">**Keep the Publisher change**</span></span>    
    -   <span data-ttu-id="42f66-280">**구독자 변경 내용 유지**</span><span class="sxs-lookup"><span data-stu-id="42f66-280">**Keep the Subscriber change**</span></span>    
    -   <span data-ttu-id="42f66-281">**구독 다시 초기화**</span><span class="sxs-lookup"><span data-stu-id="42f66-281">**Reinitialize the subscription**</span></span>    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a><span data-ttu-id="42f66-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42f66-282">See Also</span></span> ##
 <span data-ttu-id="42f66-283">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="42f66-283">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="42f66-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="42f66-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="42f66-285">스크립팅 변수와 함께 sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="42f66-285">Use sqlcmd with Scripting Variables</span></span>](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
