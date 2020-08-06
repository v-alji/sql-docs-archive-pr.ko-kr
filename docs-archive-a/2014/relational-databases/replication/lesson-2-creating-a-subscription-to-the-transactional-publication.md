---
title: '2단원: 트랜잭션 게시에 구독 만들기 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: rothja
ms.author: jroth
ms.openlocfilehash: dbf40fa259302dffdd6c0b8e8717b7c35b0cf92d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646862"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a><span data-ttu-id="30cb5-102">2단원: 트랜잭션 게시에 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="30cb5-102">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>
  <span data-ttu-id="30cb5-103">이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-103">In this lesson, you will create a subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="30cb5-104">이 단원을 수행하려면 이전 단원인 [1단원: 트랜잭션 복제를 사용하여 데이터 게시](lesson-1-publishing-data-using-transactional-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-104">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Transactional Replication](lesson-1-publishing-data-using-transactional-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="30cb5-105">구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="30cb5-105">To create the subscription</span></span>  
  
1.  <span data-ttu-id="30cb5-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="30cb5-107">**로컬 게시** 폴더에서 **AdvWorksProductTrans** 게시를 마우스 오른쪽 단추로 클릭한 다음 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-107">In the **Local Publications** folder, right-click the **AdvWorksProductTrans** publication, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="30cb5-108">새 구독 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-108">The New Subscription Wizard launches.</span></span>  
  
3.  <span data-ttu-id="30cb5-109">게시 페이지에서 **AdvWorksProductTrans**를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-109">On the Publication page, select **AdvWorksProductTrans**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="30cb5-110">배포 에이전트 위치 페이지에서 **배포자에서 모든 에이전트 실행**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-110">On the Distribution Agent Location page, select **Run all agents at the Distributor**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="30cb5-111">구독자 페이지에서 구독자 인스턴스 이름이 표시되지 않는 경우 **구독자 추가**, **SQL Server 구독자 추가**를 차례로 클릭하고 **서버에 연결** 대화 상자에 구독자 인스턴스 이름을 입력한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-111">On the Subscribers page, if the name of the Subscriber instance is not displayed, click **Add Subscriber**, click **Add SQL Server Subscriber**, enter the Subscriber instance name in the **Connect to Server** dialog box, and then click **Connect**.</span></span>  
  
6.  <span data-ttu-id="30cb5-112">구독자 페이지에서 구독자 서버의 인스턴스 이름을 선택 하 고 **\<New Database>** **구독 데이터베이스**에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-112">On the Subscribers page, select the instance name of the Subscriber server, and select **\<New Database>** under **Subscription Database**.</span></span>  
  
7.  <span data-ttu-id="30cb5-113">**새 데이터베이스** 대화 상자에서 **데이터베이스 이름** 상자에 **ProductReplica** 를 입력하고 **확인**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-113">On the **New Database** dialog box, enter **ProductReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="30cb5-114">**배포 에이전트 보안** 대화 상자에서 줄임표 (**...**) 단추를 클릭 하 고 \<_Machine_Name> **프로세스 계정** 상자에 _**\ repl_distribution** 를 입력 한 다음이 계정에 대 한 암호를 입력 하 고 **확인**을 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-114">In the **Distribution Agent Security** dialog box, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_distribution** in the **Process account** box, enter the password for this account, click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="30cb5-115">**마침** 을 클릭하여 나머지 페이지의 기본값을 적용하고 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-115">Click **Finish** to accept the default values on the remaining pages and complete the wizard.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="30cb5-116">구독자에서 데이터베이스 권한 설정</span><span class="sxs-lookup"><span data-stu-id="30cb5-116">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="30cb5-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결하고 **데이터베이스**, **ProductReplica**및 **보안**을 확장하고 **사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-117">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **ProductReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="30cb5-118">**일반** 페이지에 있는 **사용자 유형** 목록에서 **Windows 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-118">On the **General** page, in the **User type** list, select **Windows user**.</span></span>  
  
3.  <span data-ttu-id="30cb5-119">**사용자 이름** 상자를 선택 하 고 줄임표 (...) 단추를 클릭 한 다음 **선택할 개체 이름을 입력 하십시오** . 상자에 <Machine_Name>**\ Repl_distribution**를 입력 하 고 **이름 확인**을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-119">Select the **User name** box and click the ellipsis (...) button, in the **Enter the object name to select** box type <Machine_Name>**\repl_distribution**, click **Check Names**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="30cb5-120">**멤버 자격** 페이지의 **데이터베이스 역할 멤버 자격** 영역에서 **db_owner**를 선택한 다음 **확인** 을 클릭하여 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-120">On the **Membership** page, in **Database role membership** area, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a><span data-ttu-id="30cb5-121">구독의 동기화 상태를 보려면</span><span class="sxs-lookup"><span data-stu-id="30cb5-121">To view the synchronization status of the subscription</span></span>  
  
1.  <span data-ttu-id="30cb5-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-122">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="30cb5-123">**로컬 게시** 폴더에서 **AdvWorksProductTrans** 게시를 확장하고 **ProductReplica** 데이터베이스의 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-123">In the **Local Publications** folder, expand the **AdvWorksProductTrans** publication, right-click the subscription in the **ProductReplica** database, and then click **View Synchronization Status**.</span></span>  
  
     <span data-ttu-id="30cb5-124">구독의 현재 동기화 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-124">The current synchronization status of the subscription is displayed.</span></span>  
  
3.  <span data-ttu-id="30cb5-125">**AdvWorksProductTrans**에 해당 구독이 표시되지 않으면 F5 키를 눌러 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-125">If the subscription is not visible under **AdvWorksProductTrans**, press F5 to refresh the list.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="30cb5-126">다음 단계</span><span class="sxs-lookup"><span data-stu-id="30cb5-126">Next Steps</span></span>  
 <span data-ttu-id="30cb5-127">트랜잭션 게시에 구독을 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-127">You have successfully created a subscription to the transactional publication.</span></span> <span data-ttu-id="30cb5-128">이 구독에 대한 배포 에이전트가 계속 실행되므로 구독은 생성될 때 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-128">Because the Distribution Agent for this subscription runs continuously, the subscription is initialized when it is created.</span></span> <span data-ttu-id="30cb5-129">다음 단원에서는 추적 프로그램 토큰을 사용하여 변경 내용이 구독자에 복제되었는지 여부 및 대기 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="30cb5-129">Next, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency.</span></span> <span data-ttu-id="30cb5-130">[Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30cb5-130">See [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cb5-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30cb5-131">See Also</span></span>  
 <span data-ttu-id="30cb5-132">[스냅샷으로 구독 초기화](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="30cb5-132">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="30cb5-133">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="30cb5-133">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="30cb5-134">게시 구독</span><span class="sxs-lookup"><span data-stu-id="30cb5-134">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
