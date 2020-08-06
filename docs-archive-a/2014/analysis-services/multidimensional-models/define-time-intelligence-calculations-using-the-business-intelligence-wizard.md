---
title: 비즈니스 인텔리전스 마법사를 사용 하 여 시간 인텔리전스 계산 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 222efb572c227e6a8ca3d1e2295b662cb586184a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647299"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a><span data-ttu-id="7bf47-102">비즈니스 인텔리전스 마법사를 사용하여 시간 인텔리전스 계산 정의</span><span class="sxs-lookup"><span data-stu-id="7bf47-102">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>
  <span data-ttu-id="7bf47-103">시간 인텔리전스 기능은 선택한 계층에 시간 계산(또는 시간 보기)을 추가하는 큐브 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-103">The time intelligence enhancement is a cube enhancement that adds time calculations (or time views) to a selected hierarchy.</span></span> <span data-ttu-id="7bf47-104">이 기능은 다음과 같은 계산 범주를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-104">This enhancement supports the following categories of calculations:</span></span>  
  
-   <span data-ttu-id="7bf47-105">월간 누계</span><span class="sxs-lookup"><span data-stu-id="7bf47-105">Period to date.</span></span>  
  
-   <span data-ttu-id="7bf47-106">기간별 증가</span><span class="sxs-lookup"><span data-stu-id="7bf47-106">Period over period growth.</span></span>  
  
-   <span data-ttu-id="7bf47-107">이동 평균</span><span class="sxs-lookup"><span data-stu-id="7bf47-107">Moving averages.</span></span>  
  
-   <span data-ttu-id="7bf47-108">동일 기간 비교</span><span class="sxs-lookup"><span data-stu-id="7bf47-108">Parallel period comparisons.</span></span>  
  
 <span data-ttu-id="7bf47-109">시간 차원이 있는 큐브에 시간 인텔리전스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-109">You apply time intelligence to cubes that have a time dimension.</span></span> <span data-ttu-id="7bf47-110">시간 차원은 차원의 `Type` 속성이 `Time`으로 설정되어 있는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-110">(A time dimension is a dimension whose `Type` property is set to `Time`).</span></span> <span data-ttu-id="7bf47-111">또한 해당 차원의 시간 특성에는 관련 `Type` 속성에 대한 적절한 설정(예: Years 또는 Months)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-111">Additionally, the time attributes of that dimension must also have the appropriate setting (such as, Years or Months) for their `Type` property.</span></span> <span data-ttu-id="7bf47-112">차원 마법사를 사용하여 시간 차원을 만들면 차원과 차원의 특성 모두에 대한 `Type` 속성이 올바르게 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-112">The `Type` property of both the dimension and its attributes will be set correctly if you use the Dimension Wizard to create the time dimension.</span></span>  
  
 <span data-ttu-id="7bf47-113">큐브에 시간 인텔리전스를 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **시간 인텔리전스 정의** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-113">To add time intelligence to a cube, you use the Business Intelligence Wizard, and select the **Define time intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="7bf47-114">그런 다음 마법사의 안내를 따라 시간 인텔리전스를 추가할 계층을 선택하고 계층에서 시간 인텔리전스를 적용할 멤버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-114">This wizard then guides you through the steps of selecting a hierarchy to which you are adding time intelligence and specifying which members in the hierarchy will have time intelligence applied to them.</span></span> <span data-ttu-id="7bf47-115">마법사의 마지막 페이지에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 선택한 시간 인텔리전스를 추가 하기 위해 데이터베이스에 적용 되는 변경 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-115">On the last page of the wizard, you can see the changes that will be made to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to add the selected time intelligence.</span></span>  
  
## <a name="selecting-a-time-hierarchy"></a><span data-ttu-id="7bf47-116">시간 계층 선택</span><span class="sxs-lookup"><span data-stu-id="7bf47-116">Selecting a Time Hierarchy</span></span>  
 <span data-ttu-id="7bf47-117">**대상 계층 및 계산 선택** 페이지에서 시간 기능을 적용할 시간 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-117">On the **Choose Target Hierarchy and Calculations** page, you select the time hierarchy to which the time enhancement applies.</span></span> <span data-ttu-id="7bf47-118">비즈니스 인텔리전스 마법사를 실행할 때마다 시간 계층 하나에만 시간 기능을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-118">You can apply the time enhancement to only one time hierarchy every time that you run the Business Intelligence Wizard.</span></span> <span data-ttu-id="7bf47-119">여러 시간 계층에 기능을 적용하려면 마법사를 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-119">If you want to apply the enhancement to more than one time hierarchy, you run the wizard again.</span></span>  
  
 <span data-ttu-id="7bf47-120">시간 계층을 선택한 후 **사용 가능한 시간 계산** 목록에서 계층에 적용할 계산을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-120">After you select a time hierarchy, in the **Available time calculations** list, you select the calculations that apply to the hierarchy.</span></span> <span data-ttu-id="7bf47-121">나열되는 계산은 계층의 수준과 각 수준의 특성에 대한 `Type` 속성 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-121">The calculations that are listed depend on the levels in the hierarchy, and on the `Type` property setting for the attribute for each level.</span></span> <span data-ttu-id="7bf47-122">예를 들어 년 계층은 연간 누계 및 전년동기대비 성장을 지원하지만 분기 계층은 이러한 계산을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-122">For example, a Years hierarchy supports Year to Date and Year Over Year Growth, but a Quarters hierarchy does not.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bf47-123">Timeintelligence.xml 템플릿 파일은 **사용 가능한 시간 계산**에 나열되는 시간 계산을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-123">The Timeintelligence.xml template file defines the time calculations that are listed in **Available time calculations**.</span></span> <span data-ttu-id="7bf47-124">나열된 계산이 요구에 맞지 않으면 기존 계산을 변경하거나 Timeintelligence.xml 파일에 새 계산을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-124">If the listed calculations do not meet your needs, you can either change the existing calculations or add new calculations to the Timeintelligence.xml file.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7bf47-125">계산에 대한 설명을 보려면 위와 아래 화살표를 사용하여 원하는 계산을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-125">To view a description for a calculation, use the up and down arrows to highlight that calculation.</span></span>  
  
## <a name="apply-time-views-to-members"></a><span data-ttu-id="7bf47-126">멤버에 시간 보기 적용</span><span class="sxs-lookup"><span data-stu-id="7bf47-126">Apply Time Views to Members</span></span>  
 <span data-ttu-id="7bf47-127">**계산 범위 정의** 페이지에서 새 시간 보기를 적용할 멤버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-127">On the **Define Scope of Calculations** page, you specify the members to which the new time views apply.</span></span> <span data-ttu-id="7bf47-128">다음 개체 중 하나에 새 시간 보기를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-128">You can apply the new time views to one of the following objects:</span></span>  
  
-   <span data-ttu-id="7bf47-129">**계정 차원의 멤버\*\*\*\*계산 범위 정의** 페이지의 **사용 가능한 측정값** 목록에는 계정 차원이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-129">**Members of an account dimension** On the **Define Scope of Calculations** page, the **Available measures** list includes account dimensions.</span></span> <span data-ttu-id="7bf47-130">계정 차원의 `Type` 속성은 `Accounts`로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-130">Account dimensions have their `Type` properties set to `Accounts`.</span></span> <span data-ttu-id="7bf47-131">계정 차원이 있지만 해당 차원이 **사용 가능한 측정값** 목록에 나타나지 않으면 비즈니스 인텔리전스 마법사를 사용하여 해당 차원에 계정 인텔리전스를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-131">If you have an accounts dimension but that dimension does not appear in the **Available measures** list, you can use the Business Intelligence Wizard to apply the account intelligence to that dimension.</span></span> <span data-ttu-id="7bf47-132">자세한 내용은 [차원에 계정 인텔리전스 추가](bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7bf47-132">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
-   <span data-ttu-id="7bf47-133">**측정값** 계정 차원을 지정하는 대신 시간 보기가 적용될 측정값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-133">**Measures** Instead of specifying an account dimension, you can specify the measures to which the time views apply.</span></span> <span data-ttu-id="7bf47-134">이 경우 선택한 시간 계산을 적용할 보기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-134">In this case, select the views to which selected time calculations apply.</span></span> <span data-ttu-id="7bf47-135">예를 들어 자산과 부채는 연간 누계 데이터이므로 자산이나 부채 측정값에는 연간 누계 계산을 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-135">For example, assets and liabilities are year-to-date data; therefore, you do not apply a Year-to-Date calculation to assets or liabilities measures.</span></span>  
  
## <a name="viewing-the-time-intelligence-enhancement"></a><span data-ttu-id="7bf47-136">시간 인텔리전스 기능 보기</span><span class="sxs-lookup"><span data-stu-id="7bf47-136">Viewing the Time Intelligence Enhancement</span></span>  
 <span data-ttu-id="7bf47-137">비즈니스 인텔리전스 마법사의 마지막 페이지에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 변경 사항을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-137">On the final page of the Business Intelligence Wizard, you can view the changes that will be made to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="7bf47-138">시간 인텔리전스 기능의 경우 다음 표에서 설명하는 것처럼 마법사에서 선택한 시간 차원, 연결된 데이터 원본 뷰 및 연결된 큐브를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-138">For a time intelligence enhancement, the wizard will change the selected time dimension, associated data source view, and associated cube as described in the following table.</span></span>  
  
|<span data-ttu-id="7bf47-139">Object</span><span class="sxs-lookup"><span data-stu-id="7bf47-139">Object</span></span>|<span data-ttu-id="7bf47-140">변화</span><span class="sxs-lookup"><span data-stu-id="7bf47-140">Change</span></span>|  
|------------|------------|  
|<span data-ttu-id="7bf47-141">시간 차원</span><span class="sxs-lookup"><span data-stu-id="7bf47-141">Time dimension</span></span>|<span data-ttu-id="7bf47-142">각 계산(또는 보기)에 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-142">Adds an attribute for each calculation (or view).</span></span>|  
|<span data-ttu-id="7bf47-143">데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="7bf47-143">Data source view</span></span>|<span data-ttu-id="7bf47-144">시간 차원의 각 새 특성에 대한 시간 테이블에 계산 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-144">Adds a calculated column in the time table for each new attribute in the time dimension.</span></span>|  
|<span data-ttu-id="7bf47-145">큐브</span><span class="sxs-lookup"><span data-stu-id="7bf47-145">Cube</span></span>|<span data-ttu-id="7bf47-146">계산을 수행하는 MDX(Multidimensional Expressions) 코드를 정의하는 계산 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7bf47-146">Adds a calculated member that defines the Multidimensional Expressions (MDX) code to perform the calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bf47-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7bf47-147">See Also</span></span>  
 [<span data-ttu-id="7bf47-148">계산 멤버 만들기</span><span class="sxs-lookup"><span data-stu-id="7bf47-148">Create Calculated Members</span></span>](create-calculated-members.md)  
  
  
