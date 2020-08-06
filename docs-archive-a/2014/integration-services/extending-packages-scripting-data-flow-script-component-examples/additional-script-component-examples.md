---
title: 추가 스크립트 구성 요소 예 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 897ca075674f5c3dbaf355390fe8346580bf638a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652219"
---
# <a name="additional-script-component-examples"></a><span data-ttu-id="a1848-102">추가 스크립트 구성 요소 예</span><span class="sxs-lookup"><span data-stu-id="a1848-102">Additional Script Component Examples</span></span>
  <span data-ttu-id="a1848-103">스크립트 구성 요소는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 원본, 변환 및 대상이 충족시키지 않는 거의 모든 요구 사항을 충족시키기 위해 패키지의 데이터 흐름에서 사용할 수 있는 구성 가능한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="a1848-104">이 섹션에는 사용할 수 있는 다양한 유형의 기능을 보여 주는 스크립트 구성 요소 코드 예제가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-104">This section contains Script component code samples that demonstrate the various types of functionality that are available.</span></span>  
  
 <span data-ttu-id="a1848-105">스크립트 구성 요소를 기본 원본, 변환 또는 대상으로 구성하는 방법에 대한 샘플은 [특정 유형의 스크립트 구성 요소 개발](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1848-105">For samples that demonstrate how to configure the Script component as a basic source, transformation, or destination, see [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1848-106">여러 데이터 흐름 태스크 및 여러 패키지에서 쉽게 다시 사용할 수 있는 구성 요소를 만들려면 이 스크립트 구성 요소 예제에 있는 코드를 바탕으로 사용자 지정 데이터 흐름 구성 요소를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a1848-106">If you want to create components that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in these Script component samples as the starting point for custom data flow components.</span></span> <span data-ttu-id="a1848-107">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1848-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1848-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a1848-108">In This Section</span></span>  
 [<span data-ttu-id="a1848-109">스크립트 구성 요소의 오류 출력 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="a1848-109">Simulating an Error Output for the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 <span data-ttu-id="a1848-110">스크립트 구성 요소에서는 표준 오류 출력을 지원하지 않지만 아주 적은 양의 추가 구성 및 코딩을 통해 표준 오류 출력을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-110">The Script component does not support a standard error output, but you can simulate a standard error output with very little additional configuration and coding.</span></span>  
  
 [<span data-ttu-id="a1848-111">스크립트 구성 요소를 사용하여 오류 출력 향상</span><span class="sxs-lookup"><span data-stu-id="a1848-111">Enhancing an Error Output with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 <span data-ttu-id="a1848-112">스크립트 구성 요소를 사용하여 표준 오류 출력에 다른 정보를 추가하는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-112">Explains and demonstrates how to add additional information to a standard error output by using the Script component.</span></span>  
  
 [<span data-ttu-id="a1848-113">스크립트 구성 요소를 사용하여 ODBC 대상 만들기</span><span class="sxs-lookup"><span data-stu-id="a1848-113">Creating an ODBC Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 <span data-ttu-id="a1848-114">스크립트 구성 요소를 사용하여 ODBC 데이터 흐름 대상을 만드는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-114">Explains and demonstrates how to create an ODBC data flow destination by using the Script component.</span></span>  
  
 [<span data-ttu-id="a1848-115">스크립트 구성 요소를 사용하여 비표준 텍스트 파일 형식의 구문 분석</span><span class="sxs-lookup"><span data-stu-id="a1848-115">Parsing Non-Standard Text File Formats with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 <span data-ttu-id="a1848-116">표준이 아닌 두 개의 서로 다른 파일 형식을 대상 테이블로 구문 분석하는 방법을 설명하고 예로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1848-116">Explains and demonstrates how to parse two different non-standard text file formats into destination tables.</span></span>  
  
<span data-ttu-id="a1848-117">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a1848-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a1848-118">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a1848-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a1848-119">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a1848-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a1848-120">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="a1848-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
