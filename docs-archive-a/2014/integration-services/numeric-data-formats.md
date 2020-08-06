---
title: 숫자 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc54a331c3762e31ba9d9a431aaca7eda6374d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651088"
---
# <a name="numeric-data-formats"></a><span data-ttu-id="3ca3e-102">숫자 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3ca3e-102">Numeric Data Formats</span></span>
  <span data-ttu-id="3ca3e-103">빠른 구문 분석에서는 데이터 구문 분석을 위해 로캘을 구분하지 않는 신속하고 간단한 루틴을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-103">Fast parse provides a fast, simple, locale-insensitive set of routines for parsing data.</span></span> <span data-ttu-id="3ca3e-104">빠른 구문 분석은 일부 제한된 정수 데이터 형식만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-104">Fast parse supports only a limited set of formats for integer data types.</span></span>  
  
## <a name="integer-data-types"></a><span data-ttu-id="3ca3e-105">정수 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3ca3e-105">Integer Data Types</span></span>  
 <span data-ttu-id="3ca3e-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 제공되는 정수 데이터 형식은 DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8 및 DT_UI8입니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-106">The integer data types that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides are DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8, and DT_UI8.</span></span> <span data-ttu-id="3ca3e-107">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-107">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="3ca3e-108">빠른 구문 분석에서는 정수 데이터에 대해 다음과 같은 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-108">Fast parse supports the following formats for integer data types:</span></span>  
  
-   <span data-ttu-id="3ca3e-109">0개 이상의 선행 및 후행 공백이나 탭 정지.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-109">Zero or more leading and trailing spaces or tab stops.</span></span> <span data-ttu-id="3ca3e-110">예를 들어 "  123  "은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-110">For example, the value "  123  " is valid.</span></span> <span data-ttu-id="3ca3e-111">공백으로만 이뤄진 값은 0으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-111">A value that is all spaces evaluates to zero.</span></span>  
  
-   <span data-ttu-id="3ca3e-112">선행 더하기 기호, 빼기 기호 또는 아무 기호도 사용되지 않음.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-112">A leading plus sign, minus sign, or neither.</span></span> <span data-ttu-id="3ca3e-113">예를 들어 +123, -123 및 123은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-113">For example, the values +123, -123, and 123 are valid.</span></span>  
  
-   <span data-ttu-id="3ca3e-114">하나 이상의 힌두-아라비아 숫자(0-9).</span><span class="sxs-lookup"><span data-stu-id="3ca3e-114">One or more Hindu-Arabic numerals (0-9).</span></span> <span data-ttu-id="3ca3e-115">예를 들어 345는 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-115">For example, the value 345 is valid.</span></span> <span data-ttu-id="3ca3e-116">다른 언어의 숫자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-116">Other language numerals are not supported.</span></span>  
  
 <span data-ttu-id="3ca3e-117">지원되지 않는 데이터 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-117">Non-supported data formats include the following:</span></span>  
  
-   <span data-ttu-id="3ca3e-118">특수 문자.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-118">Special characters.</span></span> <span data-ttu-id="3ca3e-119">예를 들어 통화 문자 $는 지원되지 않으며 $20 값은 구문 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-119">For example, the currency character $ is not supported, and the value $20 cannot be parsed.</span></span>  
  
-   <span data-ttu-id="3ca3e-120">줄 바꿈, 캐리지 리턴 및 줄 바꿈하지 않는 공백과 같은 공백 문자.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-120">White-space characters such as line feed, carriage returns, and non-breaking spaces.</span></span> <span data-ttu-id="3ca3e-121">예를 들어 "123" 값은 구문 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-121">For example, the value " 123" cannot be parsed.</span></span>  
  
-   <span data-ttu-id="3ca3e-122">정수의 16진 표시.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-122">Hexadecimal representations of integers.</span></span> <span data-ttu-id="3ca3e-123">예를 들어 2EE 값은 구문 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-123">For example, the value 2EE cannot be parsed.</span></span>  
  
-   <span data-ttu-id="3ca3e-124">정수의 공학 표시.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-124">Scientific notation representation of integers.</span></span> <span data-ttu-id="3ca3e-125">예를 들어 1E+10 값은 구문 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-125">For example, the value 1E+10 cannot be parsed.</span></span>  
  
 <span data-ttu-id="3ca3e-126">다음 형식은 정수에 대한 출력 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-126">The following formats are output data formats for integers:</span></span>  
  
-   <span data-ttu-id="3ca3e-127">음수에는 빼기 기호가 표시되고 양수에는 기호가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-127">A minus sign for negative numbers and nothing for positive ones.</span></span>  
  
-   <span data-ttu-id="3ca3e-128">공백이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ca3e-128">No white spaces.</span></span>  
  
-   <span data-ttu-id="3ca3e-129">하나 이상의 힌두-아라비아 숫자(0-9).</span><span class="sxs-lookup"><span data-stu-id="3ca3e-129">One or more Hindu-Arabic numerals (0-9).</span></span>  
  
  
