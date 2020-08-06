---
title: Column의 Name 요소 (DTA) | Microsoft Docs
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
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
author: stevestein
ms.author: sstein
ms.openlocfilehash: fad3d9a86a7c5db6b6a7503dc90b5a1540e3618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727631"
---
# <a name="name-element-for-column-dta"></a><span data-ttu-id="27626-102">Column의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="27626-102">Name Element for Column (DTA)</span></span>
  <span data-ttu-id="27626-103">사용자 지정 구성에서 인덱스 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27626-103">Specifies the name for an index column in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27626-104">구문</span><span class="sxs-lookup"><span data-stu-id="27626-104">Syntax</span></span>  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="27626-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="27626-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="27626-106">특성</span><span class="sxs-lookup"><span data-stu-id="27626-106">Characteristic</span></span>|<span data-ttu-id="27626-107">Description</span><span class="sxs-lookup"><span data-stu-id="27626-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="27626-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="27626-108">**Data type and length**</span></span>|<span data-ttu-id="27626-109">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="27626-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="27626-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="27626-110">**Default value**</span></span>|<span data-ttu-id="27626-111">없음</span><span class="sxs-lookup"><span data-stu-id="27626-111">None.</span></span>|  
|<span data-ttu-id="27626-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="27626-112">**Occurrence**</span></span>|<span data-ttu-id="27626-113">각 `Column` 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27626-113">Required once for each `Column` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="27626-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="27626-114">Element Relationships</span></span>  
  
|<span data-ttu-id="27626-115">관계</span><span class="sxs-lookup"><span data-stu-id="27626-115">Relationship</span></span>|<span data-ttu-id="27626-116">요소</span><span class="sxs-lookup"><span data-stu-id="27626-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="27626-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="27626-117">**Parent element**</span></span>|[<span data-ttu-id="27626-118">Index의 Column 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="27626-118">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)|  
|<span data-ttu-id="27626-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="27626-119">**Child elements**</span></span>|<span data-ttu-id="27626-120">없음</span><span class="sxs-lookup"><span data-stu-id="27626-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27626-121">예제</span><span class="sxs-lookup"><span data-stu-id="27626-121">Example</span></span>  
 <span data-ttu-id="27626-122">이 요소의 사용 예제를 보려면 [사용자 지정 구성이 포함된 XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27626-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27626-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27626-123">See Also</span></span>  
 [<span data-ttu-id="27626-124">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="27626-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
