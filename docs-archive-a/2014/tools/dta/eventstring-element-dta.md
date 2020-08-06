---
title: EventString 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 981cd0be06fd0972426fcb2fa67b0c4143cf9178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737317"
---
# <a name="eventstring-element-dta"></a><span data-ttu-id="acf02-102">EventString 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="acf02-102">EventString Element (DTA)</span></span>
  <span data-ttu-id="acf02-103">XML 입력 파일에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 작업을 직접 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-103">Specifies a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload directly in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf02-104">구문</span><span class="sxs-lookup"><span data-stu-id="acf02-104">Syntax</span></span>  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="acf02-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="acf02-105">Element Attributes</span></span>  
  
|<span data-ttu-id="acf02-106">attribute</span><span class="sxs-lookup"><span data-stu-id="acf02-106">Attribute</span></span>|<span data-ttu-id="acf02-107">설명</span><span class="sxs-lookup"><span data-stu-id="acf02-107">Description</span></span>|  
|---------------|-----------------|  
|`Weight`|<span data-ttu-id="acf02-108">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="acf02-108">Optional.</span></span> <span data-ttu-id="acf02-109">지정한 이벤트에 대한 쿼리 가중치 요인(중요도 요인)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-109">Specifies the query weight factor (a factor of importance) for the specified event.</span></span> <span data-ttu-id="acf02-110">`float` 데이터 형식을 사용하여 가중치를 지정할 수 있습니다(예:</span><span class="sxs-lookup"><span data-stu-id="acf02-110">Use a `float` data type to specify the weight.</span></span> <span data-ttu-id="acf02-111">`Weight`="100.01").</span><span class="sxs-lookup"><span data-stu-id="acf02-111">For example, `Weight`="100.01".</span></span> <span data-ttu-id="acf02-112">`Weight`에 지정할 수 있는 최소값은 "0"입니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-112">The minimum value you can specify for `Weight` is "0".</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="acf02-113">요소 특징</span><span class="sxs-lookup"><span data-stu-id="acf02-113">Element Characteristics</span></span>  
  
|<span data-ttu-id="acf02-114">특성</span><span class="sxs-lookup"><span data-stu-id="acf02-114">Characteristic</span></span>|<span data-ttu-id="acf02-115">Description</span><span class="sxs-lookup"><span data-stu-id="acf02-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="acf02-116">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="acf02-116">**Data type and length**</span></span>|<span data-ttu-id="acf02-117">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="acf02-117">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="acf02-118">**기본값**</span><span class="sxs-lookup"><span data-stu-id="acf02-118">**Default value**</span></span>|<span data-ttu-id="acf02-119">없음</span><span class="sxs-lookup"><span data-stu-id="acf02-119">None.</span></span>|  
|<span data-ttu-id="acf02-120">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="acf02-120">**Occurrence**</span></span>|<span data-ttu-id="acf02-121">다른 작업 유형이 지정되지 않은 경우 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-121">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="acf02-122">`EventString` 부모에 대해 `File`, `Database` 또는 `Workload` 자식 요소를 지정해야 하지만 한 유형만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-122">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="acf02-123">예를 들어 `EventString` 요소로 작업을 지정할 경우 동일한 XML 입력 파일에서 `File` 요소로 작업을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acf02-123">For example, if you specify a workload with the `EventString` element, then you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="acf02-124">요소 관계</span><span class="sxs-lookup"><span data-stu-id="acf02-124">Element Relationships</span></span>  
  
|<span data-ttu-id="acf02-125">관계</span><span class="sxs-lookup"><span data-stu-id="acf02-125">Relationship</span></span>|<span data-ttu-id="acf02-126">요소</span><span class="sxs-lookup"><span data-stu-id="acf02-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="acf02-127">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="acf02-127">**Parent element**</span></span>|[<span data-ttu-id="acf02-128">Workload 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="acf02-128">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="acf02-129">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="acf02-129">**Child elements**</span></span>|<span data-ttu-id="acf02-130">없음</span><span class="sxs-lookup"><span data-stu-id="acf02-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="acf02-131">예제</span><span class="sxs-lookup"><span data-stu-id="acf02-131">Example</span></span>  
 <span data-ttu-id="acf02-132">이 요소의 사용 예를 보려면 [인라인 워크로드가 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acf02-132">For a usage example of this element, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf02-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acf02-133">See Also</span></span>  
 [<span data-ttu-id="acf02-134">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="acf02-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
