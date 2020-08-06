---
title: 정책 기반 관리 정책 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e76b4dce17e00bae5e8ca4fcf071868c0641c786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651666"
---
# <a name="create-a-policy-based-management-policy"></a><span data-ttu-id="bb4f5-102">정책 기반 관리 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="bb4f5-102">Create a Policy-Based Management Policy</span></span>
  <span data-ttu-id="bb4f5-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 정책을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-103">This topic describes how to create a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="bb4f5-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bb4f5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bb4f5-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bb4f5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bb4f5-106">보안</span><span class="sxs-lookup"><span data-stu-id="bb4f5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bb4f5-107">**다음을 사용하여 정책을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="bb4f5-107">**To create a policy, using:**</span></span>  
  
     [<span data-ttu-id="bb4f5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb4f5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bb4f5-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bb4f5-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bb4f5-110">보안</span><span class="sxs-lookup"><span data-stu-id="bb4f5-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bb4f5-111">권한</span><span class="sxs-lookup"><span data-stu-id="bb4f5-111">Permissions</span></span>  
 <span data-ttu-id="bb4f5-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bb4f5-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bb4f5-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-policy"></a><span data-ttu-id="bb4f5-114">정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bb4f5-114">To create a policy</span></span>  
  
1.  <span data-ttu-id="bb4f5-115">**개체 탐색기**에서 더하기 기호를 클릭하여 새로운 정책 기반 관리 정책을 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a new a Policy-Based Management policy.</span></span>  
  
2.  <span data-ttu-id="bb4f5-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="bb4f5-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="bb4f5-118">**정책** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 정책**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-118">Right-click the **Policies** folder and select **New Policy**.</span></span>  
  
5.  <span data-ttu-id="bb4f5-119">**새 정책 만들기** 대화 상자의 **이름** 상자에 새 정책의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-119">In the **Create New Policy** dialog box, in the **Name** box, type the name of the new policy.</span></span>  
  
6.  <span data-ttu-id="bb4f5-120">정책을 만든 즉시 사용하려면 **사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-120">If you want the policy to be enabled as soon as it is created, select the **Enabled** check box.</span></span> <span data-ttu-id="bb4f5-121">평가 모드가 **요청 시**인 경우 **사용** 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-121">If the evaluation mode is **On demand**, the **Enabled** check box is not available.</span></span>  
  
7.  <span data-ttu-id="bb4f5-122">**조건 확인** 목록에서 기존 조건 중 하나를 선택하거나 **새 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-122">In the **Check condition** list, select one of the existing conditions, or select **New Condition**.</span></span> <span data-ttu-id="bb4f5-123">조건을 편집하려면 조건을 선택한 다음 줄임표( **...** )를 클릭합니다. 자세한 내용은 [새로운 정책 기반 관리 조건 만들기](create-a-new-policy-based-management-condition.md) 또는 [정책 기반 관리 조건의 속성 보기 또는 수정](view-or-modify-the-properties-of-a-policy-based-management-condition.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-123">To edit a condition, select the condition and then click the ellipsis (**...**). For more information, see [Create a New Policy-Based Management Condition](create-a-new-policy-based-management-condition.md) or [View or Modify the Properties of a Policy-Based Management Condition](view-or-modify-the-properties-of-a-policy-based-management-condition.md).</span></span>  
  
8.  <span data-ttu-id="bb4f5-124">**적용 대상** 상자에서 이 정책의 대상 유형을 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-124">In the **Against targets** box, select one or more target types for this policy.</span></span> <span data-ttu-id="bb4f5-125">일부 조건 및 패싯만 특정 대상 유형에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-125">Some conditions and facets can only be applied to certain types of targets.</span></span> <span data-ttu-id="bb4f5-126">사용 가능한 대상 집합이 관련 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-126">The available target sets appear in the associated box.</span></span> <span data-ttu-id="bb4f5-127">**매** 를 확장하여 일부 대상 유형에 대한 필터링 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-127">Expand **Every** to select a filtering condition for some types of the targets.</span></span> <span data-ttu-id="bb4f5-128">이 상자에 대상이 표시되지 않으면 검사 조건 범위가 서버 수준으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-128">If no targets appear in this box, the check condition is scoped at the server level.</span></span>  
  
9. <span data-ttu-id="bb4f5-129">**평가 모드** 상자에서 이 정책의 동작 방식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-129">In the **Evaluation Mode** box, select how this policy will behave.</span></span> <span data-ttu-id="bb4f5-130">서로 다른 조건은 서로 다른 유효한 평가 모드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-130">Different conditions can have different valid evaluation modes.</span></span> <span data-ttu-id="bb4f5-131">유효한 평가 모드에 대한 자세한 내용은 [정책 기반 관리를 사용하여 서버 관리](administer-servers-by-using-policy-based-management.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-131">For more information about which evaluation modes are valid, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
10. <span data-ttu-id="bb4f5-132">일정에 따라 정책이 평가되는 경우 평가 모드를 **예약 시**로 설정하고 **선택** 을 클릭하여 일정을 선택하거나 **새로 만들기** 를 클릭하여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-132">If the policy will be evaluated on a schedule, set the evaluation mode to **On schedule**, and then click **Pick** to select a schedule, or click **New** to create a new schedule.</span></span>  
  
11. <span data-ttu-id="bb4f5-133">정책을 대상 유형의 하위 집합으로 제한하려면 **서버 제한** 상자에 있는 제한 조건 중에서 선택하거나 새 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-133">To limit the policy to subset of the target types, in the **Server restriction** box, select from limiting conditions or create a new condition.</span></span>  
  
     <span data-ttu-id="bb4f5-134">**새 정책 만들기** 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [새 정책 만들기 또는 정책 열기 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md) 또는 [새 정책 만들기 또는 정책 열기 대화 상자, 설명 페이지](create-new-policy-or-open-policy-dialog-box-description-page.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-134">For more information on the available options in the **Create New Policy** dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) or [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
12. <span data-ttu-id="bb4f5-135">완료되면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb4f5-135">When finished click **OK**.</span></span>  
  
  
