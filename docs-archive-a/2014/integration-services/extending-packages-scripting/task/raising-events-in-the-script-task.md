---
title: 스크립트 태스크에서 이벤트 발생 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e20a276b91e434b6915cfb218eba17c07acd6544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731895"
---
# <a name="raising-events-in-the-script-task"></a><span data-ttu-id="809dd-102">스크립트 태스크에서 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="809dd-102">Raising Events in the Script Task</span></span>
  <span data-ttu-id="809dd-103">이벤트를 사용하면 포함하는 패키지에 오류 및 경고와 태스크 진행률 또는 상태 같은 기타 정보를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="809dd-104">패키지에서는 이벤트 알림을 관리하기 위한 이벤트 처리기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="809dd-105">스크립트 태스크에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 속성에서 메서드를 호출하여 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-105">The Script task can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="809dd-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지 처리 이벤트에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 이벤트 처리기](../../integration-services-ssis-event-handlers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="809dd-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="809dd-107">이벤트는 패키지에서 사용할 수 있도록 설정된 모든 로그 공급자에 로깅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="809dd-108">로그 공급자는 이벤트에 대한 정보를 데이터 원본에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="809dd-109">스크립트 태스크에서는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드를 사용하여 이벤트를 발생시키지 않고 로그 공급자에 정보를 로깅할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-109">The Script task can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="809dd-110"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드의 사용 방법은 [스크립트 태스크에서 로깅](logging-in-the-script-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="809dd-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method, see [Logging in the Script Task](logging-in-the-script-task.md).</span></span>  
  
 <span data-ttu-id="809dd-111">이벤트를 발생시키기 위해 스크립트 태스크에서는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 속성에 의해 제공된 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-111">To raise an event, the Script task calls one of the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span> <span data-ttu-id="809dd-112">다음 표에서는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 속성에 의해 제공된 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-112">The following table lists the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
|<span data-ttu-id="809dd-113">행사</span><span class="sxs-lookup"><span data-stu-id="809dd-113">Event</span></span>|<span data-ttu-id="809dd-114">Description</span><span class="sxs-lookup"><span data-stu-id="809dd-114">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|<span data-ttu-id="809dd-115">패키지에서 사용자가 정의한 사용자 지정 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-115">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|<span data-ttu-id="809dd-116">패키지에 오류 조건을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-116">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|<span data-ttu-id="809dd-117">사용자에게 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-117">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|<span data-ttu-id="809dd-118">패키지에 태스크 진행률을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-118">Informs the package of the progress of the task.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|<span data-ttu-id="809dd-119">패키지에서 태스크를 중간에 종료해야 하는지 여부를 나타내는 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-119">Returns a value that indicates whether the package needs the task to shut down prematurely.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|<span data-ttu-id="809dd-120">태스크가 사용자 알림이 발생할 수 있지만 오류 조건은 아닌 상태에 있음을 패키지에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-120">Informs the package that the task is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
## <a name="events-example"></a><span data-ttu-id="809dd-121">이벤트 예</span><span class="sxs-lookup"><span data-stu-id="809dd-121">Events Example</span></span>  
 <span data-ttu-id="809dd-122">다음 예에서는 스크립트 태스크 내에서 이벤트를 발생시키는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-122">The following example demonstrates how to raise events from within the Script task.</span></span> <span data-ttu-id="809dd-123">이 예에서는 네이티브 Windows API 함수를 사용하여 인터넷 연결을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-123">The example uses a native Windows API function to determine whether an Internet connection is available.</span></span> <span data-ttu-id="809dd-124">연결을 사용할 수 없으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-124">If no connection is available, it raises an error.</span></span> <span data-ttu-id="809dd-125">불안정할 수 있는 모뎀 연결이 사용 중인 경우에는 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-125">If a potentially volatile modem connection is in use, the example raises a warning.</span></span> <span data-ttu-id="809dd-126">그렇지 않은 경우 인터넷 연결이 검색되었다는 정보 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="809dd-126">Otherwise, it returns an informational message that an Internet connection has been detected.</span></span>  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
<span data-ttu-id="809dd-127">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="809dd-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="809dd-128">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="809dd-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="809dd-129">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="809dd-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="809dd-130">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="809dd-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="809dd-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="809dd-131">See Also</span></span>  
 <span data-ttu-id="809dd-132">[Integration Services&#40;SSIS&#41; 이벤트 처리기](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="809dd-132">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="809dd-133">패키지에 이벤트 처리기 추가</span><span class="sxs-lookup"><span data-stu-id="809dd-133">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
