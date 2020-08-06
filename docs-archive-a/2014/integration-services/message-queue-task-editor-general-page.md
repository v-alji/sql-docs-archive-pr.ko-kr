---
title: 메시지 큐 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcec75f3a4dd85efb7c97226c592d6b1e1bb26ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661244"
---
# <a name="message-queue-task-editor-general-page"></a><span data-ttu-id="72f51-102">메시지 큐 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="72f51-102">Message Queue Task Editor (General Page)</span></span>
  <span data-ttu-id="72f51-103">**메시지 큐 태스크 편집기** 대화 상자의 **일반 페이지** 를 사용하여 메시지 큐 태스크의 이름을 지정하고 설명하며 메시지 형식을 지정하고 태스크에서 메시지를 보내거나 받을지를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-103">Use the **General page** of the **Message Queue Task Editor** dialog box to name and describe the Message Queue task, to specify the message format, and to indicate whether the task sends or receives messages.</span></span>  
  
 <span data-ttu-id="72f51-104">이 태스크에 대한 자세한 내용은 [Message Queue Task](control-flow/message-queue-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="72f51-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="72f51-105">옵션</span><span class="sxs-lookup"><span data-stu-id="72f51-105">Options</span></span>  
 <span data-ttu-id="72f51-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="72f51-106">**Name**</span></span>  
 <span data-ttu-id="72f51-107">메시지 큐 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-107">Provide a unique name for the Message Queue task.</span></span> <span data-ttu-id="72f51-108">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72f51-109">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="72f51-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="72f51-110">**Description**</span></span>  
 <span data-ttu-id="72f51-111">메시지 큐 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-111">Type a description of the Message Queue task.</span></span>  
  
 <span data-ttu-id="72f51-112">**Use2000Format**</span><span class="sxs-lookup"><span data-stu-id="72f51-112">**Use2000Format**</span></span>  
 <span data-ttu-id="72f51-113">2000 형식의 MSMQ(메시지 큐)를 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-113">Indicate whether to use the 2000 format of Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="72f51-114">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-114">The default is `False`.</span></span>  
  
 <span data-ttu-id="72f51-115">**MSMQConnection**</span><span class="sxs-lookup"><span data-stu-id="72f51-115">**MSMQConnection**</span></span>  
 <span data-ttu-id="72f51-116">기존 MSMQ 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-116">Select an existing MSMQ connection manager or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="72f51-117">**관련 항목**: [MSMQ 연결 관리자](connection-manager/msmq-connection-manager.md), [MSMQ 연결 관리자 편집기](../../2014/integration-services/msmq-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="72f51-117">**Related Topics**: [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md), [MSMQ Connection Manager Editor](../../2014/integration-services/msmq-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="72f51-118">**메시지**</span><span class="sxs-lookup"><span data-stu-id="72f51-118">**Message**</span></span>  
 <span data-ttu-id="72f51-119">메시지 큐 태스크에서 메시지를 보내거나 받을지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-119">Specify whether the Message Queue task sends or receive messages.</span></span> <span data-ttu-id="72f51-120">**메시지 보내기**를 선택하면 대화 상자의 왼쪽 창에 보내기 페이지가 표시되고 **메시지 받기**를 선택하면 받기 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-120">If you select **Send message**, the Send page is listed in the left pane of the dialog box; if you select **Receive message**, the Receive page is listed.</span></span> <span data-ttu-id="72f51-121">기본적으로 이 값은 **메시지 보내기**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="72f51-121">By default, this value is set to **Send message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f51-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72f51-122">See Also</span></span>  
 <span data-ttu-id="72f51-123">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="72f51-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="72f51-124">[메시지 큐 태스크 편집기 &#40;수신 페이지&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="72f51-124">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 <span data-ttu-id="72f51-125">[메시지 큐 태스크 편집기 &#40;보내기 페이지&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="72f51-125">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 [<span data-ttu-id="72f51-126">식 페이지</span><span class="sxs-lookup"><span data-stu-id="72f51-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
