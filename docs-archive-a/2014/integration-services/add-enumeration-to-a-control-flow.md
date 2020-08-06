---
title: 제어 흐름에 열거 추가 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59b8569880fdf1a49f5f2ca1f6841841f9790af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650244"
---
# <a name="add-enumeration-to-a-control-flow"></a><span data-ttu-id="ca9f1-102">제어 흐름에 열거 추가</span><span class="sxs-lookup"><span data-stu-id="ca9f1-102">Add Enumeration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="ca9f1-103">에는 패키지의 제어 흐름에 파일 및 개체를 열거하는 루핑 구성을 간단하게 포함시킬 수 있는 제어 흐름 요소인 Foreach 루프 컨테이너가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-103">includes the Foreach Loop container, a control flow element that makes it simple to include a looping construct that enumerates files and objects in the control flow of a package.</span></span> <span data-ttu-id="ca9f1-104">자세한 내용은 [Foreach 루프 컨테이너](control-flow/foreach-loop-container.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-104">For more information, see [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="ca9f1-105">Foreach 루프 컨테이너는 특정 기능을 제공하는 것이 아니라 반복 가능한 제어 흐름을 작성하고, 열거자 유형을 지정하고, 열거자를 구성할 수 있는 구조만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-105">The Foreach Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow, specify an enumerator type, and configure the enumerator.</span></span> <span data-ttu-id="ca9f1-106">컨테이너 기능을 제공하려면 적어도 하나 이상의 태스크를 Foreach 루프 컨테이너에 포함시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-106">To provide container functionality, you must include at least one task in the Foreach Loop container.</span></span> <span data-ttu-id="ca9f1-107">자세한 내용은 [Integration Services Tasks](control-flow/integration-services-tasks.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-107">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="ca9f1-108">Foreach 루프 컨테이너에는 여러 태스크가 포함된 제어 흐름과 다른 컨테이너가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-108">The Foreach Loop container can include a control flow with multiple tasks and other containers.</span></span> <span data-ttu-id="ca9f1-109">Foreach 루프 컨테이너에 태스크 및 컨테이너를 추가하는 방법은 패키지에 추가하는 방법과 비슷하며, 태스크 및 컨테이너를 패키지가 아닌 Foreach 루프 컨테이너로 끌어 온다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-109">Adding tasks and containers to a Foreach Loop container is similar to adding them to a package, except you drag the tasks and containers to the Foreach Loop container instead of to the package.</span></span> <span data-ttu-id="ca9f1-110">Foreach 루프 컨테이너에 두 개 이상의 태스크 또는 컨테이너가 포함된 경우 패키지에서와 같은 방식으로 선행 제약 조건을 사용하여 이를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-110">If the Foreach Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="ca9f1-111">자세한 내용은 [Precedence Constraints](control-flow/precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-111">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a><span data-ttu-id="ca9f1-112">제어 흐름에서 Foreach 루프 컨테이너를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="ca9f1-112">To implement a Foreach Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="ca9f1-113">패키지에 Foreach 루프 컨테이너를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-113">Add the Foreach Loop container to the package.</span></span> <span data-ttu-id="ca9f1-114">자세한 내용은 [제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-114">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="ca9f1-115">.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-115">.</span></span>  
  
2.  <span data-ttu-id="ca9f1-116">Foreach 루프 컨테이너에 태스크 및 컨테이너를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-116">Add tasks and containers to the Foreach Loop container.</span></span> <span data-ttu-id="ca9f1-117">자세한 내용은 [제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-117">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="ca9f1-118">.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-118">.</span></span>  
  
3.  <span data-ttu-id="ca9f1-119">선행 제약 조건을 사용하여 Foreach 루프 컨테이너에 있는 태스크 및 컨테이너를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-119">Connect tasks and containers in the Foreach Loop container using precedence constraints.</span></span> <span data-ttu-id="ca9f1-120">자세한 내용은 [기본 선행 제약 조건을 사용하여 태스크 및 컨테이너 연결](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-120">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="ca9f1-121">Foreach 루프 컨테이너를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-121">Configure the Foreach Loop container.</span></span> <span data-ttu-id="ca9f1-122">자세한 내용은 [Foreach 루프 컨테이너 구성](../../2014/integration-services/configure-a-foreach-loop-container.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca9f1-122">For more information, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9f1-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca9f1-123">See Also</span></span>  
 <span data-ttu-id="ca9f1-124">[제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ca9f1-124">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="ca9f1-125">[구성 요소 그룹화 또는 그룹 해제](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="ca9f1-125">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="ca9f1-126">[선행 제약 조건](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="ca9f1-126">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="ca9f1-127">[제어 흐름에 반복 추가](add-iteration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ca9f1-127">[Add Iteration to a Control Flow](add-iteration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="ca9f1-128">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="ca9f1-128">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
