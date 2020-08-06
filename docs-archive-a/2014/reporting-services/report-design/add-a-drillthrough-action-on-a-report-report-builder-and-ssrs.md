---
title: 보고서에 드릴스루 동작 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 153729c4-d01e-4629-b78f-0cfd5a7f83da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a429380f677a309e4e1437a2e3c5036bb4e8a455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648802"
---
# <a name="add-a-drillthrough-action-on-a-report-report-builder-and-ssrs"></a><span data-ttu-id="45e92-102">보고서에 드릴스루 동작 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="45e92-102">Add a Drillthrough Action on a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="45e92-103">주 보고서에서 링크를 클릭할 때 열리는 보고서를 *드릴스루 보고서*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-103">The report that opens when you click the link in the main report is known as a *drillthrough report*.</span></span> <span data-ttu-id="45e92-104">이 드릴스루 링크를 통해 드릴스루 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-104">This drillthrough link enables a drillthrough action.</span></span>  
  
 <span data-ttu-id="45e92-105">드릴스루 보고서는 주 보고서와 같은 보고서 서버에 게시되어야 하지만 폴더는 달라도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-105">Drillthrough reports must be published to the same report server as the main report, but they can be in different folders.</span></span> <span data-ttu-id="45e92-106">입력란, 이미지 또는 차트의 데이터 요소와 같이 **동작** 속성이 있는 모든 항목에 드릴스루 링크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-106">You can add a drillthrough link to any item that has an **Action** property, such as a text box, an image, or data points on a chart.</span></span>  
  
 <span data-ttu-id="45e92-107">드릴스루 링크를 보고서에 추가하려면 먼저 주 보고서가 연결될 드릴스루 보고서를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-107">To add a drillthrough link to a report, you must first create the drillthrough report that the main report will link to.</span></span> <span data-ttu-id="45e92-108">드릴스루 보고서는 일반적으로 원래 요약 보고서에 들어 있는 항목에 대한 세부 정보를 포함하며 대개 주 보고서에서 전달된 매개 변수에 기초하여 드릴스루 보고서를 필터링하는 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-108">A drillthrough report commonly contains details about an item that is contained in the original summary report, and often contains parameters that filter the drillthrough report based on parameters passed to it from the main report.</span></span> <span data-ttu-id="45e92-109">드릴스루 보고서를 만드는 방법에 대한 자세한 내용은 [드릴스루 보고서&#40;보고서 작성기 및 SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e92-109">For more information on creating the drillthrough report, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-drillthrough-action"></a><span data-ttu-id="45e92-110">드릴스루 동작을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="45e92-110">To add a drillthrough action</span></span>  
  
1.  <span data-ttu-id="45e92-111">디자인 뷰에서 링크를 추가하려는 입력란, 이미지 또는 차트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-111">In Design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="45e92-112">항목의 **속성** 대화 상자에서 **동작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-112">In the item's **Properties** dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="45e92-113">**보고서로 이동**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-113">Select **Go to report**.</span></span> <span data-ttu-id="45e92-114">이 옵션에 대한 추가 섹션이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-114">Additional sections appear in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="45e92-115">**보고서 지정**에서 **찾아보기** 를 클릭하여 이동할 보고서를 찾거나 보고서의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-115">In **Specify a report**, click **Browse** to locate the report that you want to jump to, or type the name of the report.</span></span> <span data-ttu-id="45e92-116">또는 식 단추(**fx**)를 클릭하여 보고서 이름에 대한 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-116">Alternatively, click the expression (**fx**) button to create an expression for the report name.</span></span>  
  
     <span data-ttu-id="45e92-117">드릴스루 보고서에 대한 경로 형식은 기본 모드와 SharePoint 통합 모드에서 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-117">The format of the path to the drillthrough report differs for native and SharePoint integrated mode.</span></span> <span data-ttu-id="45e92-118">보고서를 찾을 때는 올바른 형식의 경로가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-118">If you browse to the report, a path of the correct format is provided.</span></span> <span data-ttu-id="45e92-119">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e92-119">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="45e92-120">드릴스루 보고서에 대한 매개 변수를 지정해야 하는 경우 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-120">If you have to specify parameters for the drillthrough report, follow the next step.</span></span>  
  
5.  <span data-ttu-id="45e92-121">**이러한 매개 변수를 사용하여 보고서 실행**에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-121">In **Use these parameters to run the report**, click **Add**.</span></span> <span data-ttu-id="45e92-122">매개 변수 표에 새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-122">A new row is added to the parameter grid.</span></span>  
  
    -   <span data-ttu-id="45e92-123">**이름** 입력란에서 드롭다운 목록을 클릭하거나 드릴스루 보고서에 있는 보고서 매개 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-123">In the **Name** text box, click the drop-down list or type the name of the report parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45e92-124">매개 변수 목록에 있는 이름이 대상 보고서의 예상 매개 변수와 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-124">The names in the parameter list must match the expected parameters in the target report exactly.</span></span> <span data-ttu-id="45e92-125">예를 들어 매개 변수 이름은 대/소문자가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-125">For example, parameter names must match by case.</span></span> <span data-ttu-id="45e92-126">이름이 일치하지 않거나 예상 매개 변수가 목록에 없는 경우 드릴스루 보고서가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-126">If the names do not match, or if an expected parameter is not listed, the drillthrough report fails.</span></span>  
  
    -   <span data-ttu-id="45e92-127">**값**에서 드릴스루 보고서의 매개 변수에 전달할 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-127">In **Value**, type or select the value to pass to the parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45e92-128">보고서 매개 변수에 전달할 값을 반환하는 식을 값에 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-128">Values can contain an expression that evaluates to a value to pass to the report parameter.</span></span> <span data-ttu-id="45e92-129">값 목록의 식에는 현재 보고서에 대한 필드 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-129">The expressions in the value list include the field list for the current report.</span></span>  
  
     <span data-ttu-id="45e92-130">보고서의 매개 변수를 숨기는 방법에 대한 자세한 내용은 [보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e92-130">For information on how to hide parameters in reports, see [Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="45e92-131">(옵션) 입력란의 경우 리본의 **홈** 탭에서 텍스트 색과 효과를 변경하여 텍스트가 링크임을 사용자에게 나타내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-131">(Optional) For text boxes, it is helpful to indicate to the user that the text is a link by changing the color and effect of the text on the **Home** tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="45e92-132">링크를 테스트하려면 보고서를 실행하고 이 링크를 설정한 보고서 항목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e92-132">To test the link, run the report and click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e92-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45e92-133">See Also</span></span>  
 <span data-ttu-id="45e92-134">[동작 속성 대화 상자&#40;보고서 작성기 및 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e92-134">[Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45e92-135">[차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45e92-135">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="45e92-136">계열에 도구 설명 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="45e92-136">Show ToolTips on a Series &#40;Report Builder and SSRS&#41;</span></span>](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
  
