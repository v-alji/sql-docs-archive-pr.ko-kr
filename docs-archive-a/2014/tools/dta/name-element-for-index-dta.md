---
title: Index의 Name 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 2300e9cf-f0a8-49e6-b1f5-45ffe03ccb5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a878923a3d483fae5ad6b55421a2b286f15ceb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740611"
---
# <a name="name-element-for-index-dta"></a><span data-ttu-id="43994-102">Index의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="43994-102">Name Element for Index (DTA)</span></span>
  <span data-ttu-id="43994-103">사용자 지정 구성에서 인덱스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43994-103">Specifies a name for an index in the user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43994-104">구문</span><span class="sxs-lookup"><span data-stu-id="43994-104">Syntax</span></span>  
  
```  
  
<Create>  
    <Index>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="43994-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="43994-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="43994-106">특성</span><span class="sxs-lookup"><span data-stu-id="43994-106">Characteristic</span></span>|<span data-ttu-id="43994-107">Description</span><span class="sxs-lookup"><span data-stu-id="43994-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="43994-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="43994-108">**Data type and length**</span></span>|<span data-ttu-id="43994-109">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="43994-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="43994-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="43994-110">**Default value**</span></span>|<span data-ttu-id="43994-111">없음</span><span class="sxs-lookup"><span data-stu-id="43994-111">None.</span></span>|  
|<span data-ttu-id="43994-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="43994-112">**Occurrence**</span></span>|<span data-ttu-id="43994-113">각 `Index` 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43994-113">Required once for each `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="43994-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="43994-114">Element Relationships</span></span>  
  
|<span data-ttu-id="43994-115">관계</span><span class="sxs-lookup"><span data-stu-id="43994-115">Relationship</span></span>|<span data-ttu-id="43994-116">요소</span><span class="sxs-lookup"><span data-stu-id="43994-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="43994-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="43994-117">**Parent element**</span></span>|[<span data-ttu-id="43994-118">Index 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="43994-118">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="43994-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="43994-119">**Child elements**</span></span>|<span data-ttu-id="43994-120">없음</span><span class="sxs-lookup"><span data-stu-id="43994-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43994-121">예제</span><span class="sxs-lookup"><span data-stu-id="43994-121">Example</span></span>  
 <span data-ttu-id="43994-122">이 요소의 사용 예제를 보려면 [사용자 지정 구성이 포함된 XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43994-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43994-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43994-123">See Also</span></span>  
 [<span data-ttu-id="43994-124">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="43994-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
