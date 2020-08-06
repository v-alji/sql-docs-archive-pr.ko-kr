---
title: MSMQ 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41d4231ce121d596c8d818485eccf5ddf6127470
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647105"
---
# <a name="msmq-connection-manager-editor"></a><span data-ttu-id="e50e3-102">MSMQ 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="e50e3-102">MSMQ Connection Manager Editor</span></span>
  <span data-ttu-id="e50e3-103">**MSMQ 연결 관리자** 대화 상자를 사용하여 MSMQ(메시지 큐)의 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-103">Use the **MSMQ Connection Manager** dialog box to specify the path to a Message Queuing (also known as MSMQ) message queue.</span></span>  
  
 <span data-ttu-id="e50e3-104">MSMQ 연결 관리자에 대한 자세한 내용은 [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e50e3-104">To learn more about the MSMQ connection manager, see [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e50e3-105">MSMQ 연결 관리자는 로컬 퍼블릭 큐, 로컬 프라이빗 큐 및 원격 퍼블릭 큐를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-105">The MSMQ connection manager supports local public and private queues and remote public queues.</span></span> <span data-ttu-id="e50e3-106">원격 프라이빗 큐는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-106">It does not support remote private queues.</span></span> <span data-ttu-id="e50e3-107">스크립트 태스크를 사용하는 해결 방법은 [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e50e3-107">For a workaround that uses the Script Task, see [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e50e3-108">옵션</span><span class="sxs-lookup"><span data-stu-id="e50e3-108">Options</span></span>  
 <span data-ttu-id="e50e3-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="e50e3-109">**Name**</span></span>  
 <span data-ttu-id="e50e3-110">워크플로의 MSMQ 연결 관리자에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-110">Provide a unique name for the MSMQ connection manager in the workflow.</span></span> <span data-ttu-id="e50e3-111">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-111">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e50e3-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="e50e3-112">**Description**</span></span>  
 <span data-ttu-id="e50e3-113">연결 관리자에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-113">Describe the connection manager.</span></span> <span data-ttu-id="e50e3-114">설명에 해당 연결 관리자의 용도를 정의하면 패키지를 이해하기 쉬우며 유지 관리가 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-114">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="e50e3-115">**Path**</span><span class="sxs-lookup"><span data-stu-id="e50e3-115">**Path**</span></span>  
 <span data-ttu-id="e50e3-116">메시지 큐의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-116">Type the complete path of the message queue.</span></span> <span data-ttu-id="e50e3-117">경로 형식은 큐 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-117">The format of the path depends on the type of queue.</span></span>  
  
|<span data-ttu-id="e50e3-118">큐 유형</span><span class="sxs-lookup"><span data-stu-id="e50e3-118">Queue type</span></span>|<span data-ttu-id="e50e3-119">샘플 경로</span><span class="sxs-lookup"><span data-stu-id="e50e3-119">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="e50e3-120">공용</span><span class="sxs-lookup"><span data-stu-id="e50e3-120">Public</span></span>|<span data-ttu-id="e50e3-121">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="e50e3-121">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="e50e3-122">프라이빗</span><span class="sxs-lookup"><span data-stu-id="e50e3-122">Private</span></span>|<span data-ttu-id="e50e3-123">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="e50e3-123">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="e50e3-124">"."를 사용하여 로컬 컴퓨터를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-124">You can use "." to represent the local computer.</span></span>  
  
 <span data-ttu-id="e50e3-125">**Test**</span><span class="sxs-lookup"><span data-stu-id="e50e3-125">**Test**</span></span>  
 <span data-ttu-id="e50e3-126">MSMQ 연결 관리자를 구성했으면 **테스트**를 클릭하여 연결이 실행 가능한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e50e3-126">After configuring the MSMQ connection manager, confirm that the connection is viable by clicking **Test**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50e3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e50e3-127">See Also</span></span>  
 [<span data-ttu-id="e50e3-128">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="e50e3-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
