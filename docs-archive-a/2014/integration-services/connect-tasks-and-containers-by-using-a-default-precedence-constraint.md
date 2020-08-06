---
title: 기본 선행 제약 조건을 사용 하 여 태스크 및 컨테이너 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 00207172babdb41b1030e77e71a2c8bc3b99799d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738613"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a><span data-ttu-id="5fed9-102">기본 선행 제약 조건을 사용하여 태스크 및 컨테이너 연결</span><span class="sxs-lookup"><span data-stu-id="5fed9-102">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>
  <span data-ttu-id="5fed9-103">선행 제약 조건은 두 실행 개체를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-103">Precedence constraints connect two executables.</span></span> <span data-ttu-id="5fed9-104">실행 개체는 임의의 태스크, For 루프, Foreach 루프 또는 시퀀스 컨테이너일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-104">An executable can be any task or a For Loop, Foreach Loop, or Sequence container.</span></span> <span data-ttu-id="5fed9-105">이 절차에서는 선행 제약 조건에 대한 기본 동작을 설정하는 방법과 기본 선행 제약 조건을 사용하여 실행 개체를 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-105">This procedure describes how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints.</span></span>  
  
## <a name="creating-default-precedence-constraints"></a><span data-ttu-id="5fed9-106">기본 선행 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="5fed9-106">Creating Default Precedence Constraints</span></span>  
 <span data-ttu-id="5fed9-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 처음 사용할 때 선행 제약 조건의 기본값은 `Success`입니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-107">When you first use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the default value of a precedence constraint is `Success`.</span></span> <span data-ttu-id="5fed9-108">다음 단계에 따라 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 구성하고 선행 제약 조건에 대해 다른 기본값을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fed9-108">Follow these steps to configure [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to use a different default value for precedence constraints.</span></span>  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a><span data-ttu-id="5fed9-109">선행 제약 조건에 대한 기본값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="5fed9-109">To set the default value for precedence constraints</span></span>  
  
1.  <span data-ttu-id="5fed9-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-110">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="5fed9-111">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-111">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="5fed9-112">**옵션** 대화 상자에서 **비즈니스 인텔리전스 디자이너** 를 확장한 후 **Integration Services 디자이너**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-112">In the **Options** dialog box, expand **Business Intelligence Designers,** and then expand **Integration Services Designers**.</span></span>  
  
4.  <span data-ttu-id="5fed9-113">**제어 흐름 자동 연결** 을 클릭하고 **기본적으로 선택한 셰이프에 새 셰이프 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-113">Click **Control Flow Auto Connect** and select **Connect a new shape to the selected shape by default**.</span></span>  
  
5.  <span data-ttu-id="5fed9-114">드롭다운 목록에서 **새 셰이프에 Failure 제약 조건 사용** 또는 **새 셰이프에 Completion 제약 조건 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-114">In the drop-down list, choose either **Use a Failure constraint for the new shape** or **Use a Completion constraint for the new shape**.</span></span>  
  
6.  <span data-ttu-id="5fed9-115">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-115">Click **OK**.</span></span>  
  
#### <a name="to-create-a-default-precedence-constraint"></a><span data-ttu-id="5fed9-116">기본 선행 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="5fed9-116">To create a default precedence constraint</span></span>  
  
1.  <span data-ttu-id="5fed9-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="5fed9-118">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="5fed9-119">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-119">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="5fed9-120">**제어 흐름** 탭의 디자인 화면에서 태스크 또는 컨테이너를 클릭하고 선행 제약 조건을 적용하려는 실행 개체에 해당 연결선을 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-120">On the design surface of the **Control Flow** tab, click the task or container and drag its connector to the executable to which you want the precedence constraint to apply.</span></span>  
  
5.  <span data-ttu-id="5fed9-121">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fed9-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fed9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fed9-122">See Also</span></span>  
 <span data-ttu-id="5fed9-123">[선행 제약 조건](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="5fed9-123">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="5fed9-124">[바로 가기 메뉴를 사용 하 여 선행 제약 조건 값 설정](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="5fed9-124">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="5fed9-125">[선행 제약 조건의 속성 설정](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="5fed9-125">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="5fed9-126">선행 제약 조건에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="5fed9-126">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
