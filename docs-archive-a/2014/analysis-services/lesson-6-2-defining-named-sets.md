---
title: 명명 된 집합 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 47254fd3-525f-4c35-b93d-316607652517
author: minewiskan
ms.author: owend
ms.openlocfilehash: e02f4624dc0ec25ee0c3d8950c83550ca3d9ed57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649783"
---
# <a name="defining-named-sets"></a><span data-ttu-id="b64dc-102">명명된 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b64dc-102">Defining Named Sets</span></span>
  <span data-ttu-id="b64dc-103">명명된 집합은 차원 멤버 집합을 반환하는 MDX(Multidimensional Expressions) 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-103">A named set is a Multidimensional Expressions (MDX) expression that returns a set of dimension members.</span></span> <span data-ttu-id="b64dc-104">명명된 집합을 정의한 후 큐브 정의의 일부로 저장할 수 있습니다. 또한 클라이언트 애플리케이션에서도 명명된 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-104">You can define named sets and save them as part of the cube definition; you can also create named sets in client applications.</span></span> <span data-ttu-id="b64dc-105">큐브 데이터, 산술 연산자, 숫자 및 함수를 조합하여 명명된 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-105">You create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="b64dc-106">명명된 집합을 클라이언트 애플리케이션의 MDX 쿼리에서 사용할 수 있으며 하위 큐브의 집합을 정의하는 데도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-106">Named sets can be used by users in MDX queries in client applications and can also be used to define sets in subcubes.</span></span> <span data-ttu-id="b64dc-107">하위 큐브는 큐브 공간을 후속 문에 대해 정의된 하위 공간으로 제한하는 크로스 조인된 집합 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-107">A subcube is a collection of crossjoined sets that restricts the cube space to the defined subspace for subsequent statements.</span></span> <span data-ttu-id="b64dc-108">제한된 큐브 공간을 정의하는 것은 MDX 스크립팅에 대한 기본 개념에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-108">Defining a restricted cube space is a fundamental concept to MDX scripting.</span></span>

 <span data-ttu-id="b64dc-109">명명된 집합은 MDX 쿼리를 단순화하며 일반적으로 사용되는 복합 집합 식에 대한 유용한 별칭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-109">Named sets simplify MDX queries and provide useful aliases for complex, typically used, set expressions.</span></span> <span data-ttu-id="b64dc-110">예를 들어 가장 많은 직원이 포함된 멤버 집합이 들어 있는 대형 대리점이라는 명명된 집합을 대리점 차원에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-110">For example, you can define a named set called Large Resellers that contains the set of members in the Reseller dimension that have the most employees.</span></span> <span data-ttu-id="b64dc-111">그러면 최종 사용자가 쿼리에서 대형 대리점의 명명된 집합을 사용하거나, 이 명명된 집합을 사용하여 하위 큐브의 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-111">End users could then use the Large Resellers named set in queries, or you could use the named set to define a set in a subcube.</span></span> <span data-ttu-id="b64dc-112">명명된 집합 정의는 큐브 에저장되지만, 값은 메모리에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-112">Named set definitions are stored in cubes, but their values exist only in memory.</span></span> <span data-ttu-id="b64dc-113">명명된 집합을 만들려면 큐브 디자이너의 **계산** 탭에 있는 **새 명명된 집합** 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-113">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="b64dc-114">자세한 내용은 [계산](multidimensional-models-olap-logical-cube-objects/calculations.md), [명명된 집합 만들기](multidimensional-models/create-named-sets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b64dc-114">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Create Named Sets](multidimensional-models/create-named-sets.md).</span></span>

 <span data-ttu-id="b64dc-115">이 항목의 태스크에서는 핵심 제품 명명된 집합과 대형 대리점 명명된 집합 등 두 개의 명명된 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-115">In the tasks in this topic, you will define two named sets: a Core Products named set and a Large Resellers named set.</span></span>

## <a name="defining-a-core-products-named-set"></a><span data-ttu-id="b64dc-116">Core Products 명명된 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b64dc-116">Defining a Core Products Named Set</span></span>

1.  <span data-ttu-id="b64dc-117">**Tutorial 큐브에 대한 큐브 디자이너의** 계산 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭으로 전환한 후 도구 모음에서 **폼 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-117">Switch to the **Calculations** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Form View** on the toolbar.</span></span>

2.  <span data-ttu-id="b64dc-118">**스크립트 구성 도우미** 창에서 **[Total Sales Ratio to All Products]** 를 클릭한 후 **계산** 탭의 도구 모음에서 **새 명명된 집합** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-118">Click **[Total Sales Ratio to All Products]** in the **Script Organizer** pane, and then click **New Named Set** on the toolbar of the **Calculations** tab.</span></span>

     <span data-ttu-id="b64dc-119">**계산** 탭에서 새 계산을 정의할 때 계산은 **스크립트 구성 도우미** 창에 나타나는 순서대로 수행된다는 사실에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="b64dc-119">When you define a new calculation on the **Calculations** tab, remember that calculations are resolved in the order in which they appear in the **Script Organizer** pane.</span></span> <span data-ttu-id="b64dc-120">새 계산을 만들 때 해당 창 내의 포커스에 따라 계산 실행 순서가 결정됩니다. 즉, 새로운 계산은 포커스된 계산 바로 다음에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-120">Your focus within that pane when you create a new calculation determines the order of the execution of the calculation; a new calculation is defined immediately after the calculation on which you are focused.</span></span>

3.  <span data-ttu-id="b64dc-121">**이름** 상자에서 새 명명 된 집합의 이름을로 변경 합니다 `[Core Products]` .</span><span class="sxs-lookup"><span data-stu-id="b64dc-121">In the **Name** box, change the name of the new named set to `[Core Products]`.</span></span>

     <span data-ttu-id="b64dc-122">**스크립트 구성 도우미** 창에는 스크립트 명령이나 계산 멤버에서 명명된 집합을 구분할 수 있는 고유 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-122">In the **Script Organizer** pane, notice the unique icon that differentiates a named set from a script command or a calculated member.</span></span>

4.  <span data-ttu-id="b64dc-123">**계산 도구** 창의 **메타 데이터** 탭에서 **Product**, **Category**,를 차례로 확장 한 `Members` 다음 **All Products**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-123">On the **Metadata** tab in the **Calculation Tools** pane, expand **Product**, expand **Category**, expand `Members`, and then expand **All Products**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b64dc-124">**계산 도구** 창에 메타데이터가 표시되지 않으면 도구 모음에서 **다시 연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-124">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="b64dc-125">이 옵션을 사용할 수 없으면 큐브를 처리하거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 시작해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-125">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

5.  <span data-ttu-id="b64dc-126">**Bikes** 를 **식** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-126">Drag **Bikes** into the **Expression** box.</span></span>

     <span data-ttu-id="b64dc-127">이제 Product 차원의 Bike 범주에 있는 멤버 집합을 반환하는 집합 식이 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-127">You now have created a set expression that will return the set of members that are in the Bike category in the Product dimension.</span></span>

## <a name="defining-a-large-resellers-named-set"></a><span data-ttu-id="b64dc-128">Large Resellers 명명된 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b64dc-128">Defining a Large Resellers Named Set</span></span>

1.  <span data-ttu-id="b64dc-129">`[Core Products]` **스크립트 구성 도우미** 창을 마우스 오른쪽 단추로 클릭 한 다음 **새 명명 된 집합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-129">Right-click `[Core Products]` in the **Script Organizer** pane, and then click **New Named Set**.</span></span>

2.  <span data-ttu-id="b64dc-130">**이름** 상자에서이 명명 된 집합의 이름을로 변경 `[Large Resellers]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-130">In the **Name** box, change the name of this named set to `[Large Resellers]`.</span></span>

3.  <span data-ttu-id="b64dc-131">**식** 상자에를 입력 `Exists()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-131">In the **Expression** box, type `Exists()`.</span></span>

     <span data-ttu-id="b64dc-132">Exists 함수를 사용하여 직원 수 특성 계층에서 직원 수가 가장 많은 멤버 집합과 공통되는 Reseller Name 특성 계층의 멤버 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-132">You will use the Exists function to return the set of members from the Reseller Name attribute hierarchy that intersects with the set of members in the Number of Employees attribute hierarchy that has the largest number of employees.</span></span>

4.  <span data-ttu-id="b64dc-133">**계산 도구** 창의 **메타데이터** 탭에서 **Reseller** 차원을 확장한 후 **Reseller Name** 특성 계층을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-133">On the **Metadata** tab in the **Calculation Tools** pane, expand the **Reseller** dimension, and then expand the **Reseller Name** attribute hierarchy.</span></span>

5.  <span data-ttu-id="b64dc-134">**Reseller Name** 수준을 Exists 집합 식에 대한 괄호 안으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-134">Drag the **Reseller Name** level into the parenthesis for the Exists set expression.</span></span>

     <span data-ttu-id="b64dc-135">Members 함수를 사용하여 이 집합의 모든 멤버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-135">You will use the Members function to return all members of this set.</span></span> <span data-ttu-id="b64dc-136">자세한 내용은 [Members&#40;Set&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b64dc-136">For more information, see [Members &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx).</span></span>

6.  <span data-ttu-id="b64dc-137">부분 집합 식 다음에 마침표를 입력한 후 Members 함수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-137">After the partial set expression, type a period, and then add the Members function.</span></span> <span data-ttu-id="b64dc-138">식은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-138">Your expression should look like the following:</span></span>

    ```
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)
    ```

     <span data-ttu-id="b64dc-139">이제 Exists 집합 식에 대 한 첫 번째 집합을 정의 했으므로 직원 수가 가장 많은 대리점 차원의 멤버 집합을 추가할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-139">Now that you have defined the first set for the Exists set expression, you are ready to add the second set-the set of members of the Reseller dimension that contains the largest number of employees.</span></span>

7.  <span data-ttu-id="b64dc-140">**계산 도구** 창의 **메타 데이터** 탭에서 재판매인 차원의 **직원 수** 를 확장 하 `Members` 고를 확장 한 다음 **모든 대리점**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the Reseller dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="b64dc-141">이 특성 계층의 멤버는 그룹화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-141">Notice that the members of this attribute hierarchy are not grouped.</span></span>

8.  <span data-ttu-id="b64dc-142">**Reseller** 차원에 대한 차원 디자이너를 열고 **특성** 창에서 **Number of Employees** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-142">Open Dimension Designer for the **Reseller** dimension, and then click **Number of Employees** in the **Attributes** pane.</span></span>

9. <span data-ttu-id="b64dc-143">속성 창에서 속성을 자동으로 변경 하 `DiscretizationMethod` 고 속성을로 변경 **Automatic** `DiscretizationBucketCount` `5` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-143">In the Properties window, change the `DiscretizationMethod` property to **Automatic**, and then change the `DiscretizationBucketCount` property to `5`.</span></span> <span data-ttu-id="b64dc-144">자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b64dc-144">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>

10. <span data-ttu-id="b64dc-145">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-145">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

11. <span data-ttu-id="b64dc-146">배포가 성공적으로 완료되면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 후 **계산** 탭의 도구 모음에서 **다시 연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-146">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Calculations** tab.</span></span>

12. <span data-ttu-id="b64dc-147">**계산 도구** 창의 **메타 데이터** 탭에서 **재판매인** 차원의 **직원 수** 를 확장 하 `Members` 고를 확장 한 다음 **모든 대리점**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-147">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the **Reseller** dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="b64dc-148">이제 이 특성 계층의 멤버는 0번부터 4번까지의 5개 그룹에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-148">Notice that the members of this attribute hierarchy are now contained in five groups, numbered 0 through 4.</span></span> <span data-ttu-id="b64dc-149">그룹 번호를 확인하려면 해당 그룹 위에 포인터를 잠시 올려놓고 정보 팁을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-149">To view the number of a group, pause the pointer over that group to view an InfoTip.</span></span> <span data-ttu-id="b64dc-150">`2 -17`범위의 정보 팁에는 `[Reseller].[Number of Employees].&[0]`가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-150">For the range `2 -17`, the InfoTip should contain `[Reseller].[Number of Employees].&[0]`.</span></span>

     <span data-ttu-id="b64dc-151">DiscretizationBucketCount 속성이로 설정 되 `5` 고 DiscretizationMethod 속성이 **Automatic**으로 설정 되어 있으므로이 특성 계층의 멤버는 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-151">The members of this attribute hierarchy are grouped because the DiscretizationBucketCount property is set to `5` and the DiscretizationMethod property is set to **Automatic**.</span></span>

13. <span data-ttu-id="b64dc-152">**식** 상자의 Exists 집합 식에서 Members 함수 뒤, 닫는 괄호 앞에 쉼표를 추가한 후 **메타데이터** 창에서 **83 - 100** 을 끌어다 쉼표 뒤에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-152">In the **Expression** box, add a comma in the Exists set expression after the Members function and before the closing parenthesis, and then drag **83 - 100** from the **Metadata** pane and position it after the comma.</span></span>

     <span data-ttu-id="b64dc-153">이제 Large Resellers 명명된 집합을 축 위에 놓았을 때 지정된 두 집합, 즉 모든 대리점의 집합 및 직원 수가 83명에서 100명 사이인 대리점의 집합과 공통되는 멤버 집합을 반환하는 Exists 집합 식이 완성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-153">You have now completed the Exists set expression that will return the set of members that intersects with these two specified sets, the set of all resellers and the set of resellers who have 83 to 100 employees, when the Large Resellers named set is put on an axis.</span></span>

     <span data-ttu-id="b64dc-154">다음 그림에서는 명명 된 집합에 대 한 **계산 식** 창을 보여 줍니다 `[Large Resellers]` .</span><span class="sxs-lookup"><span data-stu-id="b64dc-154">The following image shows the **Calculation Expressions** pane for the `[Large Resellers]` named set.</span></span>

     <span data-ttu-id="b64dc-155">![[대형 대리점]에 대한 계산 식 창](../../2014/tutorials/media/l6-named-set-02.gif "[대형 대리점]에 대한 계산 식 창")</span><span class="sxs-lookup"><span data-stu-id="b64dc-155">![Calculation Expressions pane for [Large Resellers]](../../2014/tutorials/media/l6-named-set-02.gif "Calculation Expressions pane for [Large Resellers]")</span></span>

14. <span data-ttu-id="b64dc-156">**계산** 탭의 도구 모음에서 **스크립트 보기**를 클릭하고 계산 스크립트에 방금 추가한 두 개의 명명된 집합을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-156">On the toolbar of the **Calculations** tab, click **Script View**, and then review the two named sets that you have just added to the calculation script.</span></span>

15. <span data-ttu-id="b64dc-157">계산 스크립트에서 첫 번째 CREATE SET 명령 바로 앞에 새 줄을 추가한 후 다음 텍스트를 별도의 줄로 스크립트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-157">Add a new line in the calculation script immediately before the first CREATE SET command, and then add the following text to the script on its own line:</span></span>

    ```
    /* named sets */
    ```

     <span data-ttu-id="b64dc-158">두 개의 명명된 집합이 정의되었으며 이러한 명명된 집합은 **스크립트 구성 도우미** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-158">You have now defined two named sets, which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="b64dc-159">이제 이러한 명명된 집합을 배포한 후 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에서 해당 측정값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-159">You are now ready to deploy these named sets, and then to browse these measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

## <a name="browsing-the-cube-by-using-the-new-named-sets"></a><span data-ttu-id="b64dc-160">새 명명된 집합을 사용하여 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="b64dc-160">Browsing the Cube by Using the New Named Sets</span></span>

1.  <span data-ttu-id="b64dc-161">**의** 빌드 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-161">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="b64dc-162">배포가 성공적으로 완료되면 **브라우저** 탭을 클릭한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-162">When deployment has successfully completed, click the **Browser** tab, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="b64dc-163">데이터 창에서 표를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-163">Clear the grid in the data pane.</span></span>

4.  <span data-ttu-id="b64dc-164">데이터 영역에 **Reseller Sales-Sales Amount** 측정값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-164">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

5.  <span data-ttu-id="b64dc-165">다음 그림에 표시된 것처럼 Product 차원을 확장한 다음 Category 및 Subcategory를 행 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-165">Expand the Product dimension, and then add Category and Subcategory to the row area, as shown in the following image.</span></span>

     <span data-ttu-id="b64dc-166">![하위 범주 특성의 구성원](../../2014/tutorials/media/l6-named-set-03.gif "하위 범주 특성의 구성원")</span><span class="sxs-lookup"><span data-stu-id="b64dc-166">![Members of the Subcategory attribute](../../2014/tutorials/media/l6-named-set-03.gif "Members of the Subcategory attribute")</span></span>

6.  <span data-ttu-id="b64dc-167">**메타데이터** 창의 **Product** 차원에서 **Core Products** 를 필터 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-167">In the **Metadata** pane, in the **Product** dimension, drag **Core Products** to the filter area.</span></span>

     <span data-ttu-id="b64dc-168">**Category** 특성의 **Bike** 멤버와 **Bike** 하위 범주의 멤버만 큐브에 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-168">Notice that only the **Bike** member of the **Category** attribute and members of the **Bike** subcategories remain in the cube.</span></span> <span data-ttu-id="b64dc-169">**Core Products** 명명된 집합이 하위 큐브를 정의하는 데 사용되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-169">This is because the **Core Products** named set is used to define a subcube.</span></span> <span data-ttu-id="b64dc-170">다음 그림에 표시된 것처럼 이 하위 큐브는 하위 큐브 내의 **Product** 차원에 포함된 **Category** 특성의 멤버를 **Core Product** 명명된 집합의 멤버로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-170">This subcube limits the members of the **Category** attribute in the **Product** dimension within the subcube to those members of the **Core Product** named set, as shown in the following image.</span></span>

     <span data-ttu-id="b64dc-171">![핵심 제품 명명된 집합의 구성원](../../2014/tutorials/media/l6-named-set-04.gif "핵심 제품 명명된 집합의 구성원")</span><span class="sxs-lookup"><span data-stu-id="b64dc-171">![Members of the Core Product named set](../../2014/tutorials/media/l6-named-set-04.gif "Members of the Core Product named set")</span></span>

7.  <span data-ttu-id="b64dc-172">**메타데이터** 창에서 **Reseller**를 확장하고 필터 영역에 **Large Resellers** 를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-172">In the **Metadata** pane, expand **Reseller**, add **Large Resellers** to the filter area.</span></span>

     <span data-ttu-id="b64dc-173">데이터 창의 Reseller Sales Amount 측정값은 자전거를 판매하는 대형 대리점의 판매액만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-173">Notice that the Reseller Sales Amount measure in the Data pane only displays sales amounts for large resellers of bikes.</span></span> <span data-ttu-id="b64dc-174">또한 필터 창에는 다음 그림에 표시된 것처럼 이러한 특정 하위 큐브를 정의하는 데 사용되는 두 개의 명명된 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b64dc-174">Notice also that the Filter pane now displays the two named sets that are used to define this particular subcube, as shown in the following image.</span></span>

     <span data-ttu-id="b64dc-175">![명명된 집합을 2개 포함하는 필터 창](../../2014/tutorials/media/l6-named-set-05.gif "명명된 집합을 2개 포함하는 필터 창")</span><span class="sxs-lookup"><span data-stu-id="b64dc-175">![Filter pane containing two named sets](../../2014/tutorials/media/l6-named-set-05.gif "Filter pane containing two named sets")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="b64dc-176">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="b64dc-176">Next Task in Lesson</span></span>
 [<span data-ttu-id="b64dc-177">7단원: KPI&#40;핵심 성과 지표&#41; 정의</span><span class="sxs-lookup"><span data-stu-id="b64dc-177">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)

## <a name="see-also"></a><span data-ttu-id="b64dc-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b64dc-178">See Also</span></span>
 <span data-ttu-id="b64dc-179">[계산](multidimensional-models-olap-logical-cube-objects/calculations.md) 에서는 [명명 된 집합을 만듭니다](multidimensional-models/create-named-sets.md) .</span><span class="sxs-lookup"><span data-stu-id="b64dc-179">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) [Create Named Sets](multidimensional-models/create-named-sets.md)</span></span>


