---
title: 사용자 지정 연결 관리자 개발 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19c5a9066db6542742537a41a7f567d1b4b1d23d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742404"
---
# <a name="developing-a-custom-connection-manager"></a><span data-ttu-id="770c0-102">사용자 지정 연결 관리자 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-102">Developing a Custom Connection Manager</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="770c0-103">에서는 연결 관리자를 사용하여 외부 데이터 원본에 연결하는 데 필요한 정보를 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-103">uses connection managers to encapsulate the information needed to connect to an external data source.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="770c0-104">에는 엔터프라이즈 데이터베이스에서 텍스트 파일 및 Excel 워크시트에 이르기까지 가장 일반적으로 사용되는 데이터 원본에 대한 연결을 지원하는 다양한 연결 관리자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-104">includes a variety of connection managers that support connections to the most commonly used data sources, from enterprise databases to text files and Excel worksheets.</span></span> <span data-ttu-id="770c0-105">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 지원하는 연결 관리자와 외부 데이터 원본이 개발자의 요구 사항을 완전히 충족시키지 못할 경우에는 사용자 지정 연결 관리자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-105">If the connection managers and external data sources supported by [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not entirely meet your requirements, you can create a custom connection manager.</span></span>  
  
 <span data-ttu-id="770c0-106">사용자 지정 연결 관리자를 만들려면 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 기본 클래스에서 상속되는 클래스를 만들고 새 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 특성을 적용한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 속성과 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 메서드를 포함하여 기본 클래스의 중요한 메서드와 속성을 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-106">To create a custom connection manager, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="770c0-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 기본 제공된 대부분의 태스크, 원본 및 대상은 특정 유형의 기본 제공 연결 관리자와만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="770c0-108">기본 제공 태스크 및 구성 요소에 사용할 사용자 지정 연결 관리자를 개발하려면 먼저 해당 구성 요소에서 특정 유형의 연결 관리자만 사용할 수 있도록 제한하는지 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-108">Before developing a custom connection manager for use with built-in tasks and components, check whether those components restrict the list of available connection managers to those of a specific type.</span></span> <span data-ttu-id="770c0-109">솔루션에 사용자 지정 연결 관리자가 필요한 경우에는 연결 관리자와 함께 사용할 사용자 지정 태스크나 사용자 지정 원본 또는 대상을 개발해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-109">If your solution requires a custom connection manager, you might also have to develop a custom task, or a custom source or destination, for use with the connection manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="770c0-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="770c0-110">In This Section</span></span>  
 <span data-ttu-id="770c0-111">이 섹션에서는 사용자 지정 연결 관리자와 선택 사항인 연결 관리자의 사용자 지정 사용자 인터페이스를 만들고 구성하고 코딩하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-111">This section describes how to create, configure, and code a custom connection manager and its optional custom user interface.</span></span> <span data-ttu-id="770c0-112">이 섹션에 표시된 코드 조각은 SQL Server 사용자 지정 연결 관리자 예제에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-112">The code snippets shown in this section are drawn from the Sql Server Custom Connection Manager Sample.</span></span>  
  
 [<span data-ttu-id="770c0-113">사용자 지정 연결 관리자 만들기</span><span class="sxs-lookup"><span data-stu-id="770c0-113">Creating a Custom Connection Manager</span></span>](creating-a-custom-connection-manager.md)  
 <span data-ttu-id="770c0-114">사용자 지정 연결 관리자 프로젝트의 클래스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-114">Describes how to create the classes for a custom connection manager project.</span></span>  
  
 [<span data-ttu-id="770c0-115">사용자 지정 연결 관리자 코딩</span><span class="sxs-lookup"><span data-stu-id="770c0-115">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
 <span data-ttu-id="770c0-116">기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 연결 관리자를 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-116">Describes how to implement a custom connection manager by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="770c0-117">사용자 지정 연결 관리자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-117">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
 <span data-ttu-id="770c0-118">사용자 지정 연결 관리자를 구성하는 데 사용되는 사용자 인터페이스 클래스 및 폼을 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-118">Describes how to implement the user interface class and the form that is used to configure the custom connection manager.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="770c0-119">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="770c0-119">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="770c0-120">모든 사용자 지정 개체에 대한 일반적인 정보</span><span class="sxs-lookup"><span data-stu-id="770c0-120">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="770c0-121">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 모든 사용자 지정 개체 유형에 공통적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="770c0-121">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="770c0-122">Integration Services용 사용자 지정 개체 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-122">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="770c0-123">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 모든 사용자 지정 개체 유형을 구현하는 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-123">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="770c0-124">사용자 지정 개체 지속</span><span class="sxs-lookup"><span data-stu-id="770c0-124">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="770c0-125">사용자 지정 지속성 및 해당 지속성이 필요한 경우에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-125">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="770c0-126">사용자 지정 개체 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="770c0-126">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="770c0-127">사용자 지정 개체를 작성, 서명, 배포 및 디버깅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-127">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="770c0-128">기타 사용자 지정 개체에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="770c0-128">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="770c0-129">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 기타 사용자 지정 개체 유형에 대한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="770c0-129">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="770c0-130">사용자 지정 태스크 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-130">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="770c0-131">사용자 지정 태스크를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-131">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="770c0-132">사용자 지정 로그 공급자 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-132">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="770c0-133">사용자 지정 로그 공급자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-133">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="770c0-134">사용자 지정 ForEach 열거자 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-134">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="770c0-135">사용자 지정 열거자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-135">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="770c0-136">사용자 지정 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="770c0-136">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="770c0-137">사용자 지정 데이터 흐름 원본, 변환 및 대상을 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="770c0-137">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="770c0-138">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="770c0-138">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="770c0-139">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="770c0-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="770c0-140">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="770c0-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="770c0-141">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="770c0-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
