---
title: 다 대 다 관계 및 다 대 다 관계 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- many-to-many relationships [Analysis Services]
ms.assetid: edb5f61a-a581-467a-a367-134b7f9b849f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1cd5d46ce07ff8eb6a3893c0dac261797c6ef19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660167"
---
# <a name="define-a-many-to-many-relationship-and-many-to-many-relationship-properties"></a><span data-ttu-id="422b8-102">다 대 다 관계 및 다 대 다 관계 속성 정의</span><span class="sxs-lookup"><span data-stu-id="422b8-102">Define a Many-to-Many Relationship and Many-to-Many Relationship Properties</span></span>
  <span data-ttu-id="422b8-103">이 항목에서는 Analysis Services의 다 대 다 차원에 대해 설명하고 이러한 차원을 사용하는 경우와 만드는 방법도 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-103">This topic explains many-to-many dimensions in Analysis Services, including when to use them and how to create them.</span></span>  
  
## <a name="introduction"></a><span data-ttu-id="422b8-104">소개</span><span class="sxs-lookup"><span data-stu-id="422b8-104">Introduction</span></span>  
 <span data-ttu-id="422b8-105">Analysis Services는 다 대 다 차원을 지원하여 표준 별모양 스키마에서 설명할 수 있는 것보다 복잡한 분석을 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-105">Analysis Services supports many-to-many dimensions, allowing for more complex analytics than what can be described in a classic star schema.</span></span> <span data-ttu-id="422b8-106">표준 별모양 스키마에서는 모든 차원이 팩트 테이블과 일 대 다 관계를 맺고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-106">In a classic star schema, all dimensions have a one-to-many relationship with a fact table.</span></span> <span data-ttu-id="422b8-107">각 팩트는 하나의 차원 멤버에 조인되고 단일 차원 멤버는 여러 팩트와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-107">Each fact joins to one dimension member; a single dimension member is associated with many facts.</span></span>  
  
 <span data-ttu-id="422b8-108">다 대 다는 팩트(계정 잔액 등)이 동일한 차원의 여러 멤버와 연결될 수 있도록 하여(공동 계정의 잔액이 공동 계정의 예금주 둘 이상에 할당될 수 있음) 이러한 모델링 제한을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-108">Many-to-many removes this modeling restriction by enabling a fact (such as an account balance) to be associated with multiple members of the same dimension (the balance of a joint account can be attributed to two or more owners of a joint account).</span></span>  
  
 <span data-ttu-id="422b8-109">개념적으로 Analysis Services의 다 대 다 차원 관계는 관계형 모델의 다 대 다 관계와 동일하며 같은 종류의 시나리오를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-109">Conceptually, a many-to-many dimensional relationship in Analysis Services is equivalent to many-to-many relationships in a relational model, supporting the same kinds of scenarios.</span></span> <span data-ttu-id="422b8-110">다 대 다의 일반적인 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-110">Common examples of many-to-many include:</span></span>  
  
-   <span data-ttu-id="422b8-111">학생들이 많은 과목에 등록되고 각 과목에 많은 학생이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-111">Students are enrolled in many courses; each course has many students.</span></span>  
  
-   <span data-ttu-id="422b8-112">의사들에게 많은 환자가 있고 환자들에게 많은 의사가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-112">Doctors have many patients; patients have many doctors.</span></span>  
  
-   <span data-ttu-id="422b8-113">고객들이 많은 은행 계정을 갖고 있고 은행 계정들이 둘 이상의 고객에게 속할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-113">Customers have many bank accounts; bank accounts might belong to more than one customer.</span></span>  
  
-   <span data-ttu-id="422b8-114">Adventure Works에서는 많은 고객이 제품을 구매하는 다양한 이유를 갖고 있으며 판매 이유가 많은 주문과 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-114">In Adventure Works, many customers have many reasons for ordering a product, and a sales reason can be associated with many orders.</span></span>  
  
 <span data-ttu-id="422b8-115">분석 측면에서 다 대 다 관계의 이점은 차원 관계에 비해 개수나 합계를 정확히 표현한다는 것입니다. 이는 일반적으로 특정 차원 멤버에 대한 계산을 수행할 때 중복 개수를 제거하여 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-115">Analytically, the problem that a many-to-many relationship solves is accurate representation of a count or sum relative to the dimensional relationship (usually by eliminating double-counts when performing calculations for a specific dimension member).</span></span> <span data-ttu-id="422b8-116">이 점을 명확히 하기 위해</span><span class="sxs-lookup"><span data-stu-id="422b8-116">An example is necessary to clarify this point.</span></span> <span data-ttu-id="422b8-117">둘 이상의 범주에 속하는 제품이나 서비스를 예로 들어보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-117">Consider a product or service that belongs to more than one category.</span></span> <span data-ttu-id="422b8-118">범주별로 서비스 수를 세는 경우 두 범주에 모두 속하는 서비스가 각 범주에 포함되게 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-118">If you were counting the number of services by category, you would want a service belonging to both categories to be included in each one.</span></span> <span data-ttu-id="422b8-119">이와 동시에 제공하는 서비스의 수를 과장하지는 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-119">At the same time, you would not want to overstate the number of services that you provide.</span></span> <span data-ttu-id="422b8-120">다 대 다 차원 관계를 지정하면 범주나 서비스별로 쿼리할 때 올바른 결과를 얻을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-120">By specifying the many-to-many dimensional relationship, you are more likely to get the correct results back when querying by category or by service.</span></span> <span data-ttu-id="422b8-121">그러나 이렇게 되려면 항상 철저한 테스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-121">However, thorough testing is always necessary to ensure that this is the case.</span></span>  
  
 <span data-ttu-id="422b8-122">구조적 측면에서 볼 때 다 대 다 차원 관계를 만드는 것은 관계형 데이터 모델에서 다 대 다를 만들 수 있는 방법과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-122">Structurally, creating a many-to-many dimensional relationship is similar to how you might create many-to-many in a relational data model.</span></span> <span data-ttu-id="422b8-123">관계형 모델이 *접합 테이블* 을 사용하여 행 연결을 저장하는 반면에 다차원 모델은 *중간 측정값 그룹*을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-123">Whereas a relational model uses a *junction table* to store row associations, a multidimensional model uses an *intermediate measure group*.</span></span> <span data-ttu-id="422b8-124">중간 측정값 그룹은 여러 차원의 멤버를 매핑하는 테이블을 나타내는 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-124">Intermediate measure group is the term we use to refer to a table that maps members from different dimensions.</span></span>  
  
 <span data-ttu-id="422b8-125">시각적으로 다 대 다 차원 관계는 큐브 다이어그램에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-125">Visually, a many-to-many dimensional relationship is not indicated in a cube diagram.</span></span> <span data-ttu-id="422b8-126">대신 차원 용도 탭을 사용하여 모델에서 다 대 다 관계를 신속하게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-126">Instead, use the Dimension Usage tab to quickly identify any many-to-many relationships in a model.</span></span> <span data-ttu-id="422b8-127">다 대 다 관계는 다음 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-127">A many-to-many relationship is indicated by the following icon.</span></span>  
  
 <span data-ttu-id="422b8-128">![차원 용도의 다 대 다 아이콘](../media/ssas-m2m-icondimusage.png "차원 용도의 다 대 다 아이콘")</span><span class="sxs-lookup"><span data-stu-id="422b8-128">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
 <span data-ttu-id="422b8-129">단추를 클릭하여 관계 정의 대화 상자를 연 다음 관계 유형이 다 대 다인지 확인하고 관계에서 사용되는 중간 측정값 그룹을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-129">Click the button to open the Define Relationship dialog box to verify the relationship type is many-to-many, and to view which intermediate measure group is used in the relationship.</span></span>  
  
 <span data-ttu-id="422b8-130">![차원 사용의 관계 정의 단추](../media/ssas-m2m-btndimusage.png "차원 사용의 관계 정의 단추")</span><span class="sxs-lookup"><span data-stu-id="422b8-130">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
 <span data-ttu-id="422b8-131">이후의 섹션들에서는 다 대 다 차원을 설정하고 모엘 동작을 테스트하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-131">In subsequent sections, you will learn how to set up a many-to-many dimension and test model behaviors.</span></span> <span data-ttu-id="422b8-132">먼저 추가 정보를 검토하거나 자습서를 살펴보려면 이 문서 끝에 있는 **자세한 정보** 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="422b8-132">If you would rather review additional information or try tutorials first, see **Learn More** at the end of this article.</span></span>  
  
## <a name="create-a-many-to-many-dimension"></a><span data-ttu-id="422b8-133">다 대 다 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="422b8-133">Create a many-to-many dimension</span></span>  
 <span data-ttu-id="422b8-134">간단한 다 대 다 관계에는 다 대 다 카디널리티가 있는 두 차원, 멤버 연결을 저장하기 위한 중간 측정값 그룹 및 총 매출 합계, 은행 계정 잔액 등의 측정 가능한 데이터가 포함된 팩트 측정값 그룹이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-134">A simple many-to-many relationship includes two dimensions having a many-to-many cardinality, an intermediate measure group for storing member associations, and a fact measure group containing measurable data, such as sum of total sales or the balance of a bank account.</span></span>  
  
 <span data-ttu-id="422b8-135">다 대 다 관계의 차원은 DSV에 대응하는 테이블이 있을 수도 있으며, 이 경우 모델의 각 차원이 데이터 원본의 기존 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-135">Dimensions in a many-to-many relationship might have correspondent tables in the DSV, where each dimension in the model is based on an existing table in a data source.</span></span> <span data-ttu-id="422b8-136">반대로 모델의 차원은 DSV에 있는 더 적거나 서로 다른 물리적 테이블에서 파생될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-136">Conversely, the dimensions in your model might derive from fewer or different physical tables in the DSV.</span></span> <span data-ttu-id="422b8-137">Sales Reasons 및 Sales Orders를 적절한 예로 사용하여 Adventure Works 예제 큐브에서는 DSV에서 대응하는 물리적 항목 없이 모델 전용 데이터 구조로 존재하는 차원을 사용하는 다 대 다 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-137">Using Sales Reasons and Sales Orders as a case in point, the Adventure Works sample cube demonstrates a many-to-many relationship using dimensions that exist as model-only data structures, without physical counterparts in the DSV.</span></span> <span data-ttu-id="422b8-138">Sales Order 차원은 기본 데이터 원본의 차원 테이블이 아니라 팩트 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-138">The Sales Order dimension is based on a fact table, rather than a dimension table, in the underlying data source.</span></span>  
  
 <span data-ttu-id="422b8-139">다음 절차에서는 다 대 다 관계에 참여하는 엔터티를 이미 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-139">The next procedure assumes that you already know which entities participate in the many-to-many relationship.</span></span> <span data-ttu-id="422b8-140">자세한 내용은 **자세한 정보** 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="422b8-140">See **Learn More** for further study.</span></span>  
  
 <span data-ttu-id="422b8-141">다 대 다 관계를 만드는 데 사용되는 단계를 보여주기 위해 이 절차에서는 Adventure Works 예제 큐브에서 다 대 다 관계 중 하나를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-141">To illustrate the steps used to create a many-to-many relationship, this procedure re-creates one of the many-to-many relationships in the Adventure Works sample cube.</span></span> <span data-ttu-id="422b8-142">원본 데이터(즉, Adventure Works 예제 데이터 웨어하우스)가 관계형 데이터베이스 엔진 인스턴스에 설치되어 있는 경우 다음 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-142">If you have the source data (that is, the Adventure Works sample data warehouse) installed on a relational database engine instance, you can follow these steps.</span></span>  
  
#### <a name="step-1-verify-dsv-relationships"></a><span data-ttu-id="422b8-143">1단계: DSV 관계 확인</span><span class="sxs-lookup"><span data-stu-id="422b8-143">Step 1: Verify DSV relationships</span></span>  
  
1.  <span data-ttu-id="422b8-144">SQL Server Data Tools의 다차원 프로젝트에서 SQL Server 데이터베이스 엔진 인스턴스에 호스팅된 Adventure Works DW 2012 관계형 데이터 웨어하우스를 데이터 원본으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-144">In SQL Server Data Tools, in a multidimensional project, create a data source to the Adventure Works DW 2012 relational data warehouse, hosted on a SQL Server Database Engine instance.</span></span>  
  
2.  <span data-ttu-id="422b8-145">다음 기존 테이블을 사용하여 데이터 원본 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-145">Create a Data Source View using the following existing tables:</span></span>  
  
    -   <span data-ttu-id="422b8-146">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="422b8-146">FactInternetSales</span></span>  
  
    -   <span data-ttu-id="422b8-147">FactInternetSalesReason</span><span class="sxs-lookup"><span data-stu-id="422b8-147">FactInternetSalesReason</span></span>  
  
    -   <span data-ttu-id="422b8-148">DimSalesReason</span><span class="sxs-lookup"><span data-stu-id="422b8-148">DimSalesReason</span></span>  
  
3.  <span data-ttu-id="422b8-149">다 대 다 관계에서 사용하려는 모든 테이블이 기본 키 관계를 통해 DSV에서 관련되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-149">Verify that all of the tables you plan to use in the many-to-many relationships are related in the DSV through primary key relationships.</span></span> <span data-ttu-id="422b8-150">이 작업은 이후 단계에서 중간 측정값 그룹에 대한 연결을 설정하기 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-150">This is a requirement for establishing a link to the intermediate measure group in a subsequent step.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="422b8-151">기본 데이터 원본에서 기본 및 외래 키 관계를 제공하지 않는 경우 DSV에서 수동으로 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-151">If the underlying data source does not provide primary and foreign key relationships, you can create the relationships manually in the DSV.</span></span> <span data-ttu-id="422b8-152">자세한 내용은 [데이터 원본 뷰에서 논리적 관계 정의&#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="422b8-152">For more information, see [Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md).</span></span>  
  
     <span data-ttu-id="422b8-153">다음 예제에서는 이 절차에서 사용되는 테이블이 기본 키를 사용하여 연결되어 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-153">The following example confirms that the tables used in this procedure are linked using primary keys.</span></span>  
  
     <span data-ttu-id="422b8-154">![관련 테이블을 표시하는 DSV](../media/ssas-m2m-dsvpkeys.PNG "관련 테이블을 표시하는 DSV")</span><span class="sxs-lookup"><span data-stu-id="422b8-154">![DSV showing related tables](../media/ssas-m2m-dsvpkeys.PNG "DSV showing related tables")</span></span>  
  
#### <a name="step-2-create-dimensions-and-measure-groups"></a><span data-ttu-id="422b8-155">2단계: 차원 및 측정값 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="422b8-155">Step 2: Create dimensions and measure groups</span></span>  
  
1.  <span data-ttu-id="422b8-156">SQL Server Data Tools의 다차원 프로젝트에서 **차원** 을 마우스 오른쪽 단추로 클릭하고 **새 차원**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-156">In SQL Server Data Tools, in a multidimensional project, right-click **Dimensions** and select **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="422b8-157">기존 **DimSalesReason**테이블을 기반으로 새 차원을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-157">Create a new dimension based on existing table, **DimSalesReason**.</span></span> <span data-ttu-id="422b8-158">원본을 지정할 때 기본값을 모두 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-158">Accept all of the default values when specifying the source.</span></span>  
  
     <span data-ttu-id="422b8-159">특성의 경우 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-159">For attributes, select all.</span></span>  
  
     <span data-ttu-id="422b8-160">![새 차원의 특성 목록](../media/ssas-m2m-dimsalesreason.PNG "새 차원의 특성 목록")</span><span class="sxs-lookup"><span data-stu-id="422b8-160">![Attributes list in new dimension](../media/ssas-m2m-dimsalesreason.PNG "Attributes list in new dimension")</span></span>  
  
3.  <span data-ttu-id="422b8-161">기존 Fact Internet Sales 테이블을 기반으로 두 번째 차원을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-161">Create a second dimension based on existing table, Fact Internet Sales.</span></span> <span data-ttu-id="422b8-162">이 테이블은 팩트 테이블이지만 Sales Order 정보를 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-162">Although this is a fact table, it contains Sales Order information.</span></span> <span data-ttu-id="422b8-163">이 정보를 사용하여 Sales Order 차원을 만들 것입니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-163">We'll use it to build a Sales Order dimension.</span></span>  
  
4.  <span data-ttu-id="422b8-164">원본 정보 지정에서 이름 열을 지정해야 한다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-164">In Specify Source Information, you will see a warning that indicates a Name column must be specified.</span></span> <span data-ttu-id="422b8-165">**SalesOrderNumber** 를 이름으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-165">Choose **SalesOrderNumber** as the Name.</span></span>  
  
     <span data-ttu-id="422b8-166">![이름 열을 표시하는 Sales Order 차원](../media/ssas-m2m-dimsalesordersource.PNG "이름 열을 표시하는 Sales Order 차원")</span><span class="sxs-lookup"><span data-stu-id="422b8-166">![Sales Order dimension showing the name column](../media/ssas-m2m-dimsalesordersource.PNG "Sales Order dimension showing the name column")</span></span>  
  
5.  <span data-ttu-id="422b8-167">마법사의 다음 페이지에서 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-167">On the next page of the wizard, choose the attributes.</span></span> <span data-ttu-id="422b8-168">이 예에서는 **SalesOrderNumber**만 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-168">In this example, you can select just **SalesOrderNumber**.</span></span>  
  
     <span data-ttu-id="422b8-169">![특성 목록을 보여 주는 Sales Order 차원](../media/ssas-m2m-dimsalesorderattrib.PNG "특성 목록을 보여 주는 Sales Order 차원")</span><span class="sxs-lookup"><span data-stu-id="422b8-169">![Sales order dimension showing attribute list](../media/ssas-m2m-dimsalesorderattrib.PNG "Sales order dimension showing attribute list")</span></span>  
  
6.  <span data-ttu-id="422b8-170">차원에 대해 일관성 있는 명명 규칙을 사용하기 위해 차원의 이름을 **Dim Sales Orders**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-170">Rename the dimension to **Dim Sales Orders**, so that you have a consistent naming convention for the dimensions.</span></span>  
  
     <span data-ttu-id="422b8-171">![차원 이름 바꾸기를 표시하는 마법사 페이지](../media/ssas-m2m-dimsalesorders.PNG "차원 이름 바꾸기를 표시하는 마법사 페이지")</span><span class="sxs-lookup"><span data-stu-id="422b8-171">![Wizard page showing dimension rename](../media/ssas-m2m-dimsalesorders.PNG "Wizard page showing dimension rename")</span></span>  
  
7.  <span data-ttu-id="422b8-172">**큐브** 를 마우스 오른쪽 단추로 클릭하고 **새 큐브**를 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="422b8-172">Right-click **Cubes** and select **New Cube**.</span></span>  
  
8.  <span data-ttu-id="422b8-173">측정값 그룹 테이블에서 **FactInternetSales** 및 **FactInternetSalesReason**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-173">In measure group tables, choose **FactInternetSales** and **FactInternetSalesReason**.</span></span>  
  
     <span data-ttu-id="422b8-174">**FactInternetSales** 는 큐브에서 사용하려는 측정값을 포함하고 있기 때문에 선택하고,</span><span class="sxs-lookup"><span data-stu-id="422b8-174">You are choosing **FactInternetSales** because it contains the measures you want to use in the cube.</span></span> <span data-ttu-id="422b8-175">**FactInternetSalesReason** 은 판매 주문과 판매 이유의 관계를 설정하는 멤버 연결 데이터를 제공하는 중간 측정값 그룹이기 때문에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-175">You are choosing **FactInternetSalesReason** because it is the intermediate measure group, providing member association data that relates sales orders to sales reasons.</span></span>  
  
9. <span data-ttu-id="422b8-176">각 팩트 테이블의 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-176">Choose measures for each fact table.</span></span>  
  
     <span data-ttu-id="422b8-177">모델을 단순하게 만들기 위해 모든 측정값을 지운 다음 목록 아래쪽에서 **Sales Amount** 및 **Fact Internet Sales Count** 만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-177">To simplify your model, clear all the measures, and then select just **Sales Amount** and **Fact Internet Sales Count** at the bottom of the list.</span></span> <span data-ttu-id="422b8-178">**FactInternetSalesReason** 은 측정값을 하나만 포함하므로 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-178">The **FactInternetSalesReason** only has one measure, so it is selected for you automatically.</span></span>  
  
10. <span data-ttu-id="422b8-179">차원 목록에 **Dim Sales Reason** 및 **Dim Sales Orders**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-179">In the dimension list, you should see **Dim Sales Reason** and **Dim Sales Orders**.</span></span>  
  
     <span data-ttu-id="422b8-180">새 차원 선택 페이지에서 **Fact Internet Sales Dimension**의 새 차원을 만들라는 메시지가 마법사에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-180">In the Select New Dimensions page, the wizard prompts you to create a new dimension for **Fact Internet Sales Dimension**.</span></span> <span data-ttu-id="422b8-181">이 차원은 필요하지 않으므로 목록에서 지워도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-181">You do not need this dimension, so you can clear it from the list.</span></span>  
  
11. <span data-ttu-id="422b8-182">큐브의 이름을 지정하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-182">Name the cube and click **Finish**.</span></span>  
  
#### <a name="step-3-define-many-to-many-relationship"></a><span data-ttu-id="422b8-183">3단계: 다 대 다 관계 정의</span><span class="sxs-lookup"><span data-stu-id="422b8-183">Step 3: Define Many-to-Many relationship</span></span>  
  
1.  <span data-ttu-id="422b8-184">큐브 디자이너에서 차원 용도 탭을 클릭 합니다. **Dim Sales Reason** 과 **Fact Internet Sales**간에 이미 다 대 다 관계가 있음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-184">In cube designer, click Dimension Usage tab. Notice that there is already a many-to-many relationship between **Dim Sales Reason** and **Fact Internet Sales**.</span></span> <span data-ttu-id="422b8-185">이전에 설명한 대로 다음 아이콘은 다 대 다 관계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-185">Recall that the following icon indicates a many-to-many relationship.</span></span>  
  
     <span data-ttu-id="422b8-186">![차원 용도의 다 대 다 아이콘](../media/ssas-m2m-icondimusage.png "차원 용도의 다 대 다 아이콘")</span><span class="sxs-lookup"><span data-stu-id="422b8-186">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
2.  <span data-ttu-id="422b8-187">**Dim Sales Reason** 과 **Fact Internet Sales**간의 교집합 셀을 클릭한 다음 단추를 클릭하여 관계 정의 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-187">Click on the intersection cell between **Dim Sales Reason** and **Fact Internet Sales**, and then click the button to open the Define Relationship dialog box.</span></span>  
  
     <span data-ttu-id="422b8-188">이 대화 상자가 다 대 다 관계를 지정하는 데 사용됨을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-188">You can see that this dialog box is used to specify a many-to-many relationship.</span></span> <span data-ttu-id="422b8-189">일반 관계가 있는 차원을 대신 추가한 경우에는 이 대화 상자를 사용하여 다 대 다로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-189">If you were adding dimensions that had a regular relationship instead, you would use this dialog box to change it to many-to-many.</span></span>  
  
     <span data-ttu-id="422b8-190">![차원 사용의 관계 정의 단추](../media/ssas-m2m-btndimusage.png "차원 사용의 관계 정의 단추")</span><span class="sxs-lookup"><span data-stu-id="422b8-190">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
3.  <span data-ttu-id="422b8-191">Analysis Services 다차원 인스턴스에 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-191">Deploy the project to an Analysis Services multidimensional instance.</span></span> <span data-ttu-id="422b8-192">다음 단계에서는 Excel에서 큐브를 탐색하여 동작을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-192">In the next step, you will browse the cube in Excel to verify its behaviors.</span></span>  
  
## <a name="testing-many-to-many"></a><span data-ttu-id="422b8-193">다 대 다 테스트</span><span class="sxs-lookup"><span data-stu-id="422b8-193">Testing Many-to-Many</span></span>  
 <span data-ttu-id="422b8-194">큐브에서 다 대 다 관계를 정의하는 경우 쿼리가 예상되는 결과를 반환하는지 확인하기 위해 반드시 테스트를 거쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-194">When you define a many-to-many relationship in a cube, testing is imperative to ensure queries return expected results.</span></span> <span data-ttu-id="422b8-195">최종 사용자가 사용할 클라이언트 애플리케이션을 사용하여 큐브를 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-195">You should test the cube using the client application tool that will be used by end-users.</span></span> <span data-ttu-id="422b8-196">다음 절차에서는 Excel을 사용하여 큐브에 연결하고 쿼리 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-196">In this next procedure, you will use Excel to connect to the cube and verify query results.</span></span>  
  
#### <a name="browse-the-cube-in-excel"></a><span data-ttu-id="422b8-197">Excel에서 큐브 탐색</span><span class="sxs-lookup"><span data-stu-id="422b8-197">Browse the cube in Excel</span></span>  
  
1.  <span data-ttu-id="422b8-198">프로젝트를 배포한 다음 큐브를 탐색하여 집계가 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-198">Deploy the project and then browse the cube to confirm the aggregations are valid.</span></span>  
  
2.  <span data-ttu-id="422b8-199">Excel의 **Data**  |  Analysis Services에서**기타 원본의**데이터를 클릭  |  **From Analysis Services**합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-199">In Excel, click **Data** | **From Other Sources** | **From Analysis Services**.</span></span> <span data-ttu-id="422b8-200">서버의 이름을 입력하고 데이터베이스와 큐브를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-200">Enter the name of the server, choose the database and cube.</span></span>  
  
3.  <span data-ttu-id="422b8-201">다음과 같은 피벗 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-201">Create a PivotTable that uses the following:</span></span>  
  
    -   <span data-ttu-id="422b8-202">**Sales Amount** 를 값으로 사용함</span><span class="sxs-lookup"><span data-stu-id="422b8-202">**Sales Amount** as the Value</span></span>  
  
    -   <span data-ttu-id="422b8-203">열에서**Sales Reason Name** 을 사용함</span><span class="sxs-lookup"><span data-stu-id="422b8-203">**Sales Reason Name** on Columns</span></span>  
  
    -   <span data-ttu-id="422b8-204">행에서**Sales Order Number** 를 사용함</span><span class="sxs-lookup"><span data-stu-id="422b8-204">**Sales Order Number** on Rows</span></span>  
  
4.  <span data-ttu-id="422b8-205">결과를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-205">Analyze the results.</span></span> <span data-ttu-id="422b8-206">예제 데이터를 사용하고 있기 때문에 처음에는 모든 판매 주문에 동일한 값이 있는 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-206">Because we are using sample data, the initial impression is that all sales orders have identical values.</span></span> <span data-ttu-id="422b8-207">그러나 아래로 스크롤하면 데이터 변화를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-207">However, if you scroll down, you begin to see data variation.</span></span>  
  
     <span data-ttu-id="422b8-208">어느 정도 내려가면 주문 번호 **SO5382**에 대한 판매액과 판매 이유를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-208">Part way down, you can find the sales amount and sales reasons for order number **SO5382**.</span></span> <span data-ttu-id="422b8-209">이 특정 주문의 총합계는 **539.99**이고 이 주문에 할당된 구매 이유에는 Promotion, Other 및 Price가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-209">Grand total of this particular order is **539.99**, and the purchase reasons attributed to this order include Promotion, Other and Price.</span></span>  
  
     <span data-ttu-id="422b8-210">![다 대 다 집계를 표시하는 Excel 워크시트](../media/ssas-m2m-excel.png "다 대 다 집계를 표시하는 Excel 워크시트")</span><span class="sxs-lookup"><span data-stu-id="422b8-210">![Excel worksheet showing many-to-many aggregations](../media/ssas-m2m-excel.png "Excel worksheet showing many-to-many aggregations")</span></span>  
  
     <span data-ttu-id="422b8-211">주문의 판매액은 올바르게 계산되었습니다. 즉, 전체 주문의 판매액은 **539.99** 입니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-211">Notice that the Sales Amount is correctly calculated for the order; it is **539.99** for the entire order.</span></span> <span data-ttu-id="422b8-212">**539.99** 가 각 이유에 표시되어 있지만 모든 세 이유의 값에 대한 합계가 계산되지 않아서 총합계가 잘못된 값으로 커지지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-212">Although **539.99** is indicated for each reason, that value is not summed for all three reasons, erroneously inflating our grand total.</span></span>  
  
     <span data-ttu-id="422b8-213">왜 처음부터 판매액을 각 판매 이유 아래에 넣지 않았을까요?</span><span class="sxs-lookup"><span data-stu-id="422b8-213">Why put a sales amount under each sales reason in the first place?</span></span> <span data-ttu-id="422b8-214">그것은 바로 각 이유에 할당할 수 있는 판매액을 식별할 수 있도록 하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-214">The answer is that it allows us to identify the amount of sales we can attribute to each reason.</span></span>  
  
5.  <span data-ttu-id="422b8-215">워크시트의 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-215">Scroll to the bottom of the worksheet.</span></span> <span data-ttu-id="422b8-216">이제 총합계뿐만 아니라 다른 이유에 비해 Price가 고객 구매의 가장 중요한 이유인 것을 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-216">It is now easy to see that Price is the most important reason for customer purchases, relative to other reasons as well as the grand total.</span></span>  
  
     <span data-ttu-id="422b8-217">![다 대 다에서 합계를 표시하는 Excel 통합 문서](../media/ssas-m2m-excelgrandtotal.png "다 대 다에서 합계를 표시하는 Excel 통합 문서")</span><span class="sxs-lookup"><span data-stu-id="422b8-217">![Excel workbook showing totals in many-to-many](../media/ssas-m2m-excelgrandtotal.png "Excel workbook showing totals in many-to-many")</span></span>  
  
#### <a name="tips-for-handling-unexpected-query-results"></a><span data-ttu-id="422b8-218">예기치 않은 쿼리 결과 처리 시 유용한 정보</span><span class="sxs-lookup"><span data-stu-id="422b8-218">Tips for handling unexpected query results</span></span>  
  
1.  <span data-ttu-id="422b8-219">쿼리에서 의미 있는 결과를 반환하지 않는 개수와 같은 측정값을 중간 측정값 그룹에서 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-219">Hide measures in the intermediate measure group, such as the count, that do not return meaningful results in a query.</span></span> <span data-ttu-id="422b8-220">이렇게 하면 의미 없는 데이터를 생성하는 집계를 사용하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-220">This prevents people from trying to use aggregations producing meaningless data.</span></span> <span data-ttu-id="422b8-221">측정값을 숨기려면 차원 디자이너에서 특성에 대한 **표시 유형** 을 **False** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-221">To hide a measure, set **Visibility** to **False** on the attribute in dimension designer.</span></span>  
  
2.  <span data-ttu-id="422b8-222">제공하려는 분석 환경을 지원하는 차원과 측정값의 하위 집합을 사용하기 위해 큐브 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-222">Create perspectives to use a subset of measures and dimensions that support the analytical experience you want to provide.</span></span> <span data-ttu-id="422b8-223">경우에 따라 함께 제대로 작동하지 않는 많은 측정값 그룹과 차원이 큐브에 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-223">Possibly, a cube that contains many measure groups and dimensions do not work well together in all cases.</span></span> <span data-ttu-id="422b8-224">함께 사용하려는 차원과 측정값 그룹을 분리하면 보다 예측 가능한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-224">By isolating the dimensions and measure groups that you intend to be used together, you ensure a more predictable outcome.</span></span>  
  
3.  <span data-ttu-id="422b8-225">모델을 변경한 후 배포하고 다시 연결하는 작업을 항상 잊지 말고 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-225">Always remember to deploy and reconnect after changing a model.</span></span> <span data-ttu-id="422b8-226">Excel에서 피벗 테이블 분석 리본의 새로 고침 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-226">In Excel, use the Refresh button on the PivotTable Analyze ribbon.</span></span>  
  
4.  <span data-ttu-id="422b8-227">연결된 측정값 그룹을 여러 다 대 다 관계에서 사용하지 마십시오. 특히 해당 관계가 서로 다른 큐브에 있는 경우에 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="422b8-227">Avoid using linked measure groups in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="422b8-228">사용하면 모호한 집계가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="422b8-228">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="422b8-229">자세한 내용은 [다 대 다 관계가 포함된 큐브의 연결된 측정값에 대한 잘못된 집계](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="422b8-229">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
##  <a name="learn-more"></a><a name="bkmk_Learn"></a><span data-ttu-id="422b8-230">더 알아보세요</span><span class="sxs-lookup"><span data-stu-id="422b8-230">Learn more</span></span>  
 <span data-ttu-id="422b8-231">개념을 완전히 이해하는 데 유용한 추가 정보를 얻으려면 다음 링크를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="422b8-231">Use the following links to get additional information that helps you master the concepts.</span></span>  
  
 [<span data-ttu-id="422b8-232">Analysis Services에서 다 대 다 차원을 정의하는 방법</span><span class="sxs-lookup"><span data-stu-id="422b8-232">How do I define a many-to-many dimension in Analysis Services</span></span>](../lesson-5-3-defining-a-many-to-many-relationship.md)  
  
 [<span data-ttu-id="422b8-233">다 대 다 혁명 2.0</span><span class="sxs-lookup"><span data-stu-id="422b8-233">The many-to-many Revolution 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkId=324760)  
  
 [<span data-ttu-id="422b8-234">자습서: SQL Server Analysis Services의 다 대 다 차원 예제</span><span class="sxs-lookup"><span data-stu-id="422b8-234">Tutorial: Many-to-many dimension example for SQL Server Analysis Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=324761)  
  
## <a name="see-also"></a><span data-ttu-id="422b8-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="422b8-235">See Also</span></span>  
 <span data-ttu-id="422b8-236">[차원 관계](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="422b8-236">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="422b8-237">[Analysis Services 다차원 모델링 자습서에 사용할 샘플 데이터 및 프로젝트 설치](../install-sample-data-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="422b8-237">[Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md) </span></span>  
 <span data-ttu-id="422b8-238">[SSDT&#41;&#40;Analysis Services 프로젝트 배포](deploy-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="422b8-238">[Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="422b8-239">다차원 모델의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="422b8-239">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)  
  
  
