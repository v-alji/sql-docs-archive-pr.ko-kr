---
title: Schema의 Table 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd444b1da99b22e0259dc1f50818c1763b7052ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735744"
---
# <a name="table-element-for-schema-dta"></a><span data-ttu-id="36f9d-102">Schema의 Table 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="36f9d-102">Table Element for Schema (DTA)</span></span>
  <span data-ttu-id="36f9d-103">튜닝에 사용할 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9d-103">Specifies the table for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f9d-104">구문</span><span class="sxs-lookup"><span data-stu-id="36f9d-104">Syntax</span></span>  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="36f9d-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="36f9d-105">Element Attributes</span></span>  
  
|<span data-ttu-id="36f9d-106">attribute</span><span class="sxs-lookup"><span data-stu-id="36f9d-106">Attribute</span></span>|<span data-ttu-id="36f9d-107">설명</span><span class="sxs-lookup"><span data-stu-id="36f9d-107">Description</span></span>|  
|---------------|-----------------|  
|`NumberOfRows`|<span data-ttu-id="36f9d-108">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="36f9d-108">Optional.</span></span> <span data-ttu-id="36f9d-109">여러 다른 크기의 테이블을 시뮬레이트할 수 있게 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="36f9d-109">Integer that allows you to simulate tables of different sizes.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="36f9d-110">요소 특징</span><span class="sxs-lookup"><span data-stu-id="36f9d-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="36f9d-111">특성</span><span class="sxs-lookup"><span data-stu-id="36f9d-111">Characteristic</span></span>|<span data-ttu-id="36f9d-112">Description</span><span class="sxs-lookup"><span data-stu-id="36f9d-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="36f9d-113">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="36f9d-113">**Data type and length**</span></span>|<span data-ttu-id="36f9d-114">**string**, 1에서 255자 사이</span><span class="sxs-lookup"><span data-stu-id="36f9d-114">**string**, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="36f9d-115">**기본값**</span><span class="sxs-lookup"><span data-stu-id="36f9d-115">**Default value**</span></span>|<span data-ttu-id="36f9d-116">없음</span><span class="sxs-lookup"><span data-stu-id="36f9d-116">None.</span></span>|  
|<span data-ttu-id="36f9d-117">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="36f9d-117">**Occurrence**</span></span>|<span data-ttu-id="36f9d-118">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="36f9d-118">Optional.</span></span> <span data-ttu-id="36f9d-119">작업에 적합한 수만큼 테이블을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9d-119">List as many tables as appropriate for your workload.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="36f9d-120">요소 관계</span><span class="sxs-lookup"><span data-stu-id="36f9d-120">Element Relationships</span></span>  
  
|<span data-ttu-id="36f9d-121">관계</span><span class="sxs-lookup"><span data-stu-id="36f9d-121">Relationship</span></span>|<span data-ttu-id="36f9d-122">요소</span><span class="sxs-lookup"><span data-stu-id="36f9d-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="36f9d-123">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="36f9d-123">**Parent element**</span></span>|[<span data-ttu-id="36f9d-124">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="36f9d-124">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="36f9d-125">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="36f9d-125">**Child elements**</span></span>|[<span data-ttu-id="36f9d-126">Table의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="36f9d-126">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="36f9d-127">설명</span><span class="sxs-lookup"><span data-stu-id="36f9d-127">Remarks</span></span>  
 <span data-ttu-id="36f9d-128">`Table` 요소를 지정하지 않을 경우 데이터베이스 엔진 튜닝 관리자는 지정된 데이터베이스의 모든 테이블을 튜닝할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9d-128">If you do not specify a `Table` element, Database Engine Tuning Advisor will assume all tables on the specified database can be tuned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f9d-129">예제</span><span class="sxs-lookup"><span data-stu-id="36f9d-129">Example</span></span>  
 <span data-ttu-id="36f9d-130">사용 예를 보려면 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9d-130">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f9d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36f9d-131">See Also</span></span>  
 [<span data-ttu-id="36f9d-132">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="36f9d-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
