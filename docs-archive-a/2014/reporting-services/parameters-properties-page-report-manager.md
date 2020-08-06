---
title: 매개 변수 속성 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddaf6598225c36bd6490797e52aeb1a5fed1b60a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648850"
---
# <a name="parameters-properties-page-report-manager"></a><span data-ttu-id="81773-102">매개 변수 속성 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="81773-102">Parameters Properties Page (Report Manager)</span></span>
  <span data-ttu-id="81773-103">매개 변수 속성 페이지를 사용하여 매개 변수가 있는 보고서의 매개 변수 설정을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-103">Use the Parameters properties page to view or modify parameter settings for a parameterized report.</span></span>  
  
 <span data-ttu-id="81773-104">매개 변수는 보고서를 게시하기 전에 보고서 정의에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-104">Parameters are specified in the report definition before the report is published.</span></span> <span data-ttu-id="81773-105">보고서를 게시한 후에도 일부 매개 변수 속성 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-105">After the report is published, you can modify some parameter property values.</span></span> <span data-ttu-id="81773-106">수정할 수 있는 값은 보고서에서 매개 변수를 정의하는 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="81773-106">The values that you can modify will vary based on how the parameters are defined in the report.</span></span> <span data-ttu-id="81773-107">예를 들어 매개 변수에 대해 정적 값 목록을 정의하는 경우에는 다른 정적 값을 기본값으로 사용하도록 선택할 수는 있지만 목록 값을 추가하거나 제거할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-107">For example, if a list of static values is defined for a parameter, you can choose a different static value to use as a default, but you cannot add or remove values from the list.</span></span> <span data-ttu-id="81773-108">마찬가지로 매개 변수가 쿼리를 기반으로 하는 경우에는 null이나 공백 값 허용 여부와 기본값 제공 여부에 관계없이 사용되는 데이터 세트를 포함하여 해당 쿼리의 모든 항목이 게시 전에 보고서에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-108">Similarly, if the parameter is based on a query, all aspects of that query (including the dataset that is used, whether null or blank values are allowed, and whether a default value is provided) are defined in the report before publication.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="81773-109">탐색</span><span class="sxs-lookup"><span data-stu-id="81773-109">Navigation</span></span>  
 <span data-ttu-id="81773-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="81773-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-parameters-properties-page"></a><span data-ttu-id="81773-111">매개 변수 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="81773-111">To open the Parameters properties page</span></span>  
  
1.  <span data-ttu-id="81773-112">보고서 관리자를 열고 매개 변수 설정을 수정할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-112">Open Report Manager, and locate the report for which you want to modify parameter settings.</span></span>  
  
2.  <span data-ttu-id="81773-113">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="81773-114">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="81773-115">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81773-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="81773-116">**매개 변수** 탭을 선택 합니다. **매개 변수** 탭이 표시 되지 않는 경우 보고서에 매개 변수가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-116">Select the **Parameters** tab. If the **Parameters** tab is not visible, the report does not contain parameters.</span></span>  
  
## <a name="options"></a><span data-ttu-id="81773-117">옵션</span><span class="sxs-lookup"><span data-stu-id="81773-117">Options</span></span>  
 <span data-ttu-id="81773-118">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="81773-118">**Parameter Name**</span></span>  
 <span data-ttu-id="81773-119">매개 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-119">Specifies the name of the parameter.</span></span>  
  
 <span data-ttu-id="81773-120">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="81773-120">**Data Type**</span></span>  
 <span data-ttu-id="81773-121">매개 변수의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-121">Specifies the data type of the parameter.</span></span>  
  
 <span data-ttu-id="81773-122">**기본값 설정 여부**</span><span class="sxs-lookup"><span data-stu-id="81773-122">**Has Default**</span></span>  
 <span data-ttu-id="81773-123">이 확인란을 선택하여 매개 변수의 기본값 유무를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-123">Select this check box to specify whether the parameter has a default value.</span></span> <span data-ttu-id="81773-124">이 확인란을 선택하면 **기본값**이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-124">Selecting this check box enables **Default Value**.</span></span> <span data-ttu-id="81773-125">보고서 매개 변수가 Null 값을 허용하는 경우 **Null** 도 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-125">It also enables **Null** if the report parameter accepts null values.</span></span> <span data-ttu-id="81773-126">**기본값 설정 여부** 를 선택하지 않으면 값을 숨기거나 보고서를 실행할 때 사용자에게 값을 제공하라는 메시지를 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-126">If **Has Default** is not selected, you must either hide the value or prompt the user to provide a value when the report runs.</span></span>  
  
 <span data-ttu-id="81773-127">**기본값**</span><span class="sxs-lookup"><span data-stu-id="81773-127">**Default Value**</span></span>  
 <span data-ttu-id="81773-128">매개 변수의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-128">Specify a value for the parameter.</span></span> <span data-ttu-id="81773-129">기본값을 지정하려면 **기본값 설정 여부** 를 선택하고 **Null** 은 선택하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-129">To specify a default value, **Has Default** must be selected, and **Null** must not be selected.</span></span> <span data-ttu-id="81773-130">기본값은 보고서 정의를 통해 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-130">A default value may be provided through the report definition.</span></span> <span data-ttu-id="81773-131">**기본값** 이 하나 이상의 정적 값으로 채워지는 경우 이 값들은 보고서에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81773-131">If **Default Value** is populated with one or more static values, those values originate with the report.</span></span> <span data-ttu-id="81773-132">**기본값** 이 **쿼리 기반**인 경우 매개 변수 값은 보고서에 정의된 쿼리에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-132">If **Default value** is **Query Based**, the parameter value is determined by a query that is defined in the report.</span></span>  
  
 <span data-ttu-id="81773-133">**기본값** 에 값을 입력할 수 있는 경우 보고서에 사용된 데이터 처리 확장 프로그램에 적합한 상수나 구문을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-133">If **Default Value** accepts a value, you can type a constant or syntax that is valid for the data processing extension used with the report.</span></span> <span data-ttu-id="81773-134">예를 들어 데이터 처리 확장 프로그램의 쿼리 언어에서 와일드카드를 지원하는 경우 와일드카드 문자를 기본값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-134">For example, if the query language of the data processing extension supports wildcards, you can specify a wildcard character as a default value.</span></span>  
  
 <span data-ttu-id="81773-135">이후에 사용자에게 프롬프트가 표시되도록 지정하면 이 기본값은 사용자가 사용하거나 수정할 수 있는 초기 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-135">If you subsequently specify that a prompt be displayed to the user, the default value becomes an initial value that users can either use or modify.</span></span> <span data-ttu-id="81773-136">매개 변수 값을 입력하라는 요청이 없는 경우 이 값은 보고서를 사용하는 모든 사용자에 대해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-136">If you do not prompt for a parameter value, this value is used for all users who run the report.</span></span>  
  
 <span data-ttu-id="81773-137">**Null**</span><span class="sxs-lookup"><span data-stu-id="81773-137">**Null**</span></span>  
 <span data-ttu-id="81773-138">이 확인란을 선택하면 Null을 기본값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-138">Select this check box to specify null as the default value.</span></span> <span data-ttu-id="81773-139">Null 값을 지정하면 사용자가 매개 변수 값을 제공하지 않아도 보고서가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-139">A null value means that the report runs even if the user does not provide a parameter value.</span></span> <span data-ttu-id="81773-140">이 열에 확인란이 없으면 매개 변수가 Null 값을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-140">If there is no check box in this column, the parameter does not accept null values.</span></span>  
  
 <span data-ttu-id="81773-141">**숨기기**</span><span class="sxs-lookup"><span data-stu-id="81773-141">**Hide**</span></span>  
 <span data-ttu-id="81773-142">보고서 맨 위에 나타나는 매개 변수 영역에서 매개 변수를 숨기려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-142">Select this check box to hide the parameter in the parameter area that appears at the top of the report.</span></span> <span data-ttu-id="81773-143">매개 변수는 계속 구독 정의 페이지에 나타나며 보고서 URL에서도 계속 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-143">The parameter will still appear in subscription definition pages and it can still be specified on a report URL.</span></span> <span data-ttu-id="81773-144">항상 사용자가 지정한 기본값으로 보고서를 실행하려는 경우에는 매개 변수를 숨기는 것이 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-144">Hiding the parameter is useful when you want to always run the report with a default value that you specify.</span></span>  
  
 <span data-ttu-id="81773-145">보고서에 매개 변수를 표시하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-145">Clear this check box if you want the parameter to be visible in the report.</span></span>  
  
 <span data-ttu-id="81773-146">**사용자에게 확인**</span><span class="sxs-lookup"><span data-stu-id="81773-146">**Prompt User**</span></span>  
 <span data-ttu-id="81773-147">사용자에게 매개 변수 값 입력을 요청하는 입력란을 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-147">Select this check box to display a text box that prompts users for a parameter value.</span></span>  
  
 <span data-ttu-id="81773-148">보고서를 무인 모드로 실행하려는 경우(예: 보고서 기록 또는 보고서 실행 스냅샷 생성), 모든 사용자에 대해 동일한 매개 변수 값을 사용하려는 경우 또는 사용자가 값을 입력하지 않도록 하려는 경우에는 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-148">Clear this check box if you want to run the report in unattended mode (for example, to generate report history or report execution snapshots), if you want to use the same parameter value for all users, or if you do not require user input for the value.</span></span>  
  
 <span data-ttu-id="81773-149">**텍스트 표시**</span><span class="sxs-lookup"><span data-stu-id="81773-149">**Display Text**</span></span>  
 <span data-ttu-id="81773-150">매개 변수 입력란 옆에 표시되는 텍스트 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="81773-150">Provide a text string that appears next to the parameter text box.</span></span> <span data-ttu-id="81773-151">이 문자열은 레이블이나 설명문으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-151">This string provides a label or descriptive text.</span></span> <span data-ttu-id="81773-152">문자열 길이는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81773-152">There is no limit on string length.</span></span> <span data-ttu-id="81773-153">텍스트 문자열이 긴 경우 해당 공간에 맞게 줄 바꿈됩니다.</span><span class="sxs-lookup"><span data-stu-id="81773-153">Longer text strings wrap within the space provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81773-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81773-154">See Also</span></span>  
 <span data-ttu-id="81773-155">[일반 속성 페이지, 보고서 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="81773-155">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="81773-156">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="81773-156">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
