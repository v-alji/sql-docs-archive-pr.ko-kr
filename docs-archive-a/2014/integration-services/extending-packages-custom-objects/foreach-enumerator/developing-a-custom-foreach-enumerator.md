---
title: 사용자 지정 ForEach 열거자 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3d61f98266320f63d7ee56262b7c85dfb64d39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651206"
---
# <a name="developing-a-custom-foreach-enumerator"></a><span data-ttu-id="16911-102">사용자 지정 ForEach 열거자 개발</span><span class="sxs-lookup"><span data-stu-id="16911-102">Developing a Custom ForEach Enumerator</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="16911-103">에서는 foreach 열거자를 사용하여 컬렉션의 항목을 반복하고 각 요소에 대해 동일한 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-103">uses foreach enumerators to iterate over the items in a collection and perform the same tasks for each element.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="16911-104">에는 폴더의 모든 파일, 데이터베이스의 모든 테이블 또는 패키지 변수에 저장된 목록의 모든 요소와 같이 가장 일반적으로 사용되는 컬렉션을 지원하는 다양한 foreach 열거자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16911-104">includes a variety of foreach enumerators that support the most commonly used collections, such as all the files in a folder, all the tables in a database, or all the elements of a list stored in a package variable.</span></span> <span data-ttu-id="16911-105">제공된 foreach 열거자 및 컬렉션이 개발자의 요구 사항을 완전하게 충족시키지 못할 경우에는 사용자 지정 foreach 열거자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16911-105">If the foreach enumerators and collections that are provided do not entirely meet your requirements, you can create a custom foreach enumerator.</span></span>  
  
 <span data-ttu-id="16911-106">사용자 지정 foreach 열거자를 만들려면 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 기본 클래스에서 상속되는 클래스를 만들고 새 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 특성을 적용한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 메서드를 포함하여 기본 클래스의 중요한 메서드와 속성을 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-106">To create a custom foreach enumerator, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16911-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="16911-107">In This Section</span></span>  
 <span data-ttu-id="16911-108">이 섹션에서는 사용자 지정 foreach 열거자와 해당 사용자 지정 사용자 인터페이스를 만들고 구성하고 코딩하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-108">This section describes how to create, configure, and code a custom foreach enumerator and its custom user interface.</span></span>  
  
 [<span data-ttu-id="16911-109">사용자 지정 Foreach 열거자 만들기</span><span class="sxs-lookup"><span data-stu-id="16911-109">Creating a Custom Foreach Enumerator</span></span>](creating-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="16911-110">사용자 지정 foreach 열거자 프로젝트의 클래스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-110">Describes how to create the classes for a custom foreach enumerator project.</span></span>  
  
 [<span data-ttu-id="16911-111">사용자 지정 Foreach 열거자 코딩</span><span class="sxs-lookup"><span data-stu-id="16911-111">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="16911-112">기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 foreach 열거자를 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-112">Describes how to implement a custom foreach enumerator by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="16911-113">사용자 지정 ForEach 열거자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="16911-113">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="16911-114">사용자 지정 foreach 열거자를 구성하는 데 사용되는 사용자 인터페이스 클래스 및 폼을 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-114">Describes how to implement the user interface class and the form that is used to configure the custom foreach enumerator.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="16911-115">관련 항목</span><span class="sxs-lookup"><span data-stu-id="16911-115">Related Topics</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="16911-116">모든 사용자 지정 개체에 대한 일반적인 정보</span><span class="sxs-lookup"><span data-stu-id="16911-116">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="16911-117">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 모든 사용자 지정 개체 유형에 공통적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="16911-117">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="16911-118">Integration Services용 사용자 지정 개체 개발</span><span class="sxs-lookup"><span data-stu-id="16911-118">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="16911-119">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 모든 사용자 지정 개체 유형을 구현하는 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-119">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="16911-120">사용자 지정 개체 지속</span><span class="sxs-lookup"><span data-stu-id="16911-120">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="16911-121">사용자 지정 지속성 및 해당 지속성이 필요한 경우에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-121">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="16911-122">사용자 지정 개체 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="16911-122">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="16911-123">사용자 지정 개체를 작성, 서명, 배포 및 디버깅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-123">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="16911-124">기타 사용자 지정 개체에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="16911-124">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="16911-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 만들 수 있는 기타 사용자 지정 개체 유형에 대한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="16911-125">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="16911-126">사용자 지정 태스크 개발</span><span class="sxs-lookup"><span data-stu-id="16911-126">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="16911-127">사용자 지정 태스크를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-127">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="16911-128">사용자 지정 연결 관리자 개발</span><span class="sxs-lookup"><span data-stu-id="16911-128">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="16911-129">사용자 지정 연결 관리자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-129">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="16911-130">사용자 지정 로그 공급자 개발</span><span class="sxs-lookup"><span data-stu-id="16911-130">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="16911-131">사용자 지정 로그 공급자를 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-131">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="16911-132">사용자 지정 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="16911-132">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="16911-133">사용자 지정 데이터 흐름 원본, 변환 및 대상을 프로그래밍하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16911-133">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="16911-134">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="16911-134">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="16911-135">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="16911-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="16911-136">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="16911-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="16911-137">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="16911-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
