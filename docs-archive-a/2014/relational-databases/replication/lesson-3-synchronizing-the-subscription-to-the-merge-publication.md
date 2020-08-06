---
title: '3단원: 병합 게시에 구독 동기화 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
ms.openlocfilehash: bf0256c69d69d1236869fa83285bf4dbf5c462da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739699"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a><span data-ttu-id="07a4c-102">3단원: 병합 게시에 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="07a4c-102">Lesson 3: Synchronizing the Subscription to the Merge Publication</span></span>
  <span data-ttu-id="07a4c-103">이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 병합 에이전트를 시작하여 구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-103">In this lesson, you will start the Merge Agent to initialize the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="07a4c-104">또한 이 절차를 사용하여 게시자와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-104">You also use this procedure to synchronize with the Publisher.</span></span> <span data-ttu-id="07a4c-105">이 단원을 수행하려면 이전 단원인 [2단원: 병합 게시에 대한 구독 만들기](lesson-2-creating-a-subscription-to-the-merge-publication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-105">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a><span data-ttu-id="07a4c-106">동기화를 시작하고 구독을 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="07a4c-106">To start synchronization and initialize the subscription</span></span>  
  
1.  <span data-ttu-id="07a4c-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="07a4c-108">**로컬 구독** 폴더에서 **SalesOrdersReplica** 데이터베이스의 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-108">In the **Local Subscriptions** folder, right-click the subscription in the **SalesOrdersReplica** database, and then click **View Synchronization Status**.</span></span>  
  
3.  <span data-ttu-id="07a4c-109">**시작** 을 클릭하여 구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-109">Click **Start** to initialize the subscription.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="07a4c-110">다음 단계</span><span class="sxs-lookup"><span data-stu-id="07a4c-110">Next Steps</span></span>  
 <span data-ttu-id="07a4c-111">병합 에이전트를 실행하여 동기화를 시작하고 구독을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-111">You have successfully run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="07a4c-112">또한 게시자나 구독자에 있는 **SalesOrderHeader** 나 **SalesOrderDetail** 테이블에서 데이터를 삽입, 업데이트 또는 삭제할 수 있고 네트워크가 연결되어 있을 때 이 절차를 반복하여 게시자와 구독자 사이의 데이터를 동기화한 다음 다른 서버에 있는 **SalesOrderHeader** 나 **SalesOrderDetail** 테이블을 쿼리하여 복제된 변경 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-112">You can also insert, update, or delete data in the **SalesOrderHeader** or **SalesOrderDetail** tables at the Publisher or Subscriber, repeat this procedure when network connectivity is available to synchronize data between the Publisher and the Subscriber, and then query the **SalesOrderHeader** or **SalesOrderDetail** tables at the other server to view the replicated changes.</span></span>  
  
 <span data-ttu-id="07a4c-113">이로써 모바일 클라이언트와의 데이터 복제 자습서를 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="07a4c-113">This completes the Replicating Data with Mobile Clients tutorial.</span></span> <span data-ttu-id="07a4c-114">트랜잭션 복제를 사용하는 유사한 자습서를 보려면 [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07a4c-114">For a similar tutorial that uses transactional replication, see [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a4c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07a4c-115">See Also</span></span>  
 <span data-ttu-id="07a4c-116">[스냅샷으로 구독 초기화](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="07a4c-116">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="07a4c-117">[데이터 동기화](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="07a4c-117">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="07a4c-118">끌어오기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="07a4c-118">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)  
  
  
