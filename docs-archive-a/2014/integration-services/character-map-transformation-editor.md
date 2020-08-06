---
title: 문자표 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6cdcdba448dafc6ccf03774d4f611dee704b823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648503"
---
# <a name="character-map-transformation-editor"></a><span data-ttu-id="51afc-102">문자표 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="51afc-102">Character Map Transformation Editor</span></span>
  <span data-ttu-id="51afc-103">**문자표 변환 편집기** 대화 상자를 사용하여 열 데이터에 적용할 문자열 함수를 선택하고 매핑이 내부 변경인지, 아니면 새 열로 추가되었는지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-103">Use the **Character Map Transformation Editor** dialog box to select the string functions to apply to column data and to specify whether mapping is an in-place change or added as a new column.</span></span>  
  
 <span data-ttu-id="51afc-104">문자 매핑 변환에 대한 자세한 내용은 [Character Map Transformation](data-flow/transformations/character-map-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51afc-104">To learn more about the Character Map transformation, see [Character Map Transformation](data-flow/transformations/character-map-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="51afc-105">옵션</span><span class="sxs-lookup"><span data-stu-id="51afc-105">Options</span></span>  
 <span data-ttu-id="51afc-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="51afc-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="51afc-107">확인란을 사용하여 문자열 함수로 변환할 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-107">Use the check boxes to select the columns to transform using string functions.</span></span> <span data-ttu-id="51afc-108">아래 테이블에 선택 내용이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-108">Your selections appear in the table below.</span></span>  
  
 <span data-ttu-id="51afc-109">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="51afc-109">**Input Column**</span></span>  
 <span data-ttu-id="51afc-110">위 테이블에서 선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-110">View input columns selected from the table above.</span></span> <span data-ttu-id="51afc-111">사용 가능한 입력 열 목록을 사용하여 선택 내용을 변경 또는 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-111">You can also change or remove a selection by using the list of available input columns.</span></span>  
  
 <span data-ttu-id="51afc-112">**대상**</span><span class="sxs-lookup"><span data-stu-id="51afc-112">**Destination**</span></span>  
 <span data-ttu-id="51afc-113">문자열 작업 결과를 기존 열을 사용하여 내부에 저장할지, 아니면 수정된 데이터를 새 열로 저장할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-113">Specify whether to save the results of the string operations in place, using the existing column, or to save the modified data as a new column.</span></span>  
  
|<span data-ttu-id="51afc-114">값</span><span class="sxs-lookup"><span data-stu-id="51afc-114">Value</span></span>|<span data-ttu-id="51afc-115">Description</span><span class="sxs-lookup"><span data-stu-id="51afc-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51afc-116">새 열</span><span class="sxs-lookup"><span data-stu-id="51afc-116">New column</span></span>|<span data-ttu-id="51afc-117">새 열에 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-117">Save the data in a new column.</span></span> <span data-ttu-id="51afc-118">**출력 별칭**의 열 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-118">Assign the column name under **Output Alias**.</span></span>|  
|<span data-ttu-id="51afc-119">내부 변경</span><span class="sxs-lookup"><span data-stu-id="51afc-119">In-place change</span></span>|<span data-ttu-id="51afc-120">수정된 데이터를 기존 열에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-120">Save the modified data in the existing column.</span></span>|  
  
 <span data-ttu-id="51afc-121">**작업**</span><span class="sxs-lookup"><span data-stu-id="51afc-121">**Operation**</span></span>  
 <span data-ttu-id="51afc-122">열 데이터에 적용할 문자열 함수를 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-122">Select from the list the string functions to apply to column data.</span></span>  
  
|<span data-ttu-id="51afc-123">값</span><span class="sxs-lookup"><span data-stu-id="51afc-123">Value</span></span>|<span data-ttu-id="51afc-124">Description</span><span class="sxs-lookup"><span data-stu-id="51afc-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51afc-125">소문자</span><span class="sxs-lookup"><span data-stu-id="51afc-125">Lowercase</span></span>|<span data-ttu-id="51afc-126">소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-126">Convert to lower case.</span></span>|  
|<span data-ttu-id="51afc-127">대문자</span><span class="sxs-lookup"><span data-stu-id="51afc-127">Uppercase</span></span>|<span data-ttu-id="51afc-128">대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-128">Convert to upper case.</span></span>|  
|<span data-ttu-id="51afc-129">바이트 반전</span><span class="sxs-lookup"><span data-stu-id="51afc-129">Byte reversal</span></span>|<span data-ttu-id="51afc-130">바이트 순서를 반대로 바꿔 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-130">Convert by reversing byte order.</span></span>|  
|<span data-ttu-id="51afc-131">히라가나</span><span class="sxs-lookup"><span data-stu-id="51afc-131">Hiragana</span></span>|<span data-ttu-id="51afc-132">일본어 가타카나 문자를 히라가나로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-132">Convert Japanese katakana characters to hiragana.</span></span>|  
|<span data-ttu-id="51afc-133">가타카나</span><span class="sxs-lookup"><span data-stu-id="51afc-133">Katakana</span></span>|<span data-ttu-id="51afc-134">일본어 히라가나 문자를 가타카나로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-134">Convert Japanese hiragana characters to katakana.</span></span>|  
|<span data-ttu-id="51afc-135">반자</span><span class="sxs-lookup"><span data-stu-id="51afc-135">Half width</span></span>|<span data-ttu-id="51afc-136">전자 문자를 반자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-136">Convert full-width characters to half width.</span></span>|  
|<span data-ttu-id="51afc-137">전자</span><span class="sxs-lookup"><span data-stu-id="51afc-137">Full width</span></span>|<span data-ttu-id="51afc-138">반자 문자를 전자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-138">Convert half-width characters to full width.</span></span>|  
|<span data-ttu-id="51afc-139">대/소문자 구분 기능</span><span class="sxs-lookup"><span data-stu-id="51afc-139">Linguistic casing</span></span>|<span data-ttu-id="51afc-140">시스템 규칙 대신 대/소문자 구분 규칙(터키어 및 다른 로캘의 유니코드 단순 대/소문자 구분 매핑)을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-140">Apply linguistic rules of casing (Unicode simple case mapping for Turkic and other locales) instead of the system rules.</span></span>|  
|<span data-ttu-id="51afc-141">중국어(간체)</span><span class="sxs-lookup"><span data-stu-id="51afc-141">Simplified Chinese</span></span>|<span data-ttu-id="51afc-142">중국어 번체 문자를 간체로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-142">Convert traditional Chinese characters to simplified Chinese.</span></span>|  
|<span data-ttu-id="51afc-143">중국어 번체</span><span class="sxs-lookup"><span data-stu-id="51afc-143">Traditional Chinese</span></span>|<span data-ttu-id="51afc-144">중국어 간체 문자를 번체로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-144">Convert simplified Chinese characters to traditional Chinese.</span></span>|  
  
 <span data-ttu-id="51afc-145">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="51afc-145">**Output Alias**</span></span>  
 <span data-ttu-id="51afc-146">각 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-146">Type an alias for each output column.</span></span> <span data-ttu-id="51afc-147">기본값은 **Copy of** 뒤에 입력 열 이름이 오는 형식이지만 설명이 포함된 고유 이름을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-147">The default is **Copy of** followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="51afc-148">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="51afc-148">**Configure Error Output**</span></span>  
 <span data-ttu-id="51afc-149">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 이 변환에 대한 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51afc-149">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51afc-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51afc-150">See Also</span></span>  
 [<span data-ttu-id="51afc-151">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="51afc-151">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
