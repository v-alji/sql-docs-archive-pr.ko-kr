---
title: 구독자 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c5281a53b755bc171cdf96e7856e38ee6a54a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648917"
---
# <a name="subscribers"></a><span data-ttu-id="4c93f-102">게시자 속성</span><span class="sxs-lookup"><span data-stu-id="4c93f-102">Subscribers</span></span>
  <span data-ttu-id="4c93f-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 선택한 게시에 대 한 구독을 받을 또는 이외 구독자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-103">Specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers that will receive a subscription to the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c93f-104">옵션</span><span class="sxs-lookup"><span data-stu-id="4c93f-104">Options</span></span>  
 <span data-ttu-id="4c93f-105">**게시자 속성**</span><span class="sxs-lookup"><span data-stu-id="4c93f-105">**Subscribers**</span></span>  
 <span data-ttu-id="4c93f-106">표에서 확인란을 선택하여 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 데이터 원본을 **게시** 페이지에서 선택한 게시에 대한 구독자로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-106">Select the check box in the grid to enable the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source as a Subscriber to the publication chosen on the **Publication** page.</span></span> <span data-ttu-id="4c93f-107">구독자가 나열되어 있지 않은 경우 **구독자 추가** 또는 **SQL Server 구독자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-107">If the Subscriber is not listed, click **Add Subscriber** or **Add SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="4c93f-108">**구독 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="4c93f-108">**Subscription database**</span></span>  
 <span data-ttu-id="4c93f-109">이 열에 표시되는 정보 및 사용 가능한 동작은 **구독자** 열에 나열된 구독자 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-109">The information displayed in and actions available from this column depend on the type of Subscriber listed in the **Subscribers** column:</span></span>  
  
-   <span data-ttu-id="4c93f-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자의 경우 **구독 데이터베이스** 목록에서 구독 데이터베이스를 선택하거나 동일한 목록에서 **새 데이터베이스** 명령을 선택하여 새 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-110">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, select a subscription database from the **Subscription Database** list or create a new database by selecting the **New database** command from the same list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c93f-111">게시자를 구독자로 설정하는 경우 구독 데이터베이스가 게시 데이터베이스와 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-111">If you are enabling the Publisher as a Subscriber, the subscription database must be different from the publication database.</span></span>  
  
-   <span data-ttu-id="4c93f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자의 경우 구독 데이터베이스가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-112">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, the subscription database is not displayed.</span></span> <span data-ttu-id="4c93f-113">**SQL Server 이외 구독자 추가** 대화 상자의 **데이터 원본 이름** 필드에 데이터베이스 및 기타 연결 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-113">Specify the database, along with other connection information, in the **Data source name** field of the **Add Non-SQL Server** dialog box.</span></span> <span data-ttu-id="4c93f-114">**구독자 추가** 를 클릭한 다음 **SQL Server 이외 구독자 추가**를 클릭하여 이 대화 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-114">This dialog box is available by clicking **Add Subscriber** and then clicking **Add Non-SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="4c93f-115">**구독자 추가**</span><span class="sxs-lookup"><span data-stu-id="4c93f-115">**Add Subscriber**</span></span>  
 <span data-ttu-id="4c93f-116">구독자로 설정할 수 있는 서버 목록에 서버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-116">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="4c93f-117">이 단추는 다음 조건이 모두 충족되는 경우 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-117">This button is displayed when all of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="4c93f-118">선택한 게시가 구독 업데이트를 지원하지 않는 스냅샷 또는 트랜잭션 게시입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-118">The publication you selected is a snapshot or transactional publication that does not support updating subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c93f-119">사용자가 구독하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독 및 게시가 있는 게시를[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자가 사용할 수 없을 경우 사용자는[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-119">If the publication you are subscribing to has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscriptions and the publication is not already enabled for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, you cannot add a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscription.</span></span>  
  
-   <span data-ttu-id="4c93f-120">구독이 밀어넣기 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-120">The subscription is a push subscription.</span></span>  
  
-   <span data-ttu-id="4c93f-121">선택한 게시의 게시자가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-121">The Publisher of the selected publication is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span>  
  
 <span data-ttu-id="4c93f-122">**구독자 추가** 를 클릭하면 **SQL Server 구독자 추가** 및 **SQL Server 이외 구독자 추가**의 두 선택 사항으로 메뉴가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-122">Clicking **Add Subscriber** shows a menu with two choices: **Add SQL Server Subscriber** and **Add Non-SQL Server Subscriber**.</span></span> <span data-ttu-id="4c93f-123">Oracle 또는 IBM DB2 구독자를 추가하려면 **SQL Server 이외 구독자 추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-123">Click **Add Non-SQL Server Subscriber** to add an Oracle or IBM DB2 Subscriber.</span></span>  
  
 <span data-ttu-id="4c93f-124">**SQL Server 구독자 추가**</span><span class="sxs-lookup"><span data-stu-id="4c93f-124">**Add SQL Server Subscriber**</span></span>  
 <span data-ttu-id="4c93f-125">구독자로 설정할 수 있는 서버 목록에 서버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-125">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="4c93f-126">이 단추는 다음 조건 중 하나 이상이 충족되는 경우 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-126">This button is displayed when one or more of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="4c93f-127">선택한 게시가 병합 게시이거나 구독 업데이트를 지원하는 스냅샷 또는 트랜잭션 게시입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-127">The publication you selected is a merge publication, or a snapshot or transactional publication that supports updating subscriptions.</span></span>  
  
-   <span data-ttu-id="4c93f-128">구독이 끌어오기 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-128">The subscription is a pull subscription.</span></span>  
  
-   <span data-ttu-id="4c93f-129">선택한 게시의 게시자가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]이전 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-129">The Publisher of the selected publication is earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="4c93f-130">이전 버전의 경우 이 단추는 다음 조건 중 하나 이상이 충족되는 경우 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-130">For earlier versions, the button is displayed only if one or more of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="4c93f-131">사용자가 게시자에서 **sysadmin** 고정 서버 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-131">You are a member of the **sysadmin** fixed server role at the Publisher.</span></span>  
  
    -   <span data-ttu-id="4c93f-132">**게시자 속성** 대화 상자의 **구독자** 페이지에서 구독자가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-132">The Subscriber has been added on the **Subscribers** page of the **Publisher Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="4c93f-133">게시에서 익명 구독을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4c93f-133">The publication allows anonymous subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c93f-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c93f-134">See Also</span></span>  
 <span data-ttu-id="4c93f-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="4c93f-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="4c93f-136">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="4c93f-136">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="4c93f-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="4c93f-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="4c93f-138">게시 구독</span><span class="sxs-lookup"><span data-stu-id="4c93f-138">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
