---
title: 등록 된 서버를 사용 하 여 요청 시 평가 수행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a3a06efaabff7e94e5b560744f0e1c739831042a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639168"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a><span data-ttu-id="62c51-102">등록된 서버를 사용하여 요청 시 평가 수행</span><span class="sxs-lookup"><span data-stu-id="62c51-102">Perform an On-Demand Evaluation by Using Registered Servers</span></span>

  <span data-ttu-id="62c51-103">등록된 서버를 사용하여 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대해 최선의 구현 방법 정책의 요청 시 평가를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-103">You can perform an on-demand evaluation of best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Registered Servers.</span></span> <span data-ttu-id="62c51-104">로컬 서버 그룹 또는 중앙 관리 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-104">You can use either local server groups or a central management server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62c51-105">[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이상 버전이 실행되는 서버 그룹 멤버에 대해 최선의 구현 방법 정책의 요청 시 평가를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-105">You can perform an on-demand evaluation of best practices policies against server group members that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or a later version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="62c51-106">그러나 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 또는 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]에서 지원되지 않는 정책에서 참조하는 속성이 있는 경우 예외 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-106">However, you may receive an exception error if there are some properties that are referred to by a policy that are not supported in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="62c51-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="62c51-107">Prerequisites</span></span>  
 <span data-ttu-id="62c51-108">등록된 서버에서 하나 이상의 서버 등록을 구성한 경우에만 이 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-108">To perform this task, you must have configured one or more server registrations in Registered Servers.</span></span> <span data-ttu-id="62c51-109">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62c51-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="62c51-110">서버 그룹 만들기 또는 편집&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="62c51-110">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   <span data-ttu-id="62c51-111">[연결 된 서버 &#40;SQL Server Management Studio&#41;등록 ](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-111">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
-   [<span data-ttu-id="62c51-112">중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="62c51-112">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a><span data-ttu-id="62c51-113">서버 그룹에 대해 최선의 구현 방법 정책을 평가하려면</span><span class="sxs-lookup"><span data-stu-id="62c51-113">To evaluate best practices policies against a server group</span></span>  
  
1.  <span data-ttu-id="62c51-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="62c51-115">**데이터베이스 엔진**를 확장 한 다음 구성에 따라 **로컬 서버 그룹**또는 **중앙 관리 서버**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-115">Expand **Database Engine**, and then expand either **Local Server Groups**, or **Central Management Servers**, depending on your configuration.</span></span>  
  
3.  <span data-ttu-id="62c51-116">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-116">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="62c51-117">로컬 서버 그룹 또는 중앙 관리 서버에서 관리 하는 모든 서버에 대해 정책을 평가 하려면 로컬 서버 그룹 이름 또는 중앙 관리 서버 이름을 마우스 오른쪽 단추로 클릭 한 다음 **정책 평가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-117">To evaluate the policies against all servers that are managed by the local server group or the central management server, right-click the local server group name or the central management server name, and then click **Evaluate Policies**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="62c51-118">중앙 관리 서버를 통해 정책을 평가하면 중앙 관리 서버 자체에 대해서는 정책이 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-118">When you evaluate policies through a central management server, the policies are not evaluated against the central management server itself.</span></span>  
  
    -   <span data-ttu-id="62c51-119">특정 서버나 서버 그룹에 대해 정책을 평가 하려면 **로컬 서버 그룹** 또는 중앙 관리 서버 이름을 확장 하 고 정책을 평가할 서버 또는 서버 그룹을 마우스 오른쪽 단추로 클릭 한 다음 **정책 평가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-119">To evaluate the policies against a specific server or server group, expand **Local Server Groups** or the central management server name, right-click the server or server group that you want to evaluate policies against, and then click **Evaluate Policies**.</span></span>  
  
4.  <span data-ttu-id="62c51-120">**정책 평가** 대화 상자에서 **원본** 상자 옆의 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-120">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="62c51-121">**원본 선택** 대화 상자에서 평가할 정책 파일의 원본으로 **파일** 또는 **서버** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-121">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="62c51-122">**서버**를 클릭 하면 로컬 또는 원격 서버에서 정책 기반 관리로 이전에 가져온 모범 사례 정책에 대 한 요청 시 평가를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-122">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="62c51-123">이 자습서에서는 **파일**을 클릭 한 다음 평가할 개별 정책 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-123">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="62c51-124">이렇게 하려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="62c51-124">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="62c51-125">**파일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-125">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="62c51-126">**파일**옆에 있는 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-126">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="62c51-127">평가할 하나 이상의 .xml 정책 파일을 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-127">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="62c51-128">선택한 파일의 목록이 **파일** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-128">The list of selected files appears in the **Files** box.</span></span>  
  
    4.  <span data-ttu-id="62c51-129">**원본 선택** 대화 상자에서 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-129">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="62c51-130">**정책 로드 중** 대화 상자가 나타나면 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-130">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="62c51-131">선택한 정책이 **정책 선택** 페이지에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-131">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="62c51-132">정책 옆의 경고 아이콘은 정책에 스크립트가 포함되어 있다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-132">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
6.  <span data-ttu-id="62c51-133">**평가** 를 클릭 하 여 정책을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-133">Click **Evaluate** to evaluate the policies.</span></span>  
  
7.  <span data-ttu-id="62c51-134">일부 정책 실패의 경우 정책 기반 관리를 사용하면 대상에서 정책 준수를 즉시 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-134">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="62c51-135">이러한 실패의 경우 실패한 정책 옆에 확인란이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-135">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="62c51-136">확인란을 선택 하거나 실패 한 정책이 포함 된 행을 클릭 하면 평가에 실패 한 대상 인스턴스 옆의 **대상 세부 정보** 창에 확인란이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-136">If you select the check box, or click the row with the failed policy, check boxes appear in the **Target details** pane next to the target instances that failed the evaluation.</span></span> <span data-ttu-id="62c51-137">확인란 중 하나를 선택 하면 **적용** 단추를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-137">If any of the check boxes are selected, the **Apply** button becomes available.</span></span> <span data-ttu-id="62c51-138">**적용**을 클릭 하면 선택한 대상 인스턴스에서 비규격 설정이 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instances that you selected.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="62c51-139">대상 인스턴스를 자동으로 업데이트하기 전에 정책 설정을 충분히 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="62c51-140">하나 이상의 확인란을 선택한 후에는 **스크립트**를 클릭 하 고 출력 위치를 선택 하 여 [!INCLUDE[tsql](../includes/tsql-md.md)] 변경 내용을 적용 하기 전에 기본 코드를 검토할 수 있도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
8.  <span data-ttu-id="62c51-141">정책에 대 한 자세한 결과를 보려면 **결과** 테이블에서 정책을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span> <span data-ttu-id="62c51-142">**대상 세부 정보** 테이블에는 각 인스턴스에 대 한 세부 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c51-142">The **Target details** table shows the details for each instance.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="62c51-143">다음 단원</span><span class="sxs-lookup"><span data-stu-id="62c51-143">Next Lesson</span></span>  
 [<span data-ttu-id="62c51-144">2단원: 일정에 따라 최선의 구현 방법 정책 평가</span><span class="sxs-lookup"><span data-stu-id="62c51-144">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="62c51-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62c51-145">See Also</span></span>  
 <span data-ttu-id="62c51-146">[정책 기반 관리를 사용 하 여 모범 사례 모니터링 및 적용](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="62c51-146">[Monitor and Enforce Best Practices by Using Policy-Based Management](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="62c51-147">중앙 관리 서버를 사용 하 여 여러 서버 관리</span><span class="sxs-lookup"><span data-stu-id="62c51-147">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
