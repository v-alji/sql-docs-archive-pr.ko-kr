---
title: 큐브 뷰 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: e11f8be980b99c4e9bd824f281db31e9c3f7d9bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728795"
---
# <a name="perspectives-ssas-tabular"></a><span data-ttu-id="c81f9-102">큐브 뷰(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="c81f9-102">Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="c81f9-103">테이블 형식 모델에서 큐브 뷰는 모델의 보기 가능한 하위 집합을 정의하는데, 이를 통해 모델을 집중해서 보거나 비즈니스 또는 애플리케이션의 관점에서 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-103">Perspectives, in tabular models, define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span>  
  
 <span data-ttu-id="c81f9-104">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="c81f9-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="c81f9-105">이점</span><span class="sxs-lookup"><span data-stu-id="c81f9-105">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="c81f9-106">큐브 뷰 테스트</span><span class="sxs-lookup"><span data-stu-id="c81f9-106">Testing Perspectives</span></span>](#bkmk_testpersp)  
  
-   [<span data-ttu-id="c81f9-107">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c81f9-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="c81f9-108">이점</span><span class="sxs-lookup"><span data-stu-id="c81f9-108">Benefits</span></span>  
 <span data-ttu-id="c81f9-109">테이블 형식 모델은 너무 복잡해서 사용자가 탐색하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-109">Tabular models can be very complex for users to explore.</span></span> <span data-ttu-id="c81f9-110">단일 모델이 여러 개의 테이블, 측정값 및 차원을 포함하는 전체 데이터 웨어하우스의 내용을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-110">A single model can represent the contents of a complete data warehouse with many tables, measures, and dimensions.</span></span> <span data-ttu-id="c81f9-111">이러한 복잡성은 주로 비즈니스 인텔리전스 및 보고 요구 사항을 충족하기 위해 모델의 일부만 사용하는 사용자에게는 부담이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-111">Such complexity can be daunting to users who may only need to interact with a small part of the model in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="c81f9-112">큐브 뷰에서 테이블, 열 및 측정값(KPI 포함)은 필드 개체로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-112">In a perspective, tables, columns, and measures (including KPIs) are defined as field objects.</span></span> <span data-ttu-id="c81f9-113">각 큐브 뷰에 대해 보기 가능한 필드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-113">You can select the viewable fields for each perspective.</span></span> <span data-ttu-id="c81f9-114">예를 들어 단일 모델에 제품, 판매, 재무, 직원 및 지리 데이터가 포함되어 있는데,</span><span class="sxs-lookup"><span data-stu-id="c81f9-114">For example, a single model may contain product, sales, financial, employee, and geographic data.</span></span> <span data-ttu-id="c81f9-115">영업부에는 제품, 판매, 홍보 및 지리 데이터가 필요한 반면 직원 및 재무 데이터는 필요하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-115">While a sales department requires product, sales, promotions, and geography data, they likely do not require employee and financial data.</span></span> <span data-ttu-id="c81f9-116">마찬가지로 인사부에는 판매 홍보 및 지리 데이터가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-116">Similarly, a human resources department does not require data about sales promotions and geography.</span></span>  
  
 <span data-ttu-id="c81f9-117">정의된 큐브 뷰가 있는 모델(데이터 원본)에 연결하는 경우 사용자는 사용할 큐브 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-117">When a user connects to a model (as a data source) with defined perspectives, the user can select the perspective they want to use.</span></span> <span data-ttu-id="c81f9-118">예를 들어 Excel의 모델 데이터 원본에 연결할 경우 인사부의 사용자는 데이터 연결 마법사의 테이블 및 뷰 선택 페이지에서 인적 자원 큐브 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-118">For example, when connecting to a model data source in Excel, users in Human Resources can select the Human Resources perspective on the Select Tables and Views page of the Data Connection Wizard.</span></span> <span data-ttu-id="c81f9-119">이 경우 인적 자원 큐브 뷰에 대해 정의된 필드(테이블, 열 및 측정값)만 피벗 테이블 필드 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-119">Only fields (tables, columns, and measures) defined for the Human Resources perspective will be visible in the PivotTable Field List.</span></span>  
  
 <span data-ttu-id="c81f9-120">큐브 뷰는 보안 수단이 아니라 더 나은 사용자 환경을 제공하기 위한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-120">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience.</span></span> <span data-ttu-id="c81f9-121">특정 큐브 뷰에 대한 모든 보안은 기본 모델에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-121">All security for a particular perspective is inherited from the underlying model.</span></span> <span data-ttu-id="c81f9-122">큐브 뷰에서 사용자에게 액세스 권한이 없는 모델 개체에 대한 액세스 권한을 부여할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-122">Perspectives cannot provide access to model objects to which a user does not already have access.</span></span> <span data-ttu-id="c81f9-123">큐브 뷰를 통해 모델의 개체에 대한 액세스를 제공하려면 먼저 model 데이터베이스에 대한 보안을 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-123">Security for the model database must be resolved before access to objects in the model can be provided through a perspective.</span></span> <span data-ttu-id="c81f9-124">보안 역할을 사용하여 모델 메타데이터 및 데이터에 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-124">Security roles can be used to secure model metadata and data.</span></span> <span data-ttu-id="c81f9-125">자세한 내용은 [역할&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c81f9-125">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
##  <a name="testing-perspectives"></a><a name="bkmk_testpersp"></a><span data-ttu-id="c81f9-126">큐브 뷰 테스트</span><span class="sxs-lookup"><span data-stu-id="c81f9-126">Testing Perspectives</span></span>  
 <span data-ttu-id="c81f9-127">모델 제작 시 모델 디자이너의 Excel에서 분석 기능을 사용하여 정의한 큐브 뷰의 효율성을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-127">When authoring a model, you can use the Analyze in Excel feature in the model designer to test the efficacy of the perspectives you have defined.</span></span> <span data-ttu-id="c81f9-128">모델 디자이너의 **모델** 메뉴에서 **Excel에서 분석**을 클릭하면 Excel이 열리기 전에 **자격 증명 및 큐브 뷰 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-128">From the **Model** menu in the model designer, when you click **Analyze in Excel**, before Excel opens, the **Choose Credentials and Perspective** dialog box appears.</span></span> <span data-ttu-id="c81f9-129">이 대화 상자에서 현재 사용자 이름, 다른 사용자, 역할, 그리고 데이터 원본 및 뷰 데이터로 모델 작업 영역 데이터베이스에 연결하는 데 사용할 큐브 뷰를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-129">In this dialog, you can specify the current username, a different user, a role, and a perspective with which you will use to connect to the model workspace database as a data source and view data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="c81f9-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c81f9-130">Related Tasks</span></span>  
  
|<span data-ttu-id="c81f9-131">항목</span><span class="sxs-lookup"><span data-stu-id="c81f9-131">Topic</span></span>|<span data-ttu-id="c81f9-132">Description</span><span class="sxs-lookup"><span data-stu-id="c81f9-132">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c81f9-133">큐브 뷰 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="c81f9-133">Create and Manage Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)|<span data-ttu-id="c81f9-134">모델 디자이너의 큐브 뷰 대화 상자를 사용하여 큐브 뷰를 만들고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c81f9-134">Describes how to create and manage perspectives using the Perspectives dialog box in the model designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c81f9-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c81f9-135">See Also</span></span>  
 <span data-ttu-id="c81f9-136">[SSAS 테이블 형식&#41;역할 &#40;](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="c81f9-136">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="c81f9-137">계층 구조&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="c81f9-137">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
