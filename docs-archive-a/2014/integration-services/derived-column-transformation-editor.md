---
title: 파생 열 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41a0f0dcd253473f78f2f38426b5fbd3d2ac2812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660075"
---
# <a name="derived-column-transformation-editor"></a><span data-ttu-id="aa8e9-102">파생 열 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="aa8e9-102">Derived Column Transformation Editor</span></span>
  <span data-ttu-id="aa8e9-103">**파생 열 변환 편집기** 대화 상자를 사용하여 새 열 또는 대체 열을 채우는 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-103">Use the **Derived Column Transformation Editor** dialog box to create expressions that populate new or replacement columns.</span></span>  
  
 <span data-ttu-id="aa8e9-104">파생 열 변환에 대한 자세한 내용은 [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-104">To learn more about the Derived Column transformation, see [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="aa8e9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="aa8e9-105">Options</span></span>  
 <span data-ttu-id="aa8e9-106">**변수 및 열**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-106">**Variables and Columns**</span></span>  
 <span data-ttu-id="aa8e9-107">사용 가능한 변수 및 열 목록에서 아래 창의 기존 테이블 행이나 목록 아래쪽의 새 행으로 변수 또는 열을 끌어 변수 또는 입력 열을 사용하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-107">Build an expression that uses a variable or an input column by dragging the variable or column from the list of available variables and columns to an existing table row in the pane below, or to a new row at the bottom of the list.</span></span>  
  
 <span data-ttu-id="aa8e9-108">**함수 및 연산자**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-108">**Functions and Operators**</span></span>  
 <span data-ttu-id="aa8e9-109">목록에서 아래 창으로 함수와 연산자를 끌어 함수 또는 연산자를 사용하여 입력 데이터와 직접 출력 데이터를 계산하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-109">Build an expression that uses a function or an operator to evaluate input data and direct output data by dragging functions and operators from the list to the pane below.</span></span>  
  
 <span data-ttu-id="aa8e9-110">**파생 열 이름**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-110">**Derived Column Name**</span></span>  
 <span data-ttu-id="aa8e9-111">파생 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-111">Provide a derived column name.</span></span> <span data-ttu-id="aa8e9-112">기본값은 번호가 매겨진 파생 열 목록이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-112">The default is a numbered list of derived columns; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="aa8e9-113">**파생 열**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-113">**Derived Column**</span></span>  
 <span data-ttu-id="aa8e9-114">목록에서 파생 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-114">Select a derived column from the list.</span></span> <span data-ttu-id="aa8e9-115">파생 열을 새 출력 열로 추가할지, 아니면 기존 열의 데이터를 바꿀지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-115">Choose whether to add the derived column as a new output column, or to replace the data in an existing column.</span></span>  
  
 <span data-ttu-id="aa8e9-116">**식**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-116">**Expression**</span></span>  
 <span data-ttu-id="aa8e9-117">식을 입력하거나 사용 가능한 열, 변수, 함수 및 연산자에 대한 이전 목록에서 끌어 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-117">Type an expression or build one by dragging from the previous list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="aa8e9-118">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="aa8e9-119">**관련 항목**: [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md), [연산자&#40;SSIS 식&#41;](expressions/operators-ssis-expression.md) 및 [함수&#40;SSIS 식&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="aa8e9-119">**Related topics**: [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="aa8e9-120">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-120">**Data Type**</span></span>  
 <span data-ttu-id="aa8e9-121">새 열에 데이터를 추가하는 경우 **파생 열 변환 편집기** 대화 상자가 식을 자동으로 계산하고 데이터 형식을 적절하게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-121">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the data type appropriately.</span></span> <span data-ttu-id="aa8e9-122">이 열의 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-122">The value of this column is read-only.</span></span> <span data-ttu-id="aa8e9-123">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-123">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="aa8e9-124">**길이**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-124">**Length**</span></span>  
 <span data-ttu-id="aa8e9-125">새 열에 데이터를 추가하는 경우 **파생 열 변환 편집기** 대화 상자가 식을 자동으로 계산하고 문자열 데이터의 열 길이를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-125">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the column length for string data.</span></span> <span data-ttu-id="aa8e9-126">이 열의 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-126">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="aa8e9-127">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-127">**Precision**</span></span>  
 <span data-ttu-id="aa8e9-128">새 열에 데이터를 추가하는 경우 **파생 열 변환 편집기** 대화 상자가 데이터 형식을 기반으로 숫자 데이터의 전체 자릿수를 자동으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-128">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the precision for numeric data based on the data type.</span></span> <span data-ttu-id="aa8e9-129">이 열의 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-129">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="aa8e9-130">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-130">**Scale**</span></span>  
 <span data-ttu-id="aa8e9-131">새 열에 데이터를 추가하는 경우 **파생 열 변환 편집기** 대화 상자가 데이터 형식을 기반으로 숫자 데이터의 소수 자릿수를 자동으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-131">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the scale for numeric data based on the data type.</span></span> <span data-ttu-id="aa8e9-132">이 열의 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-132">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="aa8e9-133">**코드 페이지**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-133">**Code Page**</span></span>  
 <span data-ttu-id="aa8e9-134">새 열에 데이터를 추가하는 경우 **파생 열 변환 편집기** 대화 상자가 DT_STR 데이터 형식에 대한 코드 페이지를 자동으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-134">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets code page for the DT_STR data type.</span></span> <span data-ttu-id="aa8e9-135">**코드 페이지**를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-135">You can update **Code Page**.</span></span>  
  
 <span data-ttu-id="aa8e9-136">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="aa8e9-136">**Configure error output**</span></span>  
 <span data-ttu-id="aa8e9-137">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8e9-137">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8e9-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa8e9-138">See Also</span></span>  
 <span data-ttu-id="aa8e9-139">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="aa8e9-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="aa8e9-140">파생 열 변환을 사용하여 열 값 파생</span><span class="sxs-lookup"><span data-stu-id="aa8e9-140">Derive Column Values by Using the Derived Column Transformation</span></span>](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
