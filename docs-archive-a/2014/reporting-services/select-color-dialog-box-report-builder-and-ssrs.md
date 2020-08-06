---
title: 색 선택 대화 상자 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a2526b755fd4e08faf79998d351e824371fac2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739142"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="12cf6-102">색 선택 대화 상자(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="12cf6-102">Select Color Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="12cf6-103">**색 선택** 대화 상자를 사용하여 데이터 영역이나 입력란 내의 단일 셀 또는 여러 셀의 배경에 대한 색 옵션을 지정하거나 차트의 색 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-103">Use the **Select Color** dialog box to specify color options for the background of a single cell or multiple cells within a data region or a text box, or for a chart.</span></span>  
  
## <a name="options"></a><span data-ttu-id="12cf6-104">옵션</span><span class="sxs-lookup"><span data-stu-id="12cf6-104">Options</span></span>  
 <span data-ttu-id="12cf6-105">**색 선택기**</span><span class="sxs-lookup"><span data-stu-id="12cf6-105">**Color selector**</span></span>  
 <span data-ttu-id="12cf6-106">세 가지 옵션 중 하나를 선택하여 색을 선택하는 데 사용할 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-106">Choose from three options that specify how you want to select colors:</span></span>  
  
-   <span data-ttu-id="12cf6-107">**선택 - 색 원** HSB(색상/채도/명도) 색 값을 사용하여 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-107">**Picker - Color circle** Choose a color using Hue/Saturation/Brightness (HSB) color values.</span></span>  
  
-   <span data-ttu-id="12cf6-108">**선택 - 색 사각형** RGB(빨강/녹색/파랑) 색 값을 사용하여 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-108">**Picker - Color square** Choose a color using Red/Green/Blue (RGB) color values.</span></span>  
  
-   <span data-ttu-id="12cf6-109">**색상표 - 표준 색** 미리 정의된 색 값의 목록에서 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-109">**Palette - Standard colors** Choose a color from a predefined list of color values.</span></span>  
  
 <span data-ttu-id="12cf6-110">**색 원**</span><span class="sxs-lookup"><span data-stu-id="12cf6-110">**Color circle**</span></span>  
 <span data-ttu-id="12cf6-111">HSB 값은 원통형 좌표계에 매핑되므로 HSB 색에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-111">Use for HSB colors because HSB values are mapped onto a cylindrical coordinate system.</span></span> <span data-ttu-id="12cf6-112">색상은 실제 색이고, 채도는 색의 순수한 정도이고, 명도는 밝음이나 어두움의 상대적인 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-112">Hue is the actual color, saturation is purity of color, brightness is relative brightness or darkness.</span></span>  
  
 <span data-ttu-id="12cf6-113">색을 선택하면 결정된 색이 원의 중앙에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-113">When you pick a color, the center of the circle determines the color.</span></span> <span data-ttu-id="12cf6-114">색상을 변경하려면 색 슬라이더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-114">Use the color slider to change the hue.</span></span> <span data-ttu-id="12cf6-115">x 및 y 좌표는 각각 채도와 명도 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-115">The x and y coordinates represent saturation and brightness values respectively.</span></span>  
  
 <span data-ttu-id="12cf6-116">**색 사각형**</span><span class="sxs-lookup"><span data-stu-id="12cf6-116">**Color square**</span></span>  
 <span data-ttu-id="12cf6-117">RGB 값은 데카르트 좌표계에 매핑되므로 RGB 색에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-117">Use for RGB colors because RGB values are mapped to a Cartesian coordinate system.</span></span> <span data-ttu-id="12cf6-118">R은 빨강의 값, G는 녹색의 값, B는 파랑의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-118">R is the value for Red, G is the value for Green, B is the value for Blue.</span></span>  
  
 <span data-ttu-id="12cf6-119">색을 선택하면 결정된 색이 사각형의 중앙에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-119">When you pick a color, the center of the square determines the color.</span></span> <span data-ttu-id="12cf6-120">선택된 색의 범위를 변경하려면 색 슬라이더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-120">Use the color slider to change the range of the chosen color.</span></span> <span data-ttu-id="12cf6-121">x 및 y 좌표는 다른 두 색을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-121">The x and y coordinates represent the other two colors.</span></span> <span data-ttu-id="12cf6-122">예를 들어 녹색을 선택하면 슬라이더에 녹색 값의 범위가 표시되고 x 및 y 좌표는 각각 빨강 및 파랑 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-122">For example, if you pick green, the slider shows the range of green values, the x and y coordinates represent red and blue values respectively.</span></span>  
  
 <span data-ttu-id="12cf6-123">**표준 색상표 색**</span><span class="sxs-lookup"><span data-stu-id="12cf6-123">**Standard palette color**</span></span>  
 <span data-ttu-id="12cf6-124">열거형에서 명명 된 색에 사용 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` 합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-124">Use for named colors from the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` enumeration.</span></span>  
  
 <span data-ttu-id="12cf6-125">**색 시스템**</span><span class="sxs-lookup"><span data-stu-id="12cf6-125">**Color system**</span></span>  
 <span data-ttu-id="12cf6-126">RGB 또는 HSB 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-126">Specify RGB or HSB colors.</span></span> <span data-ttu-id="12cf6-127">이 선택에 따라 RGB 또는 HSB 값을 표시하도록 디스플레이가 변경됩니다. RGB와 HSB 값은 **색 선택기**에서 색 원 또는 색 사각형을 사용할 때 대화형으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-127">This choice changes the display to show RGB or HSB values, which are updated interactively when you use a color circle or color square for the **Color selector**.</span></span>  
  
 <span data-ttu-id="12cf6-128">**알파** 값은 색에 투명도 값이 포함될 수 있는 경우 일부 속성에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-128">The **Alpha** value displays for some properties when a color can include a transparency value.</span></span> <span data-ttu-id="12cf6-129">예를 들어 차트 계열은 이 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-129">For example, Chart series fill.</span></span> <span data-ttu-id="12cf6-130">투명도를 지원하지 않는 속성에 대해서는 이 값이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-130">For properties that do not support transparency, this value is disabled.</span></span>  
  
 <span data-ttu-id="12cf6-131">**Red**</span><span class="sxs-lookup"><span data-stu-id="12cf6-131">**Red**</span></span>  
 <span data-ttu-id="12cf6-132">RGB 색의 빨강 부분을 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-132">The decimal value for the red part of the RGB color.</span></span> <span data-ttu-id="12cf6-133">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-133">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-134">**Green**</span><span class="sxs-lookup"><span data-stu-id="12cf6-134">**Green**</span></span>  
 <span data-ttu-id="12cf6-135">RGB 색의 녹색 부분을 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-135">The decimal value for the green part of the RGB color.</span></span> <span data-ttu-id="12cf6-136">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-136">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-137">**Blue**</span><span class="sxs-lookup"><span data-stu-id="12cf6-137">**Blue**</span></span>  
 <span data-ttu-id="12cf6-138">RGB 색의 파랑 부분을 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-138">The decimal value for the blue part of the RGB color.</span></span> <span data-ttu-id="12cf6-139">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-139">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-140">**알파**</span><span class="sxs-lookup"><span data-stu-id="12cf6-140">**Alpha**</span></span>  
 <span data-ttu-id="12cf6-141">색의 알파, 즉 투명도 부분을 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-141">The decimal value for the alpha or transparency part of the color.</span></span> <span data-ttu-id="12cf6-142">이 값이 활성화된 경우 슬라이더 스위치를 사용하여 투명도를 원하는 정도로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-142">When this value is enabled, you can use the slider switch to adjust the degree of transparency you want.</span></span>  
  
 <span data-ttu-id="12cf6-143">**Hue**</span><span class="sxs-lookup"><span data-stu-id="12cf6-143">**Hue**</span></span>  
 <span data-ttu-id="12cf6-144">HSB 색의 색상을 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-144">The decimal value for the hue of the HSB color.</span></span> <span data-ttu-id="12cf6-145">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-145">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-146">**채도**</span><span class="sxs-lookup"><span data-stu-id="12cf6-146">**Saturation**</span></span>  
 <span data-ttu-id="12cf6-147">HSB 색의 채도를 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-147">The decimal value for the saturation of the HSB color.</span></span> <span data-ttu-id="12cf6-148">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-148">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-149">**밝기**</span><span class="sxs-lookup"><span data-stu-id="12cf6-149">**Brightness**</span></span>  
 <span data-ttu-id="12cf6-150">HSB 색의 명도를 나타내는 10진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-150">The decimal value for the brightness of the HSB color.</span></span> <span data-ttu-id="12cf6-151">스핀 상자를 사용하여 값을 변경하거나 0에서 255 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-151">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="12cf6-152">**색 보기**</span><span class="sxs-lookup"><span data-stu-id="12cf6-152">**Color sample**</span></span>  
 <span data-ttu-id="12cf6-153">창의 왼쪽 절반에 현재 색을 표시하고 사용자가 새로 선택하는 색을 창의 오른쪽 절반에 대화형으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-153">Shows the current color on the left half of the pane and interactively shows the new color you are choosing on the right half of the pane.</span></span> <span data-ttu-id="12cf6-154">기본 색이 없으면 창의 왼쪽 절반이 흰색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-154">If there is no default color, the left half of the pane is white.</span></span> <span data-ttu-id="12cf6-155">대부분의 RDL 속성에는 기본 색이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12cf6-155">Most RDL properties have no default color.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12cf6-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12cf6-156">See Also</span></span>  
 <span data-ttu-id="12cf6-157">[보고서 항목 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="12cf6-157">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="12cf6-158">텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12cf6-158">Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;</span></span>](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
