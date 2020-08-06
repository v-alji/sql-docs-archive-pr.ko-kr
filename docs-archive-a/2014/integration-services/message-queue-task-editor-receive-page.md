---
title: 메시지 큐 태스크 편집기 (받기 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f45aa579d37d1fdd3a3124eea972014ce839fdc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743356"
---
# <a name="message-queue-task-editor-receive-page"></a><span data-ttu-id="40976-102">메시지 큐 태스크 편집기(받기 페이지)</span><span class="sxs-lookup"><span data-stu-id="40976-102">Message Queue Task Editor (Receive Page)</span></span>
  <span data-ttu-id="40976-103">**메시지 큐 태스크 편집기** 대화 상자의 **받기** 페이지를 사용하여 메시지 큐 태스크가 MSMQ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing) 메시지를 받도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-103">Use the **Receive** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to receive [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) messages.</span></span>  
  
 <span data-ttu-id="40976-104">이 태스크에 대한 자세한 내용은 [Message Queue Task](control-flow/message-queue-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="40976-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="40976-105">옵션</span><span class="sxs-lookup"><span data-stu-id="40976-105">Options</span></span>  
 <span data-ttu-id="40976-106">**RemoveFromMessageQueue**</span><span class="sxs-lookup"><span data-stu-id="40976-106">**RemoveFromMessageQueue**</span></span>  
 <span data-ttu-id="40976-107">메시지를 받은 후 큐에서 제거할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="40976-107">Indicate whether to remove the message from the queue after it is received.</span></span> <span data-ttu-id="40976-108">기본적으로 이 값은 `False`로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-108">By default, this value is set to `False`.</span></span>  
  
 <span data-ttu-id="40976-109">**ErrorIfMessageTimeOut**</span><span class="sxs-lookup"><span data-stu-id="40976-109">**ErrorIfMessageTimeOut**</span></span>  
 <span data-ttu-id="40976-110">메시지 제한 시간이 초과할 경우 태스크 실패로 처리하고 오류 메시지를 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="40976-110">Indicate whether the task fails when the message times out, displaying an error message.</span></span> <span data-ttu-id="40976-111">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="40976-111">The default is `False`.</span></span>  
  
 <span data-ttu-id="40976-112">**TimeoutAfter**</span><span class="sxs-lookup"><span data-stu-id="40976-112">**TimeoutAfter**</span></span>  
 <span data-ttu-id="40976-113">태스크 실패 시 오류 메시지를 표시하도록 선택하는 경우 제한 시간 오류 메시지가 표시될 때까지 기다리는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-113">If you choose to display an error message on task failure, specify the number of seconds to wait before displaying the time-out message.</span></span>  
  
 <span data-ttu-id="40976-114">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="40976-114">**MessageType**</span></span>  
 <span data-ttu-id="40976-115">메시지 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-115">Select the message type.</span></span> <span data-ttu-id="40976-116">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-116">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="40976-117">값</span><span class="sxs-lookup"><span data-stu-id="40976-117">Value</span></span>|<span data-ttu-id="40976-118">Description</span><span class="sxs-lookup"><span data-stu-id="40976-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40976-119">**데이터 파일 메시지**</span><span class="sxs-lookup"><span data-stu-id="40976-119">**Data file message**</span></span>|<span data-ttu-id="40976-120">메시지가 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-120">The message is stored in a file.</span></span> <span data-ttu-id="40976-121">이 값을 선택하면 동적 옵션 **DataFileMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-121">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="40976-122">**변수 메시지**</span><span class="sxs-lookup"><span data-stu-id="40976-122">**Variable message**</span></span>|<span data-ttu-id="40976-123">메시지가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-123">The message is stored in a variable.</span></span> <span data-ttu-id="40976-124">이 값을 선택하면 동적 옵션 **VariableMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-124">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="40976-125">**문자열 메시지**</span><span class="sxs-lookup"><span data-stu-id="40976-125">**String message**</span></span>|<span data-ttu-id="40976-126">메시지가 메시지 큐 태스크에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-126">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="40976-127">이 값을 선택하면 동적 옵션 **StringMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-127">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
|<span data-ttu-id="40976-128">**변수에 대한 문자열 메시지**</span><span class="sxs-lookup"><span data-stu-id="40976-128">**String message to variable**</span></span>|<span data-ttu-id="40976-129">메시지</span><span class="sxs-lookup"><span data-stu-id="40976-129">The message</span></span><br /><br /> <span data-ttu-id="40976-130">이 값을 선택하면 동적 옵션 **StringMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-130">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="40976-131">MessageType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="40976-131">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="40976-132">MessageType = 데이터 파일 메시지</span><span class="sxs-lookup"><span data-stu-id="40976-132">MessageType = Data file message</span></span>  
 <span data-ttu-id="40976-133">**SaveFileAs**</span><span class="sxs-lookup"><span data-stu-id="40976-133">**SaveFileAs**</span></span>  
 <span data-ttu-id="40976-134">사용할 파일의 경로를 입력하거나 줄임표 단추 **(...)** 를 클릭한 다음, 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-134">Type the path of the file to use, or click the ellipsis button **(...)** and then locate the file.</span></span>  
  
 <span data-ttu-id="40976-135">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="40976-135">**Overwrite**</span></span>  
 <span data-ttu-id="40976-136">데이터 파일 메시지의 내용을 저장할 경우 기존 파일의 데이터를 덮어쓸지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="40976-136">Indicate whether to overwrite the data in an existing file when saving the contents of a data file message.</span></span> <span data-ttu-id="40976-137">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="40976-137">The default is `False`.</span></span>  
  
 <span data-ttu-id="40976-138">**Filter**</span><span class="sxs-lookup"><span data-stu-id="40976-138">**Filter**</span></span>  
 <span data-ttu-id="40976-139">필터를 메시지에 적용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-139">Specify whether to apply a filter to the message.</span></span> <span data-ttu-id="40976-140">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="40976-141">값</span><span class="sxs-lookup"><span data-stu-id="40976-141">Value</span></span>|<span data-ttu-id="40976-142">Description</span><span class="sxs-lookup"><span data-stu-id="40976-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40976-143">**필터 없음**</span><span class="sxs-lookup"><span data-stu-id="40976-143">**No filter**</span></span>|<span data-ttu-id="40976-144">태스크에서 메시지를 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-144">The task does not filter messages.</span></span> <span data-ttu-id="40976-145">이 값을 선택하면 동적 옵션 **IdentifierReadOnly**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-145">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="40976-146">**받을 패키지**</span><span class="sxs-lookup"><span data-stu-id="40976-146">**From package**</span></span>|<span data-ttu-id="40976-147">메시지는 지정한 패키지의 메시지만 받습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-147">The message receives only messages from the specified package.</span></span> <span data-ttu-id="40976-148">이 값을 선택하면 동적 옵션 **Identifier**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-148">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="40976-149">Filter 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="40976-149">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="40976-150">Filter = 필터 없음</span><span class="sxs-lookup"><span data-stu-id="40976-150">Filter = No filter</span></span>  
 <span data-ttu-id="40976-151">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="40976-151">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="40976-152">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="40976-152">This option is read-only.</span></span> <span data-ttu-id="40976-153">이전에 Filter 속성을 설정할 때 이 옵션은 비어 있거나 패키지의 GUID를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-153">It may be blank or contain the GUID of a package when the Filter property was previously set.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="40976-154">Filter = 받을 패키지</span><span class="sxs-lookup"><span data-stu-id="40976-154">Filter = From package</span></span>  
 <span data-ttu-id="40976-155">**식별자**</span><span class="sxs-lookup"><span data-stu-id="40976-155">**Identifier**</span></span>  
 <span data-ttu-id="40976-156">필터를 적용하도록 선택한 경우 메시지를 받을 수 있는 패키지의 고유 식별자를 입력하거나 줄임표 단추 **(...)** 를 클릭한 다음, 패키지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-156">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="40976-157">**관련 항목:** [패키지 선택](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="40976-157">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="40976-158">MessageType = 변수 메시지</span><span class="sxs-lookup"><span data-stu-id="40976-158">MessageType = Variable message</span></span>  
 <span data-ttu-id="40976-159">**Filter**</span><span class="sxs-lookup"><span data-stu-id="40976-159">**Filter**</span></span>  
 <span data-ttu-id="40976-160">필터를 메시지에 적용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-160">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="40976-161">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-161">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="40976-162">값</span><span class="sxs-lookup"><span data-stu-id="40976-162">Value</span></span>|<span data-ttu-id="40976-163">Description</span><span class="sxs-lookup"><span data-stu-id="40976-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40976-164">**필터 없음**</span><span class="sxs-lookup"><span data-stu-id="40976-164">**No filter**</span></span>|<span data-ttu-id="40976-165">태스크에서 메시지를 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-165">The task does not filter messages.</span></span> <span data-ttu-id="40976-166">이 값을 선택하면 동적 옵션 **IdentifierReadOnly**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-166">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="40976-167">**받을 패키지**</span><span class="sxs-lookup"><span data-stu-id="40976-167">**From package**</span></span>|<span data-ttu-id="40976-168">메시지는 지정한 패키지의 메시지만 받습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-168">The message receives only messages from the specified package.</span></span> <span data-ttu-id="40976-169">이 값을 선택하면 동적 옵션 **Identifier**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40976-169">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
 <span data-ttu-id="40976-170">**변수**</span><span class="sxs-lookup"><span data-stu-id="40976-170">**Variable**</span></span>  
 <span data-ttu-id="40976-171">변수 이름을 입력하거나 \<**New variable...**>를 클릭한 다음, 새 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-171">Type the variable name, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="40976-172">**관련 항목:** [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="40976-172">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="40976-173">Filter 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="40976-173">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="40976-174">Filter = 필터 없음</span><span class="sxs-lookup"><span data-stu-id="40976-174">Filter = No filter</span></span>  
 <span data-ttu-id="40976-175">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="40976-175">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="40976-176">이 옵션은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-176">This option is blank.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="40976-177">Filter = 받을 패키지</span><span class="sxs-lookup"><span data-stu-id="40976-177">Filter = From package</span></span>  
 <span data-ttu-id="40976-178">**식별자**</span><span class="sxs-lookup"><span data-stu-id="40976-178">**Identifier**</span></span>  
 <span data-ttu-id="40976-179">필터를 적용하도록 선택한 경우 메시지를 받을 수 있는 패키지의 고유 식별자를 입력하거나 줄임표 단추 **(...)** 를 클릭한 다음, 패키지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-179">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="40976-180">**관련 항목:** [패키지 선택](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="40976-180">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="40976-181">MessageType = 문자열 메시지</span><span class="sxs-lookup"><span data-stu-id="40976-181">MessageType = String message</span></span>  
 <span data-ttu-id="40976-182">**비교**</span><span class="sxs-lookup"><span data-stu-id="40976-182">**Compare**</span></span>  
 <span data-ttu-id="40976-183">필터를 메시지에 적용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-183">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="40976-184">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-184">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="40976-185">값</span><span class="sxs-lookup"><span data-stu-id="40976-185">Value</span></span>|<span data-ttu-id="40976-186">Description</span><span class="sxs-lookup"><span data-stu-id="40976-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40976-187">**없음**</span><span class="sxs-lookup"><span data-stu-id="40976-187">**None**</span></span>|<span data-ttu-id="40976-188">메시지를 비교하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-188">Messages are not compared.</span></span>|  
|<span data-ttu-id="40976-189">**정확한 일치**</span><span class="sxs-lookup"><span data-stu-id="40976-189">**Exact match**</span></span>|<span data-ttu-id="40976-190">메시지가 **CompareString** 옵션의 문자열과 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-190">Messages must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="40976-191">**대/소문자 무시**</span><span class="sxs-lookup"><span data-stu-id="40976-191">**Ignore case**</span></span>|<span data-ttu-id="40976-192">메시지가 **CompareString** 옵션의 문자열과 일치해야 하지만 비교 시 대/소문자를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-192">Message must match the string in the **CompareString** option, but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="40976-193">**포함**</span><span class="sxs-lookup"><span data-stu-id="40976-193">**Containing**</span></span>|<span data-ttu-id="40976-194">메시지가 **CompareString** 옵션의 문자열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-194">Message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="40976-195">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="40976-195">**CompareString**</span></span>  
 <span data-ttu-id="40976-196">**Compare** 옵션을 **없음**으로 설정한 경우가 아니면 메시지를 비교할 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-196">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
### <a name="messagetype--string-message-to-variable"></a><span data-ttu-id="40976-197">MessageType = 변수에 대한 문자열 메시지</span><span class="sxs-lookup"><span data-stu-id="40976-197">MessageType = String message to variable</span></span>  
 <span data-ttu-id="40976-198">**비교**</span><span class="sxs-lookup"><span data-stu-id="40976-198">**Compare**</span></span>  
 <span data-ttu-id="40976-199">필터를 메시지에 적용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-199">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="40976-200">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-200">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="40976-201">값</span><span class="sxs-lookup"><span data-stu-id="40976-201">Value</span></span>|<span data-ttu-id="40976-202">Description</span><span class="sxs-lookup"><span data-stu-id="40976-202">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40976-203">**없음**</span><span class="sxs-lookup"><span data-stu-id="40976-203">**None**</span></span>|<span data-ttu-id="40976-204">메시지를 비교하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40976-204">Messages are not compared.</span></span>|  
|<span data-ttu-id="40976-205">**정확한 일치**</span><span class="sxs-lookup"><span data-stu-id="40976-205">**Exact match**</span></span>|<span data-ttu-id="40976-206">메시지가 **CompareString** 옵션의 문자열과 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-206">The message must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="40976-207">**대/소문자 무시**</span><span class="sxs-lookup"><span data-stu-id="40976-207">**Ignore case**</span></span>|<span data-ttu-id="40976-208">메시지가 **CompareString** 옵션의 문자열과 일치해야 하지만 비교 시 대/소문자를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-208">The message must match the string in the **CompareString** option but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="40976-209">**포함**</span><span class="sxs-lookup"><span data-stu-id="40976-209">**Containing**</span></span>|<span data-ttu-id="40976-210">메시지가 **CompareString** 옵션의 문자열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-210">The message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="40976-211">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="40976-211">**CompareString**</span></span>  
 <span data-ttu-id="40976-212">**Compare** 옵션을 **없음**으로 설정한 경우가 아니면 메시지를 비교할 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-212">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
 <span data-ttu-id="40976-213">**변수**</span><span class="sxs-lookup"><span data-stu-id="40976-213">**Variable**</span></span>  
 <span data-ttu-id="40976-214">받은 메시지를 보관할 변수의 이름을 입력하거나 \<**New variable...**>를 클릭한 다음, 새 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="40976-214">Type the name of the variable to hold the received message, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="40976-215">**관련 항목:** [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="40976-215">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40976-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40976-216">See Also</span></span>  
 <span data-ttu-id="40976-217">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="40976-217">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="40976-218">[메시지 큐 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="40976-218">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="40976-219">[메시지 큐 태스크 편집기 &#40;보내기 페이지&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="40976-219">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 <span data-ttu-id="40976-220">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="40976-220">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="40976-221">메시지 큐 태스크</span><span class="sxs-lookup"><span data-stu-id="40976-221">Message Queue Task</span></span>](control-flow/message-queue-task.md)  
  
  
