---
title: 사용자 지정 데이터 흐름 구성 요소 개발 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7126129ede3f419c6fbdcae6245a47636e6e65ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734379"
---
# <a name="developing-a-custom-data-flow-component"></a><span data-ttu-id="1a979-102">사용자 지정 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="1a979-102">Developing a Custom Data Flow Component</span></span>
  <span data-ttu-id="1a979-103">데이터 흐름 태스크는 다양한 데이터 원본에 연결한 다음 해당 데이터를 빠른 속도로 변환하고 라우팅하는 여러 구성 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-103">The data flow task consists of components that connect to a variety of data sources and then transform and route that data at high speed.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1a979-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서는 개발자가 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]와 배포된 패키지에서 사용할 수 있는 사용자 지정 원본, 변환 및 대상을 만들 수 있게 해주는 확장 가능한 개체 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides an extensible object model that lets developers create custom sources, transformations, and destinations that you can use in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and in deployed packages.</span></span> <span data-ttu-id="1a979-105">이 섹션에는 사용자 지정 데이터 흐름 구성 요소의 개발 과정을 설명하는 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-105">This section contains topics that will guide you in developing custom data flow components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1a979-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1a979-106">In This Section</span></span>
 <span data-ttu-id="1a979-107">[사용자 지정 데이터 흐름 구성 요소 만들기](creating-a-custom-data-flow-component.md) 사용자 지정 데이터 흐름 구성 요소를 만드는 초기 단계에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-107">[Creating a Custom Data Flow Component](creating-a-custom-data-flow-component.md) Describes the initial steps in creating a custom data flow component.</span></span>

 <span data-ttu-id="1a979-108">[데이터 흐름 구성 요소의 디자인 타임 메서드](design-time-methods-of-a-data-flow-component.md) 사용자 지정 데이터 흐름 구성 요소에서 구현할 디자인 타임 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-108">[Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md) Describes the design-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="1a979-109">[데이터 흐름 구성 요소의 런타임 메서드](run-time-methods-of-a-data-flow-component.md) 사용자 지정 데이터 흐름 구성 요소에서 구현 하는 런타임 메서드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-109">[Run-time Methods of a Data Flow Component](run-time-methods-of-a-data-flow-component.md) Describes the run-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="1a979-110">[실행 계획 및 버퍼 할당](execution-plan-and-buffer-allocation.md) 데이터 흐름 실행 계획 및 데이터 버퍼 할당에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-110">[Execution Plan and Buffer Allocation](execution-plan-and-buffer-allocation.md) Describes the data flow execution plan and the allocation of data buffers.</span></span>

 <span data-ttu-id="1a979-111">[데이터 흐름의 데이터 형식 작업](working-with-data-types-in-the-data-flow.md) 데이터 흐름이 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 데이터 형식을 .NET Framework 관리 되는 데이터 형식에 매핑하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-111">[Working with Data Types in the Data Flow](working-with-data-types-in-the-data-flow.md) Explains how the data flow maps [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types to .NET Framework managed data types.</span></span>

 <span data-ttu-id="1a979-112">[데이터 흐름 구성 요소의 유효성 검사](validating-a-data-flow-component.md) 구성 요소 구성을 확인 하 고 구성 요소 메타 데이터를 다시 구성 하는 데 사용 되는 메서드를 설명 합니다</span><span class="sxs-lookup"><span data-stu-id="1a979-112">[Validating a Data Flow Component](validating-a-data-flow-component.md) Explains the methods used to validate component configuration and to reconfigure component metadata.</span></span>

 <span data-ttu-id="1a979-113">[외부 메타 데이터 구현](implementing-external-metadata.md) 외부 메타 데이터 열을 사용 하 여 데이터 유효성 검사를 수행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-113">[Implementing External Metadata](implementing-external-metadata.md) Explains how to use external metadata columns for data validation.</span></span>

 <span data-ttu-id="1a979-114">[데이터 흐름 구성 요소에서 이벤트 발생 및 정의](raising-and-defining-events-in-a-data-flow-component.md) 미리 정의 된 이벤트 및 사용자 지정 이벤트를 발생 시키는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-114">[Raising and Defining Events in a Data Flow Component](raising-and-defining-events-in-a-data-flow-component.md) Explains how to raise predefined and custom events.</span></span>

 <span data-ttu-id="1a979-115">[데이터 흐름 구성 요소에서 로그 항목 로깅 및 정의](logging-and-defining-log-entries-in-a-data-flow-component.md) 사용자 지정 로그 항목을 만들고 작성 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-115">[Logging and Defining Log Entries in a Data Flow Component](logging-and-defining-log-entries-in-a-data-flow-component.md) Explains how to create and write to custom log entries.</span></span>

 <span data-ttu-id="1a979-116">[데이터 흐름 구성 요소에서 오류 출력 사용](using-error-outputs-in-a-data-flow-component.md) 오류 행을 대체 출력으로 리디렉션하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-116">[Using Error Outputs in a Data Flow Component](using-error-outputs-in-a-data-flow-component.md) Explains how to redirect error rows to an alternative output.</span></span>

 <span data-ttu-id="1a979-117">[데이터 흐름 구성 요소의 버전 업그레이드](upgrading-the-version-of-a-data-flow-component.md) 구성 요소의 새 버전을 처음 사용할 때 저장 된 구성 요소 메타 데이터를 업데이트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-117">[Upgrading the Version of a Data Flow Component](upgrading-the-version-of-a-data-flow-component.md) Explains how to update saved component metadata when a new version of your component is first used.</span></span>

 <span data-ttu-id="1a979-118">[데이터 흐름 구성 요소에 대 한 사용자 인터페이스 개발](developing-a-user-interface-for-a-data-flow-component.md) 구성 요소에 대 한 사용자 지정 편집기를 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-118">[Developing a User Interface for a Data Flow Component](developing-a-user-interface-for-a-data-flow-component.md) Explains how to implement a custom editor for a component.</span></span>

 <span data-ttu-id="1a979-119">[특정 유형의 데이터 흐름 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) 세 가지 유형의 데이터 흐름 구성 요소인 원본, 변환 및 대상을 개발 하는 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-119">[Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Contains information about developing the three types of data flow components: sources, transformations, and destinations.</span></span>

## <a name="reference"></a><span data-ttu-id="1a979-120">참조</span><span class="sxs-lookup"><span data-stu-id="1a979-120">Reference</span></span>
 <span data-ttu-id="1a979-121"><xref:Microsoft.SqlServer.Dts.Pipeline>사용자 지정 데이터 흐름 구성 요소를 만드는 데 사용 되는 클래스 및 인터페이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-121"><xref:Microsoft.SqlServer.Dts.Pipeline> Contains the classes and interfaces used to create custom data flow components.</span></span>

 <span data-ttu-id="1a979-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>데이터 흐름 태스크 개체 모델을 구성 하 고 사용자 지정 데이터 흐름 구성 요소를 만들거나 데이터 흐름 태스크를 작성 하는 데 사용 되는 클래스 및 인터페이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> Contains the classes and interfaces that make up the data flow task object model, and is used to create custom data flow components or build a data flow task.</span></span>

 <span data-ttu-id="1a979-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design>데이터 흐름 구성 요소에 대 한 사용자 인터페이스를 만드는 데 사용 되는 클래스 및 인터페이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design> Contains the classes and interfaces used to create the user interface for data flow components.</span></span>

 <span data-ttu-id="1a979-124">[Integration Services 오류 및 메시지 참조](../../integration-services-error-and-message-reference.md) 미리 정의 된 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 오류 코드와 해당 심볼 이름 및 설명을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-124">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1a979-125">관련 단원</span><span class="sxs-lookup"><span data-stu-id="1a979-125">Related Sections</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="1a979-126">모든 사용자 지정 개체에 대한 일반적인 정보</span><span class="sxs-lookup"><span data-stu-id="1a979-126">Information Common to All Custom Objects</span></span>
 <span data-ttu-id="1a979-127">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 모든 사용자 지정 개체 유형에 공통적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a979-127">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="1a979-128">[Integration Services에 대 한 사용자 지정 개체 개발](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) 에 대 한 모든 형식의 사용자 지정 개체를 구현 하는 기본 단계를 설명 합니다 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a979-128">[Developing Custom Objects for Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="1a979-129">[사용자 지정 개체 유지](../../extending-packages-custom-objects/persisting-custom-objects.md) 사용자 지정 지 속성에 대해 설명 하 고 필요한 경우에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-129">[Persisting Custom Objects](../../extending-packages-custom-objects/persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="1a979-130">[사용자 지정 개체 빌드, 배포 및 디버깅](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) 사용자 지정 개체를 빌드, 서명, 배포 및 디버깅 하는 기술에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-130">[Building, Deploying, and Debugging Custom Objects](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="1a979-131">기타 사용자 지정 개체에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="1a979-131">Information about Other Custom Objects</span></span>
 <span data-ttu-id="1a979-132">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 기타 사용자 지정 개체 유형에 대한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a979-132">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="1a979-133">[사용자 지정 작업 개발](../../extending-packages-custom-objects/task/developing-a-custom-task.md) 사용자 지정 태스크를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-133">[Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="1a979-134">[사용자 지정 연결 관리자 개발](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) 사용자 지정 연결 관리자를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-134">[Developing a Custom Connection Manager](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="1a979-135">[사용자 지정 로그 공급자 개발](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) 사용자 지정 로그 공급자를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-135">[Developing a Custom Log Provider](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Discusses how to program custom log providers.</span></span>

 <span data-ttu-id="1a979-136">[사용자 지정 ForEach 열거자 개발](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) 사용자 지정 열거자를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a979-136">[Developing a Custom ForEach Enumerator](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

<span data-ttu-id="1a979-137">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1a979-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1a979-138">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="1a979-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1a979-139">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="1a979-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1a979-140">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="1a979-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a979-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a979-141">See Also</span></span>
 <span data-ttu-id="1a979-142">[스크립트 구성 요소를 사용 하 여 데이터 흐름 확장] (.. /.. /extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md [스크립팅 솔루션과 사용자 지정 개체 비교](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span><span class="sxs-lookup"><span data-stu-id="1a979-142">[Extending the Data Flow with the Script Component](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md [Comparing Scripting Solutions and Custom Objects](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span></span>


