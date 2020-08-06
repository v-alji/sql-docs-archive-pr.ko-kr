---
title: 여러 선행 제약 조건 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16fefbbf886818989131710876564fc9e147a56a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651093"
---
# <a name="multiple-precedence-constraints"></a><span data-ttu-id="4d3e8-102">여러 선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="4d3e8-102">Multiple Precedence Constraints</span></span>
  <span data-ttu-id="4d3e8-103">선행 제약 조건은 두 개의 태스크, 두 개의 컨테이너 또는 각 태스크와 컨테이너를 하나씩 선택하여 두 개의 실행 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-103">A precedence constraint connects two executables: two tasks, two containers, or one of each.</span></span> <span data-ttu-id="4d3e8-104">선행 제약 조건을 선행 실행 개체 및 제약 조건이 지정된 실행 개체라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-104">They are known as the precedence executable and the constrained executable.</span></span> <span data-ttu-id="4d3e8-105">제약 조건이 지정된 실행 개체에는 여러 선행 제약 조건이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-105">A constrained executable can have multiple precedence constraints.</span></span> <span data-ttu-id="4d3e8-106">자세한 내용은 [Precedence Constraints](control-flow/precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-106">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="4d3e8-107">제약 조건을 그룹화하여 복잡한 제약 조건 시나리오를 조합하면 패키지에 복잡한 제어 흐름을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-107">Assembling complex constraint scenarios by grouping constraints enables you to implement complex control flow in packages.</span></span> <span data-ttu-id="4d3e8-108">예를 들어 다음 그림에서 태스크 D는 `Success` 제약 조건에 의해 태스크 A에 연결되며 태스크 D는 다시 `Failure` 제약 조건에 의해 태스크 B에 연결되고, 태스크 D는 `Success` 제약 조건에 의해 태스크 C에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-108">For example, in the following illustration, Task D is linked to Task A by a `Success` constraint, Task D is linked to Task B by a `Failure` constraint, and Task D is linked to Task C by a `Success` constraint.</span></span> <span data-ttu-id="4d3e8-109">태스크 D와 태스크 A 사이의 선행 제약 조건, 태스크 D와 태스크 B 사이의 선행 제약 조건 및 태스크 D와 태스크 C 사이의 선행 제약 조건은 논리적 *AND* 관계에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-109">The precedence constraints between Task D and Task A, between Task D and Task B, and between Task D and Task C participate in a logical *and* relationship.</span></span> <span data-ttu-id="4d3e8-110">따라서 태스크 D를 실행하려면 태스크 A와 태스크 C는 성공적으로 실행되어야 하고 태스크 B는 실패해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-110">Therefore, for Task D to run, Task A must run successfully, Task B must fail, and Task C must run successfully.</span></span>  
  
 <span data-ttu-id="4d3e8-111">![선행 제약 조건으로 연결된 태스크](media/precedenceconstraints.gif "선행 제약 조건으로 연결된 태스크")</span><span class="sxs-lookup"><span data-stu-id="4d3e8-111">![Tasks linked by precedence constraints](media/precedenceconstraints.gif "Tasks linked by precedence constraints")</span></span>  
  
## <a name="logicaland-property"></a><span data-ttu-id="4d3e8-112">LogicalAnd 속성</span><span class="sxs-lookup"><span data-stu-id="4d3e8-112">LogicalAnd Property</span></span>  
 <span data-ttu-id="4d3e8-113">태스크 또는 컨테이너에 여러 제약 조건이 있는 경우 `LogicalAnd` 속성은 선행 제약 조건이 그 자체로만 평가되는지 또는 다른 제약 조건과 함께 평가되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-113">If a task or a container has multiple constraints, the `LogicalAnd` property specifies whether a precedence constraint is evaluated singly or in concert with other constraints.</span></span>  
  
 <span data-ttu-id="4d3e8-114">`LogicalAnd`디자이너에서 **선행 제약 조건 편집기** [!INCLUDE[ssIS](../includes/ssis-md.md)] 를 사용 하거나에서 제공 하는 속성 창을 사용 하 여 속성을 설정할 수 있습니다 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d3e8-114">You can set the `LogicalAnd` property using the **Precedence Constraint Editor** in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, or in the Properties window that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4d3e8-115">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4d3e8-115">Related Tasks</span></span>  
 [<span data-ttu-id="4d3e8-116">선행 제약 조건의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="4d3e8-116">Set the Properties of a Precedence Constraint</span></span>](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
