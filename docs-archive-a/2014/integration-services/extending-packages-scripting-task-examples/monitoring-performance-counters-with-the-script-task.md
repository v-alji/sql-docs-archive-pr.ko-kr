---
title: 스크립트 태스크를 사용하여 성능 카운터 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 143e11ff966eb11961aa15073a503522c4b9c86b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736573"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a><span data-ttu-id="e8b59-102">스크립트 태스크를 사용하여 성능 카운터 모니터링</span><span class="sxs-lookup"><span data-stu-id="e8b59-102">Monitoring Performance Counters with the Script Task</span></span>
  <span data-ttu-id="e8b59-103">관리자는 대량의 데이터에 대해 복잡한 변환을 수행하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 성능을 모니터링하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-103">Administrators may need to monitor the performance of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that perform complex transformations on large amounts of data.</span></span> <span data-ttu-id="e8b59-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 **System.Diagnostics** 네임스페이스에서는 기존 성능 카운터를 사용하고 개발자 고유의 성능 카운터를 만들기 위한 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-104">The **System.Diagnostics** namespace of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for using existing performance counters and for creating your own performance counters.</span></span>  
  
 <span data-ttu-id="e8b59-105">성능 카운터는 시간 경과에 따른 소프트웨어 성능을 분석하는 데 사용할 수 있는 애플리케이션 성능 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-105">Performance counters store application performance information that you can use to analyze the performance of software over time.</span></span> <span data-ttu-id="e8b59-106">**성능 모니터** 도구를 사용하여 로컬 또는 원격으로 성능 카운터를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-106">Performance counters can be monitored locally or remotely by using the **Performance Monitor** tool.</span></span> <span data-ttu-id="e8b59-107">나중에 패키지에서 제어 흐름을 분기할 수 있도록 성능 카운터의 값을 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-107">You can store the values of performance counters in variables for later control flow branching in the package.</span></span>  
  
 <span data-ttu-id="e8b59-108">성능 카운터를 사용하는 대신 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 속성을 통해 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 이벤트를 발생시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-108">As an alternative to using performance counters, you can raise the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="e8b59-109"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 이벤트는 진행률 및 완료율 정보를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-109">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event returns both incremental progress and percentage complete information to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8b59-110">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="e8b59-110">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="e8b59-111">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b59-111">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="e8b59-112">Description</span><span class="sxs-lookup"><span data-stu-id="e8b59-112">Description</span></span>  
 <span data-ttu-id="e8b59-113">다음 예에서는 사용자 지정 성능 카운터를 만들고 해당 카운터를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-113">The following example creates a custom performance counter and increments the counter.</span></span> <span data-ttu-id="e8b59-114">이 예에서는 먼저 성능 카운터가 이미 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-114">First, the example determines whether the performance counter already exists.</span></span> <span data-ttu-id="e8b59-115">성능 카운터가 만들어지지 않은 경우 스크립트에서는 `Create` 개체의 `PerformanceCounterCategory` 메서드를 호출하여 성능 카운터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-115">If the performance counter has not been created, the script calls the `Create` method of the `PerformanceCounterCategory` object to create it.</span></span> <span data-ttu-id="e8b59-116">성능 카운터를 만든 후에는 스크립트에서 해당 카운터를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-116">After the performance counter has been created, the script increments the counter.</span></span> <span data-ttu-id="e8b59-117">마지막으로, 성능 카운터가 더 이상 필요하지 않은 경우 성능 카운터에서 `Close` 메서드를 호출하는 최상의 방법을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-117">Finally, the example follows the best practice of calling the `Close` method on the performance counter when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8b59-118">성능 카운터 범주와 성능 카운터를 새로 만들려면 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-118">Creating a new performance counter category and performance counter requires administrative rights.</span></span> <span data-ttu-id="e8b59-119">또한 새 범주 및 카운터는 만든 후에도 해당 컴퓨터에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-119">Also, the new category and counter persist on the computer after creation.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="e8b59-120">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e8b59-120">To configure this Script Task example</span></span>  
  
-   <span data-ttu-id="e8b59-121">`Imports`코드에서 문을 사용 하 여 **Diagnostics** 네임 스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8b59-121">Use an `Imports` statement in your code to import the **System.Diagnostics** namespace.</span></span>  
  
### <a name="example-code"></a><span data-ttu-id="e8b59-122">코드 예</span><span class="sxs-lookup"><span data-stu-id="e8b59-122">Example Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
<span data-ttu-id="e8b59-123">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e8b59-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e8b59-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b59-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e8b59-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b59-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e8b59-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b59-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
