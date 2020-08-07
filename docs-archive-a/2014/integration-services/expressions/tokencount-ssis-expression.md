---
title: TOKENCOUNT(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9068e4958570a0222bc8e1a4c90d34acc5bdf3dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732764"
---
# <a name="tokencount-ssis-expression"></a><span data-ttu-id="0864e-102">TOKENCOUNT(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="0864e-102">TOKENCOUNT (SSIS Expression)</span></span>
  <span data-ttu-id="0864e-103">지정된 구분 기호로 구분된 토큰을 포함하는 문자열의 토큰 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-103">Returns the number of tokens in a string that contains tokens separated by the specified delimiters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0864e-104">구문</span><span class="sxs-lookup"><span data-stu-id="0864e-104">Syntax</span></span>  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a><span data-ttu-id="0864e-105">인수</span><span class="sxs-lookup"><span data-stu-id="0864e-105">Arguments</span></span>  
 <span data-ttu-id="0864e-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="0864e-106">*character_expression*</span></span>  
 <span data-ttu-id="0864e-107">구분 기호로 구분된 토큰이 포함된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="0864e-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="0864e-108">*delimiter_string*</span></span>  
 <span data-ttu-id="0864e-109">구분 기호 문자가 포함된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="0864e-110">예를 들어 "; ,"에는 세미콜론, 공백 및 쉼표의 세 구분 문자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0864e-111">결과 형식</span><span class="sxs-lookup"><span data-stu-id="0864e-111">Result Types</span></span>  
 <span data-ttu-id="0864e-112">DT_I4</span><span class="sxs-lookup"><span data-stu-id="0864e-112">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0864e-113">설명</span><span class="sxs-lookup"><span data-stu-id="0864e-113">Remarks</span></span>  
 <span data-ttu-id="0864e-114">다음 설명은 TOKEN 함수에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-114">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="0864e-115">구분 기호 문자열은 하나 이상의 구분 기호 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-115">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="0864e-116">선행 구분 기호는 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-116">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="0864e-117">TOKENCOUNT는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-117">TOKENCOUNT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="0864e-118">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 TOKEN 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="0864e-119">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="0864e-120">character_expression이 null인 경우 TOKENCOUNT는 0(영)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-120">TOKENCOUNT returns 0 (zero) if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="0864e-121">변수 및 열을 이 식의 인수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-121">You can use variables and columns as arguments for this expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="0864e-122">식 예</span><span class="sxs-lookup"><span data-stu-id="0864e-122">Expression Examples</span></span>  
 <span data-ttu-id="0864e-123">다음 예제에서는 문자열에 "01", "12", "2011"의 토큰 3개가 있으므로 TOKENCOUNT 함수에서 3을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-123">In the following example, the TOKENCOUNT function returns 3 because the string contains three tokens: "01", "12", "2011".</span></span>  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 <span data-ttu-id="0864e-124">다음 예제에서는 토큰 4개("a", "little", "white", "dog")가 있으므로 TOKENCOUNT 함수에서 4를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-124">In the following example, the TOKENCOUNT function returns 4 because there are four tokens ("a", "little", "white", "dog").</span></span>  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 <span data-ttu-id="0864e-125">다음 예에서 TOKENCOUNT 함수는 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-125">In the following example, the TOKENCOUNT function returns 1.</span></span> <span data-ttu-id="0864e-126">이 함수는 입력 문자열에서 구분 기호를 구문 분석하고 문자열에 구분 기호가 없으므로 전체 문자열을 첫 번째 토큰으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-126">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 <span data-ttu-id="0864e-127">다음 예에서 TOKENCOUNT 함수는 4를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-127">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="0864e-128">이 예의 구분 기호 문자열에는 구분 기호가 5개 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-128">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="0864e-129">입력 문자열에는 "a", "little", "white", "dog"의 4개 토큰이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-129">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 <span data-ttu-id="0864e-130">다음 예에서 TOKENCOUNT 함수는 4를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-130">In the following example, the TOKENCOUNT function returns 4.</span></span> <span data-ttu-id="0864e-131">모든 선행 공백 문자는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="0864e-131">It ignores all the leading space characters.</span></span>  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="0864e-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0864e-132">See Also</span></span>  
 [<span data-ttu-id="0864e-133">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="0864e-133">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
