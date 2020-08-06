---
title: + (연결)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c01f82a50962f42862db836171b0ad683c97453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732864"
---
# <a name="-concatenate-ssis-expression"></a><span data-ttu-id="c73d6-102">+(연결)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="c73d6-102">+ (Concatenate) (SSIS Expression)</span></span>
  <span data-ttu-id="c73d6-103">두 식을 하나의 식으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-103">Concatenates two expressions into one expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73d6-104">구문</span><span class="sxs-lookup"><span data-stu-id="c73d6-104">Syntax</span></span>  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c73d6-105">인수</span><span class="sxs-lookup"><span data-stu-id="c73d6-105">Arguments</span></span>  
 <span data-ttu-id="c73d6-106">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="c73d6-106">*expression1, expression2*</span></span>  
 <span data-ttu-id="c73d6-107">DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT 또는 DT_IMAGE 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-107">Is any valid DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c73d6-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="c73d6-108">Result Types</span></span>  
 <span data-ttu-id="c73d6-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="c73d6-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c73d6-110">설명</span><span class="sxs-lookup"><span data-stu-id="c73d6-110">Remarks</span></span>  
 <span data-ttu-id="c73d6-111">식은 DT_STR 및 DT_WSTR 데이터 형식 중 하나 또는 둘 다를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-111">The expression can use either or both of the DT_STR and DT_WSTR data types.</span></span>  
  
 <span data-ttu-id="c73d6-112">DT_STR 및 DT_WSTR 데이터 형식을 연결하면 DT_WSTR 형식의 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-112">The concatenation of the DT_STR and DT_WSTR data types returns a result of the DT_WSTR type.</span></span> <span data-ttu-id="c73d6-113">문자열 길이는 문자로 표시된 원래 문자열 길이의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-113">The length of the string is the sum of the lengths of the original strings expressed in characters.</span></span>  
  
 <span data-ttu-id="c73d6-114">문자열 데이터 형식 DT_STR 및 DT_WSTR나 BLOB(Binary Large Object Block) 데이터 형식 DT_TEXT, DT_NTEXT 및 DT_IMAGE의 데이터만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-114">Only data with the string data types DT_STR and DT_WSTR or the Binary Large Object Block (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE can be concatenated.</span></span> <span data-ttu-id="c73d6-115">기타 데이터 형식은 연결을 수행하기 전에 명시적으로 이러한 데이터 형식 중 하나로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-115">Other data types must be explicitly converted to one of these data types before concatenation occurs.</span></span> <span data-ttu-id="c73d6-116">데이터 형식 간 올바른 캐스트에 대한 자세한 내용은 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c73d6-116">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="c73d6-117">두 식이 모두 동일한 데이터 형식으로 되어 있거나 식 하나가 암시적으로 또 다른 식의 데이터 형식으로 변환될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-117">Both expressions must be of the same data type, or one expression must be implicitly convertible to the data type of the other expression.</span></span> <span data-ttu-id="c73d6-118">예를 들어 "Order date is " 문자열과 **OrderDate** 열을 연결하면 **OrderDate** 값이 암시적으로 문자열 데이터 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-118">For example, if the string "Order date is " and the column **OrderDate** are concatenated, the values in **OrderDate** are implicitly converted to a string data type.</span></span> <span data-ttu-id="c73d6-119">두 개의 숫자 값을 연결하려면 두 숫자 값을 모두 명시적으로 문자열 데이터 형식으로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-119">To concatenate two numeric values, both numeric values must be explicitly cast to a string data type.</span></span>  
  
 <span data-ttu-id="c73d6-120">연결은 BLOB 데이터 형식인 DT_TEXT, DT_NTEXT 또는 DT_IMAGE 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-120">A concatenation can use only one BLOB data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="c73d6-121">두 요소 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-121">If either element is null, the result is null.</span></span>  
  
 <span data-ttu-id="c73d6-122">문자열 리터럴은 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-122">String literals must be enclosed in quotation marks.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c73d6-123">식 예</span><span class="sxs-lookup"><span data-stu-id="c73d6-123">Expression Examples</span></span>  
 <span data-ttu-id="c73d6-124">다음 예에서는 **FirstName** 및 **LastName** 열의 값을 연결하고 사이에 공백을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-124">This example concatenates the values in the **FirstName** and **LastName** columns and inserts a space between them.</span></span>  
  
```  
FirstName + ' ' + LastName  
```  
  
 <span data-ttu-id="c73d6-125">다음 예에서는 변수 **ZIPCode** 와 **ZIPCode+4**를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-125">This example concatenates the variables **ZIPCode** and **ZIPCode+4**.</span></span> <span data-ttu-id="c73d6-126">두 변수는 모두 문자열 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-126">Both variables have a string data type.</span></span> <span data-ttu-id="c73d6-127">**ZIPCode+4** 는 변수 이름에 + 문자가 포함되어 있으므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c73d6-127">**ZIPCode+4** must be enclosed in brackets because the variable name includes the + character.</span></span>  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a><span data-ttu-id="c73d6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c73d6-128">See Also</span></span>  
 <span data-ttu-id="c73d6-129">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="c73d6-129">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="c73d6-130">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="c73d6-130">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
