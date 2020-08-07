---
title: '1단원: 트랜잭션 복제를 사용하여 데이터 게시 | Microsoft 문서'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce20f4ed8863ede34c8709d2b77bf032e7d14a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729352"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a><span data-ttu-id="9985b-102">1단원: 트랜잭션 복제를 사용하여 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="9985b-102">Lesson 1: Publishing Data Using Transactional Replication</span></span>
  <span data-ttu-id="9985b-103"> 이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 트랜잭션 게시를 만들어 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 샘플 데이터베이스에 **Product** 테이블의 필터링된 하위 집합을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-103">In this lesson, you will create a transactional publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a filtered subset of the **Product** table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="9985b-104">또한 배포 에이전트에 사용된 SQL Server 로그인을 PAL(게시 액세스 목록)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-104">You will also add the SQL Server login used by the Distribution Agent to the publication access list (PAL).</span></span> <span data-ttu-id="9985b-105">이 자습서를 시작하려면 이전 자습서인 [복제용 서버 준비](tutorial-preparing-the-server-for-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-105">Before starting this tutorial, you should have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="9985b-106">게시를 만들고 아티클을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="9985b-106">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="9985b-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-107">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9985b-108">**복제** 폴더를 확장하고 **로컬 게시** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-108">Expand the **Replication** folder, right-click the **Local Publications** folder, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="9985b-109">게시 구성 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-109">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="9985b-110">게시 데이터베이스 페이지에서 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-110">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="9985b-111">게시 유형 페이지에서 **트랜잭션 게시**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-111">On the Publication Type page, select **Transactional publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9985b-112">아티클 페이지에서 **테이블** 노드를 확장하고 **Product** 확인란을 선택한 다음 **Product** 를 확장하고 **ListPrice** 및 **StandardCost** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-112">On the Articles page, expand the **Tables** node, select the **Product** check box, then expand **Product** and clear the **ListPrice** and **StandardCost** check boxes.</span></span> <span data-ttu-id="9985b-113">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="9985b-114">테이블 행 필터 페이지에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-114">On the Filter Table Rows page, click **Add**.</span></span>  
  
7.  <span data-ttu-id="9985b-115">**필터 추가** 대화 상자에서 **SafetyStockLevel** 열을 클릭하고 오른쪽 화살표를 클릭하여 필터 쿼리의 필터 문 WHERE 절에 해당 열을 추가한 후 WHERE 절을 다음과 같이 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-115">In the **Add Filter** dialog box, click the **SafetyStockLevel** column, click the right arrow to add the column to the Filter statement WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  <span data-ttu-id="9985b-116">**확인**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-116">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="9985b-117">**즉시 스냅샷을 만들고 구독 초기화에 사용할 수 있도록 유지합니다.** 확인란을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-117">Select the **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** check box, and click **Next**.</span></span>  
  
10. <span data-ttu-id="9985b-118">에이전트 보안 페이지에서 **스냅샷 에이전트의 보안 설정 사용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-118">On the Agent Security page, clear **Use the security settings from the Snapshot Agent** check box.</span></span>  
  
11. <span data-ttu-id="9985b-119">스냅숏 에이전트에 대 한 **보안 설정** 을 클릭 하 고 \<_Machine_Name> **프로세스 계정** 상자에 _**\ repl_snapshot** 를 입력 한 다음이 계정에 대 한 암호를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-119">Click **Security Settings** for the Snapshot Agent, enter \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="9985b-120">이전 단계를 반복하여 repl_logreader를 로그 판독기 에이전트에 대한 프로세스 계정으로 설정한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-120">Repeat the previous step to set repl_logreader as the process account for the Log Reader Agent, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="9985b-121">마법사 완료 페이지에서 **게시 이름** 상자에 **AdvWorksProductTrans** 를 입력하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-121">On the Complete the Wizard page, type **AdvWorksProductTrans** in the **Publication name** box, and click **Finish**.</span></span>  
  
14. <span data-ttu-id="9985b-122">게시를 만든 후 **닫기** 를 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-122">After the publication is created, click **Close** to complete the wizard.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="9985b-123">스냅샷 생성의 상태를 보려면</span><span class="sxs-lookup"><span data-stu-id="9985b-123">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="9985b-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="9985b-125">**로컬 게시** 폴더에서 **AdvWorksProductTrans**를 마우스 오른쪽 단추로 클릭한 다음 **스냅샷 에이전트 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-125">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="9985b-126">게시에 대한 스냅샷 에이전트 작업의 현재 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-126">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="9985b-127">다음 단원을 진행하기 전에 스냅샷 작업이 성공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-127">Verify that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a><span data-ttu-id="9985b-128">PAL에 배포 에이전트 로그인을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="9985b-128">To add the Distribution Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="9985b-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-129">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="9985b-130">**로컬 게시** 폴더에서 **AdvWorksProductTrans**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-130">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="9985b-131">**게시 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-131">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="9985b-132">**게시 액세스 목록** 페이지를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-132">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="9985b-133">**게시 액세스 추가** 대화 상자에서 _<Machine_Name>_**\repl_distribution**을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-133">\In the **Add Publication Access** dialog box, select _<Machine_Name>_**\repl_distribution** and click **OK**.</span></span> <span data-ttu-id="9985b-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9985b-135">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9985b-135">Next Steps</span></span>  
 <span data-ttu-id="9985b-136">트랜잭션 게시를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-136">You have successfully created the transactional publication.</span></span> <span data-ttu-id="9985b-137">다음 단원에서는 이 게시를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="9985b-137">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="9985b-138">[2단원: 트랜잭션 게시에 구독 만들기](lesson-2-creating-a-subscription-to-the-transactional-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9985b-138">See [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9985b-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9985b-139">See Also</span></span>  
 <span data-ttu-id="9985b-140">[게시된 데이터 필터링](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="9985b-140">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="9985b-141">[Define an Article](publish/define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="9985b-141">[Define an Article](publish/define-an-article.md) </span></span>  
 [<span data-ttu-id="9985b-142">스냅샷 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="9985b-142">Create and Apply the Snapshot</span></span>](create-and-apply-the-snapshot.md)  
  
  
