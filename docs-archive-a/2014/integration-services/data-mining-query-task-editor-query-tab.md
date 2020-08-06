---
title: 데이터 마이닝 쿼리 태스크 편집기 (쿼리 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.query.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 72b1755d-d226-46c5-b862-0c9333196a10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6005c92d0d48850461c01353ddf94c61140d0f2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738518"
---
# <a name="data-mining-query-task-editor-query-tab"></a><span data-ttu-id="b750f-102">데이터 마이닝 쿼리 태스크 편집기(쿼리 탭)</span><span class="sxs-lookup"><span data-stu-id="b750f-102">Data Mining Query Task Editor (Query Tab)</span></span>
  <span data-ttu-id="b750f-103">**데이터 마이닝 쿼리 태스크** 대화 상자의 **쿼리** 탭을 사용하여 마이닝 모델을 기반으로 하는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-103">Use the **Query** tab of the **Data Mining Query Task** dialog box to create prediction queries based on a mining model.</span></span> <span data-ttu-id="b750f-104">또한 이 대화 상자에서 매개 변수 및 결과 집합을 변수에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-104">In this dialog box you can also bind parameters and result sets to variables.</span></span>  
  
 <span data-ttu-id="b750f-105">패키지에서 데이터 마이닝을 구현하는 방법에 대한 자세한 내용은 [데이터 마이닝 쿼리 태스크](control-flow/data-mining-query-task.md) 및 [데이터 마이닝 솔루션](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b750f-105">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="b750f-106">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="b750f-106">General Options</span></span>  
 <span data-ttu-id="b750f-107">**이름**</span><span class="sxs-lookup"><span data-stu-id="b750f-107">**Name**</span></span>  
 <span data-ttu-id="b750f-108">데이터 마이닝 쿼리 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-108">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="b750f-109">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-109">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b750f-110">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-110">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="b750f-111">**설명**</span><span class="sxs-lookup"><span data-stu-id="b750f-111">**Description**</span></span>  
 <span data-ttu-id="b750f-112">데이터 마이닝 쿼리 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-112">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="build-query-tab-options"></a><span data-ttu-id="b750f-113">쿼리 작성 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="b750f-113">Build Query Tab Options</span></span>  
 <span data-ttu-id="b750f-114">**데이터 마이닝 쿼리**</span><span class="sxs-lookup"><span data-stu-id="b750f-114">**Data mining query**</span></span>  
 <span data-ttu-id="b750f-115">데이터 마이닝 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-115">Type a data mining query.</span></span>  
  
 <span data-ttu-id="b750f-116">**관련 항목:**  [DMX&#40;Data Mining Extensions&#41; 참조](/sql/dmx/data-mining-extensions-dmx-reference)</span><span class="sxs-lookup"><span data-stu-id="b750f-116">**Related Topics:**  [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference)</span></span>  
  
 <span data-ttu-id="b750f-117">**새 쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="b750f-117">**Build New Query**</span></span>  
 <span data-ttu-id="b750f-118">그래픽 도구를 사용하여 데이터 마이닝 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-118">Create the data mining query using a graphical tool.</span></span>  
  
 <span data-ttu-id="b750f-119">**관련 항목:** [Data Mining Query](control-flow/data-mining-query.md)</span><span class="sxs-lookup"><span data-stu-id="b750f-119">**Related Topics:** [Data Mining Query](control-flow/data-mining-query.md)</span></span>  
  
## <a name="parameter-mapping-tab-options"></a><span data-ttu-id="b750f-120">매개 변수 매핑 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="b750f-120">Parameter Mapping Tab Options</span></span>  
 <span data-ttu-id="b750f-121">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="b750f-121">**Parameter Name**</span></span>  
 <span data-ttu-id="b750f-122">필요에 따라 매개 변수 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-122">Optionally, update the parameter name.</span></span> <span data-ttu-id="b750f-123">**변수 이름** 목록에서 변수를 선택하여 매개 변수를 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-123">Map the parameter to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="b750f-124">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="b750f-124">**Variable Name**</span></span>  
 <span data-ttu-id="b750f-125">목록에서 매개 변수에 매핑할 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-125">Select a variable in the list to map it to the parameter.</span></span>  
  
 <span data-ttu-id="b750f-126">**추가**</span><span class="sxs-lookup"><span data-stu-id="b750f-126">**Add**</span></span>  
 <span data-ttu-id="b750f-127">목록에 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-127">Add to a parameter to the list.</span></span>  
  
 <span data-ttu-id="b750f-128">**제거**</span><span class="sxs-lookup"><span data-stu-id="b750f-128">**Remove**</span></span>  
 <span data-ttu-id="b750f-129">매개 변수를 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-129">Select a parameter, and then click **Remove**.</span></span>  
  
## <a name="result-set-tab-options"></a><span data-ttu-id="b750f-130">결과 집합 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="b750f-130">Result Set Tab Options</span></span>  
 <span data-ttu-id="b750f-131">**결과 이름**</span><span class="sxs-lookup"><span data-stu-id="b750f-131">**Result Name**</span></span>  
 <span data-ttu-id="b750f-132">필요에 따라 결과 집합 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-132">Optionally, update the result set name.</span></span> <span data-ttu-id="b750f-133">**변수 이름** 목록에서 변수를 선택하여 결과를 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-133">Map the result to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="b750f-134">**추가**를 클릭하여 결과를 추가한 다음 결과에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-134">After you have added a result by clicking **Add**, provide a unique name for the result.</span></span>  
  
 <span data-ttu-id="b750f-135">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="b750f-135">**Variable Name**</span></span>  
 <span data-ttu-id="b750f-136">목록에서 결과 집합에 매핑할 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-136">Select a variable in the list to map it to the result set.</span></span>  
  
 <span data-ttu-id="b750f-137">**결과 형식**</span><span class="sxs-lookup"><span data-stu-id="b750f-137">**Result Type**</span></span>  
 <span data-ttu-id="b750f-138">단일 행을 반환할지, 아니면 전체 결과 집합을 반환할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-138">Indicate whether to return a single row or a full result set.</span></span>  
  
 <span data-ttu-id="b750f-139">**추가**</span><span class="sxs-lookup"><span data-stu-id="b750f-139">**Add**</span></span>  
 <span data-ttu-id="b750f-140">목록에 결과 집합을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-140">Add a result set to the list.</span></span>  
  
 <span data-ttu-id="b750f-141">**제거**</span><span class="sxs-lookup"><span data-stu-id="b750f-141">**Remove**</span></span>  
 <span data-ttu-id="b750f-142">결과를 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b750f-142">Select a result, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b750f-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b750f-143">See Also</span></span>  
 <span data-ttu-id="b750f-144">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b750f-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b750f-145">[데이터 마이닝 쿼리 태스크 편집기 &#40;마이닝 모델 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="b750f-145">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="b750f-146">[데이터 마이닝 쿼리 태스크 편집기 &#40;출력 탭&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="b750f-146">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="b750f-147">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="b750f-147">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
