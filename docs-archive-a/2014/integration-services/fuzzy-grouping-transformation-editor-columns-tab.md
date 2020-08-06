---
title: 유사 항목 그룹화 변환 편집기 (열 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.columns.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 24f4539f-2a9f-4acd-acc7-06228a07f7df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d3aef9c30a81760b7f09378a8ecd66fee0dac62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729628"
---
# <a name="fuzzy-grouping-transformation-editor-columns-tab"></a><span data-ttu-id="94773-102">유사 항목 그룹화 변환 편집기(열 탭)</span><span class="sxs-lookup"><span data-stu-id="94773-102">Fuzzy Grouping Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="94773-103">**유사 항목 그룹화 변환 편집기** 대화 상자의 **열** 탭을 사용하여 중복 값을 가진 행을 그룹화하는 데 사용할 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-103">Use the **Columns** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify the columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="94773-104">유사 항목 그룹화 변환에 대한 자세한 내용은 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="94773-104">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="94773-105">옵션</span><span class="sxs-lookup"><span data-stu-id="94773-105">Options</span></span>  
 <span data-ttu-id="94773-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="94773-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="94773-107">중복 값을 가진 행을 그룹화하는 데 사용할 입력 열을 이 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-107">Select from this list the input columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="94773-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="94773-108">**Name**</span></span>  
 <span data-ttu-id="94773-109">사용 가능한 입력 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-109">View the names of available input columns.</span></span>  
  
 <span data-ttu-id="94773-110">**통과**</span><span class="sxs-lookup"><span data-stu-id="94773-110">**Pass Through**</span></span>  
 <span data-ttu-id="94773-111">입력 열을 변환의 출력에 포함할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-111">Select whether to include the input column in the output of the transformation.</span></span> <span data-ttu-id="94773-112">그룹화에 사용되는 모든 열이 자동으로 출력에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="94773-112">All columns used for grouping are automatically copied to the output.</span></span> <span data-ttu-id="94773-113">이 열을 선택하여 추가 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-113">You can include additional columns by checking this column.</span></span>  
  
 <span data-ttu-id="94773-114">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="94773-114">**Input Column**</span></span>  
 <span data-ttu-id="94773-115">**사용 가능한 입력 열** 목록에서 이전에 선택한 입력 열 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-115">Select one of the input columns selected earlier in the **Available Input Columns** list.</span></span>  
  
 <span data-ttu-id="94773-116">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="94773-116">**Output Alias**</span></span>  
 <span data-ttu-id="94773-117">해당 출력 열을 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-117">Enter a descriptive name for the corresponding output column.</span></span> <span data-ttu-id="94773-118">기본적으로 출력 열 이름은 입력 열 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-118">By default, the output column name is the same as the input column name.</span></span>  
  
 <span data-ttu-id="94773-119">**그룹 출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="94773-119">**Group Output Alias**</span></span>  
 <span data-ttu-id="94773-120">그룹화된 중복의 정식 값이 포함될 열을 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-120">Enter a descriptive name for the column that will contain the canonical value for the grouped duplicates.</span></span> <span data-ttu-id="94773-121">이 출력 열의 기본 이름은 입력 열 이름에 _clean이 추가된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="94773-121">The default name of this output column is the input column name with _clean appended.</span></span>  
  
 <span data-ttu-id="94773-122">**일치 유형**</span><span class="sxs-lookup"><span data-stu-id="94773-122">**Match Type**</span></span>  
 <span data-ttu-id="94773-123">유사 항목 일치 또는 정확히 일치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-123">Select fuzzy or exact matching.</span></span> <span data-ttu-id="94773-124">유사 항목 일치 유형에서 모든 열이 충분히 유사할 경우 중복 행으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="94773-124">Rows are considered duplicates if they are sufficiently similar across all columns with a fuzzy match type.</span></span> <span data-ttu-id="94773-125">또한 특정 열에 대해 정확히 일치를 지정하면 정확히 일치 열에 동일한 값이 포함된 행만 중복 가능한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="94773-125">If you also specify exact matching on certain columns, only rows that contain identical values in the exact matching columns are considered as possible duplicates.</span></span> <span data-ttu-id="94773-126">따라서 특정 열에 확실하게 오류 없음이나 불일치가 포함되어 있으면 해당 열에 대해 정확히 일치를 지정하여 다른 열에 대한 유사 항목 일치의 정확도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-126">Therefore, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column to increase the accuracy of the fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="94773-127">**최소 유사성**</span><span class="sxs-lookup"><span data-stu-id="94773-127">**Minimum Similarity**</span></span>  
 <span data-ttu-id="94773-128">슬라이더를 사용하여 조인 수준에서 유사성 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-128">Set the similarity threshold at the join level by using the slider.</span></span> <span data-ttu-id="94773-129">값이 1에 가까울수록 조회 값과 원본 값이 근접하여 일치 항목으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="94773-129">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="94773-130">임계값을 높이면 고려할 레코드 수가 감소하기 때문에 비교 속도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-130">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="94773-131">**유사성 출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="94773-131">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="94773-132">선택한 조인에 대한 유사성 점수가 포함된 새 출력 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-132">Specify the name for a new output column that contains the similarity scores for the selected join.</span></span> <span data-ttu-id="94773-133">이 값을 비워 놓으면 출력 열이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-133">If you leave this value empty, the output column is not created.</span></span>  
  
 <span data-ttu-id="94773-134">**숫자**</span><span class="sxs-lookup"><span data-stu-id="94773-134">**Numerals**</span></span>  
 <span data-ttu-id="94773-135">열 데이터 비교 시 선행 및 후행 숫자의 의미를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="94773-135">Specify the significance of leading and trailing numerals in comparing the column data.</span></span> <span data-ttu-id="94773-136">예를 들어 선행 숫자가 의미가 있을 경우 "123 Main Street"는 "456 Main Street"와 그룹화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-136">For example, if leading numerals are significant, "123 Main Street" will not be grouped with "456 Main Street."</span></span>  
  
|<span data-ttu-id="94773-137">값</span><span class="sxs-lookup"><span data-stu-id="94773-137">Value</span></span>|<span data-ttu-id="94773-138">Description</span><span class="sxs-lookup"><span data-stu-id="94773-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94773-139">**Neither**</span><span class="sxs-lookup"><span data-stu-id="94773-139">**Neither**</span></span>|<span data-ttu-id="94773-140">선행 및 후행 숫자 모두 의미가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-140">Leading and trailing numerals are not significant.</span></span>|  
|<span data-ttu-id="94773-141">**붙지**</span><span class="sxs-lookup"><span data-stu-id="94773-141">**Leading**</span></span>|<span data-ttu-id="94773-142">선행 숫자만 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-142">Only leading numerals are significant.</span></span>|  
|<span data-ttu-id="94773-143">**Trailing**</span><span class="sxs-lookup"><span data-stu-id="94773-143">**Trailing**</span></span>|<span data-ttu-id="94773-144">후행 숫자만 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-144">Only trailing numerals are significant.</span></span>|  
|<span data-ttu-id="94773-145">**LeadingAndTrailing**</span><span class="sxs-lookup"><span data-stu-id="94773-145">**LeadingAndTrailing**</span></span>|<span data-ttu-id="94773-146">선행 및 후행 숫자 모두 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94773-146">Both leading and trailing numerals are significant.</span></span>|  
  
 <span data-ttu-id="94773-147">**비교 플래그**</span><span class="sxs-lookup"><span data-stu-id="94773-147">**Comparison Flags**</span></span>  
 <span data-ttu-id="94773-148">문자열 비교 옵션에 대한 자세한 내용은 [문자열 데이터 비교](data-flow/comparing-string-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94773-148">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94773-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94773-149">See Also</span></span>  
 <span data-ttu-id="94773-150">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="94773-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="94773-151">유사 항목 그룹화 변환을 사용하여 유사한 데이터 행 식별</span><span class="sxs-lookup"><span data-stu-id="94773-151">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
