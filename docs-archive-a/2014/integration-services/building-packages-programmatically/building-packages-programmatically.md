---
title: 프로그래밍 방식으로 패키지 작성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef8fd0b6b5bdeead718f204a0933771fe58924a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649643"
---
# <a name="building-packages-programmatically"></a><span data-ttu-id="4fc69-102">프로그래밍 방식으로 패키지 작성</span><span class="sxs-lookup"><span data-stu-id="4fc69-102">Building Packages Programmatically</span></span>
  <span data-ttu-id="4fc69-103">패키지를 동적으로 만들거나 개발 환경 외부에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 관리 및 실행해야 하는 경우 패키지를 프로그래밍 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-103">If you need to create packages dynamically, or to manage and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="4fc69-104">이 경우 다음 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-104">In this approach, you have a continuous range of options:</span></span>

-   <span data-ttu-id="4fc69-105">기존 패키지를 로드하고 수정하지 않은 채로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-105">Load and execute an existing package without modification.</span></span>

-   <span data-ttu-id="4fc69-106">기존 패키지를 로드하고 다시 구성(예를 들어 다른 데이터 원본에 사용할 수 있도록 구성)한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-106">Load an existing package, reconfigure it (for example, for a different data source), and execute it.</span></span>

-   <span data-ttu-id="4fc69-107">새 패키지를 만들고 구성 요소를 개체별 및 속성별로 구성한 다음 새 패키지를 저장 후 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-107">Create a new package, add and configure components object by object and property by property, save it, and execute it.</span></span>

 <span data-ttu-id="4fc69-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 개체 모델을 사용하면 패키지를 만들고 구성하고 실행하는 코드를 관리되는 프로그래밍 언어로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-108">You can use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to write code that creates, configures, and executes packages in any managed programming language.</span></span> <span data-ttu-id="4fc69-109">예를 들어 선택한 데이터 원본과 해당 데이터 원본의 테이블 및 열을 기반으로 연결이나 데이터 원본, 변환 및 대상을 구성하는 메타데이터 구동 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-109">For example, you may want to create metadata-driven packages that configure their connections or their data sources, transformations, and destinations based on the selected data source and its tables and columns.</span></span>

 <span data-ttu-id="4fc69-110">이 섹션에서는 패키지를 프로그래밍 방식으로 한 줄씩 만들고 구성하는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-110">This section describes and demonstrates how to create and configure a package programmatically line by line.</span></span> <span data-ttu-id="4fc69-111">위에 나열된 패키지 프로그래밍 방법 중 비교적 덜 복잡한 첫 번째 방법은 [프로그래밍 방식으로 패키지 실행 및 관리](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)에 설명된 대로 단순히 기존 패키지를 로드한 다음 수정하지 않은 채 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-111">At the less complex end of the range of package programming options, you can simply load and run an existing package without modification as described in [Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).</span></span>

 <span data-ttu-id="4fc69-112">두 번째 방법은 여기에서는 설명하지 않지만 기존 패키지를 템플릿으로 로드하고 다시 구성(예를 들어 다른 데이터 원본에 사용할 수 있도록 구성)한 다음 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-112">An intermediate option not described here is that of loading an existing package as a template, reconfiguring it (for example, for a different data source), and executing it.</span></span> <span data-ttu-id="4fc69-113">이 섹션의 정보를 사용하여 패키지의 기존 개체를 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-113">You can also use the information in this section to modify the existing objects in a package.</span></span>

> [!NOTE]
>  <span data-ttu-id="4fc69-114">기존 패키지를 템플릿으로 사용하고 데이터 흐름의 기존 열을 수정할 경우 기존 열을 제거하고 영향을 받는 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 메서드를 호출해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-114">When you use an existing package as a template and modify existing columns in the data flow, you may have to remove existing columns and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method of affected components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4fc69-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4fc69-115">In This Section</span></span>
 <span data-ttu-id="4fc69-116">[프로그래밍 방식으로 패키지 만들기](../building-packages-programmatically/creating-a-package-programmatically.md) 프로그래밍 방식으로 패키지를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-116">[Creating a Package Programmatically](../building-packages-programmatically/creating-a-package-programmatically.md) Describes how to create a package programmatically.</span></span>

 <span data-ttu-id="4fc69-117">[프로그래밍 방식으로 태스크 추가](../building-packages-programmatically/adding-tasks-programmatically.md) 패키지에 태스크를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-117">[Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md) Describes how to add tasks to the package.</span></span>

 <span data-ttu-id="4fc69-118">[프로그래밍 방식으로 태스크 연결](../building-packages-programmatically/connecting-tasks-programmatically.md) 이전 태스크 또는 컨테이너의 실행 결과에 따라 패키지의 컨테이너 및 태스크 실행을 제어 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-118">[Connecting Tasks Programmatically](../building-packages-programmatically/connecting-tasks-programmatically.md) Describes how to control execution of the containers and tasks in a package based on the result of the execution of a previous task or container.</span></span>

 <span data-ttu-id="4fc69-119">[프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md) 패키지에 연결 관리자를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-119">[Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md) Describes how to add connection managers to a package.</span></span>

 <span data-ttu-id="4fc69-120">[프로그래밍 방식으로 변수 작업](../building-packages-programmatically/working-with-variables-programmatically.md) 패키지를 실행 하는 동안 변수를 추가 하 고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-120">[Working with Variables Programmatically](../building-packages-programmatically/working-with-variables-programmatically.md) Describes how to add and use variables during package execution.</span></span>

 <span data-ttu-id="4fc69-121">[프로그래밍 방식으로 이벤트 처리](../building-packages-programmatically/handling-events-programmatically.md) 패키지 및 태스크 이벤트를 처리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-121">[Handling Events Programmatically](../building-packages-programmatically/handling-events-programmatically.md) Describes how to handle package and task events.</span></span>

 <span data-ttu-id="4fc69-122">[프로그래밍 방식으로 로깅 설정](../building-packages-programmatically/enabling-logging-programmatically.md) 패키지 또는 태스크에 대 한 로깅을 사용 하도록 설정 하는 방법 및 로그 이벤트에 사용자 지정 필터를 적용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-122">[Enabling Logging Programmatically](../building-packages-programmatically/enabling-logging-programmatically.md) Describes how to enable logging for a package or task, and how to apply custom filters to log events.</span></span>

 <span data-ttu-id="4fc69-123">[프로그래밍 방식으로 데이터 흐름 태스크 추가](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) 데이터 흐름 태스크 및 해당 구성 요소를 추가 하 고 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-123">[Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Describes how to add and configure the Data Flow task and its components.</span></span>

 <span data-ttu-id="4fc69-124">[프로그래밍 방식으로 데이터 흐름 구성 요소 검색](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) 로컬 컴퓨터에 설치 된 구성 요소를 검색 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-124">[Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Describes how to detect the components that are installed on the local computer.</span></span>

 <span data-ttu-id="4fc69-125">[프로그래밍 방식으로 데이터 흐름 구성 요소 추가](../building-packages-programmatically/adding-data-flow-components-programmatically.md) 데이터 흐름 태스크에 구성 요소를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-125">[Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Describes how to add a component to a data flow task.</span></span>

 <span data-ttu-id="4fc69-126">[프로그래밍 방식으로 데이터 흐름 구성 요소 연결](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) 두 데이터 흐름 구성 요소를 연결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-126">[Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Describes how to connect two data flow components.</span></span>

 <span data-ttu-id="4fc69-127">[프로그래밍 방식으로 입력 열 선택](../building-packages-programmatically/selecting-input-columns-programmatically.md) 데이터 흐름의 업스트림 구성 요소에서 구성 요소에 제공한 입력 열에서 입력 열을 선택 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-127">[Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md) Describes how to select input columns from those that are provided to a component by upstream components in the data flow.</span></span>

 <span data-ttu-id="4fc69-128">[프로그래밍 방식으로 패키지 저장](../building-packages-programmatically/saving-a-package-programmatically.md) 프로그래밍 방식으로 패키지를 저장 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-128">[Saving a Package Programmatically](../building-packages-programmatically/saving-a-package-programmatically.md) Describes how to save a package programmatically.</span></span>

## <a name="reference"></a><span data-ttu-id="4fc69-129">참조</span><span class="sxs-lookup"><span data-stu-id="4fc69-129">Reference</span></span>
 <span data-ttu-id="4fc69-130">[Integration Services 오류 및 메시지 참조](../integration-services-error-and-message-reference.md) 미리 정의 된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 코드와 해당 심볼 이름 및 설명을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-130">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4fc69-131">관련 단원</span><span class="sxs-lookup"><span data-stu-id="4fc69-131">Related Sections</span></span>
 <span data-ttu-id="4fc69-132">[스크립팅을 사용 하 여 패키지 확장](../extending-packages-scripting/extending-packages-with-scripting.md) 스크립트 태스크를 사용 하 여 제어 흐름을 확장 하는 방법 및 스크립트 구성 요소를 사용 하 여 데이터 흐름을 확장 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-132">[Extending Packages with Scripting](../extending-packages-scripting/extending-packages-with-scripting.md) Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>

 <span data-ttu-id="4fc69-133">[사용자 지정 개체를 사용 하 여 패키지 확장](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) 여러 패키지에서 사용할 프로그램 사용자 지정 태스크, 데이터 흐름 구성 요소 및 기타 패키지 개체를 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-133">[Extending Packages with Custom Objects](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>

 <span data-ttu-id="4fc69-134">[프로그래밍 방식으로 패키지 실행 및 관리](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) 패키지 및 패키지가 저장 된 폴더를 열거 하 고 실행 하 고 관리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc69-134">[Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Discusses how to enumerate, run, and manage packages and the folders in which they are stored.</span></span>

## <a name="external-resources"></a><span data-ttu-id="4fc69-135">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="4fc69-135">External Resources</span></span>

-   <span data-ttu-id="4fc69-136">[www.codeplex.com/MSFTISProdSamples](www.codeplex.com/MSFTISProdSamples) 의 CodePlex 예제 - [Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="4fc69-136">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>

-   <span data-ttu-id="4fc69-137">blogs.msdn.com의 블로그 항목 - [사용자 지정 확장 프로그램 성능 프로파일링](https://go.microsoft.com/fwlink/?LinkId=238831)</span><span class="sxs-lookup"><span data-stu-id="4fc69-137">Blog entry, [Performance profiling your custom extensions](https://go.microsoft.com/fwlink/?LinkId=238831), on blogs.msdn.com.</span></span>

<span data-ttu-id="4fc69-138">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4fc69-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4fc69-139">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4fc69-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4fc69-140">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4fc69-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4fc69-141">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4fc69-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fc69-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fc69-142">See Also</span></span>
 [<span data-ttu-id="4fc69-143">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="4fc69-143">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)


