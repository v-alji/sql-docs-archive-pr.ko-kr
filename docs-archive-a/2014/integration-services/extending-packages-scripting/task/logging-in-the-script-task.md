---
title: 스크립트 태스크에서 로깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61f7a46088de5df2765d860bd4a43e4872a1be6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731899"
---
# <a name="logging-in-the-script-task"></a><span data-ttu-id="d1e99-102">스크립트 태스크에서 로깅</span><span class="sxs-lookup"><span data-stu-id="d1e99-102">Logging in the Script Task</span></span>
  <span data-ttu-id="d1e99-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지의 로깅 기능을 사용하면 나중에 분석할 수 있도록 미리 정의된 이벤트나 사용자 정의 메시지를 기록하여 실행 진행률, 결과 및 문제에 대한 세부 정보를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-103">The use of logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you record detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="d1e99-104">스크립트 태스크에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드를 사용하여 사용자 정의 데이터를 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-104">The Script task can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method of the `Dts` object to log user-defined data.</span></span> <span data-ttu-id="d1e99-105">로깅을 사용하도록 설정하고 **SSIS 로그 구성** 대화 상자의 **자세히** 탭에서 **ScriptTaskLogEntry** 이벤트를 로깅하도록 선택할 경우 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드를 한 번만 호출하면 태스크에 대해 구성된 모든 로그 공급자에 해당 이벤트 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-105">If logging is enabled, and the **ScriptTaskLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method stores the event information in all the log providers configured for the task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1e99-106">스크립트 태스크에서 직접 로깅을 수행할 수도 있지만 로깅보다는 이벤트를 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-106">Although you can perform logging directly from your Script task, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="d1e99-107">이벤트를 사용하면 이벤트 메시지의 로깅 기능을 사용할 수 있을 뿐 아니라 기본 또는 사용자 정의 이벤트 처리기를 사용하여 이벤트에 응답할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-107">When using events, not only can you enable the logging of event messages, but you can also respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="d1e99-108">로깅에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../../performance/integration-services-ssis-logging.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e99-108">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
## <a name="logging-example"></a><span data-ttu-id="d1e99-109">로깅 예</span><span class="sxs-lookup"><span data-stu-id="d1e99-109">Logging Example</span></span>  
 <span data-ttu-id="d1e99-110">다음 예에서는 처리된 행 수를 나타내는 값을 로깅하여 스크립트 태스크에서의 로깅을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1e99-110">The following example demonstrates logging from the Script task by logging a value that represents the number of rows processed.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 <span data-ttu-id="d1e99-111">}</span><span class="sxs-lookup"><span data-stu-id="d1e99-111">}</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d1e99-112">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="d1e99-112">External Resources</span></span>  
  
<span data-ttu-id="d1e99-113">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d1e99-113">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d1e99-114">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e99-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d1e99-115">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e99-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d1e99-116">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e99-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e99-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1e99-117">See Also</span></span>  
 [<span data-ttu-id="d1e99-118">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="d1e99-118">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
