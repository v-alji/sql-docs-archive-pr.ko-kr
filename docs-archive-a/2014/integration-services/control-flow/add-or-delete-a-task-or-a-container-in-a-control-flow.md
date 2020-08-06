---
title: 제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8338a4143358d732a974287e587f482dc5c36a22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651855"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a><span data-ttu-id="eaf07-102">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="eaf07-102">Add or Delete a Task or a Container in a Control Flow</span></span>
  <span data-ttu-id="eaf07-103">제어 흐름 디자이너에서 작업 중일 때 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 도구 상자에는 패키지의 제어 흐름을 작성하기 위해 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공하는 태스크가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-103">When you are working in the control flow designer, the Toolbox in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists the tasks that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides for building control flow in a package.</span></span> <span data-ttu-id="eaf07-104">도구 상자에 대한 자세한 내용은 [SSIS Toolbox](../ssis-toolbox.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf07-104">For more information about the Toolbox, see [SSIS Toolbox](../ssis-toolbox.md).</span></span>  
  
 <span data-ttu-id="eaf07-105">패키지에는 동일 태스크에 대한 여러 인스턴스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-105">A package can include multiple instances of the same task.</span></span> <span data-ttu-id="eaf07-106">태스크에 대한 각 인스턴스는 패키지에서 고유하게 식별되며 각 인스턴스를 서로 다르게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-106">Each instance of a task is uniquely identified in the package, and you can configure each instance differently.</span></span>  
  
 <span data-ttu-id="eaf07-107">태스크를 삭제하면 이 태스크를 제어 흐름의 다른 태스크 및 컨테이너에 연결하는 선행 제약 조건도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-107">If you delete a task, the precedence constraints that connect the task to other tasks and containers in the control flow are also deleted.</span></span>  
  
 <span data-ttu-id="eaf07-108">다음 절차에서는 패키지의 제어 흐름에서 태스크 또는 컨테이너를 추가하거나 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-108">The following procedures describe how to add or delete a task or container in the control flow of a package.</span></span>  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a><span data-ttu-id="eaf07-109">제어 흐름에 태스크 또는 컨테이너를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="eaf07-109">To add a task or a container to a control flow</span></span>  
  
1.  <span data-ttu-id="eaf07-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="eaf07-111">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="eaf07-112">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="eaf07-113">**도구 상자**를 열려면 **보기** 메뉴에서 **도구 상자** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-113">To open the **Toolbox**, click **Toolbox** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="eaf07-114">**제어 흐름 항목** 및 **유지 관리 계획 태스크**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-114">Expand **Control Flow Items** and **Maintenance Tasks**.</span></span>  
  
6.  <span data-ttu-id="eaf07-115">**도구 상자** 에서 태스크 및 컨테이너를 **제어 흐름** 탭의 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-115">Drag tasks and containers from the **Toolbox** to the design surface of the **Control Flow** tab.</span></span>  
  
7.  <span data-ttu-id="eaf07-116">패키지 제어 흐름 내의 태스크 또는 컨테이너에서 연결선을 제어 흐름 내의 다른 구성 요소로 끌어와서 서로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-116">Connect a task or container within the package control flow by dragging its connector to another component in the control flow.</span></span>  
  
8.  <span data-ttu-id="eaf07-117">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-117">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a><span data-ttu-id="eaf07-118">제어 흐름에서 태스크 또는 컨테이너를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="eaf07-118">To delete a task or a container from a control flow</span></span>  
  
1.  <span data-ttu-id="eaf07-119">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="eaf07-120">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-120">In Solution Explorer, double-click the package to open it.</span></span> <span data-ttu-id="eaf07-121">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="eaf07-122">**제어 흐름** 탭을 클릭하고 제거하려는 태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-122">Click the **Control Flow** tab, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
    -   <span data-ttu-id="eaf07-123">**패키지 탐색기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-123">Open **Package Explorer**.</span></span> <span data-ttu-id="eaf07-124">**실행 파일** 폴더에서 제거하려는 태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-124">From the **Executables** folder, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="eaf07-125">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf07-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf07-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eaf07-126">See Also</span></span>  
 <span data-ttu-id="eaf07-127">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="eaf07-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="eaf07-128">[Integration Services 컨테이너](integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="eaf07-128">[Integration Services Containers](integration-services-containers.md) </span></span>  
 [<span data-ttu-id="eaf07-129">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="eaf07-129">Control Flow</span></span>](control-flow.md)  
  
  
