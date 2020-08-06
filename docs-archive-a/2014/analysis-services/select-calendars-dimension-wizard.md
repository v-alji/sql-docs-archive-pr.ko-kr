---
title: 달력 선택 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651919"
---
# <a name="select-calendars-dimension-wizard"></a><span data-ttu-id="4cd55-102">달력 선택(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="4cd55-102">Select Calendars (Dimension Wizard)</span></span>
  <span data-ttu-id="4cd55-103">**달력 선택** 페이지를 사용하여 시간 차원에 대한 회계 달력, 보고 달력, 제조 달력 또는 ISO(International Standards Organization) 8601 달력을 나타내는 추가 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-103">Use the **Select Calendars** page to create additional hierarchies representing fiscal, reporting, manufacturing, or International Standards Organization (ISO) 8601 calendars for the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-104"> 이 페이지는 **차원 유형 선택** 페이지에서 **서버 시간 차원** 을 선택했거나 **차원 정의** 페이지에서 **데이터 원본을 사용하지 않고 차원 생성** 을 선택한 다음 **차원 유형 선택** 페이지에서 **시간 차원** 을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Dimension Definition** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4cd55-105">옵션</span><span class="sxs-lookup"><span data-stu-id="4cd55-105">Options</span></span>  
 <span data-ttu-id="4cd55-106">**회계 달력**</span><span class="sxs-lookup"><span data-stu-id="4cd55-106">**Fiscal calendar**</span></span>  
 <span data-ttu-id="4cd55-107">회계 달력을 기반으로 시간 계층을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-107">Select to create a time hierarchy based on a fiscal calendar.</span></span>  
  
 <span data-ttu-id="4cd55-108">**시작 일 및 월**</span><span class="sxs-lookup"><span data-stu-id="4cd55-108">**Start day and month**</span></span>  
 <span data-ttu-id="4cd55-109">회계 달력의 시작 일 및 월을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-109">Select the day and month on which the fiscal calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-110">이 옵션은 **회계 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-110">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-111">**회계 달력 명명 규칙**</span><span class="sxs-lookup"><span data-stu-id="4cd55-111">**Fiscal calendar naming convention**</span></span>  
 <span data-ttu-id="4cd55-112">회계 달력에 사용할 명명 규칙을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-112">Select the naming convention used by the fiscal calendar.</span></span> <span data-ttu-id="4cd55-113">**역년 이름** 또는 **역년 이름 + 1**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-113">Select either **Calendar year name** or **Calendar year name +1**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-114">이 옵션은 **회계 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-114">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-115">**보고/마케팅 달력**</span><span class="sxs-lookup"><span data-stu-id="4cd55-115">**Reporting (or marketing) calendar**</span></span>  
 <span data-ttu-id="4cd55-116">보고 달력을 기반으로 시간 계층을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-116">Select to create a time hierarchy based on a reporting calendar.</span></span>  
  
 <span data-ttu-id="4cd55-117">**시작 주 및 월**</span><span class="sxs-lookup"><span data-stu-id="4cd55-117">**Start week and month**</span></span>  
 <span data-ttu-id="4cd55-118">보고 달력의 시작 주 및 월을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-118">Select the week and month on which the reporting calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-119">이 옵션은 **보고/마케팅 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-119">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-120">**월간 주 패턴**</span><span class="sxs-lookup"><span data-stu-id="4cd55-120">**Week by month pattern**</span></span>  
 <span data-ttu-id="4cd55-121">보고 달력에 사용할 월간 주 패턴을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-121">Select the week by month pattern used by the reporting calendar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-122">이 옵션은 **보고/마케팅 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-122">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-123">다음 표에서는 월간 주 패턴에 사용할 수 있는 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-123">The following table lists the options available for the week by month pattern.</span></span>  
  
|<span data-ttu-id="4cd55-124">값</span><span class="sxs-lookup"><span data-stu-id="4cd55-124">Value</span></span>|<span data-ttu-id="4cd55-125">Description</span><span class="sxs-lookup"><span data-stu-id="4cd55-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4cd55-126">**주 445**</span><span class="sxs-lookup"><span data-stu-id="4cd55-126">**Week 445**</span></span>|<span data-ttu-id="4cd55-127">사분기의 첫 번째 달에 4주, 두 번째 달에 4주, 세 번째 달에 5주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-127">The first month in the quarter has 4 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 5 weeks.</span></span>|  
|<span data-ttu-id="4cd55-128">**주 454**</span><span class="sxs-lookup"><span data-stu-id="4cd55-128">**Week 454**</span></span>|<span data-ttu-id="4cd55-129">사분기의 첫 번째 달에 4주, 두 번째 달에 5주, 세 번째 달에 4주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-129">The first month in the quarter has 4 weeks, the second month in the quarter has 5 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
|<span data-ttu-id="4cd55-130">**주 544**</span><span class="sxs-lookup"><span data-stu-id="4cd55-130">**Week 544**</span></span>|<span data-ttu-id="4cd55-131">사분기의 첫 번째 달에 5주, 두 번째 달에 4주, 세 번째 달에 4주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-131">The first month in the quarter has 5 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
  
 <span data-ttu-id="4cd55-132">**제조 달력**</span><span class="sxs-lookup"><span data-stu-id="4cd55-132">**Manufacturing calendar**</span></span>  
 <span data-ttu-id="4cd55-133">제조 달력을 기반으로 시간 계층을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-133">Select to create a time hierarchy based on a manufacturing calendar.</span></span>  
  
 <span data-ttu-id="4cd55-134">**시작 주 및 월**</span><span class="sxs-lookup"><span data-stu-id="4cd55-134">**Start week and month**</span></span>  
 <span data-ttu-id="4cd55-135">제조 달력의 시작 주 및 월을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-135">Select the week and month on which the manufacturing calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-136">이 옵션은 **제조 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-136">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-137">**추가 기간이 있는 사분기**</span><span class="sxs-lookup"><span data-stu-id="4cd55-137">**Quarter with extra periods**</span></span>  
 <span data-ttu-id="4cd55-138">추가 기간이 포함될 사분기를 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-138">Select or type the quarter that will contain the extra periods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd55-139">이 옵션은 **제조 달력** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-139">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="4cd55-140">**ISO 8601 달력**</span><span class="sxs-lookup"><span data-stu-id="4cd55-140">**ISO 8601 calendar**</span></span>  
 <span data-ttu-id="4cd55-141">ISO 8601 달력을 기반으로 계층을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd55-141">Select to create a hierarchy based on the ISO 8601 calendar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd55-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cd55-142">See Also</span></span>  
 <span data-ttu-id="4cd55-143">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4cd55-143">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="4cd55-144">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4cd55-144">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="4cd55-145">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="4cd55-145">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
