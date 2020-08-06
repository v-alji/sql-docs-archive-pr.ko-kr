---
title: 쿼리 조건 지정 (사용 빈도 기반 최적화 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3b93034a089ff3121155e35de4cec96846824a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648615"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a><span data-ttu-id="f3561-102">쿼리 조건 지정(사용 빈도 기반 최적화 마법사)</span><span class="sxs-lookup"><span data-stu-id="f3561-102">Specify Query Criteria (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="f3561-103">최적화할 쿼리를 식별하기 위해 **쿼리 조건 지정** 페이지를 사용하여 하나 이상의 필터 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-103">Use the **Specify Query Criteria** page to choose one or more filter options in order to identify queries to optimize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3561-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 쿼리 로그에 연결할 수 없는 경우에는 이 페이지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-104">This page is disabled if [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cannot connect to the query log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3561-105">옵션</span><span class="sxs-lookup"><span data-stu-id="f3561-105">Options</span></span>  
 <span data-ttu-id="f3561-106">**쿼리 로그 통계**</span><span class="sxs-lookup"><span data-stu-id="f3561-106">**Query log statistics**</span></span>  
 <span data-ttu-id="f3561-107">선택한 파티션에 대한 쿼리 로그에 저장된 쿼리 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-107">Displays information about the queries stored in the query log for the selected partitions.</span></span> <span data-ttu-id="f3561-108">다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-108">The following items are displayed:</span></span>  
  
|<span data-ttu-id="f3561-109">용어</span><span class="sxs-lookup"><span data-stu-id="f3561-109">Term</span></span>|<span data-ttu-id="f3561-110">정의</span><span class="sxs-lookup"><span data-stu-id="f3561-110">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f3561-111">**총 쿼리**</span><span class="sxs-lookup"><span data-stu-id="f3561-111">**Total queries**</span></span>|<span data-ttu-id="f3561-112">선택한 파티션에 대한 쿼리 로그에 저장된 총 쿼리 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-112">Displays the total number of queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3561-113">**고유 쿼리**</span><span class="sxs-lookup"><span data-stu-id="f3561-113">**Distinct queries**</span></span>|<span data-ttu-id="f3561-114">선택한 파티션에 대한 쿼리 로그에 저장된 고유한 쿼리 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-114">Displays the number of distinct queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3561-115">**고유한 사용자**</span><span class="sxs-lookup"><span data-stu-id="f3561-115">**Distinct users**</span></span>|<span data-ttu-id="f3561-116">선택한 파티션에 대한 쿼리 로그에 저장된 쿼리와 연결된 고유한 사용자의 총 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-116">Displays the total number of distinct users associated with queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="f3561-117">**평균 응답 시간**</span><span class="sxs-lookup"><span data-stu-id="f3561-117">**Average response time**</span></span>|<span data-ttu-id="f3561-118">선택한 파티션에 대한 쿼리 로그에 저장된 쿼리의 평균 응답 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-118">Displays the average response time for queries stored in the query log for the selected partitions.</span></span>|  
  
 <span data-ttu-id="f3561-119">**시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="f3561-119">**Beginning date**</span></span>  
 <span data-ttu-id="f3561-120">시작 날짜와 시간을 기준으로 쿼리 로그의 쿼리를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-120">Filters queries in the query log based on a starting date and time.</span></span> <span data-ttu-id="f3561-121">드롭다운 목록에서 날짜를 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-121">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3561-122">**종료 날짜** 를 선택하지 않으면 쿼리 로그에서 이 옵션에 대해 지정한 날짜와 시간 이후의 모든 쿼리를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-122">If **Ending date** is not selected, all queries in the query log on or after the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="f3561-123">**종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="f3561-123">**Ending date**</span></span>  
 <span data-ttu-id="f3561-124">종료 날짜와 시간을 기준으로 쿼리 로그의 쿼리를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-124">Filters queries in the query log based on an ending date and time.</span></span> <span data-ttu-id="f3561-125">드롭다운 목록에서 날짜를 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-125">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3561-126">**시작 날짜** 를 선택하지 않으면 쿼리 로그에서 이 옵션에 대해 지정한 날짜와 시간 이전의 모든 쿼리를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-126">If **Beginning date** is not selected, all queries in the query log on or before the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="f3561-127">**사용자**</span><span class="sxs-lookup"><span data-stu-id="f3561-127">**Users**</span></span>  
 <span data-ttu-id="f3561-128">지정한 사용자 집합을 기준으로 쿼리 로그의 쿼리를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-128">Filters queries in the query log based on a specified set of users.</span></span> <span data-ttu-id="f3561-129">줄임표(**...**) 단추를 클릭하여 **사용자 선택** 대화 상자를 표시하고 쿼리 필터링 기준으로 사용할 사용자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-129">Click the ellipsis (**...**) button to display the **User Selection** dialog box and choose users on which to filter queries.</span></span> <span data-ttu-id="f3561-130">**사용자 선택** 대화 상자에 대한 자세한 내용은 [사용자 선택 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3561-130">For more information about the **User Selection** dialog box, see [User Selection Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="f3561-131">**가장 자주 사용하는 쿼리**</span><span class="sxs-lookup"><span data-stu-id="f3561-131">**Most frequent queries**</span></span>  
 <span data-ttu-id="f3561-132">선택한 파티션에 대해 가장 자주 실행한 고유한 쿼리의 최상위 백분율을 기준으로 쿼리 로그의 쿼리를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-132">Filters queries in the query log based on the topmost percentage of the distinct queries most often run for the selected partitions.</span></span> <span data-ttu-id="f3561-133">입력란에서 백분율 값을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3561-133">Choose or type a percent value in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3561-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3561-134">See Also</span></span>  
 <span data-ttu-id="f3561-135">[사용 빈도 기반 최적화 마법사 F1 도움말](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f3561-135">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="f3561-136">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f3561-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
