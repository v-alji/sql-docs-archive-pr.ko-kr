---
title: 용어 조회 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookuptrans.f1
helpviewer_keywords:
- extracting data [Integration Services]
- match extracted terms [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- lookups [Integration Services]
- counting extracted items
- Term Lookup transformation
ms.assetid: 3c0fa2f8-cb6a-4371-b184-7447be001de1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a679f9e191b2b1ec54d982a715085fe5b6bddfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738535"
---
# <a name="term-lookup-transformation"></a><span data-ttu-id="d9469-102">용어 조회 변환</span><span class="sxs-lookup"><span data-stu-id="d9469-102">Term Lookup Transformation</span></span>
  <span data-ttu-id="d9469-103">용어 조회 변환은 변환 입력 열의 텍스트에서 추출된 용어와 참조 테이블에 있는 용어가 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-103">The Term Lookup transformation matches terms extracted from text in a transformation input column with terms in a reference table.</span></span> <span data-ttu-id="d9469-104">그런 다음 조회 테이블의 용어가 입력 데이터 집합에서 발생한 횟수를 계산하고 해당 개수를 참조 테이블의 용어와 함께 변환 출력의 열에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-104">It then counts the number of times a term in the lookup table occurs in the input data set, and writes the count together with the term from the reference table to columns in the transformation output.</span></span> <span data-ttu-id="d9469-105">이러한 변환은 입력 텍스트를 기준으로 단어 빈도 통계가 모두 포함된 사용자 지정 단어 목록을 만들 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-105">This transformation is useful for creating a custom word list based on the input text, complete with word frequency statistics.</span></span>  
  
 <span data-ttu-id="d9469-106">용어 조회 변환은 조회를 수행하기 전에 용어 추출 변환과 동일한 다음과 같은 방식을 사용하여 입력 열의 텍스트에서 단어를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-106">Before the Term Lookup transformation performs a lookup, it extracts words from the text in an input column using the same method as the Term Extraction transformation:</span></span>  
  
-   <span data-ttu-id="d9469-107">텍스트를 여러 문장으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-107">Text is broken into sentences.</span></span>  
  
-   <span data-ttu-id="d9469-108">문장을 여러 단어로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-108">Sentences are broken into words.</span></span>  
  
-   <span data-ttu-id="d9469-109">단어를 기본 형태로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-109">Words are normalized.</span></span>  
  
 <span data-ttu-id="d9469-110">용어 조회 변환에서 대/소문자를 구분하여 일치하는 용어를 검색할 수 있도록 구성하여 용어 검색 방법의 사용자 지정 수위를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-110">To further customize which terms to match, the Term Lookup transformation can be configured to perform a case-sensitive match.</span></span>  
  
## <a name="matches"></a><span data-ttu-id="d9469-111">일치</span><span class="sxs-lookup"><span data-stu-id="d9469-111">Matches</span></span>  
 <span data-ttu-id="d9469-112">용어 조회에서는 조회를 수행하고 다음 규칙에 따라 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-112">The Term Lookup performs a lookup and returns a value using the following rules:</span></span>  
  
-   <span data-ttu-id="d9469-113">대/소문자 구분 검색을 수행하도록 변환이 구성된 경우 대/소문자가 다른 일치 항목은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-113">If the transformation is configured to perform case-sensitive matches, matches that fail a case-sensitive comparison are discarded.</span></span> <span data-ttu-id="d9469-114">예를 들어 *student* 와 *STUDENT* 는 별개의 단어로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-114">For example, *student* and *STUDENT* are treated as separate words.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9469-115">소문자로 표기된 단어는 문장 처음에 대문자로 표시된 단어와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-115">A non-capitalized word can be matched with a word that is capitalized at the beginning of a sentence.</span></span> <span data-ttu-id="d9469-116">예를 들어 *Student* 가 문장의 첫 단어인 경우 *student* 와 *Student* 는 일치하는 단어로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-116">For example, the match between *student* and *Student* succeeds when *Student* is the first word in a sentence.</span></span>  
  
-   <span data-ttu-id="d9469-117">명사 또는 명사구의 복수 형태가 참조 테이블에 있는 경우 조회에서는 명사 또는 명사구의 복수 형태만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-117">If a plural form of the noun or noun phrase exists in the reference table, the lookup matches only the plural form of the noun or noun phrase.</span></span> <span data-ttu-id="d9469-118">예를 들어 모든 *students* 는 *student*와 별개로 카운트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-118">For example, all instances of *students* would be counted separately from the instances of *student*.</span></span>  
  
-   <span data-ttu-id="d9469-119">참조 테이블에 단어의 단수 형태만 있는 경우 단어 또는 구의 단수 및 복수 형태는 모두 단수 형태로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-119">If only the singular form of the word is found in the reference table, both the singular and the plural forms of the word or phrase are matched to the singular form.</span></span> <span data-ttu-id="d9469-120">예를 들어 조회 테이블에 *student*가 있는 경우 변환에서는 *student* 와 *students*가 검색되며, 두 단어 모두 조회 용어 *student*에 일치하는 단어로 카운트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-120">For example, if the lookup table contains *student*, and the transformation finds the words *student* and *students*, both words would be counted as a match for the lookup term *student*.</span></span>  
  
-   <span data-ttu-id="d9469-121">입력 열의 텍스트가 분류된 명사구인 경우 명사구의 마지막 단어만 기본 형태로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-121">If the text in the input column is a lemmatized noun phrase, only the last word in the noun phrase is affected by normalization.</span></span> <span data-ttu-id="d9469-122">예를 들어 *doctors appointments* 의 분류된 형태는 *doctors appointment*입니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-122">For example, the lemmatized version of *doctors appointments* is *doctors appointment*.</span></span>  
  
 <span data-ttu-id="d9469-123">참조 집합에서 겹치는 용어가 조회 항목에 포함되어 있을 경우(즉, 하위 용어가 하나를 초과하는 참조 레코드에 있는 경우) 용어 조회 변환에서는 하나의 조회 결과만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-123">When a lookup item contains terms that overlap in the reference set-that is, a sub-term is found in more than one reference record-the Term Lookup transformation returns only one lookup result.</span></span> <span data-ttu-id="d9469-124">다음 예에서는 겹치는 하위 용어가 조회 항목에 포함되어 있는 때의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-124">The following example shows the result when a lookup item contains an overlapping sub-term.</span></span> <span data-ttu-id="d9469-125">이 경우 겹치는 하위 용어는 *Windows*이며 두 개의 참조 용어에 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-125">The overlapping sub-term in this case is *Windows*, which is found within two reference terms.</span></span> <span data-ttu-id="d9469-126">그러나 변환에서는 두 개의 결과를 반환하지 않고 *Windows*라는 하나의 참조 용어만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-126">However, the transformation does not return two results, but returns only a single reference term, *Windows*.</span></span> <span data-ttu-id="d9469-127">두 번째 참조 용어인 *Windows 7 Professional*은 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-127">The second reference term, *Windows 7 Professional*, is not returned.</span></span>  
  
|<span data-ttu-id="d9469-128">항목</span><span class="sxs-lookup"><span data-stu-id="d9469-128">Item</span></span>|<span data-ttu-id="d9469-129">값</span><span class="sxs-lookup"><span data-stu-id="d9469-129">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d9469-130">입력 용어</span><span class="sxs-lookup"><span data-stu-id="d9469-130">Input term</span></span>|<span data-ttu-id="d9469-131">Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="d9469-131">Windows 7 Professional</span></span>|  
|<span data-ttu-id="d9469-132">참조 용어</span><span class="sxs-lookup"><span data-stu-id="d9469-132">Reference terms</span></span>|<span data-ttu-id="d9469-133">Windows, Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="d9469-133">Windows, Windows 7 Professional</span></span>|  
|<span data-ttu-id="d9469-134">출력</span><span class="sxs-lookup"><span data-stu-id="d9469-134">Output</span></span>|<span data-ttu-id="d9469-135">Windows</span><span class="sxs-lookup"><span data-stu-id="d9469-135">Windows</span></span>|  
  
 <span data-ttu-id="d9469-136">용어 조회 변환에서는 특수 문자가 포함된 명사 및 명사구를 검색할 수 있으며 참조 테이블의 데이터에는 이러한 문자가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-136">The Term Lookup transformation can match nouns and noun phrases that contain special characters, and the data in the reference table may include these characters.</span></span> <span data-ttu-id="d9469-137">%, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", ' 등이 특수 문자에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-137">The special characters are as follows: %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="d9469-138">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d9469-138">Data Types</span></span>  
 <span data-ttu-id="d9469-139">용어 조회 변환에서는 데이터 형식이 DT_WSTR 또는 DT_NTEXT인 열만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-139">The Term Lookup transformation can only use a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="d9469-140">열에 텍스트가 있지만 데이터 형식이 다른 경우 데이터 변환으로 데이터 흐름에 DT_WSTR 또는 DT_NTEXT 데이터 형식의 열을 추가하고 열 값을 새 열로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-140">If a column contains text, but does not have one of these data types, the Data Conversion transformation can add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="d9469-141">그런 다음 데이터 변환의 출력을 용어 조회 변환에 대한 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-141">The output from the Data Conversion transformation can then be used as the input to the Term Lookup transformation.</span></span> <span data-ttu-id="d9469-142">자세한 내용은 [Data Conversion Transformation](data-conversion-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9469-142">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="configuration-the-term-lookup-transformation"></a><span data-ttu-id="d9469-143">용어 조회 변환 구성</span><span class="sxs-lookup"><span data-stu-id="d9469-143">Configuration the Term Lookup Transformation</span></span>  
 <span data-ttu-id="d9469-144">용어 조회 변환 입력 열에는 열의 용도를 나타내는 InputColumnType 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-144">The Term Lookup transformation input columns includes the InputColumnType property, which indicates the use of the column.</span></span> <span data-ttu-id="d9469-145">InputColumnType에는 다음 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-145">InputColumnType can contain the following values:</span></span>  
  
-   <span data-ttu-id="d9469-146">값 0은 열이 출력에만 전달되며 조회에서 사용되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-146">The value 0 indicates the column is passed through to the output only and is not used in the lookup.</span></span>  
  
-   <span data-ttu-id="d9469-147">값 1은 열이 조회에서만 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-147">The value 1 indicates the column is used in the lookup only.</span></span>  
  
-   <span data-ttu-id="d9469-148">값 2는 열이 출력에 전달되고 조회에서도 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-148">The value 2 indicates the column is passed through to the output, and is also used in the lookup.</span></span>  
  
 <span data-ttu-id="d9469-149">InputColumnType 속성이 0이나 2로 설정된 변환 출력 열에는 업스트림 데이터 흐름 구성 요소에 의해 열에 할당된 계보 식별자를 포함하는 열에 대한 CustomLineageID 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-149">Transformation output columns whose InputColumnType property is set to 0 or 2 include the CustomLineageID property for a column, which contains the lineage identifier assigned to the column by an upstream data flow component.</span></span>  
  
 <span data-ttu-id="d9469-150">용어 조회 변환은 변환 출력에 기본적으로 `Term`과 `Frequency`라는 두 개의 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-150">The Term Lookup transformation adds two columns to the transformation output, named by default `Term` and `Frequency`.</span></span> <span data-ttu-id="d9469-151">`Term`은 조회 테이블의 용어를 포함하고 `Frequency`는 참조 테이블의 용어가 입력 데이터 집합에서 발생한 횟수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-151">`Term` contains a term from the lookup table and `Frequency` contains the number of times the term in the reference table occurs in the input data set.</span></span> <span data-ttu-id="d9469-152">이러한 열에는 CustomLineageID 속성이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-152">These columns do not include the CustomLineageID property.</span></span>  
  
 <span data-ttu-id="d9469-153">조회 테이블은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 Access 데이터베이스의 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-153">The lookup table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="d9469-154">용어 추출 변환의 출력이 테이블에 저장되는 경우 이 테이블을 참조 테이블로 사용할 수 있지만 다른 테이블도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-154">If the output of the Term Extraction transformation is saved to a table, this table can be used as the reference table, but other tables can also be used.</span></span> <span data-ttu-id="d9469-155">플랫 파일, Excel 통합 문서 또는 다른 원본에 있는 텍스트는 용어 조회 변환을 사용하기 전에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스나 Access 데이터베이스로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-155">Text in flat files, Excel workbooks or other sources must be imported to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database or an Access database before you can use the Term Lookup transformation.</span></span>  
  
 <span data-ttu-id="d9469-156">용어 조회 변환은 별개의 OLE DB 연결을 사용하여 참조 테이블에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-156">The Term Lookup transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="d9469-157">자세한 내용은 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9469-157">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d9469-158">용어 조회 변환은 완전히 사전 캐시된 모드에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-158">The Term Lookup transformation works in a fully precached mode.</span></span> <span data-ttu-id="d9469-159">용어 조회 변환은 런타임에 참조 테이블로부터 용어를 읽고 변환 입력 행을 처리하기 전에 이를 프라이빗 메모리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-159">At run time, the Term Lookup transformation reads the terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
 <span data-ttu-id="d9469-160">입력 열 행의 용어는 반복될 수 있기 때문에 용어 조회 변환의 출력에는 일반적으로 변환 입력보다 많은 수의 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-160">Because the terms in an input column row may repeat, the output of the Term Lookup transformation typically has more rows than the transformation input.</span></span>  
  
 <span data-ttu-id="d9469-161">이 변환에는 하나의 입력과 하나의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-161">The transformation has one input and one output.</span></span> <span data-ttu-id="d9469-162">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-162">It does not support error outputs.</span></span>  
  
 <span data-ttu-id="d9469-163">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9469-163">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d9469-164">**용어 조회 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9469-164">For more information about the properties that you can set in the **Term Lookup Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d9469-165">용어 조회 변환 편집기&#40;참조 테이블 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="d9469-165">Term Lookup Transformation Editor &#40;Reference Table Tab&#41;</span></span>](../../term-lookup-transformation-editor-reference-table-tab.md)  
  
-   [<span data-ttu-id="d9469-166">용어 조회 변환 편집기&#40;용어 조회 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="d9469-166">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
-   [<span data-ttu-id="d9469-167">용어 조회 변환 편집기&#40;고급 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="d9469-167">Term Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-lookup-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="d9469-168">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d9469-168">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d9469-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d9469-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="d9469-170">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="d9469-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="d9469-171">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9469-171">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
