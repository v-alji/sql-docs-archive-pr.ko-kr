---
title: 큐브 뷰 정의 및 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 766004b9-6578-4914-a445-6f44843a5fb0
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9658098180618c2d5d6d6d9e00e7a7e4a6c4231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734548"
---
# <a name="defining-and-browsing-perspectives"></a><span data-ttu-id="bc333-102">큐브 뷰 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="bc333-102">Defining and Browsing Perspectives</span></span>
  <span data-ttu-id="bc333-103">큐브 뷰는 특정 목적을 위해 큐브의 보기를 단순화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-103">A perspective can simplify the view of a cube for specific purposes.</span></span> <span data-ttu-id="bc333-104">기본적으로 사용자들은 사용 권한이 있는 큐브의 모든 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-104">By default, users can see all of the elements in a cube to which they have permissions.</span></span> <span data-ttu-id="bc333-105">사용자가 전체 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브를 볼 때 표시되는 내용은 큐브의 기본 큐브 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-105">What users are viewing when they view an entire [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube is the default perspective for the cube.</span></span> <span data-ttu-id="bc333-106">전체 큐브의 보기는 너무 복잡해서 사용자가 탐색하기 어려울 수 있으며, 비즈니스 인텔리전스 및 보고 요구 사항을 만족시키기 위해 큐브의 일부만 사용하면 되는 사용자에게는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-106">A view of the whole cube can be very complex for users to navigate, especially for users who only need to interact with a small part of the cube to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="bc333-107">큐브의 복잡성을 줄이기 위해 큐브에서 측정값 그룹, 측정값, 차원, 특성, 계층, KPI(핵심 성과 지표), 동작 및 계산 멤버의 부분만 표시하는 *큐브 뷰*라는 표시 가능한 큐브 하위 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-107">To reduce the apparent complexity of a cube, you can create viewable subsets of the cube, called *perspectives*, which show users only a part of the measure groups, measures, dimensions, attributes, hierarchies, Key Performance Indicators (KPIs), actions, and calculated members in the cube.</span></span> <span data-ttu-id="bc333-108">이 방법은 특히 이전 릴리스의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]용으로 작성된 클라이언트 애플리케이션으로 작업할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-108">This can be particularly useful for working with client applications that were written for a previous release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="bc333-109">예를 들어 이러한 클라이언트는 표시 폴더나 큐브 뷰에 대한 개념이 없지만 큐브 뷰는 이전 클라이언트에 큐브인 것처럼 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-109">These clients have no concept of display folders or perspectives, for example, but a perspective appears to older clients as if it were a cube.</span></span> <span data-ttu-id="bc333-110">자세한 내용은 [큐브 뷰](multidimensional-models-olap-logical-cube-objects/perspectives.md)및 [다차원 모델의 큐브 뷰](multidimensional-models/perspectives-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc333-110">For more information, see [Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md), and [Perspectives in Multidimensional Models](multidimensional-models/perspectives-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc333-111">큐브 뷰는 보안 메커니즘이 아닌 작업 효율을 높이기 위한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-111">A perspective is not a security mechanism, but instead is a tool for providing a better user experience.</span></span> <span data-ttu-id="bc333-112">큐브 뷰에 대한 모든 보안은 기본 큐브에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-112">All security for a perspective is inherited from the underlying cube.</span></span>  
  
 <span data-ttu-id="bc333-113">이 항목의 태스크에서는 여러 다른 큐브 뷰를 정의한 후 이러한 각각의 새 큐브 뷰를 통해 큐브를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-113">In the tasks in this topic, you will define several different perspectives and then browse the cube through each of these new perspectives.</span></span>  
  
## <a name="defining-an-internet-sales-perspective"></a><span data-ttu-id="bc333-114">인터넷 판매 큐브 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="bc333-114">Defining an Internet Sales Perspective</span></span>  
  
1.  <span data-ttu-id="bc333-115">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너를 열고 **큐브 뷰** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-115">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Perspectives** tab.</span></span>  
  
     <span data-ttu-id="bc333-116">다음 그림에 표시된 것처럼 모든 개체 및 해당 개체 유형이 **큐브 뷰** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-116">All the objects and their object types appear in the **Perspectives** pane, as shown in the following image.</span></span>  
  
     <span data-ttu-id="bc333-117">![큐브 디자이너의 큐브 뷰 창](../../2014/tutorials/media/l9-perspectives-1.gif "큐브 디자이너의 큐브 뷰 창")</span><span class="sxs-lookup"><span data-stu-id="bc333-117">![Perspectives pane of Cube Designer](../../2014/tutorials/media/l9-perspectives-1.gif "Perspectives pane of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="bc333-118">**큐브 뷰** 탭의 도구 모음에서 **새 큐브 뷰** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-118">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
     <span data-ttu-id="bc333-119">다음 그림에 표시된 것처럼 **큐브 뷰** 의 기본 이름과 함께 새 큐브 뷰가 **큐브 뷰 이름**열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-119">A new perspective appears in the **Perspective Name** column with a default name of **Perspective**, as shown in the following image.</span></span> <span data-ttu-id="bc333-120">개체에 대한 확인란의 선택을 취소할 때까지 모든 개체에 대한 확인란은 선택된 상태를 유지합니다. 이 큐브 뷰는 이 큐브의 기본 큐브 뷰와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-120">Notice that the check box for every object is selected; until you clear the check box for an object, this perspective is identical to the default perspective of this cube.</span></span>  
  
     <span data-ttu-id="bc333-121">![큐브 뷰 이름 열의 새 큐브 뷰](../../2014/tutorials/media/l9-perspectives-2.gif "큐브 뷰 이름 열의 새 큐브 뷰")</span><span class="sxs-lookup"><span data-stu-id="bc333-121">![New perspective in Perspective Name column](../../2014/tutorials/media/l9-perspectives-2.gif "New perspective in Perspective Name column")</span></span>  
  
3.  <span data-ttu-id="bc333-122">큐브 뷰 이름을로 변경 `Internet Sales` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-122">Change the perspective name to `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="bc333-123">다음 행에서 DefaultMeasure를 **Internet Sales-Sales Amount**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-123">On the next row, set the DefaultMeasure to **Internet Sales-Sales Amount**.</span></span>  
  
     <span data-ttu-id="bc333-124">사용자가 이 큐브 뷰를 사용하여 큐브를 찾아볼 때 다른 측정값을 지정하지 않은 경우 이 측정값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-124">When users browse the cube by using this perspective, this will be the measure that the users see unless they specify some other measure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bc333-125">또한 큐브의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브 구조 **탭에 있는 속성 창에서 전체** Tutorial 큐브에 대한 기본 측정값을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-125">You can also set the default measure for the whole [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube in the Properties window on the **Cube Structure** tab for the cube.</span></span>  
  
5.  <span data-ttu-id="bc333-126">다음 개체에 대한 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-126">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="bc333-127">`Reseller Sales`측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-127">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="bc333-128">**Sales Quotas** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-128">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-129">**Sales Quotas 1** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-129">**Sales Quotas 1** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-130">**Reseller** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-130">**Reseller** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-131">**Reseller Geography** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-131">**Reseller Geography** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-132">**Sales Territory** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-132">**Sales Territory** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-133">**Employee** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-133">**Employee** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-134">**Promotion** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-134">**Promotion** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-135">**Reseller Revenue** KPI</span><span class="sxs-lookup"><span data-stu-id="bc333-135">**Reseller Revenue** KPI</span></span>  
  
    -   <span data-ttu-id="bc333-136">**Large Resellers** 명명된 집합</span><span class="sxs-lookup"><span data-stu-id="bc333-136">**Large Resellers** named set</span></span>  
  
    -   <span data-ttu-id="bc333-137">**Total Sales Amount** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-137">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-138">**Total Product Cost** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-138">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-139">**Reseller GPM** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-139">**Reseller GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-140">**Total GPM** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-140">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-141">**Reseller Sales Ratio to All Products** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-141">**Reseller Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-142">**Total Sales Ratio to All Products** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-142">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="bc333-143">이러한 개체는 인터넷 판매와 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-143">These objects do not relate to Internet sales.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bc333-144">각 차원 내에서 큐브 뷰에 표시하려는 사용자 정의 계층 및 특성을 따로 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-144">Within each dimension, you can also individually select the user-defined hierarchies and attributes that you want to appear in a perspective.</span></span>  
  
## <a name="defining-a-reseller-sales-perspective"></a><span data-ttu-id="bc333-145">Reseller Sales 큐브 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="bc333-145">Defining a Reseller Sales Perspective</span></span>  
  
1.  <span data-ttu-id="bc333-146">**큐브 뷰** 탭의 도구 모음에서 **새 큐브 뷰** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-146">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="bc333-147">새 큐브 뷰의 이름을로 변경 `Reseller Sales` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-147">Change the name of the new perspective to `Reseller Sales`.</span></span>  
  
3.  <span data-ttu-id="bc333-148">**Reseller Sales-Sales Amount** 를 기본 측정값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-148">Set **Reseller Sales-Sales Amount** as the default measure.</span></span>  
  
     <span data-ttu-id="bc333-149">사용자가 이 큐브 뷰를 사용하여 큐브를 찾아볼 때 다른 측정값을 지정하지 않은 경우 이 측정값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-149">When users browse the cube by using this perspective, this measure will be the measure that the users will see unless they specify some other measure.</span></span>  
  
4.  <span data-ttu-id="bc333-150">다음 개체에 대한 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-150">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="bc333-151">`Internet Sales`측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-151">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="bc333-152">**Internet Sales Reason** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-152">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-153">**Customer** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-153">**Customer** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-154">**Internet Sales Order Details** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-154">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-155">**Sales Reason** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-155">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-156">**Internet Sales Details Drillthrough Action** 드릴스루 동작</span><span class="sxs-lookup"><span data-stu-id="bc333-156">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
    -   <span data-ttu-id="bc333-157">**Total Sales Amount** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-157">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-158">**Total Product Cost** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-158">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-159">**Internet GPM** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-159">**Internet GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-160">**Total GPM** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-160">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-161">**Internet Sales Ratio to All Products** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-161">**Internet Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="bc333-162">**Total Sales Ratio to All Products** 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="bc333-162">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="bc333-163">이러한 개체는 대리점 판매와 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-163">These objects do not relate to resellers sales.</span></span>  
  
## <a name="defining-a-sales-summary-perspective"></a><span data-ttu-id="bc333-164">판매 요약 큐브 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="bc333-164">Defining a Sales Summary Perspective</span></span>  
  
1.  <span data-ttu-id="bc333-165">**큐브 뷰** 탭의 도구 모음에서 **새 큐브 뷰** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-165">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="bc333-166">새 큐브 뷰의 이름을로 변경 `Sales Summary` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-166">Change the name of the new perspective to `Sales Summary`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bc333-167">계산 측정값은 기본 측정값으로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-167">You cannot specify a calculated measure as the default measure.</span></span>  
  
3.  <span data-ttu-id="bc333-168">다음 개체에 대한 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-168">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="bc333-169">`Internet Sales`측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-169">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="bc333-170">`Reseller Sales`측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-170">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="bc333-171">**Internet Sales Reason** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-171">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-172">**Sales Quotas** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-172">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-173">**Sales Quotas1** 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="bc333-173">**Sales Quotas1** measure group</span></span>  
  
    -   <span data-ttu-id="bc333-174">**Internet Sales Order Details** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-174">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-175">**Sales Reason** 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="bc333-175">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="bc333-176">**Internet Sales Details Drillthrough Action** 드릴스루 동작</span><span class="sxs-lookup"><span data-stu-id="bc333-176">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
4.  <span data-ttu-id="bc333-177">다음 개체에 대한 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-177">Select the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="bc333-178">**Internet Sales Count** 측정값</span><span class="sxs-lookup"><span data-stu-id="bc333-178">**Internet Sales Count** measure</span></span>  
  
    -   <span data-ttu-id="bc333-179">**Reseller Sales Count** 측정값</span><span class="sxs-lookup"><span data-stu-id="bc333-179">**Reseller Sales Count** measure</span></span>  
  
## <a name="browsing-the-cube-through-each-perspective"></a><span data-ttu-id="bc333-180">각 큐브 뷰를 통해 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="bc333-180">Browsing the Cube Through Each Perspective</span></span>  
  
1.  <span data-ttu-id="bc333-181">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-181">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="bc333-182">배포가 성공적으로 완료되면 **브라우저** 탭으로 전환한 다음 **다시 연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-182">When deployment has successfully completed, switch to the **Browser** tab, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="bc333-183">Excel을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-183">Start Excel.</span></span>  
  
4.  <span data-ttu-id="bc333-184">다음 그림에 표시된 것처럼 Excel에서 분석에서 Excel에서 모델을 검색할 때 사용할 큐브 뷰를 선택하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-184">Analyze in Excel prompts you to choose which perspective to use when browsing the model in Excel, as shown in the following image.</span></span>  
  
     <span data-ttu-id="bc333-185">![Internet Sales 큐브 뷰의 개체](../../2014/tutorials/media/l9-perspectives-3.gif "Internet Sales 큐브 뷰의 개체")</span><span class="sxs-lookup"><span data-stu-id="bc333-185">![Objects for the Internet Sales perspective](../../2014/tutorials/media/l9-perspectives-3.gif "Objects for the Internet Sales perspective")</span></span>  
  
5.  <span data-ttu-id="bc333-186">또는 다음 그림에 표시된 것처럼 Windows 시작 메뉴에서 Excel을 시작하고 localhost의 Analysis Services 자습서 데이터베이스에 대한 연결을 정의하고 데이터 연결 마법사에서 큐브 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-186">Alternatively, you can start Excel from the Windows Start menu, define a connection to the Analysis Services Tutorial database on localhost, and choose a perspective in the Data Connection wizard, as shown in the following image.</span></span>  
  
     <span data-ttu-id="bc333-187">![Excel의 데이터 연결 마법사](../../2014/tutorials/media/l9-perspectives-3b.gif "Excel의 데이터 연결 마법사")</span><span class="sxs-lookup"><span data-stu-id="bc333-187">![Data Connection wizard in Excel](../../2014/tutorials/media/l9-perspectives-3b.gif "Data Connection wizard in Excel")</span></span>  
  
6.  <span data-ttu-id="bc333-188">`Internet Sales` **큐브 뷰** 목록에서를 선택한 다음 메타 데이터 창에서 측정값과 차원을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-188">Select `Internet Sales` in the **Perspective** list and then review the measures and dimensions in the metadata pane.</span></span>  
  
     <span data-ttu-id="bc333-189">Internet Sales 큐브 뷰에 대해 지정된 개체만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-189">Notice that only those objects that are specified for the Internet Sales perspective appear.</span></span>  
  
7.  <span data-ttu-id="bc333-190">메타데이터 창에서 **Measures**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-190">In the metadata pane, expand **Measures**.</span></span>  
  
     <span data-ttu-id="bc333-191">`Internet Sales`측정값 그룹만 **internet gpm** 및 **Internet Sales Ratio to All Products** 계산 멤버와 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-191">Notice that only the `Internet Sales` measure group appears, together with the **Internet GPM** and **Internet Sales Ratio to All Products** calculated members.</span></span>  
  
8.  <span data-ttu-id="bc333-192">모델에서 Excel을 다시 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-192">In the model, select Excel again.</span></span> <span data-ttu-id="bc333-193">`Sales Summary`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-193">Select `Sales Summary`.</span></span>  
  
     <span data-ttu-id="bc333-194">다음 그림에 표시된 것처럼 이러한 각 측정값 그룹에서 단일 측정값만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bc333-194">Notice that in each of these measure groups, only a single measure appears, as shown in the following image.</span></span>  
  
     <span data-ttu-id="bc333-195">![Internet Sales 및 Reseller Sales 측정값](../../2014/tutorials/media/l9-perspectives-4.gif "Internet Sales 및 Reseller Sales 측정값")</span><span class="sxs-lookup"><span data-stu-id="bc333-195">![Internet Sales and Reseller Sales measures](../../2014/tutorials/media/l9-perspectives-4.gif "Internet Sales and Reseller Sales measures")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bc333-196">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="bc333-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bc333-197">번역 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="bc333-197">Defining and Browsing Translations</span></span>](lesson-9-2-defining-and-browsing-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc333-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc333-198">See Also</span></span>  
 <span data-ttu-id="bc333-199">[전망을](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span><span class="sxs-lookup"><span data-stu-id="bc333-199">[Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span></span>  
 [<span data-ttu-id="bc333-200">다차원 모델의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="bc333-200">Perspectives in Multidimensional Models</span></span>](multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
