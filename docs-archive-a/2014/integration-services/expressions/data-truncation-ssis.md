---
title: 데이터 잘림(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0c4280c9eacd22ebf84bf1570d485de51cab09b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660695"
---
# <a name="data-truncation-ssis"></a><span data-ttu-id="4c136-102">데이터 잘림(SSIS)</span><span class="sxs-lookup"><span data-stu-id="4c136-102">Data Truncation (SSIS)</span></span>
  <span data-ttu-id="4c136-103">식 처리 중 데이터가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-103">An expression may inadvertently cause data to be truncated.</span></span> <span data-ttu-id="4c136-104">잘림은 다음과 같은 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-104">Truncation can occur under the following circumstances:</span></span>  
  
-   <span data-ttu-id="4c136-105">문자열.</span><span class="sxs-lookup"><span data-stu-id="4c136-105">Strings.</span></span> <span data-ttu-id="4c136-106">예를 들어 DT_WSTR 데이터 형식의 문자열 데이터를 문자 수로 측정된 동일한 길이의 DT_STR 데이터 형식 문자열로 변환하는 경우 원래 문자열에 더블바이트 문자가 포함되어 있으면 데이터가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-106">For example, translating string data with a DT_WSTR data type to the same length string, measured in characters, with a DT_STR data type causes data loss if the original string contains double-byte characters.</span></span>  
  
-   <span data-ttu-id="4c136-107">유효 자릿수.</span><span class="sxs-lookup"><span data-stu-id="4c136-107">Significant digits.</span></span> <span data-ttu-id="4c136-108">예를 들어 정수를 DT_I4 데이터 형식에서 DT_I2 데이터 형식으로 캐스팅하거나 부호 없는 정수를 부호 있는 정수로 캐스팅하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-108">For example, casting an integer from a DT_I4 data type to a DT_I2 data type or an unsigned integer to a signed integer.</span></span>  
  
-   <span data-ttu-id="4c136-109">무효 자릿수.</span><span class="sxs-lookup"><span data-stu-id="4c136-109">Insignificant digits.</span></span> <span data-ttu-id="4c136-110">예를 들어 실수를 DT_R8에서 DT_R4로 캐스팅하거나 정수를 DT_I4 데이터 형식에서 DT_R4 데이터 형식으로 캐스팅하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-110">For example, casting a real number from a DT_R8 to a DT_R4 or an integer from a DT_I4 data type to a DT_R4 data type.</span></span>  
  
 <span data-ttu-id="4c136-111">식 계산기는 잘림을 발생시킬 수 있는 명시적 캐스트를 식별하고 식을 구문 분석할 때 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-111">The expression evaluator identifies explicit casts that may cause truncation and issues a warning when the expression is parsed.</span></span> <span data-ttu-id="4c136-112">예를 들어 30자 문자열을 20자 문자열로 캐스팅하면 식 계산기가 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-112">For example, the expression evaluator warns you if a 30-character string is cast into a 20-character string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c136-113">런타임에는 잘림을 확인하지 않으므로 경고 없이 데이터가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-113">Truncation is not checked at run time; data is truncated without warning.</span></span> <span data-ttu-id="4c136-114">그러나 대부분의 데이터 어댑터와 변환은 오류 행 처리를 수행할 수 있는 오류 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c136-114">However, most data adapters and transformations support error outputs that can handle the disposition of error rows.</span></span> <span data-ttu-id="4c136-115">데이터 잘림을 처리 하는 방법에 대 한 자세한 내용은 [데이터의 오류 처리](../data-flow/error-handling-in-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c136-115">For more information about handling truncation of data, see [Error Handling in Data](../data-flow/error-handling-in-data.md).</span></span>  
  
  
