---
title: 스크립트 구성 요소의 로깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c29dfffee6cacb39272aef07caa5539555cdd4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652204"
---
# <a name="logging-in-the-script-component"></a><span data-ttu-id="f4851-102">스크립트 구성 요소의 로깅</span><span class="sxs-lookup"><span data-stu-id="f4851-102">Logging in the Script Component</span></span>
  <span data-ttu-id="f4851-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지의 로깅 기능을 사용하면 나중에 분석할 수 있도록 미리 정의된 이벤트나 사용자 정의 메시지를 기록하여 실행 진행률, 결과 및 문제에 대한 세부 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-103">Logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="f4851-104">스크립트 구성 요소에서는 `ScriptMain` 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 사용하여 사용자 정의 데이터를 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-104">The Script component can use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class to log user-defined data.</span></span> <span data-ttu-id="f4851-105">로깅을 사용하도록 설정하고 **SSIS 로그 구성** 대화 상자의 **자세히** 탭에서 **ScriptComponentLogEntry** 이벤트를 로깅하도록 선택할 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 한 번만 호출하면 데이터 흐름 태스크에 대해 구성된 모든 로그 공급자에 해당 이벤트 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-105">If logging is enabled, and the **ScriptComponentLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method stores the event information in all the log providers that have been configured for the data flow task.</span></span>  
  
 <span data-ttu-id="f4851-106">다음은 간단한 로깅 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-106">Here is a simple example of logging:</span></span>  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  <span data-ttu-id="f4851-107">스크립트 구성 요소에서 직접 로깅을 수행할 수도 있지만 로깅보다는 이벤트를 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-107">Although you can perform logging directly from your Script component, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="f4851-108">이벤트를 사용하면 이벤트 메시지의 로깅 기능을 사용할 수 있을 뿐 아니라 기본 또는 사용자 정의 이벤트 처리기를 사용하여 이벤트에 응답할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4851-108">When using events, not only can you enable the logging of event messages, but you can respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="f4851-109">로깅에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../../performance/integration-services-ssis-logging.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4851-109">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
<span data-ttu-id="f4851-110">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f4851-110">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f4851-111">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="f4851-111">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f4851-112">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="f4851-112">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f4851-113">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="f4851-113">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4851-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4851-114">See Also</span></span>  
 [<span data-ttu-id="f4851-115">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="f4851-115">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
