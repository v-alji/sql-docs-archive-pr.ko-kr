---
title: 하위 보고서 및 매개 변수 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3aeede343763ea5fc8fbdfde179208f98fa1a2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639300"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a><span data-ttu-id="e5f31-102">하위 보고서 및 매개 변수 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e5f31-102">Add a Subreport and Parameters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e5f31-103">여러 관련 보고서의 컨테이너인 주 보고서를 만들려는 경우 하위 보고서를 보고서에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-103">Add subreports to a report when you want to create a main report that is a container for multiple related reports.</span></span> <span data-ttu-id="e5f31-104">하위 보고서는 다른 보고서에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-104">A subreport is a reference to another report.</span></span> <span data-ttu-id="e5f31-105">여러 보고서에서 동일한 고객에 대한 데이터를 표시하도록 하는 등의 이유로 데이터 값을 통해 여러 보고서를 연결하려면 매개 변수가 있는 보고서(예: 특정 고객에 대한 세부 정보를 표시하는 보고서)를 하위 보고서로 디자인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-105">To relate the reports through data values (for example, to have multiple reports show data for the same customer), you must design a parameterized report (for example, a report that shows the details for a specific customer) as the subreport.</span></span> <span data-ttu-id="e5f31-106">하위 보고서를 주 보고서에 추가할 때에는 매개 변수를 지정하여 하위 보고서에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-106">When you add a subreport to the main report, you can specify parameters to pass to the subreport.</span></span>  
  
 <span data-ttu-id="e5f31-107">하위 보고서를 테이블이나 행렬의 동적 행 또는 열에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-107">You can also add subreports to dynamic rows or columns in a table or matrix.</span></span> <span data-ttu-id="e5f31-108">주 보고서가 처리되면 하위 보고서가 각 행에 대해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-108">When the main report is processed, the subreport is processed for each row.</span></span> <span data-ttu-id="e5f31-109">이 경우 데이터 영역 또는 중첩된 데이터 영역을 사용하여 원하는 결과를 얻을 수 있는지 생각해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="e5f31-109">In this case, consider whether you can achieve the desired effect by using data regions or nested data regions.</span></span>  
  
 <span data-ttu-id="e5f31-110">보고서에 하위 보고서를 추가하려면 먼저 포함될 보고서 역할을 할 보고서를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-110">To add a subreport to a report, you must first create the report that will act as the subreport.</span></span> <span data-ttu-id="e5f31-111">하위 보고서를 만드는 방법은 [하위 보고서&#40;보고서 작성기 및 SSRS&#41;](subreports-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5f31-111">For more information on creating the subreport, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a><span data-ttu-id="e5f31-112">하위 보고서를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e5f31-112">To add a subreport</span></span>  
  
1.  <span data-ttu-id="e5f31-113">**삽입** 탭에서 **하위 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-113">On the **Insert** tab, click **Subreport**.</span></span>  
  
2.  <span data-ttu-id="e5f31-114">디자인 화면에서 보고서의 한 위치를 클릭한 다음 상자를 끌어 원하는 하위 보고서 크기로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-114">On the design surface, click a location on the report and then drag a box to the desired size of the subreport.</span></span> <span data-ttu-id="e5f31-115">또는 디자인 화면을 클릭하여 기본 크기의 하위 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-115">Alternatively, click the design surface to create a subreport of default size.</span></span>  
  
3.  <span data-ttu-id="e5f31-116">하위 보고서를 마우스 오른쪽 단추로 클릭한 다음 **하위 보고서 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-116">Right-click the subreport, and then click **Subreport Properties**.</span></span>  
  
4.  <span data-ttu-id="e5f31-117">**하위 보고서 속성** 대화 상자의 **이름** 입력란에 이름을 입력하거나 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-117">In the **Subreport Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span> <span data-ttu-id="e5f31-118">이름은 보고서 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-118">The name must be unique within the report.</span></span> <span data-ttu-id="e5f31-119">기본적으로 Subreport1 또는 Subreport2 등과 같은 일반 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-119">By default, a general name such as Subreport1 or Subreport2 is assigned.</span></span>  
  
5.  <span data-ttu-id="e5f31-120">**이 보고서를 하위 보고서로 사용** 상자에서 **찾아보기**를 클릭하거나 보고서의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-120">In the **Use this report as a subreport** box, click **Browse**, or type the name of the report.</span></span> <span data-ttu-id="e5f31-121">하위 보고서의 경로는 자동으로 지정되므로 **찾아보기** 를 클릭하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-121">Clicking **Browse** is preferred because the path to the subreport will be specified automatically.</span></span> <span data-ttu-id="e5f31-122">여러 가지 방법으로 보고서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-122">You can specify the report in the several ways.</span></span> <span data-ttu-id="e5f31-123">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5f31-123">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="e5f31-124">(옵션) 하위 보고서가 여러 페이지에 걸쳐 있는 경우 테두리가 렌더링되지 않도록 **페이지 나누기에 테두리 생략** 에서 **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-124">(Optional) Click **Yes** for **Omit border on page break** to prevent a border from being rendered in the middle of the subreport if the subreport spans more than one page.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a><span data-ttu-id="e5f31-125">하위 보고서에 전달할 매개 변수를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e5f31-125">To specify parameters to pass to a subreport</span></span>  
  
1.  <span data-ttu-id="e5f31-126">디자인 뷰에서 하위 보고서를 마우스 오른쪽 단추로 클릭한 다음 **하위 보고서 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-126">In Design view, right-click the subreport and then click **Subreport Properties**.</span></span>  
  
2.  <span data-ttu-id="e5f31-127">**하위 보고서 속성** 대화 상자에서 **매개 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-127">In the **Subreport Properties** dialog box, click **Parameters**.</span></span>  
  
3.  <span data-ttu-id="e5f31-128">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-128">Click **Add**.</span></span> <span data-ttu-id="e5f31-129">매개 변수 표에 새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-129">A new row is added to the parameter grid.</span></span>  
  
4.  <span data-ttu-id="e5f31-130">**이름** 입력란에 하위 보고서의 매개 변수 이름을 입력하거나 목록 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-130">In the **Name** text box, type the name of a parameter in the subreport or choose it from the list box.</span></span> <span data-ttu-id="e5f31-131">이 이름은 쿼리 매개 변수가 아닌 하위 보고서에 있는 보고서 매개 변수의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-131">This name must match a report parameter, not a query parameter, in the subreport.</span></span>  
  
5.  <span data-ttu-id="e5f31-132">**값** 목록 상자에서 하위 보고서에 전달할 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-132">In the **Value** list box, type or select a value to pass to the subreport.</span></span> <span data-ttu-id="e5f31-133">이 값은 정적 텍스트이거나 주 보고서의 필드 또는 기타 개체를 참조하는 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-133">This value can be static text or an expression that references a field or other object in the main report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5f31-134">보고서 작성기에서는 매개 변수가 **매개 변수** 목록에 없고 하위 보고서에 기본값이 정의되어 있으면 하위 보고서가 올바르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-134">In Report Builder, if a parameter is missing from the **Parameters** list and the subreport has a default value defined, the subreport will be processed correctly.</span></span>  
    >   
    >  <span data-ttu-id="e5f31-135">보고서 디자이너에서는 하위 보고서에 필요한 모든 매개 변수를 **매개 변수** 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-135">In Report Designer, all parameters that are required by the subreport must be included in the **Parameters** list.</span></span> <span data-ttu-id="e5f31-136">필요한 매개 변수가 없으면 하위 보고서가 주 보고서에 올바르게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-136">If a required parameter is missing, the subreport is not displayed correctly in the main report.</span></span>  
  
6.  <span data-ttu-id="e5f31-137">각 하위 보고서 매개 변수의 이름과 값을 지정하려면 3-5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-137">Repeat steps 3-5 to specify a name and value for each subreport parameter.</span></span>  
  
7.  <span data-ttu-id="e5f31-138">하위 보고서 매개 변수를 삭제하려면 매개 변수 표에서 매개 변수를 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-138">To delete a subreport parameter, click the parameter in the parameter grid, and then click **Delete**.</span></span>  
  
8.  <span data-ttu-id="e5f31-139">하위 보고서 매개 변수의 순서를 변경하려면 매개 변수를 클릭한 다음 위로 단추 또는 아래로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-139">To change the order of a subreport parameter, click the parameter, and then click the up button or the down button.</span></span>  
  
     <span data-ttu-id="e5f31-140">하위 보고서 매개 변수의 순서 변경은 하위 보고서의 처리에 아무런 영향도 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f31-140">Changing the order of a subreport parameter does not affect the processing of the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f31-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5f31-141">See Also</span></span>  
 <span data-ttu-id="e5f31-142">[하위 보고서&#40;보고서 작성기 및 SSRS&#41;](subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f31-142">[Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e5f31-143">렌더링 동작&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e5f31-143">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
