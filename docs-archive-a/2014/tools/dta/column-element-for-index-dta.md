---
title: Index의 Column 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67853dc7d1193d3a0f80e56023846bc55a20bdaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727683"
---
# <a name="column-element-for-index-dta"></a><span data-ttu-id="18f06-102">Index의 Column 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="18f06-102">Column Element for Index (DTA)</span></span>
  <span data-ttu-id="18f06-103">사용자 지정 구성에서 인덱스가 만들어지는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-103">Specifies the columns on which the index is created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f06-104">구문</span><span class="sxs-lookup"><span data-stu-id="18f06-104">Syntax</span></span>  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="18f06-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="18f06-105">Element Attributes</span></span>  
  
|<span data-ttu-id="18f06-106">Column 특성</span><span class="sxs-lookup"><span data-stu-id="18f06-106">Column Attribute</span></span>|<span data-ttu-id="18f06-107">설명</span><span class="sxs-lookup"><span data-stu-id="18f06-107">Description</span></span>|  
|----------------------|-----------------|  
|`Type`|<span data-ttu-id="18f06-108">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-108">Optional.</span></span> <span data-ttu-id="18f06-109">인덱스 열 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-109">Specifies the index column type.</span></span> <span data-ttu-id="18f06-110">**string** 데이터 형식을 사용하여 허용된 다음 값 중 하나로 이 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="18f06-111">`KeyColumn`:</span><span class="sxs-lookup"><span data-stu-id="18f06-111">`KeyColumn`:</span></span><br />                  <span data-ttu-id="18f06-112">인덱스 키에서 열을 참조하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-112">Specifies that the column is referenced by an index key.</span></span> <span data-ttu-id="18f06-113">다음 구문을 사용하여 이 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-113">Use the following syntax to set this attribute:</span></span><br />`<Column Type="KeyColumn">`<br /><span data-ttu-id="18f06-114">자세한 내용은 [클러스터형 및 비클러스터형 인덱스 소개](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18f06-114">For more information about key columns, see [Clustered and Nonclustered Indexes Described](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).</span></span><br /><br /> <span data-ttu-id="18f06-115">`IncludedColumn`: 열이 키 열 대신 포괄 열 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-115">`IncludedColumn`: Specifies that the column is an included column (instead of a key column).</span></span> <span data-ttu-id="18f06-116">다음 구문을 사용하여 이 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-116">Use the following syntax to set this attribute:</span></span><br />`<Column Type="IncludedColumn">`<br /><span data-ttu-id="18f06-117">키가 아닌 열 포함에 대한 자세한 내용은 [포괄 열을 사용하여 인덱스 만들기](../../relational-databases/indexes/create-indexes-with-included-columns.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18f06-117">For more information about included columns, see [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).</span></span>|  
|`SortOrder`|<span data-ttu-id="18f06-118">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-118">Optional.</span></span> <span data-ttu-id="18f06-119">열의 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-119">Specifies the sorting order of the column.</span></span> <span data-ttu-id="18f06-120">다음과 같이 **string** 데이터 형식을 사용하여 **"Ascending"** 또는 **"Descending"** 정렬 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-120">Use a **string** data type to specify either an **"Ascending"** or **"Descending"** sorting order as follows:</span></span><br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="18f06-121">요소 특징</span><span class="sxs-lookup"><span data-stu-id="18f06-121">Element Characteristics</span></span>  
  
|<span data-ttu-id="18f06-122">특성</span><span class="sxs-lookup"><span data-stu-id="18f06-122">Characteristic</span></span>|<span data-ttu-id="18f06-123">Description</span><span class="sxs-lookup"><span data-stu-id="18f06-123">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="18f06-124">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="18f06-124">**Data type and length**</span></span>|<span data-ttu-id="18f06-125">없음</span><span class="sxs-lookup"><span data-stu-id="18f06-125">None.</span></span>|  
|<span data-ttu-id="18f06-126">**기본값**</span><span class="sxs-lookup"><span data-stu-id="18f06-126">**Default value**</span></span>|<span data-ttu-id="18f06-127">없음</span><span class="sxs-lookup"><span data-stu-id="18f06-127">None.</span></span>|  
|<span data-ttu-id="18f06-128">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="18f06-128">**Occurrence**</span></span>|<span data-ttu-id="18f06-129">`Index` 요소에 최대 1024개의 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f06-129">Can specify up to 1024 columns for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="18f06-130">요소 관계</span><span class="sxs-lookup"><span data-stu-id="18f06-130">Element Relationships</span></span>  
  
|<span data-ttu-id="18f06-131">관계</span><span class="sxs-lookup"><span data-stu-id="18f06-131">Relationship</span></span>|<span data-ttu-id="18f06-132">요소</span><span class="sxs-lookup"><span data-stu-id="18f06-132">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="18f06-133">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="18f06-133">**Parent element**</span></span>|[<span data-ttu-id="18f06-134">Index 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="18f06-134">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="18f06-135">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="18f06-135">**Child elements**</span></span>|[<span data-ttu-id="18f06-136">Column의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="18f06-136">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="18f06-137">예제</span><span class="sxs-lookup"><span data-stu-id="18f06-137">Example</span></span>  
 <span data-ttu-id="18f06-138">이 요소의 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18f06-138">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f06-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18f06-139">See Also</span></span>  
 [<span data-ttu-id="18f06-140">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="18f06-140">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
