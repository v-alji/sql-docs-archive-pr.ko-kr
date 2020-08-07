---
title: 선행 제약 조건에 식 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a997efa448a8381cc8251cd4cbf69dc59f8968e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732732"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a><span data-ttu-id="c3fcb-102">선행 제약 조건에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="c3fcb-102">Use an Expression in a Precedence Constraint</span></span>
  <span data-ttu-id="c3fcb-103">이 절차에서는 **선행 제약 조건 편집기** 대화 상자를 사용하여 선행 제약 조건에 식을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-103">This procedure describes how to add an expression to a precedence constraint by using the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="c3fcb-104">선행 제약 조건에 식을 추가하려면 패키지에 태스크 또는 컨테이너와 같은 실행 개체가 적어도 두 개 이상 포함되어야 하며 선행 제약 조건에 의해 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-104">Before you can add an expression to a precedence constraint, the package must include at least two executables, either tasks or containers, and they must be connected by a precedence constraint.</span></span>  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a><span data-ttu-id="c3fcb-105">선행 제약 조건에 식을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c3fcb-105">To add an expression to a precedence constraint</span></span>  
  
1.  <span data-ttu-id="c3fcb-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c3fcb-107">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c3fcb-108">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="c3fcb-109">**제어 흐름** 탭의 디자인 화면에서 선행 제약 조건을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-109">On the design surface of the **Control Flow** tab, double-click the precedence constraint.</span></span> <span data-ttu-id="c3fcb-110">**선행 제약 조건 편집기** 가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-110">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="c3fcb-111">**평가 작업**목록에서 **식**, **식 및 제약 조건** 또는 **식 또는 제약 조건** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-111">Select **Expression**, **Expression and Constraint**, or **Expression or Constraint** in the **Evaluation operation** list.</span></span>  
  
6.  <span data-ttu-id="c3fcb-112">**실행** 텍스트 상자에 표현식을 입력하거나 Expression Builder를 실행하여 실행을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-112">Type an expression in the **Expression** text box or launch the Expression Builder to create an expression.</span></span>  
  
7.  <span data-ttu-id="c3fcb-113">식 구문의 유효성을 검사하려면 **테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-113">To validate the expression syntax, click **Test**.</span></span>  
  
8.  <span data-ttu-id="c3fcb-114">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3fcb-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fcb-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3fcb-115">See Also</span></span>  
 <span data-ttu-id="c3fcb-116">[선행 제약 조건](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="c3fcb-116">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="c3fcb-117">[기본 선행 제약 조건을 사용 하 여 태스크 및 컨테이너 연결](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="c3fcb-117">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="c3fcb-118">[바로 가기 메뉴를 사용 하 여 선행 제약 조건 값 설정](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="c3fcb-118">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="c3fcb-119">[선행 제약 조건의 속성 설정](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="c3fcb-119">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="c3fcb-120">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="c3fcb-120">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
