---
title: '12 단원: 역할 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 962cd19726a5404de81e20a2209b25b9cc277e21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639047"
---
# <a name="lesson-12-create-roles"></a><span data-ttu-id="ae08c-102">12단원: 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="ae08c-102">Lesson 12: Create Roles</span></span>
  <span data-ttu-id="ae08c-103">이 단원에서는 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-103">In this lesson, you will create roles.</span></span> <span data-ttu-id="ae08c-104">역할은 역할 멤버인 Windows 사용자로만 액세스를 제한함으로써 모델 데이터베이스 개체 및 데이터에 보안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-104">Roles provide model database object and data security by limiting access to only those Windows users which are role members.</span></span> <span data-ttu-id="ae08c-105">각 역할은 단일 사용 권한(없음, 읽기, 읽기 및 프로세스, 프로세스 또는 관리자)으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-105">Each role is defined with a single permission: None, Read, Read and Process, Process, or Administrator.</span></span> <span data-ttu-id="ae08c-106">모델을 제작하는 중에 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 역할 관리자 대화 상자를 사용하여 역할을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-106">Roles can be defined during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="ae08c-107">모델을 배포한 후 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 역할을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-107">After a model has been deployed, you can manage roles by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ae08c-108">자세한 내용은 [역할&#40;SSAS 테이블 형식&#41;](tabular-models/roles-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae08c-108">To learn more, see [Roles &#40;SSAS Tabular&#41;](tabular-models/roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae08c-109">이 자습서를 완료하기 위해 역할을 만들 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-109">Creating roles is not necessary to complete this tutorial.</span></span> <span data-ttu-id="ae08c-110">기본적으로 현재 로그인한 계정은 모델에 대해 관리자 권한을 포함하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-110">By default, the account you are currently logged in with will have Administrator privileges on the model.</span></span> <span data-ttu-id="ae08c-111">그러나 조직의 다른 사용자가 보고 클라이언트 애플리케이션을 통해 모델을 검색할 수 있도록 하려면 읽기 권한을 가진 역할을 하나 이상 만들어 해당 사용자를 멤버로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-111">However, to allow other users in your organization to browse the model by using a reporting client application, you must create at least one role with Read permissions and add those users as members.</span></span>  
  
 <span data-ttu-id="ae08c-112">세 가지 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-112">You will create three roles:</span></span>  
  
-   <span data-ttu-id="ae08c-113">판매 관리자-이 역할은 모든 모델 개체 및 데이터에 대 한 읽기 권한을 보유 하려는 조직의 사용자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-113">Sales Manager - This role can include users in your organization for which you want to have Read permission to all model objects and data.</span></span>  
  
-   <span data-ttu-id="ae08c-114">판매 분석가 US-이 역할에는 미국의 판매와 관련 된 데이터만 찾아볼 수 있도록 하려는 조직의 사용자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-114">Sales Analyst US - This role can include users in your organization for which you want only to be able to browse data related to sales in the US (United States).</span></span> <span data-ttu-id="ae08c-115">이 역할에 대해 DAX 수식을 사용하여 멤버가 미국에 대한 데이터만 검색할 수 있도록 제한하는 *행 필터*를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-115">For this role, you will use a DAX formula to define a *Row Filter*, which restricts members to browse data only for the United States.</span></span>  
  
-   <span data-ttu-id="ae08c-116">관리자-이 역할에는 모델 데이터베이스에 대 한 관리 태스크를 수행할 수 있는 권한이 나 무제한 액세스를 허용 하는 관리자 권한이 있는 사용자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-116">Administrator - This role can include users for which you want to have Administrator permission, which allows unlimited access and permissions to perform administrative tasks on the model database.</span></span>  
  
 <span data-ttu-id="ae08c-117">조직의 Windows 사용자 및 그룹 계정은 고유하므로 특정 조직의 계정을 멤버에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-117">Because Windows user and group accounts in your organization are unique, you can add accounts from your particular organization to members.</span></span> <span data-ttu-id="ae08c-118">그러나 이 자습서에서는 멤버를 비워둘 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-118">However, for this tutorial, you can also leave the members blank.</span></span> <span data-ttu-id="ae08c-119">나중에 12단원: Excel에서 분석에서 각 역할의 영향을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-119">You will still be able to test the effect of each role later in Lesson 12: Analyze in Excel.</span></span>  
  
 <span data-ttu-id="ae08c-120">이 단원을 완료하기 위한 예상 시간: **15분**</span><span class="sxs-lookup"><span data-stu-id="ae08c-120">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ae08c-121">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ae08c-121">Prerequisites</span></span>  
 <span data-ttu-id="ae08c-122">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-122">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="ae08c-123">이 단원의 태스크를 수행하려면 이전 단원인 [11단원: 파티션 만들기](lesson-10-create-partitions.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-123">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="create-roles"></a><span data-ttu-id="ae08c-124">역할 만들기</span><span class="sxs-lookup"><span data-stu-id="ae08c-124">Create Roles</span></span>  
  
#### <a name="to-create-a-sales-manager-user-role"></a><span data-ttu-id="ae08c-125">Sales Manager 사용자 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ae08c-125">To create a Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="ae08c-126">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="ae08c-127">**역할 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-127">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="ae08c-128">권한이 없는 새 역할이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-128">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="ae08c-129">새 역할을 클릭 한 다음 **이름** 열에서 역할의 이름을로 바꿉니다 `Internet Sales Manager` .</span><span class="sxs-lookup"><span data-stu-id="ae08c-129">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Manager`.</span></span>  
  
4.  <span data-ttu-id="ae08c-130">**사용 권한** 열에서 드롭다운 목록을 클릭한 후 **읽기** 권한을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-130">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="ae08c-131">선택 사항: **멤버** 탭을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-131">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="ae08c-132">**사용자 또는 그룹 선택** 대화 상자에서 역할에 포함하려는 조직에서 Windows 사용자 또는 그룹을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-132">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
7.  <span data-ttu-id="ae08c-133">선택 사항을 확인 한 다음 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-133">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a><span data-ttu-id="ae08c-134">Sales Analyst US 사용자 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ae08c-134">To create a Sales Analyst US user role</span></span>  
  
1.  <span data-ttu-id="ae08c-135">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="ae08c-136">**역할 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-136">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="ae08c-137">권한이 없는 새 역할이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-137">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="ae08c-138">새 역할을 클릭 한 다음 **이름** 열에서 역할의 이름을로 바꿉니다 `Internet Sales US` .</span><span class="sxs-lookup"><span data-stu-id="ae08c-138">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales US`.</span></span>  
  
4.  <span data-ttu-id="ae08c-139">**사용 권한** 열에서 드롭다운 목록을 클릭한 후 **읽기** 권한을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-139">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="ae08c-140">행 필터 탭을 클릭한 다음 **Geography** 테이블에 대해서만 DAX 필터 열에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-140">Click on the Row Filters tab, and then for the **Geography** table only, in the DAX Filter column, type the following formula:</span></span>  
  
     `=Geography[Country Region Code] = "US"`  
  
     <span data-ttu-id="ae08c-141">행 필터 수식은 부울(TRUE/FALSE) 값으로 확인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-141">A Row Filter formula must resolve to a Boolean (TRUE/FALSE) value.</span></span> <span data-ttu-id="ae08c-142">이 수식을 사용 하면 Country Region Code 값이 "US" 인 행만 사용자에 게 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-142">With this formula, you are specifying that only rows with the Country Region Code value of "US" be visible to the user.</span></span>  
  
     <span data-ttu-id="ae08c-143">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-143">When you have finished building the formula, press ENTER.</span></span>  
  
6.  <span data-ttu-id="ae08c-144">선택 사항: **멤버** 탭을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-144">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="ae08c-145">**사용자 또는 그룹 선택** 대화 상자에서 역할에 포함하려는 조직에서 Windows 사용자 또는 그룹을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-145">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
8.  <span data-ttu-id="ae08c-146">선택 사항을 확인 한 다음 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-146">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-an-administrator-role"></a><span data-ttu-id="ae08c-147">Administrator 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ae08c-147">To create an Administrator role</span></span>  
  
1.  <span data-ttu-id="ae08c-148">**역할 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-148">In the **Role Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="ae08c-149">새 역할을 클릭 한 다음 **이름** 열에서 역할의 이름을로 바꿉니다 `Internet Sales Administrator` .</span><span class="sxs-lookup"><span data-stu-id="ae08c-149">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Administrator`.</span></span>  
  
3.  <span data-ttu-id="ae08c-150">**사용 권한** 열에서 드롭다운 목록을 클릭한 다음 **관리자** 권한을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-150">In the **Permissions** column, click the dropdown list, and then select the **Administrator** permission.</span></span>  
  
4.  <span data-ttu-id="ae08c-151">**멤버** 탭을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-151">Click on the **Members** tab, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="ae08c-152">옵션: **사용자 또는 그룹 선택** 대화 상자에서 역할에 포함할 조직의 Windows 사용자 또는 그룹을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-152">Optional: In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
6.  <span data-ttu-id="ae08c-153">선택 사항을 확인 한 다음 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae08c-153">Verify your selections, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ae08c-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ae08c-154">Next Steps</span></span>  
 <span data-ttu-id="ae08c-155">이 자습서를 계속하려면 다음 단원인 [13단원: Excel에서 분석](lesson-12-analyze-in-excel.md)으로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="ae08c-155">To continue this tutorial, go to the next lesson: Lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
  
