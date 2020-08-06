---
title: 프로세스 실행 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.f1
helpviewer_keywords:
- Execute Process task [Integration Services]
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c0db683d7c900e2554b3b856cbf68f7cfb1ca087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650217"
---
# <a name="execute-process-task"></a><span data-ttu-id="850ad-102">프로세스 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="850ad-102">Execute Process Task</span></span>
  <span data-ttu-id="850ad-103">프로세스 실행 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 워크플로의 일부로 애플리케이션이나 배치 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-103">The Execute Process task runs an application or batch file as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="850ad-104">프로세스 실행 태스크를 사용하여 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 또는 [!INCLUDE[ofprword](../../includes/ofprword-md.md)]와 같은 모든 표준 애플리케이션을 열 수 있지만 이 태스크는 일반적으로 데이터 원본에 대해 작동하는 비즈니스 애플리케이션이나 배치 파일을 실행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-104">Although you can use the Execute Process task to open any standard application, such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or [!INCLUDE[ofprword](../../includes/ofprword-md.md)], you typically use it to run business applications or batch files that work against a data source.</span></span> <span data-ttu-id="850ad-105">예를 들어 프로세스 실행 태스크를 사용하여 압축된 텍스트 파일을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-105">For example, you can use the Execute Process task to expand a compressed text file.</span></span> <span data-ttu-id="850ad-106">패키지는 이 텍스트 파일을 패키지의 데이터 흐름에 대한 데이터 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-106">Then the package can use the text file as a data source for the data flow in the package.</span></span> <span data-ttu-id="850ad-107">예를 들어 프로세스 실행 태스크를 사용하여 일일 판매 보고서를 생성하는 사용자 지정 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 애플리케이션을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-107">As another example, you can use the Execute Process task to run a custom [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] application that generates a daily sales report.</span></span> <span data-ttu-id="850ad-108">그런 다음 이 보고서를 메일 보내기 태스크에 첨부하여 메일 그룹에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-108">Then you can attach the report to a Send Mail task and forward the report to a distribution list.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="850ad-109">에는 패키지 실행과 같은 워크플로 태스크를 수행하는 기타 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-109">includes other tasks that perform workflow operations such as executing packages.</span></span> <span data-ttu-id="850ad-110">자세한 내용은 [Execute Package Task](execute-package-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="850ad-110">For more information, see [Execute Package Task](execute-package-task.md)</span></span>  
  
## <a name="custom-log-entries-available-on-the-execute-process-task"></a><span data-ttu-id="850ad-111">프로세스 실행 태스크에 사용할 수 있는 사용자 지정 로그 항목</span><span class="sxs-lookup"><span data-stu-id="850ad-111">Custom Log Entries Available on the Execute Process Task</span></span>  
 <span data-ttu-id="850ad-112">다음 표에서는 프로세스 실행 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-112">The following table lists the custom log entries for the Execute Process task.</span></span> <span data-ttu-id="850ad-113">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="850ad-113">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="850ad-114">로그 항목</span><span class="sxs-lookup"><span data-stu-id="850ad-114">Log entry</span></span>|<span data-ttu-id="850ad-115">Description</span><span class="sxs-lookup"><span data-stu-id="850ad-115">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="850ad-116">태스크에서 실행하도록 구성할 프로세스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-116">Provides information about the process that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="850ad-117">두 개의 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-117">Two log entries are written.</span></span> <span data-ttu-id="850ad-118">한 항목에는 태스크가 실행하는 실행 파일의 이름과 위치에 대한 정보가 들어 있고 다른 항목은 실행 파일의 종료를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-118">One contains information about the name and location of the executable that the task runs, and the other entry records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="850ad-119">실행 파일의 입력 및 출력으로 라우팅되는 변수에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-119">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="850ad-120">stdin(입력), stdout(출력) 및 stderr(오류 출력)에 대한 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-120">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
## <a name="configuration-of-the-execute-process-task"></a><span data-ttu-id="850ad-121">프로세스 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="850ad-121">Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="850ad-122">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-122">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="850ad-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="850ad-123">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="850ad-124">프로세스 실행 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="850ad-124">Execute Process Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="850ad-125">프로세스 실행 태스크 편집기&#40;프로세스 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="850ad-125">Execute Process Task Editor &#40;Process Page&#41;</span></span>](../execute-process-task-editor-process-page.md)  
  
 <span data-ttu-id="850ad-126">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="850ad-126">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="850ad-127">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="850ad-127">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="property-settings"></a><span data-ttu-id="850ad-128">속성 설정</span><span class="sxs-lookup"><span data-stu-id="850ad-128">Property Settings</span></span>  
 <span data-ttu-id="850ad-129">프로세스 실행 태스크는 사용자 지정 애플리케이션을 실행할 때 다음 방법 중 하나 또는 모두를 통해 애플리케이션에 입력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-129">When the Execute Process task runs a custom application, the task provides input to the application through one or both of the following methods:</span></span>  
  
-   <span data-ttu-id="850ad-130">**StandardInputVariable** 속성 설정에서 지정하는 변수.</span><span class="sxs-lookup"><span data-stu-id="850ad-130">A variable that you specify in the **StandardInputVariable** property setting.</span></span> <span data-ttu-id="850ad-131">변수에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="850ad-131">For more information about variables, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
-   <span data-ttu-id="850ad-132">**Arguments** 속성 설정에서 지정하는 인수.</span><span class="sxs-lookup"><span data-stu-id="850ad-132">An argument that you specify in the **Arguments** property setting.</span></span> <span data-ttu-id="850ad-133">예를 들어 태스크가 Word 문서를 여는 경우 인수에서 .doc 파일의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-133">(For example, if the task opens a document in Word, the argument can name the .doc file.)</span></span>  
  
 <span data-ttu-id="850ad-134">하나의 프로세스 실행 태스크에 있는 사용자 지정 애플리케이션에 여러 인수를 전달하려면 공백으로 인수를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-134">To pass multiple arguments to a custom application in one Execute Process task, use spaces to delimit the arguments.</span></span> <span data-ttu-id="850ad-135">인수는 공백을 포함할 수 없습니다. 공백을 포함하는 경우 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-135">An argument cannot include a space; otherwise, the task will not run.</span></span> <span data-ttu-id="850ad-136">변수 값을 인수로 전달하는 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-136">You can use an expression to pass a variable value as the argument.</span></span> <span data-ttu-id="850ad-137">다음 예에서는 식이 두 변수 값을 인수로 전달하고 공백을 사용하여 인수를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-137">In the following example, the expression passes two variable values as arguments, and uses a space to delimit the arguments:</span></span>  
  
 `@variable1 + " " + @variable2`  
  
 <span data-ttu-id="850ad-138">여러 프로세스 실행 태스크 속성을 설정하는 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-138">You can use an expression to set various Execute Process task properties.</span></span>  
  
 <span data-ttu-id="850ad-139">**Standardinputvariable** 속성을 사용 하 여 프로세스 실행 태스크에서 입력을 제공 하도록 구성 하는 경우 `Console.ReadLine` 응용 프로그램에서 메서드를 호출 하 여 입력을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-139">When you use the **StandardInputVariable** property to configure the Execute Process task to provide input, call the `Console.ReadLine` method from the application to read the input.</span></span> <span data-ttu-id="850ad-140">자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스 라이브러리의 [Console.ReadLine 메서드](https://go.microsoft.com/fwlink/?LinkId=129201) 토픽을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="850ad-140">For more information, see [Console.ReadLine Method](https://go.microsoft.com/fwlink/?LinkId=129201)the topic, , in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Class Library.</span></span>  
  
 <span data-ttu-id="850ad-141">**Arguments** 속성을 사용하여 프로세스 실행 태스크에서 입력을 제공하도록 구성하는 경우 다음 단계 중 하나를 수행하여 인수를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-141">When you use the **Arguments** property to configure the Execute Process task to provide input, do one of the following steps to obtain the arguments:</span></span>  
  
-   <span data-ttu-id="850ad-142">Microsoft Visual Basic을 사용하여 애플리케이션을 작성하는 경우 `My.Application.CommandLineArgs` 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-142">If you use Microsoft Visual Basic to write the application, set the `My.Application.CommandLineArgs` property.</span></span> <span data-ttu-id="850ad-143">다음 예에서는 `My.Application.CommandLineArgs` 속성을 설정하여 두 인수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-143">The following example sets the `My.Application.CommandLineArgs` property is to retrieve two arguments:</span></span>  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     <span data-ttu-id="850ad-144">자세한 내용은 [참조에서](https://go.microsoft.com/fwlink/?LinkId=129200)My.Application.CommandLineArgs 속성 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="850ad-144">For more information, see the topic, [My.Application.CommandLineArgs Property](https://go.microsoft.com/fwlink/?LinkId=129200), in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] reference.</span></span>  
  
-   <span data-ttu-id="850ad-145">Microsoft Visual C#을 사용하여 응용 프로그램을 작성하는 경우 `Main` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-145">If you use Microsoft Visual C# to write the applicate, use the `Main` method.</span></span>  
  
     <span data-ttu-id="850ad-146">자세한 내용은 C# 프로그래밍 가이드의 [명령줄 인수(C# 프로그래밍 가이드)](https://go.microsoft.com/fwlink/?LinkId=129406)항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="850ad-146">For more information, see the topic, [Command-Line Arguments (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=129406), in the C# Programming Guide.</span></span>  
  
 <span data-ttu-id="850ad-147">프로세스 실행 태스크에는 각각 애플리케이션의 표준 출력과 애플리케이션 표준 오류 출력을 사용하는 변수를 지정하는 **StandardOutputVariable** 및 **StandardErrorVariable** 속성도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-147">The Execute Process task also includes the **StandardOutputVariable** and **StandardErrorVariable** properties for specifying the variables that consume the standard output and error output of the application, respectively.</span></span>  
  
 <span data-ttu-id="850ad-148">또한 프로세스 실행 태스크를 구성하여 작업 디렉터리, 제한 시간 경과 또는 실행 파일이 성공적으로 실행되었음을 나타내는 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-148">Additionally, you can configure the Execute Process task to specify a working directory, a time-out period, or a value to indicate that the executable ran successfully.</span></span> <span data-ttu-id="850ad-149">실행 파일의 반환 코드가 성공을 나타내는 값과 일치하지 않거나 지정한 위치에 실행 파일이 없을 경우 태스크가 실패하도록 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="850ad-149">The task can also be configured to fail if the return code of the executable does not match the value that indicates success, or if the executable is not found at the specified location.</span></span>  
  
## <a name="programmatic-configuration-of-the-execute-process-task"></a><span data-ttu-id="850ad-150">프로세스 실행 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="850ad-150">Programmatic Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="850ad-151">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="850ad-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess>  
  
## <a name="see-also"></a><span data-ttu-id="850ad-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="850ad-152">See Also</span></span>  
 <span data-ttu-id="850ad-153">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="850ad-153">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="850ad-154">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="850ad-154">Control Flow</span></span>](control-flow.md)  
  
  
