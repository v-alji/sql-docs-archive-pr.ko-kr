---
title: 스크립트 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638941"
---
# <a name="script-task"></a><span data-ttu-id="9381d-102">스크립트 태스크</span><span class="sxs-lookup"><span data-stu-id="9381d-102">Script Task</span></span>
  <span data-ttu-id="9381d-103">스크립트 작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 제공하는 기본 제공 작업과 변환에서 사용할 수 없는 기능을 수행하는 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-103">The Script task provides code to perform functions that are not available in the built-in tasks and transformations that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="9381d-104">또한 여러 개의 태스크와 변환을 사용하는 대신 여러 기능을 하나의 스크립트에 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-104">The Script task can also combine functions in one script instead of using multiple tasks and transformations.</span></span> <span data-ttu-id="9381d-105">스크립트 태스크는 데이터 행마다 한 번 수행하는 대신 패키지에서 한 번 또는 열거된 개체마다 한 번 수행해야 하는 작업에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-105">You use the Script task for work that must be done once in a package (or once per enumerated object), instead than once per data row.</span></span>  
  
 <span data-ttu-id="9381d-106">스크립트 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-106">You can use the Script task for the following purposes:</span></span>  
  
-   <span data-ttu-id="9381d-107">기본 제공 연결 형식에서 지원하지 않는 다른 기술을 사용하여 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-107">Access data by using other technologies that are not supported by built-in connection types.</span></span> <span data-ttu-id="9381d-108">예를 들어 스크립트는 ADSI(Active Directory Service Interface)를 사용하여 Active Directory에 액세스하고 사용자 이름을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-108">For example, a script can use Active Directory Service Interfaces (ADSI) to access and extract user names from Active Directory.</span></span>  
  
-   <span data-ttu-id="9381d-109">패키지 특정 성능 카운터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-109">Create a package-specific performance counter.</span></span> <span data-ttu-id="9381d-110">예를 들어 스크립트는 복잡하거나 성능이 저조한 태스크를 실행하는 동안 업데이트되는 성능 카운터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-110">For example, a script can create a performance counter that is updated while a complex or poorly performing task runs.</span></span>  
  
-   <span data-ttu-id="9381d-111">지정된 파일이 비어 있는지 확인하고 그렇지 않은 경우 포함된 행 수를 확인한 다음 이러한 정보를 기반으로 패키지의 제어 흐름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-111">Identify whether specified files are empty or how many rows they contain, and then based on that information affect the control flow in a package.</span></span> <span data-ttu-id="9381d-112">예를 들어 파일에 포함된 행이 없는 경우 변수 값을 0으로 설정하고 이 값을 평가하는 선행 제약 조건으로 인해 파일 시스템 태스크가 파일을 복사할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-112">For example, if a file contains zero rows, the value of a variable set to 0, and a precedence constraint that evaluates the value prevents a File System task from copying the file.</span></span>  
  
 <span data-ttu-id="9381d-113">스크립트를 사용하여 한 집합에 있는 각 데이터 행에 대해 같은 작업을 수행해야 하는 경우에는 스크립트 태스크 대신 스크립트 구성 요소를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-113">If you have to use the script to do the same work for each row of data in a set, you should use the Script component instead of the Script task.</span></span> <span data-ttu-id="9381d-114">예를 들어 적절한 우표 금액을 평가하여 금액이 너무 높거나 낮은 데이터 행을 건너뛰려면 스크립트 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-114">For example, if you want to assess the reasonableness of a postage amount and skip data rows that have very high or low amounts, you would use a Script component.</span></span> <span data-ttu-id="9381d-115">자세한 내용은 [Script Component](../data-flow/transformations/script-component.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9381d-115">For more information, see [Script Component](../data-flow/transformations/script-component.md).</span></span>  
  
 <span data-ttu-id="9381d-116">스크립트가 둘 이상의 패키지에 사용되는 경우 스크립트 태스크 대신 사용자 지정 태스크를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-116">If more than one package uses a script, consider writing a custom task instead of using the Script task.</span></span> <span data-ttu-id="9381d-117">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9381d-117">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
 <span data-ttu-id="9381d-118">스크립트 태스크를 패키지에 적합한 선택 항목으로 결정한 후에는 태스크에서 사용하는 스크립트를 개발하고 태스크 자체를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-118">After you decide that the Script task is the appropriate choice for your package, you have to both develop the script that the task uses and configure the task itself.</span></span>  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a><span data-ttu-id="9381d-119">태스크에서 사용하는 스크립트 작성 및 실행</span><span class="sxs-lookup"><span data-stu-id="9381d-119">Writing and Running the Script that the Task Uses</span></span>  
 <span data-ttu-id="9381d-120">스크립트 작업은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications)를 스크립트 작성 환경과 스크립트 실행 엔진으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-120">The Script task uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts and the engine that runs those scripts.</span></span>  
  
 <span data-ttu-id="9381d-121">VSTA는 색 구분 기능이 포함된 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 편집기, IntelliSense, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 개체 탐색기 **등**환경의 모든 표준 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-121">VSTA provides all the standard features of the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor, IntelliSense, and **Object Explorer**.</span></span> <span data-ttu-id="9381d-122">또한 다른 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 개발 도구에서 사용하는 것과 동일한 디버거를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-122">VSTA also uses the same debugger that other [!INCLUDE[msCoName](../../includes/msconame-md.md)] development tools use.</span></span> <span data-ttu-id="9381d-123">스크립트 작업의 중단점이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 태스크 및 컨테이너의 중단점과 문제 없이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-123">Breakpoints in the script work seamlessly with breakpoints on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and containers.</span></span> <span data-ttu-id="9381d-124">VSTA는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 프로그래밍 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-124">VSTA supports both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages.</span></span>  
  
 <span data-ttu-id="9381d-125">스크립트를 실행하려면 패키지가 실행되는 컴퓨터에 VSTA가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-125">To run a script, you must have VSTA installed on the computer where the package runs.</span></span> <span data-ttu-id="9381d-126">패키지를 실행하면 스크립트 태스크가 스크립트 엔진을 로드하고 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-126">When the package runs, the task loads the script engine and runs the script.</span></span> <span data-ttu-id="9381d-127">어셈블리에 대한 참조를 프로젝트에 추가하면 스크립트에서 외부 .NET 어셈블리에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-127">You can access external .NET assemblies in scripts by adding references to the assemblies in the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9381d-128">스크립트가 미리 컴파일되었는지 여부를 지정할 수 있었던 이전 버전과는 달리 모든 스크립트가 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 이상 버전에 미리 컴파일되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-128">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="9381d-129">스크립트가 미리 컴파일된 경우 런타임 시 언어 엔진이 로드되지 않으므로 패키지가 보다 신속하게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-129">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="9381d-130">그러나 미리 컴파일된 이진 파일은 상당한 디스크 공간을 소비합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-130">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-task"></a><span data-ttu-id="9381d-131">스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="9381d-131">Configuring the Script Task</span></span>  
 <span data-ttu-id="9381d-132">다음과 같은 방법으로 스크립트 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-132">You can configure the Script task in the following ways:</span></span>  
  
-   <span data-ttu-id="9381d-133">태스크에서 실행할 사용자 지정 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-133">Provide the custom script that the task runs.</span></span>  
  
-   <span data-ttu-id="9381d-134">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임이 스크립트 태스크 코드에 대한 진입점으로 호출되는 VSTA 프로젝트의 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-134">Specify the method in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span>  
  
-   <span data-ttu-id="9381d-135">스크립트 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-135">Specify the script language.</span></span>  
  
-   <span data-ttu-id="9381d-136">선택적으로 스크립트에서 사용할 읽기 전용 및 읽기/쓰기 변수 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-136">Optionally, provide lists of read-only and read/write variables for use in the script.</span></span>  
  
 <span data-ttu-id="9381d-137">이러한 속성은 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-137">You can set these properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-task-in-the-designer"></a><span data-ttu-id="9381d-138">디자이너에서 스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="9381d-138">Configuring the Script Task in the Designer</span></span>  
 <span data-ttu-id="9381d-139">다음 표에서는 스크립트 태스크용으로 로깅될 수 있는 `ScriptTaskLogEntry` 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-139">The following table describes the `ScriptTaskLogEntry` event that can be logged for Script task.</span></span> <span data-ttu-id="9381d-140">`ScriptTaskLogEntry` **SSIS 로그 구성** 대화 상자의 **자세히** 탭에서 로깅할 이벤트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-140">The `ScriptTaskLogEntry` event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box.</span></span> <span data-ttu-id="9381d-141">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9381d-141">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="9381d-142">로그 항목</span><span class="sxs-lookup"><span data-stu-id="9381d-142">Log entry</span></span>|<span data-ttu-id="9381d-143">Description</span><span class="sxs-lookup"><span data-stu-id="9381d-143">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="9381d-144">스크립트에서 로깅을 구현한 결과를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-144">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="9381d-145">이 태스크는 `Log` 개체의 `Dts` 메서드를 호출할 때마다 로그 항목을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-145">The task writes a log entry for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="9381d-146">이러한 항목은 코드가 실행될 때 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9381d-146">The task writes these entries when the code is run.</span></span> <span data-ttu-id="9381d-147">자세한 내용은 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9381d-147">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
 <span data-ttu-id="9381d-148">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9381d-148">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9381d-149">스크립트 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="9381d-149">Script Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="9381d-150">스크립트 태스크 편집기&#40;스크립트 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="9381d-150">Script Task Editor &#40;Script Page&#41;</span></span>](../script-task-editor-script-page.md)  
  
-   [<span data-ttu-id="9381d-151">식 페이지</span><span class="sxs-lookup"><span data-stu-id="9381d-151">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="9381d-152">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9381d-152">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="9381d-153">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="9381d-153">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a><span data-ttu-id="9381d-154">프로그래밍 방식으로 스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="9381d-154">Configuring the Script Task Programmatically</span></span>  
 <span data-ttu-id="9381d-155">이러한 속성을 프로그래밍 방식으로 설정하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9381d-155">For more information about programmatically setting these properties, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a><span data-ttu-id="9381d-156">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9381d-156">Related Content</span></span>  
  
-   <span data-ttu-id="9381d-157">shareourideas.com의 기술 문서 - [C#의 배달 알림으로 메일을 보내는 방법](https://go.microsoft.com/fwlink/?LinkId=237625)</span><span class="sxs-lookup"><span data-stu-id="9381d-157">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
  
