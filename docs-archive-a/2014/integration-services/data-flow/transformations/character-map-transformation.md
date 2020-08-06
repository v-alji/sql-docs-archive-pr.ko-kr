---
title: 문자표 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactertrans.f1
helpviewer_keywords:
- mutually exclusive mapping [Integration Services]
- mapping data [Integration Services]
- string functions
- Character Map transformation [Integration Services]
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5fc31e1a3500a7a7b023e43a968e70e5b438dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652241"
---
# <a name="character-map-transformation"></a><span data-ttu-id="35dfa-102">문자표 변환</span><span class="sxs-lookup"><span data-stu-id="35dfa-102">Character Map Transformation</span></span>
  <span data-ttu-id="35dfa-103">문자표 변환은 소문자에서 대문자로의 변환과 같은 문자열 함수를 문자 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-103">The Character Map transformation applies string functions, such as conversion from lowercase to uppercase, to character data.</span></span> <span data-ttu-id="35dfa-104">이 변환은 문자열 데이터 형식의 열 데이터에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-104">This transformation operates only on column data with a string data type.</span></span>  
  
 <span data-ttu-id="35dfa-105">문자표 변환은 사용 중인 열 데이터를 변환하거나 열을 변환 출력에 추가하고 변환된 데이터를 새 열에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-105">The Character Map transformation can convert column data in place or add a column to the transformation output and put the converted data in the new column.</span></span> <span data-ttu-id="35dfa-106">다양한 매핑 작업 집합을 동일한 입력 열에 적용하고 결과를 다른 열에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-106">You can apply different sets of mapping operations to the same input column and put the results in different columns.</span></span> <span data-ttu-id="35dfa-107">예를 들어 동일한 열을 대문자와 소문자로 변환하고 결과를 두 개의 서로 다른 열에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-107">For example, you can convert the same column to uppercase and lowercase and put the results in two different columns.</span></span>  
  
 <span data-ttu-id="35dfa-108">매핑으로 인해 데이터가 잘리는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-108">Mapping can, under some circumstances, cause data to be truncated.</span></span> <span data-ttu-id="35dfa-109">예를 들어 싱글바이트 문자를 멀티바이트 표현 문자로 매핑하면 데이터가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-109">For example, truncation can occur when single-byte characters are mapped to characters with a multibyte representation.</span></span> <span data-ttu-id="35dfa-110">문자표 변환에는 잘린 데이터를 별도의 출력으로 보내는 데 사용할 수 있는 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-110">The Character Map transformation includes an error output, which can be used to direct truncated data to separate output.</span></span> <span data-ttu-id="35dfa-111">자세한 내용은 [데이터 오류 처리](../error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35dfa-111">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="35dfa-112">이 변환에는 하나의 입력, 하나의 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-112">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="mapping-operations"></a><span data-ttu-id="35dfa-113">매핑 작업</span><span class="sxs-lookup"><span data-stu-id="35dfa-113">Mapping Operations</span></span>  
 <span data-ttu-id="35dfa-114">다음 표에서는 문자표 변환이 지원하는 매핑 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-114">The following table describes the mapping operations that the Character Map transformation supports.</span></span>  
  
|<span data-ttu-id="35dfa-115">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="35dfa-115">Operation</span></span>|<span data-ttu-id="35dfa-116">Description</span><span class="sxs-lookup"><span data-stu-id="35dfa-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35dfa-117">바이트 반전</span><span class="sxs-lookup"><span data-stu-id="35dfa-117">Byte reversal</span></span>|<span data-ttu-id="35dfa-118">바이트 순서를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-118">Reverses byte order.</span></span>|  
|<span data-ttu-id="35dfa-119">전자</span><span class="sxs-lookup"><span data-stu-id="35dfa-119">Full width</span></span>|<span data-ttu-id="35dfa-120">반자 문자를 전자 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-120">Maps half-width characters to full-width characters.</span></span>|  
|<span data-ttu-id="35dfa-121">반자</span><span class="sxs-lookup"><span data-stu-id="35dfa-121">Half width</span></span>|<span data-ttu-id="35dfa-122">전자 문자를 반자 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-122">Maps full-width characters to half-width characters.</span></span>|  
|<span data-ttu-id="35dfa-123">히라가나</span><span class="sxs-lookup"><span data-stu-id="35dfa-123">Hiragana</span></span>|<span data-ttu-id="35dfa-124">가타카나 문자를 히라가나 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-124">Maps katakana characters to hiragana characters.</span></span>|  
|<span data-ttu-id="35dfa-125">가타카나</span><span class="sxs-lookup"><span data-stu-id="35dfa-125">Katakana</span></span>|<span data-ttu-id="35dfa-126">히라가나 문자를 가타카나 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-126">Maps hiragana characters to katakana characters.</span></span>|  
|<span data-ttu-id="35dfa-127">대/소문자 구분 기능</span><span class="sxs-lookup"><span data-stu-id="35dfa-127">Linguistic casing</span></span>|<span data-ttu-id="35dfa-128">시스템 규칙 대신 대/소문자 구분 기능을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-128">Applies linguistic casing instead of the system rules.</span></span> <span data-ttu-id="35dfa-129">대/소문자 구분 기능은 터키어 및 다른 로캘의 유니코드 단순 대/소문자 구분 매핑을 위해 Win32 API에서 제공하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-129">Linguistic casing refers to functionality provided by the Win32 API for Unicode simple case mapping of Turkic and other locales.</span></span>|  
|<span data-ttu-id="35dfa-130">소문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-130">Lowercase</span></span>|<span data-ttu-id="35dfa-131">문자를 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-131">Converts characters to lowercase.</span></span>|  
|<span data-ttu-id="35dfa-132">중국어(간체)</span><span class="sxs-lookup"><span data-stu-id="35dfa-132">Simplified Chinese</span></span>|<span data-ttu-id="35dfa-133">중국어 번체 문자를 중국어 간체 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-133">Maps traditional Chinese characters to simplified Chinese characters.</span></span>|  
|<span data-ttu-id="35dfa-134">중국어 번체</span><span class="sxs-lookup"><span data-stu-id="35dfa-134">Traditional Chinese</span></span>|<span data-ttu-id="35dfa-135">중국어 간체 문자를 중국어 번체 문자에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-135">Maps simplified Chinese characters to traditional Chinese characters.</span></span>|  
|<span data-ttu-id="35dfa-136">대문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-136">Uppercase</span></span>|<span data-ttu-id="35dfa-137">문자를 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-137">Converts characters to uppercase.</span></span>|  
  
## <a name="mutually-exclusive-mapping-operations"></a><span data-ttu-id="35dfa-138">상호 배타적인 매핑 작업</span><span class="sxs-lookup"><span data-stu-id="35dfa-138">Mutually Exclusive Mapping Operations</span></span>  
 <span data-ttu-id="35dfa-139">한 변환에서 둘 이상의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-139">More than one operation can be performed in a transformation.</span></span> <span data-ttu-id="35dfa-140">그러나 일부 매핑 작업은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-140">However, some mapping operations are mutually exclusive.</span></span> <span data-ttu-id="35dfa-141">다음 표에서는 동일한 열에 여러 개의 작업을 사용할 때 적용되는 제한을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-141">The following table lists restrictions that apply when you use multiple operations on the same column.</span></span> <span data-ttu-id="35dfa-142">작업 A 열과 작업 B 열의 작업은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-142">Operations in the columns Operation A and Operation B are mutually exclusive.</span></span>  
  
|<span data-ttu-id="35dfa-143">작업 A</span><span class="sxs-lookup"><span data-stu-id="35dfa-143">Operation A</span></span>|<span data-ttu-id="35dfa-144">작업 B</span><span class="sxs-lookup"><span data-stu-id="35dfa-144">Operation B</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="35dfa-145">소문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-145">Lowercase</span></span>|<span data-ttu-id="35dfa-146">대문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-146">Uppercase</span></span>|  
|<span data-ttu-id="35dfa-147">히라가나</span><span class="sxs-lookup"><span data-stu-id="35dfa-147">Hiragana</span></span>|<span data-ttu-id="35dfa-148">가타카나</span><span class="sxs-lookup"><span data-stu-id="35dfa-148">Katakana</span></span>|  
|<span data-ttu-id="35dfa-149">반자</span><span class="sxs-lookup"><span data-stu-id="35dfa-149">Half width</span></span>|<span data-ttu-id="35dfa-150">전자</span><span class="sxs-lookup"><span data-stu-id="35dfa-150">Full width</span></span>|  
|<span data-ttu-id="35dfa-151">중국어 번체</span><span class="sxs-lookup"><span data-stu-id="35dfa-151">Traditional Chinese</span></span>|<span data-ttu-id="35dfa-152">중국어(간체)</span><span class="sxs-lookup"><span data-stu-id="35dfa-152">Simplified Chinese</span></span>|  
|<span data-ttu-id="35dfa-153">소문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-153">Lowercase</span></span>|<span data-ttu-id="35dfa-154">히라가나, 가타카나, 반자, 전자</span><span class="sxs-lookup"><span data-stu-id="35dfa-154">Hiragana, katakana, half width, full width</span></span>|  
|<span data-ttu-id="35dfa-155">대문자</span><span class="sxs-lookup"><span data-stu-id="35dfa-155">Uppercase</span></span>|<span data-ttu-id="35dfa-156">히라가나, 가타카나, 반자, 전자</span><span class="sxs-lookup"><span data-stu-id="35dfa-156">Hiragana, katakana, half width, full width</span></span>|  
  
## <a name="configuration-of-the-character-map-transformation"></a><span data-ttu-id="35dfa-157">문자표 변환 구성</span><span class="sxs-lookup"><span data-stu-id="35dfa-157">Configuration of the Character Map Transformation</span></span>  
 <span data-ttu-id="35dfa-158">다음과 같은 방법으로 문자표 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-158">You configure the Character Map transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="35dfa-159">변환할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-159">Specify the columns to convert.</span></span>  
  
-   <span data-ttu-id="35dfa-160">각 열에 적용할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-160">Specify the operations to apply to each column.</span></span>  
  
 <span data-ttu-id="35dfa-161">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-161">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="35dfa-162">**문자표 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Character Map Transformation Editor](../../character-map-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="35dfa-162">For more information about the properties that you can set in the **Character Map Transformation Editor** dialog box, see [Character Map Transformation Editor](../../character-map-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="35dfa-163">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35dfa-163">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="35dfa-164">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="35dfa-164">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="35dfa-165">Common Properties</span><span class="sxs-lookup"><span data-stu-id="35dfa-165">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="35dfa-166">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="35dfa-166">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="35dfa-167">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="35dfa-167">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="35dfa-168">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="35dfa-168">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="35dfa-169">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="35dfa-169">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  
