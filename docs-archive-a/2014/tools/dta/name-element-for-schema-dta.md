---
title: Schema의 Name 요소 (DTA) | Microsoft Docs
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
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 678a6d58b35b25be2aed6d91fcae7ceb2640bdcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734767"
---
# <a name="name-element-for-schema-dta"></a><span data-ttu-id="00948-102">Schema의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="00948-102">Name Element for Schema (DTA)</span></span>
  <span data-ttu-id="00948-103">스키마의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="00948-103">Contains name of the schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00948-104">구문</span><span class="sxs-lookup"><span data-stu-id="00948-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="00948-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="00948-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="00948-106">특성</span><span class="sxs-lookup"><span data-stu-id="00948-106">Characteristic</span></span>|<span data-ttu-id="00948-107">Description</span><span class="sxs-lookup"><span data-stu-id="00948-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="00948-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="00948-108">**Data type and length**</span></span>|<span data-ttu-id="00948-109">`string`, 1에서 255자 사이</span><span class="sxs-lookup"><span data-stu-id="00948-109">`string`, between 1 and 255 characters</span></span>|  
|<span data-ttu-id="00948-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="00948-110">**Default value**</span></span>|<span data-ttu-id="00948-111">없음</span><span class="sxs-lookup"><span data-stu-id="00948-111">None.</span></span>|  
|<span data-ttu-id="00948-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="00948-112">**Occurrence**</span></span>|<span data-ttu-id="00948-113">각 **Schema** 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00948-113">Required once per **Schema** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="00948-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="00948-114">Element Relationships</span></span>  
  
|<span data-ttu-id="00948-115">관계</span><span class="sxs-lookup"><span data-stu-id="00948-115">Relationship</span></span>|<span data-ttu-id="00948-116">요소</span><span class="sxs-lookup"><span data-stu-id="00948-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="00948-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="00948-117">**Parent element**</span></span>|[<span data-ttu-id="00948-118">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="00948-118">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="00948-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="00948-119">**Child elements**</span></span>|<span data-ttu-id="00948-120">없음</span><span class="sxs-lookup"><span data-stu-id="00948-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00948-121">예제</span><span class="sxs-lookup"><span data-stu-id="00948-121">Example</span></span>  
 <span data-ttu-id="00948-122">이 요소의 사용 예는 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00948-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00948-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00948-123">See Also</span></span>  
 [<span data-ttu-id="00948-124">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="00948-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
