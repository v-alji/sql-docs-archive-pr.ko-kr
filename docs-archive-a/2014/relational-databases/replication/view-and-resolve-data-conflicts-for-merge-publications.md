---
title: 병합 게시에 대 한 데이터 충돌 보기 및 해결 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649470"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a><span data-ttu-id="e9a54-102">병합 게시에 대한 데이터 충돌 보기 및 해결(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e9a54-102">View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e9a54-103">병합 복제에서의 충돌은 각 아티클에 대해 지정된 해결 프로그램에 따라 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-103">Conflicts in merge replication are resolved based on the resolver specified for each article.</span></span> <span data-ttu-id="e9a54-104">기본적으로 충돌은 사용자가 개입할 필요 없이 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-104">By default, conflicts are resolved without the need for user intervention.</span></span> <span data-ttu-id="e9a54-105">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 복제 충돌 뷰어에서 충돌을 보고 해결 결과를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-105">But conflicts can be viewed, and the outcome of the resolution can be changed, in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span>  
  
 <span data-ttu-id="e9a54-106">지정된 충돌 보존 기간(기본값: 14일) 동안 복제 충돌 뷰어에서 충돌 데이터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-106">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period (with a default of 14 days).</span></span> <span data-ttu-id="e9a54-107">충돌 보존 기간을 설정하려면 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9a54-107">To set the conflict retention period, either:</span></span>  
  
-   <span data-ttu-id="e9a54-108">**@conflict_retention** [Transact-sql&#41;&#40;sp_addmergepublication ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)의 매개 변수에 보존 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-108">Specify a retention value for the **@conflict_retention** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
-   <span data-ttu-id="e9a54-109">매개 변수의 **conflict_retention** 값 **@property** 과 **@value** [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)의 매개 변수에 보존 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-109">Specify a value of **conflict_retention** for the **@property** parameter and a retention value for the **@value** parameter of [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="e9a54-110">기본적으로 충돌 정보는 다음 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-110">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="e9a54-111">게시 호환성 수준이 90RTM 이상일 경우 게시자 및 구독자.</span><span class="sxs-lookup"><span data-stu-id="e9a54-111">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="e9a54-112">게시 호환성 수준이 80RTM 미만일 경우 게시자</span><span class="sxs-lookup"><span data-stu-id="e9a54-112">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="e9a54-113">구독자가 [!INCLUDE[ssEW](../../includes/ssew-md.md)]을 실행하는 경우 게시자.</span><span class="sxs-lookup"><span data-stu-id="e9a54-113">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="e9a54-114">충돌 데이터는 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 구독자에 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-114">Conflict data cannot be stored on [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="e9a54-115">충돌 정보의 스토리지는 **conflict_logging** 게시 속성에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-115">Storage of conflict information is controlled by the **conflict_logging** publication property.</span></span> <span data-ttu-id="e9a54-116">자세한 내용은 [sp_addmergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) 및 [sp_changemergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9a54-116">For more information, see [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) and [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="e9a54-117">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 대화형 해결 프로그램을 사용하여 동기화하는 동안 대화형으로 충돌을 해결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-117">Conflicts can also be resolved interactively during synchronization using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Interactive Resolver.</span></span> <span data-ttu-id="e9a54-118">대화형 해결 프로그램은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 동기화 관리자를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-118">The Interactive Resolver is available through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="e9a54-119">자세한 내용은 [Windows 동기화 관리자를 사용하여 구독 동기화&#40;Windows 동기화 관리자&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9a54-119">For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a><span data-ttu-id="e9a54-120">병합 게시에 대한 충돌을 보고 해결하려면</span><span class="sxs-lookup"><span data-stu-id="e9a54-120">To view and resolve conflicts for merge publications</span></span>  
  
1.  <span data-ttu-id="e9a54-121">에서 게시자 (또는 구독자)에 연결한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 다음 해당 서버 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-121">Connect to the Publisher (or Subscriber if appropriate) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e9a54-122">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-122">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e9a54-123">충돌을 확인할 게시를 마우스 오른쪽 단추로 클릭한 다음 **충돌 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-123">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9a54-124">**conflict_logging** 속성에 **'subscriber'** 값을 지정한 경우에는 **충돌 보기** 메뉴 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-124">If you specified a value of **'subscriber'** for the **conflict_logging** property, the **View Conflicts** menu option is not available.</span></span> <span data-ttu-id="e9a54-125">충돌을 보려면 명령 프롬프트에서 ConflictViewer.exe를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-125">To view conflicts, start ConflictViewer.exe from the command prompt.</span></span> <span data-ttu-id="e9a54-126">기본적으로 ConflictViewer.exe는 Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-126">By default, ConflictViewer.exe is located in the following directory: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span> <span data-ttu-id="e9a54-127">유효한 시작 매개 변수 목록을 보려면 ConflictViewer.exe -?를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-127">For a list of valid startup parameters, run ConflictViewer.exe -?.</span></span>  
  
4.  <span data-ttu-id="e9a54-128">**충돌 테이블 선택** 대화 상자에서 충돌을 확인하려는 데이터베이스, 게시 및 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-128">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="e9a54-129">복제 충돌 뷰어에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-129">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="e9a54-130">상단 표 오른쪽의 단추를 사용하여 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-130">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="e9a54-131">상단 표에서 행을 선택하여 해당 행에 대한 정보를 하단 표에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-131">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="e9a54-132">상단 표에서 하나 이상의 행을 선택한 다음 **제거**를 클릭합니다. 이것은 **적용되는 내용 전송** 단추를 클릭하는 것과 같으며 데이터는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-132">Select one or more rows in the upper grid, and then click **Remove**, which is equivalent to clicking the **Submit Winner** button (without making any changes to the data).</span></span>  
  
    -   <span data-ttu-id="e9a54-133">속성 단추(**...**)를 클릭하여 충돌과 관련된 열에 대한 자세한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-133">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="e9a54-134">데이터를 전송하기 전에 **충돌 시 적용되는 내용** 또는 **충돌 시 변경 내용 무시** 열의 데이터를 편집합니다. 열이 회색인 경우 데이터는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-134">Edit data in the **Conflict winner** or **Conflict loser** column before submitting the data (data is read-only if the column is gray).</span></span>  
  
    -   <span data-ttu-id="e9a54-135">**적용되는 내용 전송** 을 클릭하면 충돌 시 적용되도록 지정한 행을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-135">Click **Submit Winner** to accept the row designated as the winner of the conflict.</span></span>  
  
    -   <span data-ttu-id="e9a54-136">**무시되는 내용 전송** 을 클릭하면 해결을 재정의하고 충돌 시 무시되도록 지정한 값을 토폴로지의 모든 노드로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-136">Click **Submit Loser** to override the resolution and to propagate the value designated as the loser of the conflict to all nodes in the topology.</span></span>  
  
    -   <span data-ttu-id="e9a54-137">**이 충돌 정보 기록** 을 선택하여 충돌 데이터를 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-137">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="e9a54-138">파일의 위치를 지정하려면 **보기** 메뉴를 가리킨 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-138">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="e9a54-139">값을 입력하거나 찾아보기 단추 (**...**)를 클릭한 다음 해당 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-139">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="e9a54-140">**확인** 을 클릭하여 **옵션** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-140">Click **OK** to exit the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="e9a54-141">복제 충돌 뷰어를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a54-141">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a54-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9a54-142">See Also</span></span>  
 <span data-ttu-id="e9a54-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="e9a54-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="e9a54-144">병합 아티클 해결 프로그램 지정</span><span class="sxs-lookup"><span data-stu-id="e9a54-144">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)  
  
  
