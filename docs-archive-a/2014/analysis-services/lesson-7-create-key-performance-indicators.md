---
title: '8 단원: 핵심 성과 지표 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3beaab8a34844ecbd633eb5fabbacf37edfede2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731028"
---
# <a name="lesson-8-create-key-performance-indicators"></a><span data-ttu-id="17c52-102">8단원: 핵심 성과 지표 만들기</span><span class="sxs-lookup"><span data-stu-id="17c52-102">Lesson 8: Create Key Performance Indicators</span></span>
  <span data-ttu-id="17c52-103">이 단원에서는 KPI(핵심 성과 지표)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-103">In this lesson, you will create Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="17c52-104">KPI는 *기본* 측정값으로 정의된 값을 측정값이나 절대값으로 정의된 *대상* 값과 비교하여 값 성과를 측정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-104">KPIs are used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="17c52-105">비즈니스 전문가는 보고 클라이언트 애플리케이션에서 KPI를 사용하여 비즈니스 성취도에 대한 빠르고 이해하기 쉬운 요약 정보를 얻거나 추세를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-105">In reporting client applications, KPIs can provide business professionals a quick and easy way to understand a summary of business success or to identify trends.</span></span> <span data-ttu-id="17c52-106">자세한 내용은 [KPI&#40;SSAS 테이블 형식&#41;](tabular-models/kpis-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17c52-106">To learn more, see [KPIs &#40;SSAS Tabular&#41;](tabular-models/kpis-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="17c52-107">이 단원을 완료하기 위한 예상 시간: **15분**</span><span class="sxs-lookup"><span data-stu-id="17c52-107">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="17c52-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="17c52-108">Prerequisites</span></span>  
 <span data-ttu-id="17c52-109">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="17c52-110">이 단원의 태스크를 수행하려면 이전 단원인 [7단원: 측정값 만들기](lesson-6-create-measures.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
## <a name="create-key-performance-indicators"></a><span data-ttu-id="17c52-111">핵심 성과 지표 만들기</span><span class="sxs-lookup"><span data-stu-id="17c52-111">Create Key Performance Indicators</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a><span data-ttu-id="17c52-112">Internet Current Quarter Sales Performance KPI를 만들려면</span><span class="sxs-lookup"><span data-stu-id="17c52-112">To create an Internet Current Quarter Sales Performance KPI</span></span>  
  
1.  <span data-ttu-id="17c52-113">모델 디자이너에서 **Internet Sales** 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-113">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
2.  <span data-ttu-id="17c52-114">측정값 표에서 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-114">In the measure grid, click an empty cell.</span></span>  
  
3.  <span data-ttu-id="17c52-115">테이블 위의 수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-115">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="17c52-116">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-116">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="17c52-117">이 측정값은 KPI의 기본 측정값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-117">This measure will serve as the Base measure for the KPI.</span></span>  
  
4.  <span data-ttu-id="17c52-118">측정값 표에서 **Internet Current Quarter Sales Performance** 측정값을 마우스 오른쪽 단추로 클릭하고 **KPI 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-118">In the measure grid, right-click the **Internet Current Quarter Sales Performance** measure, and then click **Create KPI**.</span></span>  
  
     <span data-ttu-id="17c52-119">**핵심 성과 지표** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-119">The **Key Performance Indicator** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="17c52-120">**핵심 성과 지표** 대화 상자의 **대상 값 정의**에서 **절대값** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-120">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
6.  <span data-ttu-id="17c52-121">**절대 값** 필드에를 입력 한 `1.1` 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-121">In the **Absolute Value** field, type `1.1`, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="17c52-122">**상태 임계값 정의**의 왼쪽 (낮음) 슬라이더 필드에 `1` 를 입력 하 고 오른쪽 (높음) 슬라이더 필드에를 입력 `1.07` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-122">In **Define Status Thresholds**, in the left (low) slider field, type `1`, and then in the right (high) slider field, type `1.07`.</span></span>  
  
8.  <span data-ttu-id="17c52-123">**아이콘 스타일 선택**에서 다이아몬드(빨간색), 삼각형(노란색), 원(녹색) 아이콘 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-123">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="17c52-124">사용 가능한 아이콘 스타일 아래에 확장 가능한 **설명** 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-124">Notice the **Descriptions** expandable field below the available icon styles.</span></span> <span data-ttu-id="17c52-125">여러 KPI 요소에 대한 설명을 입력하여 클라이언트 애플리케이션에서 KPI를 알아보기 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-125">You can type descriptions for the various KPI elements to make them more identifiable in client applications.</span></span>  
  
9. <span data-ttu-id="17c52-126">**확인** 을 클릭하여 KPI를 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-126">Click **OK** to complete the KPI.</span></span>  
  
     <span data-ttu-id="17c52-127">측정값 표에서 **Internet Current Quarter Sales Performance** 측정값 옆의 아이콘을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-127">In the measure grid, notice the icon next to the **Internet Current Quarter Sales Performance** measure.</span></span> <span data-ttu-id="17c52-128">이 아이콘은 이 측정값이 KPI의 기본 측정값으로 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-128">This icon indicates that this measure serves as a Base value for a KPI.</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a><span data-ttu-id="17c52-129">Internet Current Quarter Margin Performance KPI를 만들려면</span><span class="sxs-lookup"><span data-stu-id="17c52-129">To create an Internet Current Quarter Margin Performance KPI</span></span>  
  
1.  <span data-ttu-id="17c52-130">**Internet Sales** 테이블의 측정값 표에서 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-130">In the measure grid for the **Internet Sales** table, click an empty cell.</span></span>  
  
2.  <span data-ttu-id="17c52-131">테이블 위의 수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-131">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="17c52-132">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="17c52-133">측정값 표에서 **Internet Current Quarter Margin Performance** 측정값을 마우스 오른쪽 단추로 클릭하고 **KPI 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-133">In the measure grid, right-click the **Internet Current Quarter Margin Performance** measure, and then click **Create KPI**.</span></span>  
  
4.  <span data-ttu-id="17c52-134">**핵심 성과 지표** 대화 상자의 **대상 값 정의**에서 **절대값** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-134">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
5.  <span data-ttu-id="17c52-135">**절대 값** 필드에를 입력 `1.25` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-135">In the **Absolute Value** field, type `1.25`.</span></span>  
  
6.  <span data-ttu-id="17c52-136">**상태 임계값 정의**에서 왼쪽(아래쪽) 슬라이더 필드에 **0.8**이 표시될 때까지 슬라이더를 이동한 다음 오른쪽(위쪽) 슬라이더 필드에 **1.03**이 표시될 때까지 슬라이더를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-136">In **Define Status Thresholds**, slide the left (low) slider field until the field displays **0.8**, and then slide the right (high) slider field, until the field displays **1.03**.</span></span>  
  
7.  <span data-ttu-id="17c52-137">**아이콘 스타일 선택**에서 다이아몬드(빨간색), 삼각형(노란색), 원형(녹색) 아이콘 유형을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17c52-137">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type, and then click **OK**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="17c52-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="17c52-138">Next Step</span></span>  
 <span data-ttu-id="17c52-139">이 자습서를 계속하려면 다음 단원인 [9단원: 큐브 뷰 만들기](lesson-8-create-perspectives.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="17c52-139">To continue this tutorial, go to the next lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
  
