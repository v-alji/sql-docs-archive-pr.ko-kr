---
title: 메일 보내기 태스크 편집기 (메일 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52cab62f3c88ea248b76061664547fd8f1314099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742407"
---
# <a name="send-mail-task-editor-mail-page"></a><span data-ttu-id="3d79a-102">메일 보내기 태스크 편집기(메일 페이지)</span><span class="sxs-lookup"><span data-stu-id="3d79a-102">Send Mail Task Editor (Mail Page)</span></span>
  <span data-ttu-id="3d79a-103">**메일 보내기 태스크 편집기** 대화 상자의 **메일** 페이지를 사용하여 받는 사람, 메시지 유형 및 메시지 우선 순위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-103">Use the **Mail** page of the **Send Mail Task Editor** dialog box to specify recipients, message type, and priority for a message.</span></span> <span data-ttu-id="3d79a-104">또한 메시지에 파일을 첨부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-104">You can also attach files to the message.</span></span> <span data-ttu-id="3d79a-105">메시지 텍스트는 사용자가 제공한 문자열, 텍스트가 포함된 파일에 대한 파일 연결 또는 텍스트가 포함된 변수 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-105">The message text can be a string you provide, a file connection to a file that contains the text, or the name of a variable that contains the text.</span></span>  
  
 <span data-ttu-id="3d79a-106">이 태스크에 대한 자세한 내용은 [Send Mail Task](control-flow/send-mail-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3d79a-106">To learn about this task, see [Send Mail Task](control-flow/send-mail-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d79a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="3d79a-107">Options</span></span>  
 <span data-ttu-id="3d79a-108">**SMTPConnection**</span><span class="sxs-lookup"><span data-stu-id="3d79a-108">**SMTPConnection**</span></span>  
 <span data-ttu-id="3d79a-109">목록에서 SMTP 연결 관리자를 선택하거나 **\<New connection...>** 을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-109">Select an SMTP connection manager in the list, or click **\<New connection...>** to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d79a-110">SMTP 연결 관리자는 익명 인증과 Windows 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="3d79a-110">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="3d79a-111">기본 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-111">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="3d79a-112">**관련 항목:** [SMTP 연결 관리자](connection-manager/smtp-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="3d79a-112">**Related Topics:** [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)</span></span>  
  
 <span data-ttu-id="3d79a-113">**From**</span><span class="sxs-lookup"><span data-stu-id="3d79a-113">**From**</span></span>  
 <span data-ttu-id="3d79a-114">보낸 사람의 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-114">Specify the e-mail address of the sender.</span></span>  
  
 <span data-ttu-id="3d79a-115">**수행할 작업**</span><span class="sxs-lookup"><span data-stu-id="3d79a-115">**To**</span></span>  
 <span data-ttu-id="3d79a-116">받는 사람의 전자 메일 주소를 세미콜론으로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-116">Provide the e-mail addresses of the recipients, delimited by semicolons.</span></span>  
  
 <span data-ttu-id="3d79a-117">**Cc**</span><span class="sxs-lookup"><span data-stu-id="3d79a-117">**Cc**</span></span>  
 <span data-ttu-id="3d79a-118">메시지의 복사본을 받을 사람의 전자 메일 주소를 세미콜론으로 구분하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-118">Specify the e-mail addresses, delimited by semicolons, of individuals who also receive copies of the message.</span></span>  
  
 <span data-ttu-id="3d79a-119">**Bcc**</span><span class="sxs-lookup"><span data-stu-id="3d79a-119">**Bcc**</span></span>  
 <span data-ttu-id="3d79a-120">메시지의 숨은 참조 복사본을 받을 사람의 전자 메일 주소를 세미콜론으로 구분하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-120">Specify the e-mail addresses, delimited by semicolons, of individuals who receive blind carbon copies (Bcc) copies of the message.</span></span>  
  
 <span data-ttu-id="3d79a-121">**Subject**</span><span class="sxs-lookup"><span data-stu-id="3d79a-121">**Subject**</span></span>  
 <span data-ttu-id="3d79a-122">전자 메일 메시지의 제목을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-122">Provide a subject for the e-mail message.</span></span>  
  
 <span data-ttu-id="3d79a-123">**MessageSourceType**</span><span class="sxs-lookup"><span data-stu-id="3d79a-123">**MessageSourceType**</span></span>  
 <span data-ttu-id="3d79a-124">메시지의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-124">Select the source type of the message.</span></span> <span data-ttu-id="3d79a-125">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-125">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="3d79a-126">값</span><span class="sxs-lookup"><span data-stu-id="3d79a-126">Value</span></span>|<span data-ttu-id="3d79a-127">Description</span><span class="sxs-lookup"><span data-stu-id="3d79a-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d79a-128">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="3d79a-128">**Direct input**</span></span>|<span data-ttu-id="3d79a-129">원본을 메시지 텍스트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-129">Set the source to the message text.</span></span> <span data-ttu-id="3d79a-130">이 값을 선택하면 동적 옵션 **MessageSource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-130">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="3d79a-131">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="3d79a-131">**File connection**</span></span>|<span data-ttu-id="3d79a-132">원본을 메시지 텍스트가 포함된 파일로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-132">Set the source to the file that contains the message text.</span></span> <span data-ttu-id="3d79a-133">이 값을 선택하면 동적 옵션 **MessageSource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-133">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="3d79a-134">**변수**</span><span class="sxs-lookup"><span data-stu-id="3d79a-134">**Variable**</span></span>|<span data-ttu-id="3d79a-135">원본을 메시지 텍스트가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-135">Set the source to a variable that contains the message text.</span></span> <span data-ttu-id="3d79a-136">이 값을 선택하면 동적 옵션 **MessageSource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-136">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
  
 <span data-ttu-id="3d79a-137">**우선 순위**</span><span class="sxs-lookup"><span data-stu-id="3d79a-137">**Priority**</span></span>  
 <span data-ttu-id="3d79a-138">메시지의 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-138">Set the priority of the message.</span></span>  
  
 <span data-ttu-id="3d79a-139">**Attachments**</span><span class="sxs-lookup"><span data-stu-id="3d79a-139">**Attachments**</span></span>  
 <span data-ttu-id="3d79a-140">전자 메일 메시지에 첨부하는 파일의 이름을 파이프(|)로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-140">Provide the file names of attachments to the e-mail message, delimited by the pipe (|) character.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d79a-141">인터넷 표준에 따라 받는 사람, 참조 및 숨은 참조 줄은 각각 256자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-141">The To, Cc, and Bcc lines are limited to 256 characters in accordance with Internet standards.</span></span>  
  
## <a name="messagesourcetype-dynamic-options"></a><span data-ttu-id="3d79a-142">MessageSourceType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="3d79a-142">MessageSourceType Dynamic Options</span></span>  
  
### <a name="messagesourcetype--direct-input"></a><span data-ttu-id="3d79a-143">MessageSourceType = 직접 입력</span><span class="sxs-lookup"><span data-stu-id="3d79a-143">MessageSourceType = Direct Input</span></span>  
 <span data-ttu-id="3d79a-144">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="3d79a-144">**MessageSource**</span></span>  
 <span data-ttu-id="3d79a-145">메시지 텍스트를 입력하거나 찾아보기 단추(...)를 클릭한 다음, **메시지 원본** 대화 상자에 메시지를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-145">Type the message text or click the browse button (...) and then type the message in the **Message source** dialog box.</span></span>  
  
### <a name="messagesourcetype--file-connection"></a><span data-ttu-id="3d79a-146">MessageSourceType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="3d79a-146">MessageSourceType = File connection</span></span>  
 <span data-ttu-id="3d79a-147">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="3d79a-147">**MessageSource**</span></span>  
 <span data-ttu-id="3d79a-148">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-148">Select a File connection manager in the list or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="3d79a-149">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="3d79a-149">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="messagesourcetype--variable"></a><span data-ttu-id="3d79a-150">MessageSourceType = 변수</span><span class="sxs-lookup"><span data-stu-id="3d79a-150">MessageSourceType = Variable</span></span>  
 <span data-ttu-id="3d79a-151">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="3d79a-151">**MessageSource**</span></span>  
 <span data-ttu-id="3d79a-152">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d79a-152">Select a variable in the list or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="3d79a-153">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="3d79a-153">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d79a-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d79a-154">See Also</span></span>  
 <span data-ttu-id="3d79a-155">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3d79a-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3d79a-156">[메일 보내기 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3d79a-156">[Send Mail Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="3d79a-157">식 페이지</span><span class="sxs-lookup"><span data-stu-id="3d79a-157">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
