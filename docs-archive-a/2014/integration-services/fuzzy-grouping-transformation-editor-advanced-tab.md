---
title: 유사 항목 그룹화 변환 편집기 (고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f5dd05eda56b4818914f659734eb3cdfb20c4d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648437"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a><span data-ttu-id="dc694-102">유사 항목 그룹화 변환 편집기(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="dc694-102">Fuzzy Grouping Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="dc694-103">**유사 항목 그룹화 변환 편집기** 대화 상자의 **고급** 탭을 사용하여 입/출력 열을 지정하고, 유사성 임계값을 설정하고, 구분 기호를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-103">Use the **Advanced** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify input and output columns, set similarity thresholds, and define delimiters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc694-104">유사 `Exhaustive` `MaxMemoryUsage` 항목 그룹화 변환의 및 속성은 **유사 항목 그룹화 변환 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-104">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Grouping transformation are not available in the **Fuzzy Grouping Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="dc694-105">이러한 속성에 대한 자세한 내용은 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)의 유사 항목 그룹화 변환 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc694-105">For more information on these properties, see the Fuzzy Grouping Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="dc694-106">유사 항목 그룹화 변환에 대한 자세한 내용은 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc694-106">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dc694-107">옵션</span><span class="sxs-lookup"><span data-stu-id="dc694-107">Options</span></span>  
 <span data-ttu-id="dc694-108">**입력 키 열 이름**</span><span class="sxs-lookup"><span data-stu-id="dc694-108">**Input key column name**</span></span>  
 <span data-ttu-id="dc694-109">각 입력 행에 대한 고유 식별자를 포함하는 출력 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-109">Specify the name of an output column that contains the unique identifier for each input row.</span></span> <span data-ttu-id="dc694-110">`_key_in` 열에는 각 행을 고유하게 식별하는 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-110">The `_key_in` column has a value that uniquely identifies each row.</span></span>  
  
 <span data-ttu-id="dc694-111">**출력 키 열 이름**</span><span class="sxs-lookup"><span data-stu-id="dc694-111">**Output key column name**</span></span>  
 <span data-ttu-id="dc694-112">중복 행 그룹의 정식 행에 대한 고유 식별자를 포함하는 출력 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-112">Specify the name of an output column that contains the unique identifier for the canonical row of a group of duplicate rows.</span></span> <span data-ttu-id="dc694-113">`_key_out` 열은 정식 데이터 행의 `_key_in` 값에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-113">The `_key_out` column corresponds to the `_key_in` value of the canonical data row.</span></span>  
  
 <span data-ttu-id="dc694-114">**유사성 점수 열 이름**</span><span class="sxs-lookup"><span data-stu-id="dc694-114">**Similarity score column name**</span></span>  
 <span data-ttu-id="dc694-115">유사성 점수를 포함하는 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-115">Specify a name for the column that contains the similarity score.</span></span> <span data-ttu-id="dc694-116">유사성 점수는 입력 행과 정식 행의 유사성을 나타내는 0과 1 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-116">The similarity score is a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span> <span data-ttu-id="dc694-117">정식 행과 더 비슷하게 일치할수록 점수가 1에 가까워집니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-117">The closer the score is to 1, the more closely the row matches the canonical row.</span></span>  
  
 <span data-ttu-id="dc694-118">**유사성 임계값**</span><span class="sxs-lookup"><span data-stu-id="dc694-118">**Similarity threshold**</span></span>  
 <span data-ttu-id="dc694-119">슬라이더를 사용하여 유사성 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-119">Set the similarity threshold by using the slider.</span></span> <span data-ttu-id="dc694-120">임계값이 1에 가까울수록 두 행이 보다 유사하여 중복으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-120">The closer the threshold is to 1, the more the rows must resemble each other to qualify as duplicates.</span></span> <span data-ttu-id="dc694-121">임계값을 높이면 고려할 레코드 수가 감소하기 때문에 비교 속도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-121">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="dc694-122">**토큰 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="dc694-122">**Token delimiters**</span></span>  
 <span data-ttu-id="dc694-123">변환에서 데이터 토큰화에 사용할 수 있는 기본 구분 기호 집합을 제공하지만 필요에 따라 목록을 편집하여 구분 기호를 추가 또는 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc694-123">The transformation provides a default set of delimiters for tokenizing data, but you can add or remove delimiters as needed by editing the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc694-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc694-124">See Also</span></span>  
 <span data-ttu-id="dc694-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dc694-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="dc694-126">유사 항목 그룹화 변환을 사용하여 유사한 데이터 행 식별</span><span class="sxs-lookup"><span data-stu-id="dc694-126">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
