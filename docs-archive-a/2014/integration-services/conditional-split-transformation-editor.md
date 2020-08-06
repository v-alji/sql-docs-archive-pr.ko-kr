---
title: 조건부 분할 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386a93eb7c3058c7c3e98f2b652199d115d841f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647168"
---
# <a name="conditional-split-transformation-editor"></a><span data-ttu-id="df826-102">조건부 분할 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="df826-102">Conditional Split Transformation Editor</span></span>
  <span data-ttu-id="df826-103">**조건부 분할 변환 편집기** 대화 상자를 사용하여 식을 만들고, 식을 평가하는 순서를 설정하고, 조건부 분할 출력의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df826-103">Use the **Conditional Split Transformation Editor** dialog box to create expressions, set the order in which expressions are evaluated, and name the outputs of a conditional split.</span></span> <span data-ttu-id="df826-104">이 대화 상자에는 식을 작성할 때 사용할 수 있는 수치 연산, 문자열 및 날짜/시간 함수와 연산자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df826-104">This dialog box includes mathematical, string, and date/time functions and operators that you can use to build expressions.</span></span> <span data-ttu-id="df826-105">True로 평가하는 첫 번째 조건에 따라 행을 전송할 출력이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="df826-105">The first condition that evaluates as true determines the output to which a row is directed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df826-106">조건부 분할 변환에서는 각 입력 행을 하나의 출력에만 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-106">The Conditional Split transformation directs each input row to one output only.</span></span> <span data-ttu-id="df826-107">여러 조건을 입력하는 경우 조건부 분할 변환에서는 각 행을 조건이 True가 되는 첫 번째 출력으로 전송하고 해당 행에 대한 다른 조건은 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-107">If you enter multiple conditions, the transformation sends each row to the first output for which the condition is true and disregards subsequent conditions for that row.</span></span> <span data-ttu-id="df826-108">여러 조건을 연속적으로 평가해야 하는 경우 조건부 분할 변환을 데이터 흐름에서 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-108">If you need to evaluate several conditions successively, you may need to concatenate multiple Conditional Split transformations in the data flow.</span></span>  
  
 <span data-ttu-id="df826-109">조건부 분할 변환에 대한 자세한 내용은 [조건부 분할 변환](data-flow/transformations/conditional-split-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df826-109">To learn more about the Conditional Split transformation, see [Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="df826-110">옵션</span><span class="sxs-lookup"><span data-stu-id="df826-110">Options</span></span>  
 <span data-ttu-id="df826-111">**주문**</span><span class="sxs-lookup"><span data-stu-id="df826-111">**Order**</span></span>  
 <span data-ttu-id="df826-112">행을 선택하고 오른쪽의 화살표 키를 사용하여 식을 평가하는 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-112">Select a row and use the arrow keys at right to change the order in which to evaluate expressions.</span></span>  
  
 <span data-ttu-id="df826-113">**출력 이름**</span><span class="sxs-lookup"><span data-stu-id="df826-113">**Output Name**</span></span>  
 <span data-ttu-id="df826-114">출력 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-114">Provide an output name.</span></span> <span data-ttu-id="df826-115">기본값은 번호가 매겨진 사례 목록이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df826-115">The default is a numbered list of cases; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="df826-116">**Condition**</span><span class="sxs-lookup"><span data-stu-id="df826-116">**Condition**</span></span>  
 <span data-ttu-id="df826-117">식을 입력하거나 사용 가능한 열, 변수, 함수 및 연산자 목록에서 끌어 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-117">Type an expression or build one by dragging from the list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="df826-118">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df826-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="df826-119">**관련 항목:**  [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md), [연산자&#40;SSIS 식&#41;](expressions/operators-ssis-expression.md) 및 [함수&#40;SSIS 식&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="df826-119">**Related topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="df826-120">**기본 출력 이름**</span><span class="sxs-lookup"><span data-stu-id="df826-120">**Default output name**</span></span>  
 <span data-ttu-id="df826-121">기본 출력의 이름을 입력하거나 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-121">Type a name for the default output, or use the default.</span></span>  
  
 <span data-ttu-id="df826-122">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="df826-122">**Configure error output**</span></span>  
 <span data-ttu-id="df826-123">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df826-123">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df826-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df826-124">See Also</span></span>  
 <span data-ttu-id="df826-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="df826-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="df826-126">조건부 분할 변환을 사용하여 데이터 세트 분할</span><span class="sxs-lookup"><span data-stu-id="df826-126">Split a Dataset by Using the Conditional Split Transformation</span></span>](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
