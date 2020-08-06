---
title: 사용자 지정 로그 공급자 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88d4f70fa9d50628b831b56f9fa22100648fce51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647164"
---
# <a name="developing-a-custom-log-provider"></a><span data-ttu-id="13e30-102">사용자 지정 로그 공급자 개발</span><span class="sxs-lookup"><span data-stu-id="13e30-102">Developing a Custom Log Provider</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="13e30-103">에는 패키지 실행 중 발생하는 이벤트를 캡처할 수 있게 해 주는 광범위한 로깅 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-103">has extensive logging capabilities that make it possible to capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="13e30-104">에는 XML, 텍스트, 데이터베이스, Windows 이벤트 로그 등의 형식으로 로그를 만들고 저장하는 데 사용할 수 있는 다양한 로그 공급자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-104">includes a variety of log providers that enable logs to be created and stored in formats such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="13e30-105">제공된 로그 공급자 및 출력 형식이 개발자의 요구 사항을 완전하게 충족시키지 못할 경우 사용자 지정 로그 공급자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-105">If the log providers and the output formats that are provided do not entirely meet your requirements, you can create a custom log provider.</span></span>

 <span data-ttu-id="13e30-106">사용자 지정 로그 공급자를 만들려면 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 기본 클래스에서 상속되는 클래스를 만들고 새 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 특성을 적용한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 속성 및 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 메서드를 포함하여 기본 클래스의 중요한 메서드와 속성을 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-106">To create a custom log provider, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="13e30-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="13e30-107">In This Section</span></span>
 <span data-ttu-id="13e30-108">이 섹션에서는 사용자 지정 로그 공급자를 만들고 구성하고 코딩하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-108">This section describes how to create, configure, and code a custom log provider.</span></span>

 <span data-ttu-id="13e30-109">[사용자 지정 로그 공급자 만들기](creating-a-custom-log-provider.md) 사용자 지정 로그 공급자 프로젝트에 대 한 클래스를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-109">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) Describes how to create the classes for a custom log provider project.</span></span>

 <span data-ttu-id="13e30-110">[사용자 지정 로그 공급자 코딩](coding-a-custom-log-provider.md) 기본 클래스의 메서드 및 속성을 재정의 하 여 사용자 지정 로그 공급자를 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-110">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) Describes how to implement a custom log provider by overriding the methods and properties of the base class.</span></span>

 <span data-ttu-id="13e30-111">[사용자 지정 로그 공급자의 사용자 인터페이스 개발](developing-a-user-interface-for-a-custom-log-provider.md) 사용자 지정 로그 공급자에 대 한 사용자 지정 사용자 인터페이스는에서 지원 되지 않습니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="13e30-111">[Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md) Custom user interfaces for custom log providers are not supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="related-topics"></a><span data-ttu-id="13e30-112">관련 항목</span><span class="sxs-lookup"><span data-stu-id="13e30-112">Related Topics</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="13e30-113">모든 사용자 지정 개체에 대한 일반적인 정보</span><span class="sxs-lookup"><span data-stu-id="13e30-113">Information Common to all Custom Objects</span></span>
 <span data-ttu-id="13e30-114">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 모든 사용자 지정 개체 유형에 공통적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13e30-114">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="13e30-115">[Integration Services에 대 한 사용자 지정 개체 개발](../developing-custom-objects-for-integration-services.md) 에 대 한 모든 형식의 사용자 지정 개체를 구현 하는 기본 단계를 설명 합니다 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="13e30-115">[Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="13e30-116">[사용자 지정 개체 유지](../persisting-custom-objects.md) 사용자 지정 지 속성에 대해 설명 하 고 필요한 경우에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-116">[Persisting Custom Objects](../persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="13e30-117">[사용자 지정 개체 빌드, 배포 및 디버깅](../building-deploying-and-debugging-custom-objects.md) 사용자 지정 개체를 빌드, 서명, 배포 및 디버깅 하는 기술에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-117">[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="13e30-118">기타 사용자 지정 개체에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="13e30-118">Information about Other Custom Objects</span></span>
 <span data-ttu-id="13e30-119">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 기타 사용자 지정 개체 유형에 대한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13e30-119">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="13e30-120">[사용자 지정 작업 개발](../task/developing-a-custom-task.md) 사용자 지정 태스크를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-120">[Developing a Custom Task](../task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="13e30-121">[사용자 지정 연결 관리자 개발](../connection-manager/developing-a-custom-connection-manager.md) 사용자 지정 연결 관리자를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-121">[Developing a Custom Connection Manager](../connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="13e30-122">[사용자 지정 ForEach 열거자 개발](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) 사용자 지정 열거자를 프로그래밍 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-122">[Developing a Custom ForEach Enumerator](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

 <span data-ttu-id="13e30-123">[사용자 지정 데이터 흐름 구성 요소 개발](../data-flow/developing-a-custom-data-flow-component.md) 사용자 지정 데이터 흐름 원본, 변환 및 대상을 프로그래밍 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e30-123">[Developing a Custom Data Flow Component](../data-flow/developing-a-custom-data-flow-component.md) Discusses how to program custom data flow sources, transformations, and destinations.</span></span>

<span data-ttu-id="13e30-124">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="13e30-124">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="13e30-125">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="13e30-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="13e30-126">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="13e30-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="13e30-127">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="13e30-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>


