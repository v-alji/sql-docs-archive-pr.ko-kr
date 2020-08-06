---
title: 숫자 및 날짜 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.placeholderproperties.number.f1
- sql12.rtp.rptdesigner.serieslabelproperties.number.f1
- "10127"
- sql12.rtp.rptdesigner.axisproperties.number.f1
- "10130"
- "10286"
- sql12.rtp.rptdesigner.textboxproperties.number.f1
- "10285"
ms.assetid: 6de1a725-9f06-4708-be26-2d55e442e344
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 597ff535e72bc174cc6f9bd5a226e95641ba8a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728016"
---
# <a name="formatting-numbers-and-dates-report-builder-and-ssrs"></a><span data-ttu-id="c5909-102">숫자 및 날짜 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c5909-102">Formatting Numbers and Dates (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c5909-103">해당 데이터 영역 **속성** 대화 상자의 **숫자** 페이지에서 형식을 선택하여 데이터 영역에 있는 숫자와 날짜의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-103">You can format numbers and dates in data regions by selecting a format from the **Number** page of the corresponding data region's **Properties** dialog box.</span></span>  
  
 <span data-ttu-id="c5909-104">입력란 보고서 항목 안에 있는 문자열의 형식을 지정하려면 형식을 지정할 항목을 선택하고 마우스 오른쪽 단추를 클릭한 후 **입력란 속성**을 선택하고 **숫자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-104">To specify format strings within a text box report item, you need to select the item that you want to format, right-click, select **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="c5909-105">테이블 또는 행렬의 셀은 개별 입력란이기 때문에 테이블이나 행렬 데이터 영역의 개별 셀에 형식을 지정할 때도 이 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-105">You can format individual cells in a table or matrix data region in the same manner, because cells in a table or matrix are individual text boxes.</span></span>  
  
 <span data-ttu-id="c5909-106">차트 데이터 영역은 범주(x) 축을 따라 날짜를 표시하고 값(y) 축을 따라 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-106">A chart data region commonly shows dates along the category (x) axis, and values along the value (y) axis.</span></span> <span data-ttu-id="c5909-107">차트에서 형식을 지정하려면 축을 마우스 오른쪽 단추로 클릭하고 **축 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-107">To specify formatting in a chart, right-click an axis and select **Axis Properties**.</span></span> <span data-ttu-id="c5909-108">값 축에서는 숫자에 대한 형식만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-108">On the value axis, you can specify formats only for numbers.</span></span> <span data-ttu-id="c5909-109">자세한 내용은 [차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5909-109">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c5909-110">계기 데이터 영역에서 형식을 지정하려면 계기의 눈금을 마우스 오른쪽 단추로 클릭하고 **방사형 눈금 속성** 또는 **선형 눈금 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-110">To specify formatting in a Gauge data region, right-click the scale of the gauge and select **Radial Scale Properties** or **Linear Scale Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5909-111">사용하려는 일부 서식 옵션이 회색으로 표시되어 있으면 해당 서식 옵션이 데이터 원본에 설정된 필드의 데이터 형식과 호환되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-111">If some formatting options you want to use are grayed out, it means that those formatting options are not compatible the field's data type, which is set in the data source.</span></span> <span data-ttu-id="c5909-112">예를 들어 필드에 숫자 값이 포함되어 있지만 필드의 데이터 형식이 문자열인 경우 통화 또는 10진수와 같은 숫자 데이터 서식 옵션을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-112">For example, if the field contains number values but the field's data type is String, you cannot apply numerical data formatting options such as currency or decimals.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="considerations-for-formatting-numbers-and-dates"></a><span data-ttu-id="c5909-113">숫자 및 날짜 형식 지정 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c5909-113">Considerations for Formatting Numbers and Dates</span></span>  
 <span data-ttu-id="c5909-114">보고서에서 숫자와 날짜의 형식을 지정하기 전에 다음을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-114">Before you format numbers and dates in your report, consider the following:</span></span>  
  
-   <span data-ttu-id="c5909-115">기본적으로 클라이언트 컴퓨터의 culture 설정에 따라 숫자 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-115">By default, numbers are formatted to reflect the cultural settings on the client computer.</span></span> <span data-ttu-id="c5909-116">형식 문자열을 사용하여 숫자 표시 방법을 지정하면 보고서를 보는 사람의 위치에 관계 없이 일관된 형식으로 숫자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-116">Use formatting strings to specify how numbers are displayed so that formatting is consistent regardless of where the person who is viewing the report is located.</span></span>  
  
-   <span data-ttu-id="c5909-117">**숫자** 페이지에서 제공되는 형식은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 표준 숫자 형식 문자열의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-117">The formats provided on the **Number** page are a subset of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard numeric format strings.</span></span> <span data-ttu-id="c5909-118">대화 상자에 표시되지 않는 사용자 지정 형식을 사용하여 숫자나 날짜에 형식을 지정하려는 경우에는 숫자 또는 날짜에 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 형식 문자열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-118">To format a number or date using a custom format that is not shown in the dialog box, you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] format strings for numbers or dates.</span></span> <span data-ttu-id="c5909-119">사용자 지정 형식 문자열에 대한 자세한 내용은 MSDN에서 [형식 지정](https://go.microsoft.com/fwlink/?LinkId=112024) 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c5909-119">For more information about custom format strings, see the [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) topic on MSDN.</span></span>  
  
-   <span data-ttu-id="c5909-120">사용자 지정 형식 문자열을 지정하면 culture별 기본 설정보다 높은 우선 순위를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-120">If a custom format string has been specified, it has a higher priority over default settings that are culture-specific.</span></span> <span data-ttu-id="c5909-121">예를 들어 숫자 1234를 1,234로 표시하기 위한 사용자 지정 형식 문자열인 "#,###"를 설정했다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-121">For example, suppose you set a custom format string of "#,###" to show the number 1234 as 1,234.</span></span> <span data-ttu-id="c5909-122">미국의 사용자와 유럽의 사용자는 이 형식 문자열을 다르게 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-122">This may have different meaning to users in the United States than it does to users in Europe.</span></span> <span data-ttu-id="c5909-123">사용자 지정 형식을 지정하기 전에, 선택한 형식이 해당 보고서를 보게 될 다른 culture의 사용자에게 어떤 영향을 줄지에 대해 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="c5909-123">Before you specify a custom format, consider how the format you choose will affect users of different cultures who may view the report.</span></span>  
  
-   <span data-ttu-id="c5909-124">잘못된 형식 문자열을 지정하면 형식 지정된 텍스트는 형식 지정을 무시하는 리터럴 문자열로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-124">If you specify an invalid format string, the formatted text is interpreted as a literal string which overrides the formatting.</span></span>  
  
-   <span data-ttu-id="c5909-125">같은 입력란에 함께 포함된 숫자와 문자의 형식을 지정할 때는 숫자를 나머지 텍스트와 구분하기 위해 자리 표시자를 사용하는 것을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="c5909-125">If you are formatting a mix of numbers and characters in the same text box, consider using a placeholder to format the number separately from the rest of the text.</span></span> <span data-ttu-id="c5909-126">자세한 내용은 [텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-126">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="c5909-127">입력란의 Format 속성에 잘못된 형식 문자열을 지정하면 형식 문자열이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-127">If an invalid format string is specified for the Format property on the text box, the format string is ignored.</span></span> <span data-ttu-id="c5909-128">차트나 계기의 Format 속성에 잘못된 형식 문자열을 지정하면 지정한 형식 문자열은 문자열로 해석되고 형식이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-128">If an invalid format string is specified for the Format property on the chart or gauge, the format string that you specified is interpreted as a string and formatting is not applied.</span></span>  
  
-   <span data-ttu-id="c5909-129">**범주** 에서 **통화** 를 선택하고 **값 표시 단위**를 선택한 경우 재무 형식을 사용하여 숫자를 표시하는 단위로 **천**, **백만**또는 **10억** 을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-129">If you select **Currency** under **Category** and you check **Show values in**, you can select **Thousands**, **Millions**, or **Billions** to display numbers using financial formats.</span></span> <span data-ttu-id="c5909-130">예를 들어 필드 값이 1,789,905,394인 경우 값 표시 단위로 **10억** 을 선택하고 소수 자릿수를 두 자리로 지정하면 보고서에는 1.78이 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5909-130">For example, if the field value is 1,789,905,394 and you select **Billions** and specify 2 decimal places, the value displayed in the report is 1.78.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5909-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5909-131">See Also</span></span>  
 <span data-ttu-id="c5909-132">[텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5909-132">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5909-133">[선, 색 및 이미지 서식 지정&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5909-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5909-134">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5909-134">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5909-135">[축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5909-135">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c5909-136">계기의 눈금 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c5909-136">Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;</span></span>](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)  
  
  
