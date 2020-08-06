---
title: 계산 멤버 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated members [Analysis Services]
- custom measures [Analysis Services]
- members [Analysis Services], calculated
- calculations [Analysis Services], calculated members
ms.assetid: 820e4b18-9c3a-4b12-a126-ca16d8364a00
author: minewiskan
ms.author: owend
ms.openlocfilehash: c45ef3cf720e6a3cc43156b032d91d205d6334bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646693"
---
# <a name="create-calculated-members"></a><span data-ttu-id="647ee-102">계산 멤버 만들기</span><span class="sxs-lookup"><span data-stu-id="647ee-102">Create Calculated Members</span></span>
  <span data-ttu-id="647ee-103">큐브 데이터, 산술 연산자, 숫자 및 함수 등을 결합하여 계산 멤버라고 하는 사용자 지정 측정값 또는 차원 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-103">You can create customized measures or dimension members, called calculated members, by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="647ee-104">예를 들어 기존 달러 측정값을 환율과 곱해서 달러를 유로로 환산하는 Euros라는 계산 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-104">For example, you can create a calculated member named Euros that converts dollars to euros by multiplying an existing dollar measure by a conversion rate.</span></span> <span data-ttu-id="647ee-105">그런 다음 Euros를 별도의 행이나 열로 최종 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-105">Euros can then be displayed to end users in a separate row or column.</span></span>  
  
 <span data-ttu-id="647ee-106">계산 멤버의 정의는 저장되지만, 값은 메모리에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-106">Calculated member definitions are stored, but their values exist only in memory.</span></span> <span data-ttu-id="647ee-107">위의 예에서는 유로 값이 최종 사용자에게 표시되기만 하고 큐브 데이터로 저장되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-107">In the preceding example, values in marks are displayed to end users but are not stored as cube data.</span></span>  
  
 <span data-ttu-id="647ee-108">계산 멤버는 큐브에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-108">You create calculated members in cubes.</span></span> <span data-ttu-id="647ee-109">계산 멤버를 만들려면 큐브 디자이너의 **계산** 탭에서 도구 모음의 **새 계산 멤버** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-109">To create a calculated member, in Cube Designer, on the **Calculations** tab, click the **New Calculated Member** icon on the toolbar.</span></span> <span data-ttu-id="647ee-110">이 명령은 계산 멤버에 대해 다음 옵션을 지정할 수 있는 폼을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-110">This command displays a form to specify the following options for the calculated member:</span></span>  
  
 <span data-ttu-id="647ee-111">**이름**</span><span class="sxs-lookup"><span data-stu-id="647ee-111">**Name**</span></span>  
 <span data-ttu-id="647ee-112">계산 멤버의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-112">Select the name of the calculated member.</span></span> <span data-ttu-id="647ee-113">이 이름은 최종 사용자가 해당 큐브를 찾아볼 때 계산 멤버 값에 대한 열 또는 행 머리글로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-113">This name appears as the column or row heading for the calculated member values when end users browse the cube.</span></span>  
  
 <span data-ttu-id="647ee-114">**부모 계층**</span><span class="sxs-lookup"><span data-stu-id="647ee-114">**Parent hierarchy**</span></span>  
 <span data-ttu-id="647ee-115">계산 멤버에 포함할 부모 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-115">Select the parent hierarchy to include in the calculated member.</span></span> <span data-ttu-id="647ee-116">계층은 분석을 위해 큐브의 숫자 데이터(즉, 측정값)를 분리할 때 기준이 되는 차원의 설명 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-116">Hierarchies are descriptive categories of a dimension by which the numeric data (that is, measures) in a cube can be separated for analysis.</span></span> <span data-ttu-id="647ee-117">테이블 형식의 브라우저에서는 큐브 데이터를 찾아볼 때 최종 사용자에게 표시되는 열 머리글과 행 머리글이 계층에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-117">In tabular browsers, hierarchies provide the column and row headings displayed to end users when they browse data in a cube.</span></span> <span data-ttu-id="647ee-118">그래픽 브라우저에서는 다른 종류의 설명 레이블이 제공되지만, 기능은 테이블 형식의 브라우저와 동일합니다. 계산 멤버는 선택한 부모 차원에 새 머리글(또는 레이블)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-118">(In graphical browsers, they provide other types of descriptive labels, but they have the same function as in tabular browsers.) A calculated member provides a new heading (or label) in the parent dimension you select.</span></span>  
  
 <span data-ttu-id="647ee-119">또 다른 방법으로, 차원이 아닌 측정값에 계산 멤버를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-119">Alternatively, you can include the calculated member in the measures instead of in a dimension.</span></span> <span data-ttu-id="647ee-120">또한 이 옵션은 새로운 열 또는 행 머리글을 제공하지만, 이것은 브라우저에서 측정값에 첨부됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-120">This option also provides a new column or row heading, but it is attached to measures in the browser.</span></span>  
  
 <span data-ttu-id="647ee-121">**부모 멤버**</span><span class="sxs-lookup"><span data-stu-id="647ee-121">**Parent member**</span></span>  
 <span data-ttu-id="647ee-122">계산 멤버를 포함할 부모 멤버를 선택하려면 **변경** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-122">Click **Change** to select a parent member to include the calculated member.</span></span> <span data-ttu-id="647ee-123">한 수준으로 이루어진 계층 또는 측정값을 부모 차원으로 선택하는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-123">This option is unavailable if you select a one-level hierarchy or MEASURES as the parent dimension.</span></span>  
  
 <span data-ttu-id="647ee-124">계층은 멤버가 포함된 여러 개의 수준으로 나누어집니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-124">Hierarchies are divided into levels that contain members.</span></span> <span data-ttu-id="647ee-125">각 멤버는 열 머리글을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-125">Each member produces a heading.</span></span> <span data-ttu-id="647ee-126">최종 사용자는 큐브 데이터를 찾아보는 동안 선택한 머리글로부터 이전에 표시되지 않은 종속 머리글로 드릴다운할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-126">While browsing data in a cube, end users can drill down from a selected heading to previously undisplayed subordinate headings.</span></span> <span data-ttu-id="647ee-127">계산 멤버의 머리글은 선택한 부모 멤버 바로 아래 수준에서 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-127">The heading for the calculated member is added at the level directly below the parent member you select.</span></span>  
  
 <span data-ttu-id="647ee-128">**식**</span><span class="sxs-lookup"><span data-stu-id="647ee-128">**Expression**</span></span>  
 <span data-ttu-id="647ee-129">계산 멤버의 값을 생성하는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-129">Specify the expression that produces the values of the calculated member.</span></span> <span data-ttu-id="647ee-130">이 식은 다차원 식(MDX)으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-130">This expression can be written in Multidimensional Expressions (MDX).</span></span> <span data-ttu-id="647ee-131">식에 포함할 수 있는 항목들은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-131">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="647ee-132">차원, 수준, 측정값 등 큐브의 구성 요소를 나타내는 데이터 식</span><span class="sxs-lookup"><span data-stu-id="647ee-132">Data expressions that represent cube components such as dimensions, levels, measures, and so on</span></span>  
  
-   <span data-ttu-id="647ee-133">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="647ee-133">Arithmetic operators</span></span>  
  
-   <span data-ttu-id="647ee-134">숫자</span><span class="sxs-lookup"><span data-stu-id="647ee-134">Numbers</span></span>  
  
-   <span data-ttu-id="647ee-135">함수</span><span class="sxs-lookup"><span data-stu-id="647ee-135">Functions</span></span>  
  
 <span data-ttu-id="647ee-136">**계산 도구** 창의 **메타데이터** 탭에서 큐브 구성 요소를 끌어오거나 복사하여 식에 간편하게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-136">You can drag or copy cube components from the **Metadata** tab of the **Calculation Tools** pane to quickly add them to an expression.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="647ee-137">다른 계산 멤버의 값 식에서 사용될 모든 계산 멤버는 이를 사용할 계산 멤버보다 먼저 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-137">Any calculated member that is to be used in the value expression of another calculated member must be created before the calculated member that uses it.</span></span>  
  
 <span data-ttu-id="647ee-138">Format String</span><span class="sxs-lookup"><span data-stu-id="647ee-138">Format String</span></span>  
 <span data-ttu-id="647ee-139">계산 멤버를 기반으로 셀 값의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-139">Specifies the format of cell values that are based on the calculated member.</span></span> <span data-ttu-id="647ee-140">이 속성은 측정값의 `Display Format` 속성과 같은 값을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-140">This property accepts the same values as the `Display Format` property for measures.</span></span> <span data-ttu-id="647ee-141">표시 형식에 대한 자세한 내용은 [측정값 속성 구성](configure-measure-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="647ee-141">For more information about display formats, see [Configure Measure Properties](configure-measure-properties.md).</span></span>  
  
 <span data-ttu-id="647ee-142">표시</span><span class="sxs-lookup"><span data-stu-id="647ee-142">Visible</span></span>  
 <span data-ttu-id="647ee-143">큐브 메타데이터를 검색할 때 계산 멤버를 표시할 것인지 숨길 것인지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-143">Determines whether the calculated member is visible or hidden when cube metadata is retrieved.</span></span> <span data-ttu-id="647ee-144">계산 멤버를 숨길 경우 MDX 식, 문 및 스크립트에서 계산 멤버를 사용할 수는 있지만 클라이언트 사용자 인터페이스에서 선택 가능한 개체로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-144">If the calculated member is hidden, it can still be used in MDX expressions, statements, and scripts, but it is not displayed as a selectable object in client user interfaces.</span></span>  
  
 <span data-ttu-id="647ee-145">Non-empty Behavior</span><span class="sxs-lookup"><span data-stu-id="647ee-145">Non-empty Behavior</span></span>  
 <span data-ttu-id="647ee-146">MDX에서 NON EMPTY 쿼리를 해결하기 위해 사용하는 측정값의 이름을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-146">Stores the names of measures used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="647ee-147">이 속성이 비어 있으면 멤버가 비어 있는지 확인하기 위해 계산 멤버가 반복적으로 평가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-147">If this property is blank, the calculated member must be evaluated repeatedly to determine whether a member is empty.</span></span> <span data-ttu-id="647ee-148">그러나 이 속성에 하나 이상의 측정값 이름이 있으면 지정된 측정값이 모두 비어 있는 경우 계산 멤버가 비어 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-148">If this property contains the name of one or more measures, the calculated member is treated as empty if all the specified measures are empty.</span></span> <span data-ttu-id="647ee-149">이 속성은 NULL이 아닌 레코드만 반환하는 Analysis Services에 대한 최적화 힌트입니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-149">This property is an optimization hint to Analysis Services to return only non-NULL records.</span></span> <span data-ttu-id="647ee-150">NULL이 아닌 레코드만 반환하면 NON EMPTY 연산자 또는 NonEmpty 함수를 사용하거나 셀 값을 계산해야 하는 MDX 쿼리의 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-150">Returning only non-NULL records improves the performance of MDX queries that utilize the NON EMPTY operator or the NonEmpty function, or that require the calculation of cell values.</span></span> <span data-ttu-id="647ee-151">최상의 셀 계산 성능을 얻으려면 가능한 경우 멤버를 하나만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-151">For best performance with cell calculations, specify only a single member when possible.</span></span>  
  
 <span data-ttu-id="647ee-152">색 식</span><span class="sxs-lookup"><span data-stu-id="647ee-152">Color Expressions</span></span>  
 <span data-ttu-id="647ee-153">계산 멤버의 값을 기반으로 셀의 전경색 및 배경색을 동적으로 설정하는 MDX 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-153">Specifies MDX expressions that dynamically set the foreground and background colors of cells based on the value of the calculated member.</span></span> <span data-ttu-id="647ee-154">이 속성은 클라이언트 애플리케이션에서 지원하지 않으면 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-154">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="647ee-155">글꼴 식</span><span class="sxs-lookup"><span data-stu-id="647ee-155">Font Expressions</span></span>  
 <span data-ttu-id="647ee-156">계산 멤버의 값을 기반으로 셀의 글꼴, 글꼴 크기 및 글꼴 특성을 동적으로 설정하는 MDX 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-156">Specifies MDX expressions that dynamically set the font, font size, and font attributes for cells based on the value of the calculated member.</span></span> <span data-ttu-id="647ee-157">이 속성은 클라이언트 애플리케이션에서 지원하지 않으면 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-157">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="647ee-158">**계산 도구** 창의 **메타데이터** 탭에서 계산 식 창의 **식** 상자로 큐브 구성 요소를 복사하거나 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-158">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span> <span data-ttu-id="647ee-159">**계산 도구** 창의 **함수** 탭에서 계산 식 창의 **식** 상자로 함수를 복사하거나 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-159">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span>  
  
## <a name="addressing-calculated-members"></a><span data-ttu-id="647ee-160">계산 멤버 접근성</span><span class="sxs-lookup"><span data-stu-id="647ee-160">Addressing Calculated Members</span></span>  
 <span data-ttu-id="647ee-161">**큐브 디자이너** 의 **계산**탭에서 계산 멤버를 만들 때 계산 멤버가 저장된 부모 계층을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-161">When you create a calculated member on the **Calculations** tab of **Cube Designer**, you specify the parent hierarchy in which the calculated member is stored.</span></span> <span data-ttu-id="647ee-162">다음 규칙에 따라 부모 계층은 계산 멤버에 접근하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-162">The parent hierarchy determines how a calculated member can be addressed, according to the following rules:</span></span>  
  
-   <span data-ttu-id="647ee-163">계산 멤버가 측정값 차원에서 생성되는 경우 해당 차원에서 계산 멤버에 접근할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="647ee-163">If a calculated member is created in the measures dimension, the calculated member is addressable in that dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647ee-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="647ee-164">See Also</span></span>  
 [<span data-ttu-id="647ee-165">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="647ee-165">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
