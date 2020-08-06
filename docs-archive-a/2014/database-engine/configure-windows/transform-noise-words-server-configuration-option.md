---
title: transform noise words 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 49de4a381de3e998073a73c284e3e3e5960f4921
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738692"
---
# <a name="transform-noise-words-server-configuration-option"></a><span data-ttu-id="1c776-102">transform noise words 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="1c776-102">transform noise words Server Configuration Option</span></span>
  <span data-ttu-id="1c776-103">`transform noise words`의미 없는 단어 ( [중지 단어](../../relational-databases/search/full-text-search.md))로 인해 전체 텍스트 쿼리에 대 한 부울 연산에서 0 개의 행을 반환 하는 경우 오류 메시지를 표시 하지 않으려면 서버 구성 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-103">Use the `transform noise words` server configuration option to suppress an error message if noise words, that is [stopwords](../../relational-databases/search/full-text-search.md), cause a Boolean operation on a full-text query to return zero rows.</span></span> <span data-ttu-id="1c776-104">이 옵션은 부울 연산 또는 NEAR 연산에 의미 없는 단어가 들어 있는 CONTAINS 조건자를 사용하는 전체 텍스트 쿼리에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-104">This option is useful for full-text queries that use the CONTAINS predicate in which Boolean operations or NEAR operations include noise words.</span></span> <span data-ttu-id="1c776-105">다음 표에서는 이 옵션에 사용할 수 있는 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-105">The possible values are described in the following table.</span></span>  
  
|<span data-ttu-id="1c776-106">값</span><span class="sxs-lookup"><span data-stu-id="1c776-106">Value</span></span>|<span data-ttu-id="1c776-107">설명</span><span class="sxs-lookup"><span data-stu-id="1c776-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1c776-108">0</span><span class="sxs-lookup"><span data-stu-id="1c776-108">0</span></span>|<span data-ttu-id="1c776-109">의미 없는 단어(또는 중지 단어)가 변환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-109">Noise words (or stopwords) are not transformed.</span></span> <span data-ttu-id="1c776-110">전체 텍스트 쿼리에 의미 없는 단어가 들어 있으면 쿼리에서 행이 반환되지 않고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-110">When a full-text query contains noise words, the query returns zero rows, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] raises a warning.</span></span> <span data-ttu-id="1c776-111">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-111">This is the default behavior.</span></span><br /><br /> <span data-ttu-id="1c776-112">경고는 런타임 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-112">Note that the warning is a run-time warning.</span></span> <span data-ttu-id="1c776-113">쿼리에 있는 전체 텍스트 절이 실행되지 않으면 경고가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-113">Therefore, if the full-text clause in the query is not executed, the warning is not raised.</span></span> <span data-ttu-id="1c776-114">로컬 쿼리의 경우 여러 개의 전체 텍스트 쿼리 절이 있어도 경고는 하나만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-114">For a local query, only one warning is raised, even when there are multiple full-text query clauses.</span></span> <span data-ttu-id="1c776-115">원격 쿼리의 경우 연결된 서버에서 오류를 릴레이하지 않을 수 있으므로 경고가 발생하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-115">For a remote query, the linked server might not relay the error; therefore, the warning might not be raised.</span></span>|  
|<span data-ttu-id="1c776-116">1</span><span class="sxs-lookup"><span data-stu-id="1c776-116">1</span></span>|<span data-ttu-id="1c776-117">의미 없는 단어(또는 중지 단어)가 변환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-117">Noise words (or stopwords) are transformed.</span></span> <span data-ttu-id="1c776-118">이러한 단어는 무시되고 쿼리의 나머지가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-118">They are ignored, and the rest of the query is evaluated.</span></span><br /><br /> <span data-ttu-id="1c776-119">근접 단어에서 의미 없는 단어가 지정된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 의미 없는 단어를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-119">If noise words are specified in a proximity term, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] removes them.</span></span> <span data-ttu-id="1c776-120">예를 들어 `is` 에서 의미 없는 단어 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`가 제거되고 검색 쿼리가 `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-120">For example, the noise word `is` is removed from `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, transforming the search query into `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`.</span></span> <span data-ttu-id="1c776-121">`CONTAINS(<column_name>, 'NEAR(hello,is)')` 는 유효한 검색 단어가 하나만 있으므로 간단히 `CONTAINS(<column_name>, hello)` 로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-121">Notice that `CONTAINS(<column_name>, 'NEAR(hello,is)')` would be transformed into simply `CONTAINS(<column_name>, hello)` because there is only one valid search term.</span></span>|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a><span data-ttu-id="1c776-122">의미 없는 단어 변환 설정의 효과</span><span class="sxs-lookup"><span data-stu-id="1c776-122">Effects of the transform noise words Setting</span></span>  
 <span data-ttu-id="1c776-123">이 섹션에서는 `transform noise words`의 설정별로 의미 없는 단어 "`the`"가 들어 있는 쿼리의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-123">This section illustrates the behavior of queries containing a noise word, "`the`", under the alternate settings of `transform noise words`.</span></span>  <span data-ttu-id="1c776-124">예제 전체 텍스트 쿼리 문자열은 다음 데이터가 포함된 테이블 행에 대해 실행되는 것으로 가정합니다. `[1, "The black cat"]`.</span><span class="sxs-lookup"><span data-stu-id="1c776-124">The sample full-text query strings are assumed to be run against a table row containing the following data: `[1, "The black cat"]`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c776-125">이러한 모든 시나리오에서 의미 없는 단어 경고가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-125">All such scenarios can generate a noise word warning.</span></span>  
  
-   <span data-ttu-id="1c776-126">의미 없는 단어를 0으로 설정한 경우:</span><span class="sxs-lookup"><span data-stu-id="1c776-126">With transform noise words set to 0:</span></span>  
  
    |<span data-ttu-id="1c776-127">쿼리 문자열</span><span class="sxs-lookup"><span data-stu-id="1c776-127">Query string</span></span>|<span data-ttu-id="1c776-128">결과</span><span class="sxs-lookup"><span data-stu-id="1c776-128">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="1c776-129">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-129">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="1c776-130">결과가 없습니다. 이 동작은 "`the`" AND "`cat`"의 경우에도 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-130">No results (The behavior is the same for "`the`" AND "`cat`".)</span></span>|  
    |<span data-ttu-id="1c776-131">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-131">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="1c776-132">결과가 없습니다. 이 동작은 "`the`" NEAR "`cat`"의 경우에도 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-132">No results (The behavior is the same for "`the`" NEAR "`cat`".)</span></span>|  
    |<span data-ttu-id="1c776-133">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="1c776-133">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="1c776-134">결과 없음</span><span class="sxs-lookup"><span data-stu-id="1c776-134">No results</span></span>|  
    |<span data-ttu-id="1c776-135">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-135">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="1c776-136">결과 없음</span><span class="sxs-lookup"><span data-stu-id="1c776-136">No results</span></span>|  
  
-   <span data-ttu-id="1c776-137">의미 없는 단어를 1로 설정한 경우:</span><span class="sxs-lookup"><span data-stu-id="1c776-137">With transform noise words set to 1:</span></span>  
  
    |<span data-ttu-id="1c776-138">쿼리 문자열</span><span class="sxs-lookup"><span data-stu-id="1c776-138">Query string</span></span>|<span data-ttu-id="1c776-139">결과</span><span class="sxs-lookup"><span data-stu-id="1c776-139">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="1c776-140">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-140">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="1c776-141">ID가 1인 행</span><span class="sxs-lookup"><span data-stu-id="1c776-141">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="1c776-142">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-142">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="1c776-143">ID가 1인 행</span><span class="sxs-lookup"><span data-stu-id="1c776-143">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="1c776-144">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="1c776-144">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="1c776-145">결과 없음</span><span class="sxs-lookup"><span data-stu-id="1c776-145">No results</span></span>|  
    |<span data-ttu-id="1c776-146">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="1c776-146">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="1c776-147">ID가 1인 행</span><span class="sxs-lookup"><span data-stu-id="1c776-147">Hit for row with ID 1</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1c776-148">예제</span><span class="sxs-lookup"><span data-stu-id="1c776-148">Example</span></span>  
 <span data-ttu-id="1c776-149">다음 예에서는 `transform noise words`를 `1`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c776-149">The following example sets `transform noise words` to `1`.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c776-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c776-150">See Also</span></span>  
 <span data-ttu-id="1c776-151">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c776-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="1c776-152">CONTAINS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1c776-152">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
