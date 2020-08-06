---
title: '1단원: 병합 복제를 사용하여 데이터 게시 | Microsoft 문서'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
ms.openlocfilehash: ba1d8829d84c02d1436013af80de4bf0979049e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736223"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a><span data-ttu-id="e2fc1-102">1단원: 병합 복제를 사용하여 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="e2fc1-102">Lesson 1: Publishing Data Using Merge Replication</span></span>
  <span data-ttu-id="e2fc1-103">이 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 병합 게시를 만들어 **샘플 데이터베이스에**Employee **,** SalesOrderHeader **및** SalesOrderDetail [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 테이블의 하위 집합을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-103">In this lesson, you will create a merge publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a subset of the **Employee**, **SalesOrderHeader**, and **SalesOrderDetail** tables in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="e2fc1-104">이러한 테이블은 각 구독에 고유한 데이터 파티션이 포함되도록 매개 변수가 있는 행 필터로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-104">These tables are filtered with parameterized row filters so that each subscription contains a unique partition of the data.</span></span> <span data-ttu-id="e2fc1-105">또한 병합 에이전트에 사용된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 PAL(게시 액세스 목록)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-105">You will also add the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Merge Agent to the publication access list (PAL).</span></span> <span data-ttu-id="e2fc1-106">이 자습서를 사용하려면 이전 자습서인 [복제용 서버 준비](tutorial-preparing-the-server-for-replication.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-106">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="e2fc1-107">게시를 만들고 아티클을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e2fc1-107">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="e2fc1-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e2fc1-109">**복제** 폴더를 확장하고 **로컬 게시**를 마우스 오른쪽 단추로 클릭한 다음 **새 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-109">Expand the **Replication** folder, right-click **Local Publications**, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="e2fc1-110">게시 구성 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-110">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="e2fc1-111">게시 데이터베이스 페이지에서 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-111">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="e2fc1-112">게시 유형 페이지에서 **병합 게시**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-112">On the Publication Type page, select **Merge publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="e2fc1-113">구독자 유형 페이지에서 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전만 선택되어 있는지 확인한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-113">On the Subscriber Types page, ensure that only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later is selected, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="e2fc1-114">아티클 페이지에서 **테이블** 노드를 확장하고 **SalesOrderHeader** 와 **SalesOrderDetail**을 선택한 다음 **Employee**를 확장하고 **EmployeeID** 또는 **LoginID**를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-114">On the Articles page, expand the **Tables** node, select **SalesOrderHeader** and **SalesOrderDetail**, then expand **Employee**, select **EmployeeID** or **LoginID**, and then click **Next**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e2fc1-115">필요한 추가 열은 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-115">Additional required columns are automatically selected.</span></span> <span data-ttu-id="e2fc1-116">자동으로 선택된 열 중 하나를 선택하고 **게시할 개체** 목록 아래의 정보에서 열이 필요한 이유에 대한 설명을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-116">Select any of  the automatically selected columns and view the note below the **Objects to publish** list for an explanation why the column is required.</span></span>  
  
7.  <span data-ttu-id="e2fc1-117">테이블 행 필터 페이지에서 **추가** 를 클릭한 다음 **필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-117">On the Filter Table Rows page, click **Add** and then click **Add Filter**.</span></span>  
  
8.  <span data-ttu-id="e2fc1-118">**필터 추가** 대화 상자의 **필터링할 테이블을 선택하십시오.** 에서 **Employee(HumanResources)** 를 선택하고 **LoginID** 열을 클릭한 다음 오른쪽 화살표를 클릭하여 해당 열을 필터 쿼리의 WHERE 절에 추가하고 WHERE 절을 다음과 같이 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-118">In the **Add Filter** dialog box, select **Employee (HumanResources)** in **Select the table to filter**, click the **LoginID** column, click the right arrow to add the column to the WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. <span data-ttu-id="e2fc1-119">**이 테이블의 행을 단일 구독으로 이동**을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-119">Click **A row from this table will go to only one subscription**, and click **OK**.</span></span>  
  
10. <span data-ttu-id="e2fc1-120">**테이블 행 필터** 페이지에서 **Employee(Human Resources)** 를 클릭하고 **추가** 를 클릭한 다음 **선택한 필터 확장을 위해 조인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-120">On the **Filter Table Rows** page, click **Employee (Human Resources)**, click **Add,** and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
11. <span data-ttu-id="e2fc1-121">**조인 추가** 대화 상자의 **조인된 테이블** 에서 **Sales.SalesOrderHeader**를 선택하고 **조인 문 직접 작성**을 클릭한 후 다음과 같이 조인 문을 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-121">In the **Add Join** dialog box, select **Sales.SalesOrderHeader** under **Joined table**, click **Write the join statement manually**, and complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. <span data-ttu-id="e2fc1-122">**조인 옵션을 지정하십시오.** 에서 **고유 키**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-122">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="e2fc1-123">테이블 행 필터 페이지에서 **SalesOrderHeader**를 클릭하고 **추가**를 클릭한 다음 **선택한 필터 확장을 위해 조인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-123">On the Filter Table Rows page, click **SalesOrderHeader**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
14. <span data-ttu-id="e2fc1-124">**조인 추가** 대화 상자의 **조인된 테이블** 에서 **Sales.SalesOrderDetail**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-124">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**.</span></span>  
  
15. <span data-ttu-id="e2fc1-125">**조인 문 직접 작성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-125">Click **Write the join statement manually**.</span></span>  
  
16. <span data-ttu-id="e2fc1-126">**필터링된 테이블 열**에서 **BusinessEntityID**를 선택한 다음 화살표 단추를 클릭하여 열 이름을 조인 문에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-126">In **Filtered table columns**, select **BusinessEntityID**, then click the arrow button to copy the column name to the loin statement.</span></span>  
  
17. <span data-ttu-id="e2fc1-127">**조인 문** 상자에서 다음과 같이 조인 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-127">In the **Join statement** box, complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. <span data-ttu-id="e2fc1-128">**조인 옵션을 지정하십시오.** 에서 **고유 키**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-128">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="e2fc1-129">**테이블 행 필터** 페이지에서 **SalesOrderHeader(Sales)** 를 클릭하고 **추가**를 클릭한 다음 **선택한 필터 확장을 위해 조인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-129">On the **Filter Table Rows** page, click **SalesOrderHeader (Sales)**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
20. <span data-ttu-id="e2fc1-130">**조인 추가** 대화 상자의 **조인된 테이블** 에서 **Sales.SalesOrderDetail**을 선택한 다음 **확인**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-130">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**, click **OK**, and then click **Next**.</span></span>  
  
21. <span data-ttu-id="e2fc1-131">**즉시 스냅샷 만들기**를 선택하고 **스냅샷 에이전트 실행 시간 예약**을 선택 취소한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-131">Select **Create a snapshot immediately**, clear **Schedule the snapshot agent to run at the following times**, and click **Next**.</span></span>  
  
22. <span data-ttu-id="e2fc1-132">에이전트 보안 페이지에서 **보안 설정**을 클릭 하 고 \<_Machine_Name> **프로세스 계정** 상자에 _**\ repl_snapshot** 를 입력 한 다음이 계정에 대 한 암호를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-132">On the Agent Security page, click **Security Settings**, type \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span> <span data-ttu-id="e2fc1-133">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-133">Click **Finish**.</span></span>  
  
23. <span data-ttu-id="e2fc1-134">마법사 완료 페이지에서 **게시 이름** 상자에 **AdvWorksSalesOrdersMerge** 를 입력하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-134">On the Complete the Wizard page, enter **AdvWorksSalesOrdersMerge** in the **Publication name** box and click **Finish**.</span></span>  
  
24. <span data-ttu-id="e2fc1-135">게시를 만든 후 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-135">After the publication is created, click **Close**.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="e2fc1-136">스냅샷 생성의 상태를 보려면</span><span class="sxs-lookup"><span data-stu-id="e2fc1-136">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="e2fc1-137">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-137">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="e2fc1-138">로컬 게시 폴더에서 **AdvWorksSalesOrdersMerge**를 마우스 오른쪽 단추로 클릭한 다음 **스냅샷 에이전트 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-138">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="e2fc1-139">게시에 대한 스냅샷 에이전트 작업의 현재 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-139">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="e2fc1-140">다음 단원을 진행하기 전에 스냅샷 작업이 성공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-140">Ensure that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a><span data-ttu-id="e2fc1-141">PAL에 병합 에이전트 로그인을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e2fc1-141">To add the Merge Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="e2fc1-142">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결하고 해당 서버 노드를 확장한 다음 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-142">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="e2fc1-143">로컬 게시 폴더에서 **AdvWorksSalesOrdersMerge**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-143">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="e2fc1-144">**게시 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-144">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="e2fc1-145">**게시 액세스 목록** 페이지를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-145">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="e2fc1-146">게시 액세스 추가 대화 상자에서 _<Machine_Name>_**\repl_merge**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-146">In the Add Publication Access dialog box, select _<Machine_Name>_**\repl_merge** and click **OK**.</span></span> <span data-ttu-id="e2fc1-147">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-147">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e2fc1-148">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e2fc1-148">Next Steps</span></span>  
 <span data-ttu-id="e2fc1-149">병합 게시를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-149">You have successfully created the merge publication.</span></span> <span data-ttu-id="e2fc1-150">다음 단원에서는 이 게시를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-150">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="e2fc1-151">[2단원: 병합 게시에 대한 구독 만들기](lesson-2-creating-a-subscription-to-the-merge-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2fc1-151">See [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fc1-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2fc1-152">See Also</span></span>  
 <span data-ttu-id="e2fc1-153">[게시된 데이터 필터링](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="e2fc1-153">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="e2fc1-154">[매개 변수가 있는 행 필터](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e2fc1-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="e2fc1-155">아티클 정의</span><span class="sxs-lookup"><span data-stu-id="e2fc1-155">Define an Article</span></span>](publish/define-an-article.md)  
  
  
