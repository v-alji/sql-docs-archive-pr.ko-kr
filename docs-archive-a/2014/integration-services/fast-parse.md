---
title: 빠른 구문 분석 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 343b8b8b74338512dbf29b3d2efd436df1ffa8ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735476"
---
# <a name="fast-parse"></a><span data-ttu-id="49f26-102">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="49f26-102">Fast Parse</span></span>
  <span data-ttu-id="49f26-103">빠른 구문 분석에서는 데이터 구문 분석을 위한 신속하고 간단한 루틴을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="49f26-104">이러한 루틴은 로캘을 구분하지 않으며 날짜, 시간 및 정수 형식의 하위 집합만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-104">These routines are not locale-sensitive and they support only a subset of date, time, and integer formats.</span></span>  
  
## <a name="requirements-and-limitations"></a><span data-ttu-id="49f26-105">요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="49f26-105">Requirements and Limitations</span></span>  
 <span data-ttu-id="49f26-106">빠른 구문 분석을 구현하면 패키지는 날짜, 시간 및 숫자 데이터를 로캘 관련 형식 및 자주 사용하는 ISO 8601 기본 및 확장 형식으로 해석하는 기능을 사용할 수 없지만 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-106">By implementing fast parse, a package forfeits its ability to interpret date, time, and numeric data in locale-specific formats and many frequently used ISO 8601 basic and extended formats, but the package enhances its performance.</span></span> <span data-ttu-id="49f26-107">예를 들어 빠른 구문 분석에서는 YYYYMMDD 및 YYYY-MM-DD처럼 가장 일반적으로 사용되는 날짜 형식 표현만 지원되고, 로캘 관련 구문 분석은 수행되지 않으며, 통화 데이터의 특수 문자가 인식되지 않고, 정수의 16진수 또는 과학적 표기법이 변환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-107">For example, fast parse supports only the most commonly used date format representations such as YYYYMMDD and YYYY-MM-DD, does not perform locale-specific parsing, does not recognize special characters in currency data, and cannot convert hexadecimal or scientific representation of integers.</span></span>  
  
 <span data-ttu-id="49f26-108">빠른 구문 분석은 플랫 파일 원본 또는 데이터 변환을 사용하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-108">Fast parse is available only when you use the Flat File source or the Data Conversion transformation.</span></span> <span data-ttu-id="49f26-109">성능 향상이 중요한 경우 가능하면 이러한 데이터 흐름 구성 요소에 빠른 구문 분석을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-109">The increase in performance can be significant, and you should consider using fast parse in these data flow components if you can.</span></span>  
  
 <span data-ttu-id="49f26-110">패키지의 데이터 흐름에 로캘 구분 구문 분석이 필요한 경우 빠른 구문 분석 대신 표준 구문 분석이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-110">If the data flow in the package requires locale-sensitive parsing, standard parse is recommended instead of fast parse.</span></span> <span data-ttu-id="49f26-111">예를 들어 빠른 구문 분석에서는 쉼표, 연도-월-날짜 형식 이외의 날짜 형식 및 통화 기호와 같은 숫자 기호가 포함되는 로캘 구분 데이터가 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-111">For example, fast parse does not recognize locale-sensitive data that includes decimal symbols such as the comma, date formats other than year-month-date formats, and currency symbols.</span></span>  
  
 <span data-ttu-id="49f26-112">세기, 연도 또는 월과 같은 하나 이상의 날짜 부분을 의미하는 잘린 표시는 빠른 구문 분석에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-112">Truncated representations that imply one or more date parts, such as a century, a year, or a month, are not recognized by fast parse.</span></span> <span data-ttu-id="49f26-113">예를 들어 빠른 구문 분석에서는 세기가 암시적으로 잘린 연도 및 월을 나타내는 '**-YYMM**' 형식이나 연도가 암시적으로 잘린 월을 나타내는 '**--MM**'이 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-113">For example, fast parse recognizes neither the '**-YYMM**' format, which specifies a year and month in an implied century, nor '**--MM**', which specifies a month in an implied year.</span></span> <span data-ttu-id="49f26-114">하지만 일부 축약 형식 표현은 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-114">However, some representations with reduced precision are recognized.</span></span> <span data-ttu-id="49f26-115">예를 들어 빠른 구문 분석에서는 시간과 분만 나타내는 'hhmm;' 형식과 연도만 나타내는 '**YYYY**'가 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-115">For example, fast parse recognizes the 'hhmm;' format, which indicates hour and minute only, and '**YYYY**', which indicates year only.</span></span>  
  
 <span data-ttu-id="49f26-116">빠른 구문 분석은 열 수준에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-116">Fast parse is specified at the column level.</span></span> <span data-ttu-id="49f26-117">플랫 파일 원본과 데이터 변환의 경우 출력 열에 빠른 구문 분석을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-117">In the Flat File source and the Data Conversion transformation, you can specify Fast parse on output columns.</span></span> <span data-ttu-id="49f26-118">입력과 출력에는 로캘 구분 및 로캘 비구분 열이 모두 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49f26-118">Inputs and outputs can include both locale-sensitive and locale-insensitive columns.</span></span>  
  
 <span data-ttu-id="49f26-119">빠른 구문 분석에서 지원되는 데이터 형식에 대한 자세한 내용은 [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) 및 [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="49f26-119">For more information about the data formats that Fast parse supports, see [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) and [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="49f26-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="49f26-120">Related Tasks</span></span>  
 [<span data-ttu-id="49f26-121">빠른 구문 분석 설정</span><span class="sxs-lookup"><span data-stu-id="49f26-121">Set Fast Parse</span></span>](../../2014/integration-services/set-fast-parse.md)  
  
  
