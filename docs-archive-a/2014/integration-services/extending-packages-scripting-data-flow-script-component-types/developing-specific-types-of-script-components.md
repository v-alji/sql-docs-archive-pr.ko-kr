---
title: 특정 유형의 스크립트 구성 요소 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651772"
---
# <a name="developing-specific-types-of-script-components"></a><span data-ttu-id="faf1d-102">특정 유형의 스크립트 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="faf1d-102">Developing Specific Types of Script Components</span></span>
  <span data-ttu-id="faf1d-103">스크립트 구성 요소는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 원본, 변환 및 대상이 충족시키지 않는 거의 모든 요구 사항을 충족시키기 위해 패키지의 데이터 흐름에서 사용할 수 있는 구성 가능한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="faf1d-104">이 섹션에는 스크립트 구성 요소를 구성하는 네 가지 옵션을 보여 주는 스크립트 구성 요소 코드 예제가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-104">This section contains Script component code samples that demonstrate the four options for configuring the Script component:</span></span>  
  
-   <span data-ttu-id="faf1d-105">원본으로 구성</span><span class="sxs-lookup"><span data-stu-id="faf1d-105">As a source.</span></span>  
  
-   <span data-ttu-id="faf1d-106">동기 출력을 사용하는 변환으로 구성</span><span class="sxs-lookup"><span data-stu-id="faf1d-106">As a transformation with synchronous outputs.</span></span>  
  
-   <span data-ttu-id="faf1d-107">비동기 출력을 사용하는 변환으로 구성</span><span class="sxs-lookup"><span data-stu-id="faf1d-107">As a transformation with asynchronous outputs.</span></span>  
  
-   <span data-ttu-id="faf1d-108">대상으로 구성</span><span class="sxs-lookup"><span data-stu-id="faf1d-108">As a destination.</span></span>  
  
 <span data-ttu-id="faf1d-109">스크립트 구성 요소에 대한 추가 예제는 [추가 스크립트 구성 요소 예](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="faf1d-109">For additional examples of the Script component, see [Additional Script Component Examples](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="faf1d-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="faf1d-110">In This Section</span></span>  
 [<span data-ttu-id="faf1d-111">스크립트 구성 요소를 사용하여 원본 만들기</span><span class="sxs-lookup"><span data-stu-id="faf1d-111">Creating a Source with the Script Component</span></span>](creating-a-source-with-the-script-component.md)  
 <span data-ttu-id="faf1d-112">스크립트 구성 요소를 사용하여 데이터 흐름 원본을 만드는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-112">Explains and demonstrates how to create a data flow source by using the Script component.</span></span>  
  
 [<span data-ttu-id="faf1d-113">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="faf1d-113">Creating a Synchronous Transformation with the Script Component</span></span>](creating-a-synchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="faf1d-114">스크립트 구성 요소를 사용하여 동기 출력을 사용하는 데이터 흐름 변환을 만드는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-114">Explains and demonstrates how to create a data flow transformation with synchronous outputs by using the Script component.</span></span> <span data-ttu-id="faf1d-115">이러한 종류의 변환에서는 데이터 행이 구성 요소를 통해 전달될 때 현재 위치에서 해당 행을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-115">This kind of transformation modifies rows of data in place as they pass through the component.</span></span>  
  
 [<span data-ttu-id="faf1d-116">스크립트 구성 요소를 사용하여 비동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="faf1d-116">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="faf1d-117">스크립트 구성 요소를 사용하여 비동기 출력을 사용하는 데이터 흐름 변환을 만드는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-117">Explains and demonstrates how to create a data flow transformation with asynchronous outputs by using the Script component.</span></span> <span data-ttu-id="faf1d-118">이러한 종류의 변환에서는 모든 데이터 행을 읽은 후에만 계산된 집계와 같은 추가 정보를 구성 요소를 통해 전달되는 데이터에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-118">This kind of transformation has to read all rows of data before it can add more information, such as calculated aggregates, to the data that passes through the component.</span></span>  
  
 [<span data-ttu-id="faf1d-119">스크립트 구성 요소를 사용하여 대상 만들기</span><span class="sxs-lookup"><span data-stu-id="faf1d-119">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 <span data-ttu-id="faf1d-120">스크립트 구성 요소를 사용하여 데이터 흐름 대상을 만드는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf1d-120">Explains and demonstrates how to create a data flow destination by using the Script component.</span></span>  
  
<span data-ttu-id="faf1d-121">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="faf1d-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="faf1d-122">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="faf1d-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="faf1d-123">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="faf1d-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="faf1d-124">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="faf1d-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf1d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="faf1d-125">See Also</span></span>  
 <span data-ttu-id="faf1d-126">[스크립팅 솔루션과 사용자 지정 개체 비교](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="faf1d-126">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="faf1d-127">특정 유형의 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="faf1d-127">Developing Specific Types of Data Flow Components</span></span>](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
