---
title: Analysis Services 처리 태스크 편집기 (Analysis Services 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aabcfe286b40f58b429227654107d58e8a4ee837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648520"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a><span data-ttu-id="d02ce-102">Analysis Services 처리 태스크 편집기(Analysis Services 페이지)</span><span class="sxs-lookup"><span data-stu-id="d02ce-102">Analysis Services Processing Task Editor (Analysis Services Page)</span></span>
  <span data-ttu-id="d02ce-103">**Analysis Services 처리 태스크 편집기** 대화 상자의 **Analysis Services** 페이지를 사용하여 Analysis Services 연결 관리자를 지정하고, 처리할 분석 개체를 선택하고, 처리 및 오류 처리 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-103">Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.</span></span>  
  
 <span data-ttu-id="d02ce-104">테이블 형식 모델을 처리할 때는 다음 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-104">When processing tabular models, keep the following in mind:</span></span>  
  
1.  <span data-ttu-id="d02ce-105">테이블 형식 모델에서는 영향 분석을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-105">You cannot perform impact analysis on tabular models.</span></span>  
  
2.  <span data-ttu-id="d02ce-106">조각 모음 처리 및 다시 계산 처리와 같은 테이블 형식 모드에 대한 일부 처리 옵션은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="d02ce-107">DDL 실행 태스크를 사용하여 이러한 함수를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
3.  <span data-ttu-id="d02ce-108">인덱스 처리와 같은 제공되는 일부 처리 옵션은 테이블 형식 모델에 적합하지 않으며 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-108">Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.</span></span>  
  
4.  <span data-ttu-id="d02ce-109">테이블 형식 모델에서는 일괄 설정이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-109">Batch settings are ignored for tabular models.</span></span>  
  
 <span data-ttu-id="d02ce-110">이 태스크에 대한 자세한 내용은 [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d02ce-110">To learn about this task, see [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d02ce-111">옵션</span><span class="sxs-lookup"><span data-stu-id="d02ce-111">Options</span></span>  
 <span data-ttu-id="d02ce-112">**Analysis Services 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="d02ce-112">**Analysis Services connection manager**</span></span>  
 <span data-ttu-id="d02ce-113">목록에서 기존 Analysis Services 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-113">Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d02ce-114">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="d02ce-114">**New**</span></span>  
 <span data-ttu-id="d02ce-115">새 Analysis Services 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-115">Create a new Analysis Services connection manager.</span></span>  
  
 <span data-ttu-id="d02ce-116">**관련 항목:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Analysis Services 연결 관리자 추가 대화 상자 UI 참조](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="d02ce-116">**Related Topics:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="d02ce-117">**개체 목록**</span><span class="sxs-lookup"><span data-stu-id="d02ce-117">**Object list**</span></span>  
 |<span data-ttu-id="d02ce-118">속성</span><span class="sxs-lookup"><span data-stu-id="d02ce-118">Property</span></span>|<span data-ttu-id="d02ce-119">Description</span><span class="sxs-lookup"><span data-stu-id="d02ce-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d02ce-120">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="d02ce-120">**Object Name**</span></span>|<span data-ttu-id="d02ce-121">지정한 개체 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-121">Lists the specified object names.</span></span>|  
|<span data-ttu-id="d02ce-122">**형식**</span><span class="sxs-lookup"><span data-stu-id="d02ce-122">**Type**</span></span>|<span data-ttu-id="d02ce-123">지정한 개체의 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-123">Lists the types of the specified objects.</span></span>|  
|<span data-ttu-id="d02ce-124">**처리 옵션**</span><span class="sxs-lookup"><span data-stu-id="d02ce-124">**Process Options**</span></span>|<span data-ttu-id="d02ce-125">목록에서 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-125">Select a processing option in the list.</span></span><br /><br /> <span data-ttu-id="d02ce-126">**관련 항목**: [다차원 모델 개체 처리](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span><span class="sxs-lookup"><span data-stu-id="d02ce-126">**Related Topics**: [Multidimensional Model Object Processing](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span></span>|  
|<span data-ttu-id="d02ce-127">**설정**</span><span class="sxs-lookup"><span data-stu-id="d02ce-127">**Settings**</span></span>|<span data-ttu-id="d02ce-128">지정한 개체에 대한 처리 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-128">Lists processing settings for the specified objects.</span></span>|  
  
 <span data-ttu-id="d02ce-129">**추가**</span><span class="sxs-lookup"><span data-stu-id="d02ce-129">**Add**</span></span>  
 <span data-ttu-id="d02ce-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체를 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-130">Add an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object to the list.</span></span>  
  
 <span data-ttu-id="d02ce-131">**제거**</span><span class="sxs-lookup"><span data-stu-id="d02ce-131">**Remove**</span></span>  
 <span data-ttu-id="d02ce-132">개체를 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-132">Select an object, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="d02ce-133">**영향 분석**</span><span class="sxs-lookup"><span data-stu-id="d02ce-133">**Impact Analysis**</span></span>  
 <span data-ttu-id="d02ce-134">선택한 개체에 대한 영향 분석을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-134">Perform impact analysis on the selected object.</span></span>  
  
 <span data-ttu-id="d02ce-135">**관련 항목:** [영향 분석 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="d02ce-135">**Related Topics:** [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
 <span data-ttu-id="d02ce-136">**일괄 처리 설정 요약**</span><span class="sxs-lookup"><span data-stu-id="d02ce-136">**Batch Settings Summary**</span></span>  
 |<span data-ttu-id="d02ce-137">속성</span><span class="sxs-lookup"><span data-stu-id="d02ce-137">Property</span></span>|<span data-ttu-id="d02ce-138">Description</span><span class="sxs-lookup"><span data-stu-id="d02ce-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d02ce-139">**처리 순서**</span><span class="sxs-lookup"><span data-stu-id="d02ce-139">**Processing order**</span></span>|<span data-ttu-id="d02ce-140">개체가 순차적으로 또는 일괄 처리 방식으로 처리되는지 여부를 지정합니다. 병렬 처리가 사용되면 동시에 처리할 개체 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-140">Specifies whether objects are processed sequentially or in a batch; if parallel processing is used, specifies the number of objects to process concurrently.</span></span>|  
|<span data-ttu-id="d02ce-141">**트랜잭션 모드**</span><span class="sxs-lookup"><span data-stu-id="d02ce-141">**Transaction mode**</span></span>|<span data-ttu-id="d02ce-142">순차적 처리를 위한 트랜잭션 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-142">Specifies the transaction mode for sequential processing.</span></span>|  
|<span data-ttu-id="d02ce-143">**차원 오류**</span><span class="sxs-lookup"><span data-stu-id="d02ce-143">**Dimension errors**</span></span>|<span data-ttu-id="d02ce-144">오류 발생 시의 태스크 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-144">Specifies the task behavior when errors occur.</span></span>|  
|<span data-ttu-id="d02ce-145">**차원 키 오류 로그 경로**</span><span class="sxs-lookup"><span data-stu-id="d02ce-145">**Dimension key error log path**</span></span>|<span data-ttu-id="d02ce-146">오류가 기록되는 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-146">Specifies the path of the file to which errors are logged.</span></span>|  
|<span data-ttu-id="d02ce-147">**영향을 받는 개체 처리**</span><span class="sxs-lookup"><span data-stu-id="d02ce-147">**Process affected objects**</span></span>|<span data-ttu-id="d02ce-148">종속 개체나 영향을 받는 개체도 처리되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-148">Indicates whether dependent or affected objects are also processed.</span></span>|  
  
 <span data-ttu-id="d02ce-149">**설정 변경**</span><span class="sxs-lookup"><span data-stu-id="d02ce-149">**Change Settings**</span></span>  
 <span data-ttu-id="d02ce-150">처리 옵션 및 차원 키의 오류 처리를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d02ce-150">Change the processing options and the handling of errors in dimension keys.</span></span>  
  
 <span data-ttu-id="d02ce-151">**관련 항목:** [설정 변경 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="d02ce-151">**Related Topics:** [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02ce-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d02ce-152">See Also</span></span>  
 <span data-ttu-id="d02ce-153">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d02ce-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d02ce-154">[Analysis Services 처리 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d02ce-154">[Analysis Services Processing Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="d02ce-155">Analysis Services DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="d02ce-155">Analysis Services Execute DDL Task</span></span>](control-flow/analysis-services-execute-ddl-task.md)  
  
  
