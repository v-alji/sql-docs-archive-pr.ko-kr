---
title: 측정값 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649206"
---
# <a name="create-and-manage-measures-ssas-tabular"></a><span data-ttu-id="bc357-102">측정값 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="bc357-102">Create and Manage Measures (SSAS Tabular)</span></span>
  <span data-ttu-id="bc357-103">측정값은 보고서나 Excel 피벗 테이블 또는 피벗 차트에 사용하기 위해 만드는 수식입니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-103">A measure is a formula that is created for use in a report or Excel PivotTable (or PivotChart).</span></span> <span data-ttu-id="bc357-104">COUNT 또는 SUM과 같은 표준 집계 함수를 기반으로 측정값을 만들거나 DAX를 사용하여 고유한 수식을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-104">Measures can be based on standard aggregation functions, such as COUNT or SUM, or you can define your own formula by using DAX.</span></span> <span data-ttu-id="bc357-105">이 항목의 태스크에서는 테이블의 측정값 표를 사용 하 여 측정값을 만들고 관리 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-105">The tasks in this topic describe how to create and manage measures by using a table's measure grid.</span></span>  
  
 <span data-ttu-id="bc357-106">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-106">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="bc357-107">표준 집계 수식을 사용하여 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bc357-107">To create a measure using a standard aggregation formula</span></span>](#bkmk_create_stand)  
  
-   [<span data-ttu-id="bc357-108">사용자 지정 수식을 사용 하 여 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bc357-108">To create a measure using a custom formula</span></span>](#bkmk_create_custom)  
  
-   [<span data-ttu-id="bc357-109">측정값을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="bc357-109">To edit measure properties</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="bc357-110">측정값의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="bc357-110">To rename a measure</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="bc357-111">측정값을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="bc357-111">To delete a measure</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="bc357-112">작업</span><span class="sxs-lookup"><span data-stu-id="bc357-112">Tasks</span></span>  
 <span data-ttu-id="bc357-113">측정값을 만들고 관리 하려면 테이블의 측정값 표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-113">To create and manage measures, you will use a table's measure grid.</span></span> <span data-ttu-id="bc357-114">모델 디자이너의 데이터 뷰에서만 테이블에 대한 측정값 표를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-114">You can view the measure grid for a table in the model designer in Data View only.</span></span> <span data-ttu-id="bc357-115">다이어그램 뷰에서는 측정값을 만들거나 측정값 표를 볼 수 없지만 기존 측정값을 볼 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-115">You cannot create measures or view the measure grid when in Diagram View; however, you can view existing measures in Diagram View.</span></span> <span data-ttu-id="bc357-116">테이블의 측정값 표를 보려면 **테이블** 메뉴를 클릭한 다음 **측정값 표 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-116">To show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a><span data-ttu-id="bc357-117">표준 집계 수식을 사용 하 여 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bc357-117">To create a measure using a standard aggregation formula</span></span>  
  
-   <span data-ttu-id="bc357-118">측정값을 만들 열을 클릭한 후 **열** 메뉴를 클릭하고 **자동 합계**를 가리킨 다음 집계 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-118">Click on the column for which you want to create the measure, then click the **Column** menu, then point to **AutoSum**, and then click an aggregation type.</span></span>  
  
     <span data-ttu-id="bc357-119">기본 이름 뒤에 측정값 표의 해당 열 바로 아래에 있는 첫 번째 셀의 수식이 추가되어 측정값이 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-119">The measure will be created automatically with a default name, followed by the formula in the first cell in the measure grid directly beneath the column.</span></span>  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a> <span data-ttu-id="bc357-120">사용자 지정 수식을 사용하여 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bc357-120">To create a measure using a custom formula</span></span>  
  
-   <span data-ttu-id="bc357-121">측정값 표에서 측정값을 만들려는 열 아래의 셀을 클릭한 다음 수식 표시줄에 이름과 콜론(:), 등호(=) 및 수식을 차례로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-121">In the measure grid, beneath the column for which you want to create the measure, click a cell, then in the formula bar, type a name, followed by a colon (:), followed by an equals sign (=), followed by the formula.</span></span> <span data-ttu-id="bc357-122">Enter 키를 눌러 수식을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-122">Press ENTER to accept the formula.</span></span>  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a><span data-ttu-id="bc357-123">측정값 속성을 편집 하려면</span><span class="sxs-lookup"><span data-stu-id="bc357-123">To edit measure properties</span></span>  
  
-   <span data-ttu-id="bc357-124">측정값 표에서 측정값을 클릭한 다음 **속성** 창에서 다른 속성 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-124">In the measure grid, click a measure, and then In the **Properties** window, type or select a different property value.</span></span>  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a><span data-ttu-id="bc357-125">측정값 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="bc357-125">To rename a measure</span></span>  
  
-   <span data-ttu-id="bc357-126">측정값 표에서 측정값을 클릭한 다음 **속성** 창의 **측정값 이름**에 새 이름을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-126">In the measure grid, click on a measure, and then In the **Properties** window, in **Measure Name**, type a new name, and then click ENTER.</span></span>  
  
     <span data-ttu-id="bc357-127">수식 입력줄에서 측정값 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-127">You can also rename a measure in the formula bar.</span></span> <span data-ttu-id="bc357-128">수식 앞에 측정값 이름이 표시되고 그 뒤에 콜론이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-128">The measure name precedes the formula, followed by a colon.</span></span>  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a><span data-ttu-id="bc357-129">측정값을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="bc357-129">To delete a measure</span></span>  
  
-   <span data-ttu-id="bc357-130">측정값 표에서 측정값을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc357-130">In the measure grid, right-click a measure, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc357-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc357-131">See Also</span></span>  
 <span data-ttu-id="bc357-132">[SSAS 테이블 형식&#41;&#40;측정값](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="bc357-132">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 <span data-ttu-id="bc357-133">[SSAS 테이블 형식&#41;&#40;Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="bc357-133">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="bc357-134">계산 열&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="bc357-134">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)  
  
  
