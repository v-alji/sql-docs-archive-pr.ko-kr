---
title: '3단원: 구독 유효성 검사 및 대기 시간 측정 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: rothja
ms.author: jroth
ms.openlocfilehash: e4893c054d25d131eb2f88f32291606b0b789af7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739694"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a><span data-ttu-id="5b20d-102">3단원: 구독 유효성 검사 및 대기 시간 측정</span><span class="sxs-lookup"><span data-stu-id="5b20d-102">Lesson 3: Validating the Subscription and Measuring Latency</span></span>
  <span data-ttu-id="5b20d-103">이 단원에서는 추적 프로그램 토큰을 사용하여 구독자에 변경 내용이 복제되는지 확인하고 대기 시간, 즉 게시자에서 변경한 내용이 구독자에게 표시될 때까지 걸리는 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-103">In this lesson, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency, the time it takes for a change made at the Publisher to appear to the Subscriber.</span></span> <span data-ttu-id="5b20d-104">이 단원을 수행하려면 이전 단원인 [2단원: 트랜잭션 게시에 구독 만들기](lesson-2-creating-a-subscription-to-the-transactional-publication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-104">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="5b20d-105">추적 프로그램 토큰을 삽입하고 이 토큰에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="5b20d-105">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="5b20d-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 서버 노드를 확장한 다음 **복제** 폴더를 마우스 오른쪽 단추로 클릭하고 **복제 모니터 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, right-click the **Replication** folder, and then click **Launch Replication Monitor**.</span></span>  
  
     <span data-ttu-id="5b20d-107">복제 모니터가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-107">Replication Monitor launches.</span></span>  
  
2.  <span data-ttu-id="5b20d-108">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자 인스턴스를 확장한 다음 **AdvWorksProductTrans** 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-108">Expand a Publisher group in the left pane, expand the Publisher instance, and then click the **AdvWorksProductTrans** publication.</span></span>  
  
3.  <span data-ttu-id="5b20d-109">**추적 프로그램 토큰** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-109">Click the **Tracer Tokens** tab.</span></span>  
  
4.  <span data-ttu-id="5b20d-110">**추적 프로그램 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-110">Click **Insert Tracer**.</span></span>  
  
5.  <span data-ttu-id="5b20d-111">**게시자에서 배포자로 연결 시 대기 시간**, **배포자에서 구독자로 연결 시 대기 시간**, **총 대기 시간**열에서 추적 프로그램 토큰에 대한 경과 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-111">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="5b20d-112">**보류** 중 값은 토큰이 지정 된 지점에 도달 하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-112">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5b20d-113">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5b20d-113">Next Steps</span></span>  
 <span data-ttu-id="5b20d-114">이 단원에서는 추적 프로그램 토큰을 사용하여 데이터 변경 내용이 게시자에서 구독자로 복제되고 있는지 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-114">In this lesson, you successfully used tracer tokens to validate that data changes are being replicated from the Publisher to the Subscriber.</span></span> <span data-ttu-id="5b20d-115">게시자의 **Product** 테이블에서 데이터를 삽입, 업데이트 또는 삭제할 수 있으며 이러한 변경 내용을 복제한 다음 구독자에서 **Product** 테이블을 쿼리하여 해당 변경 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-115">You can also insert, update, or delete data in the **Product** table at the Publisher and query the **Product** table at the Subscriber to view these changes after they are replicated.</span></span>  
  
 <span data-ttu-id="5b20d-116">이로써 계속 연결된 서버 간 데이터 복제 자습서를 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="5b20d-116">This completes the Replicating Data Between Continuously Connected Servers tutorial.</span></span> <span data-ttu-id="5b20d-117">병합 복제를 사용하는 유사한 자습서를 보려면 [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5b20d-117">For a similar tutorial that uses merge replication, see [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b20d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b20d-118">See Also</span></span>  
 [<span data-ttu-id="5b20d-119">트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="5b20d-119">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
