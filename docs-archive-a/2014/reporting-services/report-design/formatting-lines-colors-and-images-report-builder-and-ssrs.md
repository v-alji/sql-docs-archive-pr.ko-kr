---
title: 선, 색 및 이미지 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.textboxproperties.border.f1
- "10502"
- "10094"
- sql12.rtp.rptdesigner.pictureproperties.border.f1
- "10063"
- sql12.rtp.rptdesigner.rectangleproperties.border.f1
- "10055"
- sql12.rtp.rptdesigner.subreportproperties.border.f1
- "10126"
- sql12.rtp.rptdesigner.shared.borderdv.f1
- "10066"
- sql12.rtp.rptdesigner.reportbody.border.f1
ms.assetid: 0f5f0d2a-9537-4152-b441-b40d7f04cf4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 681ff6b46f692804aef5c7cbbc16e5abe99dbb2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728019"
---
# <a name="formatting-lines-colors-and-images-report-builder-and-ssrs"></a><span data-ttu-id="e79c4-102">선, 색 및 이미지 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e79c4-102">Formatting Lines, Colors, and Images (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e79c4-103">를 사용하면 선, 색, 데이터 영역, 이미지 및 다른 보고서 항목의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-103">gives you the ability to format lines, colors, data regions, images, and other report items.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="borders-lines-and-gridlines"></a><span data-ttu-id="e79c4-104">테두리, 선 및 눈금선</span><span class="sxs-lookup"><span data-stu-id="e79c4-104">Borders, Lines and Gridlines</span></span>  
 <span data-ttu-id="e79c4-105">테두리, 선 및 눈금선은 페이지에서 항목을 시각적으로 함께 연결하고 보고서를 읽는 사용자가 보고서의 내용을 보다 쉽게 읽을 수 있도록 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-105">Borders, lines, and gridlines can visually tie items together on the page and help your report readers easily read the contents of the report.</span></span> <span data-ttu-id="e79c4-106">미리 정의된 테두리 스타일을 사용하여 입력란 주위의 테두리, 입력란 그룹 또는 이미지를 빠르게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-106">Using the predefined border styles, you can quickly add a border around a text box, a group of text boxes, or an image.</span></span> <span data-ttu-id="e79c4-107">또한 테두리, 선 및 눈금선의 스타일, 두께 및 색을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-107">In addition, you can change the style, width, and color for the borders, lines, and gridlines.</span></span> <span data-ttu-id="e79c4-108">선택한 전체 항목 주위 또는 항목 가장자리를 따라 테두리 주위(예: 입력란 아래쪽 테두리)에 테두리가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-108">Borders are added around the entire item selected or around a border along an edge of the item, for example, a border along the bottom of a text box.</span></span>  
  
 <span data-ttu-id="e79c4-109">입력란, 보고서 레이아웃 또는 이미지 주위에서 테두리 및 눈금선의 서식을 지정하려면 보고서 항목의 **속성** 대화 상자에 있는 **테두리** 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-109">To format borders and gridlines in a text box, report layout, or around an image, use the **Border** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="e79c4-110">예를 들어 이미지 주위에 테두리를 추가하려는 경우 이미지를 마우스 오른쪽 단추로 클릭한 다음 **이미지 속성** 대화 상자에서 **테두리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-110">For example, if you want to add a border around an image, right-click the image and then in the **Image Properties** dialog box, click **Border**.</span></span>  
  
 <span data-ttu-id="e79c4-111">차트에 표준 테두리 프레임 이외에도 추가 테두리 프레임을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-111">In addition to the standard border frames, additional border frames can be applied to charts.</span></span> <span data-ttu-id="e79c4-112">자세한 내용은 [차트에 테두리 프레임 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e79c4-112">For more information, see [Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e79c4-113">보고서 자체에 테두리를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-113">You can also add a border to the report itself.</span></span> <span data-ttu-id="e79c4-114">자세한 내용은 [보고서에 테두리 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-114">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="applying-background-colors"></a><span data-ttu-id="e79c4-115">배경색 적용</span><span class="sxs-lookup"><span data-stu-id="e79c4-115">Applying Background Colors</span></span>  
 <span data-ttu-id="e79c4-116">전체 보고서의 배경, 보고서 내의 입력란 또는 데이터 영역 내의 셀 또는 셀 그룹에 단색을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-116">A solid color can be added to the background of the entire report, a text box within the report, or to a cell or group of cells within a data region.</span></span> <span data-ttu-id="e79c4-117">기본적으로 배경색은 흰색이지만 보고서 항목의 **속성** 대화 상자에 있는 **채우기** 탭에서 색을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-117">By default, the background color is white; however, you can select a color from the **Fill** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="e79c4-118">예를 들어 입력란의 배경색을 변경할 경우 입력란을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-118">For example, if you want to change the background color of a text box, right-click the text box and select **Text Box Properties**.</span></span> <span data-ttu-id="e79c4-119">**채우기** 를 클릭한 다음 원하는 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-119">Click **Fill** and then select the color you want.</span></span> <span data-ttu-id="e79c4-120">이 대화 상자에서 선택한 항목의 배경색을 선택하거나 배경에 나타나는 이미지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-120">In this dialog box, you can select a background color for the selected item or you can add an image that appears in the background.</span></span>  
  
 <span data-ttu-id="e79c4-121">차트를 사용하는 경우 배경색에 대한 그라데이션 및 패턴 스타일을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-121">When you use the chart, you can also specify gradients and pattern styles for background colors.</span></span> <span data-ttu-id="e79c4-122">자세한 내용은 [차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e79c4-122">For more information, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-images-as-formatting"></a><span data-ttu-id="e79c4-123">이미지를 서식으로 사용</span><span class="sxs-lookup"><span data-stu-id="e79c4-123">Using Images as Formatting</span></span>  
 <span data-ttu-id="e79c4-124">이미지가 포함된 필드를 데이터 영역에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-124">Fields that contain images can be added to a data region.</span></span> <span data-ttu-id="e79c4-125">이미지 필드를 사용하는 경우 보고서를 실행하면 이미지가 보고서에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-125">If you use an image field, the images appear in the report with the report is run.</span></span>  
  
 <span data-ttu-id="e79c4-126">보고서의 배경이나 사각형, 입력란, 테이블, 행렬, 차트의 일부분 또는 보고서의 본문 및 페이지 구역에 로고와 같은 이미지를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79c4-126">You can also add images such as logos to the background of your report or to a rectangle, text box, table, matrix, or some parts of a chart, or to the body and page sections of a report.</span></span> <span data-ttu-id="e79c4-127">자세한 내용은 [이미지&#40;보고서 작성기 및 SSRS&#41;](images-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e79c4-127">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79c4-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e79c4-128">See Also</span></span>  
 <span data-ttu-id="e79c4-129">[텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e79c4-129">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e79c4-130">[숫자 및 날짜 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e79c4-130">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e79c4-131">[입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e79c4-131">[Format Text in a Text Box &#40;Report Builder and SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e79c4-132">채우기 대화 상자&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e79c4-132">Fill Dialog Box &#40;Report Builder and SSRS&#41;</span></span>](../fill-dialog-box-report-builder-and-ssrs.md)  
  
  
