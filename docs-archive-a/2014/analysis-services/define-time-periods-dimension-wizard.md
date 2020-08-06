---
title: 기간 정의 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timefrequency.f1
ms.assetid: 6bda6b7e-d306-4e68-9acb-84de8f44d1b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88b69eaa265b7a98f7d32063b602897d02016fa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660196"
---
# <a name="define-time-periods-dimension-wizard"></a><span data-ttu-id="b6eca-102">기간 정의(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="b6eca-102">Define Time Periods (Dimension Wizard)</span></span>
  <span data-ttu-id="b6eca-103">**기간 정의** 페이지를 사용하여 시간 차원 또는 서버 시간 차원에 포함할 역년 정보 및 시간 빈도를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-103">Use the **Define Time Periods** page to define the calendar year information and time frequencies to include in the time dimension or server time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6eca-104"> 이 페이지는 **차원 유형 선택** 페이지에서 **서버 시간 차원** 을 선택했거나 **생성 방법 선택** 페이지에서 **데이터 원본을 사용하지 않고 차원 생성** 을 선택한 다음 **차원 유형 선택** 페이지에서 **시간 차원** 을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Select Build Method** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b6eca-105">이 페이지는 시간 차원의 역년을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-105">This page is for defining the calendar year of a time dimension.</span></span> <span data-ttu-id="b6eca-106">시간 차원에 대해 회계 연도, 제조 연도, 보고 연도 또는 ISO(International Standards Organization) 8601 연도를 정의하려면 **달력 선택** 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-106">To define a fiscal, manufacturing, reporting, or International Standards Organization (ISO) 8601 year for the time dimension, use the **Select Calendars** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6eca-107">옵션</span><span class="sxs-lookup"><span data-stu-id="b6eca-107">Options</span></span>  
 <span data-ttu-id="b6eca-108">**첫 번째 역일**</span><span class="sxs-lookup"><span data-stu-id="b6eca-108">**First calendar day**</span></span>  
 <span data-ttu-id="b6eca-109">현재 연도의 시작 날짜를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-109">Type or select the day that begins the current year.</span></span>  
  
 <span data-ttu-id="b6eca-110">**마지막 역일**</span><span class="sxs-lookup"><span data-stu-id="b6eca-110">**Last calendar day**</span></span>  
 <span data-ttu-id="b6eca-111">현재 연도의 종료 날짜를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-111">Type or select the day that ends the current year.</span></span>  
  
 <span data-ttu-id="b6eca-112">**첫 번째 요일**</span><span class="sxs-lookup"><span data-stu-id="b6eca-112">**First day of the week**</span></span>  
 <span data-ttu-id="b6eca-113">한 주의 시작 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-113">Select the day that begins a week.</span></span>  
  
 <span data-ttu-id="b6eca-114">**기간**</span><span class="sxs-lookup"><span data-stu-id="b6eca-114">**Time periods**</span></span>  
 <span data-ttu-id="b6eca-115">시간 차원의 역년 기간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-115">Select the time periods for the calendar year of the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6eca-116">`Date` 기간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-116">The `Date` time period is required.</span></span>  
  
 <span data-ttu-id="b6eca-117">**시간 멤버 이름의 언어**</span><span class="sxs-lookup"><span data-stu-id="b6eca-117">**Language for time member names**</span></span>  
 <span data-ttu-id="b6eca-118">시간 차원의 멤버의 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6eca-118">Select the language for the members in the time dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6eca-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6eca-119">See Also</span></span>  
 <span data-ttu-id="b6eca-120">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b6eca-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="b6eca-121">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b6eca-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b6eca-122">[다차원 모델의 차원](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="b6eca-122">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="b6eca-123">달력 &#40;차원 마법사를 선택&#41;</span><span class="sxs-lookup"><span data-stu-id="b6eca-123">Select Calendars &#40;Dimension Wizard&#41;</span></span>](select-calendars-dimension-wizard.md)  
  
  
