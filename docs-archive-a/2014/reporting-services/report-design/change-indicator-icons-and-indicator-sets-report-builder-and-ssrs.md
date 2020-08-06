---
title: 표시기 아이콘 및 표시기 집합 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 398d21319ab6da22f2b10c3607baf8f110d6e65b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737947"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a><span data-ttu-id="32c33-102">표시기 아이콘 및 표시기 집합 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="32c33-102">Change Indicator Icons and Indicator Sets (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="32c33-103">는 미리 구성 된 표시기 집합을 제공 하며,이는 항상 데이터를 효과적으로 표시 하 고 배달 된 보고서에서 잘 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-103">provides preconfigured indicators sets, which might not always depict your data effectively and work well in the delivered report.</span></span> <span data-ttu-id="32c33-104">이 항목에서는 표시기 아이콘 모양을 변경하고 더 많거나 더 적은 표시기 아이콘 또는 다른 표시기 아이콘을 포함하도록 표시기 집합을 변경하는 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-104">This topic provides procedures to change the appearance of indicator icons and change the indicator sets to include different, more, or fewer indicator icons.</span></span>  
  
 <span data-ttu-id="32c33-105">식을 사용하여 색 등의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-105">Options such as colors can be set by using expressions.</span></span> <span data-ttu-id="32c33-106">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32c33-106">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-color-of-an-indicator-icon"></a><span data-ttu-id="32c33-107">표시기 아이콘의 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="32c33-107">To change the color of an indicator icon</span></span>  
  
1.  <span data-ttu-id="32c33-108">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-108">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32c33-109">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-109">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32c33-110">변경할 아이콘 옆의 **색** 열에 있는 아래쪽 화살표를 클릭하고 사용할 색, **색 없음**또는 **다른 색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-110">Click the down arrow in the **Color** column next to the icon that you want to change and click the color to use, **No Color**, or **More colors**.</span></span>  
  
     <span data-ttu-id="32c33-111">필요한 경우 **식** 단추(*fx*)를 클릭하여 **색** 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-111">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Color** option.</span></span>  
  
     <span data-ttu-id="32c33-112">**다른 색**을 클릭한 경우 **색 선택** 대화 상자가 열리고 여기서 여러 색 중 원하는 색을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-112">If you clicked **More Colors**, the **Select Color** dialog box opens, where you can choose from a wide array of colors.</span></span> <span data-ttu-id="32c33-113">해당 옵션에 대한 자세한 내용은 [색 선택 대화 상자&#40;보고서 작성기 및 SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32c33-113">For more information about its options, see [Select Color Dialog Box &#40;Report Builder and SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="32c33-114">**확인** 을 클릭하여 **색 선택** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-114">Click **OK** to close the **Select Color** dialog box.</span></span>  
  
4.  <span data-ttu-id="32c33-115">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-115">Click **OK**.</span></span>  
  
### <a name="to-change-the-icon"></a><span data-ttu-id="32c33-116">아이콘을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="32c33-116">To change the icon</span></span>  
  
1.  <span data-ttu-id="32c33-117">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-117">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32c33-118">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-118">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32c33-119">변경할 아이콘 옆의 아래쪽 화살표를 클릭하고 다른 아이콘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-119">Click the down arrow next to the icon that you want to change and select a different icon.</span></span>  
  
     <span data-ttu-id="32c33-120">필요한 경우 **식** 단추(*fx*)를 클릭하여 **아이콘** 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Icon** option.</span></span>  
  
4.  <span data-ttu-id="32c33-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-121">Click **OK**.</span></span>  
  
### <a name="to-use-a-custom-image-as-an-indicator-icon"></a><span data-ttu-id="32c33-122">사용자 지정 이미지를 표시기 아이콘으로 사용하려면</span><span class="sxs-lookup"><span data-stu-id="32c33-122">To use a custom image as an indicator icon</span></span>  
  
1.  <span data-ttu-id="32c33-123">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32c33-124">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32c33-125">변경할 아이콘 옆의 아래쪽 화살표를 클릭하고 **이미지**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-125">Click the down arrow next to the icon that you wan to change and select **Image**.</span></span>  
  
4.  <span data-ttu-id="32c33-126">**이미지 원본 선택** 목록에서 **외부**, **포함**또는 **데이터베이스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-126">In the **Select the image source** list, click **External**, **Embedded**, or **Database**.</span></span>  
  
5.  <span data-ttu-id="32c33-127">이미지 원본에 따라 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-127">Depending on the source of the image, do the one of the following:</span></span>  
  
    -   <span data-ttu-id="32c33-128">보고서 외부에 저장된 이미지를 사용하려면 **찾아보기** 를 클릭하고 이미지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-128">To use an image that is stored externally to the report, click **Browse** and locate the image.</span></span> <span data-ttu-id="32c33-129">보고서에는 이미지에 대한 참조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-129">The report will include a reference to the image.</span></span>  
  
    -   <span data-ttu-id="32c33-130">보고서에 포함된 이미지를 사용하려면 **가져오기** 를 클릭하고 이미지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-130">To use an image that is embedded in the report, click **Import** and locate the image.</span></span> <span data-ttu-id="32c33-131">이미지가 보고서 정의에 추가되며 정의와 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-131">The image will be added to the report definition and saved with it.</span></span>  
  
    -   <span data-ttu-id="32c33-132">데이터베이스에 있는 이미지를 사용하려면 **이 필드 사용** 목록에서</span><span class="sxs-lookup"><span data-stu-id="32c33-132">To use an image that is in a database, in the **Use this field** list.</span></span> <span data-ttu-id="32c33-133">필드를 선택하고 **이 MIME 형식 사용** 목록에서 이미지의 MIME 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-133">select the field from the list and then in the **Use this MIME type** list, select the MIME type of the image.</span></span>  
  
6.  <span data-ttu-id="32c33-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-134">Click **OK**.</span></span>  
  
### <a name="to-add-an-icon-to-the-indicator-set"></a><span data-ttu-id="32c33-135">표시기 집합에 아이콘을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="32c33-135">To add an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="32c33-136">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-136">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32c33-137">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-137">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32c33-138">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-138">Click **Add**.</span></span> <span data-ttu-id="32c33-139">기본 아이콘과 **색 없음** 옵션을 사용하여 표시기가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-139">An indicator is added, using the default icon and the **No Color** option.</span></span>  
  
     <span data-ttu-id="32c33-140">원하는 아이콘과 색을 사용하도록 표시기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-140">Configure the indictor to use the icon and color you want.</span></span> <span data-ttu-id="32c33-141">이 작업을 수행하는 단계는 이 항목 앞부분의 절차에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-141">Procedures earlier in this topic describe the steps to do this.</span></span>  
  
4.  <span data-ttu-id="32c33-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-142">Click **OK**.</span></span>  
  
### <a name="to-delete-an-icon-to-the-indicator-set"></a><span data-ttu-id="32c33-143">표시기 집합에서 아이콘을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="32c33-143">To delete an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="32c33-144">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-144">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32c33-145">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-145">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32c33-146">삭제할 아이콘을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-146">Select the icon to delete, and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="32c33-147">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c33-147">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c33-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32c33-148">See Also</span></span>  
 [<span data-ttu-id="32c33-149">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32c33-149">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
