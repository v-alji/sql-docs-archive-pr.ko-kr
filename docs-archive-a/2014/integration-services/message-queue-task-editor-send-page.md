---
title: 메시지 큐 태스크 편집기 (보내기 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3534e1a8b475f22064ef7f2283c2e70eb561294f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743355"
---
# <a name="message-queue-task-editor-send-page"></a><span data-ttu-id="bc394-102">메시지 큐 태스크 편집기(보내기 페이지)</span><span class="sxs-lookup"><span data-stu-id="bc394-102">Message Queue Task Editor (Send Page)</span></span>
  <span data-ttu-id="bc394-103">**메시지 큐 태스크 편집기** 대화 상자의 **보내기** 페이지를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에서 메시지를 보내도록 메시지 큐 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-103">Use the **Send** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to send messages from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="bc394-104">이 태스크에 대한 자세한 내용은 [Message Queue Task](control-flow/message-queue-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc394-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bc394-105">옵션</span><span class="sxs-lookup"><span data-stu-id="bc394-105">Options</span></span>  
 <span data-ttu-id="bc394-106">**UseEncryption**</span><span class="sxs-lookup"><span data-stu-id="bc394-106">**UseEncryption**</span></span>  
 <span data-ttu-id="bc394-107">메시지 암호화 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-107">Indicate whether to encrypt the message.</span></span> <span data-ttu-id="bc394-108">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-108">The default is `False`.</span></span>  
  
 <span data-ttu-id="bc394-109">**EncryptionAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="bc394-109">**EncryptionAlgorithm**</span></span>  
 <span data-ttu-id="bc394-110">암호화 사용을 선택한 경우 사용할 암호화 알고리즘의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-110">If you choose to use encryption, specify the name of the encryption algorithm to use.</span></span> <span data-ttu-id="bc394-111">메시지 큐 태스크에는 RC2 및 RC4 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-111">The Message Queue task can use the RC2 and RC4 algorithms.</span></span> <span data-ttu-id="bc394-112">기본값은 **RC2**입니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-112">The default is **RC2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc394-113">RC4 알고리즘은 이전 버전과의 호환성을 위해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-113">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="bc394-114">데이터베이스의 호환성 수준이 90 또는 100인 경우 새 자료는 RC4 또는 RC4_128로만 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-114">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="bc394-115">이 옵션은 사용하지 않는 것이 좋습니다. 대신 AES 알고리즘 중 하나와 같은 새 알고리즘을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc394-115">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="bc394-116">현재 릴리스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 RC4 또는 RC4_128을 사용하여 암호화된 자료는 모든 호환성 수준에서 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-116">In the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc394-117">이러한 알고리즘은 MSMQ(메시지 큐) 기술에서 지원하는 암호화 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-117">These are the encryption algorithms that the Message Queuing (also known as MSMQ) technology supports.</span></span> <span data-ttu-id="bc394-118">이 두 암호화 알고리즘은 메시지 큐에서 현재 지원하지 않는 최신 알고리즘에 비해 암호화 방식이 취약한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-118">Both of these encryption algorithms are now considered cryptographically weak compared to newer algorithms, which Message Queuing does not yet support.</span></span> <span data-ttu-id="bc394-119">따라서 메시지 큐 태스크를 사용하여 메시지를 전송할 때는 암호화 요구를 신중하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-119">Therefore, you should consider your cryptography needs carefully when sending messages using the Message Queue task.</span></span>  
  
 <span data-ttu-id="bc394-120">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="bc394-120">**MessageType**</span></span>  
 <span data-ttu-id="bc394-121">메시지 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-121">Select the message type.</span></span> <span data-ttu-id="bc394-122">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-122">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="bc394-123">값</span><span class="sxs-lookup"><span data-stu-id="bc394-123">Value</span></span>|<span data-ttu-id="bc394-124">Description</span><span class="sxs-lookup"><span data-stu-id="bc394-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bc394-125">**데이터 파일 메시지**</span><span class="sxs-lookup"><span data-stu-id="bc394-125">**Data file message**</span></span>|<span data-ttu-id="bc394-126">메시지가 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-126">The message is stored in a file.</span></span> <span data-ttu-id="bc394-127">이 값을 선택하면 동적 옵션 **DataFileMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-127">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="bc394-128">**변수 메시지**</span><span class="sxs-lookup"><span data-stu-id="bc394-128">**Variable message**</span></span>|<span data-ttu-id="bc394-129">메시지가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-129">The message is stored in a variable.</span></span> <span data-ttu-id="bc394-130">이 값을 선택하면 동적 옵션 **VariableMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-130">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="bc394-131">**문자열 메시지**</span><span class="sxs-lookup"><span data-stu-id="bc394-131">**String message**</span></span>|<span data-ttu-id="bc394-132">메시지가 메시지 큐 태스크에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-132">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="bc394-133">이 값을 선택하면 동적 옵션 **StringMessage**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-133">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="bc394-134">MessageType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="bc394-134">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="bc394-135">MessageType = 데이터 파일 메시지</span><span class="sxs-lookup"><span data-stu-id="bc394-135">MessageType = Data file message</span></span>  
 <span data-ttu-id="bc394-136">**DataFileMessage**</span><span class="sxs-lookup"><span data-stu-id="bc394-136">**DataFileMessage**</span></span>  
 <span data-ttu-id="bc394-137">데이터 파일의 경로를 입력하거나 줄임표 **(...)** 를 클릭한 다음, 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-137">Type the path of the data file, or click the ellipsis **(...)** and then locate the file.</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="bc394-138">MessageType = 변수 메시지</span><span class="sxs-lookup"><span data-stu-id="bc394-138">MessageType = Variable message</span></span>  
 <span data-ttu-id="bc394-139">**VariableMessage**</span><span class="sxs-lookup"><span data-stu-id="bc394-139">**VariableMessage**</span></span>  
 <span data-ttu-id="bc394-140">변수 이름을 입력하거나 줄임표 **(...)** 를 클릭한 다음, 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-140">Type the variable names, or click the ellipsis **(...)** and then select the variables.</span></span> <span data-ttu-id="bc394-141">변수는 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-141">Variables are separated by commas.</span></span>  
  
 <span data-ttu-id="bc394-142">**관련 항목:** 변수 선택</span><span class="sxs-lookup"><span data-stu-id="bc394-142">**Related Topics:** Select Variables</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="bc394-143">MessageType = 문자열 메시지</span><span class="sxs-lookup"><span data-stu-id="bc394-143">MessageType = String message</span></span>  
 <span data-ttu-id="bc394-144">**StringMessage**</span><span class="sxs-lookup"><span data-stu-id="bc394-144">**StringMessage**</span></span>  
 <span data-ttu-id="bc394-145">문자열 메시지를 입력하거나 줄임표 **(...)** 를 클릭한 다음, **문자열 메시지 입력** 대화 상자에 메시지를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-145">Type the string message, or click the ellipsis **(...)** and then type the message in the **Enter String Message** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc394-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc394-146">See Also</span></span>  
 <span data-ttu-id="bc394-147">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bc394-147">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bc394-148">[메시지 큐 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bc394-148">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bc394-149">[메시지 큐 태스크 편집기 &#40;수신 페이지&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="bc394-149">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 [<span data-ttu-id="bc394-150">식 페이지</span><span class="sxs-lookup"><span data-stu-id="bc394-150">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
