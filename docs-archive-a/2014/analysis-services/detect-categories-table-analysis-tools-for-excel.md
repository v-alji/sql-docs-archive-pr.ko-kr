---
title: 범주 검색 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4874c85d7e4ab65716741e8ae9433406dfb08b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737180"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a><span data-ttu-id="ec186-102">범주 검색(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="ec186-102">Detect Categories (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="ec186-103">![리본의 범주 검색 단추](media/tat-detectcat.gif "리본의 범주 검색 단추")</span><span class="sxs-lookup"><span data-stu-id="ec186-103">![Detect Categories button in ribbon](media/tat-detectcat.gif "Detect Categories button in ribbon")</span></span>

 <span data-ttu-id="ec186-104">**범주 검색** 도구는 유사한 특징이 있는 테이블의 행을 자동으로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-104">The **Detect Categories** tool automatically finds rows in a table that have similar characteristics.</span></span>

 <span data-ttu-id="ec186-105">도구를 완료하면 검색한 범주 및 구별되는 특성을 함께 나열한 보고서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-105">When the tool finishes, it creates a report that lists the categories it found, together with their distinguishing characteristics.</span></span> <span data-ttu-id="ec186-106">기본적으로 도구는 각 데이터 행에 대해 제안된 범주가 포함된 데이터 테이블에 새 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-106">By default, it adds a new column to the data table that contains the proposed category for each row of your data.</span></span> <span data-ttu-id="ec186-107">사용자는 범주를 검토하고 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-107">You can then review the categories and rename them.</span></span>

## <a name="using-the-detect-categories-tool"></a><span data-ttu-id="ec186-108">범주 검색 도구 사용</span><span class="sxs-lookup"><span data-stu-id="ec186-108">Using the Detect Categories Tool</span></span>

1.  <span data-ttu-id="ec186-109">Excel 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-109">Open an Excel table.</span></span>

2.  <span data-ttu-id="ec186-110">**범주 검색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-110">Click **Detect Categories**.</span></span>

3.  <span data-ttu-id="ec186-111">분석에 사용할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-111">Specify the columns to use in analysis.</span></span> <span data-ttu-id="ec186-112">개인 이름이나 레코드 ID와 같은 고유 값을 포함한 열은 분석에 유용하지 않을 수 있으므로 선택을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-112">You can deselect columns that have distinct values, such as personal names or record IDs, because these columns might not be useful for analysis.</span></span>

4.  <span data-ttu-id="ec186-113">필요에 따라 생성할 범주의 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-113">Optionally, specify the maximum number of categories to create.</span></span> <span data-ttu-id="ec186-114">기본적으로 도구는 자동으로 검색한 수만큼 범주를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-114">By default, the tool automatically creates as many categories as it finds.</span></span>

5.  <span data-ttu-id="ec186-115">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-115">Click **Run**.</span></span>

6.  <span data-ttu-id="ec186-116">이 도구는 범주 보고서로 명명된 범주 목록과 특성을 포함하는 새 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-116">The tool creates a new worksheet, named Categories Report, which contains the list of categories and their characteristics.</span></span>

 <span data-ttu-id="ec186-117">도구에 대 한 옵션을 지정 하는 방법에 대 한 자세한 내용은 [범주 검색 대화 상자 (Excel 용 테이블 분석 도구)](detect-categories-table-analysis-tools-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec186-117">For more information about how to specify options for the tool, see [Detect Categories Dialog Box (Table Analysis Tools for Excel)](detect-categories-table-analysis-tools-for-excel.md).</span></span>

## <a name="understanding-the-categories-report"></a><span data-ttu-id="ec186-118">범주 보고서 이해</span><span class="sxs-lookup"><span data-stu-id="ec186-118">Understanding the Categories Report</span></span>
 <span data-ttu-id="ec186-119">범주 **보고서** 에는 **범주 목록과** 범주 **특성**, **범주 프로필** 차트 등 두 개의 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-119">The **Categories Report** contains two tables, **Category List** and **Category Characteristics**, and a **Category Profiles** chart.</span></span>

### <a name="category-list"></a><span data-ttu-id="ec186-120">범주 목록</span><span class="sxs-lookup"><span data-stu-id="ec186-120">Category List</span></span>
 <span data-ttu-id="ec186-121">첫 번째 테이블에는 발견된 범주가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-121">The first table lists the categories that were found.</span></span> <span data-ttu-id="ec186-122">**행 개수** 열은 각 범주에 할당 된 데이터 행 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-122">The **Row Count** column indicates how many rows of data were assigned to each category.</span></span>

 <span data-ttu-id="ec186-123">모델은 각 범주에 대 한 임시 이름을 만들지만 원하는 대로 범주의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-123">The model creates temporary names for each category, but you can rename the categories as you like.</span></span> <span data-ttu-id="ec186-124">예를 들어 다음 예제에서 첫 번째 범주의 이름은 클러스터의 최상위 특성 이므로 **낮은 소득**으로 이름이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-124">For example, in the following example, the first category has been renamed **Low Income**, because that was the top attribute of the cluster.</span></span>

 <span data-ttu-id="ec186-125">![범주 검색 도구로 만든 보고서](media/dm13-tat-detectcat-report1.gif "범주 검색 도구로 만든 보고서")</span><span class="sxs-lookup"><span data-stu-id="ec186-125">![report created by Detect Categories tool](media/dm13-tat-detectcat-report1.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="ec186-126">새 레이블을 입력하자마자 변경된 레이블이 다른 모든 차트와 원본 데이터 워크시트에서 추가된 범주 목록으로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-126">As soon as you type the new label, the change is propagated to all the other charts as well as to the category list added in the source data worksheet.</span></span>

### <a name="category-characteristics"></a><span data-ttu-id="ec186-127">범주 특징</span><span class="sxs-lookup"><span data-stu-id="ec186-127">Category Characteristics</span></span>
 <span data-ttu-id="ec186-128">두 번째 테이블인 **범주 특징**은 각 범주의 구성을 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-128">The second table, **Category Characteristics**, shows details about the makeup of each category.</span></span> <span data-ttu-id="ec186-129">**범주** 열의 맨 위에 있는 **필터** 단추를 클릭 하 여 하나 이상의 범주에 대 한 포커스를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-129">Click the **Filter** button at the top of the **Category** column to see focus on one or just a few categories.</span></span>

 <span data-ttu-id="ec186-130">![범주 검색 도구로 만든 보고서](media/dm13-tat-detectcat-report2.gif "범주 검색 도구로 만든 보고서")</span><span class="sxs-lookup"><span data-stu-id="ec186-130">![report created by Detect Categories tool](media/dm13-tat-detectcat-report2.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="ec186-131">**상대적 중요도**열의 음영은 특성 및 값의 조합이 구별 되는 요소와 얼마나 중요 한지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-131">The shading in the column, **Relative Importance**, indicates how important that combination of attribute and value is as a distinguishing factor.</span></span> <span data-ttu-id="ec186-132">표시줄이 길수록 이 특성이 이 범주를 대표할 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-132">The longer the bar, the more likely it is that this attribute is strongly representative of this category.</span></span>

### <a name="categories-profile-chart"></a><span data-ttu-id="ec186-133">범주 프로필 차트</span><span class="sxs-lookup"><span data-stu-id="ec186-133">Categories Profile Chart</span></span>
 <span data-ttu-id="ec186-134">**범주 보고서** 워크시트의 최종 차트 **범주 프로필**은 필드를 다시 정렬 하 고 숨기고 값을 필터링 하 고 차트의 모양을 사용자 지정 하는 데 사용할 수 있는 대화형 **피벗 차트** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-134">The final chart in the **Categories Report** worksheet, **Category Profiles**, is an interactive **Pivot Chart** that you can use to rearrange and hide fields, filter on values, and customize the chart's appearance.</span></span>

 <span data-ttu-id="ec186-135">이제 Excel 2013은 디자인 화면에서 바로 차트 **스타일** 및 차트 **요소** 컨트롤을 제공 하 여 차트 디자인을 쉽게 개선할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-135">Excel 2013 now provides **Chart Styles** and **Chart Elements** controls right in the design surface that make it easy to improve the chart design.</span></span>

 <span data-ttu-id="ec186-136">![범주 검색 도구로 만든 보고서](media/dm13-tat-detectcat-report3.gif "범주 검색 도구로 만든 보고서")</span><span class="sxs-lookup"><span data-stu-id="ec186-136">![report created by Detect Categories tool](media/dm13-tat-detectcat-report3.gif "report created by Detect Categories tool")</span></span>

## <a name="requirements"></a><span data-ttu-id="ec186-137">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ec186-137">Requirements</span></span>
 <span data-ttu-id="ec186-138">**범주 검색** 도구에는 데이터 양 또는 형식에 대 한 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-138">The **Detect Categories** tool has no requirements for the amount or type of data.</span></span>

> [!NOTE]
>  <span data-ttu-id="ec186-139">**범주 검색** 도구를 사용 하면 원래 데이터 테이블에 새 열인 Category가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-139">When you use the **Detect Categories** tool, it creates a new column, Category, in the original data table.</span></span> <span data-ttu-id="ec186-140">이 열을 데이터 테이블에 남겨두고 후속 데이터 마이닝 작업을 수행할 경우 이 열이 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-140">If you leave this column in the data table and then perform subsequent data mining operations, the presence of this column could influence your results.</span></span> <span data-ttu-id="ec186-141">이 열이 다른 작업에 영향을 주지 않도록 하려면 다른 데이터 마이닝 도구를 사용하기 전에 범주 열이 없는 데이터 테이블의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-141">To ensure that this does not affect other operations, you should make a copy of the data table without the Category column before using other data mining tools.</span></span>

## <a name="related-tools"></a><span data-ttu-id="ec186-142">관련 도구</span><span class="sxs-lookup"><span data-stu-id="ec186-142">Related Tools</span></span>
 <span data-ttu-id="ec186-143">**범주 검색** 도구는 데이터를 분석 하는 경우 클러스터링 알고리즘을 사용 하 여 데이터 마이닝 구조 및 데이터 마이닝 모델을 만듭니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ec186-143">When the **Detect Categories** tool analyzes your data, it creates a data mining structure and data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>

 <span data-ttu-id="ec186-144">**주요 영향 요인 분석** 도구를 사용 하 여 데이터 마이닝 모델을 만든 후 Excel 용 데이터 마이닝 클라이언트를 사용 하 여 모델을 찾아보고 관계를 보다 자세히 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-144">After you have created a data mining model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client for Excel to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="ec186-145">Excel용 데이터 마이닝 클라이언트는 고급 데이터 마이닝 기능을 제공하는 별도의 추가 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="ec186-145">The Data Mining Client for Excel is a separate add-in that provides more advanced data mining functionality.</span></span> <span data-ttu-id="ec186-146">자세한 내용은 [Excel에서 모델 찾아보기 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec186-146">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>

 <span data-ttu-id="ec186-147">Excel 용 데이터 마이닝 클라이언트에서 데이터 모델링 기능을 사용 하는 방법에 대 한 자세한 내용은 [데이터 마이닝 모델 만들기](creating-a-data-mining-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec186-147">For more information about using the data modeling capabilities in the Data Mining Client for Excel, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="ec186-148">**범주 검색** 도구에서 사용 하는 알고리즘에 대 한 자세한 내용은 온라인 설명서의 "Microsoft 클러스터링 알고리즘" 항목을 참조 하십시오 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ec186-148">For more information about the algorithm used by the **Detect Categories** tool, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec186-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec186-149">See Also</span></span>
 [<span data-ttu-id="ec186-150">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="ec186-150">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


