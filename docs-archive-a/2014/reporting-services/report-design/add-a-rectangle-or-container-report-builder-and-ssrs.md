---
title: 사각형 또는 컨테이너 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fddda2f02b9f370d9742ae6add5bae444f8f55f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639301"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a><span data-ttu-id="f85f8-102">사각형 또는 컨테이너 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f85f8-102">Add a Rectangle or Container (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f85f8-103">보고서 영역을 구분하거나, 보고서 영역을 강조하거나, 하나 이상의 보고서 항목에 대해 배경을 제공하기 위해 그래픽 요소가 필요한 경우 보고서에 사각형을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-103">Add a rectangle to your report when you want a graphical element to separate areas of the report, emphasize areas of a report, or provide a background for one or more report items.</span></span> <span data-ttu-id="f85f8-104">사각형은 보고서에서 데이터 영역이 렌더링되는 방식을 제어하는 데 도움이 되는 컨테이너로도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-104">Rectangles are also used as containers to help control the way data regions render in a report.</span></span> <span data-ttu-id="f85f8-105">배경색 및 테두리 색과 같은 사각형 속성을 편집하여 사각형의 모양을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-105">You can customize the appearance of a rectangle by editing rectangle properties such as the background and border colors.</span></span> <span data-ttu-id="f85f8-106">사각형을 컨테이너로 사용하는 방법은 [사각형 및 선&#40;보고서 작성기 및 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) 및 [행렬 및 차트에 같은 데이터 표시&#40;보고서 작성기&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f85f8-106">For more information about using a rectangle as a container, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a><span data-ttu-id="f85f8-107">사각형을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f85f8-107">To add a rectangle</span></span>  
  
1.  <span data-ttu-id="f85f8-108">**삽입** 탭의 **보고서 항목** 그룹에서 **사각형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-108">On the **Insert** tab, in the **Report Items** group, click **Rectangle.**</span></span>  
  
2.  <span data-ttu-id="f85f8-109">디자인 화면에서 사각형 왼쪽 위 모퉁이를 배치할 위치를 클릭한 다음 오른쪽 아래 모퉁이로 지정할 위치까지 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-109">On the design surface, click the location where you want the upper left corner of the rectangle, and drag to where you want the lower-right corner.</span></span>  
  
     <span data-ttu-id="f85f8-110">커서를 이동할 때 커서가 디자인 화면의 다른 개체와 일렬이 되면 "맞춤선"이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-110">Note that as you move the cursor, "snap lines" appear as the cursor lines up with other objects on the design surface.</span></span> <span data-ttu-id="f85f8-111">맞춤선을 사용하면 개체를 쉽게 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-111">These help you if you want objects to be aligned.</span></span>  
  
### <a name="to-create-a-container"></a><span data-ttu-id="f85f8-112">컨테이너를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f85f8-112">To create a container</span></span>  
  
1.  <span data-ttu-id="f85f8-113">보고서에 사각형 보고서 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-113">Add a rectangle report item to the report.</span></span>  
  
2.  <span data-ttu-id="f85f8-114">다른 보고서 항목을 사각형으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-114">Drag other report items into the rectangle.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f85f8-115">사각형은 사각형 안에서 만들거나 사각형 안으로 끌어 놓은 항목에 대한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="f85f8-116">디자인 화면에서 기존 항목을 포함하도록 사각형을 그려도 사각형이 기존 항목의 컨테이너로 동작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span>  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a><span data-ttu-id="f85f8-117">색, 스타일 또는 두께와 같은 사각형 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="f85f8-117">To change rectangle properties such as color, style, or weight</span></span>  
  
1.  <span data-ttu-id="f85f8-118">사각형을 선택한 다음 홈 탭의 **테두리** 섹션에서 선 색, 스타일 또는 두께 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-118">Select the rectangle, and then click the line color, style, or weight options in the **Border** section of the Home tab.</span></span>  
  
2.  <span data-ttu-id="f85f8-119">**테두리** 단추 옆의 화살표를 클릭하여 변경할 사각형의 면을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-119">Click the arrow next to the **Border** button to determine which sides of the rectangle to change.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f85f8-120">선 스타일을 **이중선** 으로 설정하고 선 두께를 1 1/2pt 이하로 설정하면 보고서 작성기, 보고서 디자이너 또는 보고서 관리자에서 보고서를 실행할 때 선이 이중선으로 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-120">If you set the line style to **Double** and the line width is 1 1/2 pt or narrower, the line may not appear double when you run the report in Report Builder, Report Designer, or Report Manager.</span></span> <span data-ttu-id="f85f8-121">보고서를 Microsoft Word 및 Acrobat PDF 같은 다른 형식으로 내보내면 이중선이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f85f8-121">It will appear double when you export the report to other formats such as Microsoft Word and Acrobat PDF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85f8-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f85f8-122">See Also</span></span>  
 <span data-ttu-id="f85f8-123">[사각형 및 선&#40;보고서 작성기 및 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f85f8-123">[Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f85f8-124">렌더링 동작&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f85f8-124">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
