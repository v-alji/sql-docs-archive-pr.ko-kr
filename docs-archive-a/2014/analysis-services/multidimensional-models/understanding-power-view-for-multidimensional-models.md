---
title: 다차원 모델에 대 한 파워 뷰 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d0558cae-8209-4242-80c5-2c95981b88b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 778bdb769238618e733e46f903cf70024cd27bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732123"
---
# <a name="understanding-power-view-for-multidimensional-models"></a><span data-ttu-id="1b0d6-102">다차원 모델용 파워 뷰 이해</span><span class="sxs-lookup"><span data-stu-id="1b0d6-102">Understanding Power View for Multidimensional Models</span></span>
  <span data-ttu-id="1b0d6-103">이 문서에서는 Microsoft SQL Server 2014의 다차원 모델용 Power View 기능에 대해 설명하고, 조직에서 다차원 모델용 Power View를 구현하려고 하는 BI 전문가 및 관리자에게 중요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-103">This article describes the Power View for Multidimensional Models feature in Microsoft SQL Server 2014, and provides important information for BI professionals and administrators who intend to implement Power View for Multidimensional Models in their organization.</span></span>  
  
 <span data-ttu-id="1b0d6-104">다차원 모델은 업계 최고의 OLAP 데이터 모델링, 스토리지 및 분석 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-104">Multidimensional models provide industry leading OLAP data modeling, storage, and analysis solutions.</span></span> <span data-ttu-id="1b0d6-105">SQL Server 2014의 다차원 모델은 Microsoft Power View를 사용하여 임시 데이터 분석, 탐색 및 시각화를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-105">Multidimensional models in SQL Server 2014 support ad-hoc data analysis, exploration, and visualization by using Microsoft Power View.</span></span>  
  
 <span data-ttu-id="1b0d6-106">파워 뷰는 SharePoint 라이브러리의 공유 보고서 데이터 원본 파일(.rsds)로부터 브라우저에서 실행되는 씬 웹 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-106">Power View is a thin web client that launches in the browser from a shared Report Data Source (.rsds) file in a SharePoint library.</span></span> <span data-ttu-id="1b0d6-107">보고서 데이터 원본은 클라이언트와 백 엔드 데이터 원본 간을 연결하는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-107">The Report Data Source acts as a bridge between the client and the back-end data source.</span></span> <span data-ttu-id="1b0d6-108">백 엔드 데이터 원본은 SharePoint의 PowerPivot 통합 문서, 테이블 형식 모드에서 실행되는 Analysis Services 서버의 테이블 형식 모델 또는 다차원 모드에서 실행되는 Analysis Services 서버의 다차원 모델일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-108">The back-end data source can be a PowerPivot workbook in SharePoint, a Tabular model on an Analysis Services server running in Tabular mode, or a Multidimensional model on an Analysis Services server running in Multidimensional mode.</span></span> <span data-ttu-id="1b0d6-109">파워 뷰 보고서는 SharePoint 라이브러리 또는 갤러리에 저장할 수 있으며 조직의 다른 구성원과 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-109">Power View reports can then be saved to a SharePoint library or gallery and shared with other members in your organization.</span></span>  
  
 <span data-ttu-id="1b0d6-110">**다차원 모델용 파워 뷰 아키텍처**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-110">**Power View for Multidimensional Models architecture**</span></span>  
  
 <span data-ttu-id="1b0d6-111">![다차원 모델 아키텍처에 대 한 파워 뷰](../media/daxmd-architecture.gif "다차원 모델 아키텍처에 대 한 파워 뷰")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-111">![Power View for Multidimensional Models Architecture](../media/daxmd-architecture.gif "Power View for Multidimensional Models Architecture")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1b0d6-112">필수 조건</span><span class="sxs-lookup"><span data-stu-id="1b0d6-112">Prerequisites</span></span>  
 <span data-ttu-id="1b0d6-113">**서버 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-113">**Server Requirements**</span></span>  
  
-   <span data-ttu-id="1b0d6-114">다차원 모드에서 실행하는 Analysis Service와 SQL Server 2014 Enterprise 또는 Business Intelligence Edition.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-114">SQL Server 2014 Enterprise or Business Intelligence edition with Analysis Services running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="1b0d6-115">Microsoft SharePoint Server 2010 또는 2013 Enterprise Edition용 SQL Server 2014 Reporting Services 추가 기능.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-115">SQL Server 2014 Reporting Services Add-in for Microsoft SharePoint Server 2010 or 2013 Enterprise Edition.</span></span>  
  
 <span data-ttu-id="1b0d6-116">**클라이언트 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-116">**Client Requirements**</span></span>  
  
-   <span data-ttu-id="1b0d6-117">파워 뷰 클라이언트 기능에는 Microsoft Silverlight 5가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-117">Power View client functionality requires Microsoft Silverlight 5.</span></span> <span data-ttu-id="1b0d6-118">자세한 내용은 [Reporting Services 계획 및 파워 뷰 브라우저 지원 &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-118">For more information, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
## <a name="features"></a><span data-ttu-id="1b0d6-119">기능</span><span class="sxs-lookup"><span data-stu-id="1b0d6-119">Features</span></span>  
 <span data-ttu-id="1b0d6-120">**파워 뷰에 대한 기본 지원**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-120">**Native support for Power View**</span></span>  
  
 <span data-ttu-id="1b0d6-121">이 릴리스에서 다차원 모델은 SharePoint 모드의 파워 뷰를 사용하여 분석 및 시각화를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-121">With this release, multidimensional models support analysis and visualization by using Power View in SharePoint mode.</span></span> <span data-ttu-id="1b0d6-122">다차원 모델에 대한 특별한 구성은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-122">No special configuration of your multidimensional models is necessary.</span></span> <span data-ttu-id="1b0d6-123">하지만 Microsoft Excel 및 Microsoft PerformancePoint 등의 다른 클라이언트 도구와 비교할 때 파워 뷰에서 다차원 모델 개체가 표시되는 방식에는 몇 가지 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-123">There are however some differences in how multidimensional model objects are displayed in Power View compared to other client tools such as Microsoft Excel and Microsoft Performance Point.</span></span> <span data-ttu-id="1b0d6-124">이 릴리스에서는 Excel 2013의 Power View를 사용하여 다차원 모델의 분석 및 시각화를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-124">This release does not support analysis and visualization of multidimensional models by using Power View in Excel 2013.</span></span>  
  
 <span data-ttu-id="1b0d6-125">**DAX 쿼리에 대한 기본 지원**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-125">**Native support for DAX queries**</span></span>  
  
 <span data-ttu-id="1b0d6-126">이 릴리스에서 다차원 모델은 일반적인 MDX 쿼리뿐 아니라 DAX 쿼리 및 함수도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-126">With this release, multidimensional models support DAX queries and functions in addition to more traditional MDX queries.</span></span> <span data-ttu-id="1b0d6-127">PATH 같은 일부 DAX 함수는 다차원 모델링에 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-127">Some DAX functions, such as PATH, are not applicable in multidimensional modeling.</span></span> <span data-ttu-id="1b0d6-128">DAX에 대한 자세한 내용 및 MDX와의 차이점을 알아보려면 [Data Analysis Expressions 및 MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-128">For a better understanding of DAX and how it compares to MDX, see [Data Analysis Expressions and MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx).</span></span>  
  
## <a name="multidimensional-to-tabular-object-mapping"></a><span data-ttu-id="1b0d6-129">다차원 개체와 테이블 형식 개체의 매핑</span><span class="sxs-lookup"><span data-stu-id="1b0d6-129">Multidimensional to tabular object mapping</span></span>  
 <span data-ttu-id="1b0d6-130">Analysis Services에서는 다차원 모델을 테이블 형식 모델 메타데이터로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-130">Analysis Services provides a tabular model metadata representation of a multidimensional model.</span></span> <span data-ttu-id="1b0d6-131">다차원 모델의 개체는 파워 뷰와 BI 주석이 포함된 CSDL 출력에서 테이블 형식 개체로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-131">Objects in a multidimensional model are represented as tabular objects in Power View and in CSDL out with BI annotations.</span></span>  
  
 <span data-ttu-id="1b0d6-132">**개체 매핑 요약**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-132">**Object mapping summary**</span></span>  
  
|<span data-ttu-id="1b0d6-133">다차원 개체</span><span class="sxs-lookup"><span data-stu-id="1b0d6-133">Multidimensional Object</span></span>|<span data-ttu-id="1b0d6-134">테이블 형식 개체</span><span class="sxs-lookup"><span data-stu-id="1b0d6-134">Tabular Object</span></span>|  
|-----------------------------|--------------------|  
|<span data-ttu-id="1b0d6-135">큐브</span><span class="sxs-lookup"><span data-stu-id="1b0d6-135">Cube</span></span>|<span data-ttu-id="1b0d6-136">모델</span><span class="sxs-lookup"><span data-stu-id="1b0d6-136">Model</span></span>|  
|<span data-ttu-id="1b0d6-137">큐브 차원</span><span class="sxs-lookup"><span data-stu-id="1b0d6-137">Cube Dimension</span></span>|<span data-ttu-id="1b0d6-138">표</span><span class="sxs-lookup"><span data-stu-id="1b0d6-138">Table</span></span>|  
|<span data-ttu-id="1b0d6-139">차원 특성(키, 이름)</span><span class="sxs-lookup"><span data-stu-id="1b0d6-139">Dimension Attributes (Key(s), Name)</span></span>|<span data-ttu-id="1b0d6-140">열</span><span class="sxs-lookup"><span data-stu-id="1b0d6-140">Column</span></span>|  
|<span data-ttu-id="1b0d6-141">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="1b0d6-141">Measure Group</span></span>|<span data-ttu-id="1b0d6-142">표</span><span class="sxs-lookup"><span data-stu-id="1b0d6-142">Table</span></span>|  
|<span data-ttu-id="1b0d6-143">측정값</span><span class="sxs-lookup"><span data-stu-id="1b0d6-143">Measure</span></span>|<span data-ttu-id="1b0d6-144">측정값</span><span class="sxs-lookup"><span data-stu-id="1b0d6-144">Measure</span></span>|  
|<span data-ttu-id="1b0d6-145">측정값 그룹이 없는 측정값</span><span class="sxs-lookup"><span data-stu-id="1b0d6-145">Measure without Measure Group</span></span>|<span data-ttu-id="1b0d6-146">Measures라는 테이블의 내부</span><span class="sxs-lookup"><span data-stu-id="1b0d6-146">In a table named Measures</span></span>|  
|<span data-ttu-id="1b0d6-147">측정값 그룹 큐브 차원 관계</span><span class="sxs-lookup"><span data-stu-id="1b0d6-147">Measure Group Cube Dimension Relationship</span></span>|<span data-ttu-id="1b0d6-148">관계</span><span class="sxs-lookup"><span data-stu-id="1b0d6-148">Relationship</span></span>|  
|<span data-ttu-id="1b0d6-149">관점</span><span class="sxs-lookup"><span data-stu-id="1b0d6-149">Perspective</span></span>|<span data-ttu-id="1b0d6-150">관점</span><span class="sxs-lookup"><span data-stu-id="1b0d6-150">Perspective</span></span>|  
|<span data-ttu-id="1b0d6-151">KPI</span><span class="sxs-lookup"><span data-stu-id="1b0d6-151">KPI</span></span>|<span data-ttu-id="1b0d6-152">KPI</span><span class="sxs-lookup"><span data-stu-id="1b0d6-152">KPI</span></span>|  
|<span data-ttu-id="1b0d6-153">사용자/부모-자식 계층</span><span class="sxs-lookup"><span data-stu-id="1b0d6-153">User/Parent-Child Hierarchies</span></span>|<span data-ttu-id="1b0d6-154">계층</span><span class="sxs-lookup"><span data-stu-id="1b0d6-154">Hierarchy</span></span>|  
|<span data-ttu-id="1b0d6-155">표시 폴더</span><span class="sxs-lookup"><span data-stu-id="1b0d6-155">Display Folder</span></span>|<span data-ttu-id="1b0d6-156">표시 폴더</span><span class="sxs-lookup"><span data-stu-id="1b0d6-156">Display Folder</span></span>|  
  
## <a name="measures-measure-groups-and-kpis"></a><span data-ttu-id="1b0d6-157">측정값, 측정값 그룹 및 KPI</span><span class="sxs-lookup"><span data-stu-id="1b0d6-157">Measures, measure groups, and KPIs</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b0d6-158">이 문서의 일부 이미지 및 텍스트는 SQL Server 2012용 Adventure Works 다차원 모델 예제 데이터베이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-158">Some images and text in this article refer to the Adventure Works Multidimensional Model for SQL Server 2012 sample database.</span></span>  
  
 <span data-ttu-id="1b0d6-159">다차원 큐브의 측정값 그룹은 파워 뷰 필드 목록에서 시그마(∑) 기호가 있는 테이블로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-159">Measure groups in a multidimensional cube are seen in the Power View Field List as tables with the sigma (∑) sign.</span></span>  
  
 <span data-ttu-id="1b0d6-160">**파워 뷰 필드 목록의 측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-160">**Measure groups in the Power View Field List**</span></span>  
  
 <span data-ttu-id="1b0d6-161">![Power View의 필드 목록](../media/daxmd-powerviewfieldlist.gif "Power View의 필드 목록")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-161">![Field List in Power View](../media/daxmd-powerviewfieldlist.gif "Field List in Power View")</span></span>  
  
 <span data-ttu-id="1b0d6-162">측정값 그룹 내의 측정값은 측정값으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-162">Measures within a measure group appear as measures.</span></span> <span data-ttu-id="1b0d6-163">연결된 측정값 그룹이 없는 계산 측정값이 있을 경우 이러한 측정값은 Measures라는 특수 테이블에 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-163">If there are calculated measures that do not have an associated measure group, they will be grouped under a special table called Measures.</span></span>  
  
 <span data-ttu-id="1b0d6-164">보다 복잡한 다차원 모델을 단순화하기 쉽도록 모델 작성자는 표시 폴더에 배치할 큐브의 측정값 또는 KPI 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-164">To help simplify more complex multidimensional models, model authors can define a set of measures or KPIs in a cube to be located within a display folder.</span></span> <span data-ttu-id="1b0d6-165">파워 뷰에서는 표시 폴더와 그 안의 측정값 및 KPI를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-165">Power View can show display folders and the measures and KPIs in them.</span></span>  
  
 <span data-ttu-id="1b0d6-166">**측정값 그룹의 측정값 및 KPI**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-166">**Measures and KPIs in a measure group**</span></span>  
  
 <span data-ttu-id="1b0d6-167">![Power View 필드 목록의 측정값 그룹](../media/daxmd-fieldlist-group.gif "Power View 필드 목록의 측정값 그룹")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-167">![Measure group in Power View Field List](../media/daxmd-fieldlist-group.gif "Measure group in Power View Field List")</span></span>  
  
### <a name="measures-as-variants"></a><span data-ttu-id="1b0d6-168">variant로서의 측정값</span><span class="sxs-lookup"><span data-stu-id="1b0d6-168">Measures as variants</span></span>  
 <span data-ttu-id="1b0d6-169">다차원 모델의 측정값은 variant입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-169">Measures in multidimensional models are variants.</span></span> <span data-ttu-id="1b0d6-170">즉, 이 측정값은 강력한 형식이 아니며 다른 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-170">This means the measures are not strongly typed and can have different data types.</span></span> <span data-ttu-id="1b0d6-171">예를 들어 아래 이미지에서 Financial Reporting 테이블의 Amount 측정값은 기본적으로 통화 데이터 형식 이지만, 문자열 데이터 형식인 "통계 계정"의 합계에 대 한 문자열 값 "NA"도 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-171">For example, in the image below, the Amount measure in the Financial Reporting table by default is Currency data type, but also has a string value "NA" for the sub-total of "Statistical Accounts", which is String data type.</span></span> <span data-ttu-id="1b0d6-172">파워 뷰에서는 일부 측정값을 variant로 인식하고 다른 시각화 유형으로 올바른 값 및 서식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-172">Power View recognizes certain measures as variants and shows the correct values and formatting in the different visualizations.</span></span>  
  
 <span data-ttu-id="1b0d6-173">**variant로서의 측정값**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-173">**Measure as variant**</span></span>  
  
 <span data-ttu-id="1b0d6-174">![파워 뷰의 집계할 수 없는 계층](../media/daxmd-nonaggrattrib.gif "파워 뷰의 집계할 수 없는 계층")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-174">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
### <a name="implicit-measures"></a><span data-ttu-id="1b0d6-175">암시적 측정값</span><span class="sxs-lookup"><span data-stu-id="1b0d6-175">Implicit measures</span></span>  
 <span data-ttu-id="1b0d6-176">테이블 형식 모델에서는 사용자가 필드에 count, sum 또는 average와 같은 *암시적* 측정값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-176">Tabular models provide users the ability to create *implicit* measures such as count, sum, or average on fields.</span></span> <span data-ttu-id="1b0d6-177">다차원 모델의 경우에는 차원 특성 데이터가 다른 방식으로 저장되므로 암시적 측정값을 쿼리하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-177">For multidimensional models, because dimension attribute data is stored is stored differently, querying implicit measures can take a long time.</span></span> <span data-ttu-id="1b0d6-178">따라서 Powe View에서는 암시적 측정값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-178">Because of this, implicit measures are not available in Power View.</span></span>  
  
## <a name="dimensions-attributes-and-hierarchies"></a><span data-ttu-id="1b0d6-179">차원, 특성 및 계층</span><span class="sxs-lookup"><span data-stu-id="1b0d6-179">Dimensions, attributes, and hierarchies</span></span>  
 <span data-ttu-id="1b0d6-180">큐브 차원은 테이블 형식 메타데이터에서 테이블로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-180">Cube dimensions are exposed as tables in tabular metadata.</span></span> <span data-ttu-id="1b0d6-181">파워 뷰 필드 목록에서 차원 특성은 표시 폴더 내에 열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-181">In the Power View Field List, dimension attributes are shown as columns within display folders.</span></span>  <span data-ttu-id="1b0d6-182">Customer 차원의 Birth Date 특성과 같이 AttributeHierarchyEnabled 속성이 false로 설정된 차원 특성이나 AttributeHierarchyVisible 속성이 false로 설정된 차원 특성은 파워 뷰 필드 목록에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-182">The dimension attributes that have the AttributeHierarchyEnabled property set to false; for example: Birth Date attribute in Customer dimension, or AttributeHierarchyVisible property set to false will not appear in the Power View Field List.</span></span> <span data-ttu-id="1b0d6-183">여러 수준 계층 또는 사용자 계층(예: Customer 차원의 Customer Geography)은 파워 뷰 필드 목록에서 계층으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-183">Multi-level hierarchies or user hierarchies; for example Customer Geography in the Customer dimension, are exposed as hierarchies in the Power View Field List.</span></span> <span data-ttu-id="1b0d6-184">차원 특성의 숨겨진 UnknownMember는 DAX 쿼리와 파워 뷰에서는 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-184">Hidden UnknownMembers of a dimension attribute are exposed in DAX Queries and in Power View.</span></span>  
  
 <span data-ttu-id="1b0d6-185">**SSDT(SQL Server Data Tools) 및 파워 뷰 필드 목록의 차원, 특성 및 계층**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-185">**Dimension, attributes and hierarchies in SQL Server Data Tools (SSDT) and Power View Field List**</span></span>  
  
 <span data-ttu-id="1b0d6-186">![SSDT 및 Power View 필드 목록의 차원](../media/daxmd-ssdt-dimensions.gif "SSDT 및 Power View 필드 목록의 차원")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-186">![Dimensions in SSDT and in Power View Field List](../media/daxmd-ssdt-dimensions.gif "Dimensions in SSDT and in Power View Field List")</span></span>  
  
### <a name="dimension-attribute-type"></a><span data-ttu-id="1b0d6-187">차원 특성 유형</span><span class="sxs-lookup"><span data-stu-id="1b0d6-187">Dimension attribute type</span></span>  
 <span data-ttu-id="1b0d6-188">다차원 모델에서는 차원 특성을 특정 차원 특성 유형과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-188">Multidimensional models support associating dimension attributes with specific dimension attribute types.</span></span> <span data-ttu-id="1b0d6-189">아래 이미지에서는 City, State-Province, Country 및 Postal Code 차원 특성에 지리 유형이 연결된 Geography 차원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-189">The image below shows the Geography dimension where the City, State-Province, Country and Postal Code dimension attributes have geography types associated with them.</span></span> <span data-ttu-id="1b0d6-190">이러한 차원 특성은 테이블 형식 메타데이터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-190">These are exposed in the tabular metadata.</span></span> <span data-ttu-id="1b0d6-191">파워 뷰에서는 메타데이터를 인식하므로 사용자가 지도 시각화를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-191">Power View recognizes the metadata enabling users to create map visualizations.</span></span> <span data-ttu-id="1b0d6-192">이는 파워 뷰 필드 목록에서 Geography 테이블의 City, Country, Postal Code 및 State-Province 열 옆에 지도 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-192">This is indicated by the map icon next to the City, Country, Postal Code and State-Province columns in the Geography table in the Power View Field List.</span></span>  
  
 <span data-ttu-id="1b0d6-193">**SSDT 및 파워 뷰 필드 목록의 차원 특성 지리 유형**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-193">**Dimension attribute geography types in SSDT and Power View Field List**</span></span>  
  
 <span data-ttu-id="1b0d6-194">![차원 특성 유형 geography 형식](../media/daxmd-ssdt-attribute-geog-types.gif "차원 특성 유형 geography 형식")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-194">![Dimension attribute geography types](../media/daxmd-ssdt-attribute-geog-types.gif "Dimension attribute geography types")</span></span>  
  
### <a name="dimension-calculated-members"></a><span data-ttu-id="1b0d6-195">차원 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="1b0d6-195">Dimension calculated members</span></span>  
 <span data-ttu-id="1b0d6-196">다차원 모델에서는 단일 실제 멤버가 있는 모든 항목의 자식에 대해 계산 멤버를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-196">Multidimensional models support calculated members for child of All with a single real member.</span></span> <span data-ttu-id="1b0d6-197">이러한 유형의 계산 멤버를 표시할 때의 추가 제약 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-197">Additional constraints while exposing this type of calculated member are:</span></span>  
  
-   <span data-ttu-id="1b0d6-198">차원에 둘 이상의 특성이 있는 경우 단일 실제 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-198">Must be a single real member when the dimension has more than one attribute.</span></span>  
  
-   <span data-ttu-id="1b0d6-199">계산 멤버를 포함하는 특성이 유일한 특성이 아닐 경우 이 특성은 차원의 키 특성일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-199">An attribute containing calculated members cannot be the key attribute of the dimension unless it is the only attribute.</span></span>  
  
-   <span data-ttu-id="1b0d6-200">계산 멤버를 포함하는 특성은 부모-자식 특성일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-200">An attribute containing calculated members cannot be a parent-child attribute.</span></span>  
  
 <span data-ttu-id="1b0d6-201">사용자 계층의 계산 멤버는 파워 뷰에서 표시되지만, 최종 사용자는 여전히 사용자 계층의 계산 멤버를 포함하는 큐브에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-201">Calculated members of user hierarchies are not exposed in Power View; however, end-users will still be able to connect to a cube containing calculated members on user hierarchies.</span></span>  
  
 <span data-ttu-id="1b0d6-202">아래 이미지에서는 Date 차원의 "회계 날짜 계산" 차원 특성에 대 한 시간 인텔리전스 계산 멤버를 포함 하는 큐브에 대 한 파워 뷰 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-202">The image below shows a Power View report for a cube that contains time-intelligence calculated members on dimension attribute "Fiscal Date Calculations" in the Date dimension.</span></span>  
  
 <span data-ttu-id="1b0d6-203">**계산 멤버가 있는 파워 뷰 보고서**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-203">**Power View report with calculated members**</span></span>  
  
 <span data-ttu-id="1b0d6-204">![Power View의 계산 구성원](../media/daxmd-calcmembersinpowerview.gif "Power View의 계산 구성원")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-204">![Calculated members in Power View](../media/daxmd-calcmembersinpowerview.gif "Calculated members in Power View")</span></span>  
  
### <a name="default-members"></a><span data-ttu-id="1b0d6-205">기본 멤버</span><span class="sxs-lookup"><span data-stu-id="1b0d6-205">Default members</span></span>  
 <span data-ttu-id="1b0d6-206">다차원 모델에서는 차원 특성의 기본 멤버를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-206">Multidimensional models support default members for dimension attributes.</span></span> <span data-ttu-id="1b0d6-207">기본 멤버는 Analysis Services에서 쿼리를 위해 데이터를 집계할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-207">The default member is used by Analysis Services when aggregating data for a query.</span></span> <span data-ttu-id="1b0d6-208">차원 특성의 기본 멤버는 테이블 형식 메타데이터에서 해당하는 열의 기본 값 또는 필터로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-208">The default member of a dimension attribute is exposed as default value or filter for the corresponding column in the tabular metadata.</span></span>  
  
 <span data-ttu-id="1b0d6-209">특성이 적용될 경우 파워 뷰는 Excel 피벗 테이블과 거의 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-209">Power View behaves much the same as Excel PivotTables when attributes are applied.</span></span> <span data-ttu-id="1b0d6-210">사용자가 기본값을 포함하는 파워 뷰 시각화 유형(테이블, 행렬 또는 차트)에 열을 추가할 경우 해당 기본값이 적용되지 않고 사용 가능한 모든 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-210">When a user adds a column to a Power View visualization (table, matrix, or chart) that contains a default value, the default value will not be applied and all available values are shown.</span></span> <span data-ttu-id="1b0d6-211">사용자가 필터에 열을 추가할 경우에는 기본값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-211">If the user adds the column to Filters, the default value will be applied.</span></span>  
  
### <a name="dimension-security"></a><span data-ttu-id="1b0d6-212">차원 보안</span><span class="sxs-lookup"><span data-stu-id="1b0d6-212">Dimension security</span></span>  
 <span data-ttu-id="1b0d6-213">다차원 모델에서는 역할을 통해 차원 및 셀 수준 보안을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-213">Multidimensional models support dimension and cell level security through roles.</span></span> <span data-ttu-id="1b0d6-214">파워 뷰를 사용하여 큐브에 연결하는 사용자는 인증 후 적절한 사용 권한이 있는지 여부가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-214">A user connecting to a cube by using Power View is authenticated and evaluated for appropriate permissions.</span></span> <span data-ttu-id="1b0d6-215">차원 보안이 적용된 경우에는 해당 차원 멤버가 파워 뷰에서 사용자에게 표시되지 않고, 사용자에게 일부 셀이 제한된 셀 보안 사용 권한이 정의된 경우에는 해당 사용자가 파워 뷰를 사용하여 큐브에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-215">When dimension security is applied, the respective dimension members will not be seen by the user in Power View; however if a user has a cell security permission defined where certain cells are restricted, then that user cannot connect to the cube with Power View.</span></span> <span data-ttu-id="1b0d6-216">집계 데이터의 일부가 보안 데이터에서 계산된 경우 사용자가 집계 데이터를 볼 수 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-216">In some cases, users can see aggregate data when portions of that data are calculated from secured data.</span></span>  
  
### <a name="non-aggregatable-attributeshierarchies"></a><span data-ttu-id="1b0d6-217">집계할 수 없는 특성/계층</span><span class="sxs-lookup"><span data-stu-id="1b0d6-217">Non-aggregatable attributes/hierarchies</span></span>  
 <span data-ttu-id="1b0d6-218">다차원 모델에서는 차원의 특성에 대해 IsAggregatable 속성이 false로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-218">In a multidimensional model, attributes of a dimension can have the IsAggregatable property set to false.</span></span> <span data-ttu-id="1b0d6-219">이는 클라이언트 애플리케이션에서 데이터를 쿼리할 때 계층 간에 데이터를 집계하지 않도록 모델 작성자가 지정했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-219">This means the model author has specified client applications should not aggregate the data across hierarchies (attribute or multi-level) when they query the data.</span></span> <span data-ttu-id="1b0d6-220">파워 뷰에서 이 차원 특성은 부분합을 사용할 수 없는 열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-220">In Power View, this dimension attribute is exposed as a column for which sub-totals are not available.</span></span> <span data-ttu-id="1b0d6-221">아래 이미지에서는 집계할 수 없는 계층의 예인 Accounts를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-221">In the image below, you can see an example of a non-aggregatable hierarchy: Accounts.</span></span> <span data-ttu-id="1b0d6-222">Accounts 부모-자식 계층의 최상위 수준은 집계할 수 없는 반면 다른 수준은 집계할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-222">The top-most level of the Accounts parent-child hierarchy is non-aggregatable while other levels are aggregatable.</span></span> <span data-ttu-id="1b0d6-223">Accounts 계층의 행렬 시각화(처음 두 수준)에서는 Account Level 02에 대한 부분합이 표시되지만 최상위 수준인 Account Level 01에 대한 부분합은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-223">In a matrix visualization of the Accounts hierarchy (first two levels), you see sub-totals for Account Level 02 but not for the top-most level, Account Level 01.</span></span>  
  
 <span data-ttu-id="1b0d6-224">**파워 뷰의 집계할 수 없는 계층**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-224">**Non-aggregatable hierarchy in Power View**</span></span>  
  
 <span data-ttu-id="1b0d6-225">![파워 뷰의 집계할 수 없는 계층](../media/daxmd-nonaggrattrib.gif "파워 뷰의 집계할 수 없는 계층")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-225">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
## <a name="images"></a><span data-ttu-id="1b0d6-226">이미지</span><span class="sxs-lookup"><span data-stu-id="1b0d6-226">Images</span></span>  
 <span data-ttu-id="1b0d6-227">파워 뷰에서는 이미지를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-227">Power View provides the ability to render images.</span></span> <span data-ttu-id="1b0d6-228">다차원 모델에서 파워 뷰에 이미지를 제공하는 방법 중 하나는 이미지의 URL(Uniform Resource Locator)을 포함하는 열을 표시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-228">In multidimensional models, one of the ways you can provide images to Power View is to expose columns containing URLs (Uniform Resource Locator) of the images.</span></span> <span data-ttu-id="1b0d6-229">이 릴리스의 Analysis Services에서는 ImageURL 형식으로 차원 특성의 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-229">With this release, Analysis Services supports tagging dimension attributes as type ImageURL.</span></span> <span data-ttu-id="1b0d6-230">그런 다음 이 데이터 형식이 테이블 형식 메타데이터에 포함되어 파워 뷰에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-230">This data type is then provided to Power View in the tabular metadata.</span></span> <span data-ttu-id="1b0d6-231">그러면 파워 뷰는 시각화 내에서 URL에 지정된 이미지를 다운로드하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-231">Power View can then download and display the images specified in the URLs within visualizations.</span></span>  
  
 <span data-ttu-id="1b0d6-232">**SSDT의 ImageURL 차원 특성 유형**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-232">**ImageURL dimension attribute type in SSDT**</span></span>  
  
 <span data-ttu-id="1b0d6-233">![차원 특성 속성](../media/daxmd-dimattribute-properties.gif "차원 특성 속성")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-233">![Dimension attribute properties](../media/daxmd-dimattribute-properties.gif "Dimension attribute properties")</span></span>  
  
## <a name="parent-child-hierarchies"></a><span data-ttu-id="1b0d6-234">부모-자식 계층</span><span class="sxs-lookup"><span data-stu-id="1b0d6-234">Parent-child hierarchies</span></span>  
 <span data-ttu-id="1b0d6-235">다차원 모델은 부모-자식 계층을 지원하며 이 계층은 테이블 형식 메타데이터에 계층으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-235">Multidimensional models support parent-child hierarchies, which are exposed as a hierarchy in the tabular metadata.</span></span> <span data-ttu-id="1b0d6-236">부모-자식 계층의 각 수준은 숨겨진 열로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-236">Each level of the parent-child hierarchy is exposed as a hidden column.</span></span> <span data-ttu-id="1b0d6-237">부모-자식 차원의 키 특성은 테이블 형식 메타데이터에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-237">The key attribute of the parent-child dimension is not exposed in the tabular metadata.</span></span>  
  
 <span data-ttu-id="1b0d6-238">**파워 뷰의 부모-자식 계층**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-238">**Parent-child hierarchies in Power View**</span></span>  
  
 <span data-ttu-id="1b0d6-239">![부모-자식 계층](../media/daxmd-ssdt-hierarchies.gif "부모-자식 계층")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-239">![Parent-child hierarchies](../media/daxmd-ssdt-hierarchies.gif "Parent-child hierarchies")</span></span>  
  
## <a name="perspectives-and-translations"></a><span data-ttu-id="1b0d6-240">큐브 뷰 및 번역</span><span class="sxs-lookup"><span data-stu-id="1b0d6-240">Perspectives and translations</span></span>  
 <span data-ttu-id="1b0d6-241">큐브 뷰는 일부 차원 또는 측정값 그룹만 클라이언트 도구에 표시되는 큐브의 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-241">Perspectives are views of cubes where only certain dimensions or measure groups are visible in client tools.</span></span> <span data-ttu-id="1b0d6-242">큐브 뷰의 이름은 큐브 연결 문자열 속성에 대한 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-242">You can specify a perspective name as a value to the Cube connection string property.</span></span> <span data-ttu-id="1b0d6-243">예를 들어 다음 연결 문자열에서 ' 직접 판매 '는 다차원 모델의 큐브 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-243">For example, in the following connection string, 'Direct Sales' is a perspective in the multidimensional model:</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Direct Sales'`  
  
 <span data-ttu-id="1b0d6-244">큐브에서는 모델 내의 다양한 언어에 대해 메타데이터 및 데이터 번역이 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-244">Cubes can have metadata and data translations specified for various Languages within the model.</span></span> <span data-ttu-id="1b0d6-245">번역 (데이터 및 메타 데이터)을 보려면 아래와 같이 .RSDS 파일에서 연결 문자열에 선택적 "로캘 식별자" 속성을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-245">In order to see the translations (data and metadata) you need to add the optional "Locale Identifier" property to the connection string in the RSDS file as shown below.</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Adventure Works'; Locale Identifier=3084`  
  
 <span data-ttu-id="1b0d6-246">파워 뷰에서 로캘 ID가 있는 .rsds 파일로 다차원 모델에 연결할 때 해당 번역이 큐브에 포함되어 있으면 파워 뷰에 번역이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-246">When Power View connects to a multidimensional model with an .rsds file that has a Locale Identifier, and if a corresponding translation is contained in the cube, users will see the translations in Power View.</span></span>  
  
 <span data-ttu-id="1b0d6-247">자세한 내용은 [Create a Report Data Source](create-a-report-data-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-247">For more information, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
## <a name="power-view-pinned-filters"></a><span data-ttu-id="1b0d6-248">파워 뷰의 고정된 필터</span><span class="sxs-lookup"><span data-stu-id="1b0d6-248">Power View pinned filters</span></span>  
 <span data-ttu-id="1b0d6-249">파워 뷰 보고서에는 여러 뷰가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-249">Power View reports can contain multiple views.</span></span> <span data-ttu-id="1b0d6-250">이 릴리스에서는 테이블 형식 모델과 다차원 모델 모두에 대해 *필터 고정* 기능을 사용하여 보고서의 모든 뷰에 적용되는 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-250">With this release, the *Pin Filter* feature for both tabular and multidimensional models provides the ability to create filters that apply across all views in a report.</span></span> <span data-ttu-id="1b0d6-251">아래 이미지에서는 뷰 필터에 대한 필터 고정 토글 단추를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-251">The image below shows the Pin filter toggle button for a view filter.</span></span> <span data-ttu-id="1b0d6-252">기본적으로 뷰 필터는 고정 해제되어 있고 해당 뷰에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-252">By default, a view filter is unpinned and applies only to that view.</span></span> <span data-ttu-id="1b0d6-253">뷰 필터 고정은 모든 뷰에 적용되며, 뷰 필터를 고정 해제하면 다른 뷰에서 해당 필터가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-253">Pinning a view filter applies it to all views; unpinning it removes it from other views.</span></span>  
  
 <span data-ttu-id="1b0d6-254">**고정된 필터**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-254">**Pinned Filters**</span></span>  
  
 <span data-ttu-id="1b0d6-255">![고정된 필터](../media/daxmd-pinnedfilterinpowerview.gif "고정된 필터")</span><span class="sxs-lookup"><span data-stu-id="1b0d6-255">![Pinned Filter](../media/daxmd-pinnedfilterinpowerview.gif "Pinned Filter")</span></span>  
  
## <a name="unsupported-features"></a><span data-ttu-id="1b0d6-256">지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="1b0d6-256">Unsupported features</span></span>  
 <span data-ttu-id="1b0d6-257">**Excel 2013의 파워 뷰** -다차원 모델에 대 한 보고서 연결 및 만들기를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-257">**Power View in Excel 2013** - does not support connecting to and creating reports for multidimensional models.</span></span> <span data-ttu-id="1b0d6-258">다차원 모델용 Power View는 브라우저 기반 Power View 클라이언트만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-258">Power View for multidimensional models supports browser based Power View clients only.</span></span>  
  
 <span data-ttu-id="1b0d6-259">**동작** - 다차원 모델에 대한 파워 뷰 보고서나 DAX 쿼리에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-259">**Actions** - are not supported in Power View reports or in DAX queries against a multidimensional model.</span></span>  
  
 <span data-ttu-id="1b0d6-260">**명명된 집합** - 다차원 모델에서는 다차원 모델에 대한 파워 뷰 또는 DAX 쿼리에서 명명된 집합이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-260">**Named sets** - in multidimensional models, are not supported in Power View or in DAX queries against a multidimensional model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b0d6-261">동작과 명명된 집합이 지원되지 않더라도 사용자는 파워 뷰를 사용하여 다차원 모델에 연결하고 이를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-261">Unsupported Actions and Named sets do not prevent users from connecting to and exploring multidimensional models using Power View.</span></span>  
  
 <span data-ttu-id="1b0d6-262">**셀 수준 보안** -파워 뷰 보고서에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-262">**Cell level security** - is not supported in Power View reports.</span></span>  
  
## <a name="csdlbi-annotations"></a><span data-ttu-id="1b0d6-263">CSDLBI 주석</span><span class="sxs-lookup"><span data-stu-id="1b0d6-263">CSDLBI Annotations</span></span>  
 <span data-ttu-id="1b0d6-264">다차원 큐브 메타데이터는 CSDLBI(비즈니스 인텔리전스 포함 개념 스키마 정의 언어) 주석을 사용하여 EDM(엔터티 데이터 모델) 기반 개념 모델로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-264">Multidimensional cube metadata is exposed as an Entity Data Model (EDM) based conceptual model by Conceptual Schema Definition Language with Business Intelligence annotations (CSDLBI).</span></span>  
  
 <span data-ttu-id="1b0d6-265">Analysis Services 인스턴스로 DISCOVER_CSDL_METADATA 요청이 보내질 때 다차원 메타데이터는 CSDLBI 문서, 즉 CSDL 출력에서 테이블 형식 모델 네임스페이스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-265">Multidimensional metadata is represented as a tabular model namespace in a CSDLBI document, or CSDL out, when a DISCOVER_CSDL_METADATA request is sent to the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="1b0d6-266">**DISCOVER_CSDL_METADATA 요청 예제**</span><span class="sxs-lookup"><span data-stu-id="1b0d6-266">**Sample DISCOVER_CSDL_METADATA request**</span></span>  
  
```  
<Envelopexmlns="http://schemas.xmlsoap.org/soap/envelope/">  
   <Body>  
      <Discoverxmlns="urn:schemas-microsoft-com:xml-analysis">  
         <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
              <CATALOG_NAME>"catalogname"<CATALOG_NAME>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
            <PropertyList>  
            </PropertyList>  
         </Properties>  
      </Discover>  
   </Body>  
</Envelope>  
  
```  
  
 <span data-ttu-id="1b0d6-267">DISCOVER_CSDL_METADATA 요청에는 다음과 같은 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-267">DISCOVER_CSDL_METADATA request has the following restrictions:</span></span>  
  
|<span data-ttu-id="1b0d6-268">Name</span><span class="sxs-lookup"><span data-stu-id="1b0d6-268">Name</span></span>|<span data-ttu-id="1b0d6-269">필수</span><span class="sxs-lookup"><span data-stu-id="1b0d6-269">Required</span></span>|<span data-ttu-id="1b0d6-270">설명</span><span class="sxs-lookup"><span data-stu-id="1b0d6-270">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="1b0d6-271">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="1b0d6-271">CATALOG_NAME</span></span>|<span data-ttu-id="1b0d6-272">Yes</span><span class="sxs-lookup"><span data-stu-id="1b0d6-272">Yes</span></span>|<span data-ttu-id="1b0d6-273">카탈로그\데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-273">The catalog\database name.</span></span>|  
|<span data-ttu-id="1b0d6-274">PERSPECTIVE_NAME</span><span class="sxs-lookup"><span data-stu-id="1b0d6-274">PERSPECTIVE_NAME</span></span>|<span data-ttu-id="1b0d6-275">큐브에 둘 이상의 큐브 뷰가 포함된 경우 필수,</span><span class="sxs-lookup"><span data-stu-id="1b0d6-275">Yes, if the cube contains more than one perspective.</span></span> <span data-ttu-id="1b0d6-276">큐브가 하나뿐이고 기본 큐브 뷰가 있는 경우 선택적</span><span class="sxs-lookup"><span data-stu-id="1b0d6-276">Optional if there is only one cube or there is a default perspective.</span></span>|<span data-ttu-id="1b0d6-277">다차원 데이터베이스의 큐브 이름 또는 큐브 뷰 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-277">The cube name or perspective name in the multidimensional database.</span></span>|  
|<span data-ttu-id="1b0d6-278">VERSION</span><span class="sxs-lookup"><span data-stu-id="1b0d6-278">VERSION</span></span>|<span data-ttu-id="1b0d6-279">Yes</span><span class="sxs-lookup"><span data-stu-id="1b0d6-279">Yes</span></span>|<span data-ttu-id="1b0d6-280">클라이언트가 요청한 CSDL 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-280">CSDL version requested by client.</span></span> <span data-ttu-id="1b0d6-281">다차원 기능 및 구문은 버전 2.0에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-281">Multidimensional features and constructs are supported in version 2.0.</span></span>|  
  
 <span data-ttu-id="1b0d6-282">반환되는 CSDL 출력 문서에서는 모델을 네임스페이스, 포함 엔터티, 연결 및 속성으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-282">The return CSDL out document represents the model as a namespace, containing entities, associations, and properties.</span></span>  
  
 <span data-ttu-id="1b0d6-283">테이블 형식 모델의 CSDLBI 주석에 대한 자세한 내용은 MSDN의 [CSDL용 BI 주석에 대한 기술 참조](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) 및 [\[MS-CSDLBI\]: 비즈니스 인텔리전스 주석을 사용하는 개념 스키마 정의 파일 형식](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-283">For more detailed information about CSDLBI annotations for tabular models, see [Technical Reference for BI Annotations to CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) on MSDN, and [\[MS-CSDLBI\]: Conceptual Schema Definitions File Format with Business Intelligence Annotations](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx).</span></span>  
  
## <a name="client-help-on-officecom"></a><span data-ttu-id="1b0d6-284">Office.com의 클라이언트 도움말</span><span class="sxs-lookup"><span data-stu-id="1b0d6-284">Client Help on Office.com</span></span>  
 <span data-ttu-id="1b0d6-285">Office.com에서 제공되는 다음 문서는 파워 뷰에서 다차원 모델 개체가 나타나는 방식과 예제 보고서를 만드는 방법을 배우는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b0d6-285">The following articles are provided on Office.com to help users learn about how Multidimensional Model objects appear in Power View and how to create a sample report:</span></span>  
  
 [<span data-ttu-id="1b0d6-286">파워 뷰의 다차원 모델 개체 이해</span><span class="sxs-lookup"><span data-stu-id="1b0d6-286">Understanding Multidimensional Model Objects in Power View</span></span>](https://office.microsoft.com/excel-help/understanding-multidimensional-model-objects-in-power-view-HA104018589.aspx)  
  
 [<span data-ttu-id="1b0d6-287">파워 뷰를 사용하여 Adventure Works 다차원 모델 탐색</span><span class="sxs-lookup"><span data-stu-id="1b0d6-287">Explore the Adventure Works Multidimensional Model by using Power View</span></span>](https://office.microsoft.com/excel-help/explore-the-adventure-works-multidimensional-model-by-using-power-view-HA104046830.aspx)  
  
