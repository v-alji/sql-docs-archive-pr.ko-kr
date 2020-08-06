---
title: MSMQ 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c51866eeef281f6587bf281461e4faa2278308d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659604"
---
# <a name="msmq-connection-manager"></a><span data-ttu-id="bbb23-102">MSMQ 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="bbb23-102">MSMQ Connection Manager</span></span>
  <span data-ttu-id="bbb23-103">MSMQ 연결 관리자를 사용하면 패키지에서 MSMQ(메시지 큐)를 사용하는 메시지 큐에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-103">An MSMQ connection manager enables a package to connect to a message queue that uses Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="bbb23-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 메시지 큐 태스크에서는 MSMQ 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-104">The Message Queue task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an MSMQ connection manager.</span></span>  
  
 <span data-ttu-id="bbb23-105">패키지에 MSMQ 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 MSMQ 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하며, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-105">When you add an MSMQ connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an MSMQ connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="bbb23-106">연결 관리자의 `ConnectionManagerType` 속성이 `MSMQ`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-106">The `ConnectionManagerType` property of the connection manager is set to `MSMQ`.</span></span>  
  
 <span data-ttu-id="bbb23-107">다음과 같은 방법으로 MSMQ 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-107">You can configure an MSMQ connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="bbb23-108">연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-108">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="bbb23-109">연결할 메시지 큐의 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-109">Provide the path of the message queue to connect to.</span></span>  
  
 <span data-ttu-id="bbb23-110">다음 표에서 보여 주는 것과 같이 경로 형식은 큐 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-110">The format of the path depends on the type of queue, as shown in the following table.</span></span>  
  
|<span data-ttu-id="bbb23-111">큐 유형</span><span class="sxs-lookup"><span data-stu-id="bbb23-111">Queue type</span></span>|<span data-ttu-id="bbb23-112">샘플 경로</span><span class="sxs-lookup"><span data-stu-id="bbb23-112">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="bbb23-113">공용</span><span class="sxs-lookup"><span data-stu-id="bbb23-113">Public</span></span>|<span data-ttu-id="bbb23-114">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="bbb23-114">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="bbb23-115">프라이빗</span><span class="sxs-lookup"><span data-stu-id="bbb23-115">Private</span></span>|<span data-ttu-id="bbb23-116">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="bbb23-116">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="bbb23-117">마침표(.)를 사용하여 로컬 컴퓨터를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-117">You can use a period (.) to represent the local computer.</span></span>  
  
## <a name="configuration-of-the-msmq-connection-manager"></a><span data-ttu-id="bbb23-118">MSMQ 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="bbb23-118">Configuration of the MSMQ Connection Manager</span></span>  
 <span data-ttu-id="bbb23-119">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bbb23-120">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [MSMQ 연결 관리자 편집기](../msmq-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bbb23-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [MSMQ Connection Manager Editor](../msmq-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="bbb23-121">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb23-121">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb23-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbb23-122">See Also</span></span>  
 <span data-ttu-id="bbb23-123">[메시지 큐 태스크](../control-flow/message-queue-task.md) </span><span class="sxs-lookup"><span data-stu-id="bbb23-123">[Message Queue Task](../control-flow/message-queue-task.md) </span></span>  
 [<span data-ttu-id="bbb23-124">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="bbb23-124">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
