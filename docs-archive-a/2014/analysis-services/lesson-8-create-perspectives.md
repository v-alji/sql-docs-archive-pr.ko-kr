---
title: '9 단원: 큐브 뷰 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 417b6a4d3b16857f48bcc2f39dc8ec4c010a2b10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739009"
---
# <a name="lesson-9-create-perspectives"></a><span data-ttu-id="19980-102">9단원: 큐브 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="19980-102">Lesson 9: Create Perspectives</span></span>
  <span data-ttu-id="19980-103">이 단원에서는 Internet Sales 큐브 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19980-103">In this lesson, you will create an Internet Sales perspective.</span></span> <span data-ttu-id="19980-104">큐브 뷰는 비즈니스 또는 애플리케이션 중심의 관점에서 파악할 수 있게 해 주는 보기 가능한 모델 하위 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-104">A perspective defines a viewable subset of a model that provides focused, business-specific, or application-specific viewpoints.</span></span> <span data-ttu-id="19980-105">사용자가 큐브 뷰를 사용하여 모델에 연결하는 경우 해당 모델 개체(테이블, 열, 측정값, 계층 및 KPI)만 해당 큐브 뷰에 정의되어 있는 필드로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-105">When a user connects to a model using a perspective, they see only those model objects (tables, columns, measures, hierarchies, and KPIs) as fields defined in that perspective.</span></span>  
  
 <span data-ttu-id="19980-106">이 단원에서 만드는 Internet Sales 큐브 뷰에는 Customer 테이블 개체가 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="19980-106">The Internet Sales perspective you create in this lesson will exclude the Customer table object.</span></span> <span data-ttu-id="19980-107">뷰에서 특정 개체를 제외하는 큐브 뷰를 만들면 해당 개체가 모델에는 그대로 있지만 보고 클라이언트 필드 목록에서는 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-107">When you create a perspective that excludes certain objects from view, that object still exists in the model; however, it is not visible in a reporting client field list.</span></span> <span data-ttu-id="19980-108">큐브 뷰에 포함되어 있거나 포함되어 있지 않은 계산 열 및 측정값을 계속해서 제외된 개체 데이터에서 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-108">Calculated columns and measures either included in a perspective or not can still calculate from object data that is excluded.</span></span>  
  
 <span data-ttu-id="19980-109">이 단원의 목표는 큐브 뷰를 만드는 방법을 설명하고 테이블 형식 모델 제작 도구를 파악하도록 돕는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-109">The purpose of this lesson is to describe how to create perspectives and become familiar with the tabular model authoring tools.</span></span> <span data-ttu-id="19980-110">나중에 추가 테이블을 포함하도록 이 모델을 확장할 경우 큐브 뷰를 추가로 만들어 모델에 대한 다양한 뷰포인트(예: Inventory 및 Sales Force)를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-110">If you later expand this model to include additional tables, you can create additional perspectives to define different viewpoints of the model, for example, Inventory and Sales Force.</span></span>  
  
 <span data-ttu-id="19980-111">자세한 내용은 [큐브 뷰&#40;SSAS 테이블 형식&#41;](tabular-models/perspectives-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19980-111">To learn more, see [Perspectives &#40;SSAS Tabular&#41;](tabular-models/perspectives-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="19980-112">이 단원에 소요되는 예상 시간: **5분**</span><span class="sxs-lookup"><span data-stu-id="19980-112">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19980-113">전제 조건</span><span class="sxs-lookup"><span data-stu-id="19980-113">Prerequisites</span></span>  
 <span data-ttu-id="19980-114">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-114">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="19980-115">이 단원의 태스크를 수행하려면 이전 단원인 [8단원: 핵심 성과 지표 만들기](lesson-7-create-key-performance-indicators.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-115">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
## <a name="create-perspectives"></a><span data-ttu-id="19980-116">큐브 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="19980-116">Create Perspectives</span></span>  
  
#### <a name="to-create-an-internet-sales-perspective"></a><span data-ttu-id="19980-117">Internet Sales 큐브 뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="19980-117">To create an Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="19980-118">모델 디자이너에서 **모델** 메뉴를 클릭 한 다음 **큐브 뷰**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-118">In the model designer, click the **Model** menu, and then click **Perspectives**.</span></span>  
  
2.  <span data-ttu-id="19980-119">**큐브 뷰** 대화 상자에서 **새 큐브 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-119">In the **Perspectives** dialog box, click **New Perspective**.</span></span>  
  
3.  <span data-ttu-id="19980-120">큐브 뷰의 이름을 바꾸려면 **새 큐브 뷰 1** 열 머리글을 두 번 클릭 한 다음를 입력 `Internet Sales` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-120">To rename the perspective, double-click the **New Perspective 1** column heading, and then type `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="19980-121">**필드**에서 **Date**, **Geography**, **Product**, **product Category**, **product 하위 범주**및 테이블을 선택 합니다 `Internet Sales` .</span><span class="sxs-lookup"><span data-stu-id="19980-121">In **Fields**, select the following tables **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and `Internet Sales`.</span></span>  
  
     <span data-ttu-id="19980-122">이 큐브 뷰에서 Customer 테이블과 이 테이블의 모든 열을 제외했습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-122">Notice you excluded the Customer table and all of its columns from this perspective.</span></span> <span data-ttu-id="19980-123">나중에 12단원에서 Excel에서 분석 기능을 사용하여 이 큐브 뷰를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-123">Later, in Lesson 12, you will use the Analyze in Excel feature to test this perspective.</span></span> <span data-ttu-id="19980-124">Excel 피벗 테이블 필드 목록에는 Customer 테이블을 제외한 각 테이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="19980-124">The Excel PivotTable Field List will include each table except the Customer table.</span></span>  
  
5.  <span data-ttu-id="19980-125">선택 항목을 확인하여 **Customer** 테이블이 선택되어 있지 않은지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-125">Verify your selections, making sure the **Customer** table is not checked, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="19980-126">다음 단계</span><span class="sxs-lookup"><span data-stu-id="19980-126">Next Steps</span></span>  
 <span data-ttu-id="19980-127">이 자습서를 계속하려면 다음 단원인 [10단원: 계층 만들기](lesson-9-create-hierarchies.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="19980-127">To continue this tutorial, go to the next lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
  
