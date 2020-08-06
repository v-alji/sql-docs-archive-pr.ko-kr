---
title: 메일 보내기 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c93723f3c443705acc14226ce07f456da4d5a884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647796"
---
# <a name="send-mail-task"></a><span data-ttu-id="d32e1-102">메일 보내기 태스크</span><span class="sxs-lookup"><span data-stu-id="d32e1-102">Send Mail Task</span></span>
  <span data-ttu-id="d32e1-103">메일 보내기 태스크는 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-103">The Send Mail task sends an e-mail message.</span></span> <span data-ttu-id="d32e1-104">메일 보내기 태스크를 사용하면 패키지 워크플로의 태스크 성공 여부에 관계없이 패키지가 메시지를 보낼 수 있거나 런타임 시 패키지에서 발생한 이벤트에 응답하여 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-104">By using the Send Mail task, a package can send messages if tasks in the package workflow succeed or fail, or send messages in response to an event that the package raises at run time.</span></span> <span data-ttu-id="d32e1-105">예를 들어 이 태스크는 데이터베이스 백업 태스크의 성공 또는 실패에 대해 데이터베이스 관리자에게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-105">For example, the task can notify a database administrator about the success or failure of the Backup Database task.</span></span>  
  
 <span data-ttu-id="d32e1-106">다음과 같은 방법으로 메일 보내기 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-106">You can configure the Send Mail task in the following ways:</span></span>  
  
-   <span data-ttu-id="d32e1-107">전자 메일 메시지의 메시지 텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-107">Provide the message text for the e-mail message.</span></span>  
  
-   <span data-ttu-id="d32e1-108">전자 메일 메시지의 제목 줄을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-108">Provide a subject line for the e-mail message.</span></span>  
  
-   <span data-ttu-id="d32e1-109">메시지의 우선 순위 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-109">Set the priority level of the message.</span></span> <span data-ttu-id="d32e1-110">이 태스크는 보통, 낮음 및 높음의 3가지 우선 순위 수준을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-110">The task supports three priority levels: normal, low, and high.</span></span>  
  
-   <span data-ttu-id="d32e1-111">받는 사람, 참조 및 숨은 참조 줄의 받는 사람을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-111">Specify the recipients on the To, Cc, and Bcc lines.</span></span> <span data-ttu-id="d32e1-112">태스크에서 받는 사람을 여러 명 지정하면 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-112">If the task specifies multiple recipients, they are separated by semicolons.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d32e1-113">인터넷 표준에 따라 받는 사람, 참조 및 숨은 참조 줄은 각각 256자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-113">The To, Cc, and Bcc lines are limited to 256 characters each in accordance with Internet standards.</span></span>  
  
-   <span data-ttu-id="d32e1-114">첨부 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-114">Include attachments.</span></span> <span data-ttu-id="d32e1-115">태스크에서 첨부 파일을 여러 개 지정하면 파이프(|) 문자로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-115">If the task specifies multiple attachments, they are separated by the pipe (|) character.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d32e1-116">패키지를 실행할 때 첨부 파일이 없으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-116">If an attachment file does not exist when the package runs, an error occurs.</span></span>  
  
-   <span data-ttu-id="d32e1-117">사용할 SMTP 연결 관리자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-117">Specify the SMTP connection manager to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d32e1-118">SMTP 연결 관리자는 익명 인증과 Windows 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="d32e1-118">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="d32e1-119">기본 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-119">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="d32e1-120">메시지 텍스트는 사용자가 제공한 문자열, 텍스트가 포함된 파일에 대한 연결 또는 텍스트가 포함된 변수 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-120">The message text can be a string that you provide, a connection to a file that contains the text, or the name of a variable that contains the text.</span></span> <span data-ttu-id="d32e1-121">이 태스크는 파일 연결 관리자를 사용하여 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-121">The task uses a File connection manager to connect to a file.</span></span> <span data-ttu-id="d32e1-122">자세한 내용은 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d32e1-122">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d32e1-123">이 태스크는 SMTP 연결 관리자를 사용하여 메일 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-123">The task uses an SMTP connection manager to connect to a mail server.</span></span> <span data-ttu-id="d32e1-124">자세한 내용은 [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d32e1-124">For more information, see [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a><span data-ttu-id="d32e1-125">메일 보내기 태스크에 사용할 수 있는 사용자 지정 로깅 메시지</span><span class="sxs-lookup"><span data-stu-id="d32e1-125">Custom Logging Messages Available on the Send Mail Task</span></span>  
 <span data-ttu-id="d32e1-126">다음 표에서는 메일 보내기 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-126">The following table lists the custom log entries for the Send Mail task.</span></span> <span data-ttu-id="d32e1-127">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d32e1-127">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="d32e1-128">로그 항목</span><span class="sxs-lookup"><span data-stu-id="d32e1-128">Log entry</span></span>|<span data-ttu-id="d32e1-129">Description</span><span class="sxs-lookup"><span data-stu-id="d32e1-129">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="d32e1-130">태스크에서 전자 메일 메시지 보내기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-130">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="d32e1-131">태스크에서 전자 메일 메시지 보내기를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-131">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="d32e1-132">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-132">Provides descriptive information about the task.</span></span>|  
  
## <a name="configuring-the-send-mail-task"></a><span data-ttu-id="d32e1-133">메일 보내기 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="d32e1-133">Configuring the Send Mail Task</span></span>  
 <span data-ttu-id="d32e1-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-134">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d32e1-135">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d32e1-135">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d32e1-136">메일 보내기 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d32e1-136">Send Mail Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="d32e1-137">메일 보내기 태스크 편집기&#40;메일 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d32e1-137">Send Mail Task Editor &#40;Mail Page&#41;</span></span>](../send-mail-task-editor-mail-page.md)  
  
-   [<span data-ttu-id="d32e1-138">식 페이지</span><span class="sxs-lookup"><span data-stu-id="d32e1-138">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="d32e1-139">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d32e1-139">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="d32e1-140">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d32e1-140">Related Tasks</span></span>  
 <span data-ttu-id="d32e1-141">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d32e1-141">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d32e1-142">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d32e1-142">Related Content</span></span>  
  
-   <span data-ttu-id="d32e1-143">shareourideas.com의 기술 문서 - [C#의 배달 알림으로 메일을 보내는 방법](https://go.microsoft.com/fwlink/?LinkId=237625)</span><span class="sxs-lookup"><span data-stu-id="d32e1-143">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d32e1-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d32e1-144">See Also</span></span>  
 <span data-ttu-id="d32e1-145">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d32e1-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="d32e1-146">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="d32e1-146">Control Flow</span></span>](control-flow.md)  
  
  
