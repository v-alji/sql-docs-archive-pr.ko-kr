---
title: Integration Services 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649621"
---
# <a name="integration-services-tasks"></a><span data-ttu-id="ae463-102">Integration Services 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-102">Integration Services Tasks</span></span>
  <span data-ttu-id="ae463-103">태스크는 패키지 제어 흐름에서 수행되는 작업 단위를 정의하는 제어 흐름 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-103">Tasks are control flow elements that define units of work that are performed in a package control flow.</span></span> <span data-ttu-id="ae463-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 두 개 이상의 태스크로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-104">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package is made up of one or more tasks.</span></span> <span data-ttu-id="ae463-105">패키지에 둘 이상의 태스크가 포함되면 이러한 태스크는 선행 제약 조건에 의해 제어 흐름으로 연결되고 순차화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-105">If the package contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span>  
  
 <span data-ttu-id="ae463-106">COM을 지원하는 Visual Basic 등의 프로그래밍 언어와 C#과 같은 .NET 프로그래밍 언어를 사용하여 사용자 지정 태스크를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-106">You can also write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span>  
  
 <span data-ttu-id="ae463-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 패키지 작업용 그래픽 도구인 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 디자이너는 패키지 제어 흐름을 만들기 위한 디자인 화면과 태스크 구성을 위한 사용자 지정 편집기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the graphical tool in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] for working with packages, provides the design surface for creating package control flow, and provides custom editors for configuring tasks.</span></span> <span data-ttu-id="ae463-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체 모델을 프로그래밍하여 프로그래밍 방식으로 패키지를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-108">You can also program the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to create packages programmatically.</span></span>  
  
## <a name="types-of-tasks"></a><span data-ttu-id="ae463-109">태스크 유형</span><span class="sxs-lookup"><span data-stu-id="ae463-109">Types of Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ae463-110">에는 다음 유형의 태스크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-110">includes the following types of tasks.</span></span>  
  
 <span data-ttu-id="ae463-111">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-111">Data Flow Task</span></span>  
 <span data-ttu-id="ae463-112">데이터 흐름을 실행하여 데이터를 추출하고 열 수준 변환을 적용하며 데이터를 로드하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-112">The task that runs data flows to extract data, apply column level transformations, and load data.</span></span>  
  
 <span data-ttu-id="ae463-113">데이터 준비 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-113">Data Preparation Tasks</span></span>  
 <span data-ttu-id="ae463-114">파일 및 디렉터리 복사, 파일 및 데이터 다운로드, 웹 메서드 실행, XML 문서에 작업 적용 및 정리할 데이터 프로파일링 등의 프로세스를 수행하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-114">These tasks do the following processes: copy files and directories; download files and data; run Web methods; apply operations to XML documents; and profile data for cleansing.</span></span>  
  
 <span data-ttu-id="ae463-115">워크플로 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-115">Workflow Tasks</span></span>  
 <span data-ttu-id="ae463-116">다른 프로세스와 통신하여 패키지 실행, 프로그램 또는 배치 파일 실행, 패키지 간에 메시지 송수신, 전자 메일 메시지 보내기, WMI(Windows Management Instrumentation) 데이터 읽기, WMI 이벤트 감시 등을 수행하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-116">The tasks that communicate with other processes to run packages, run programs or batch files, send and receive messages between packages, send e-mail messages, read Windows Management Instrumentation (WMI) data, and watch for WMI events.</span></span>  
  
 <span data-ttu-id="ae463-117">SQL Server 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-117">SQL Server Tasks</span></span>  
 <span data-ttu-id="ae463-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 및 데이터를 액세스, 복사, 삽입, 삭제 및 수정하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-118">The tasks that access, copy, insert, delete, and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and data.</span></span>  
  
 <span data-ttu-id="ae463-119">스크립팅 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-119">Scripting Tasks</span></span>  
 <span data-ttu-id="ae463-120">스크립트를 사용하여 패키지 기능을 확장하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-120">The tasks that extend package functionality by using scripts.</span></span>  
  
 <span data-ttu-id="ae463-121">Analysis Services 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-121">Analysis Services Tasks</span></span>  
 <span data-ttu-id="ae463-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 만들고 수정, 삭제 및 처리하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-122">The tasks that create, modify, delete, and process [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="ae463-123">유지 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-123">Maintenance Tasks</span></span>  
 <span data-ttu-id="ae463-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 백업 및 축소, 인덱스 다시 작성 및 다시 구성, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 실행 등의 관리 기능을 수행하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-124">The tasks that perform administrative functions such as backing up and shrinking [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, rebuilding and reorganizing indexes, and running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="ae463-125">사용자 지정 태스크</span><span class="sxs-lookup"><span data-stu-id="ae463-125">Custom Tasks</span></span>  
 <span data-ttu-id="ae463-126">COM을 지원하는 Visual Basic 등의 프로그래밍 언어와 C#과 같은 .NET 프로그래밍 언어를 사용하여 사용자 지정 태스크를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-126">Additionally, you can write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span> <span data-ttu-id="ae463-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 사용자 지정 태스크에 액세스하려는 경우 해당 태스크의 사용자 인터페이스를 만들어 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-127">If you want to access your custom task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can create and register a user interface for the task.</span></span> <span data-ttu-id="ae463-128">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-128">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="configuration-of-tasks"></a><span data-ttu-id="ae463-129">태스크 구성</span><span class="sxs-lookup"><span data-stu-id="ae463-129">Configuration of Tasks</span></span>  
 <span data-ttu-id="ae463-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에는 패키지 실행 시 데이터베이스 테이블에서 레코드를 삭제하는 SQL 실행 태스크와 같은 단일 태스크가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-130">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can contain a single task, such as an Execute SQL task that deletes records in a database table when the package runs.</span></span> <span data-ttu-id="ae463-131">그러나 패키지는 일반적으로 여러 개의 태스크를 포함하며 각 태스크는 패키지 제어 흐름의 컨텍스트에서 실행되도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-131">However, packages typically contain several tasks, and each task is set to run within the context of the package control flow.</span></span> <span data-ttu-id="ae463-132">런타임 이벤트에 응답하여 실행되는 작업 흐름인 이벤트 처리기도 태스크를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-132">Event handlers, which are workflows that run in response to run-time events, can also have tasks.</span></span>  
  
 <span data-ttu-id="ae463-133">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하여 패키지에 태스크를 추가하는 방법에 대한 자세한 내용은 [제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](add-or-delete-a-task-or-a-container-in-a-control-flow.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-133">For more information about adding a task to a package using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>  
  
 <span data-ttu-id="ae463-134">프로그래밍 방식으로 패키지에 태스크를 추가하는 방법에 대한 자세한 내용은 [프로그래밍 방식으로 태스크 추가](../building-packages-programmatically/adding-tasks-programmatically.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-134">For more information about adding a task to a package programmatically, see [Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md).</span></span>  
  
 <span data-ttu-id="ae463-135">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 제공하는 각 태스크의 사용자 지정 대화 상자나 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에 포함된 속성 창을 사용하여 각 태스크를 개별적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-135">Each task can be configured individually using the custom dialog boxes for each task that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, or the Properties window included in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ae463-136">패키지에는 동일한 유형의 태스크(예: 6개의 SQL 실행 태스크)가 여러 개 포함될 수 있으며 각 태스크는 서로 다르게 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-136">A package can include multiple tasks of the same type-for example, six Execute SQL tasks-and each task can be configured differently.</span></span> <span data-ttu-id="ae463-137">자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-137">For more information, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="tasks-connections-and-groups"></a><span data-ttu-id="ae463-138">태스크 연결 및 그룹</span><span class="sxs-lookup"><span data-stu-id="ae463-138">Tasks Connections and Groups</span></span>  
 <span data-ttu-id="ae463-139">태스크에 둘 이상의 태스크가 포함되면 이러한 태스크는 선행 제약 조건에 의해 제어 흐름으로 연결되고 순차화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-139">If the task contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span> <span data-ttu-id="ae463-140">자세한 내용은 [Precedence Constraints](precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-140">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="ae463-141">태스크를 그룹화하여 단일 작업 단위로 수행하거나 루프에서 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae463-141">Tasks can be grouped together and performed as a single unit of work, or repeated in a loop.</span></span> <span data-ttu-id="ae463-142">자세한 내용은 [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md)및 [Sequence Container](sequence-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae463-142">For more information, see [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md), and [Sequence Container](sequence-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ae463-143">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ae463-143">Related Tasks</span></span>  
 [<span data-ttu-id="ae463-144">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="ae463-144">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
