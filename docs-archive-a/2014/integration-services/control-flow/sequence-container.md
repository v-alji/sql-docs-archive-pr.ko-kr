---
title: 시퀀스 컨테이너 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b972f923e2134363ba1b378beebebbeb1e5d6bb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652248"
---
# <a name="sequence-container"></a><span data-ttu-id="768e7-102">시퀀스 컨테이너</span><span class="sxs-lookup"><span data-stu-id="768e7-102">Sequence Container</span></span>
  <span data-ttu-id="768e7-103">시퀀스 컨테이너는 패키지 제어 흐름의 하위 집합인 제어 흐름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-103">The Sequence container defines a control flow that is a subset of the package control flow.</span></span> <span data-ttu-id="768e7-104">시퀀스 컨테이너는 패키지를 여러 개의 별도 제어 흐름으로 그룹화하며, 각 제어 흐름에는 전체 패키지 제어 흐름 내에서 실행되는 하나 이상의 태스크 및 컨테이너가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-104">Sequence containers group the package into multiple separate control flows, each containing one or more tasks and containers that run within the overall package control flow.</span></span>  
  
 <span data-ttu-id="768e7-105">시퀀스 컨테이너에는 여러 태스크 외에도 다른 컨테이너를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-105">The Sequence container can include multiple tasks in addition to other containers.</span></span> <span data-ttu-id="768e7-106">시퀀스 컨테이너에 태스크 및 컨테이너를 추가하는 방법은 패키지에 추가하는 방법과 비슷하며, 태스크 및 컨테이너를 패키지 컨테이너가 아닌 시퀀스 컨테이너로 끌어 온다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-106">Adding tasks and containers to a Sequence container is similar to adding them to a package, except you drag the tasks and containers to the Sequence container instead of to the package container.</span></span> <span data-ttu-id="768e7-107">시퀀스 컨테이너에 두 개 이상의 태스크 또는 컨테이너가 포함된 경우 패키지에서와 같은 방식으로 선행 제약 조건을 사용하여 이를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-107">If the Sequence container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="768e7-108">자세한 내용은 [Precedence Constraints](precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="768e7-108">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="768e7-109">시퀀스 컨테이너를 사용할 경우 다음과 같은 많은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-109">There are many benefits of using a Sequence container:</span></span>  
  
-   <span data-ttu-id="768e7-110">패키지 제어 흐름의 특정 하위 집합에서 패키지 디버깅을 중점적으로 처리하기 위해 태스크 그룹 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="768e7-110">Disabling groups of tasks to focus package debugging on one subset of the package control flow.</span></span>  
  
-   <span data-ttu-id="768e7-111">개별 태스크가 아닌 시퀀스 컨테이너의 속성을 설정하여 한 위치에서 여러 태스크의 속성 관리</span><span class="sxs-lookup"><span data-stu-id="768e7-111">Managing properties on multiple tasks in one location by setting properties on a Sequence container instead of on the individual tasks.</span></span>  
  
     <span data-ttu-id="768e7-112">예를 들어 시퀀스 컨테이너의 `Disable` 속성을 `True`로 설정하여 시퀀스 컨테이너의 모든 태스크와 컨테이너를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-112">For example, you can set the `Disable` property of the Sequence container to `True` to disable all the tasks and containers in the Sequence container.</span></span>  
  
-   <span data-ttu-id="768e7-113">관련 태스크 및 컨테이너 그룹에서 사용하는 변수의 범위 제공</span><span class="sxs-lookup"><span data-stu-id="768e7-113">Providing scope for variables that a group of related tasks and containers use.</span></span>  
  
-   <span data-ttu-id="768e7-114">시퀀스 컨테이너를 확장하거나 축소하여 보다 쉽게 관리할 수 있도록 많은 태스크 그룹화</span><span class="sxs-lookup"><span data-stu-id="768e7-114">Grouping many tasks so you can more easily managed them by collapsing and expanding the Sequence container.</span></span>  
  
     <span data-ttu-id="768e7-115">또한 **그룹** 상자를 사용하여 확장 및 축소되는 태스크 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-115">You can also create task groups, which expand and collapse using the **Group** box.</span></span> <span data-ttu-id="768e7-116">하지만 **그룹** 상자는 디자인 타임 기능이기 때문에 속성이나 런타임 동작이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-116">However, the **Group** box is a design-time feature that has no properties or run-time behavior.</span></span> <span data-ttu-id="768e7-117">자세한 내용은 [구성 요소 그룹화 또는 그룹 해제](../group-or-ungroup-components.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="768e7-117">For more information, see [Group or Ungroup Components](../group-or-ungroup-components.md)</span></span>  
  
-   <span data-ttu-id="768e7-118">시퀀스 컨테이너에 트랜잭션 특성을 설정하여 패키지 제어 흐름의 하위 집합에 대한 트랜잭션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-118">Set a transaction attribute on the Sequence container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="768e7-119">이러한 방식으로 보다 세부적으로 트랜잭션을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-119">In this way, you can manage transactions at a more granular level.</span></span>  
  
     <span data-ttu-id="768e7-120">예를 들어 시퀀스 컨테이너에 두 개의 관련 태스크가 포함되어 있으며 두 태스크 중 하나는 테이블의 데이터를 삭제하고 다른 태스크는 테이블에 데이터를 삽입하는 경우 삽입 동작 실패 시 삭제 동작이 롤백되도록 트랜잭션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-120">For example, if a Sequence container includes two related tasks, one task that deletes data in a table and another task that inserts data into a table, you can configure a transaction to ensure that the delete action is rolled back if the insert action fails.</span></span> <span data-ttu-id="768e7-121">자세한 내용은 [Integration Services 트랜잭션](../integration-services-transactions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="768e7-121">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-sequence-container"></a><span data-ttu-id="768e7-122">시퀀스 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="768e7-122">Configuration of the Sequence Container</span></span>  
 <span data-ttu-id="768e7-123">시퀀스 컨테이너에는 사용자 지정 사용자 인터페이스가 없으며 **의** 속성 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 창에서나 프로그래밍 방식으로만 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768e7-123">The Sequence container has no custom user interface and you can configure it only in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="768e7-124">프로그래밍 방식으로 이러한 속성을 설정하는 방법은 개발자 가이드에서 **T:Microsoft.SqlServer.Dts.Runtime.Sequence** 클래스에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="768e7-124">For information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.Sequence** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="768e7-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="768e7-125">Related Tasks</span></span>  
 <span data-ttu-id="768e7-126">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="768e7-126">For information about how to set properties of the component in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768e7-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="768e7-127">See Also</span></span>  
 <span data-ttu-id="768e7-128">[제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="768e7-128">[Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="768e7-129">[기본 선행 제약 조건을 사용하여 태스크 및 컨테이너 연결](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="768e7-129">[Connect Tasks and Containers by Using a Default Precedence Constraint](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="768e7-130">Integration Services 컨테이너</span><span class="sxs-lookup"><span data-stu-id="768e7-130">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
