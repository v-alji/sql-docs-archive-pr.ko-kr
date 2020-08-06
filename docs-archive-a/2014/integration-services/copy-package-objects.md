---
title: 패키지 개체 복사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3219f0023c9a28ed270adeb6fd2b795e3459c3e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648496"
---
# <a name="copy-package-objects"></a><span data-ttu-id="5ac54-102">패키지 개체 복사</span><span class="sxs-lookup"><span data-stu-id="5ac54-102">Copy Package Objects</span></span>
  <span data-ttu-id="5ac54-103">이 항목에서는 한 패키지 내에서 또는 패키지 간에 제어 흐름 항목, 데이터 흐름 항목 및 연결 관리자를 복사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-103">This topic describes how to copy control flow items, data flow items, and connection managers within a package or between packages.</span></span>  
  
### <a name="to-copy-control-and-data-flow-items"></a><span data-ttu-id="5ac54-104">제어 흐름 항목 및 데이터 흐름 항목을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="5ac54-104">To copy control and data flow items</span></span>  
  
1.  <span data-ttu-id="5ac54-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the packages that you want work with.</span></span>  
  
2.  <span data-ttu-id="5ac54-106">솔루션 탐색기에서 복사할 두 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-106">In Solution Explorer, double-click the packages that you want to copy between.</span></span>  
  
3.  <span data-ttu-id="5ac54-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 복사할 항목이 포함된 패키지의 탭을 클릭한 다음 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the tab for the package that contains the items to copy and click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="5ac54-108">복사할 제어 흐름 항목 또는 데이터 흐름 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-108">Select the control flow or data flow items to copy.</span></span> <span data-ttu-id="5ac54-109">Shift 키를 누른 채 항목을 클릭하여 한 번에 한 항목을 선택하거나 선택할 항목을 포인터로 끌어서 그룹으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-109">You can either select items one at a time by pressing the Shift key and clicking the item or select items as a group by dragging the pointer across the items you want to select.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5ac54-110">항목을 연결하는 선행 제약 조건 및 경로는 연결하는 두 항목을 선택할 때 자동으로 선택되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-110">The precedence constraints and paths that connect items are not selected automatically when you select the two items that they connect.</span></span> <span data-ttu-id="5ac54-111">순서가 지정된 워크플로, 즉 제어 흐름 또는 데이터 흐름 세그먼트를 복사하려면 선행 제약 조건 및 경로도 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-111">To copy an ordered workflow-a segment of control flow or data flow-make sure to also copy the precedence constrains and the paths.</span></span>  
  
5.  <span data-ttu-id="5ac54-112">선택한 항목을 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-112">Right-click a selected item and click **Copy**.</span></span>  
  
6.  <span data-ttu-id="5ac54-113">항목을 다른 패키지에 복사하는 경우 복사할 패키지를 클릭한 다음 항목 유형에 해당하는 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-113">If copying items to a different package, click the package that you want to copy to, and then click the appropriate tab for the item type.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5ac54-114">패키지에 한 개 이상의 데이터 흐름 태스크가 포함되지 않은 경우 데이터 흐름을 패키지에 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-114">You cannot copy a data flow to a package unless the package contains at least one Data Flow task.</span></span>  
  
7.  <span data-ttu-id="5ac54-115">마우스 오른쪽 단추를 클릭한 다음 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-115">Right-click and click **Paste**.</span></span>  
  
### <a name="to-copy-connection-managers"></a><span data-ttu-id="5ac54-116">연결 관리자를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="5ac54-116">To copy connection managers</span></span>  
  
1.  <span data-ttu-id="5ac54-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to work with.</span></span>  
  
2.  <span data-ttu-id="5ac54-118">솔루션 탐색기에서 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-118">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="5ac54-119">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-119">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
4.  <span data-ttu-id="5ac54-120">**연결 관리자** 영역에서 연결 관리자를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-120">In the **Connection Managers** area, right-click the connection manager, and then click **Copy**.</span></span> <span data-ttu-id="5ac54-121">한 번에 하나의 연결 관리자만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-121">You can copy only one connection manager at a time.</span></span>  
  
5.  <span data-ttu-id="5ac54-122">항목을 다른 패키지에 복사하는 경우 복사할 패키지를 클릭한 다음 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-122">If you are copying items to a different package, click the package that you want to copy to and then click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
6.  <span data-ttu-id="5ac54-123">**연결 관리자** 영역을 마우스 오른쪽 단추로 클릭한 다음 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac54-123">Right-click in the **Connection Managers** area and click **Paste**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac54-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ac54-124">See Also</span></span>  
 <span data-ttu-id="5ac54-125">[제어 흐름](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5ac54-125">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="5ac54-126">[데이터 흐름](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5ac54-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 <span data-ttu-id="5ac54-127">[Integration Services&#40;SSIS&#41; 연결](connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="5ac54-127">[Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="5ac54-128">프로젝트 항목 복사</span><span class="sxs-lookup"><span data-stu-id="5ac54-128">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
  
