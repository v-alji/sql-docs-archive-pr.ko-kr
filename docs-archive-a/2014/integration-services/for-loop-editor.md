---
title: For 루프 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b610805808e0f392e675ad79f16d2d39886c7f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647133"
---
# <a name="for-loop-editor"></a><span data-ttu-id="2dc6d-102">For 루프 편집기</span><span class="sxs-lookup"><span data-stu-id="2dc6d-102">For Loop Editor</span></span>
  <span data-ttu-id="2dc6d-103">**For 루프 편집기** 대화 상자의 **For 루프** 페이지를 사용하여 지정한 조건이 False로 평가될 때까지 워크플로를 반복하는 루프를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-103">Use the **For Loop** page of the **For Loop Editor** dialog box to configure a loop that repeats a workflow until a specified condition evaluates to false.</span></span>  
  
 <span data-ttu-id="2dc6d-104">For 루프 컨테이너 및 패키지에서의 해당 컨테이너 사용 방법은 [For Loop Container](control-flow/for-loop-container.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-104">To learn about the For Loop container and how to use it in packages, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2dc6d-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2dc6d-105">Options</span></span>  
 <span data-ttu-id="2dc6d-106">**InitExpression**</span><span class="sxs-lookup"><span data-stu-id="2dc6d-106">**InitExpression**</span></span>  
 <span data-ttu-id="2dc6d-107">필요에 따라 루프에서 사용하는 값을 초기화하는 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-107">Optionally, provide an expression that initializes values used by the loop.</span></span>  
  
 <span data-ttu-id="2dc6d-108">**EvalExpression**</span><span class="sxs-lookup"><span data-stu-id="2dc6d-108">**EvalExpression**</span></span>  
 <span data-ttu-id="2dc6d-109">루프를 중단할 것인지, 아니면 계속할 것인지를 평가하는 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-109">Provide an expression to evaluate whether the loop should stop or continue.</span></span>  
  
 <span data-ttu-id="2dc6d-110">**AssignExpression**</span><span class="sxs-lookup"><span data-stu-id="2dc6d-110">**AssignExpression**</span></span>  
 <span data-ttu-id="2dc6d-111">필요에 따라 루프가 반복될 때마다 조건을 변경하는 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-111">Optionally, provide an expression that changes a condition each time that the loop repeats.</span></span>  
  
 <span data-ttu-id="2dc6d-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="2dc6d-112">**Name**</span></span>  
 <span data-ttu-id="2dc6d-113">For 루프 컨테이너에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-113">Provide a unique name for the For Loop container.</span></span> <span data-ttu-id="2dc6d-114">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-114">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dc6d-115">개체 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-115">Object names must be unique within a package.</span></span>  
  
 <span data-ttu-id="2dc6d-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="2dc6d-116">**Description**</span></span>  
 <span data-ttu-id="2dc6d-117">For 루프 컨테이너에 대한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dc6d-117">Provide a description of the For Loop container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc6d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dc6d-118">See Also</span></span>  
 <span data-ttu-id="2dc6d-119">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2dc6d-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2dc6d-120">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="2dc6d-120">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="2dc6d-121">[Foreach 루프 컨테이너](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="2dc6d-121">[Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="2dc6d-122">For 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="2dc6d-122">Configure a For Loop Container</span></span>](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
