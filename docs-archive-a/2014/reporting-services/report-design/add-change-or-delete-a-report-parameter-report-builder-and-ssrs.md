---
title: 보고서 매개 변수 추가, 변경 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 231cd51d7ed0a481f004b39a2e8819df3fc33748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650764"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="bb8d6-102">보고서 매개 변수 추가, 변경 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="bb8d6-102">Add, Change, or Delete a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bb8d6-103">보고서 매개 변수를 사용하면 보고서 데이터를 선택하고, 관련된 보고서를 서로 연결하고, 다양하게 보고서를 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-103">A report parameter provides a way to choose report data, connect related reports together, and vary the report presentation.</span></span> <span data-ttu-id="bb8d6-104">기본값 및 사용 가능한 값 목록을 제공할 수 있으며 사용자는 선택 항목을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-104">You can provide a default value and a list of available values, and the user can change the selection.</span></span>  
  
 <span data-ttu-id="bb8d6-105">보고서를 게시한 후에는 보고서 서버에서 보고서 매개 변수의 기본값, 사용 가능한 값 및 기타 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-105">After you publish a report, you can change the default values, the available values, and other properties for a report parameter on the report server.</span></span> <span data-ttu-id="bb8d6-106">링크된 보고서를 만들어 여러 기본 매개 변수 값 집합을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-106">You can provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="bb8d6-107">자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 온라인 설명서 [의](https://go.microsoft.com/fwlink/?linkid=120955)설명서에 있는 "게시된 보고서의 매개 변수 속성 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-107">For more information, see "Setting Parameter Properties for a Published Report" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a><span data-ttu-id="bb8d6-108">보고서 매개 변수를 추가하거나 편집하려면</span><span class="sxs-lookup"><span data-stu-id="bb8d6-108">To add or edit a report parameter</span></span>  
  
1.  <span data-ttu-id="bb8d6-109">**보고서 데이터** 창에서 **매개 변수** 노드를 마우스 오른쪽 단추로 클릭하고 **매개 변수 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-109">In the **Report Data** pane, right-click the **Parameters** node and click **Add Parameter**.</span></span> <span data-ttu-id="bb8d6-110">**보고서 매개 변수 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-110">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="bb8d6-111">**이름**에 매개 변수의 이름을 입력하거나 기본 이름을 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-111">In **Name**, type the name of the parameter or accept the default name.</span></span>  
  
3.  <span data-ttu-id="bb8d6-112">**프롬프트**에 사용자가 보고서를 실행할 때 매개 변수 입력란 옆에 표시되는 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-112">In **Prompt**, type the text that appears next to the parameter text box when the user runs the report.</span></span>  
  
4.  <span data-ttu-id="bb8d6-113">**데이터 형식**에서 매개 변수 값에 대한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-113">In **Data type**, select the data type for the parameter value.</span></span>  
  
5.  <span data-ttu-id="bb8d6-114">매개 변수에 빈 값을 포함할 수 있는 경우 **빈 값 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-114">If the parameter can contain a blank value, select **Allow blank value**.</span></span>  
  
6.  <span data-ttu-id="bb8d6-115">매개 변수에 Null 값을 포함할 수 있는 경우 **Null 값 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-115">If the parameter can contain a null value, select **Allow null value**.</span></span>  
  
7.  <span data-ttu-id="bb8d6-116">사용자가 매개 변수 값을 둘 이상 선택할 수 있도록 하려면 **다중 값 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-116">To allow a user to select more than one value for the parameter, select **Allow multiple values**.</span></span>  
  
8.  <span data-ttu-id="bb8d6-117">표시 여부 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-117">Set the visibility option.</span></span>  
  
    -   <span data-ttu-id="bb8d6-118">보고서 위쪽의 도구 모음에 매개 변수를 표시하려면 **표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-118">To show the parameter on the toolbar at the top of the report, select **Visible**.</span></span>  
  
    -   <span data-ttu-id="bb8d6-119">매개 변수를 숨겨서 도구 모음에 표시하지 않으려면 **숨김**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-119">To hide the parameter so that it does not display on the toolbar, select **Hidden**.</span></span>  
  
    -   <span data-ttu-id="bb8d6-120">매개 변수를 숨겨서 보고서가 게시된 후 보고서 서버에서 수정되지 않도록 하려면 **내부**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-120">To hide the parameter and protect it from being modified on the report server after the report is published, select **Internal**.</span></span> <span data-ttu-id="bb8d6-121">그러면 보고서 매개 변수는 보고서 정의에서만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-121">The report parameter can then only be viewed in the report definition.</span></span> <span data-ttu-id="bb8d6-122">이 옵션을 사용하려면 기본값을 설정하거나 Null 값을 허용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-122">For this option, you must set a default value or allow the parameter to accept a null value.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a><span data-ttu-id="bb8d6-123">보고서 매개 변수를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="bb8d6-123">To delete a report parameter</span></span>  
  
1.  <span data-ttu-id="bb8d6-124">**보고서 데이터** 창에서 **매개 변수** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-124">In the **Report Data** pane, expand the **Parameters** node.</span></span>  
  
2.  <span data-ttu-id="bb8d6-125">보고서 매개 변수를 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8d6-125">Right-click the report parameter and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8d6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb8d6-126">See Also</span></span>  
 <span data-ttu-id="bb8d6-127">[보고서 매개 변수의 사용 가능한 값을 추가, 변경 또는 삭제 &#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-127">[Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="bb8d6-128">[보고서 매개 변수의 기본값 추가, 변경 또는 삭제 &#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-128">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="bb8d6-129">[보고서 매개 변수의 순서를 변경 하 여 보고서 작성기 및 SSRS를 &#40;&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-129">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bb8d6-130">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-130">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="bb8d6-131">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-131">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="bb8d6-132">[보고서 &#40;보고서 작성기 및 SSRS에 연계 매개 변수를 추가&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-132">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bb8d6-133">[자습서: 보고서에 매개 변수를 추가 &#40;보고서 작성기&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-133">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="bb8d6-134">[자습서 &#40;보고서 작성기&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-134">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="bb8d6-135">[데이터 집합 필터, 데이터 영역 필터 및 그룹 필터를 추가 하 여 보고서 작성기 및 SSRS &#40;&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-135">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="bb8d6-136">[매개 변수 컬렉션 참조 &#40;보고서 작성기 및 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bb8d6-136">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 [<span data-ttu-id="bb8d6-137">보고서에 다중 값 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="bb8d6-137">Add a multi-value parameter to a Report</span></span>](add-a-multi-value-parameter-to-a-report.md)  
  
  
