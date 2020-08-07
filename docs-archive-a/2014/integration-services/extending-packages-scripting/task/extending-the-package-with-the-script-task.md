---
title: 스크립트 태스크를 사용하여 패키지 확장 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f1a265b01a898cdc87bdf9df6cb67399879061b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731911"
---
# <a name="extending-the-package-with-the-script-task"></a><span data-ttu-id="f6b05-102">스크립트 태스크를 사용하여 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="f6b05-102">Extending the Package with the Script Task</span></span>
  <span data-ttu-id="f6b05-103">스크립트 태스크는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Visual C#으로 작성되고 패키지 런타임에 컴파일 및 실행되는 사용자 지정 코드를 사용하여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 패키지의 런타임 기능을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-103">The Script task extends the run-time capabilities of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages with custom code written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# that is compiled and executed at package run time.</span></span> <span data-ttu-id="f6b05-104">스크립트 태스크를 사용하면 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 제공하는 태스크가 개발자의 요구 사항을 완전히 만족시키지 못하는 경우 사용자 지정 런타임을 손쉽게 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-104">The Script task simplifies the development of a custom run-time task when the tasks included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not fully satisfy your requirements.</span></span> <span data-ttu-id="f6b05-105">스크립트 태스크에서는 필요한 모든 인프라 코드를 자동으로 작성하므로 개발자는 사용자 지정 처리에 필요한 코드에만 집중하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-105">The Script task writes all the required infrastructure code for you, letting you focus exclusively on the code that is required for your custom processing.</span></span>  
  
 <span data-ttu-id="f6b05-106">스크립트 태스크는 스크립팅 환경에서 제공되는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스의 인스턴스인 전역 `Dts` 개체를 통해 포함하는 패키지와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-106">A Script task interacts with the containing package through the global `Dts` object, an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class that is exposed in the scripting environment.</span></span> <span data-ttu-id="f6b05-107">스크립트 태스크에서 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 변수에 저장된 값을 수정하는 코드를 작성할 수 있습니다. 그러면 나중에 패키지에서 업데이트된 이 값을 사용하여 패키지 워크플로의 경로를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-107">You can write code in a Script task that modifies the values stored in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] variables; later, the package can use those updated values to determine the path of its workflow.</span></span> <span data-ttu-id="f6b05-108">또한 스크립트 태스크에서는 사용자 지정 기능을 구현하는 데 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 네임스페이스 및 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 클래스 라이브러리뿐 아니라 사용자 지정 어셈블리도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-108">The Script task can also use the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] namespace and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library, as well as custom assemblies, to implement custom functionality.</span></span>  
  
 <span data-ttu-id="f6b05-109">스크립트 태스크 및 해당 구성 요소가 생성하는 인프라 코드를 사용하면 사용자 지정 태스크를 개발하는 과정이 훨씬 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-109">The Script task and the infrastructure code that it generates for you simplify significantly the process of developing a custom task.</span></span> <span data-ttu-id="f6b05-110">하지만 스크립트 태스크의 작동 방식을 이해하려면 [사용자 지정 태스크 개발](../../extending-packages-custom-objects/task/developing-a-custom-task.md) 섹션을 통해 사용자 지정 태스크를 개발하는 데 필요한 단계를 파악하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-110">However, to understand how the Script task works, you may find it useful to read the section [Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) to understand the steps that are involved in developing a custom task.</span></span>  
  
 <span data-ttu-id="f6b05-111">여러 패키지에서 재사용할 태스크를 만들 경우에는 스크립트 태스크를 사용하는 대신 사용자 지정 태스크를 개발하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-111">If you are creating a task that you plan to reuse in multiple packages, you should consider developing a custom task instead of using the Script task.</span></span> <span data-ttu-id="f6b05-112">자세한 내용은 [스크립팅 솔루션과 사용자 지정 개체 비교](../comparing-scripting-solutions-and-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6b05-112">For more information, see [Comparing Scripting Solutions and Custom Objects](../comparing-scripting-solutions-and-custom-objects.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6b05-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f6b05-113">In This Section</span></span>  
 <span data-ttu-id="f6b05-114">다음 항목에서는 스크립트 태스크에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-114">The following topics provide more information about the Script task.</span></span>  
  
 [<span data-ttu-id="f6b05-115">스크립트 태스크 편집기에서 스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="f6b05-115">Configuring the Script Task in the Script Task Editor</span></span>](configuring-the-script-task-in-the-script-task-editor.md)  
 <span data-ttu-id="f6b05-116">**스크립트 태스크 편집기**에서 구성하는 속성이 스크립트 태스크 코드의 기능과 성능에 미치는 영향에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-116">Explains how the properties that you configure in the **Script Task Editor** affect the capabilities and the performance of the code in the Script task.</span></span>  
  
 [<span data-ttu-id="f6b05-117">스크립트 태스크 코딩 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="f6b05-117">Coding and Debugging the Script Task</span></span>](../../control-flow/script-task.md)  
 <span data-ttu-id="f6b05-118">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications)를 사용하여 스크립트 태스크에 포함되는 스크립트를 개발하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-118">Explains how to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) to develop the scripts that are contained in the Script task.</span></span>  
  
 [<span data-ttu-id="f6b05-119">스크립트 태스크에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="f6b05-119">Using Variables in the Script Task</span></span>](using-variables-in-the-script-task.md)  
 <span data-ttu-id="f6b05-120"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 통해 변수를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-120">Explains how to use variables through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>  
  
 [<span data-ttu-id="f6b05-121">스크립트 태스크에서 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="f6b05-121">Connecting to Data Sources in the Script Task</span></span>](connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="f6b05-122"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 속성을 통해 연결을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-122">Explains how to use connections through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property.</span></span>  
  
 [<span data-ttu-id="f6b05-123">스크립트 태스크에서 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="f6b05-123">Raising Events in the Script Task</span></span>](raising-events-in-the-script-task.md)  
 <span data-ttu-id="f6b05-124"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 속성을 통해 이벤트를 발생시키는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-124">Explains how to raise events through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
 [<span data-ttu-id="f6b05-125">스크립트 태스크에서 로깅</span><span class="sxs-lookup"><span data-stu-id="f6b05-125">Logging in the Script Task</span></span>](logging-in-the-script-task.md)  
 <span data-ttu-id="f6b05-126"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드를 통해 정보를 로깅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-126">Explains how to log information through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method.</span></span>  
  
 [<span data-ttu-id="f6b05-127">스크립트 태스크에서 결과 반환</span><span class="sxs-lookup"><span data-stu-id="f6b05-127">Returning Results from the Script Task</span></span>](returning-results-from-the-script-task.md)  
 <span data-ttu-id="f6b05-128"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 속성 및 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 속성을 통해 결과를 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-128">Explains how to return results through the property <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property.</span></span>  
  
 [<span data-ttu-id="f6b05-129">스크립트 태스크 예제</span><span class="sxs-lookup"><span data-stu-id="f6b05-129">Script Task Examples</span></span>](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 <span data-ttu-id="f6b05-130">스크립트 태스크의 가능한 용도 몇 가지를 보여 주는 간단한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b05-130">Provides simple examples that demonstrate several possible uses for a Script task.</span></span>  
  
<span data-ttu-id="f6b05-131">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f6b05-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f6b05-132">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]의 최신 다운로드, 아티클, 예제 및 비디오와 커뮤니티의 정선된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6b05-132">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f6b05-133">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="f6b05-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f6b05-134">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="f6b05-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b05-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6b05-135">See Also</span></span>  
 <span data-ttu-id="f6b05-136">[스크립트 태스크](../../control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="f6b05-136">[Script Task](../../control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="f6b05-137">스크립트 태스크와 스크립트 구성 요소 비교</span><span class="sxs-lookup"><span data-stu-id="f6b05-137">Comparing the Script Task and the Script Component</span></span>](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
