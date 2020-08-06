---
title: 사용자 지정 태스크 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9d3446acff7ced73ab47014bec51708dba225b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652954"
---
# <a name="developing-a-custom-task"></a><span data-ttu-id="98a6d-102">사용자 지정 태스크 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-102">Developing a Custom Task</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="98a6d-103">에서는 태스크를 사용하여 데이터의 추출, 변환 및 로드를 지원하는 작업 단위를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-103">uses tasks to perform units of work in support of the extraction, transformation, and loading of data.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="98a6d-104">에는 SQL 문 실행부터 FTP 사이트의 파일 다운로드에 이르기까지 가장 자주 사용되는 동작을 수행하는 다양한 태스크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-104">includes a variety of tasks that perform the most frequently used actions, from executing an SQL statement to downloading a file from an FTP site.</span></span> <span data-ttu-id="98a6d-105">포함된 태스크와 지원되는 동작이 요구 사항을 완전히 충족시키지 못할 경우에는 사용자 지정 태스크를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-105">If the included tasks and supported actions do not completely meet your requirements, you can create a custom task.</span></span>  
  
 <span data-ttu-id="98a6d-106">사용자 지정 태스크를 만들려면 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 기본 클래스에서 상속되는 클래스를 만들고 새 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성을 적용한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드를 포함하여 기본 클래스의 중요한 메서드와 속성을 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-106">To create a custom task, you have to create a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98a6d-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="98a6d-107">In This Section</span></span>  
 <span data-ttu-id="98a6d-108">이 섹션에서는 사용자 지정 태스크와 선택 사항인 태스크의 사용자 지정 사용자 인터페이스를 만들고 구성하고 코딩하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-108">This section describes how to create, configure, and code a custom task and its optional custom user interface.</span></span>  
  
 [<span data-ttu-id="98a6d-109">사용자 지정 태스크 만들기</span><span class="sxs-lookup"><span data-stu-id="98a6d-109">Creating a Custom Task</span></span>](creating-a-custom-task.md)  
 <span data-ttu-id="98a6d-110">사용자 지정 태스크를 만드는 첫 번째 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-110">Describes the first step, which is creating the custom task.</span></span>  
  
 [<span data-ttu-id="98a6d-111">사용자 지정 태스크 코딩</span><span class="sxs-lookup"><span data-stu-id="98a6d-111">Coding a Custom Task</span></span>](coding-a-custom-task.md)  
 <span data-ttu-id="98a6d-112">사용자 지정 태스크의 주요 메서드를 코딩하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-112">Describes how to code the principal methods of a custom task.</span></span>  
  
 [<span data-ttu-id="98a6d-113">사용자 지정 태스크에서 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="98a6d-113">Connecting to Data Sources in a Custom Task</span></span>](connecting-to-data-sources-in-a-custom-task.md)  
 <span data-ttu-id="98a6d-114">사용자 지정 태스크를 데이터 원본에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-114">Describes how to connect a custom task to a data source.</span></span>  
  
 [<span data-ttu-id="98a6d-115">사용자 지정 태스크에서 이벤트 발생 및 정의</span><span class="sxs-lookup"><span data-stu-id="98a6d-115">Raising and Defining Events in a Custom Task</span></span>](raising-and-defining-events-in-a-custom-task.md)  
 <span data-ttu-id="98a6d-116">사용자 지정 태스크에서 이벤트를 발생시키고 사용자 지정 이벤트를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-116">Describes how to raise events and define custom events from the custom task.</span></span>  
  
 [<span data-ttu-id="98a6d-117">사용자 지정 태스크에 디버깅 지원 추가</span><span class="sxs-lookup"><span data-stu-id="98a6d-117">Adding Support for Debugging in a Custom Task</span></span>](adding-support-for-debugging-in-a-custom-task.md)  
 <span data-ttu-id="98a6d-118">사용자 지정 태스크에 중단점 대상을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-118">Describes how to create breakpoint targets in the custom task.</span></span>  
  
 [<span data-ttu-id="98a6d-119">사용자 지정 태스크의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-119">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
 <span data-ttu-id="98a6d-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에 표시되는 사용자 인터페이스를 만들어 사용자 지정 태스크의 속성을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-120">Describes how to create a user interface that shows in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to configure properties on the custom task.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="98a6d-121">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="98a6d-121">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="98a6d-122">모든 사용자 지정 개체에 대한 일반적인 정보</span><span class="sxs-lookup"><span data-stu-id="98a6d-122">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="98a6d-123">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 모든 사용자 지정 개체 유형에 공통적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98a6d-123">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="98a6d-124">Integration Services용 사용자 지정 개체 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-124">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="98a6d-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 모든 종류의 사용자 지정 개체를 구현하는 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-125">Describes the basic steps in implementing all kinds of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="98a6d-126">사용자 지정 개체 지속</span><span class="sxs-lookup"><span data-stu-id="98a6d-126">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="98a6d-127">사용자 지정 지속성 및 해당 지속성이 필요한 경우에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-127">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="98a6d-128">사용자 지정 개체 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="98a6d-128">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="98a6d-129">사용자 지정 개체를 작성, 서명, 배포 및 디버깅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-129">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="98a6d-130">기타 사용자 지정 개체에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="98a6d-130">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="98a6d-131">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 기타 사용자 지정 개체 유형에 대한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98a6d-131">For information about the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="98a6d-132">사용자 지정 연결 관리자 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-132">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="98a6d-133">사용자 지정 연결 관리자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-133">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="98a6d-134">사용자 지정 로그 공급자 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-134">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="98a6d-135">사용자 지정 로그 공급자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-135">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="98a6d-136">사용자 지정 ForEach 열거자 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-136">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="98a6d-137">사용자 지정 열거자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-137">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="98a6d-138">사용자 지정 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="98a6d-138">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="98a6d-139">사용자 지정 데이터 흐름 원본, 변환 및 대상을 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98a6d-139">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="98a6d-140">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="98a6d-140">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="98a6d-141">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="98a6d-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="98a6d-142">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="98a6d-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="98a6d-143">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="98a6d-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a6d-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98a6d-144">See Also</span></span>  
 <span data-ttu-id="98a6d-145">[스크립트 태스크를 사용하여 패키지 확장](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span><span class="sxs-lookup"><span data-stu-id="98a6d-145">[Extending the Package with the Script Task](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span></span>  
 [<span data-ttu-id="98a6d-146">스크립팅 솔루션과 사용자 지정 개체 비교</span><span class="sxs-lookup"><span data-stu-id="98a6d-146">Comparing Scripting Solutions and Custom Objects</span></span>](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
