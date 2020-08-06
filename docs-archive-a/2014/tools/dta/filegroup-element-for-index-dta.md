---
title: Index의 Filegroup 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ed8ea723d6c0798b93e16411ee47d6e956c6c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735748"
---
# <a name="filegroup-element-for-index-dta"></a><span data-ttu-id="34c5a-102">Index의 Filegroup 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="34c5a-102">Filegroup Element for Index (DTA)</span></span>
  <span data-ttu-id="34c5a-103">사용자 지정 구성에서 인덱스를 만들려는 파일 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34c5a-103">Specifies the filegroup on which the index is to be created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c5a-104">구문</span><span class="sxs-lookup"><span data-stu-id="34c5a-104">Syntax</span></span>  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="34c5a-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="34c5a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="34c5a-106">특성</span><span class="sxs-lookup"><span data-stu-id="34c5a-106">Characteristic</span></span>|<span data-ttu-id="34c5a-107">Description</span><span class="sxs-lookup"><span data-stu-id="34c5a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="34c5a-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="34c5a-108">**Data type and length**</span></span>|<span data-ttu-id="34c5a-109">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="34c5a-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="34c5a-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="34c5a-110">**Default value**</span></span>|<span data-ttu-id="34c5a-111">없음</span><span class="sxs-lookup"><span data-stu-id="34c5a-111">None.</span></span>|  
|<span data-ttu-id="34c5a-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="34c5a-112">**Occurrence**</span></span>|<span data-ttu-id="34c5a-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="34c5a-113">Optional.</span></span> <span data-ttu-id="34c5a-114">각 `Index` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34c5a-114">Can use once for each `Index` element.</span></span> <span data-ttu-id="34c5a-115">`PartitionScheme` 및 `PartitionColumn` 요소를 `Index` 요소에 지정한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34c5a-115">This element cannot be used if the `PartitionScheme` and `PartitionColumn` elements are specified for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="34c5a-116">요소 관계</span><span class="sxs-lookup"><span data-stu-id="34c5a-116">Element Relationships</span></span>  
  
|<span data-ttu-id="34c5a-117">관계</span><span class="sxs-lookup"><span data-stu-id="34c5a-117">Relationship</span></span>|<span data-ttu-id="34c5a-118">요소</span><span class="sxs-lookup"><span data-stu-id="34c5a-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="34c5a-119">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="34c5a-119">**Parent element**</span></span>|[<span data-ttu-id="34c5a-120">Index 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="34c5a-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="34c5a-121">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="34c5a-121">**Child elements**</span></span>|<span data-ttu-id="34c5a-122">없음</span><span class="sxs-lookup"><span data-stu-id="34c5a-122">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="34c5a-123">예제</span><span class="sxs-lookup"><span data-stu-id="34c5a-123">Example</span></span>  
 <span data-ttu-id="34c5a-124">이 요소의 사용 예제를 보려면 [사용자 지정 구성이 포함된 XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34c5a-124">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c5a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34c5a-125">See Also</span></span>  
 [<span data-ttu-id="34c5a-126">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="34c5a-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
