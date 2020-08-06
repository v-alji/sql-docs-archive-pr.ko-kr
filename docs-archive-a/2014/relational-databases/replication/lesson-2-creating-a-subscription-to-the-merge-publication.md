---
title: '2단원: 병합 게시에 대한 구독 만들기 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ca4f9cdf9c40d80b428d65b4201be61c2ea3eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652068"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a><span data-ttu-id="adabe-102">2단원: 병합 게시에 대한 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="adabe-102">Lesson 2: Creating a Subscription to the Merge Publication</span></span>
  <span data-ttu-id="adabe-103">이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-103">In this lesson, you will create the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="adabe-104">그런 다음 구독 데이터베이스에 대한 사용 권한을 설정하고 새 구독에 대한 필터링된 데이터 스냅샷을 수동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-104">You will then set permissions on the subscription database and manually generate the filtered data snapshot for the new subscription.</span></span> <span data-ttu-id="adabe-105">이 단원을 수행하려면 이전 단원인 [1단원: 병합 복제를 사용하여 데이터 게시](lesson-1-publishing-data-using-merge-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-105">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Merge Replication](lesson-1-publishing-data-using-merge-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="adabe-106">구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="adabe-106">To create the subscription</span></span>  
  
1.  <span data-ttu-id="adabe-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결하여 해당 서버 노드와 **복제** 폴더를 확장하고 **로컬 구독** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, expand the **Replication** folder, right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="adabe-108">새 구독 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-108">The New Subscription Wizard launches.</span></span>  
  
2.  <span data-ttu-id="adabe-109">**게시** 페이지에서 **게시자** 목록에 있는 **SQL Server 게시자 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-109">On the **Publication** page, click **Find SQL Server Publisher** in the **Publisher** list.</span></span>  
  
3.  <span data-ttu-id="adabe-110">**서버에 연결** 대화 상자에서 **서버 이름** 상자에 게시자 인스턴스의 이름을 입력하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-110">In the **Connect to Server** dialog box, enter the name of the Publisher instance in the **Server name** box, and click **Connect**.</span></span>  
  
4.  <span data-ttu-id="adabe-111">**AdvWorksSalesOrdersMerge**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-111">Click **AdvWorksSalesOrdersMerge**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="adabe-112">병합 에이전트 위치 페이지에서 **각 에이전트를 해당 구독자에서 실행**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-112">On the Merge Agent Location page, click **Run each agent at its Subscriber**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="adabe-113">구독자 페이지에서 구독자 서버의 인스턴스 이름을 선택하고 **구독 데이터베이스**의 목록에서 **\<New Database>** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-113">On the Subscribers page, select the instance name of the Subscriber server, and under **Subscription Database**, select **\<New Database>** from the list.</span></span>  
  
7.  <span data-ttu-id="adabe-114">**새 데이터베이스** 대화 상자에서 **데이터베이스 이름** 상자에 **SalesOrdersReplica** 를 입력하고 **확인**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-114">In the **New Database** dialog box, enter **SalesOrdersReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="adabe-115">병합 에이전트 보안 페이지에서 줄임표 (**...**) 단추를 클릭 하 고 \<_Machine_Name> **프로세스 계정** 상자에 _**\ repl_merge** 를 입력 한 다음이 계정에 대 한 암호를 입력 하 고 **확인**, **다음**을 차례로 클릭 한 후 **다음** 을 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-115">On the Merge Agent Security page, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_merge** in the **Process account** box, supply the password for this account, click **OK**, click **Next**, and then click **Next** again.</span></span>  
  
9. <span data-ttu-id="adabe-116">구독 초기화 페이지의 **초기화 시기** 목록에서 **첫 번째 동기화 시** 를 선택하고 **다음**을 클릭한 후 다시 **다음** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-116">On the Initialize Subscriptions page, select **At first synchronization** from the **Initialize When** list, click **Next**, and then click **Next** again.</span></span>  
  
10. <span data-ttu-id="adabe-117">HOST_NAME 값 페이지에서 `adventure-works\pamela0` **HOST_NAME 값** 상자에 값을 입력 한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-117">On the HOST_NAME Values page, enter a value of `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="adabe-118">**마침** 을 다시 클릭하고 구독이 생성되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-118">Click **Finish** again, and after the subscription is created, click **Close**.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="adabe-119">구독자에서 데이터베이스 권한 설정</span><span class="sxs-lookup"><span data-stu-id="adabe-119">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="adabe-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결하고 **데이터베이스**, **SalesOrdersReplica**및 **보안**을 확장하고 **사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **SalesOrdersReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="adabe-121">**일반** 페이지에서 \<_Machine_Name> _ **사용자 이름** 상자에 **\ repl_merge** 를 입력 하 고 줄임표 (**...**) 단추를 클릭 한 다음 **찾아보기**를 \<_Machine_Name> _클릭 하 고, **\ repl_merge**를 선택 하 고, **확인**을 클릭 하 고, **이름 확인**을 클릭 한 후 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-121">On the **General** page, enter \<_Machine_Name>_**\repl_merge** in the **User name** box, click the ellipsis (**...**) button, click **Browse**, select \<_Machine_Name>_**\repl_merge**, click **OK**, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="adabe-122">**데이터베이스 역할 멤버 자격**에서 **db_owner**를 선택한 다음 **확인** 을 클릭하여 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-122">In **Database role membership**, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a><span data-ttu-id="adabe-123">구독에 대한 필터링된 데이터 스냅샷을 만들려면</span><span class="sxs-lookup"><span data-stu-id="adabe-123">To create the filtered data snapshot for the subscription</span></span>  
  
1.  <span data-ttu-id="adabe-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="adabe-125">**로컬 게시** 폴더에서 **AdvWorksSalesOrdersMerge** 게시를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-125">In the **Local Publications** folder, right-click the **AdvWorksSalesOrdersMerge** publication, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="adabe-126">**게시 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-126">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="adabe-127">**데이터 파티션** 페이지를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-127">Select the **Data Partitions** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="adabe-128">**데이터 파티션 추가** 대화 상자에서 `adventure-works\pamela0` **HOST_NAME 값** 상자에를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-128">In the **Add Data Partition** dialog box, type `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="adabe-129">새로 추가된 파티션을 선택하고 **선택한 스냅샷 지금 생성**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-129">Select the newly added partition, click **Generate the selected snapshots now**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="adabe-130">다음 단계</span><span class="sxs-lookup"><span data-stu-id="adabe-130">Next Steps</span></span>  
 <span data-ttu-id="adabe-131">구독이 초기화되면 사용할 수 있도록 병합 게시에 대한 구독을 만들고 새 구독의 데이터 파티션에 대한 필터링된 스냅샷을 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-131">You have successfully created a subscription to the merge publication and generated the filtered snapshot for the new subscription's data partition so that it will be available when the subscription is initialized.</span></span> <span data-ttu-id="adabe-132">다음 단원에서는 병합 에이전트에 구독 데이터베이스에 대한 권한을 부여하고 병합 에이전트를 실행하여 동기화를 시작하고 구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="adabe-132">Next, you will grant rights to the Merge Agent on the subscription database and run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="adabe-133">[3단원: 병합 게시에 구독 동기화](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="adabe-133">See [Lesson 3: Synchronizing the Subscription to the Merge Publication](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adabe-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adabe-134">See Also</span></span>  
 <span data-ttu-id="adabe-135">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="adabe-135">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="adabe-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="adabe-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="adabe-137">매개 변수가 있는 필터를 사용하는 병합 게시의 스냅샷</span><span class="sxs-lookup"><span data-stu-id="adabe-137">Snapshots for Merge Publications with Parameterized Filters</span></span>](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
