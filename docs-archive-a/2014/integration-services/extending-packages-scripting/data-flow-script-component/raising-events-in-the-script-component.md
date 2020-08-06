---
title: 스크립트 구성 요소에서 이벤트 발생 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78eb44239f4e58e43bdd65c41d5fdeb58d053a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652202"
---
# <a name="raising-events-in-the-script-component"></a><span data-ttu-id="eb73b-102">스크립트 구성 요소에서 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="eb73b-102">Raising Events in the Script Component</span></span>
  <span data-ttu-id="eb73b-103">이벤트를 사용하면 포함하는 패키지에 오류 및 경고와 태스크 진행률 또는 상태 같은 기타 정보를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="eb73b-104">패키지에서는 이벤트 알림을 관리하기 위한 이벤트 처리기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="eb73b-105">스크립트 구성 요소에서는 `ScriptMain` 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 속성에서 메서드를 호출하여 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-105">The Script component can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class.</span></span> <span data-ttu-id="eb73b-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지 처리 이벤트에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 이벤트 처리기](../../integration-services-ssis-event-handlers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eb73b-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="eb73b-107">이벤트는 패키지에서 사용할 수 있도록 설정된 모든 로그 공급자에 로깅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="eb73b-108">로그 공급자는 이벤트에 대한 정보를 데이터 원본에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="eb73b-109">스크립트 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 사용하여 이벤트를 발생시키지 않고 로그 공급자에 정보를 로깅할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-109">The Script component can also use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="eb73b-110"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드의 사용 방법은 다음 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eb73b-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method, see the following section.</span></span>  
  
 <span data-ttu-id="eb73b-111">이벤트를 발생시키기 위해 스크립트 태스크에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 속성에 의해 제공된 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 인터페이스의 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-111">To raise an event, the Script task calls one of the following methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface exposed by the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property:</span></span>  
  
|<span data-ttu-id="eb73b-112">행사</span><span class="sxs-lookup"><span data-stu-id="eb73b-112">Event</span></span>|<span data-ttu-id="eb73b-113">Description</span><span class="sxs-lookup"><span data-stu-id="eb73b-113">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|<span data-ttu-id="eb73b-114">패키지에서 사용자가 정의한 사용자 지정 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-114">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|<span data-ttu-id="eb73b-115">패키지에 오류 조건을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-115">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|<span data-ttu-id="eb73b-116">사용자에게 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-116">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|<span data-ttu-id="eb73b-117">패키지에 구성 요소 진행률을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-117">Informs the package of the progress of the component.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|<span data-ttu-id="eb73b-118">구성 요소가 사용자 알림이 발생할 수 있지만 오류 조건은 아닌 상태에 있음을 패키지에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-118">Informs the package that the component is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
 <span data-ttu-id="eb73b-119">다음은 Error 이벤트를 발생시키는 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eb73b-119">Here is a simple example of raising an Error event:</span></span>  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
<span data-ttu-id="eb73b-120">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="eb73b-120">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="eb73b-121">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="eb73b-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="eb73b-122">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="eb73b-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="eb73b-123">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="eb73b-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb73b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb73b-124">See Also</span></span>  
 <span data-ttu-id="eb73b-125">[Integration Services&#40;SSIS&#41; 이벤트 처리기](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="eb73b-125">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="eb73b-126">패키지에 이벤트 처리기 추가</span><span class="sxs-lookup"><span data-stu-id="eb73b-126">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
