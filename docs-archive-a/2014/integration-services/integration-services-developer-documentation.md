---
title: 개발자&#39;s 가이드 (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services, programming
- SSIS, programming
- SQL Server Integration Services, programming
- packages [Integration Services], programming
ms.assetid: 60fe148b-a7c4-4289-ae3e-2e949fc1886c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c16ec1a21cf7ebb711f6d3996eb6239ea052c83c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659523"
---
# <a name="developer39s-guide-integration-services"></a><span data-ttu-id="a096c-102">개발자&#39;s 가이드 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="a096c-102">Developer&#39;s Guide (Integration Services)</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="a096c-103">에는 완전히 다시 작성된 개체 모델이 포함되어 있으며 이러한 개체 모델은 패키지 확장 및 프로그래밍을 보다 쉽고 유연하고 강력하게 해 주는 다양한 기능을 갖도록 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-103">includes a completely rewritten object model, which has been enhanced with many features that make extending and programming packages easier, more flexible, and more powerful.</span></span> <span data-ttu-id="a096c-104">개발자는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지의 거의 모든 측면을 확장하고 프로그래밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-104">Developers can extend and program almost every aspect of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="a096c-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개발자가 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로그래밍에 사용할 수 있는 기본적인 방법은 다음 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-105">As an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] developer, there are two fundamental approaches that you can take to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming:</span></span>  
  
-   <span data-ttu-id="a096c-106">패키지에 사용자 지정 기능을 제공하기 위해 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너 내에서 사용할 수 있게 되는 구성 요소를 작성하여 패키지를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-106">You can extend packages by writing components that become available within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to provide custom functionality in a package.</span></span>  
  
-   <span data-ttu-id="a096c-107">개발자 고유의 애플리케이션에서 프로그래밍 방식으로 패키지를 만들고 구성하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-107">You can create, configure, and run packages programmatically from your own applications.</span></span>  
  
 <span data-ttu-id="a096c-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 기본 제공 구성 요소가 개발자의 요구 사항을 충족시키지 못할 경우 개발자 고유의 확장을 코딩하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-108">If you find that the built-in components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="a096c-109">이 경우 다음 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-109">In this approach, you have two discrete options:</span></span>  
  
-   <span data-ttu-id="a096c-110">단일 패키지에서 임시로 사용하려는 경우 스크립트 태스크에 코드를 작성하여 사용자 지정 태스크를 만들거나, 스크립트 구성 요소에 코드를 작성하여 사용자 지정 데이터 흐름 구성 요소를 만들 수 있습니다. 스크립트 구성 요소는 원본, 변환 또는 대상으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-110">For ad hoc use in a single package, you can create a custom task by writing code in the Script task, or a custom data flow component by writing code in the Script component, which you can configure as a source, transformation, or destination.</span></span> <span data-ttu-id="a096c-111">이러한 강력한 래퍼는 인프라 코드를 자동으로 작성하므로 개발자가 사용자 지정 기능을 개발하는 데만 집중할 수 있게 해 주지만 다른 항목에서 쉽게 재사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-111">These powerful wrappers write the infrastructure code for you and let you focus exclusively on developing your custom functionality; however, they are not easily reusable elsewhere.</span></span>  
  
-   <span data-ttu-id="a096c-112">여러 패키지에서 사용하려는 경우 연결 관리자, 태스크, 열거자, 로그 공급자 및 데이터 흐름 구성 요소와 같은 사용자 지정 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 확장을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-112">For use in multiple packages, you can create custom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] extensions such as connection managers, tasks, enumerators, log providers, and data flow components.</span></span> <span data-ttu-id="a096c-113">관리되는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에는 사용자 지정 확장을 개발하기 위한 시작 지점을 제공하며 이 작업을 이전보다 쉽게 해 주는 기본 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-113">The managed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model contains base classes that provide a starting point and make developing custom extensions easier than ever.</span></span>  
  
 <span data-ttu-id="a096c-114">패키지를 동적으로 만들거나 개발 환경 외부에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리 및 실행하려는 경우 패키지를 프로그래밍 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-114">If you want to create packages dynamically, or to manage and run [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="a096c-115">기존 패키지를 로드한 다음 수정하여 실행할 수도 있고 프로그래밍 방식으로 완전히 새로운 패키지를 만들어 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-115">You can load, modify, and run existing packages, or you can create and run entirely new packages programmatically.</span></span> <span data-ttu-id="a096c-116">이 경우 다음 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-116">In this approach, you have a continuous range of options:</span></span>  
  
-   <span data-ttu-id="a096c-117">기존 패키지를 로드하고 수정하지 않은 채로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-117">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="a096c-118">기존 패키지를 로드하고 다시 구성(예를 들어 다른 데이터 원본을 지정)한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-118">Load an existing package, reconfigure it (for example, specify a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="a096c-119">새 패키지를 만들고, 개체별 및 속성별로 변경 작업을 수행하여 구성 요소를 추가 및 구성하고, 새 패키지를 저장한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-119">Create a new package, add and configure components, making changes object by object and property by property, save it, and then run it.</span></span>  
  
 <span data-ttu-id="a096c-120">이 섹션에서는 이러한 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로그래밍 방법에 대해 설명하고 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-120">These approaches to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming are described in this section and demonstrated with examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a096c-121">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a096c-121">In This Section</span></span>  
 [<span data-ttu-id="a096c-122">Integration Services 프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="a096c-122">Integration Services Programming Overview</span></span>](integration-services-programming-overview.md)  
 <span data-ttu-id="a096c-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개발 과정에서 제어 흐름과 데이터 흐름이 하는 역할을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-123">Describes the roles of control flow and data flow in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] development.</span></span>  
  
 [<span data-ttu-id="a096c-124">동기 및 비동기 변환 이해</span><span class="sxs-lookup"><span data-stu-id="a096c-124">Understanding Synchronous and Asynchronous Transformations</span></span>](understanding-synchronous-and-asynchronous-transformations.md)  
 <span data-ttu-id="a096c-125">동기 출력과 비동기 출력 간의 중요한 차이를 설명하고 데이터 흐름에서 이러한 출력을 사용하는 구성 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-125">Describes the important distinction between synchronous and asynchronous outputs and the components that use them in the data flow.</span></span>  
  
 [<span data-ttu-id="a096c-126">프로그래밍 방식으로 연결 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="a096c-126">Working with Connection Managers Programmatically</span></span>](working-with-connection-managers-programmatically.md)  
 <span data-ttu-id="a096c-127">관리 코드에서 사용할 수 있는 연결 관리자 및 코드에서 `AcquireConnection` 메서드를 호출할 때 연결 관리자에서 반환하는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-127">Lists the connection managers that you can use from managed code, and the values that the connection managers return when the code calls the `AcquireConnection` method.</span></span>  
  
 [<span data-ttu-id="a096c-128">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="a096c-128">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="a096c-129">스크립트 태스크를 사용하여 제어 흐름을 확장하는 방법이나 스크립트 구성 요소를 사용하여 데이터 흐름을 확장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-129">Describes how to extend the control flow by using the Script task, or the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="a096c-130">사용자 지정 개체를 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="a096c-130">Extending Packages with Custom Objects</span></span>](extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="a096c-131">여러 패키지에서 사용할 사용자 지정 태스크, 데이터 흐름 구성 요소 및 기타 패키지 개체를 만들고 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-131">Describes how to create and program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="a096c-132">프로그래밍 방식으로 패키지 빌드</span><span class="sxs-lookup"><span data-stu-id="a096c-132">Building Packages Programmatically</span></span>](building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="a096c-133">프로그래밍 방식으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 만들고 구성 및 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-133">Describes how to create, configure, and save [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
 [<span data-ttu-id="a096c-134">프로그래밍 방식으로 패키지 실행 및 관리</span><span class="sxs-lookup"><span data-stu-id="a096c-134">Running and Managing Packages Programmatically</span></span>](run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 <span data-ttu-id="a096c-135">프로그래밍 방식으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 열거, 실행 및 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-135">Describes how to enumerate, run, and manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a096c-136">참조</span><span class="sxs-lookup"><span data-stu-id="a096c-136">Reference</span></span>  
 [<span data-ttu-id="a096c-137">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="a096c-137">Integration Services Error and Message Reference</span></span>](integration-services-error-and-message-reference.md)  
 <span data-ttu-id="a096c-138">미리 정의된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 오류 코드와 해당 심볼 이름 및 설명을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-138">Lists the predefined [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error codes, together with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a096c-139">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="a096c-139">Related Sections</span></span>  
 [<span data-ttu-id="a096c-140">패키지 배포 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="a096c-140">Troubleshooting Tools for Package Development</span></span>](troubleshooting/troubleshooting-tools-for-package-development.md)  
 <span data-ttu-id="a096c-141">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 개발 과정의 패키지 문제 해결을 위해 제공하는 기능 및 도구에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a096c-141">Describes the features and tools that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides for troubleshooting packages during development.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="a096c-142">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="a096c-142">External Resources</span></span>  
  
-   <span data-ttu-id="a096c-143">www.codeplex.com/MSFTISProdSamples 의 CodePlex 예제 - [Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="a096c-143">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a096c-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a096c-144">See Also</span></span>  
 [<span data-ttu-id="a096c-145">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="a096c-145">SQL Server Integration Services</span></span>](sql-server-integration-services.md)  
  
  
