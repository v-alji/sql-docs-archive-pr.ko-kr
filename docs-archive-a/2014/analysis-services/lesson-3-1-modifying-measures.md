---
title: 측정값 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd352cbca1d21f5842e075d9cb8e5e766aa369b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653632"
---
# <a name="modifying-measures"></a><span data-ttu-id="237b5-102">측정값 수정</span><span class="sxs-lookup"><span data-stu-id="237b5-102">Modifying Measures</span></span>
  <span data-ttu-id="237b5-103">**FormatString** 속성을 사용하여 측정값이 사용자에게 표시되는 방식을 제어하는 서식 설정을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-103">You can use the **FormatString** property to define formatting settings that control how measures are displayed to users.</span></span> <span data-ttu-id="237b5-104">이 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 통화 및 백분율 측정값에 대한 서식 속성을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-104">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
### <a name="to-modify-the-measures-of-the-cube"></a><span data-ttu-id="237b5-105">큐브의 측정값을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="237b5-105">To modify the measures of the cube</span></span>  
  
1.  <span data-ttu-id="237b5-106">**Tutorial 큐브에 대한 큐브 디자이너의** 큐브 구조 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭으로 전환하고 **측정값** 창에서 **Internet Sales** 측정값 그룹을 확장한 다음 **Order Quantity**를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-106">Switch to the **Cube Structure** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, expand the **Internet Sales** measure group in the **Measures** pane, right-click **Order Quantity**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="237b5-107">속성 창에서 **자동 숨기기** 압정 아이콘을 클릭하여 속성 창을 열려 있게 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-107">In the Properties window, click the **Auto Hide** pushpin icon to pin the Properties window open.</span></span>  
  
     <span data-ttu-id="237b5-108">속성 창이 열려 있으면 큐브에 있는 여러 항목의 속성을 보다 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-108">It is easier to change properties for several items in the cube when the Properties window remains open.</span></span>  
  
3.  <span data-ttu-id="237b5-109">속성 창에서 **FormatString** 목록을 클릭하고 **#,#** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-109">In the Properties window, click the **FormatString** list, and then type **#,#**.</span></span>  
  
4.  <span data-ttu-id="237b5-110">**큐브 구조** 탭 도구 모음에서 왼쪽의 **측정값 표 표시** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-110">On the toolbar of the **Cube Structure** tab, click the **Show Measures Grid** icon on the left.</span></span>  
  
     <span data-ttu-id="237b5-111">표 뷰를 사용하면 동시에 여러 측정값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-111">The grid view lets you select multiple measures at the same time.</span></span>  
  
5.  <span data-ttu-id="237b5-112">다음 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-112">Select the following measures.</span></span> <span data-ttu-id="237b5-113">CTRL 키를 누른 채 각 측정값을 클릭하면 여러 측정값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-113">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="237b5-114">**Unit Price**</span><span class="sxs-lookup"><span data-stu-id="237b5-114">**Unit Price**</span></span>  
  
    -   <span data-ttu-id="237b5-115">**Extended Amount**</span><span class="sxs-lookup"><span data-stu-id="237b5-115">**Extended Amount**</span></span>  
  
    -   <span data-ttu-id="237b5-116">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="237b5-116">**Discount Amount**</span></span>  
  
    -   <span data-ttu-id="237b5-117">**Product Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="237b5-117">**Product Standard Cost**</span></span>  
  
    -   <span data-ttu-id="237b5-118">**Total Product Cost**</span><span class="sxs-lookup"><span data-stu-id="237b5-118">**Total Product Cost**</span></span>  
  
    -   <span data-ttu-id="237b5-119">**Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="237b5-119">**Sales Amount**</span></span>  
  
    -   <span data-ttu-id="237b5-120">**Tax Amt**</span><span class="sxs-lookup"><span data-stu-id="237b5-120">**Tax Amt**</span></span>  
  
    -   <span data-ttu-id="237b5-121">**Freight**</span><span class="sxs-lookup"><span data-stu-id="237b5-121">**Freight**</span></span>  
  
6.  <span data-ttu-id="237b5-122">속성 창의 **FormatString** 목록에서 **Currency**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-122">In the Properties window, in the **FormatString** list, select **Currency**.</span></span>  
  
7.  <span data-ttu-id="237b5-123">제목 표시줄 바로 아래의 속성 창 맨 위에 있는 드롭다운 목록에서 **Unit Price Discount Pct**측정값을 선택한 다음 **FormatString** 목록에서 **Percent** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-123">In the drop-down list at the top of the Properties window (right below the title bar), select the measure **Unit Price Discount Pct**, and then select **Percent** in the **FormatString** list.</span></span>  
  
8.  <span data-ttu-id="237b5-124">속성 창에서 **Unit Price 할인 Pct** 측정값의 **Name** 속성을로 변경 `Unit Price Discount Percentage` 합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-124">In the Properties window, change the **Name** property for the **Unit Price Discount Pct** measure to `Unit Price Discount Percentage`.</span></span>  
  
9. <span data-ttu-id="237b5-125">**측정값** 창에서 **세금 Amt** 를 클릭 하 고이 측정값의 이름을로 변경 `Tax Amount` 합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-125">In the **Measures** pane, click **Tax Amt** and change the name of this measure to `Tax Amount`.</span></span>  
  
10. <span data-ttu-id="237b5-126">속성 창에서 **자동 숨기기** 아이콘을 클릭하여 속성 창을 숨긴 다음 **큐브 구조** 탭의 도구 모음에서 **측정값 트리 표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-126">In the Properties window, click the **Auto Hide** icon to hide the Properties window, and then click **Show Measures Tree** on the toolbar of the **Cube Structure** tab.</span></span>  
  
11. <span data-ttu-id="237b5-127">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="237b5-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="237b5-128">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="237b5-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="237b5-129">Customer 차원 수정</span><span class="sxs-lookup"><span data-stu-id="237b5-129">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="237b5-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="237b5-130">See Also</span></span>  
 <span data-ttu-id="237b5-131">[데이터베이스 차원 정의](multidimensional-models/define-database-dimensions.md) </span><span class="sxs-lookup"><span data-stu-id="237b5-131">[Define Database Dimensions](multidimensional-models/define-database-dimensions.md) </span></span>  
 [<span data-ttu-id="237b5-132">측정값 속성 구성</span><span class="sxs-lookup"><span data-stu-id="237b5-132">Configure Measure Properties</span></span>](multidimensional-models/configure-measure-properties.md)  
  
  
