---
title: Kpi 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649207"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a><span data-ttu-id="8efaa-102">KPI 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="8efaa-102">Create and Manage KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="8efaa-103">이 항목에서는 테이블 형식 모델에서 KPI(핵심 성과 지표)를 만들거나 편집하거나 삭제하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-103">This topic describes how to create, edit, or delete a KPI (Key Performance Indicator) in a tabular model.</span></span> <span data-ttu-id="8efaa-104">KPI를 만들려면 KPI의 기본 값으로 평가 되는 측정값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-104">To create a KPI, you select a measure that evaluates to the KPI's Base value.</span></span> <span data-ttu-id="8efaa-105">그런 후 핵심 성과 지표 대화 상자를 사용해서 대상 값으로 평가되는 두 번째 측정값 또는 절대값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-105">You then use the Key Performance Indicator dialog box to select a second measure or an absolute value that evaluates to a target value.</span></span> <span data-ttu-id="8efaa-106">그리고 기본 및 대상 측정값 사이의 성능을 측정하는 상태 임계값을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-106">You can then define status thresholds that measure the performance between the Base and Target measures.</span></span>  
  
 <span data-ttu-id="8efaa-107">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-107">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="8efaa-108">KPI를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8efaa-108">To create a KPI</span></span>](#bkmk_create_KPI)  
  
-   [<span data-ttu-id="8efaa-109">KPI를 편집 하려면</span><span class="sxs-lookup"><span data-stu-id="8efaa-109">To edit a KPI</span></span>](#bkmk_edit_KPI)  
  
-   [<span data-ttu-id="8efaa-110">KPI 및 기본 측정값을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="8efaa-110">To delete a KPI and the base measure</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="8efaa-111">KPI를 삭제하고 기본 측정값 유지</span><span class="sxs-lookup"><span data-stu-id="8efaa-111">To delete a KPI, but keep the base measure</span></span>](#bkmk_delete_KPI)  
  
## <a name="tasks"></a><span data-ttu-id="8efaa-112">작업</span><span class="sxs-lookup"><span data-stu-id="8efaa-112">Tasks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8efaa-113">KPI를 만들려면 먼저 값으로 계산되는 기본 측정값을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-113">Before creating a KPI, you must first create a Base measure that evaluates to value.</span></span> <span data-ttu-id="8efaa-114">그런 다음 기본 측정값을 KPI로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-114">You then extend the Base measure to a KPI.</span></span> <span data-ttu-id="8efaa-115">측정값을 만드는 방법은 다른 항목 [측정값 만들기 및 관리&#40;SSAS 테이블 형식&#41;](measures-ssas-tabular.md)에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-115">How to create measures are described in another topic, [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md).</span></span> <span data-ttu-id="8efaa-116">KPI에는 대상 값도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-116">A KPI also requires a target value.</span></span> <span data-ttu-id="8efaa-117">이 값은 미리 정의된 다른 측정값이나 절대값에서 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-117">This value can be from another pre-defined measure or an absolute value.</span></span> <span data-ttu-id="8efaa-118">기본 측정값을 KPI로 확장한 후 핵심 성과 지표 대화 상자에서 대상 값을 선택하고 상태 임계값을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-118">Once you have extended a Base measure to a KPI, you can then select the target value and define status thresholds in the Key Performance Indicator dialog box.</span></span>  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a> <span data-ttu-id="8efaa-119">KPI 만들기</span><span class="sxs-lookup"><span data-stu-id="8efaa-119">To create a KPI</span></span>  
  
1.  <span data-ttu-id="8efaa-120">측정값 표에서 기본 측정값(값)으로 사용할 측정값을 마우스 오른쪽 단추로 클릭하고 **KPI 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-120">In the measure grid, right-click the measure that will serve as the Base measure (value), and then click **Create KPI**.</span></span>  
  
2.  <span data-ttu-id="8efaa-121">**핵심 성과 지표** 대화 상자의 **대상 값 정의**에서 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-121">In the **Key Performance Indicator** dialog box, in **Define target value**, select from one of the following:</span></span>  
  
     <span data-ttu-id="8efaa-122">**측정값**을 선택하고 목록 상자에서 대상 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-122">Select **Measure**, and then select a target measure from the listbox.</span></span>  
  
     <span data-ttu-id="8efaa-123">**절대값**을 선택하고 숫자 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-123">Select **Absolute value**, and then type a numerical value.</span></span>  
  
3.  <span data-ttu-id="8efaa-124">**상태 임계값 정의**에서 낮은 임계값과 높은 임계값을 클릭한 후 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-124">In **Define status thresholds**, click and slide the low and high threshold values.</span></span>  
  
4.  <span data-ttu-id="8efaa-125">**아이콘 스타일 선택**에서 이미지 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-125">In **Select icon style**, click an image type.</span></span>  
  
5.  <span data-ttu-id="8efaa-126">**설명**을 클릭하고 KPI, 값, 상태 및 대상에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-126">Click on **Descriptions**, and then type descriptions for KPI, Value, Status, and Target.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8efaa-127">Excel에서 분석 기능을 사용하여 KPI를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-127">You can use the Analyze in Excel feature to test your KPI.</span></span> <span data-ttu-id="8efaa-128">자세한 내용은 이 항목의 뒷부분에 나오는 [Excel에서 분석&#40;SSAS 테이블 형식&#41;](analyze-in-excel-ssas-tabular.md)에서 역할 관리자 대화 상자를 사용하여 역할을 정의하는 테이블 형식 모델 작성자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-128">For more information, see [Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md).</span></span>  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a> <span data-ttu-id="8efaa-129">KPI 편집</span><span class="sxs-lookup"><span data-stu-id="8efaa-129">To edit a KPI</span></span>  
  
-   <span data-ttu-id="8efaa-130">측정값 표에서 KPI의 기본 측정값(값)으로 사용할 측정값을 마우스 오른쪽 단추로 클릭하고 **KPI 설정 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-130">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Edit KPI Settings**.</span></span>  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a> <span data-ttu-id="8efaa-131">KPI 및 기본 측정값 삭제</span><span class="sxs-lookup"><span data-stu-id="8efaa-131">To delete a KPI and the base measure</span></span>  
  
-   <span data-ttu-id="8efaa-132">측정값 표에서 KPI의 기본 측정값(값)으로 사용할 측정값을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-132">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete**.</span></span>  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a><span data-ttu-id="8efaa-133">KPI를 삭제 하 고 기본 측정값 유지</span><span class="sxs-lookup"><span data-stu-id="8efaa-133">To delete a KPI, but keep the base measure</span></span>  
  
-   <span data-ttu-id="8efaa-134">측정값 표에서 KPI의 기본 측정값(값)으로 사용할 측정값을 마우스 오른쪽 단추로 클릭하고 **KPI 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efaa-134">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete KPI**.</span></span>  
  
## <a name="alt-shortcuts"></a><span data-ttu-id="8efaa-135">Alt 바로 가기</span><span class="sxs-lookup"><span data-stu-id="8efaa-135">ALT Shortcuts</span></span>  
  
|<span data-ttu-id="8efaa-136">UI 섹션</span><span class="sxs-lookup"><span data-stu-id="8efaa-136">UI section</span></span>|<span data-ttu-id="8efaa-137">키 명령</span><span class="sxs-lookup"><span data-stu-id="8efaa-137">Key command</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="8efaa-138">KPI 기본 측정값</span><span class="sxs-lookup"><span data-stu-id="8efaa-138">KPI base measure</span></span>|<span data-ttu-id="8efaa-139">Alt+B</span><span class="sxs-lookup"><span data-stu-id="8efaa-139">ALT+B</span></span>|  
|<span data-ttu-id="8efaa-140">KPI 상태</span><span class="sxs-lookup"><span data-stu-id="8efaa-140">KPI Status</span></span>|<span data-ttu-id="8efaa-141">Alt+S</span><span class="sxs-lookup"><span data-stu-id="8efaa-141">ALT+S</span></span>|  
|<span data-ttu-id="8efaa-142">측정값</span><span class="sxs-lookup"><span data-stu-id="8efaa-142">Measure</span></span>|<span data-ttu-id="8efaa-143">Alt+M</span><span class="sxs-lookup"><span data-stu-id="8efaa-143">ALT+M</span></span>|  
|<span data-ttu-id="8efaa-144">절대값</span><span class="sxs-lookup"><span data-stu-id="8efaa-144">Absolute value</span></span>|<span data-ttu-id="8efaa-145">ALT + A</span><span class="sxs-lookup"><span data-stu-id="8efaa-145">ALT+A</span></span>|  
|<span data-ttu-id="8efaa-146">상태 임계값 정의</span><span class="sxs-lookup"><span data-stu-id="8efaa-146">Define status thresholds</span></span>|<span data-ttu-id="8efaa-147">Alt+U</span><span class="sxs-lookup"><span data-stu-id="8efaa-147">ALT+U</span></span>|  
|<span data-ttu-id="8efaa-148">아이콘 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="8efaa-148">Select icon style</span></span>|<span data-ttu-id="8efaa-149">Alt+I</span><span class="sxs-lookup"><span data-stu-id="8efaa-149">ALT+I</span></span>|  
|<span data-ttu-id="8efaa-150">추세</span><span class="sxs-lookup"><span data-stu-id="8efaa-150">Trend</span></span>|<span data-ttu-id="8efaa-151">Alt+T</span><span class="sxs-lookup"><span data-stu-id="8efaa-151">ALT+T</span></span>|  
|<span data-ttu-id="8efaa-152">설명</span><span class="sxs-lookup"><span data-stu-id="8efaa-152">Descriptions</span></span>|<span data-ttu-id="8efaa-153">Alt+D</span><span class="sxs-lookup"><span data-stu-id="8efaa-153">ALT+D</span></span>|  
|<span data-ttu-id="8efaa-154">추세</span><span class="sxs-lookup"><span data-stu-id="8efaa-154">Trend</span></span>|<span data-ttu-id="8efaa-155">Alt+T</span><span class="sxs-lookup"><span data-stu-id="8efaa-155">ALT+T</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8efaa-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8efaa-156">See Also</span></span>  
 <span data-ttu-id="8efaa-157">[SSAS 테이블 형식&#41;&#40;Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="8efaa-157">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 <span data-ttu-id="8efaa-158">[SSAS 테이블 형식&#41;&#40;측정값](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="8efaa-158">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="8efaa-159">측정값 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="8efaa-159">Create and Manage Measures &#40;SSAS Tabular&#41;</span></span>](create-and-manage-measures-ssas-tabular.md)  
  
  
