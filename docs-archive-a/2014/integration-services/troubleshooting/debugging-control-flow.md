---
title: 제어 흐름 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2e2feff6723a510cb773131cb6452bdc7a77cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734272"
---
# <a name="debugging-control-flow"></a><span data-ttu-id="d6fd7-102">제어 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="d6fd7-102">Debugging Control Flow</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="d6fd7-103">및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지에서 제어 흐름 문제를 해결하는 데 사용할 수 있는 기능과 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-103">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include features and tools that you can use to troubleshoot the control flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package.</span></span>

-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="d6fd7-104">는 컨테이너 및 태스크에서의 중단점을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-104">supports breakpoints on containers and tasks.</span></span>

-   [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="d6fd7-105">디자이너는 런타임에 진행률을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-105">Designer provides progress reporting at run time.</span></span>

-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="d6fd7-106">는 디버그 창을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-106">provides debug windows.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="d6fd7-107">중단점</span><span class="sxs-lookup"><span data-stu-id="d6fd7-107">Breakpoints</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="d6fd7-108">디자이너는 중단 조건을 설정하고 패키지 실행이 일시 중지되기 전에 중단점이 발생할 수 있는 횟수를 지정하여 중단점을 설정할 수 있는 **중단점 설정** 대화 상자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-108">Designer provides the **Set Breakpoints** dialog box, in which you can set breakpoints by enabling break conditions and specifying the number of times a breakpoint can occur before the execution of the package is suspended.</span></span> <span data-ttu-id="d6fd7-109">중단점은 패키지 수준이나 개별 구성 요소의 수준에서 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-109">Breakpoints can be enabled at the package level, or at the level of the individual component.</span></span> <span data-ttu-id="d6fd7-110">중단 조건이 태스크 또는 컨테이너 수준에서 설정된 경우 중단점 아이콘이 **제어 흐름** 탭의 디자인 화면에 있는 태스크 또는 컨테이너 옆에 표시됩니다. 중단 조건이 패키지에서 설정된 경우 중단점 아이콘이 **제어 흐름** 탭의 레이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-110">If break conditions are enabled at the task or container level, the breakpoint icon appears next to the task or container on the design surface of the **Control Flow** tab. If the break conditions are enabled on the package, the breakpoint icon appears on the label of the **Control Flow** tab.</span></span>

 <span data-ttu-id="d6fd7-111">중단점에 도달하면 중단점 아이콘이 변경되어 중단점의 원본을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-111">When a breakpoint is hit, the breakpoint icon changes to help you identify the source of the breakpoint.</span></span> <span data-ttu-id="d6fd7-112">패키지가 실행 중일 때 중단점을 추가, 삭제 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-112">You can add, delete, and change breakpoints when the package is running.</span></span>

 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="d6fd7-113">는 모든 태스크 및 컨테이너에 설정할 수 있는 10개의 중단 조건을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-113">provides ten break conditions that you can enable on all tasks and containers.</span></span> <span data-ttu-id="d6fd7-114">**중단점 설정** 대화 상자에서 다음 조건에 따라 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-114">In the **Set Breakpoints** dialog box, you can enable breakpoints on the following conditions:</span></span>

|<span data-ttu-id="d6fd7-115">중단 조건</span><span class="sxs-lookup"><span data-stu-id="d6fd7-115">Break condition</span></span>|<span data-ttu-id="d6fd7-116">Description</span><span class="sxs-lookup"><span data-stu-id="d6fd7-116">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="d6fd7-117">태스크나 컨테이너가 `OnPreExecute` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-117">When the task or container receives the `OnPreExecute` event.</span></span>|<span data-ttu-id="d6fd7-118">태스크가 실행되려는 순간에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-118">Called when a task is about to execute.</span></span> <span data-ttu-id="d6fd7-119">이 이벤트는 작업이 실행되기 바로 전에 태스크나 컨테이너에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-119">This event is raised by a task or a container immediately before it runs.</span></span>|
|<span data-ttu-id="d6fd7-120">태스크나 컨테이너가 `OnPostExecute` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-120">When the task or container receives the `OnPostExecute` event.</span></span>|<span data-ttu-id="d6fd7-121">태스크의 실행 논리가 완료되자 마자 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-121">Called immediately after the execution logic of the task finishes.</span></span> <span data-ttu-id="d6fd7-122">이 이벤트는 작업이 실행된 바로 후에 태스크나 컨테이너에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-122">This event is raised by a task or container immediately after it runs.</span></span>|
|<span data-ttu-id="d6fd7-123">태스크나 컨테이너가 `OnError` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-123">When the task or container receives the `OnError` event.</span></span>|<span data-ttu-id="d6fd7-124">오류가 발생할 때 태스크 또는 컨테이너에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-124">Called by a task or container when an error occurs.</span></span>|
|<span data-ttu-id="d6fd7-125">태스크나 컨테이너가 `OnWarning` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-125">When the task or container receives the `OnWarning` event.</span></span>|<span data-ttu-id="d6fd7-126">태스크로 인해 오류가 발생되지는 않지만 경고가 발생할 가능성이 매우 높은 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-126">Called when the task is in a state that does not justify an error, but does warrant a warning.</span></span>|
|<span data-ttu-id="d6fd7-127">태스크나 컨테이너가 `OnInformation` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-127">When the task or container receives the `OnInformation` event.</span></span>|<span data-ttu-id="d6fd7-128">태스크가 정보를 제공해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-128">Called when the task is required to provide information.</span></span>|
|<span data-ttu-id="d6fd7-129">태스크나 컨테이너가 `OnTaskFailed` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-129">When the task or container receives the `OnTaskFailed` event.</span></span>|<span data-ttu-id="d6fd7-130">태스크 호스트가 실패할 때 해당 태스크 호스트에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-130">Called by the task host when it fails.</span></span>|
|<span data-ttu-id="d6fd7-131">태스크나 컨테이너가 `OnProgress` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-131">When the task or container receives the `OnProgress` event.</span></span>|<span data-ttu-id="d6fd7-132">태스크 실행에 대한 진행률을 업데이트하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-132">Called to update progress about task execution.</span></span>|
|<span data-ttu-id="d6fd7-133">태스크나 컨테이너가 `OnQueryCancel` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-133">When the task or container receives the `OnQueryCancel` event.</span></span>|<span data-ttu-id="d6fd7-134">태스크 처리 중 실행을 취소할 수 있는 모든 시점에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-134">Called at any time in task processing when you can cancel execution.</span></span>|
|<span data-ttu-id="d6fd7-135">태스크나 컨테이너가 `OnVariableValueChanged` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-135">When the task or container receives the `OnVariableValueChanged` event.</span></span>|<span data-ttu-id="d6fd7-136">변수 값이 변경될 때 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임 시 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-136">Called by the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime when the value of a variable changes.</span></span> <span data-ttu-id="d6fd7-137">이 이벤트를 발생 시키려면 변수의 RaiseChangeEvent을로 설정 해야 합니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="d6fd7-137">The RaiseChangeEvent of the variable must be set to `true` to raise this event.</span></span><br /><br /> <span data-ttu-id="d6fd7-138">**&#42;&#42;경고&#42;&#42;** 이 중단점과 연결된 변수는 **컨테이너** 범위에서 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-138">**&#42;&#42; Warning &#42;&#42;** The variable associated with this breakpoint must be defined at the **container** scope.</span></span> <span data-ttu-id="d6fd7-139">변수가 패키지 범주로 정의된 경우 중단점이 적중되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-139">If the variable is defined at the package scope, the breakpoint does not get hit.</span></span>|
|<span data-ttu-id="d6fd7-140">태스크나 컨테이너가 `OnCustomEvent` 이벤트를 받을 때</span><span class="sxs-lookup"><span data-stu-id="d6fd7-140">When the task or container receives the `OnCustomEvent` event.</span></span>|<span data-ttu-id="d6fd7-141">사용자 지정 태스크 정의 이벤트를 발생시키기 위해 태스크에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-141">Called by tasks to raise custom task-defined events.</span></span>|

 <span data-ttu-id="d6fd7-142">모든 태스크 및 컨테이너에 대해 사용할 수 있는 중단 조건 외에도 일부 태스크 및 컨테이너에는 중단점 설정을 위한 특수한 중단 조건이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-142">In addition to the break conditions available to all tasks and containers, some tasks and containers include special break conditions for setting breakpoints.</span></span> <span data-ttu-id="d6fd7-143">예를 들어 For 루프 컨테이너에 중단 조건을 설정하여 반복되는 각 루프가 시작될 때 실행을 일시 중지하도록 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-143">For example, you can enable a break condition on the For Loop container that sets a breakpoint that suspends execution at the start of each iteration of the loop.</span></span>

 <span data-ttu-id="d6fd7-144">중단점의 유연성과 기능 향상을 위해 다음 옵션을 지정하여 중단점의 동작을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-144">To add flexibility and power to a breakpoint, you can modify the behavior of a breakpoint by specifying the following options:</span></span>

-   <span data-ttu-id="d6fd7-145">실행이 일시 중지되기 전에 중단 조건이 발생하는 최대 횟수 또는 적중 횟수</span><span class="sxs-lookup"><span data-stu-id="d6fd7-145">The hit count, or the maximum number of times that a break condition occurs before the execution is suspended.</span></span>

-   <span data-ttu-id="d6fd7-146">중단 조건이 중단점을 트리거하는 시점을 지정하는 규칙 또는 적중 횟수 유형</span><span class="sxs-lookup"><span data-stu-id="d6fd7-146">The hit count type, or the rule that specifies when the break condition triggers the breakpoint.</span></span>

 <span data-ttu-id="d6fd7-147">항상 유형을 제외한 적중 횟수 유형은 적중 횟수로 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-147">The hit count types, except for the Always type, are further qualified by the hit count.</span></span> <span data-ttu-id="d6fd7-148">예를 들어 유형이 "다음과 같은 적중 횟수"이고 적중 횟수가 5이면 6번째 중단 조건 발생 시 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-148">For example, if the type is "Hit count equals" and the hit count is 5, execution is suspended on the sixth occurrence of the break condition.</span></span>

 <span data-ttu-id="d6fd7-149">다음 표에서는 적중 횟수 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-149">The following table describes the hit count types.</span></span>

|<span data-ttu-id="d6fd7-150">적중 횟수 유형</span><span class="sxs-lookup"><span data-stu-id="d6fd7-150">Hit count type</span></span>|<span data-ttu-id="d6fd7-151">Description</span><span class="sxs-lookup"><span data-stu-id="d6fd7-151">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="d6fd7-152">항상</span><span class="sxs-lookup"><span data-stu-id="d6fd7-152">Always</span></span>|<span data-ttu-id="d6fd7-153">중단점에 도달하면 실행이 항상 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-153">Execution is always suspended when the breakpoint is hit.</span></span>|
|<span data-ttu-id="d6fd7-154">다음과 같은 적중 횟수</span><span class="sxs-lookup"><span data-stu-id="d6fd7-154">Hit count equals</span></span>|<span data-ttu-id="d6fd7-155">중단점이 발생한 횟수가 적중 횟수와 같으면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-155">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|
|<span data-ttu-id="d6fd7-156">다음보다 크거나 같은 적중 횟수</span><span class="sxs-lookup"><span data-stu-id="d6fd7-156">Hit count greater than or equal to</span></span>|<span data-ttu-id="d6fd7-157">중단점이 발생한 횟수가 적중 횟수보다 크거나 같으면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-157">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|
|<span data-ttu-id="d6fd7-158">다음 배수의 적중 횟수</span><span class="sxs-lookup"><span data-stu-id="d6fd7-158">Hit count multiple</span></span>|<span data-ttu-id="d6fd7-159">적중 횟수의 배수가 되면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-159">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="d6fd7-160">예를 들어 이 옵션을 5로 설정하면 5번째 중단점마다 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-160">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|

#### <a name="to-set-breakpoints"></a><span data-ttu-id="d6fd7-161">중단점을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d6fd7-161">To set breakpoints</span></span>

-   [<span data-ttu-id="d6fd7-162">태스크 또는 컨테이너에 중단점을 설정하여 패키지 디버깅</span><span class="sxs-lookup"><span data-stu-id="d6fd7-162">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)

## <a name="progress-reporting"></a><span data-ttu-id="d6fd7-163">진행률 보고</span><span class="sxs-lookup"><span data-stu-id="d6fd7-163">Progress Reporting</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="d6fd7-164">디자이너에는 **제어 흐름** 탭의 디자인 화면상의 색 구분 기능과 **진행률** 탭에 표시되는 진행률 메시지의 두 가지 진행률 보고 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-164">Designer includes two types of progress reporting: color-coding on the design surface of the **Control Flow** tab, and progress messages on the **Progress** tab.</span></span>

 <span data-ttu-id="d6fd7-165">패키지를 실행할 때 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너는 실행 상태를 나타내는 색을 사용하여 각 태스크나 컨테이너를 표시하여 실행 진행 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-165">When you run a package, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer depicts execution progress by displaying each task or container using a color that indicates execution status.</span></span> <span data-ttu-id="d6fd7-166">색을 보면 요소가 실행 대기 중인지, 현재 실행 중인지, 성공적으로 완료되었는지 또는 오류가 발생하여 종료되었는지를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-166">You can tell by its color whether the element is waiting to run, currently running, has completed successfully, or has ended unsuccessfully.</span></span> <span data-ttu-id="d6fd7-167">패키지 실행을 중지한 다음에는 색 구분이 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-167">After you stop package execution, the color-coding disappears.</span></span>

 <span data-ttu-id="d6fd7-168">다음 표에서는 실행 상태를 보여 주는 데 사용되는 색에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-168">The following table describes the colors that are used to depict execution status.</span></span>

|<span data-ttu-id="d6fd7-169">색</span><span class="sxs-lookup"><span data-stu-id="d6fd7-169">Color</span></span>|<span data-ttu-id="d6fd7-170">실행 상태</span><span class="sxs-lookup"><span data-stu-id="d6fd7-170">Execution status</span></span>|
|-----------|----------------------|
|<span data-ttu-id="d6fd7-171">회색</span><span class="sxs-lookup"><span data-stu-id="d6fd7-171">Gray</span></span>|<span data-ttu-id="d6fd7-172">실행 대기 중</span><span class="sxs-lookup"><span data-stu-id="d6fd7-172">Waiting to run</span></span>|
|<span data-ttu-id="d6fd7-173">노란색</span><span class="sxs-lookup"><span data-stu-id="d6fd7-173">Yellow</span></span>|<span data-ttu-id="d6fd7-174">실행 중</span><span class="sxs-lookup"><span data-stu-id="d6fd7-174">Running</span></span>|
|<span data-ttu-id="d6fd7-175">녹색</span><span class="sxs-lookup"><span data-stu-id="d6fd7-175">Green</span></span>|<span data-ttu-id="d6fd7-176">성공적으로 실행됨</span><span class="sxs-lookup"><span data-stu-id="d6fd7-176">Ran successfully</span></span>|
|<span data-ttu-id="d6fd7-177">강조 표시됨</span><span class="sxs-lookup"><span data-stu-id="d6fd7-177">highlighted</span></span>|<span data-ttu-id="d6fd7-178">실행 중 오류 발생</span><span class="sxs-lookup"><span data-stu-id="d6fd7-178">Ran with errors</span></span>|

 <span data-ttu-id="d6fd7-179">**진행률** 탭에는 실행 순서별로 태스크와 컨테이너가 나열되며 시작 및 종료 횟수, 경고 및 오류 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-179">The **Progress** tab lists tasks and containers in execution order and includes the start and finish times, warnings, and error messages.</span></span> <span data-ttu-id="d6fd7-180">패키지 실행을 중지한 후에도 진행률 정보는 **실행 결과** 탭에 활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-180">After you stop package execution, the progress information remains available on the **Execution Results** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="d6fd7-181">**진행률** 탭에 메시지를 표시할지 여부는 **SSIS** 메뉴의 **디버그 진행률 보고** 옵션을 선택 또는 선택 취소하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-181">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

 <span data-ttu-id="d6fd7-182">다음 다이어그램에서는 **진행률** 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-182">The following diagram shows the **Progress** tab.</span></span>

 <span data-ttu-id="d6fd7-183">![SSIS 디자이너의 진행률 탭](../media/mw-dtsflow04.gif "SSIS 디자이너의 진행률 탭")</span><span class="sxs-lookup"><span data-stu-id="d6fd7-183">![Progress tab of SSIS Designer](../media/mw-dtsflow04.gif "Progress tab of SSIS Designer")</span></span>

## <a name="debug-windows"></a><span data-ttu-id="d6fd7-184">디버그 창</span><span class="sxs-lookup"><span data-stu-id="d6fd7-184">Debug Windows</span></span>
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="d6fd7-185">에는 중단점을 사용하고, 중단점이 포함된 패키지를 디버깅하는 데 사용할 수 있는 여러 창이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-185">includes many windows that you can use to work with breakpoints, and to debug packages that contain breakpoints.</span></span> <span data-ttu-id="d6fd7-186">각 창에 대한 자세한 내용을 알아보려면 F1을 눌러서 해당 창에 대한 도움말을 표시하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-186">To learn more about each window, open the window, and then press F1 to display Help for the window.</span></span>

 <span data-ttu-id="d6fd7-187">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 이러한 창을 열려면 **디버그** 메뉴를 클릭하고 **창**을 가리킨 다음 **중단점**, **출력**또는 **직접 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-187">To open these windows in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], click the **Debug** menu, point to **Windows**, and then click **Breakpoints**, **Output**, or **Immediate**.</span></span>

 <span data-ttu-id="d6fd7-188">다음 표에서는 이러한 창에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-188">The following table describes the windows.</span></span>

|<span data-ttu-id="d6fd7-189">시간 범위</span><span class="sxs-lookup"><span data-stu-id="d6fd7-189">Window</span></span>|<span data-ttu-id="d6fd7-190">Description</span><span class="sxs-lookup"><span data-stu-id="d6fd7-190">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="d6fd7-191">중단점</span><span class="sxs-lookup"><span data-stu-id="d6fd7-191">Breakpoints</span></span>|<span data-ttu-id="d6fd7-192">패키지에 있는 중단점을 나열하고 중단점을 설정 및 해제할 수 있는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-192">Lists the breakpoints in a package and provides options to enable and delete breakpoints.</span></span>|
|<span data-ttu-id="d6fd7-193">출력</span><span class="sxs-lookup"><span data-stu-id="d6fd7-193">Output</span></span>|<span data-ttu-id="d6fd7-194">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 기능에 대한 상태 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-194">Displays status messages for features in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|
|<span data-ttu-id="d6fd7-195">즉시</span><span class="sxs-lookup"><span data-stu-id="d6fd7-195">Immediate</span></span>|<span data-ttu-id="d6fd7-196">식을 디버깅 및 계산하고 변수 값을 출력하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6fd7-196">Used to debug and evaluate expressions and print variable values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d6fd7-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6fd7-197">See Also</span></span>
 [<span data-ttu-id="d6fd7-198">패키지 배포 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="d6fd7-198">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)


