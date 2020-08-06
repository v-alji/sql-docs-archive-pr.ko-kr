---
title: 게시 된 보고서에 대 한 매개 변수 설정 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d0a2b1a23f382adb9e0cdddbebcded0050d34bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639293"
---
# <a name="set-parameters-on-a-published-report-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="52644-102">게시된 보고서에 매개 변수 설정(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="52644-102">Set Parameters on a Published Report (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="52644-103">매개 변수가 있는 보고서는 보고서 실행 시 데이터를 필터링하는 데 사용되는 입력 값을 받아들이는 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="52644-103">A parameterized report is a report that accepts input values that are used to filter data when you run the report.</span></span> <span data-ttu-id="52644-104">매개 변수는 보고서를 만들 때 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="52644-104">Parameters are defined when the report is created.</span></span> <span data-ttu-id="52644-105">보고서 매개 변수는 보고서 정의에 정의된 방식에 따라 단일 값, 다중 값 또는 동적 값을 받아들일 수 있습니다. 여기서 동적 값은 이전 선택 사항에 따라 변경되는 값입니다. 예를 들어 제품 범주를 선택하면 다음 선택 사항은 해당 범주에 속한 특정 제품이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-105">Depending on how a report parameter is defined in the report definition, it can accept a single value, multiple values, or dynamic values, which change in response to a previous selection (for example, when you select product category, your next selection might be a specific product from that category).</span></span> <span data-ttu-id="52644-106">매개 변수에는 기본값을 지정할 수 있으며 이 값을 사용하여 자동으로 보고서의 필터링된 버전을 실행하거나 해당 값을 다른 값으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-106">A parameter can have a default value, which can be used to run a filtered version of the report automatically or possibly be replaced with a different value.</span></span>  
  
 <span data-ttu-id="52644-107">이러한 속성은 보고서 정의에 설정하거나 보고서가 게시된 후 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-107">These properties can be set in the report definition, or after the report is published.</span></span> <span data-ttu-id="52644-108">게시된 보고서에서 일부 매개 변수 속성을 수정하여 값과 표시 속성을 변경할 수 있지만 매개 변수 이름이나 데이터 형식은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-108">Although you can modify some parameter properties in a published to change the value and display properties, you cannot change a parameter name or the data type.</span></span> <span data-ttu-id="52644-109">매개 변수 이름과 데이터 형식은 보고서 작성자가 보고서 정의에서만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-109">The parameter name and data type can only be changed by the report author in the report definition.</span></span>  
  
 <span data-ttu-id="52644-110">매개 변수가 있는 보고서를 실행하려면 선택할 유효한 값 드롭다운 목록이 보고서에 포함되어 있는 경우에도 입력할 값을 알고 있어야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-110">To run a parameterized report, you typically must know which values to type, although a report might include drop-down lists of valid values from which to choose.</span></span>  
  
 <span data-ttu-id="52644-111">게시된 보고서에 매개 변수 속성을 설정하려면 해당 보고서에 대한 항목 편집 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-111">To set parameter properties on a published report, you must have Edit Items permission for the report.</span></span> <span data-ttu-id="52644-112">SharePoint 사이트에서 실행하는 보고서의 매개 변수 속성을 일부 또는 모두 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-112">You can modify some or all of the parameter properties on a report that you run from a SharePoint site.</span></span> <span data-ttu-id="52644-113">반복해서 사용하려는 매개 변수 값 조합을 저장하여 보고서를 개인 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-113">You cannot personalize a report by saving a combination of parameter values that you want to use repeatedly.</span></span> <span data-ttu-id="52644-114">지정한 기본값은 보고서를 여는 모든 사용자에 의해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52644-114">Any default values that you specify are used by all users who open the report.</span></span>  
  
 <span data-ttu-id="52644-115">보고서를 항상 표시하도록 구성된 보고서 뷰어 웹 파트에 보고서가 포함되어 있는 경우에는 보고서 뷰어 웹 파트에서 속성을 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="52644-115">If the report is embedded in a Report Viewer Web part that is configured to always show that report, set the properties on the Report Viewer Web Part.</span></span> <span data-ttu-id="52644-116">자세한 내용은 [웹 페이지에 보고서 뷰어 웹 파트 추가&#40;SharePoint 통합 모드의 Reporting Services&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52644-116">For more information, see [Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="to-run-a-parameterized-report"></a><span data-ttu-id="52644-117">매개 변수가 있는 보고서를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="52644-117">To run a parameterized report</span></span>  
  
1.  <span data-ttu-id="52644-118">보고서가 포함된 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52644-118">Open the library that contains the report.</span></span>  
  
2.  <span data-ttu-id="52644-119">보고서 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-119">Click the report name.</span></span> <span data-ttu-id="52644-120">매개 변수가 있는 보고서를 미리 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-120">You must know in advance which reports have parameters.</span></span> <span data-ttu-id="52644-121">보고서에 매개 변수가 있다는 사실이 시각적으로 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-121">There is no visual identifier on the report to indicate that it is parameterized.</span></span>  
  
3.  <span data-ttu-id="52644-122">보고서가 열리면 사용할 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-122">When the report opens, specify the parameters you want to use.</span></span> <span data-ttu-id="52644-123">매개 변수 영역은 보고서 뷰어 웹 파트에 속성이 설정된 방식에 따라 표시 또는 축소되거나 숨겨질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-123">The Parameters area might be visible, collapsed, or hidden depending on how properties are set on the Report Viewer Web Part.</span></span>  
  
    1.  <span data-ttu-id="52644-124">매개 변수 영역이 표시되어 있으면 각 매개 변수의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-124">If the Parameters area is visible, choose a value for each parameter.</span></span>  
  
    2.  <span data-ttu-id="52644-125">보고서의 위에서 아래까지 이어지고 가운데에 화살표가 있는 가는 색 줄이 있으면 매개 변수 영역이 축소된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52644-125">If there is a thin strip of color that runs down the length of the report that has an arrow in the middle of it, the Parameters area is collapsed.</span></span> <span data-ttu-id="52644-126">화살표를 클릭하여 해당 영역을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-126">You can click the arrow to expand it.</span></span>  
  
    3.  <span data-ttu-id="52644-127">매개 변수 영역이 숨겨져 있으면 값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-127">If the Parameters area is hidden, you cannot specify a value.</span></span>  
  
4.  <span data-ttu-id="52644-128">매개 변수 영역의 아래쪽에서 **적용** 을 클릭하여 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-128">Click **Apply** at the bottom of the Parameters area to run the report.</span></span>  
  
     <span data-ttu-id="52644-129">지정한 값 조합이 원하는 결과를 제공하지 않을 수 있으며</span><span class="sxs-lookup"><span data-stu-id="52644-129">It is possible to specify a combination of values that do not give you the results you expect.</span></span> <span data-ttu-id="52644-130">이렇게 필요한 정보를 얻을 수 없는 경우 보고서 작성자가 보고서를 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-130">The report might need to be modified by the report author if you are not getting the information you require.</span></span>  
  
5.  <span data-ttu-id="52644-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-131">Click **OK**.</span></span>  
  
### <a name="to-set-parameter-properties"></a><span data-ttu-id="52644-132">매개 변수 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="52644-132">To set parameter properties</span></span>  
  
1.  <span data-ttu-id="52644-133">보고서가 포함된 라이브러리나 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52644-133">Open the library or folder that contains the report.</span></span>  
  
2.  <span data-ttu-id="52644-134">보고서를 가리키고 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-134">Point to the report and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="52644-135">**매개 변수 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-135">Click **Manage Parameters**.</span></span> <span data-ttu-id="52644-136">보고서에 매개 변수가 포함되어 있으면 각 매개 변수가 페이지에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="52644-136">If the report contains parameters, each parameter will be listed on the page.</span></span> <span data-ttu-id="52644-137">이 목록에는 매개 변수 이름, 데이터 형식, 기본적으로 사용되는 데이터 값 및 보고서를 열 때 이 값이 매개 변수 영역에 나타나는지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52644-137">The list shows the parameter name, data type, data value that is used by default, and whether it is visible in the parameter area when you open the report.</span></span>  
  
4.  <span data-ttu-id="52644-138">목록에서 매개 변수를 클릭하여 해당 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-138">Click a parameter in the list to modify its settings.</span></span>  
  
5.  <span data-ttu-id="52644-139">기본값에 매개 변수의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-139">In Default Value, enter a value for the parameter.</span></span> <span data-ttu-id="52644-140">값의 유효성은 검사되지 않으므로 보고서에 유효한 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-140">The value will not be validated, so be sure that you are providing a value that works for the report.</span></span>  
  
    1.  <span data-ttu-id="52644-141">보고서를 만들 때 정의한 기본값을 사용하려면 **보고서에 지정된 값 식 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-141">Choose **Use value expression specified in report definition** if you want to use the default value that was defined when the report was created.</span></span> <span data-ttu-id="52644-142">보고서 정의에 기본값이 제공되어 있지 않으면 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-142">If the report definition does not provide a default value, this option will be unavailable.</span></span>  
  
    2.  <span data-ttu-id="52644-143">보고서 정의 기본값을 대체할 값을 지정하려면 **보고서 기본값 다시 정의** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-143">Choose **Override the report default value** if you want to specify a replacement for the report definition default value.</span></span> <span data-ttu-id="52644-144">Null 값을 허용하는 보고서 매개 변수에 대해 필요에 따라 **Null** 확인란을 선택하여 해당 매개 변수를 기반으로 필터링되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-144">Optionally, for report parameters that accept null values, you can select the **Null** check box to prevent filtering based on that parameter.</span></span>  
  
    3.  <span data-ttu-id="52644-145">보고서가 처리되기 전에 각 사용자가 값을 지정하도록 하려면 **기본값 사용 안 함** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-145">Choose **Parameter does not have a default value** if you want each user to specify a value before the report is processed.</span></span> <span data-ttu-id="52644-146">이 옵션을 선택하는 경우 사용자에게 값을 지정하라는 메시지를 나타내는 표시 설정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-146">If you select this option, you should set display settings that prompt the user to specify a value.</span></span>  
  
     <span data-ttu-id="52644-147">모든 매개 변수 값에 기본값이 있으면 사용자가 보고서를 열 때 해당 값을 사용하여 자동으로 보고서가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="52644-147">Note that if all parameter values have a default value, the report will automatically run with those values when the user opens the report.</span></span> <span data-ttu-id="52644-148">그러나 매개 변수 영역이 표시되면 사용자가 기본값을 다시 정의하고 보고서를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-148">However, if the parameter area is displayed, users can override the default value and re-run the report.</span></span>  
  
6.  <span data-ttu-id="52644-149">표시 옵션을 설정하여 매개 변수를 표시할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-149">Set display options to determine whether the parameter is visible.</span></span>  
  
    1.  <span data-ttu-id="52644-150">페이지에 매개 변수를 표시하려면 **사용자에게 확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-150">Choose **Prompt User** to show the parameter on the page.</span></span> <span data-ttu-id="52644-151">사용자가 제공해야 하는 데이터 형식에 대해 간단히 설명하는 프롬프트 텍스트를 지정하여 필드 내에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52644-151">You can specify prompt text that appears within a field to provide a brief statement about the format or type of data that the user must provide.</span></span>  
  
    2.  <span data-ttu-id="52644-152">기본값을 사용하고 매개 변수 영역에 매개 변수를 표시하지 않으려면 **숨김** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-152">Choose **Hidden** if you are using a default value and you do not want the parameter to be visible in the Parameters area.</span></span>  
  
    3.  <span data-ttu-id="52644-153">기본값을 사용하고 매개 변수 영역이나 구독 페이지에 매개 변수를 표시하지 않으려면 **내부** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-153">Choose **Internal** if you are using a default value and you do not want the parameter to be visible in the Parameters area or on subscription pages.</span></span>  
  
7.  <span data-ttu-id="52644-154">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52644-154">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52644-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52644-155">See Also</span></span>  
 [<span data-ttu-id="52644-156">보고서 서버 항목에 대한 SharePoint 사이트 및 목록 사용 권한 참조</span><span class="sxs-lookup"><span data-stu-id="52644-156">SharePoint Site and List Permission Reference for Report Server Items</span></span>](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
