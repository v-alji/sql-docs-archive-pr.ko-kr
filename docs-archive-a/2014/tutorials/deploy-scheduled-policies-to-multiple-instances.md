---
title: 여러 인스턴스에 예약 된 정책 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 30faf94c2033be43ac035517e58d5a18c0c68ab8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728984"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a><span data-ttu-id="0f812-102">여러 인스턴스에 예약된 정책 배포</span><span class="sxs-lookup"><span data-stu-id="0f812-102">Deploy Scheduled Policies to Multiple Instances</span></span>
  <span data-ttu-id="0f812-103">등록된 서버를 사용하면 중앙 위치에서 관리되는 서버로 예약된 정책을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-103">By using Registered Servers, you can deploy scheduled policies to managed servers from a central location.</span></span> <span data-ttu-id="0f812-104">로컬 서버 그룹 또는 중앙 관리 서버에서 예약된 정책을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-104">You can deploy scheduled policies from either a local server group, or from a Central Management Server.</span></span>  
  
 <span data-ttu-id="0f812-105">이 태스크에서는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-105">In this task, you will do the following:</span></span>  
  
1.  <span data-ttu-id="0f812-106">이전 태스크에서 예약한 정책을 폴더로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-106">Export the policies that you scheduled in the previous task to a folder.</span></span>  
  
2.  <span data-ttu-id="0f812-107">예약된 정책을 등록된 서버로 관리되는 대상 인스턴스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-107">Deploy the scheduled policies to target instances that are managed through Registered Servers.</span></span>  
  
 <span data-ttu-id="0f812-108">이 단원에서는 이전 태스크를 완료한 컴퓨터에서 이러한 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-108">You will perform these tasks on the computer where you completed the previous tasks in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0f812-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0f812-109">Prerequisites</span></span>  
 <span data-ttu-id="0f812-110">이 태스크의 선행 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-110">This task has the following prerequisites:</span></span>  
  
-   <span data-ttu-id="0f812-111">이 단원에서 이전 태스크를 완료했어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-111">You must have completed the previous tasks in this lesson.</span></span>  
  
-   <span data-ttu-id="0f812-112">예약된 정책을 배포할 인스턴스에서 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 이상 버전을 실행하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-112">The instances where you want to deploy the scheduled policies must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="0f812-113">Automation을 수행하려면 정책을 로컬로 저장해야 합니다. 이 기능은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 버전에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-113">Automation requires the policies to be stored locally, which is not supported on versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
-   <span data-ttu-id="0f812-114">예약 된 정책을 배포 하려는 서버는 **로컬 서버 그룹** 또는 **중앙 관리 서버** 노드의 등록 된 서버에 등록 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-114">The servers where you want to deploy the scheduled policies must be registered in Registered Servers in either the **Local Server Groups** or the **Central Management Servers** node.</span></span> <span data-ttu-id="0f812-115">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f812-115">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="0f812-116">서버 그룹 만들기 또는 편집&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0f812-116">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="0f812-117">[연결 된 서버 &#40;SQL Server Management Studio&#41;등록 ](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-117">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
    -   [<span data-ttu-id="0f812-118">중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0f812-118">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a><span data-ttu-id="0f812-119">예약된 정책을 .xml 파일로 내보내려면</span><span class="sxs-lookup"><span data-stu-id="0f812-119">To export the scheduled policies as .xml files</span></span>  
  
1.  <span data-ttu-id="0f812-120">이전 작업에서 예약 된 정책을 구성한 서버에서 **관리**, **정책 관리**를 차례로 확장 한 다음 **정책**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-120">On the server where you configured scheduled policies in the previous task, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span>  
  
2.  <span data-ttu-id="0f812-121">**보기** 메뉴에서 **개체 탐색기 정보**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-121">On the **View** menu, click **Object Explorer Details**.</span></span>  
  
3.  <span data-ttu-id="0f812-122">**개체 탐색기 세부 정보** 창에서 등록 된 서버를 통해 다른 서버에 배포할 예약 된 최선의 구현 방법 정책을 모두 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-122">In the **Object Explorer Details** pane, select all the scheduled best practices policies that you want to deploy to other servers through Registered Servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f812-123">**범주 제목을 클릭** 하 여 범주별로 정책을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-123">You can click the **Category** heading to sort the policies by category.</span></span>  
  
4.  <span data-ttu-id="0f812-124">선택 영역을 마우스 오른쪽 단추로 클릭 한 다음 **정책 내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-124">Right-click the selection, and then click **Export Policy**.</span></span>  
  
5.  <span data-ttu-id="0f812-125">내보낼 여러 정책을 선택한 경우 **폴더 찾아보기** 대화 상자에서 대상 폴더를 선택 하거나 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-125">If you selected multiple policies to export, in the **Browse For Folder** dialog box, select a destination folder, or create a new folder.</span></span> <span data-ttu-id="0f812-126">이 단원에서는 **c:\ Scheduled_BP_Policies**경로를 사용 하 여 새 폴더를 만든 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-126">For this lesson, create a new folder with the path **C:\Scheduled_BP_Policies**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0f812-127">내보낼 정책을 하나만 선택한 경우 **정책 내보내기** 대화 상자에서 **c:\ Scheduled_BP_Policies**경로를 사용 하 여 새 폴더를 만들고 **열기**를 클릭 한 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-127">If you only selected one policy to export, in the **Export Policy** dialog box, create a new folder with the path **C:\Scheduled_BP_Policies**, click **Open**, and then click **Save**.</span></span>  
  
     <span data-ttu-id="0f812-128">.xml 정책 파일은 폴더 위치에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-128">The .xml policy files are created in the folder location.</span></span>  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a><span data-ttu-id="0f812-129">예약된 정책을 등록된 서버를 통해 관리되는 서버에 배포하려면</span><span class="sxs-lookup"><span data-stu-id="0f812-129">To deploy the scheduled policies to servers that are managed through Registered Servers</span></span>  
  
1.  <span data-ttu-id="0f812-130">**보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-130">On the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="0f812-131">**데이터베이스 엔진**를 확장 하 고 **로컬 서버 그룹** 또는 **중앙 관리 서버**를 확장 하 고 정책을 배포할 노드를 마우스 오른쪽 단추로 클릭 한 다음 **정책 가져오기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-131">Expand **Database Engine**, expand either **Local Server Groups** or **Central Management Servers**, right-click the node that you want to deploy the policies to, and then click **Import Policies**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f812-132">**로컬 서버 그룹** 또는 중앙 관리 서버 자체를 마우스 오른쪽 단추로 클릭 하면 정책이 모든 관리 되는 서버에 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-132">If you right-click **Local Server Groups** or the Central Management Server itself, the policies will be deployed to all managed servers.</span></span> <span data-ttu-id="0f812-133">특정 서버 그룹을 마우스 오른쪽 단추로 클릭하면 해당 그룹의 서버에만 정책이 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-133">If you right-click a specific server group, the policies will only be deployed to servers in that group.</span></span> <span data-ttu-id="0f812-134">등록된 특정 서버를 마우스 오른쪽 단추로 클릭하면 해당 서버에만 정책이 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-134">If you right-click a specific registered server, the policies will only be deployed to that server.</span></span>  
  
3.  <span data-ttu-id="0f812-135">**가져올 파일**옆에 있는 줄임표 단추 (**...**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-135">Next to **Files to import**, click the ellipsis button (**...**).</span></span>  
  
4.  <span data-ttu-id="0f812-136">**정책 선택** 대화 상자에서 예약 된 정책을 저장 한 폴더 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-136">In the **Select Policy** dialog box, browse to the folder location where you saved the scheduled policies.</span></span> <span data-ttu-id="0f812-137">이 예에서는 **c:\ Scheduled_BP_Policies**위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-137">For this example, browse to the location **C:\Scheduled_BP_Policies**.</span></span>  
  
5.  <span data-ttu-id="0f812-138">대상 인스턴스로 가져올 정책을 선택한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-138">Select the policies that you want to import to the target instances, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="0f812-139">**가져오기** 대화 상자의 **정책 상태** 목록에서 원하는 정책 상태를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-139">In the **Import** dialog box, in the **Policy state** list, select the desired policy state.</span></span> <span data-ttu-id="0f812-140">가져올 때 정책 상태를 유지하거나 정책을 설정 또는 해제하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-140">You can choose to preserve the policy state, enable, or disable the policies on import.</span></span> <span data-ttu-id="0f812-141">정책은 예약 실행하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-141">Be aware that the policies must be enabled to run on a schedule.</span></span>  
  
7.  <span data-ttu-id="0f812-142">**확인** 을 클릭 하 여 모든 대상 인스턴스로 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-142">Click **OK** to import the policies to all the target instances.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f812-143">오류가 있는 경우 **가져오기** 대화 상자는 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-143">If there are any errors, the **Import** dialog box does not disappear.</span></span> <span data-ttu-id="0f812-144">**로그** 페이지를 클릭 하 여 메시지를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-144">Click the **Log** page to review the messages.</span></span> <span data-ttu-id="0f812-145">**취소**를 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-145">Click **Cancel** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="0f812-146">대상 인스턴스에서 정책을 보려면 인스턴스에 연결 하 고 개체 탐색기를 연 다음 **관리**, **정책**을 차례로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-146">To view the policies from a target instance, connect to the instance, open Object Explorer, expand **Management**, and then expand **Policies**.</span></span> <span data-ttu-id="0f812-147">가져온 정책이 **정책** 노드에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-147">You should see the imported policies in the **Policies** node.</span></span> <span data-ttu-id="0f812-148">각 정책을 두 번 클릭하면 일정을 보거나 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-148">If you double-click each policy, you can view the schedule, or change the settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f812-149">예약된 정책 실행 이후 평가 결과를 보려면 대상 인스턴스에 대한 정책 기록 로그를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-149">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="0f812-150">로그를 열려면 **정책 관리**를 마우스 오른쪽 단추로 클릭 한 다음 **기록 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-150">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="0f812-151">요약</span><span class="sxs-lookup"><span data-stu-id="0f812-151">Summary</span></span>  
 <span data-ttu-id="0f812-152">이 자습서에서는 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대해 최선의 구현 방법 정책에 대한 요청 시 평가와 예약된 평가를 모두 수행하는 방법을 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-152">This tutorial has shown you how to perform both on-demand and scheduled evaluations of the best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="next"></a><span data-ttu-id="0f812-153">다음</span><span class="sxs-lookup"><span data-stu-id="0f812-153">Next</span></span>  
 <span data-ttu-id="0f812-154">이 자습서를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-154">This tutorial is finished.</span></span> <span data-ttu-id="0f812-155">시작으로 돌아가려면 [자습서: 정책 기반 관리를 사용 하 여 최선의 구현 방법 평가](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0f812-155">To return to the start, see [Tutorial: Evaluating Best Practices by Using Policy-Based Management](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="0f812-156">자습서 목록을 보려면 [!INCLUDE[ssDE](../includes/ssde-md.md)] [데이터베이스 엔진 자습서](../relational-databases/database-engine-tutorials.md)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f812-156">To see a list of [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorials, click [Database Engine Tutorials](../relational-databases/database-engine-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f812-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f812-157">See Also</span></span>  
 [<span data-ttu-id="0f812-158">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="0f812-158">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
