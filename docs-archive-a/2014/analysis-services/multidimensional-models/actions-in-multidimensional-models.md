---
title: 다차원 모델의 동작 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
ms.openlocfilehash: ce42907190363be085e8f4d8e9adfbab52a70590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649756"
---
# <a name="actions-in-multidimensional-models"></a><span data-ttu-id="eaee4-102">다차원 모델의 동작</span><span class="sxs-lookup"><span data-stu-id="eaee4-102">Actions in Multidimensional Models</span></span>
  <span data-ttu-id="eaee4-103">동작이란 선택한 큐브 또는 큐브의 일부분에 대해 최종 사용자가 시작하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-103">An action is an end user-initiated operation upon a selected cube or portion of a cube.</span></span> <span data-ttu-id="eaee4-104">작업은 선택한 항목을 매개 변수로 애플리케이션을 시작하거나 선택한 항목에 대한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-104">The operation can start an application with the selected item as a parameter, or it can retrieve information about the selected item.</span></span> <span data-ttu-id="eaee4-105">동작에 대한 자세한 내용은 [동작&#40;Analysis Services - 다차원 데이터&#41;](actions-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaee4-105">For more information about actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="eaee4-106">큐브 디자이너의 **동작** 탭을 사용하여 큐브에 대한 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-106">Use the **Actions** tab of Cube Designer to build actions for a cube.</span></span> <span data-ttu-id="eaee4-107">다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-107">Specify the following:</span></span>  
  
 <span data-ttu-id="eaee4-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="eaee4-108">**Name**</span></span>  
 <span data-ttu-id="eaee4-109">동작을 식별하는 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-109">Select a name that identifies the action.</span></span>  
  
 <span data-ttu-id="eaee4-110">**동작 대상**</span><span class="sxs-lookup"><span data-stu-id="eaee4-110">**Action Target**</span></span>  
 <span data-ttu-id="eaee4-111">동작을 연결할 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-111">Select the object to which the action is attached.</span></span> <span data-ttu-id="eaee4-112">클라이언트 애플리케이션에서는 일반적으로 최종 사용자가 대상 개체를 선택할 때 작업이 표시되지만 동작을 표시하는 최종 사용자의 동작은 클라이언트 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-112">Generally, in client applications, the action is displayed when end users select the target object; however, the client application determines which end-user operation displays actions.</span></span> <span data-ttu-id="eaee4-113">다음 개체 중에서 **대상 유형**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-113">For **Target type**, select from the following objects:</span></span>  
  
-   <span data-ttu-id="eaee4-114">특성 멤버</span><span class="sxs-lookup"><span data-stu-id="eaee4-114">Attribute members</span></span>  
  
-   <span data-ttu-id="eaee4-115">셀</span><span class="sxs-lookup"><span data-stu-id="eaee4-115">Cells</span></span>  
  
-   <span data-ttu-id="eaee4-116">큐브</span><span class="sxs-lookup"><span data-stu-id="eaee4-116">Cube</span></span>  
  
-   <span data-ttu-id="eaee4-117">차원 멤버</span><span class="sxs-lookup"><span data-stu-id="eaee4-117">Dimension members</span></span>  
  
-   <span data-ttu-id="eaee4-118">계층</span><span class="sxs-lookup"><span data-stu-id="eaee4-118">Hierarchy</span></span>  
  
-   <span data-ttu-id="eaee4-119">계층 멤버</span><span class="sxs-lookup"><span data-stu-id="eaee4-119">Hierarchy members</span></span>  
  
-   <span data-ttu-id="eaee4-120">Level</span><span class="sxs-lookup"><span data-stu-id="eaee4-120">Level</span></span>  
  
-   <span data-ttu-id="eaee4-121">수준 멤버</span><span class="sxs-lookup"><span data-stu-id="eaee4-121">Level members</span></span>  
  
 <span data-ttu-id="eaee4-122">대상 개체 유형을 선택한 후 **대상 개체**에서 지정된 유형의 큐브 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-122">After you select the target object type, under **Target object**, select the cube object of the designated type.</span></span>  
  
 <span data-ttu-id="eaee4-123">**조건(옵션)**</span><span class="sxs-lookup"><span data-stu-id="eaee4-123">**Condition (Optional)**</span></span>  
 <span data-ttu-id="eaee4-124">부울 값으로 확인되는 선택적 MDX(Multidimensional Expression) 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-124">Specify an optional Multidimensional Expressions (MDX) expression that resolves to a Boolean value.</span></span> <span data-ttu-id="eaee4-125">값이 `True`이면 지정된 대상에서 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-125">If the value is `True`, the action is performed on the specified target.</span></span> <span data-ttu-id="eaee4-126">값이 `False`이면 동작이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-126">If the value is `False`, the action is not performed.</span></span>  
  
 <span data-ttu-id="eaee4-127">**동작 내용**</span><span class="sxs-lookup"><span data-stu-id="eaee4-127">**Action Content**</span></span>  
 <span data-ttu-id="eaee4-128">동작의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-128">Select the type of action.</span></span> <span data-ttu-id="eaee4-129">다음 표에는 사용 가능한 유형이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-129">The following table summarizes the available types.</span></span>  
  
|<span data-ttu-id="eaee4-130">Type</span><span class="sxs-lookup"><span data-stu-id="eaee4-130">Type</span></span>|<span data-ttu-id="eaee4-131">Description</span><span class="sxs-lookup"><span data-stu-id="eaee4-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="eaee4-132">데이터 집합</span><span class="sxs-lookup"><span data-stu-id="eaee4-132">Data Set</span></span>|<span data-ttu-id="eaee4-133">데이터 세트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-133">Retrieves a dataset.</span></span>|  
|<span data-ttu-id="eaee4-134">소유</span><span class="sxs-lookup"><span data-stu-id="eaee4-134">Proprietary</span></span>|<span data-ttu-id="eaee4-135">이 표에 나열되지 않은 인터페이스를 사용하여 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-135">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="eaee4-136">행 집합</span><span class="sxs-lookup"><span data-stu-id="eaee4-136">Row Set</span></span>|<span data-ttu-id="eaee4-137">행 집합을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-137">Retrieves a rowset.</span></span>|  
|<span data-ttu-id="eaee4-138">문</span><span class="sxs-lookup"><span data-stu-id="eaee4-138">Statement</span></span>|<span data-ttu-id="eaee4-139">OLE DB 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-139">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="eaee4-140">URL</span><span class="sxs-lookup"><span data-stu-id="eaee4-140">URL</span></span>|<span data-ttu-id="eaee4-141">가변 페이지를 인터넷 브라우저로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-141">Displays a variable page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="eaee4-142">**동작 식**의 경우 작업이 실행될 때 전달되는 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-142">For **Action Expression**, specify the parameters that are passed when the action is run.</span></span> <span data-ttu-id="eaee4-143">구문은 문자열로 평가되어야 하며 MDX로 작성된 식이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-143">The syntax must evaluate to a string, and you must include an expression written in MDX.</span></span> <span data-ttu-id="eaee4-144">예를 들어 MDX 식으로 구문에 포함되는 큐브의 일부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-144">For example, your MDX expression can indicate a part of the cube that is included in the syntax.</span></span> <span data-ttu-id="eaee4-145">MDX 식은 매개 변수가 전달되기 전에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-145">MDX expressions are evaluated before the parameters are passed.</span></span> <span data-ttu-id="eaee4-146">또한 MDX 식 작성을 도와 주는 MDX 작성기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-146">Also, MDX Builder is available to help you build MDX expressions.</span></span>  
  
 <span data-ttu-id="eaee4-147">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="eaee4-147">**Additional Properties**</span></span>  
 <span data-ttu-id="eaee4-148">속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-148">Select the property.</span></span> <span data-ttu-id="eaee4-149">다음 표에는 사용 가능한 속성이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-149">The following table summarizes the available properties.</span></span>  
  
|<span data-ttu-id="eaee4-150">속성</span><span class="sxs-lookup"><span data-stu-id="eaee4-150">Property</span></span>|<span data-ttu-id="eaee4-151">Description</span><span class="sxs-lookup"><span data-stu-id="eaee4-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="eaee4-152">**호출**</span><span class="sxs-lookup"><span data-stu-id="eaee4-152">**Invocation**</span></span>|<span data-ttu-id="eaee4-153">동작 실행 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-153">Specifies how the action is run.</span></span> <span data-ttu-id="eaee4-154">기본값인 대화형은 사용자가 개체에 액세스할 때 동작이 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-154">Interactive, the default, specifies that the action is run when a user accesses an object.</span></span> <span data-ttu-id="eaee4-155">가능한 설정은 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-155">The possible settings are:</span></span><br /><br /> <span data-ttu-id="eaee4-156">Batch</span><span class="sxs-lookup"><span data-stu-id="eaee4-156">Batch</span></span><br /><br /> <span data-ttu-id="eaee4-157">대화형</span><span class="sxs-lookup"><span data-stu-id="eaee4-157">Interactive</span></span><br /><br /> <span data-ttu-id="eaee4-158">열 때</span><span class="sxs-lookup"><span data-stu-id="eaee4-158">On Open</span></span>|  
|<span data-ttu-id="eaee4-159">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="eaee4-159">**Application**</span></span>|<span data-ttu-id="eaee4-160">동작의 애플리케이션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-160">Describes the application of the action.</span></span>|  
|<span data-ttu-id="eaee4-161">**설명**</span><span class="sxs-lookup"><span data-stu-id="eaee4-161">**Description**</span></span>|<span data-ttu-id="eaee4-162">동작에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-162">Describes the action.</span></span>|  
|<span data-ttu-id="eaee4-163">**캡션**</span><span class="sxs-lookup"><span data-stu-id="eaee4-163">**Caption**</span></span>|<span data-ttu-id="eaee4-164">동작에 대해 표시되는 캡션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-164">Provides a caption that is displayed for the action.</span></span> <span data-ttu-id="eaee4-165">캡션이 MDX 인 경우 `True` **캡션에 mdx**를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-165">If the caption is MDX, specify `True` for **Caption is MDX**.</span></span>|  
|<span data-ttu-id="eaee4-166">**MDX 캡션**</span><span class="sxs-lookup"><span data-stu-id="eaee4-166">**Caption is MDX**</span></span>|<span data-ttu-id="eaee4-167">캡션이 MDX이면 `True`를 지정하고 그렇지 않으면 `False`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-167">Specify `True` if the caption is MDX or `False` if it is not.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="eaee4-168">HTML 및 명령줄 동작 유형을 정의하려면 ASSL(Analysis Services Scripting Language)이나 AMO(Analysis Management Objects)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-168">You must use Analysis Services Scripting Language (ASSL) or Analysis Management Objects (AMO) to define HTML and Command Line action types.</span></span> <span data-ttu-id="eaee4-169">자세한 내용은 [Action 요소&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type 요소&#40;Action&#41;&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl) 및 [AMO OLAP 고급 개체 프로그래밍](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaee4-169">For more information, see [Action Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type Element &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl), and [Programming AMO OLAP Advanced Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects).</span></span>  
  
## <a name="creating-a-reporting-action"></a><span data-ttu-id="eaee4-170">보고 동작 만들기</span><span class="sxs-lookup"><span data-stu-id="eaee4-170">Creating a Reporting Action</span></span>  
 <span data-ttu-id="eaee4-171">보고서 서버는 URL 기반 보고서 요청에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-171">The report server responds to URL-based requests for reports.</span></span> <span data-ttu-id="eaee4-172">보고 동작을 만들려면 **큐브** 메뉴에서 **새 보고 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-172">To create a reporting action, on the **Cube** menu, click **New Reporting Action**.</span></span> <span data-ttu-id="eaee4-173">보고 동작에 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-173">The following options are specific to a reporting action.</span></span>  
  
 <span data-ttu-id="eaee4-174">**보고서 서버**</span><span class="sxs-lookup"><span data-stu-id="eaee4-174">**Report Server**</span></span>  
 <span data-ttu-id="eaee4-175">보고서 서버에 다음 표에서 설명하는 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-175">The properties described in the following table are specified for the report server.</span></span>  
  
|<span data-ttu-id="eaee4-176">속성</span><span class="sxs-lookup"><span data-stu-id="eaee4-176">Property</span></span>|<span data-ttu-id="eaee4-177">Description</span><span class="sxs-lookup"><span data-stu-id="eaee4-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="eaee4-178">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="eaee4-178">**Server name**</span></span>|<span data-ttu-id="eaee4-179">보고서 서버를 실행 중인 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-179">The name of the computer running report server.</span></span>|  
|<span data-ttu-id="eaee4-180">**서버 경로**</span><span class="sxs-lookup"><span data-stu-id="eaee4-180">**Server path**</span></span>|<span data-ttu-id="eaee4-181">보고서 서버를 나타내는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-181">The path exposed by report server.</span></span>|  
|<span data-ttu-id="eaee4-182">**보고서 형식**</span><span class="sxs-lookup"><span data-stu-id="eaee4-182">**Report format**</span></span>|<span data-ttu-id="eaee4-183">HTML5, HTML3, Excel 또는 PDF입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-183">HTML5, HTML3, Excel, or PDF.</span></span>|  
  
 <span data-ttu-id="eaee4-184">**매개 변수(옵션)**</span><span class="sxs-lookup"><span data-stu-id="eaee4-184">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="eaee4-185">매개 변수는 동작이 생성될 때 URL 문자열의 일부로 서버에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-185">The parameters are sent to the server as part of the URL string when the action is created.</span></span> <span data-ttu-id="eaee4-186">이러한 매개 변수에는 MDX 식인 **매개 변수 이름** 과 **매개 변수 값**이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-186">They include **Parameter Name** and **Parameter Value**, which is an MDX expression.</span></span>  
  
 <span data-ttu-id="eaee4-187">보고서 서버 URL의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-187">The report server URL is constructed as follows:</span></span>  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 <span data-ttu-id="eaee4-188">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-188">For example:</span></span>  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a><span data-ttu-id="eaee4-189">드릴스루 동작 만들기</span><span class="sxs-lookup"><span data-stu-id="eaee4-189">Creating a Drillthrough Action</span></span>  
 <span data-ttu-id="eaee4-190">드릴스루 동작은 클라이언트 애플리케이션에 드릴스루 문으로 반환되는 행 집합 작업으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-190">A drillthrough action is defined by a rowset action, which is returned to the client application as a drillthrough statement.</span></span> <span data-ttu-id="eaee4-191">동작 대상은 측정값 그룹의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-191">The action target is a member of a measure group.</span></span> <span data-ttu-id="eaee4-192">새 드릴스루 작업을 만들려면 **큐브** 메뉴에서 **새 드릴스루 동작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-192">To create a new drillthrough action, on the **Cube** menu, click **New Drillthrough Action**.</span></span> <span data-ttu-id="eaee4-193">드릴스루 동작에 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-193">The following options are specific to a drillthrough action:</span></span>  
  
 <span data-ttu-id="eaee4-194">**드릴스루 열**</span><span class="sxs-lookup"><span data-stu-id="eaee4-194">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="eaee4-195">하나 이상의 차원을 선택하고 각 차원에 대해 동작에 따라 클라이언트 애플리케이션에 반환되는 드릴스루 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaee4-195">Select one or more dimensions and, for each dimension, the drillthrough columns returned to the client application by the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaee4-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eaee4-196">See Also</span></span>  
 [<span data-ttu-id="eaee4-197">다차원 모델의 큐브</span><span class="sxs-lookup"><span data-stu-id="eaee4-197">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
