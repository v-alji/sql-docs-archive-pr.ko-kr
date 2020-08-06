---
title: 개체 탐색기 |를 사용 하 여 요청 시 평가 수행 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e32876978ac462af361986d84e11ef3dc0f278e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639167"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="be660-102">개체 탐색기를 사용하여 요청 시 평가 수행</span><span class="sxs-lookup"><span data-stu-id="be660-102">Perform an On-Demand Evaluation by Using Object Explorer</span></span>
  <span data-ttu-id="be660-103">이 태스크에서는 개체 탐색기를 사용하여 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]의 단일 인스턴스에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 최선의 구현 방법 정책에 대한 요청 시 평가를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-103">In this task, you will use Object Explorer to perform an on-demand evaluation of best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be660-104">등록된 서버를 통해 단일 인스턴스에서 정책을 평가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-104">You can also evaluate policies on a single instance through Registered Servers.</span></span> <span data-ttu-id="be660-105">자세한 내용은 [등록 된 서버를 사용 하 여 요청 시 평가 수행](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be660-105">For more information, see [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="be660-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="be660-106">Prerequisites</span></span>  
 <span data-ttu-id="be660-107">이 단원은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-107">This lesson is based on the version of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be660-108">실행 중인 인스턴스에 대해 최선의 구현 방법 정책의 요청 시 평가를 수행 하려면 등록 된 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [서버를 사용 하 여 요청 시 평가 수행](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)항목의 절차를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-108">To perform an on-demand evaluation of best practices policies against instances that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you must use the procedure in the topic [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="be660-109">개체 탐색기를 사용하여 요청 시 평가를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="be660-109">To perform an on-demand evaluation by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="be660-110">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]를 시작하고 [!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-110">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="be660-111">개체 탐색기에서 **관리**, **정책 관리**를 차례로 확장 하 고 **정책**을 마우스 오른쪽 단추로 클릭 한 다음 **평가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-111">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and then click **Evaluate**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be660-112">기본적으로 로컬 인스턴스가 정책의 원본으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-112">By default, the local instance is used as the source of the policies.</span></span> <span data-ttu-id="be660-113">이전에 최선의 구현 방법 정책을 가져온 경우 만들어진 다른 정책과 함께 해당 정책이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-113">If you have previously imported best practices policies, they will be listed, together with any other policies that you have created.</span></span> <span data-ttu-id="be660-114">가져온 모범 사례 정책 중 하나를 선택 하 고 **평가**를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-114">You can select any of the imported best practices policies, and then click **Evaluate**.</span></span> <span data-ttu-id="be660-115">최선의 구현 방법 정책을 가져오지 않은 경우 이 절차를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-115">If you have not imported the best practices policies, continue with this procedure.</span></span>  
  
3.  <span data-ttu-id="be660-116">**정책 평가** 대화 상자에서 **원본** 상자 옆의 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-116">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
4.  <span data-ttu-id="be660-117">**원본 선택** 대화 상자에서 평가할 정책 파일의 원본으로 **파일** 또는 **서버** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-117">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="be660-118">**서버**를 클릭 하면 로컬 또는 원격 서버에서 정책 기반 관리로 이전에 가져온 모범 사례 정책에 대 한 요청 시 평가를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-118">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="be660-119">이 자습서에서는 **파일**을 클릭 한 다음 평가할 개별 정책 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-119">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="be660-120">이렇게 하려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="be660-120">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="be660-121">**파일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-121">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="be660-122">**파일**옆에 있는 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-122">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="be660-123">**정책 선택** 대화 상자에서 최선의 구현 방법 정책이 포함 된 다음 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-123">In the **Select Policy** dialog box, browse to the following folder, which contains the best practices policies:</span></span>  
  
         <span data-ttu-id="be660-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="be660-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="be660-125">파일 경로는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 프로그램 파일의 설치 위치, 32비트 운영 체제를 실행하는지 아니면 64비트 운영 체제를 실행하는지 여부 및 언어 식별자에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-125">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
    4.  <span data-ttu-id="be660-126">평가할 하나 이상의 .xml 정책 파일을 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-126">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="be660-127">선택한 파일의 목록이 **파일** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="be660-127">The list of selected files appears in the **Files** box.</span></span>  
  
    5.  <span data-ttu-id="be660-128">**원본 선택** 대화 상자에서 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-128">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="be660-129">**정책 로드 중** 대화 상자가 나타나면 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-129">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="be660-130">선택한 정책이 **정책 선택** 페이지에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-130">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="be660-131">정책 옆의 경고 아이콘은 정책에 스크립트가 포함되어 있다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be660-131">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
5.  <span data-ttu-id="be660-132">**평가** 를 클릭 하 여 정책을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-132">Click **Evaluate** to evaluate the policies.</span></span>  
  
     <span data-ttu-id="be660-133">**결과** 테이블에 각 정책에 대 한 결과가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-133">In the **Results** table, the results for each policy are listed.</span></span> <span data-ttu-id="be660-134">빨간색 "x" 아이콘은 정책 준수에 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be660-134">A red "x" icon indicates that policy compliance failed.</span></span>  
  
6.  <span data-ttu-id="be660-135">일부 정책 실패의 경우 정책 기반 관리를 사용하면 대상에서 정책 준수를 즉시 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-135">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="be660-136">이러한 실패의 경우 실패한 정책 옆에 확인란이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="be660-136">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="be660-137">이 확인란을 선택 하면 **적용** 단추를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-137">If you select the check box, the **Apply** button becomes available.</span></span> <span data-ttu-id="be660-138">**적용**을 클릭 하면 대상 인스턴스에서 비규격 설정이 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be660-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instance.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="be660-139">대상 인스턴스를 자동으로 업데이트하기 전에 정책 설정을 충분히 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="be660-140">하나 이상의 확인란을 선택한 후에는 **스크립트**를 클릭 하 고 출력 위치를 선택 하 여 [!INCLUDE[tsql](../includes/tsql-md.md)] 변경 내용을 적용 하기 전에 기본 코드를 검토할 수 있도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="be660-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
7.  <span data-ttu-id="be660-141">정책에 대 한 자세한 결과를 보려면 **결과** 테이블에서 정책을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be660-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="be660-142">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="be660-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="be660-143">등록된 서버를 사용하여 요청 시 평가 수행</span><span class="sxs-lookup"><span data-stu-id="be660-143">Perform an On-Demand Evaluation by Using Registered Servers</span></span>](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
