---
title: Kpi (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54cc7341f2d0f002496c1936f2c4f0808cd5e243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728812"
---
# <a name="kpis-ssas-tabular"></a><span data-ttu-id="00c0d-102">KPI(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="00c0d-102">KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="00c0d-103">테이블 형식 모델에서 *KPI* (핵심 성과 지표)는 측정값 또는 절대값으로 정의된 *대상* 값에 대해 *기본* 측정값으로 정의된 값의 성능을 측정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-103">A *KPI* (Key Performance Indicator), in a tabular model, is used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="00c0d-104">이 항목은 테이블 형식 모델 작성자에게 테이블 형식 모델에서 KPI에 대한 기본적인 이해를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-104">This topic provides tabular model authors a basic understanding of KPIs in a tabular model.</span></span>  
  
 <span data-ttu-id="00c0d-105">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="00c0d-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="00c0d-106">이점</span><span class="sxs-lookup"><span data-stu-id="00c0d-106">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="00c0d-107">예제</span><span class="sxs-lookup"><span data-stu-id="00c0d-107">Example</span></span>](#bkmk_example)  
  
-   [<span data-ttu-id="00c0d-108">Kpi 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="00c0d-108">Create and Edit KPIs</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="00c0d-109">관련 작업</span><span class="sxs-lookup"><span data-stu-id="00c0d-109">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="00c0d-110">이점</span><span class="sxs-lookup"><span data-stu-id="00c0d-110">Benefits</span></span>  
 <span data-ttu-id="00c0d-111">비즈니스 용어에서 KPI(핵심 성과 지표)는 비즈니스 목표를 평가하기 위한 정량 측정값입니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-111">In business terminology, a Key Performance Indicator (KPI) is a quantifiable measurement for gauging business objectives.</span></span> <span data-ttu-id="00c0d-112">KPI는 주로 시간에 따라 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-112">A KPI is frequently evaluated over time.</span></span> <span data-ttu-id="00c0d-113">예를 들어 조직의 영업부에서는 KPI를 사용하여 월별 예상 매출 총 이익 대비 매출 총 이익을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-113">For example, the sales department of an organization may use a KPI to measure monthly gross profit against projected gross profit.</span></span> <span data-ttu-id="00c0d-114">회계부에서는 월별 수익 대비 지출을 계산하여 비용을 평가하고, 인사부에서는 분기별 직원 전직률을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-114">The accounting department may measure monthly expenditures against revenue to evaluate costs, and a human resources department may measure quarterly employee turnover.</span></span> <span data-ttu-id="00c0d-115">각각은 KPI의 예에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-115">Each is an example of a KPI.</span></span> <span data-ttu-id="00c0d-116">경영진은 비즈니스 성과표에 그룹화된 KPI를 사용하여 비즈니스 성취도에 대한 빠르고 정확한 요약 정보를 얻거나 추세를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-116">Business professionals frequently consume KPIs that are grouped together in a business scorecard to obtain a quick and accurate historical summary of business success or to identify trends.</span></span>  
  
 <span data-ttu-id="00c0d-117">테이블 형식 모델의 KPI에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-117">A KPI in a tabular model includes:</span></span>  
  
 <span data-ttu-id="00c0d-118">**기본 값**</span><span class="sxs-lookup"><span data-stu-id="00c0d-118">**Base Value**</span></span>  
 <span data-ttu-id="00c0d-119">기본 값은 값으로 확인되는 측정값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-119">A Base value is defined by a measure that resolves to a value.</span></span> <span data-ttu-id="00c0d-120">이 값은 예를 들어 실제 매출의 집계 또는 특정 기간 동안의 수익과 같은 계산된 측정값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-120">This value, for example, can be an aggregate of actual Sales or a calculated measure such as Profit for a given period.</span></span>  
  
 <span data-ttu-id="00c0d-121">**대상 값**</span><span class="sxs-lookup"><span data-stu-id="00c0d-121">**Target value**</span></span>  
 <span data-ttu-id="00c0d-122">대상 값은 값으로 확인되는 측정값이나 절대값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-122">A Target value is defined by a measure that resolves to a value, or by an absolute value.</span></span> <span data-ttu-id="00c0d-123">예를 들어, 대상 값은 조직의 비즈니스 관리자가 매출 또는 수익을 증가시키려는 금액일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-123">For example, a target value could be the amount by which the business managers of an organization want to increase sales or profit.</span></span>  
  
 <span data-ttu-id="00c0d-124">**상태 임계값**</span><span class="sxs-lookup"><span data-stu-id="00c0d-124">**Status thresholds**</span></span>  
 <span data-ttu-id="00c0d-125">상태 임계값은 낮은 임계값과 높은 임계값 간의 범위 또는 고정 값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-125">A Status threshold is defined by the range between a low and high threshold or by a fixed value.</span></span> <span data-ttu-id="00c0d-126">상태 임계값은 그래픽과 함께 표시되므로 대상 값과 비교한 기본 값의 상태를 손쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-126">The Status threshold displays with a graphic to help users easily determine the status of the Base value compared to the Target value.</span></span>  
  
##  <a name="example"></a><a name="bkmk_example"></a> <span data-ttu-id="00c0d-127">예제</span><span class="sxs-lookup"><span data-stu-id="00c0d-127">Example</span></span>  
 <span data-ttu-id="00c0d-128">Adventure Works의 영업 관리자는 영업 직원이 특정 기간(년) 동안 자신의 판매 할당량을 달성하고 있는지 여부를 빠르게 표시하는 데 사용할 수 있는 피벗 테이블을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-128">The sales manager at Adventure Works wants to create a PivotTable that she can use to quickly display whether or not sales employees are meeting their sales quota for a given period (year).</span></span> <span data-ttu-id="00c0d-129">각 영업 직원에 대해 실제 판매액(달러)과 판매 할당액(달러)이 표시되고 각 영업 직원이 현재 자신의 판매 할당액을 달성했는지 그 이하 또는 이상인지를 보여 주는 간단한 그래픽이 표시되는 피벗 테이블을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-129">For each sales employee, she wants the PivotTable to display the actual sales amount in dollars, the sales quota amount in dollars, and a simple graphic display showing the status of whether or not each sales employee is below, at, or above their sales quota.</span></span> <span data-ttu-id="00c0d-130">또한 데이터를 연도별로 분류할 수 있도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-130">She wants to be able to slice the data by year.</span></span>  
  
 <span data-ttu-id="00c0d-131">이렇게 하기 위해 영업 관리자는 조직의 BI 솔루션 개발자의 도움을 받아 AdventureWorks 테이블 형식 모델에 Sales KPI를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-131">To do this, the sales manager enlists the help of her organization's BI solution developer to add a Sales KPI to the AdventureWorks Tabular Model.</span></span> <span data-ttu-id="00c0d-132">그런 다음 영업 관리자는 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 을 사용하여 Adventure Works 테이블 형식 모델에 데이터 원본으로 연결하고 필드(측정값 및 KPI)와 슬라이서가 포함된 피벗 테이블을 만들어 영업 직원이 자신의 할당액을 달성하고 있는지 여부를 분석하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-132">The sales manager will then use [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] to connect to the Adventure Works Tabular Model as a data source and create a PivotTable with the fields (measures and KPI) and slicers to analyze whether or not the sales force is meeting their quotas.</span></span>  
  
 <span data-ttu-id="00c0d-133">모델에서 FactResellerSales 테이블의 SalesAmount 열에는 각 영업 직원의 실제 판매액(달러)을 보여 주는 측정값이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-133">In the model, a measure on the SalesAmount column in the FactResellerSales table, which gives the actual sales amount in dollars for each sales employee is created.</span></span> <span data-ttu-id="00c0d-134">이 측정값은 KPI의 기본 값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-134">This measure will define the Base value of the KPI.</span></span>  
  
 <span data-ttu-id="00c0d-135">Sales 측정값은 다음 수식을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-135">The Sales measure is created with the following formula:</span></span>  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 <span data-ttu-id="00c0d-136">FactSalesQuota 테이블의 SalesAmountQuota 열에는 각 직원에 대해 정의된 판매 할당액이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-136">The SalesAmountQuota column in the FactSalesQuota table has a sales amount quota defined for each employee.</span></span> <span data-ttu-id="00c0d-137">이 열의 값은 KPI의 대상 측정값(값)으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-137">The values in this column will serve as the Target measure (value) in the KPI.</span></span>  
  
 <span data-ttu-id="00c0d-138">SalesAmountQuota 측정값은 다음 수식을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-138">The SalesAmountQuota measure is created with the following formula:</span></span>  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="00c0d-139">FactSalesQuota 테이블의 EmployeeKey 열과 DimEmployees 테이블의 EmployeeKey 간에는 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-139">There is a relationship between the EmployeeKey column in the FactSalesQuota table and the EmployeeKey in the DimEmployees table.</span></span> <span data-ttu-id="00c0d-140">이 관계는 DimEmployee 테이블의 각 영업 직원이 FactSalesQuota 테이블에 표시되도록 하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-140">This relationship is necessary so that each sales employee in the DimEmployee table is represented in the FactSalesQuota table.</span></span>  
  
 <span data-ttu-id="00c0d-141">KPI의 기본 값과 대상 값으로 사용할 측정값을 만든 후에는 Sales 측정값을 새 Sales KPI로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-141">Now that measures have been created to serve as the Base value and Target value of the KPI, the Sales measure is extended to a new Sales KPI.</span></span> <span data-ttu-id="00c0d-142">Sales KPI에서 Target SalesAmountQuota 측정값은 대상 값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-142">In the Sales KPI, the Target SalesAmountQuota measure is defined as the Target value.</span></span> <span data-ttu-id="00c0d-143">상태 임계값은 백분율 단위의 범위로 정의되며, 목표 백분율인 100%는 Sales 측정값으로 정의된 실제 판매액이 Target SalesAmoutnQuota 측정값에 정의된 할당액에 도달했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-143">The Status threshold is defined as a range by percentage, the target of which is 100% meaning actual sales defined by the Sales measure met the quota amount defined in the Target SalesAmoutnQuota measure.</span></span> <span data-ttu-id="00c0d-144">낮은 백분율과 높은 백분율은 상태 표시줄에 정의되고 그래픽 종류가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-144">Low and High percentages are defined on the status bar, and a graphic type is selected.</span></span>  
  
 <span data-ttu-id="00c0d-145">이제 sales manager에서 KPI의 기본 값, 대상 값 및 상태를 값 필드에 추가 하는 피벗 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-145">The sales manager can now create a PivotTable adding the KPI's Base value, Target value, and Status to the Values field.</span></span> <span data-ttu-id="00c0d-146">Employees 열이 RowLabel 필드에 추가되고 CalendarYear 열이 슬라이서로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-146">The Employees column is added to the RowLabel field, and the CalendarYear column is added as a Slicer.</span></span>  
  
 <span data-ttu-id="00c0d-147">이제 영업 관리자는 각 영업 직원의 실제 판매액, 판매 할당액 및 상태를 연도별로 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-147">The sales manager can now slice by year the actual sales amount, sales quota amount, and status for each sales employee.</span></span> <span data-ttu-id="00c0d-148">또한 몇 년 동안의 판매 추세를 분석하여 영업 직원의 판매 할당액을 조정해야 하는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-148">She can analyze sales trends over years to determine whether or not she needs to adjust the sales quota for a sales employee.</span></span>  
  
##  <a name="create-and-edit-kpis"></a><a name="bkmk_create"></a><span data-ttu-id="00c0d-149">Kpi 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="00c0d-149">Create and Edit KPIs</span></span>  
 <span data-ttu-id="00c0d-150">KPI를 만들려면 모델 디자이너에서 핵심 성과 지표 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-150">To create KPIs, in the model designer, you will use the Key Performance Indicator dialog box.</span></span> <span data-ttu-id="00c0d-151">KPI는 측정값과 관련되어야 하므로 기준 값으로 평가되는 측정값을 확장한 다음 대상 값으로 평가되는 측정값을 만들거나 절대값을 입력하여 KPI를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-151">Since KPIs must be associated with a measure, you create a KPI by extending a measure that evaluates to a Base value, and then either creating a measure that evaluates to a Target value or by entering an absolute value.</span></span> <span data-ttu-id="00c0d-152">기본 측정값(값과 대상 값을 정의한 후 기준 값과 대상 값 사이에서 상태 임계값 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-152">After the Base measure (value) and Target value is defined, you can then define the status threshold parameters between the Base and Target values.</span></span> <span data-ttu-id="00c0d-153">상태는 선택 가능한 아이콘, 막대, 그래프 또는 색상을 사용하여 그래픽 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-153">The status is displayed in a graphical format using selectable icons, bars, graphs, or colors.</span></span> <span data-ttu-id="00c0d-154">그런 다음 기준 값 및 대상 값과 상태를 다른 데이터 필드에 대해 분할할 수 있는 값으로 보고서 또는 피벗 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-154">The Base and Target values, as well as the Status can then be added to a report or PivotTable as values that can be sliced against other data fields.</span></span>  
  
 <span data-ttu-id="00c0d-155">핵심 성과 지표 대화 상자를 보려면 테이블에 대한 측정값 표에서 기준 값으로 사용되는 측정값을 마우스 오른쪽 단추로 클릭한 다음 **KPI 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-155">To view the Key Performance Indicator dialog box, in the measure grid for a table, right click a measure that will serve as the Base value, and then click **Create KPI**.</span></span> <span data-ttu-id="00c0d-156">측정값이 기준 값으로 KPI에 확장된 후에는 KPI와 관련된 측정값을 식별하는 아이콘이 측정값 표의 측정값 이름 옆에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-156">After a measure has been extended to a KPI as a Base value, an icon will appear alongside the measure name in the measure grid identifying the measure as associated with a KPI.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="00c0d-157">관련 작업</span><span class="sxs-lookup"><span data-stu-id="00c0d-157">Related Tasks</span></span>  
  
|<span data-ttu-id="00c0d-158">항목</span><span class="sxs-lookup"><span data-stu-id="00c0d-158">Topic</span></span>|<span data-ttu-id="00c0d-159">Description</span><span class="sxs-lookup"><span data-stu-id="00c0d-159">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="00c0d-160">KPI 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="00c0d-160">Create and Manage KPIs &#40;SSAS Tabular&#41;</span></span>](kpis-ssas-tabular.md)|<span data-ttu-id="00c0d-161">기본 측정값, 대상 측정값 및 상태 임계값을 사용하여 KPI를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00c0d-161">Describes how to create a KPI with a Base measure, a Target measure, and status thresholds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00c0d-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00c0d-162">See Also</span></span>  
 <span data-ttu-id="00c0d-163">[SSAS 테이블 형식&#41;&#40;측정값](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="00c0d-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="00c0d-164">큐브 뷰&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="00c0d-164">Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)  
  
  
