---
title: 특정 유형의 데이터 흐름 구성 요소 개발 | Microsoft Docs
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e168c866e03bfa5fd1f32127e4bfd6e58a2e8d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736603"
---
# <a name="developing-specific-types-of-data-flow-components"></a><span data-ttu-id="6eae5-102">특정 유형의 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-102">Developing Specific Types of Data Flow Components</span></span>
  <span data-ttu-id="6eae5-103">이 섹션에서는 원본 구성 요소, 동기 출력을 사용하는 변환 구성 요소, 비동기 출력을 사용하는 변환 구성 요소 및 대상 구성 요소를 개발할 때의 세부 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-103">This section covers the specifics of developing source components, transformation components with synchronous outputs, transformation components with asynchronous outputs, and destination components.</span></span>  
  
 <span data-ttu-id="6eae5-104">구성 요소 개발에 대한 일반적인 정보는 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6eae5-104">For information about component development in general, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6eae5-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6eae5-105">In This Section</span></span>  
 [<span data-ttu-id="6eae5-106">사용자 지정 원본 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-106">Developing a Custom Source Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 <span data-ttu-id="6eae5-107">외부 데이터 원본의 데이터에 액세스하고 이 데이터를 데이터 흐름의 다운스트림 구성 요소에 제공하는 구성 요소를 개발하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-107">Contains information on developing a component that accesses data from an external data source and supplies it to downstream components in the data flow.</span></span>  
  
 [<span data-ttu-id="6eae5-108">동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-108">Developing a Custom Transformation Component with Synchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 <span data-ttu-id="6eae5-109">출력이 입력과 동기적으로 이루어지는 변환 구성 요소를 개발하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-109">Contains information on developing a transformation component whose outputs are synchronous to its inputs.</span></span> <span data-ttu-id="6eae5-110">이러한 구성 요소는 데이터를 데이터 흐름에 추가하는 것이 아니라 해당 데이터가 전달될 때 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-110">These components do not add data to the data flow, but process data as it passes through.</span></span>  
  
 [<span data-ttu-id="6eae5-111">비동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-111">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 <span data-ttu-id="6eae5-112">출력이 입력과 동기적으로 이루어지지 않는 변환 구성 요소를 개발하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-112">Contains information on developing a transformation component whose outputs are not synchronous to its inputs.</span></span> <span data-ttu-id="6eae5-113">이러한 구성 요소는 업스트림 구성 요소에서 데이터를 받고 데이터 흐름에 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-113">These components receive data from upstream components, but also add data to the dataflow.</span></span>  
  
 [<span data-ttu-id="6eae5-114">사용자 지정 대상 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-114">Developing a Custom Destination Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 <span data-ttu-id="6eae5-115">데이터 흐름의 업스트림 구성 요소에서 행을 받고 이를 외부 데이터 원본에 쓰는 구성 요소를 개발하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-115">Contains information on developing a component that receives rows from upstream components in the data flow and writes them to an external data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6eae5-116">참조</span><span class="sxs-lookup"><span data-stu-id="6eae5-116">Reference</span></span>  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 <span data-ttu-id="6eae5-117">사용자 지정 데이터 흐름 구성 요소를 만드는 데 사용되는 클래스와 인터페이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-117">Contains the classes and interfaces used to create custom data flow components.</span></span>  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 <span data-ttu-id="6eae5-118">데이터 흐름 태스크의 관리되지 않는 클래스 및 인터페이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-118">Contains the unmanaged classes and interfaces of the data flow task.</span></span> <span data-ttu-id="6eae5-119">개발자는 프로그래밍 방식으로 데이터 흐름을 작성하거나 사용자 지정 데이터 흐름 구성 요소를 만들 때 이러한 클래스 및 인터페이스와 관리되는 <xref:Microsoft.SqlServer.Dts.Pipeline> 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6eae5-119">The developer uses these, and the managed <xref:Microsoft.SqlServer.Dts.Pipeline> namespace, when building a data flow programmatically or creating custom data flow components.</span></span>  
  
<span data-ttu-id="6eae5-120">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6eae5-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6eae5-121">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6eae5-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6eae5-122">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6eae5-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6eae5-123">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6eae5-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eae5-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6eae5-124">See Also</span></span>  
 <span data-ttu-id="6eae5-125">[스크립팅 솔루션과 사용자 지정 개체 비교](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="6eae5-125">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="6eae5-126">특정 유형의 스크립트 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6eae5-126">Developing Specific Types of Script Components</span></span>](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
