---
title: 용어 추출 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextractiontrans.f1
helpviewer_keywords:
- word boundaries [Integration Services]
- extracting data [Integration Services]
- sentence boundaries
- word extractions [Integration Services]
- Term Extraction transformation
- tagging words
- normalized data [Integration Services]
- tokenizing text [Integration Services]
- parts of speech [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- stemming words [Integration Services]
ms.assetid: d0821526-1603-4ea6-8322-2d901568fbeb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8215b53de7da43bbdbcbe29a9bb7f5ad8edc0d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738542"
---
# <a name="term-extraction-transformation"></a><span data-ttu-id="e536a-102">용어 추출 변환</span><span class="sxs-lookup"><span data-stu-id="e536a-102">Term Extraction Transformation</span></span>
  <span data-ttu-id="e536a-103">용어 추출 변환은 변환 입력 열의 텍스트에서 용어를 추출한 후 용어를 변환 출력 열에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-103">The Term Extraction transformation extracts terms from text in a transformation input column, and then writes the terms to a transformation output column.</span></span> <span data-ttu-id="e536a-104">변환은 영어 텍스트에서만 작동되며 자체 영어 사전과 영어에 대한 언어적 정보가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-104">The transformation works only with English text and it uses its own English dictionary and linguistic information about English.</span></span>  
  
 <span data-ttu-id="e536a-105">용어 추출 변환을 사용하면 데이터 집합의 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-105">You can use the Term Extraction transformation to discover the content of a data set.</span></span> <span data-ttu-id="e536a-106">예를 들어 전자 메일 메시지가 포함된 텍스트는 제품에 대한 유용한 피드백을 제공할 수 있으므로 용어 추출 변환을 사용하여 메시지의 주요 내용을 추출하고 고객 의견을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-106">For example, text that contains e-mail messages may provide useful feedback about products, so that you could use the Term Extraction transformation to extract the topics of discussion in the messages, as a way of analyzing the feedback.</span></span>  
  
## <a name="extracted-terms-and-data-types"></a><span data-ttu-id="e536a-107">추출된 용어 및 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e536a-107">Extracted Terms and Data Types</span></span>  
 <span data-ttu-id="e536a-108">용어 추출 변환에서는 명사 또는 명사구를 따로 추출하거나 모두 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-108">The Term Extraction transformation can extract nouns only, noun phrases only, or both nouns and noun phases.</span></span> <span data-ttu-id="e536a-109">명사는 단일 명사이며, 명사구는 하나의 명사와 명사 또는 형용사를 포함하는 두 개 이상의 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-109">A noun is a single noun; a noun phrases is at least two words, of which one is a noun and the other is a noun or an adjective.</span></span> <span data-ttu-id="e536a-110">예를 들어 명사만 추출하는 옵션이 사용된 경우에는 변환에서 *bicycle* 및 *landscape*등과 같은 용어가 추출되며 명사구 옵션이 사용된 경우에는 *new blue bicycle*, *bicycle helmet*및 *boxed bicycles*와 같은 용어가 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-110">For example, if the transformation uses the nouns-only option, it extracts terms like *bicycle* and *landscape*; if the transformation uses the noun phrase option, it extracts terms like *new blue bicycle*, *bicycle helmet*, and *boxed bicycles*.</span></span>  
  
 <span data-ttu-id="e536a-111">관사와 대명사는 추출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-111">Articles and pronouns are not extracted.</span></span> <span data-ttu-id="e536a-112">예를 들어 용어 추출 변환은 *the bicycle* , *my bicycle*및 *that bicycle*에서 *bicycle*을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-112">For example, the Term Extraction transformation extracts the term *bicycle* from the text *the bicycle*, *my bicycle*, and *that bicycle*.</span></span>  
  
 <span data-ttu-id="e536a-113">용어 추출 변환은 추출되는 각 용어에 대한 순위를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-113">The Term Extraction transformation generates a score for each term that it extracts.</span></span> <span data-ttu-id="e536a-114">순위는 TFIDF 값이나 입력에서 기본 용어가 나타나는 횟수를 의미하는 기본 빈도일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-114">The score can be either a TFIDF value or the raw frequency, meaning the number of times the normalized term appears in the input.</span></span> <span data-ttu-id="e536a-115">어느 경우에도 순위는 0 이상의 실수로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-115">In either case, the score is represented by a real number that is greater than 0.</span></span> <span data-ttu-id="e536a-116">예를 들어 TFIDF 순위 값이 0.5이거나 빈도 값이 1.0 또는 2.0일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-116">For example, the TFIDF score might have the value 0.5, and the frequency would be a value like 1.0 or 2.0.</span></span>  
  
 <span data-ttu-id="e536a-117">용어 추출 변환의 출력에는 두 개의 열만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-117">The output of the Term Extraction transformation includes only two columns.</span></span> <span data-ttu-id="e536a-118">한 열에는 추출된 용어가 포함되고 다른 열에는 순위가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-118">One column contains the extracted terms and the other column contains the score.</span></span> <span data-ttu-id="e536a-119">열의 기본 이름은 **Term** 및 `Score` 입니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-119">The default names of the columns are **Term** and `Score`.</span></span> <span data-ttu-id="e536a-120">입력의 텍스트 열에는 여러 용어가 포함될 수 있기 때문에 용어 추출 변환의 출력에는 일반적으로 입력보다 많은 개수의 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-120">Because the text column in the input may contain multiple terms, the output of the Term Extraction transformation typically has more rows than the input.</span></span>  
  
 <span data-ttu-id="e536a-121">추출된 용어를 테이블에 기록하는 경우에는 용어 조회, 유사 항목 조회 및 조회 변환과 같은 다른 조회 변환에서 해당 용어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-121">If the extracted terms are written to a table, they can be used by other lookup transformation such as the Term Lookup, Fuzzy Lookup, and Lookup transformations.</span></span>  
  
 <span data-ttu-id="e536a-122">용어 추출 변환에서는 데이터 형식이 DT_WSTR 또는 DT_NTEXT인 열의 텍스트만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-122">The Term Extraction transformation can work only with text in a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="e536a-123">열에 텍스트가 있지만 데이터 형식이 다른 경우 데이터 변환으로 데이터 흐름에 DT_WSTR 또는 DT_NTEXT 데이터 형식의 열을 추가하고 열 값을 새 열로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-123">If a column contains text but does not have one of these data types, the Data Conversion transformation can be used to add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="e536a-124">그런 다음 데이터 변환의 출력을 용어 추출 변환에 대한 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-124">The output from the Data Conversion transformation can then be used as the input to the Term Extraction transformation.</span></span> <span data-ttu-id="e536a-125">자세한 내용은 [Data Conversion Transformation](data-conversion-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-125">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="exclusion-terms"></a><span data-ttu-id="e536a-126">제외 용어</span><span class="sxs-lookup"><span data-stu-id="e536a-126">Exclusion Terms</span></span>  
 <span data-ttu-id="e536a-127">선택적으로 용어 추출 변환은 데이터 집합에서 용어를 추출할 때 건너뛸 수 있는 용어를 의미하는 제외 용어가 포함된 테이블의 열을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-127">Optionally, the Term Extraction transformation can reference a column in a table that contains exclusion terms, meaning terms that the transformation should skip when it extracts terms from a data set.</span></span> <span data-ttu-id="e536a-128">이 기능은 특정 비즈니스 및 분야에서 텍스트에 너무 자주 나와서 쓸모가 없는 단어와 같은 일련의 용어를 중요하지 않은 용어로 이미 정의해 둔 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-128">This is useful when a set of terms has already been identified as inconsequential in a particular business and industry, typically because the term occurs with such high frequency that it becomes a noise word.</span></span> <span data-ttu-id="e536a-129">예를 들어 특정 상표의 자동차에 대한 고객 지원 정보가 포함된 데이터 집합에서 용어를 추출할 때 해당 상표 이름은 너무 자주 나와서 중요하지 않으므로 제외될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-129">For example, when extracting terms from a data set that contains customer support information about a particular brand of cars, the brand name itself might be excluded because it is mentioned too frequently to have significance.</span></span> <span data-ttu-id="e536a-130">따라서 제외 목록의 값은 사용 중인 데이터 집합에 맞게 사용자 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-130">Therefore, the values in the exclusion list must be customized to the data set you are working with.</span></span>  
  
 <span data-ttu-id="e536a-131">제외 목록에 용어를 추가하면 해당 용어를 포함하는 단어나 명사구와 같은 모든 용어도 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-131">When you add a term to the exclusion list, all the terms-words or noun phrases-that contain the term are also excluded.</span></span> <span data-ttu-id="e536a-132">예를 들어 제외 목록에 *data*와 같은 한 단어가 있는 경우 *data*, *data mining*, *data integrity*및 *data validation* 과 같이 이 단어를 포함하는 모든 용어도 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-132">For example, if the exclusion list includes the single word *data*, then all the terms that contain this word, such as *data*, *data mining*, *data integrity*, and *data validation* will also be excluded.</span></span> <span data-ttu-id="e536a-133">*data*를 포함하는 복합어만 제외하려는 경우에는 제외 목록에 해당 복합 용어를 명시적으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-133">If you want to exclude only compounds that contain the word *data*, you must explicitly add those compound terms to the exclusion list.</span></span> <span data-ttu-id="e536a-134">예를 들어 *data*항목은 추출하지만 *data validation*은 제외하려는 경우에는 제외 목록에 *data validation* 을 추가하고 제외 목록에서 *data* 가 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-134">For example, if you want to extract incidences of *data*, but exclude *data validation*, you would add *data validation* to the exclusion list, and make sure that *data* is removed from the exclusion list.</span></span>  
  
 <span data-ttu-id="e536a-135">참조 테이블은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 Access 데이터베이스의 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-135">The reference table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="e536a-136">용어 추출 변환은 별개의 OLE DB 연결을 사용하여 참조 테이블에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-136">The Term Extraction transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="e536a-137">자세한 내용은 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-137">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e536a-138">용어 추출 변환은 완전히 사전 캐시된 모드에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-138">The Term Extraction transformation works in a fully precached mode.</span></span> <span data-ttu-id="e536a-139">용어 추출 변환은 런타임에 참조 테이블로부터 제외 용어를 읽고 변환 입력 행을 처리하기 전에 이를 프라이빗 메모리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-139">At run time, the Term Extraction transformation reads the exclusion terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
## <a name="extraction-of-terms-from-text"></a><span data-ttu-id="e536a-140">텍스트에서 용어 추출</span><span class="sxs-lookup"><span data-stu-id="e536a-140">Extraction of Terms from Text</span></span>  
 <span data-ttu-id="e536a-141">텍스트에서 용어를 추출하기 위해 용어 추출 변환은 다음과 같은 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-141">To extract terms from text, the Term Extraction transformation performs the following tasks.</span></span>  
  
### <a name="identification-of-words"></a><span data-ttu-id="e536a-142">단어 식별</span><span class="sxs-lookup"><span data-stu-id="e536a-142">Identification of Words</span></span>  
 <span data-ttu-id="e536a-143">첫째, 용어 추출 변환은 다음 태스크를 수행하여 단어를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-143">First, the Term Extraction transformation identifies words by performing the following tasks:</span></span>  
  
-   <span data-ttu-id="e536a-144">공백, 줄 바꿈 및 기타 영어에서 사용되는 단어 종료 문자를 사용하여 텍스트를 여러 단어로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-144">Separating text into words by using spaces, line breaks, and other word terminators in the English language.</span></span> <span data-ttu-id="e536a-145">예를 들어 *?*</span><span class="sxs-lookup"><span data-stu-id="e536a-145">For example, punctuation marks such as *?*</span></span> <span data-ttu-id="e536a-146">및 *:* 과 같은 문장 부호는 단어를 구분하는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-146">and *:* are word-breaking characters.</span></span>  
  
-   <span data-ttu-id="e536a-147">하이픈이나 밑줄로 연결된 단어는 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-147">Preserving words that are connected by hyphens or underscores.</span></span> <span data-ttu-id="e536a-148">예를 들어 *copy-protected* 및 *read-only* 와 같은 단어는 한 단어로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-148">For example, the words *copy-protected* and *read-only* remain one word.</span></span>  
  
-   <span data-ttu-id="e536a-149">마침표가 포함된 머리 글자어를 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-149">Keeping intact acronyms that include periods.</span></span> <span data-ttu-id="e536a-150">예를 들어 *A.B.C* Company는 **ABC** 와 **Company**로 토큰화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-150">For example, the *A.B.C* Company would be tokenized as **ABC** and **Company**.</span></span>  
  
-   <span data-ttu-id="e536a-151">특수 문자가 사용된 단어를 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-151">Splitting words on special characters.</span></span> <span data-ttu-id="e536a-152">예를 들어 *date/time* 단어는 *date* 와 *time*으로 추출되고, *(bicycle)* 은 *bicycle*로, C#은 C로 취급됩니다. 특수 문자는 삭제되며 단어로 취급될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-152">For example, the word *date/time* is extracted as *date* and *time*, *(bicycle)* as *bicycle*, and C# is treated as C. Special characters are discarded and cannot be lexicalized.</span></span>  
  
-   <span data-ttu-id="e536a-153">아포스트로피와 같이 단어를 분할하지 않는 특수 문자를 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-153">Recognizing when special characters such as the apostrophe should not split words.</span></span> <span data-ttu-id="e536a-154">예를 들어 *bicycle's* 는 두 단어로 분할되지 않으며 *bicycle* (명사)라는 단일 용어로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-154">For example, the word *bicycle's* is not split into two words, and yields the single term *bicycle* (noun).</span></span>  
  
-   <span data-ttu-id="e536a-155">시간 식, 통화 식, 전자 메일 주소 및 우편 주소를 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-155">Splitting time expressions, monetary expressions, e-mail addresses, and postal addresses.</span></span> <span data-ttu-id="e536a-156">예를 들어 *January 31, 2004* 는 *January*, *31*및 *2004*의 3개의 토큰으로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-156">For example, the date *January 31, 2004* is separated into the three tokens *January*, *31*, and *2004*.</span></span>  
  
### <a name="tagged-words"></a><span data-ttu-id="e536a-157">태그가 지정된 단어</span><span class="sxs-lookup"><span data-stu-id="e536a-157">Tagged Words</span></span>  
 <span data-ttu-id="e536a-158">둘째, 용어 추출 변환은 다음과 같은 문장 요소 중 하나로 단어를 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-158">Second, the Term Extraction transformation tags words as one of the following parts of speech:</span></span>  
  
-   <span data-ttu-id="e536a-159">단수 형태의 명사.</span><span class="sxs-lookup"><span data-stu-id="e536a-159">A noun in the singular form.</span></span> <span data-ttu-id="e536a-160">예를 들면 *bicycle* 과 *potato*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-160">For example, *bicycle* and *potato*.</span></span>  
  
-   <span data-ttu-id="e536a-161">복수 형태의 명사.</span><span class="sxs-lookup"><span data-stu-id="e536a-161">A noun in the plural form.</span></span> <span data-ttu-id="e536a-162">예를 들면 *bicycles* 와 *potatoes*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-162">For example, *bicycles* and *potatoes*.</span></span> <span data-ttu-id="e536a-163">분류되지 않은 모든 복수 명사는 형태소 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-163">All plural nouns that are not lemmatized are subject to stemming.</span></span>  
  
-   <span data-ttu-id="e536a-164">단수 형태의 고유 명사.</span><span class="sxs-lookup"><span data-stu-id="e536a-164">A proper noun in the singular form.</span></span> <span data-ttu-id="e536a-165">예를 들면 *April* 과 *Peter*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-165">For example, *April* and *Peter*.</span></span>  
  
-   <span data-ttu-id="e536a-166">복수 형태의 고유 명사.</span><span class="sxs-lookup"><span data-stu-id="e536a-166">A proper noun in the plural form.</span></span> <span data-ttu-id="e536a-167">예를 들면 *Aprils* 와 *Peters*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-167">For example *Aprils* and *Peters*.</span></span> <span data-ttu-id="e536a-168">고유 명사가 형태소 분석되기 위해서는 표준 영어 단어로 제한되는 내부 어휘집에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-168">For a proper noun to be subject to stemming, it must be a part of the internal lexicon, which is limited to standard English words.</span></span>  
  
-   <span data-ttu-id="e536a-169">형용사.</span><span class="sxs-lookup"><span data-stu-id="e536a-169">An adjective.</span></span> <span data-ttu-id="e536a-170">예를 들면 *blue*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-170">For example, *blue*.</span></span>  
  
-   <span data-ttu-id="e536a-171">두 개의 사물을 비교하는 비교 형용사.</span><span class="sxs-lookup"><span data-stu-id="e536a-171">A comparative adjective that compares two things.</span></span> <span data-ttu-id="e536a-172">예를 들면 *higher* 와 *taller*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-172">For example, *higher* and *taller*.</span></span>  
  
-   <span data-ttu-id="e536a-173">적어도 두 개 이상의 사물에 대해 성질이 높거나 낮은 사물을 나타내는 최상급 형용사.</span><span class="sxs-lookup"><span data-stu-id="e536a-173">A superlative adjective that identifies a thing that has a quality above or below the level of at least two others.</span></span> <span data-ttu-id="e536a-174">예를 들면 *highest* 와 *tallest*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-174">For example, *highest* and *tallest*.</span></span>  
  
-   <span data-ttu-id="e536a-175">숫자.</span><span class="sxs-lookup"><span data-stu-id="e536a-175">A number.</span></span> <span data-ttu-id="e536a-176">예를 들면 *62* 와 *2004*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-176">For example, *62* and *2004*.</span></span>  
  
 <span data-ttu-id="e536a-177">이러한 문장 요소에 속하지 않는 단어는 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-177">Words that are not one of these parts of speech are discarded.</span></span> <span data-ttu-id="e536a-178">예를 들어 동사와 대명사는 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-178">For example, verbs and pronouns are discarded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e536a-179">문장 요소 분류는 통계 모델을 기반으로 하며 분류는 완전히 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-179">The tagging of parts of speech is based on a statistical model and the tagging may not be completely accurate.</span></span>  
  
 <span data-ttu-id="e536a-180">용어 추출 변환이 명사만 추출하도록 구성된 경우 명사 또는 고유 명사의 단/복수 형태로 분류되는 단어만 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-180">If the Term Extraction transformation is configured to extract only nouns, only the words that are tagged as singular or plural forms of nouns and proper nouns are extracted.</span></span>  
  
 <span data-ttu-id="e536a-181">용어 추출 변환이 명사구만 추출하도록 구성된 경우 명사, 고유 명사, 형용사 및 숫자로 분류된 단어가 조합되어 명사구가 될 수 있지만 명사구에는 명사 또는 고유 명사의 단/복수 형태로 분류된 단어가 적어도 하나 이상 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-181">If the Term Extraction transformation is configured to extract only noun phrases, words that are tagged as nouns, proper nouns, adjectives, and numbers may be combined to make a noun phrase, but the phrase must include at least one word that is tagged as a singular or plural form of a noun or a proper noun.</span></span> <span data-ttu-id="e536a-182">예를 들어 명사구 *highest mountain* 에는 최상급 형용사로 분류된 단어(*highest*)와 명사로 분류된 단어(*mountain*)가 조합되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-182">For example, the noun phrase *highest mountain* combines a word tagged as a superlative adjective (*highest*) and a word tagged as noun (*mountain*).</span></span>  
  
 <span data-ttu-id="e536a-183">용어 추출 변환이 명사와 명사구를 모두 추출하도록 구성된 경우 명사에 대한 규칙과 명사구에 대한 규칙이 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-183">If the Term Extraction is configured to extract both nouns and noun phrases, both the rules for nouns and the rules for noun phrases apply.</span></span> <span data-ttu-id="e536a-184">예를 들어 변환에서는 *many beautiful blue bicycles* 라는 텍스트로부터 *bicycle* 및 *beautiful blue bicycle*이 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-184">For example, the transformation extracts *bicycle* and *beautiful blue bicycle* from the text *many beautiful blue bicycles*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e536a-185">추출된 용어는 변환에서 사용되는 최대 용어 길이 및 빈도 임계값에 따라 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-185">The extracted terms remain subject to the maximum term length and frequency threshold that the transformation uses.</span></span>  
  
### <a name="stemmed-words"></a><span data-ttu-id="e536a-186">형태소가 분석된 단어</span><span class="sxs-lookup"><span data-stu-id="e536a-186">Stemmed Words</span></span>  
 <span data-ttu-id="e536a-187">용어 추출 변환은 또한 명사를 형태소 분석하여 명사의 단수 형태만 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-187">The Term Extraction transformation also stems nouns to extract only the singular form of a noun.</span></span> <span data-ttu-id="e536a-188">예를 들어 변환은 *men* 을 *man*으로 추출하고, *mice* 를 *mouse*로, *bicycles* 는 *bicycle*로 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-188">For example, the transformation extracts *man* from *men*, *mouse* from *mice*, and *bicycle* from *bicycles*.</span></span> <span data-ttu-id="e536a-189">변환은 자체 사전을 사용하여 명사를 형태소 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-189">The transformation uses its dictionary to stem nouns.</span></span> <span data-ttu-id="e536a-190">사전에 표시되지 않은 동명사는 명사로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-190">Gerunds are treated as nouns if they are in the dictionary.</span></span>  
  
 <span data-ttu-id="e536a-191">용어 추출 변환은 용어 추출 변환의 내부 사전을 사용하여 다음과 같이 사전의 단어 형태로 단어를 형태소 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-191">The Term Extraction transformation stems words to their dictionary form as shown in these examples by using the dictionary internal to the Term Extraction transformation.</span></span>  
  
-   <span data-ttu-id="e536a-192">명사에서 *s* 를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-192">Removing *s* from nouns.</span></span> <span data-ttu-id="e536a-193">예를 들어 *bicycles* 는 *bicycle*이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-193">For example, *bicycles* becomes *bicycle*.</span></span>  
  
-   <span data-ttu-id="e536a-194">명사에서 *es* 를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-194">Removing *es* from nouns.</span></span> <span data-ttu-id="e536a-195">예를 들어 *stories* 는 *story*가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-195">For example, *stories* becomes *story*.</span></span>  
  
-   <span data-ttu-id="e536a-196">불규칙 명사의 경우 사전에서 단수 형태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-196">Retrieving the singular form for irregular nouns from the dictionary.</span></span> <span data-ttu-id="e536a-197">예를 들어 *geese* 는 *goose*가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-197">For example, *geese* becomes *goose*.</span></span>  
  
### <a name="normalized-words"></a><span data-ttu-id="e536a-198">기본 형태로 변환된 단어</span><span class="sxs-lookup"><span data-stu-id="e536a-198">Normalized Words</span></span>  
 <span data-ttu-id="e536a-199">용어 추출 변환은 문장 내 위치 때문에 대문자로 표기된 용어를 해당 소문자 형태를 사용하여 기본 형태로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-199">The Term Extraction transformation normalizes terms that are capitalized only because of their position in a sentence, and uses their non-capitalized form instead.</span></span> <span data-ttu-id="e536a-200">예를 들어 *Dogs chase cats* 및 *Mountain paths are steep*와 같은 문장에서 *Dogs* 와 *Mountain* 은 *dog* 및 *mountain*의 기본 형태로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-200">For example, in the phrases *Dogs chase cats* and *Mountain paths are steep*, *Dogs* and *Mountain* would be normalized to *dog* and *mountain*.</span></span>  
  
 <span data-ttu-id="e536a-201">용어 추출 변환은 단어를 기본 형태로 바꾸기 때문에 단어의 대/소문자가 달라도 다른 용어로 취급되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-201">The Term Extraction transformation normalizes words so that the capitalized and noncapitalized versions of words are not treated as different terms.</span></span> <span data-ttu-id="e536a-202">예를 들어 *You see many bicycles in Seattle* 및 *Bicycles are blue*와 같은 텍스트에서 *bicycles* 와 *Bicycles* 는 같은 용어로 인식되고 *bicycle*만 변환에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-202">For example, in the text *You see many bicycles in Seattle* and *Bicycles are blue*, *bicycles* and *Bicycles* are recognized as the same term and the transformation keeps only *bicycle*.</span></span> <span data-ttu-id="e536a-203">내부 사전에 나열되지 않은 고유 명사 및 단어는 기본 형태로 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-203">Proper nouns and words that are not listed in the internal dictionary are not normalized.</span></span>  
  
### <a name="case-sensitive-normalization"></a><span data-ttu-id="e536a-204">대/소문자를 구분하는 기본 형태</span><span class="sxs-lookup"><span data-stu-id="e536a-204">Case-Sensitive Normalization</span></span>  
 <span data-ttu-id="e536a-205">용어 추출 변환은 소문자 및 대문자 단어를 각각 고유한 용어로 인식하거나 동일 용어의 다른 표현으로 인식하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-205">The Term Extraction transformation can be configured to consider lowercase and uppercase words as either distinct terms, or as different variants of the same term.</span></span>  
  
-   <span data-ttu-id="e536a-206">대/소문자를 다르게 인식하도록 변환이 구성된 경우 *Method* 와 *method* 는 두 개의 서로 다른 용어로 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-206">If the transformation is configured to recognize differences in case, terms like *Method* and *method* are extracted as two different terms.</span></span> <span data-ttu-id="e536a-207">문장의 첫 번째 단어가 아닌 대문자로 표시된 단어는 기본 형태로 바뀌지 않으며 고유 명사로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-207">Capitalized words that are not the first word in a sentence are never normalized, and are tagged as proper nouns.</span></span>  
  
-   <span data-ttu-id="e536a-208">대/소문자를 구분하지 않도록 변환이 구성된 경우 *Method* 및 *method* 와 같은 용어는 단일 용어의 다른 표현으로 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-208">If the transformation is configured to be case-insensitive, terms like *Method* and *method* are recognized as variants of a single term.</span></span> <span data-ttu-id="e536a-209">추출된 용어 목록에는 입력 데이터 집합에서 단어가 표시된 순서에 따라 *Method* 또는 *method*가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-209">The list of extracted terms might include either *Method* or *method*, depending on which word occurs first in the input data set.</span></span> <span data-ttu-id="e536a-210">*Method* 가 문장의 첫 번째 단어이기 때문에 대문자로 표기된 경우에는 기본 형태로 바뀌어서 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-210">If *Method* is capitalized only because it is the first word in a sentence, it is extracted in normalized form.</span></span>  
  
## <a name="sentence-and-word-boundaries"></a><span data-ttu-id="e536a-211">문장 및 단어 경계</span><span class="sxs-lookup"><span data-stu-id="e536a-211">Sentence and Word Boundaries</span></span>  
 <span data-ttu-id="e536a-212">용어 추출 변환은 다음과 같은 문자를 문장 경계로 사용하여 텍스트를 여러 문장으로 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-212">The Term Extraction transformation separates text into sentences using the following characters as sentence boundaries:</span></span>  
  
-   <span data-ttu-id="e536a-213">ASCII 줄 바꿈 문자 0x0d(캐리지 리턴) 및 0x0a(줄 바꿈).</span><span class="sxs-lookup"><span data-stu-id="e536a-213">ASCII line-break characters 0x0d (carriage return) and 0x0a (line feed).</span></span> <span data-ttu-id="e536a-214">이 문자를 문장 경계로 사용하려면 한 행에 두 개 이상의 줄 바꿈 문자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-214">To use this character as a sentence boundary, there must be two or more line-break characters in a row.</span></span>  
  
-   <span data-ttu-id="e536a-215">하이픈(-).</span><span class="sxs-lookup"><span data-stu-id="e536a-215">Hyphens (-).</span></span> <span data-ttu-id="e536a-216">이 문자를 문장 경계로 사용하려면 하이픈 왼쪽과 오른쪽의 문자가 모두 글자이면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-216">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="e536a-217">밑줄(_).</span><span class="sxs-lookup"><span data-stu-id="e536a-217">Underscore (_).</span></span> <span data-ttu-id="e536a-218">이 문자를 문장 경계로 사용하려면 하이픈 왼쪽과 오른쪽의 문자가 모두 글자이면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-218">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="e536a-219">0x19보다 작거나 같거나 0x7b보다 크거나 같은 모든 유니코드 문자.</span><span class="sxs-lookup"><span data-stu-id="e536a-219">All Unicode characters that are less than or equal to 0x19, or greater than or equal to 0x7b.</span></span>  
  
-   <span data-ttu-id="e536a-220">숫자, 문장 부호 및 영문자 조합.</span><span class="sxs-lookup"><span data-stu-id="e536a-220">Combinations of numbers, punctuation marks, and alphabetical characters.</span></span> <span data-ttu-id="e536a-221">예를 들어 *A23B#99* 는 용어 *A23B*를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-221">For example, *A23B#99* returns the term *A23B*.</span></span>  
  
-   <span data-ttu-id="e536a-222">여기에는 문자, %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", '가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-222">The characters, %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e536a-223">하나 이상의 마침표(.)가 포함된 머리 글자어는 여러 문장으로 분리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-223">Acronyms that include one or more periods (.) are not separated into multiple sentences.</span></span>  
  
 <span data-ttu-id="e536a-224">그런 다음 용어 추출 변환은 다음과 같은 단어 경계를 사용하여 문장을 여러 단어로 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-224">The Term Extraction transformation then separates the sentence into words using the following word boundaries:</span></span>  
  
-   <span data-ttu-id="e536a-225">Space</span><span class="sxs-lookup"><span data-stu-id="e536a-225">Space</span></span>  
  
-   <span data-ttu-id="e536a-226">탭</span><span class="sxs-lookup"><span data-stu-id="e536a-226">Tab</span></span>  
  
-   <span data-ttu-id="e536a-227">ASCII 0x0d(캐리지 리턴)</span><span class="sxs-lookup"><span data-stu-id="e536a-227">ASCII 0x0d (carriage return)</span></span>  
  
-   <span data-ttu-id="e536a-228">ASCII 0x0a(줄 바꿈)</span><span class="sxs-lookup"><span data-stu-id="e536a-228">ASCII 0x0a (line feed)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e536a-229">*we're* 또는 *it's*와 같이 축약형 단어에 아포스트로피가 사용된 경우에는 단어가 아포스트로피 앞에서 잘리고, 그렇지 않으면 아포스트로피 다음의 문자가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-229">If an apostrophe is in a word that is a contraction, such as *we're* or *it's*, the word is broken at the apostrophe; otherwise, the letters following the apostrophe are trimmed.</span></span> <span data-ttu-id="e536a-230">예를 들어 *we're* 는 *we* 와 *'re*로 분할되고 *bicycle's* 는 *bicycle*로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-230">For example, *we're* is split into *we* and *'re*, and *bicycle's* is trimmed to *bicycle*.</span></span>  
  
## <a name="configuration-of-the-term-extraction-transformation"></a><span data-ttu-id="e536a-231">용어 추출 변환 구성</span><span class="sxs-lookup"><span data-stu-id="e536a-231">Configuration of the Term Extraction Transformation</span></span>  
 <span data-ttu-id="e536a-232">용어 추출 변환은 내부 알고리즘과 통계 모델을 사용하여 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-232">The Text Extraction transformation uses internal algorithms and statistical models to generate its results.</span></span> <span data-ttu-id="e536a-233">용어 추출 변환을 여러 번 실행하여 결과를 검토하고 텍스트 마이닝 솔루션에 적합한 결과를 생성하도록 변환을 구성해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-233">You may have to run the Term Extraction transformation several times and examine the results to configure the transformation to generate the type of results that works for your text mining solution.</span></span>  
  
 <span data-ttu-id="e536a-234">용어 추출 변환에는 하나의 일반 입력, 하나의 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-234">The Term Extraction transformation has one regular input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="e536a-235">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-235">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e536a-236">**용어 추출 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="e536a-236">For more information about the properties that you can set in the **Term Extraction Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e536a-237">용어 추출 변환 편집기&#40;용어 추출 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-237">Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;</span></span>](../../term-extraction-transformation-editor-term-extraction-tab.md)  
  
-   [<span data-ttu-id="e536a-238">용어 추출 변환 편집기&#40;제외 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-238">Term Extraction Transformation Editor &#40;Exclusion Tab&#41;</span></span>](../../term-extraction-transformation-editor-exclusion-tab.md)  
  
-   [<span data-ttu-id="e536a-239">용어 추출 변환 편집기&#40;고급 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-239">Term Extraction Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-extraction-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="e536a-240">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-240">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e536a-241">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e536a-241">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="e536a-242">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="e536a-242">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="e536a-243">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-243">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
