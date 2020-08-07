---
title: SIGN(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a34992b0029cd378274e38ce4e37fcd313d2b788
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732800"
---
# <a name="sign-ssis-expression"></a><span data-ttu-id="cdd21-102">SIGN(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="cdd21-102">SIGN (SSIS Expression)</span></span>
  <span data-ttu-id="cdd21-103">숫자 식의 양수(+1), 음수(-1) 또는 영(0) 부호를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-103">Returns the positive (+1), negative (-1), or zero (0) sign of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd21-104">구문</span><span class="sxs-lookup"><span data-stu-id="cdd21-104">Syntax</span></span>  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="cdd21-105">인수</span><span class="sxs-lookup"><span data-stu-id="cdd21-105">Arguments</span></span>  
 <span data-ttu-id="cdd21-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="cdd21-106">*numeric_expression*</span></span>  
 <span data-ttu-id="cdd21-107">유효한 부호 있는 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-107">Is a valid signed numeric expression.</span></span> <span data-ttu-id="cdd21-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cdd21-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cdd21-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="cdd21-109">Result Types</span></span>  
 <span data-ttu-id="cdd21-110">DT_I4</span><span class="sxs-lookup"><span data-stu-id="cdd21-110">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdd21-111">설명</span><span class="sxs-lookup"><span data-stu-id="cdd21-111">Remarks</span></span>  
 <span data-ttu-id="cdd21-112">인수가 Null이면 SIGN 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-112">SIGN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="cdd21-113">식 예</span><span class="sxs-lookup"><span data-stu-id="cdd21-113">Expression Examples</span></span>  
 <span data-ttu-id="cdd21-114">이 예에서는 숫자 리터럴의 부호가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-114">This example returns the sign of a numeric literal.</span></span> <span data-ttu-id="cdd21-115">반환 결과는 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-115">The return result is -1.</span></span>  
  
```  
SIGN(-123.45)  
```  
  
 <span data-ttu-id="cdd21-116">이 예에서는 **DealerPrice** 열에서 **StandardCost** 열을 뺀 결과의 부호가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdd21-116">This example returns the sign of the result of subtracting the **StandardCost** column from the **DealerPrice** column.</span></span>  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdd21-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cdd21-117">See Also</span></span>  
 [<span data-ttu-id="cdd21-118">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="cdd21-118">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
