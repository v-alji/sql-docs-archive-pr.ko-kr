---
title: 사용자 지정 개체를 사용한 패키지 확장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0159983f518e51aa082ea23745663e7f09eee1fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727288"
---
# <a name="extending-packages-with-custom-objects"></a><span data-ttu-id="b9616-102">사용자 지정 개체를 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="b9616-102">Extending Packages with Custom Objects</span></span>
  <span data-ttu-id="b9616-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 제공된 구성 요소가 개발자의 요구 사항을 충족시키지 못할 경우 개발자 고유의 확장을 코딩하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-103">If you find that the components provided in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="b9616-104">두 가지 방법으로 패키지를 확장할 수 있습니다. 스크립트 태스크 및 스크립트 구성 요소에서 제공하는 강력한 래퍼 내에 코드를 작성할 수도 있고, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체 모델에서 제공하는 기본 클래스의 파생 클래스를 만들어 사용자 지정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 확장을 처음부터 새로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-104">You have two discrete options for extending your packages: you can write code within the powerful wrappers provided by the Script task and the Script component, or you can create custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] extensions from scratch by deriving from the base classes provided by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="b9616-105">이 섹션에서는 이 둘 중 보다 고급 방법인 사용자 지정 개체를 사용한 패키지 확장 방법에 대해 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-105">This section explores the more advanced of the two options - extending packages with custom objects.</span></span>  
  
 <span data-ttu-id="b9616-106">사용자 지정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 솔루션에 스크립트 태스크 및 스크립트 구성 요소가 제공하는 것 이상의 유연성이 필요한 경우 또는 여러 패키지에서 다시 사용할 수 있는 구성 요소가 필요한 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체 모델을 사용하면 관리 코드로 완벽하게 사용자 지정 작업, 데이터 흐름 구성 요소 및 기타 패키지 개체를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-106">When your custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] solution requires more flexibility than the Script task and the Script component provide, or when you need a component that you can reuse in multiple packages, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model lets you build custom tasks, data flow components, and other package objects in managed code from the ground up.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9616-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b9616-107">In This Section</span></span>  
 [<span data-ttu-id="b9616-108">Integration Services용 사용자 지정 개체 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-108">Developing Custom Objects for Integration Services</span></span>](developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="b9616-109">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 대해 만들 수 있는 사용자 지정 개체를 설명하고 필수 단계 및 설정을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-109">Discusses the custom objects that can be created for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and summarizes the essential steps and settings.</span></span>  
  
 [<span data-ttu-id="b9616-110">사용자 지정 개체 지속</span><span class="sxs-lookup"><span data-stu-id="b9616-110">Persisting Custom Objects</span></span>](persisting-custom-objects.md)  
 <span data-ttu-id="b9616-111">사용자 지정 개체의 기본 지속성과 사용자 지정 지속성의 구현 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-111">Discusses the default persistence of custom objects, and the process of implementing custom persistence.</span></span>  
  
 [<span data-ttu-id="b9616-112">사용자 지정 개체 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="b9616-112">Building, Deploying, and Debugging Custom Objects</span></span>](building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="b9616-113">다양한 유형의 사용자 지정 개체를 빌드, 배포 및 테스트하는 일반적인 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-113">Discusses the common approaches to building, deploying and testing the various types of custom objects.</span></span>  
  
 [<span data-ttu-id="b9616-114">사용자 지정 태스크 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-114">Developing a Custom Task</span></span>](task/developing-a-custom-task.md)  
 <span data-ttu-id="b9616-115">사용자 지정 태스크의 코딩 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-115">Describes the process of coding a custom task.</span></span>  
  
 [<span data-ttu-id="b9616-116">사용자 지정 연결 관리자 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-116">Developing a Custom Connection Manager</span></span>](connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="b9616-117">사용자 지정 연결 관리자의 코딩 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-117">Describes the process of coding a custom connection manager.</span></span>  
  
 [<span data-ttu-id="b9616-118">사용자 지정 로그 공급자 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-118">Developing a Custom Log Provider</span></span>](log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="b9616-119">사용자 지정 로그 공급자의 코딩 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-119">Describes the process of coding a custom log provider.</span></span>  
  
 [<span data-ttu-id="b9616-120">사용자 지정 ForEach 열거자 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-120">Developing a Custom ForEach Enumerator</span></span>](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="b9616-121">사용자 지정 열거자의 코딩 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-121">Describes the process of coding a custom enumerator.</span></span>  
  
 [<span data-ttu-id="b9616-122">사용자 지정 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="b9616-122">Developing a Custom Data Flow Component</span></span>](data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="b9616-123">사용자 지정 데이터 흐름 원본, 변환 및 대상을 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-123">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b9616-124">참조</span><span class="sxs-lookup"><span data-stu-id="b9616-124">Reference</span></span>  
 [<span data-ttu-id="b9616-125">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="b9616-125">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="b9616-126">미리 정의된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 코드와 해당 심볼 이름 및 설명을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-126">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9616-127">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="b9616-127">Related Sections</span></span>  
 [<span data-ttu-id="b9616-128">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="b9616-128">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="b9616-129">스크립트 태스크를 사용하여 제어 흐름을 확장하는 방법이나 스크립트 구성 요소를 사용하여 데이터 흐름을 확장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-129">Discusses how to extend the control flow by using the Script task, or extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="b9616-130">프로그래밍 방식으로 패키지 빌드</span><span class="sxs-lookup"><span data-stu-id="b9616-130">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="b9616-131">프로그래밍 방식으로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만들고 구성, 로드, 저장 및 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9616-131">Describes how to create, configure, run, load, save, and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="b9616-132">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b9616-132">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b9616-133">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b9616-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b9616-134">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b9616-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b9616-135">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="b9616-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9616-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9616-136">See Also</span></span>  
 <span data-ttu-id="b9616-137">[스크립팅 솔루션과 사용자 지정 개체 비교](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="b9616-137">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="b9616-138">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="b9616-138">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
