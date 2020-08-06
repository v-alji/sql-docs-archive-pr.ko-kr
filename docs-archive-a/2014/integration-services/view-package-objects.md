---
title: 패키지 개체 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652895"
---
# <a name="view-package-objects"></a><span data-ttu-id="2c86c-102">패키지 개체 보기</span><span class="sxs-lookup"><span data-stu-id="2c86c-102">View Package Objects</span></span>
  <span data-ttu-id="2c86c-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **패키지 탐색기** 탭은 패키지에 대한 탐색기 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-103">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the **Package Explorer** tab provides an explorer view of the package.</span></span> <span data-ttu-id="2c86c-104">이 뷰에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 아키텍처의 컨테이너 계층이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-104">The view reflects the container hierarchy of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] architecture.</span></span> <span data-ttu-id="2c86c-105">패키지 컨테이너는 최상위 계층에 있으며, 패키지를 확장하면 패키지에 있는 연결, 실행 개체, 이벤트 처리기, 로그 공급자, 선행 제약 조건 및 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-105">The package container is at the top of the hierarchy, and you expand the package to view the connections, executables, event handlers, log providers, precedence constraints, and variables in the package.</span></span>

 <span data-ttu-id="2c86c-106">패키지의 컨테이너 및 태스크인 실행 개체에는 이벤트 처리기, 선행 제약 조건 및 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-106">The executables, which are the containers and tasks in the package, can include event handlers, precedence constraints, and variables.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="2c86c-107">는 컨테이너가 중첩된 계층을 지원하며, For 루프, Foreach 루프 및 시퀀스 컨테이너에는 다른 실행 개체가 포함될 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="2c86c-107">supports a nested hierarchy of containers, and the For Loop, Foreach Loop, and Sequence containers can include other executables.</span></span>

 <span data-ttu-id="2c86c-108">패키지에 데이터 흐름이 포함된 경우 **패키지 탐색기** 에는 데이터 흐름 태스크가 나열되며 데이터 흐름 구성 요소가 나열된 **구성 요소** 폴더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-108">If a package includes a data flow, the **Package Explorer** lists the Data Flow task and includes a **Components** folder that lists the data flow components.</span></span>

 <span data-ttu-id="2c86c-109">**패키지 탐색기** 탭에서는 패키지의 개체를 삭제하고 **속성** 창을 사용하여 개체 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-109">From the **Package Explorer** tab, you can delete objects in a package and access the **Properties** window to view object properties.</span></span>

 <span data-ttu-id="2c86c-110">다음 다이어그램에서는 예제 패키지의 트리 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c86c-110">The following diagram shows a tree view of a simple package.</span></span>

 <span data-ttu-id="2c86c-111">![패키지 탐색기 탭의 스크린샷](media/packageexplorer.gif "패키지 탐색기 탭의 스크린샷")</span><span class="sxs-lookup"><span data-stu-id="2c86c-111">![Screenshot of the Package Explorer tab](media/packageexplorer.gif "Screenshot of the Package Explorer tab")</span></span>

### <a name="to-view-package-content"></a><span data-ttu-id="2c86c-112">패키지 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="2c86c-112">To view package content</span></span>

-   [<span data-ttu-id="2c86c-113">패키지 탐색기에서 패키지 개체 보기</span><span class="sxs-lookup"><span data-stu-id="2c86c-113">View Package Objects in Package Explorer</span></span>](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a><span data-ttu-id="2c86c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c86c-114">See Also</span></span>
 <span data-ttu-id="2c86c-115">[Integration Services 태스크](control-flow/integration-services-tasks.md) [Integration Services 컨테이너](control-flow/integration-services-containers.md) [선행 제약 조건](control-flow/precedence-constraints.md) [Integration Services &#40;](integration-services-ssis-variables.md) ssis&#41; [이벤트 처리기](integration-services-ssis-event-handlers.md) Integration Services ssis &#40;[로깅](performance/integration-services-ssis-logging.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="2c86c-115">[Integration Services Tasks](control-flow/integration-services-tasks.md) [Integration Services Containers](control-flow/integration-services-containers.md) [Precedence Constraints](control-flow/precedence-constraints.md) [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md)</span></span>


