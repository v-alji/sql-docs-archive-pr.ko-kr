---
title: TOKEN(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9fdd06bf-5bc9-445c-95bf-709e0ca5989b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0598c3832e4bf6f838087be4fee541663c8bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732772"
---
# <a name="token--ssis-expression"></a><span data-ttu-id="87a4d-102">TOKEN(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="87a4d-102">TOKEN  (SSIS Expression)</span></span>
  <span data-ttu-id="87a4d-103">문자열에서 토큰을 구분하는 지정된 구분 기호와 반환할 토큰을 나타내는 토큰 번호를 기반으로 문자열에서 토큰(부분 문자열)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-103">Returns a token (substring) from a string based on the specified delimiters that separate tokens in the string and the number of the token that denotes which token to be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a4d-104">구문</span><span class="sxs-lookup"><span data-stu-id="87a4d-104">Syntax</span></span>  
  
```  
TOKEN(character_expression, delimiter_string, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="87a4d-105">인수</span><span class="sxs-lookup"><span data-stu-id="87a4d-105">Arguments</span></span>  
 <span data-ttu-id="87a4d-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="87a4d-106">*character_expression*</span></span>  
 <span data-ttu-id="87a4d-107">구분 기호로 구분된 토큰이 포함된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-107">A string that contains tokens separated by delimiters.</span></span>  
  
 <span data-ttu-id="87a4d-108">*delimiter_string*</span><span class="sxs-lookup"><span data-stu-id="87a4d-108">*delimiter_string*</span></span>  
 <span data-ttu-id="87a4d-109">구분 기호 문자가 포함된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-109">A string that contains delimiter characters.</span></span> <span data-ttu-id="87a4d-110">예를 들어 "; ,"에는 세미콜론, 공백 및 쉼표의 세 구분 문자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-110">For example, "; ," contains three delimiter characters semi-colon, a blank space, and a comma.</span></span>  
  
 <span data-ttu-id="87a4d-111">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="87a4d-111">*occurrence*</span></span>  
 <span data-ttu-id="87a4d-112">반환될 토큰을 지정하는 부호 있는 또는 부호 없는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-112">A signed or unsigned integer that specifies the token to be returned.</span></span> <span data-ttu-id="87a4d-113">예를 들어 이 매개 변수의 값으로 3을 지정하면 문자열의 세 번째 토큰이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-113">For example, if you specify 3 as a value for this parameter, the third token in the string is returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="87a4d-114">결과 형식</span><span class="sxs-lookup"><span data-stu-id="87a4d-114">Result Types</span></span>  
 <span data-ttu-id="87a4d-115">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="87a4d-115">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87a4d-116">설명</span><span class="sxs-lookup"><span data-stu-id="87a4d-116">Remarks</span></span>  
 <span data-ttu-id="87a4d-117">이 함수는 <character_expression> 문자열을 <delimiter_string>에 지정된 구분 기호로 구분된 토큰 세트로 분할한 다음, N번째 토큰을 반환합니다. 여기서 N은 \<occurrence> 매개 변수로 지정된 토큰의 발생 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-117">This function splits up the <character_expression> string into a set of tokens separated by the delimiters specified in the <delimiter_string> and then returns the Nth token where N is the number of occurrence of the token specified by the \<occurrence> parameter.</span></span> <span data-ttu-id="87a4d-118">이 함수의 샘플 사용법은 예 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="87a4d-118">See Examples section for sample usages of this function.</span></span>  
  
 <span data-ttu-id="87a4d-119">다음 설명은 TOKEN 함수에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-119">The following remarks apply to the TOKEN function:</span></span>  
  
-   <span data-ttu-id="87a4d-120">구분 기호 문자열은 하나 이상의 구분 기호 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-120">The delimiter string can contain one or more delimiter characters.</span></span>  
  
-   <span data-ttu-id="87a4d-121">\<occurrence> 매개 변수 값이 문자열의 총 토큰 수보다 큰 경우 이 함수는 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-121">If the value of \<occurrence> parameter is higher than the total number of tokens in the string, the function returns NULL.</span></span>  
  
-   <span data-ttu-id="87a4d-122">선행 구분 기호는 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-122">Leading delimiters are skipped.</span></span>  
  
-   <span data-ttu-id="87a4d-123">TOKEN은 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-123">TOKEN works only with the DT_WSTR data type.</span></span> <span data-ttu-id="87a4d-124">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 TOKEN 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-124">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TOKEN performs its operation.</span></span> <span data-ttu-id="87a4d-125">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-125">Other data types must be explicitly cast to the DT_WSTR data type.</span></span>  
  
-   <span data-ttu-id="87a4d-126">character_expression이 null인 경우 TOKEN이 null 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-126">TOKEN returns a null result if the character_expression is null.</span></span>  
  
-   <span data-ttu-id="87a4d-127">식의 모든 인수에 대한 값으로 변수 및 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-127">You can use variables and columns as values of all arguments in the expression.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="87a4d-128">식 예</span><span class="sxs-lookup"><span data-stu-id="87a4d-128">Expression Examples</span></span>  
 <span data-ttu-id="87a4d-129">다음 예에서는 TOKEN 함수가 "a"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-129">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="87a4d-130">"a little white dog" 문자열에는 4개의 토큰 "a", "little", "white", "dog"가 " "(공백 문자)로 구분되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-130">The string "a little white dog" has 4 tokens "a", "little", "white", "dog" separated by the delimiter " " (space character).</span></span> <span data-ttu-id="87a4d-131">두 번째 인수인 구분 기호 문자열은 입력 문자열을 토큰으로 분할하는 데 사용되는 한 구분 기호로 공백 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-131">The second argument, a delimiter string, specifies only one delimiter, the space character, to be used in splitting the input string into tokens.</span></span> <span data-ttu-id="87a4d-132">마지막 인수 1은 첫 번째로 반환될 토큰을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-132">The last argument, 1, specifies that the first token to be returned.</span></span> <span data-ttu-id="87a4d-133">이 샘플 문자열에서 첫 번째 토큰은 "a"입니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-133">The first token is "a" in this sample string.</span></span>  
  
```  
TOKEN("a little white dog"," ",1)  
```  
  
 <span data-ttu-id="87a4d-134">다음 예에서는 TOKEN 함수가 "dog"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-134">In the following example, the TOKEN function returns "dog".</span></span> <span data-ttu-id="87a4d-135">이 예의 구분 기호 문자열에는 구분 기호가 5개 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-135">The delimiter string in this example contains 5 delimiters.</span></span> <span data-ttu-id="87a4d-136">입력 문자열에는 "a", "little", "white", "dog"의 4개 토큰이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-136">The input string contains 4 tokens: "a", "little", "white", "dog".</span></span>  
  
```  
TOKEN("a:little|white dog","| ,.:",4)  
```  
  
 <span data-ttu-id="87a4d-137">다음 예에서는 문자열에 99 토큰이 없으므로 TOKEN 함수가 ""(빈 문자열)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-137">In the following example, the TOKEN function returns "" (an empty string) because there are no 99 tokens in the string.</span></span>  
  
```  
TOKEN("a little white dog"," ",99)  
```  
  
 <span data-ttu-id="87a4d-138">다음 예에서는 TOKEN 함수가 전체 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-138">In the following example, the TOKEN function returns the full string.</span></span> <span data-ttu-id="87a4d-139">이 함수는 입력 문자열에서 구분 기호를 구문 분석하고 문자열에 구분 기호가 없으므로 전체 문자열을 첫 번째 토큰으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-139">The function parses the input string for delimiters and since there are none in the string, it just adds the entire string as the first token.</span></span>  
  
```  
TOKEN("a little white dog","|",1)  
```  
  
 <span data-ttu-id="87a4d-140">다음 예에서는 TOKEN 함수가 "a"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-140">In the following example, the TOKEN function returns "a".</span></span> <span data-ttu-id="87a4d-141">모든 선행 공백 문자는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-141">It ignores all the leading space characters.</span></span>  
  
```  
TOKEN("        a little white dog", " ", 1)  
```  
  
 <span data-ttu-id="87a4d-142">다음 예에서는 TOKEN 함수가 날짜 문자열에서 연도를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-142">In the following example, the TOKEN function returns the year from a date string.</span></span>  
  
```  
TOKEN("2009/01/01", "/"), 1  
```  
  
 <span data-ttu-id="87a4d-143">다음 예에서는 TOKEN 함수가 지정된 경로에서 파일 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-143">In the following example, the TOKEN function returns the file name from the specified path.</span></span> <span data-ttu-id="87a4d-144">예를 들어 User::Path 값이 "c:\program files\data\myfile.txt"인 경우 TOKEN 함수는 "myfile.txt"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-144">For example, if the value of User::Path is "c:\program files\data\myfile.txt", the TOKEN function returns "myfile.txt".</span></span> <span data-ttu-id="87a4d-145">TOKENCOUNT 함수는 4를 반환하고 TOKEN 함수는 4번째 토큰 "myfile.txt"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="87a4d-145">The TOKENCOUNT function returns 4 and the TOKEN function return the 4th token, "myfile.txt".</span></span>  
  
```  
TOKEN(@[User::Path], "\\", TOKENCOUNT(@[User::Path], "\\"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="87a4d-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87a4d-146">See Also</span></span>  
 [<span data-ttu-id="87a4d-147">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="87a4d-147">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
