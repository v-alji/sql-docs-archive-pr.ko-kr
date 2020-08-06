---
title: Analysis Services에 대 한 MDX 쿼리 디자이너에서 매개 변수 정의 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b2b05fc0122eb25a7a0799f7b47b1b99486a28c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742888"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a><span data-ttu-id="6f7ac-102">Analysis Services용 MDX 쿼리 디자이너에서 매개 변수 정의(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6f7ac-102">Define Parameters in the MDX Query Designer for Analysis Services (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6f7ac-103">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본에 대한 MDX 쿼리를 매개 변수화하려면 쿼리 매개 변수를 쿼리에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-103">To parameterize an MDX query for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you must add a query parameter to the query.</span></span> <span data-ttu-id="6f7ac-104">MDX 쿼리 디자이너에서 필터를 지정하여 디자인 모드와 쿼리 모드 모두에서 쿼리 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-104">In the MDX query designer, you can add a query parameter in both Design mode and Query mode by specifying a filter.</span></span> <span data-ttu-id="6f7ac-105">쿼리 매개 변수를 사용하여 쿼리를 정의하면 Reporting Services에서 자동으로 보고서 매개 변수 및 데이터 세트를 만들어 올바른 값 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-105">After you define the query with a query parameter, Reporting Services automatically creates a report parameter and a dataset to provide the list of valid values.</span></span> <span data-ttu-id="6f7ac-106">따라서 사용자는 쿼리에 직접 전달되는 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-106">This enables a user to specify a value that is passed directly to the query.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a><span data-ttu-id="6f7ac-107">디자인 모드에서 MDX의 쿼리 매개 변수를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="6f7ac-107">To define a query parameter in MDX in Design mode</span></span>

1.  <span data-ttu-id="6f7ac-108">보고서 데이터 창에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본 유형에서 만든 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음에 **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-108">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="6f7ac-109">MDX 쿼리 디자이너가 디자인 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-109">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="6f7ac-110">차원을 필터 영역으로 끈 다음 **차원** 열의 첫 번째 셀 위에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-110">Drag a dimension to the filter area and drop it on the first cell in the **Dimension** column.</span></span>

3.  <span data-ttu-id="6f7ac-111">**계층** 열의 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-111">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

4.  <span data-ttu-id="6f7ac-112">**연산자** 열의 드롭다운 목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-112">In the **Operator** column, choose an operator for the drop-down list.</span></span>

5.  <span data-ttu-id="6f7ac-113">**필터 식** 열의 드롭다운 목록에서 개별 값을 선택하거나 **모든** 멤버를 클릭하여 모든 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-113">In the **Filter Expression** column, select individual values from the drop-down list, or click the **All** member to choose all values.</span></span>

6.  <span data-ttu-id="6f7ac-114">**매개 변수** 열에서 확인란을 선택하여 보고서 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-114">In the **Parameters** column, select the check box to create a report parameter.</span></span>

7.  <span data-ttu-id="6f7ac-115">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-115">Click **Run**.</span></span>

     <span data-ttu-id="6f7ac-116">쿼리를 실행한 후 도구 모음의 **디자인** 을 클릭하여 쿼리 모드로 전환한 다음 작성된 MDX 쿼리를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-116">After you run the query, click **Design** on the toolbar to toggle to Query mode to view the MDX query that was created.</span></span> <span data-ttu-id="6f7ac-117">계속 디자인 모드를 사용하여 쿼리를 개발하려는 경우 쿼리 모드에서 쿼리 텍스트를 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-117">Do not change the query text in Query mode if you want to continue to use Design mode to develop the query.</span></span> <span data-ttu-id="6f7ac-118">**디자인** 을 클릭하여 디자인 모드로 다시 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-118">Click **Design** to toggle back to Design mode.</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="6f7ac-119">보고서 데이터 창에서 매개 변수 노드를 확장하여 필터에 대해 자동으로 만든 보고서 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-119">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="6f7ac-120">보고서 매개 변수에 대해 사용 가능한 값을 제공하는 데이터 세트를 보려면 보고서 데이터 창의 빈 영역을 마우스 오른쪽 단추로 클릭한 다음, **숨겨진 데이터 세트 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-120">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="6f7ac-121">보고서 데이터 창에 보고서의 모든 데이터 세트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-121">The Report Data pane displays all datasets in the report.</span></span>

### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a><span data-ttu-id="6f7ac-122">쿼리 모드에서 MDX의 쿼리 매개 변수를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="6f7ac-122">To define a query parameter in MDX in Query mode</span></span>

1.  <span data-ttu-id="6f7ac-123">보고서 데이터 창에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본 유형에서 만든 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음에 **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-123">In the Report Data pane, right-click on a dataset created from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source type, and then click **Query**.</span></span> <span data-ttu-id="6f7ac-124">MDX 쿼리 디자이너가 디자인 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-124">The MDX query designer opens in Design mode.</span></span>

2.  <span data-ttu-id="6f7ac-125">도구 모음에서 **디자인** 을 클릭하여 쿼리 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-125">On the toolbar, click **Design** to toggle to Query mode.</span></span>

3.  <span data-ttu-id="6f7ac-126">MDX 쿼리 디자이너 도구 모음에서 **쿼리 매개 변수**(![쿼리 매개 변수 대화 상자의 아이콘](../../analysis-services/media/iconqueryparameter.gif "쿼리 매개 변수 대화 상자 아이콘"))를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-126">On the MDX query designer toolbar, click **Query Parameters** (![Icon for the Query Parameters dialog box](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")).</span></span> <span data-ttu-id="6f7ac-127">쿼리 매개 변수 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-127">The Query Parameters dialog box opens.</span></span>

4.  <span data-ttu-id="6f7ac-128">**매개 변수** 열에서을 클릭 한 **\<Enter Parameter>** 다음 매개 변수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-128">In the **Parameter** column, click **\<Enter Parameter>**, and then type the name of a parameter.</span></span>

5.  <span data-ttu-id="6f7ac-129">**차원** 열의 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-129">In the **Dimension** column, choose a value from the drop-down list.</span></span>

6.  <span data-ttu-id="6f7ac-130">**계층** 열의 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-130">In the **Hierarchy** column, choose a value from the drop-down list.</span></span>

7.  <span data-ttu-id="6f7ac-131">**다중 값** 열에서 확인란을 선택하여 다중 값 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-131">In the **Multiple values** column, select the check box to create a multivalue parameter.</span></span>

8.  <span data-ttu-id="6f7ac-132">5단계에서 선택한 사항에 따라 **기본값** 열의 드롭다운 목록에서 단일 값 또는 다중 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-132">In the **Default** column, from the drop-down list, select a single value or multiple values depending on your choice in step 5.</span></span>

9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

10. <span data-ttu-id="6f7ac-133">쿼리 디자이너 도구 모음에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-133">On the query designer toolbar, click **Run**.</span></span>

11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="6f7ac-134">보고서 데이터 창에서 매개 변수 노드를 확장하여 필터에 대해 자동으로 만든 보고서 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-134">In the Report Data pane, expand the Parameters node to display the report parameter that was automatically created for the filter.</span></span>

     <span data-ttu-id="6f7ac-135">보고서 매개 변수에 대해 사용 가능한 값을 제공하는 데이터 세트를 보려면 보고서 데이터 창의 빈 영역을 마우스 오른쪽 단추로 클릭한 다음, **숨겨진 데이터 세트 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-135">To view the dataset that provides available values for the report parameter, right-click any blank area in the Report Data pane, and then click **Show Hidden Datasets**.</span></span> <span data-ttu-id="6f7ac-136">보고서 데이터 창에 보고서의 모든 데이터 세트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ac-136">The Report Data pane displays all datasets in the report.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f7ac-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f7ac-137">See Also</span></span>
 <span data-ttu-id="6f7ac-138">MDX &#40;SSRS&#41;[ANALYSIS SERVICES Mdx 쿼리 디자이너 사용자 인터페이스](analysis-services-mdx-query-designer-user-interface.md) [에 대 한 Analysis Services 연결 유형](analysis-services-connection-type-for-mdx-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="6f7ac-138">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)</span></span>


