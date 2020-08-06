---
title: 함수 삽입 대화 상자 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.INSERTFUNCTIONDB.F1
ms.assetid: c4b36d8f-2328-45f7-8bd4-cc0111571e25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0d92dd34e671dc026215d79e7eaed88bebfac15f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651397"
---
# <a name="insert-function-dialog-box-ssas"></a><span data-ttu-id="9e617-102">함수 삽입 대화 상자(SSAS)</span><span class="sxs-lookup"><span data-stu-id="9e617-102">Insert Function Dialog Box (SSAS)</span></span>
  <span data-ttu-id="9e617-103">**함수 삽입** 대화 상자를 사용하면 수식을 작성할 때 사용할 수 있는 함수가 포함된 목록에서 함수를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-103">The **Insert Function** dialog box enables you to choose from a list of functions that can be used when building formulas.</span></span> <span data-ttu-id="9e617-104">모델 디자이너에서 이 대화 상자에 액세스하려면 각 테이블 위에 있는 수식 입력줄에서 함수(**fx**) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-104">To access this dialog box from the model designer, in the formula bar above each table, click the function (**fx**) button.</span></span> <span data-ttu-id="9e617-105">수식에 사용할 함수를 선택하는 방법은 DAX 소개 및 수식 작성을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e617-105">For more information about choosing functions to use in formulas, see DAX Introduction and Build a Formula.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e617-106">항목</span><span class="sxs-lookup"><span data-stu-id="9e617-106">Item</span></span>|<span data-ttu-id="9e617-107">Description</span><span class="sxs-lookup"><span data-stu-id="9e617-107">Description</span></span>|  
|<span data-ttu-id="9e617-108">**범주 선택**</span><span class="sxs-lookup"><span data-stu-id="9e617-108">**Select a category**</span></span>|<span data-ttu-id="9e617-109">어떤 종류의 함수가 필요할지 어느 정도 알고 있는 경우에는 목록에서 범주를 선택합니다. 사전순으로 나열된 함수 목록을 보려면 **모두** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-109">If you have a general idea which kind of function you need, choose a category from the list; or select **All** to view an alphabetical list of functions.</span></span>|  
|<span data-ttu-id="9e617-110">**함수 선택**</span><span class="sxs-lookup"><span data-stu-id="9e617-110">**Select a function**</span></span>|<span data-ttu-id="9e617-111">선택한 범주의 함수 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-111">Displays a list of the functions in the selected category.</span></span>|  
|<span data-ttu-id="9e617-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="9e617-112">**Description**</span></span>|<span data-ttu-id="9e617-113">열 이름 및 식과 같은 필수 인수나 선택적 인수와 함께 함수가 수행하는 작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-113">Displays a description of what the function does, together with any required or optional arguments, such as column names and expressions.</span></span>|  
  
## <a name="function-categories"></a><span data-ttu-id="9e617-114">함수 범주</span><span class="sxs-lookup"><span data-stu-id="9e617-114">Function Categories</span></span>  
 <span data-ttu-id="9e617-115">DAX(Data Analysis Expressions)는 **함수 삽입** 대화 상자에서 다음과 같은 유형의 함수 범주를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-115">Data Analysis Expressions (DAX) provides the following types of function categories in the **Insert Functions** dialog box.</span></span>  
  
 <span data-ttu-id="9e617-116">모두</span><span class="sxs-lookup"><span data-stu-id="9e617-116">All</span></span>  
  
 <span data-ttu-id="9e617-117">날짜 및 시간</span><span class="sxs-lookup"><span data-stu-id="9e617-117">Date & Time</span></span>  
  
 <span data-ttu-id="9e617-118">Assert</span><span class="sxs-lookup"><span data-stu-id="9e617-118">Filter</span></span>  
  
 <span data-ttu-id="9e617-119">논리적</span><span class="sxs-lookup"><span data-stu-id="9e617-119">Logical</span></span>  
  
 <span data-ttu-id="9e617-120">수학 및 삼각</span><span class="sxs-lookup"><span data-stu-id="9e617-120">Math & Trig</span></span>  
  
 <span data-ttu-id="9e617-121">통계</span><span class="sxs-lookup"><span data-stu-id="9e617-121">Statistical</span></span>  
  
 <span data-ttu-id="9e617-122">텍스트</span><span class="sxs-lookup"><span data-stu-id="9e617-122">Text</span></span>  
  
## <a name="measures-and-formulas"></a><span data-ttu-id="9e617-123">측정값 및 수식</span><span class="sxs-lookup"><span data-stu-id="9e617-123">Measures and Formulas</span></span>  
 <span data-ttu-id="9e617-124">**함수 삽입** 대화 상자는 수식을 작성하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-124">The **Insert Function** dialog box is available only when you are building a formula.</span></span> <span data-ttu-id="9e617-125">계산된 열 또는 피벗 테이블이나 피벗 차트에서 계산을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-125">You can create calculations either in a calculated column, or in a PivotTable or PivotChart.</span></span> <span data-ttu-id="9e617-126">피벗 테이블에 사용하기 위해 명시적으로 작성한 수식을 *측정값*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e617-126">Formulas that you build expressly for use in a PivotTable are also called *measures*.</span></span> <span data-ttu-id="9e617-127">자세한 내용은 [계산 열 만들기&#40;SSAS 테이블 형식&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) 및 [측정값 만들기 및 관리&#40;SSAS 테이블 형식&#41;](tabular-models/measures-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e617-127">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) and [Create and Manage Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e617-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e617-128">See Also</span></span>  
 [<span data-ttu-id="9e617-129">계산&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="9e617-129">Calculations &#40;SSAS Tabular&#41;</span></span>](tabular-models/calculations-ssas-tabular.md)  
  
  
