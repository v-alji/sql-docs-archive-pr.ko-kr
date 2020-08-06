---
title: 상태 변수 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45d66152-883a-49a7-a877-2e8ab45f8f79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5214b3512ea0113d1abace61a76033e5531ac99f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742460"
---
# <a name="define-a-state-variable"></a><span data-ttu-id="8fb97-102">상태 변수 정의</span><span class="sxs-lookup"><span data-stu-id="8fb97-102">Define a State Variable</span></span>
  <span data-ttu-id="8fb97-103">이 절차에서는 CDC 상태가 저장되는 패키지 변수를 정의하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-103">This procedure describes how to define a package variable where the CDC state is stored.</span></span>  
  
 <span data-ttu-id="8fb97-104">CDC 상태 변수는 CDC 제어 태스크에 의해 로드, 초기화 및 업데이트되고 변경 레코드의 현재 처리 범위를 결정하기 위해 CDC 원본 데이터 흐름 구성 요소에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-104">The CDC state variable is loaded, initialized, and updated by the CDC Control task and is used by the CDC Source data flow component to determine the current processing range for change records.</span></span> <span data-ttu-id="8fb97-105">CDC 상태 변수는 CDC 제어 태스크 및 CDC 원본에 공통되는 모든 컨테이너에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-105">The CDC state variable can be defined on any container common to the CDC Control task and the CDC source.</span></span> <span data-ttu-id="8fb97-106">이는 패키지 수준에 있을 수 있지만 루프 컨테이너와 같은 다른 컨테이너에 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-106">This may be at the package level but may also be on other containers such as a loop container.</span></span>  
  
 <span data-ttu-id="8fb97-107">수동으로 CDC 상태 변수 값을 수정하는 것은 좋지 않지만 해당 내용을 이해하는 데에는 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-107">Manually modifying the CDC state variable value is not recommended, however it can be useful to understand its contents.</span></span>  
  
 <span data-ttu-id="8fb97-108">다음 표에서는 CDC 상태 변수 값의 구성 요소를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-108">The following table provides a high-level description of the components of the CDC state variable value.</span></span>  
  
|<span data-ttu-id="8fb97-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8fb97-109">Component</span></span>|<span data-ttu-id="8fb97-110">Description</span><span class="sxs-lookup"><span data-stu-id="8fb97-110">Description</span></span>|  
|---------------|-----------------|  
|`<state-name>`|<span data-ttu-id="8fb97-111">현재 CDC 상태의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-111">This is the name of the current CDC state.</span></span>|  
|`CS`|<span data-ttu-id="8fb97-112">이렇게 하면 현재 처리 범위 시작점(현재 시작)이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-112">This marks the current processing range start point (Current Start).</span></span>|  
|`<cs-lsn>`|<span data-ttu-id="8fb97-113">이전 CDC 실행 시 마지막으로 처리된 LSN(로그 시퀀스 번호)입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-113">This is the last (Log Sequence Number) LSN processed in the previous CDC run.</span></span>|  
|`CE`|<span data-ttu-id="8fb97-114">이렇게 하면 현재 처리 범위 끝점(현재 끝)이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-114">This marks the current processing range end point (Current End).</span></span> <span data-ttu-id="8fb97-115">CDC 상태에 CE 구성 요소가 있으면 CDC 패키지가 현재 처리 중이거나 해당 CDC 패키지에서 CDC 처리 범위를 완전히 처리하기 전에 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-115">The presence of the CE component in the CDC state is an indication that either a CDC package is currently processing or that a CDC package failed before fully processing its CDC processing range.</span></span>|  
|`<ce-lsn>`|<span data-ttu-id="8fb97-116">현재 CDC 실행 시 마지막으로 처리된 LSN입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-116">This is the last LSN to be processed in the current CDC Run.</span></span> <span data-ttu-id="8fb97-117">처리할 마지막 시퀀스 번호를 항상 최댓값(0xFFF…)으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-117">It is always assumed that the last sequence number to be processed is the maximum (0xFFF...).</span></span>|  
|`IR`|<span data-ttu-id="8fb97-118">이렇게 하면 초기 처리 범위가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-118">This marks the initial processing range.</span></span>|  
|`<ir-start>`|<span data-ttu-id="8fb97-119">초기 로드가 시작되기 직전 변경 내용의 LSN입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-119">This is an LSN of a change just before the initial load began.</span></span>|  
|`<ir-end>`|<span data-ttu-id="8fb97-120">초기 로드가 끝난 직후 변경 내용의 LSN입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-120">This is an LSN of a change just after the initial load ended.</span></span>|  
|`TS`|<span data-ttu-id="8fb97-121">이렇게 하면 마지막 CDC 상태 업데이트의 타임 스탬프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-121">This marks the timestamp for the last CDC state update.</span></span>|  
|**\<timestamp>**|<span data-ttu-id="8fb97-122">System.DateTime.UtcNow 속성인 64비트의 10진수 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-122">This is a decimal representation of the 64-bit, System.DateTime.UtcNow property.</span></span>|  
|`ER`|<span data-ttu-id="8fb97-123">마지막 작업이 실패했을 때 표시되며 오류의 원인에 대한 간단한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-123">This appears when the last operation failed and includes a short description of the cause of the error.</span></span> <span data-ttu-id="8fb97-124">이 구성 요소가 있으면 항상 마지막에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-124">If this component is present, it will always appear last.</span></span>|  
|`<short-error-text>`|<span data-ttu-id="8fb97-125">간단한 오류 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-125">This is the short error description.</span></span>|  
  
 <span data-ttu-id="8fb97-126">LSN 및 시퀀스 번호는 LSN 값을 Binary(10)로 표현하는 최대 20자리의 16진수 문자열로 각각 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-126">The LSNs and sequence numbers are each encoded as a hexadecimal string of up to 20 digits representing the LSN value of Binary(10).</span></span>  
  
 <span data-ttu-id="8fb97-127">다음 표에는 가능한 CDC 상태 값에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-127">The following table describes the possible CDC state values.</span></span>  
  
|<span data-ttu-id="8fb97-128">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="8fb97-128">State</span></span>|<span data-ttu-id="8fb97-129">Description</span><span class="sxs-lookup"><span data-stu-id="8fb97-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fb97-130">(INITIAL)</span><span class="sxs-lookup"><span data-stu-id="8fb97-130">(INITIAL)</span></span>|<span data-ttu-id="8fb97-131">현재 CDC 그룹에서 패키지가 실행되기 전의 초기 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-131">This is the initial state before the any package was run on the current CDC group.</span></span> <span data-ttu-id="8fb97-132">CDC 상태가 비어 있을 때의 상태이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-132">This is also the state when the CDC state is empty.</span></span>|  
|<span data-ttu-id="8fb97-133">ILSTART(초기 로드 시작)</span><span class="sxs-lookup"><span data-stu-id="8fb97-133">ILSTART (Initial Load Started)</span></span>|<span data-ttu-id="8fb97-134">CDC 제어 태스크에 대한 `MarkInitialLoadStart` 작업 호출 이후 초기 로드 패키지를 시작할 때의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-134">This is the state when the initial load package starts, after the `MarkInitialLoadStart` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="8fb97-135">ILEND(초기 로드 종료)</span><span class="sxs-lookup"><span data-stu-id="8fb97-135">ILEND (Initial Load Ended)</span></span>|<span data-ttu-id="8fb97-136">CDC 제어 태스크에 대한 `MarkInitialLoadEnd` 작업 호출 이후 초기 로드 패키지가 성공적으로 끝날 때의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-136">This is the state when the initial load package ends successfully, after the `MarkInitialLoadEnd` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="8fb97-137">ILUPDATE(초기 로드 업데이트)</span><span class="sxs-lookup"><span data-stu-id="8fb97-137">ILUPDATE (Initial Load Update)</span></span>|<span data-ttu-id="8fb97-138">초기 처리 범위를 처리 중인 동안 초기 로드 이후에 trickle feed 업데이트 패키지를 실행할 때의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-138">This is the state on the runs of the trickle feed update package following the initial load, while still processing the initial processing range.</span></span> <span data-ttu-id="8fb97-139">CDC 제어 태스크에 대한 `GetProcessingRange` 작업 호출 이후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-139">This is after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="8fb97-140">__$reprocessing 열을 사용하는 경우 이 상태는 패키지가 이미 대상에 있는 행을 다시 처리하고 있을 수 있음을 나타내는 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-140">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="8fb97-141">TFEND(Trickle-Feed 업데이트 종료)</span><span class="sxs-lookup"><span data-stu-id="8fb97-141">TFEND (Trickle-Feed Update Ended)</span></span>|<span data-ttu-id="8fb97-142">일반 CDC 실행에 대해 예상되는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-142">This is the state expected for regular CDC runs.</span></span> <span data-ttu-id="8fb97-143">이 상태는 이전 실행이 성공적으로 완료되었으며 새 처리 범위를 사용한 새 실행을 시작할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-143">It indicates that the previous run completed successfully and that a new run with a new processing range can be started.</span></span>|  
|<span data-ttu-id="8fb97-144">TFSTART</span><span class="sxs-lookup"><span data-stu-id="8fb97-144">TFSTART</span></span>|<span data-ttu-id="8fb97-145">이 상태는 CDC 제어 태스크에 대한 `GetProcessingRange` 작업 호출 이후에 trickle feed 업데이트 패키지를 처음 실행하는 것이 아닌 두 번째 실행부터 발생하는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-145">This is the state on a non-initial run of the trickle feed update package, after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="8fb97-146">이 상태는 일반 CDC 실행이 시작되었지만 종료되지 않았거나 아직 확실하게 종료되지 않았음을 나타냅니다(`MarkProcessedRange`).</span><span class="sxs-lookup"><span data-stu-id="8fb97-146">This indicates that a regular CDC run is started but has not finished or has not yet finished, cleanly (`MarkProcessedRange`).</span></span>|  
|<span data-ttu-id="8fb97-147">TFREDO(Trickle-Feed 업데이트 다시 처리)</span><span class="sxs-lookup"><span data-stu-id="8fb97-147">TFREDO (Reprocessing Trickle-Feed Updates)</span></span>|<span data-ttu-id="8fb97-148">이 상태는 TFSTART 실행 후`GetProcessingRange`에서 발생하는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-148">This is the state on a `GetProcessingRange` that occurs after TFSTART.</span></span> <span data-ttu-id="8fb97-149">이 상태는 이전 실행이 성공적으로 완료되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-149">This indicates that the previous run did not complete successfully.</span></span><br /><br /> <span data-ttu-id="8fb97-150">__$reprocessing 열을 사용하는 경우 이 상태는 패키지가 이미 대상에 있는 행을 다시 처리하고 있을 수 있음을 나타내는 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-150">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="8fb97-151">오류</span><span class="sxs-lookup"><span data-stu-id="8fb97-151">ERROR</span></span>|<span data-ttu-id="8fb97-152">CDC 그룹이 ERROR 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-152">The CDC group is in an ERROR state.</span></span>|  
  
 <span data-ttu-id="8fb97-153">다음은 CDC 상태 변수 값의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-153">The following are examples of CDC state variable values.</span></span>  
  
-   <span data-ttu-id="8fb97-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="8fb97-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="8fb97-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="8fb97-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="8fb97-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span><span class="sxs-lookup"><span data-stu-id="8fb97-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span></span>  
  
-   <span data-ttu-id="8fb97-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span><span class="sxs-lookup"><span data-stu-id="8fb97-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span></span>  
  
-   <span data-ttu-id="8fb97-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span><span class="sxs-lookup"><span data-stu-id="8fb97-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span></span>  
  
### <a name="to-define-a-cdc-state-variable"></a><span data-ttu-id="8fb97-159">CDC 상태 변수를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="8fb97-159">To define a CDC state variable</span></span>  
  
1.  <span data-ttu-id="8fb97-160">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 변수를 정의해야 하는 CDC 흐름이 있는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-160">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package that has the CDC flow where you need to define the variable.</span></span>  
  
2.  <span data-ttu-id="8fb97-161">**패키지 탐색기** 탭을 클릭하고 새 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-161">Click the **Package Explorer** tab, and add a new variable.</span></span>  
  
3.  <span data-ttu-id="8fb97-162">상태 변수로 인식할 수 있는 이름을 변수에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-162">Give the variable a name that you can recognize as your state variable.</span></span>  
  
4.  <span data-ttu-id="8fb97-163">변수에 **문자열** 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-163">Give the variable a **String** data type.</span></span>  
  
 <span data-ttu-id="8fb97-164">변수 정의의 일환으로 변수에 값을 지정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8fb97-164">Do not give the variable a value as part of its definition.</span></span> <span data-ttu-id="8fb97-165">값은 CDC 제어 태스크에 의해 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-165">The value must be set by the CDC Control task.</span></span>  
  
 <span data-ttu-id="8fb97-166">**자동 상태 지속**과 함께 CDC 제어 태스크를 사용하려는 경우 CDC 상태 변수는 사용자가 지정하는 데이터베이스 상태 테이블에서 읽히고 해당 값이 변경될 때 동일한 테이블로 다시 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-166">If you plan to use the CDC Control task with **Automatic State Persistence**, the CDC State variable will be read from the database state table you specify and will be updated back to that same table when its value changes.</span></span> <span data-ttu-id="8fb97-167">상태 테이블에 대한 자세한 내용은 [CDC Control Task](../control-flow/cdc-control-task.md)및 [CDC Control Task Editor](../cdc-control-task-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fb97-167">For more information about the State table, see [CDC Control Task](../control-flow/cdc-control-task.md)and [CDC Control Task Editor](../cdc-control-task-editor.md).</span></span>  
  
 <span data-ttu-id="8fb97-168">자동 상태 지속과 함께 CDC 제어 태스크를 사용하지 않는 경우에는 패키지가 마지막으로 실행되었을 때 변수 값이 저장된 영구 스토리지에서 해당 값을 로드하고 현재 처리 범위에 대한 처리가 완료될 때 영구 스토리지에 다시 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fb97-168">If you are not using the CDC Control task with Automatic State Persistence then you must load the variable value from persistent storage where its value was saved the last time the package ran and to write it back to the persistent storage when the processing of the current processing range was completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb97-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8fb97-169">See Also</span></span>  
 <span data-ttu-id="8fb97-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span><span class="sxs-lookup"><span data-stu-id="8fb97-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span></span>  
 [<span data-ttu-id="8fb97-171">CDC 제어 태스크 편집기</span><span class="sxs-lookup"><span data-stu-id="8fb97-171">CDC Control Task Editor</span></span>](../cdc-control-task-editor.md)  
  
  
