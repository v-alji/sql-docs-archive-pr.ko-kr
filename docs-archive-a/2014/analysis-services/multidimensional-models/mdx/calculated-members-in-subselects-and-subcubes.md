---
title: 하위 select 및 하위 큐브의 계산 멤버 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e6f4277c864b637c7fc5d93232ac6ebd8c4bb4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652409"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="50697-102">하위 SELECT 및 하위 큐브의 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="50697-102">Calculated Members in Subselects and Subcubes</span></span>
  <span data-ttu-id="50697-103">이전 릴리스에서는 계산 멤버가 하위 SELECT 또는 하위 큐브에서 허용되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-103">In previous releases, calculated members were not allowed in subselects or subcubes.</span></span> <span data-ttu-id="50697-104">그러나 SQL Server 2008부터 계산 멤버가 허용되며 연결 속성에 의해 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-104">However, starting with SQL Server 2008 they are allowed and enabled by a connection property.</span></span> <span data-ttu-id="50697-105">또한 하위 SELECT 및 하위 큐브의 계산 멤버에 대한 새 동작이 SQL Server 2008 R2에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-105">In addition, a new behavior for calculated members, in subselects and subcubes, was introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="50697-106">하위 SELECT 및 하위 큐브의 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="50697-106">Calculated Members in Subselects and Subcubes</span></span>  
 <span data-ttu-id="50697-107">`SubQueries`의 연결 문자열 속성 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 또는 `DBPROPMSMDSUBQUERIES` [지원 되는 xmla 속성 &#40;xmla&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) 의 속성은 하위 select 또는 하위 큐브에서 계산 멤버 또는 계산 집합의 동작이 나 허용을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-107">The `SubQueries` connection string property in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> or the `DBPROPMSMDSUBQUERIES` property in [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) defines the behavior or allowance of calculated members or calculated sets on subselects or subcubes.</span></span> <span data-ttu-id="50697-108">특별한 언급이 없으면 이 문서의 컨텍스트에서 하위 SELECT는 하위 SELECT 및 하위 큐브를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-108">In the context of this document, subselect refers to subselects and subcubes unless otherwise stated.</span></span>  
  
 <span data-ttu-id="50697-109">SubQueries 속성은 다음 값을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-109">The SubQueries property allows the following values.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50697-110">값</span><span class="sxs-lookup"><span data-stu-id="50697-110">Value</span></span>|<span data-ttu-id="50697-111">Description</span><span class="sxs-lookup"><span data-stu-id="50697-111">Description</span></span>|  
|<span data-ttu-id="50697-112">0</span><span class="sxs-lookup"><span data-stu-id="50697-112">0</span></span>|<span data-ttu-id="50697-113">계산 멤버는 하위 SELECT 또는 하위 큐브에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-113">Calculated members are not allowed in subselects or subcubes.</span></span><br /><br /> <span data-ttu-id="50697-114">계산 멤버가 참조된 경우 하위 SELECT 또는 하위 큐브를 평가할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-114">An error is raised when evaluating the subselect or subcube if a calculated member is referenced.</span></span>|  
|<span data-ttu-id="50697-115">1</span><span class="sxs-lookup"><span data-stu-id="50697-115">1</span></span>|<span data-ttu-id="50697-116">계산 멤버는 하위 SELECT 또는 하위 큐브에서 허용되지만 상위 항목 멤버는 반환 하위 공간에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-116">Calculated members are allowed in subselects or subcubes but no ascendant members are introduced in the returning subspace.</span></span>|  
|<span data-ttu-id="50697-117">2</span><span class="sxs-lookup"><span data-stu-id="50697-117">2</span></span>|<span data-ttu-id="50697-118">계산 멤버는 하위 SELECT 또는 하위 큐브에서 허용되고 상위 항목 멤버는 반환 하위 공간에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-118">Calculated members are allowed in subselects or subcubes and ascendant members are introduced in the returning subspace.</span></span> <span data-ttu-id="50697-119">또한 혼합 세분성이 계산 멤버 선택에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-119">Also, mixed granularity is allowed in the selection of calculated members.</span></span>|  
  
 <span data-ttu-id="50697-120">SubQueries 속성에서 값 1 또는 2를 사용하면 계산 멤버를 사용하여 하위 SELECT의 반환 하위 공간을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-120">Using values of 1 or 2 in the SubQueries property allows calculated members to be used to filter the returning subspace of subselects.</span></span>  
  
 <span data-ttu-id="50697-121">예제는 개념을 명확히 하는 데 도움이 됩니다. 먼저 위에 언급한 동작을 보여 주기 위해 계산 멤버를 만든 다음 하위 SELECT 쿼리를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-121">An example will help clarify the concept; first a calculated member must be created and then a subselect query issued to show the above mentioned behavior.</span></span>  
  
 <span data-ttu-id="50697-122">다음 샘플에서는 Washington 주 아래의 [Geography].[Geography] 계층에 [Seattle Metro]를 도시로 추가하는 계산 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50697-122">The following sample creates a calculated member that adds [Seattle Metro] as a city to the [Geography].[Geography] hierarchy under Washington state.</span></span>  
  
 <span data-ttu-id="50697-123">예제를 실행하려면 연결 문자열은 값이 1인 SubQueries 속성을 포함해야 하고 모든 MDX 문은 동일한 세션에서 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-123">To run the example, the connection string must contain the SubQueries property with a value of 1 and all MDX statements must be run in the same session.</span></span>  
  
 <span data-ttu-id="50697-124">먼저 다음 MDX 식을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-124">First issue the following MDX expression:</span></span>  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 <span data-ttu-id="50697-125">그런 후 다음 MDX 쿼리를 실행하여 하위 SELECT에서 허용되는 계산 멤버를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50697-125">Then issue the following MDX query to see calculated members allowed in subselects.</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="50697-126">다음과 같은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-126">The obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="50697-127">All Periods</span><span class="sxs-lookup"><span data-stu-id="50697-127">All Periods</span></span>|<span data-ttu-id="50697-128">CY 2001</span><span class="sxs-lookup"><span data-stu-id="50697-128">CY 2001</span></span>|<span data-ttu-id="50697-129">CY 2002</span><span class="sxs-lookup"><span data-stu-id="50697-129">CY 2002</span></span>|<span data-ttu-id="50697-130">CY 2003</span><span class="sxs-lookup"><span data-stu-id="50697-130">CY 2003</span></span>|<span data-ttu-id="50697-131">CY 2004</span><span class="sxs-lookup"><span data-stu-id="50697-131">CY 2004</span></span>|  
|<span data-ttu-id="50697-132">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="50697-132">Seattle Metro Agg</span></span>|<span data-ttu-id="50697-133">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="50697-133">$2,383,545.69</span></span>|<span data-ttu-id="50697-134">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="50697-134">$291,248.93</span></span>|<span data-ttu-id="50697-135">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="50697-135">$763,557.02</span></span>|<span data-ttu-id="50697-136">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="50697-136">$915,832.36</span></span>|<span data-ttu-id="50697-137">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="50697-137">$412,907.37</span></span>|  
  
 <span data-ttu-id="50697-138">이전에 언급한 것처럼 SubQueries=1이면 [Seattle Metro]의 상위 항목이 반환된 하위 공간에 없으므로 [Geography].[Geography].allmembers는 계산 멤버만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-138">As said before, the ascendants of [Seattle Metro] do not exist in the returned subspace, when SubQueries=1, hence [Geography].[Geography].allmembers only contains the calculated member.</span></span>  
  
 <span data-ttu-id="50697-139">SubQueries=2를 사용하여 예제를 실행할 경우 연결 문자열에서는 다음과 같은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-139">If the example is run using SubQueries=2, in the connection string, the obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="50697-140">All Periods</span><span class="sxs-lookup"><span data-stu-id="50697-140">All Periods</span></span>|<span data-ttu-id="50697-141">CY 2001</span><span class="sxs-lookup"><span data-stu-id="50697-141">CY 2001</span></span>|<span data-ttu-id="50697-142">CY 2002</span><span class="sxs-lookup"><span data-stu-id="50697-142">CY 2002</span></span>|<span data-ttu-id="50697-143">CY 2003</span><span class="sxs-lookup"><span data-stu-id="50697-143">CY 2003</span></span>|<span data-ttu-id="50697-144">CY 2004</span><span class="sxs-lookup"><span data-stu-id="50697-144">CY 2004</span></span>|  
|<span data-ttu-id="50697-145">All Geographies</span><span class="sxs-lookup"><span data-stu-id="50697-145">All Geographies</span></span>|<span data-ttu-id="50697-146">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-146">(null)</span></span>|<span data-ttu-id="50697-147">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-147">(null)</span></span>|<span data-ttu-id="50697-148">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-148">(null)</span></span>|<span data-ttu-id="50697-149">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-149">(null)</span></span>|<span data-ttu-id="50697-150">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-150">(null)</span></span>|  
|<span data-ttu-id="50697-151">미국</span><span class="sxs-lookup"><span data-stu-id="50697-151">United States</span></span>|<span data-ttu-id="50697-152">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-152">(null)</span></span>|<span data-ttu-id="50697-153">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-153">(null)</span></span>|<span data-ttu-id="50697-154">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-154">(null)</span></span>|<span data-ttu-id="50697-155">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-155">(null)</span></span>|<span data-ttu-id="50697-156">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-156">(null)</span></span>|  
|<span data-ttu-id="50697-157">워싱턴</span><span class="sxs-lookup"><span data-stu-id="50697-157">Washington</span></span>|<span data-ttu-id="50697-158">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-158">(null)</span></span>|<span data-ttu-id="50697-159">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-159">(null)</span></span>|<span data-ttu-id="50697-160">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-160">(null)</span></span>|<span data-ttu-id="50697-161">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-161">(null)</span></span>|<span data-ttu-id="50697-162">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-162">(null)</span></span>|  
|<span data-ttu-id="50697-163">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="50697-163">Seattle Metro Agg</span></span>|<span data-ttu-id="50697-164">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="50697-164">$2,383,545.69</span></span>|<span data-ttu-id="50697-165">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="50697-165">$291,248.93</span></span>|<span data-ttu-id="50697-166">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="50697-166">$763,557.02</span></span>|<span data-ttu-id="50697-167">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="50697-167">$915,832.36</span></span>|<span data-ttu-id="50697-168">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="50697-168">$412,907.37</span></span>|  
  
 <span data-ttu-id="50697-169">이전에 언급한 것처럼 SubQueries=2를 사용하면 [Seattle Metro]의 상위 항목이 반환된 하위 공간에 있지만 집계에 제공할 일반 멤버가 없으므로 이러한 멤버에 대한 값이 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-169">As said before, when using SubQueries=2, the ascendants of [Seattle Metro] exist in the returned subspace but no values exist for those members because there is no regular members to provide for the aggregations.</span></span> <span data-ttu-id="50697-170">따라서 이 예에서는 계산 멤버의 모든 상위 항목 멤버에 대해 NULL 값이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-170">Therefore, NULL values are provided for all ascendant members of the calculated member in this example.</span></span>  
  
 <span data-ttu-id="50697-171">위 동작을 이해하려면 일반 멤버와 같이 계산 멤버가 해당 부모의 집계에 영향을 주지 않는다는 사실을 이해하는 것이 도움이 됩니다. 전자의 경우 결과 하위 공간의 집계 값에 영향을 주는 일반 멤버가 없으므로 계산 멤버로 필터링하면 빈 상위 항목이 얻어집니다.</span><span class="sxs-lookup"><span data-stu-id="50697-171">To understand the above behavior, it helps to understand that calculated members do not contribute to the aggregations of their parents as regular members do; the former implies that filtering by calculated members alone will lead to empty ascendants because there are no regular members to contribute to the aggregated values of the resulting subspace.</span></span> <span data-ttu-id="50697-172">일반 멤버를 필터링 식에 추가할 경우 집계 값은 이러한 일반 멤버에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-172">If you add regular members to the filtering expression then the aggregated values will come from those regular members.</span></span> <span data-ttu-id="50697-173">위 예제의 경우 다음 MDX 식과 같이 Oregon의 Portland와 Washington의 Spokane을 계산 멤버가 나타나는 동일한 축에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-173">Continuing with the above example, if the cities of Portland, in Oregon, and the city of Spokane, in Washington, are added to the same axis where the calculated member appears; as shown in the next MDX expression:</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="50697-174">다음과 같은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-174">The following results are obtained.</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="50697-175">All Periods</span><span class="sxs-lookup"><span data-stu-id="50697-175">All Periods</span></span>|<span data-ttu-id="50697-176">CY 2001</span><span class="sxs-lookup"><span data-stu-id="50697-176">CY 2001</span></span>|<span data-ttu-id="50697-177">CY 2002</span><span class="sxs-lookup"><span data-stu-id="50697-177">CY 2002</span></span>|<span data-ttu-id="50697-178">CY 2003</span><span class="sxs-lookup"><span data-stu-id="50697-178">CY 2003</span></span>|<span data-ttu-id="50697-179">CY 2004</span><span class="sxs-lookup"><span data-stu-id="50697-179">CY 2004</span></span>|  
|<span data-ttu-id="50697-180">All Geographies</span><span class="sxs-lookup"><span data-stu-id="50697-180">All Geographies</span></span>|<span data-ttu-id="50697-181">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="50697-181">$235,171.62</span></span>|<span data-ttu-id="50697-182">$419.46</span><span class="sxs-lookup"><span data-stu-id="50697-182">$419.46</span></span>|<span data-ttu-id="50697-183">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="50697-183">$4,996.25</span></span>|<span data-ttu-id="50697-184">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="50697-184">$131,788.82</span></span>|<span data-ttu-id="50697-185">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="50697-185">$97,967.09</span></span>|  
|<span data-ttu-id="50697-186">미국</span><span class="sxs-lookup"><span data-stu-id="50697-186">United States</span></span>|<span data-ttu-id="50697-187">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="50697-187">$235,171.62</span></span>|<span data-ttu-id="50697-188">$419.46</span><span class="sxs-lookup"><span data-stu-id="50697-188">$419.46</span></span>|<span data-ttu-id="50697-189">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="50697-189">$4,996.25</span></span>|<span data-ttu-id="50697-190">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="50697-190">$131,788.82</span></span>|<span data-ttu-id="50697-191">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="50697-191">$97,967.09</span></span>|  
|<span data-ttu-id="50697-192">Oregon</span><span class="sxs-lookup"><span data-stu-id="50697-192">Oregon</span></span>|<span data-ttu-id="50697-193">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="50697-193">$30,968.25</span></span>|<span data-ttu-id="50697-194">$419.46</span><span class="sxs-lookup"><span data-stu-id="50697-194">$419.46</span></span>|<span data-ttu-id="50697-195">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="50697-195">$4,996.25</span></span>|<span data-ttu-id="50697-196">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="50697-196">$17,442.97</span></span>|<span data-ttu-id="50697-197">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="50697-197">$8,109.56</span></span>|  
|<span data-ttu-id="50697-198">Portland</span><span class="sxs-lookup"><span data-stu-id="50697-198">Portland</span></span>|<span data-ttu-id="50697-199">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="50697-199">$30,968.25</span></span>|<span data-ttu-id="50697-200">$419.46</span><span class="sxs-lookup"><span data-stu-id="50697-200">$419.46</span></span>|<span data-ttu-id="50697-201">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="50697-201">$4,996.25</span></span>|<span data-ttu-id="50697-202">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="50697-202">$17,442.97</span></span>|<span data-ttu-id="50697-203">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="50697-203">$8,109.56</span></span>|  
|<span data-ttu-id="50697-204">97205</span><span class="sxs-lookup"><span data-stu-id="50697-204">97205</span></span>|<span data-ttu-id="50697-205">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="50697-205">$30,968.25</span></span>|<span data-ttu-id="50697-206">$419.46</span><span class="sxs-lookup"><span data-stu-id="50697-206">$419.46</span></span>|<span data-ttu-id="50697-207">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="50697-207">$4,996.25</span></span>|<span data-ttu-id="50697-208">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="50697-208">$17,442.97</span></span>|<span data-ttu-id="50697-209">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="50697-209">$8,109.56</span></span>|  
|<span data-ttu-id="50697-210">워싱턴</span><span class="sxs-lookup"><span data-stu-id="50697-210">Washington</span></span>|<span data-ttu-id="50697-211">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="50697-211">$204,203.37</span></span>|<span data-ttu-id="50697-212">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-212">(null)</span></span>|<span data-ttu-id="50697-213">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-213">(null)</span></span>|<span data-ttu-id="50697-214">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="50697-214">$114,345.85</span></span>|<span data-ttu-id="50697-215">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="50697-215">$89,857.52</span></span>|  
|<span data-ttu-id="50697-216">Spokane</span><span class="sxs-lookup"><span data-stu-id="50697-216">Spokane</span></span>|<span data-ttu-id="50697-217">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="50697-217">$204,203.37</span></span>|<span data-ttu-id="50697-218">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-218">(null)</span></span>|<span data-ttu-id="50697-219">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-219">(null)</span></span>|<span data-ttu-id="50697-220">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="50697-220">$114,345.85</span></span>|<span data-ttu-id="50697-221">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="50697-221">$89,857.52</span></span>|  
|<span data-ttu-id="50697-222">99202</span><span class="sxs-lookup"><span data-stu-id="50697-222">99202</span></span>|<span data-ttu-id="50697-223">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="50697-223">$204,203.37</span></span>|<span data-ttu-id="50697-224">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-224">(null)</span></span>|<span data-ttu-id="50697-225">(null)</span><span class="sxs-lookup"><span data-stu-id="50697-225">(null)</span></span>|<span data-ttu-id="50697-226">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="50697-226">$114,345.85</span></span>|<span data-ttu-id="50697-227">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="50697-227">$89,857.52</span></span>|  
|<span data-ttu-id="50697-228">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="50697-228">Seattle Metro Agg</span></span>|<span data-ttu-id="50697-229">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="50697-229">$2,383,545.69</span></span>|<span data-ttu-id="50697-230">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="50697-230">$291,248.93</span></span>|<span data-ttu-id="50697-231">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="50697-231">$763,557.02</span></span>|<span data-ttu-id="50697-232">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="50697-232">$915,832.36</span></span>|<span data-ttu-id="50697-233">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="50697-233">$412,907.37</span></span>|  
  
 <span data-ttu-id="50697-234">위 결과에서 [All Geographies], [United States], [Oregon] 및 [Washington]에 대한 집계 값은 &[Portland]&[OR] 및 &[Spokane]&[WA]의 하위 항목에 대한 집계에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-234">In the above results the aggregated values for [All Geographies], [United States], [Oregon] and [Washington] come from aggregating over the descendants of &[Portland]&[OR] and &[Spokane]&[WA].</span></span> <span data-ttu-id="50697-235">계산 멤버에서는 아무 것도 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50697-235">Nothing comes from the calculated member.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="50697-236">설명</span><span class="sxs-lookup"><span data-stu-id="50697-236">Remarks</span></span>  
 <span data-ttu-id="50697-237">전역 또는 세션 계산 멤버만 하위 SELECT 또는 하위 큐브 식에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50697-237">Only global or session calculated members are allowed in the subselect or subcube expressions.</span></span> <span data-ttu-id="50697-238">MDX 식에 쿼리 계산 멤버가 있으면 하위 SELECT 또는 하위 큐브 식이 평가될 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="50697-238">Having query calculated members in the MDX expression will raise an error when the subselect or subcube expression is evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50697-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50697-239">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 <span data-ttu-id="50697-240">[쿼리의 하위 select](subselects-in-queries.md) </span><span class="sxs-lookup"><span data-stu-id="50697-240">[Subselects in Queries](subselects-in-queries.md) </span></span>  
 [<span data-ttu-id="50697-241">지원되는 XMLA 속성&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="50697-241">Supported XMLA Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
