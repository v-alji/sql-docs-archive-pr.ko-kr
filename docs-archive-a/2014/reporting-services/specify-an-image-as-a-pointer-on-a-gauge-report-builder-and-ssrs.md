---
title: 이미지를 계기의 포인터로 지정 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c694cdb90fb668c43eb7e9971bba967bad8dd9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734947"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="aa9d0-102">이미지를 계기의 포인터로 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="aa9d0-102">Specify an Image as a Pointer on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="aa9d0-103">계기에는 포인터의 모양을 사용자 지정하는 데 사용할 수 있는 세 가지 기본 제공 스타일이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-103">The gauge contains three built-in styles that can be used to customize the appearance of the pointer.</span></span> <span data-ttu-id="aa9d0-104">방사형 계기의 경우 기본 제공 스타일은 니 들, 표식 및 가로 막대형입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-104">For a radial gauge, the built in styles are: Needle, Marker and Bar.</span></span> <span data-ttu-id="aa9d0-105">선형 계기의 경우 기본 제공 스타일은 표식, 막대 및 온도계입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-105">For a linear gauge, the built-in styles are Marker, Bar, and Thermometer.</span></span> <span data-ttu-id="aa9d0-106">고유한 포인터가 필요한 경우 모든 기능을 갖춘 포인터로 사용할 수 있는 이미지를 만들어 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-106">If a unique pointer is required, the user can create and specify an image which can be used as a fully functional pointer.</span></span>  
  
 <span data-ttu-id="aa9d0-107">포인터의 이미지를 지정할 경우 이미지는 다음 사양을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-107">When you are specifying an image for the pointer, your image must have the following specifications:</span></span>  
  
-   <span data-ttu-id="aa9d0-108">포인터의 원점 또는 회전의 중심은 이미지의 위쪽에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-108">The origin of the pointer, or center of rotation, must be at the top of the image.</span></span>  
  
-   <span data-ttu-id="aa9d0-109">포인터의 끝은 아래쪽을 향하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-109">The end of the pointer must be pointing down.</span></span>  
  
 <span data-ttu-id="aa9d0-110">포인터의 모양은 불규칙적이므로 이미지의 필요하지 않은 부분을 숨기려면 투명 색을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-110">Since the pointer is an irregular shape, you will need to specify a transparency color to hide the unnecessary portions of the image.</span></span> <span data-ttu-id="aa9d0-111">지정된 색은 계기에 나타나지 않으므로 계기에 일반적으로 표시되지 않는 색을 투명 색으로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-111">Consider using a color that would not normally be shown on the gauge as the transparency color, since the colors specified will not appear on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a><span data-ttu-id="aa9d0-112">이미지를 계기의 포인터로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="aa9d0-112">To specify an image as a pointer on the gauge</span></span>  
  
1.  <span data-ttu-id="aa9d0-113">디자인 뷰에서 계기의 포인터를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-113">In Design view, click the pointer of the gauge.</span></span>  
  
2.  <span data-ttu-id="aa9d0-114">필드 계기에 포인터가 없는 경우 계기를 마우스 오른쪽 단추로 클릭 하 고 **포인터 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-114">(Optional) If no pointer exists on the gauge, right-click on the gauge and select **Add Pointer**.</span></span> <span data-ttu-id="aa9d0-115">포인터가 계기에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-115">A pointer is added to the gauge.</span></span>  
  
3.  <span data-ttu-id="aa9d0-116">리본 메뉴에서 **삽입** 탭을 클릭 하 고 이미지 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-116">Click the **Insert** tab on the ribbon and double-click the image icon.</span></span> <span data-ttu-id="aa9d0-117">**이미지 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-117">The **Image Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="aa9d0-118">보고서에 이미지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-118">Add an image to your report.</span></span> <span data-ttu-id="aa9d0-119">자세한 내용은 [보고서에 이미지 포함 &#40;보고서 작성기 및 SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-119">For more information, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="aa9d0-120">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-120">Open the Properties pane.</span></span>  
  
6.  <span data-ttu-id="aa9d0-121">디자인 화면에서 포인터를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-121">On the design surface, click on the pointer.</span></span> <span data-ttu-id="aa9d0-122">포인터의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-122">The properties for the pointer are displayed in the Properties pane.</span></span>  
  
7.  <span data-ttu-id="aa9d0-123">PointerImage 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-123">Expand the PointerImage node.</span></span>  
  
8.  <span data-ttu-id="aa9d0-124">**원본**의 드롭다운 목록에서 **포함** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-124">In **Source**, select **Embedded** from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aa9d0-125">이미지를 데이터베이스 또는 웹에 저장한 경우 이 속성에 적절한 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-125">If your image is stored in the database or on the web, you can specify the appropriate option for this property.</span></span> <span data-ttu-id="aa9d0-126">자세한 내용은 [이미지 속성 대화 상자, 일반 &#40;보고서 작성기 및 SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-126">For more information, see [Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).</span></span>  
  
9. <span data-ttu-id="aa9d0-127">**값**의 드롭다운 목록에서 이미지의 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-127">In **Value**, select the name of your image from the drop-down list.</span></span>  
  
10. <span data-ttu-id="aa9d0-128">**TransparentColor**에서 이미지에서 제거 하려는 색 값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-128">In **TransparentColor**, pick a color value that you want to remove from the image.</span></span> <span data-ttu-id="aa9d0-129">이렇게 하면 계기에 포인터의 모양이 깔끔하게 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aa9d0-129">This will create a seamless appearance for the pointer in the gauge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9d0-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa9d0-130">See Also</span></span>  
 <span data-ttu-id="aa9d0-131">[계기 &#40;보고서 작성기 및 SSRS에 대 한 형식 지정&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa9d0-131">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aa9d0-132">[보고서 &#40;보고서 작성기 및 SSRS에 계기를 추가&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa9d0-132">[Add a Gauge to a Report &#40;Report Builder and SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aa9d0-133">[선, 색 및 이미지 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa9d0-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aa9d0-134">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aa9d0-134">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
