---
title: 선행 제약 조건 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6853d1974f4276361d60e1d73b34c72a366a7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648422"
---
# <a name="precedence-constraint-editor"></a><span data-ttu-id="d1be9-102">선행 제약 조건 편집기</span><span class="sxs-lookup"><span data-stu-id="d1be9-102">Precedence Constraint Editor</span></span>
  <span data-ttu-id="d1be9-103">**선행 제약 조건 편집기** 대화 상자를 사용하여 선행 제약 조건을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-103">Use the **Precedence Constraint Editor** dialog box to configure precedence constraints.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1be9-104">옵션</span><span class="sxs-lookup"><span data-stu-id="d1be9-104">Options</span></span>  
 <span data-ttu-id="d1be9-105">**평가 작업**</span><span class="sxs-lookup"><span data-stu-id="d1be9-105">**Evaluation operation**</span></span>  
 <span data-ttu-id="d1be9-106">선행 제약 조건에서 사용하는 평가 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-106">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="d1be9-107">사용할 수 있는 작업에는 **제약 조건**, **식**, **식 및 제약 조건**, **식 또는 제약 조건**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-107">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
 <span data-ttu-id="d1be9-108">**값**</span><span class="sxs-lookup"><span data-stu-id="d1be9-108">**Value**</span></span>  
 <span data-ttu-id="d1be9-109">제약 조건 값을 지정합니다. **성공**, **실패** 또는 **완료**와 같은 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-109">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1be9-110"> 선행 제약 조건 줄은 **성공**인 경우 녹색으로 표시되고 **실패**인 경우 강조 표시되고 **완료**인 경우 파란색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-110">The precedence constraint line is green for **Success**, highlighted for **Failure**, and blue for **Completion**.</span></span>  
  
 <span data-ttu-id="d1be9-111">**식**</span><span class="sxs-lookup"><span data-stu-id="d1be9-111">**Expression**</span></span>  
 <span data-ttu-id="d1be9-112">**식**, **식 및 제약 조건**또는 **식 또는 제약 조건**작업을 사용하는 경우 식을 입력하거나 식 작성기를 실행하여 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-112">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression or launch the Expression Builder to create the expression.</span></span> <span data-ttu-id="d1be9-113">식은 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-113">The expression must evaluate to a Boolean.</span></span>  
  
 <span data-ttu-id="d1be9-114">**Test**</span><span class="sxs-lookup"><span data-stu-id="d1be9-114">**Test**</span></span>  
 <span data-ttu-id="d1be9-115">식의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-115">Validate the expression.</span></span>  
  
 <span data-ttu-id="d1be9-116">**논리적 AND**</span><span class="sxs-lookup"><span data-stu-id="d1be9-116">**Logical AND**</span></span>  
 <span data-ttu-id="d1be9-117">동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-117">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="d1be9-118">모든 제약 조건이 `True`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-118">All constraints must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1be9-119">이 유형의 선행 제약 조건은 녹색 실선으로 표시되거나 강조 표시되거나 파란색 실선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-119">This type of precedence constraint appears as a solid green, highlighted or blue line.</span></span>  
  
 <span data-ttu-id="d1be9-120">**논리적 OR**</span><span class="sxs-lookup"><span data-stu-id="d1be9-120">**Logical OR**</span></span>  
 <span data-ttu-id="d1be9-121">동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-121">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="d1be9-122">적어도 하나의 제약 조건이 `True`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-122">At least one constraint must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1be9-123">이 유형의 선행 제약 조건은 녹색 점선으로 표시되거나 강조 표시되거나 파란색 점선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1be9-123">This type of precedence constraint appears as a dotted green, highlighted, or blue line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1be9-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1be9-124">See Also</span></span>  
 <span data-ttu-id="d1be9-125">[선행 제약 조건](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="d1be9-125">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="d1be9-126">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d1be9-126">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="d1be9-127">[Integration Services 컨테이너](control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="d1be9-127">[Integration Services Containers](control-flow/integration-services-containers.md) </span></span>  
 [<span data-ttu-id="d1be9-128">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="d1be9-128">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
