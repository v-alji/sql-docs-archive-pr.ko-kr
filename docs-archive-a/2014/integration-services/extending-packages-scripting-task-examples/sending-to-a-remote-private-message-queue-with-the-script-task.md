---
title: 스크립트 태스크를 사용하여 원격 프라이빗 메시지 큐에 메시지 보내기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 308815293dfc41f0a0ac60c21ce7f561a5e7f660
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732736"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a><span data-ttu-id="df7b8-102">스크립트 태스크를 사용하여 원격 프라이빗 메시지 큐에 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="df7b8-102">Sending to a Remote Private Message Queue with the Script Task</span></span>
  <span data-ttu-id="df7b8-103">개발자는 메시지 큐(MSMQ)를 통해 메시지를 주고 받는 방법으로 신속하고 안전하게 애플리케이션과 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-103">Message Queuing (also known as MSMQ) makes it easy for developers to communicate with application programs quickly and reliably by sending and receiving messages.</span></span> <span data-ttu-id="df7b8-104">메시지 큐는 로컬 컴퓨터나 원격 컴퓨터에 있을 수 있으며 퍼블릭 큐이거나 프라이빗 큐일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-104">A message queue may be located on the local computer or a remote computer, and may be public or private.</span></span> <span data-ttu-id="df7b8-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 MSMQ 연결 관리자와 메시지 큐 태스크에서 원격 컴퓨터의 프라이빗 큐로 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-105">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the MSMQ connection manager and Message Queue task do not support sending to a private queue on a remote computer.</span></span> <span data-ttu-id="df7b8-106">그러나 스크립트 태스크를 사용하면 원격 프라이빗 메시지 큐에 메시지를 쉽게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-106">However, by using the Script task, it is easy to send a message to a remote private queue.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df7b8-107">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="df7b8-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="df7b8-108">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df7b8-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="df7b8-109">Description</span><span class="sxs-lookup"><span data-stu-id="df7b8-109">Description</span></span>  
 <span data-ttu-id="df7b8-110">다음 예에서는 기존 MSMQ 연결 관리자와 System.Messaging 네임스페이스의 개체 및 메서드를 사용하여 패키지 변수에 들어 있는 텍스트를 원격 프라이빗 메시지 큐에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-110">The following example uses an existing MSMQ connection manager, together with objects and methods from the System.Messaging namespace, to send the text contained in a package variable to a remote private message queue.</span></span> <span data-ttu-id="df7b8-111">MSMQ 연결 관리자의 M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection (System.object) 메서드를 호출 하면이 작업을 수행 하는 메서드가 포함 된 **MessageQueue** 개체가 반환 `Send` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-111">The call to the M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) method of the MSMQ connection manager returns a **MessageQueue** object whose `Send` method accomplishes this task.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="df7b8-112">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="df7b8-112">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="df7b8-113">기본 이름을 사용하여 MSMQ 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-113">Create an MSMQ connection manager with the default name.</span></span> <span data-ttu-id="df7b8-114">다음과 같은 형식으로 올바른 원격 프라이빗 큐의 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-114">Set the path of a valid remote private queue, in the following format:</span></span>  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  <span data-ttu-id="df7b8-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]형식의 **MessageText** 이라는 변수를 만들어 `String` 메시지 텍스트를 스크립트에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-115">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable named **MessageText** of type `String` to pass the message text into the script.</span></span> <span data-ttu-id="df7b8-116">변수의 값으로 기본 메시지를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-116">Enter a default message as the value of the variable.</span></span>  
  
3.  <span data-ttu-id="df7b8-117">디자인 화면에 스크립트 태스크를 추가하고 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-117">Add a Script Task to the design surface and edit it.</span></span> <span data-ttu-id="df7b8-118">**스크립트 태스크 편집기**의 **스크립트** 탭에서 **ReadOnlyVariables** 속성에 `MessageText` 변수를 추가하여 해당 변수를 스크립트 내에서 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-118">On the **Script** tab of the **Script Task Editor**, add the `MessageText` variable to the **ReadOnlyVariables** property to make the variable available inside the script.</span></span>  
  
4.  <span data-ttu-id="df7b8-119">**스크립트 편집**을 클릭하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-119">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) script editor.</span></span>  
  
5.  <span data-ttu-id="df7b8-120">`System.Messaging` 네임스페이스에 대한 참조를 스크립트 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-120">Add a reference in the script project to the `System.Messaging` namespace.</span></span>  
  
6.  <span data-ttu-id="df7b8-121">스크립트 창의 내용을 다음 섹션의 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="df7b8-121">Replace the contents of the script window with the code in the following section.</span></span>  
  
## <a name="code"></a><span data-ttu-id="df7b8-122">코드</span><span class="sxs-lookup"><span data-stu-id="df7b8-122">Code</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
<span data-ttu-id="df7b8-123">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="df7b8-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="df7b8-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="df7b8-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="df7b8-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="df7b8-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="df7b8-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="df7b8-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7b8-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df7b8-127">See Also</span></span>  
 [<span data-ttu-id="df7b8-128">메시지 큐 태스크</span><span class="sxs-lookup"><span data-stu-id="df7b8-128">Message Queue Task</span></span>](../control-flow/message-queue-task.md)  
  
  
