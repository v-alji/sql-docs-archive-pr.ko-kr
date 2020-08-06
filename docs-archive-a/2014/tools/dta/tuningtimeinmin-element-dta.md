---
title: TuningTimeInMin 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dae3fe4e9ac3126f43ec017c34d2bc548fda6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735723"
---
# <a name="tuningtimeinmin-element-dta"></a><span data-ttu-id="44380-102">TuningTimeInMin 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="44380-102">TuningTimeInMin Element (DTA)</span></span>
  <span data-ttu-id="44380-103">튜닝 세션의 최대 길이(분)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44380-103">Specifies the maximum length of a tuning session in minutes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44380-104">구문</span><span class="sxs-lookup"><span data-stu-id="44380-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="44380-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="44380-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="44380-106">특성</span><span class="sxs-lookup"><span data-stu-id="44380-106">Characteristic</span></span>|<span data-ttu-id="44380-107">Description</span><span class="sxs-lookup"><span data-stu-id="44380-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="44380-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="44380-108">**Data type and length**</span></span>|<span data-ttu-id="44380-109">`unsignedInt`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="44380-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="44380-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="44380-110">**Default value**</span></span>|<span data-ttu-id="44380-111">480분(8시간)</span><span class="sxs-lookup"><span data-stu-id="44380-111">480 minutes (8 hours).</span></span>|  
|<span data-ttu-id="44380-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="44380-112">**Occurrence**</span></span>|<span data-ttu-id="44380-113">`NumberOfEvents` 요소에 값을 지정하지 않은 경우 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44380-113">Required unless a value has been specified for the `NumberOfEvents` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="44380-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="44380-114">Element Relationships</span></span>  
  
|<span data-ttu-id="44380-115">관계</span><span class="sxs-lookup"><span data-stu-id="44380-115">Relationship</span></span>|<span data-ttu-id="44380-116">요소</span><span class="sxs-lookup"><span data-stu-id="44380-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="44380-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="44380-117">**Parent element**</span></span>|[<span data-ttu-id="44380-118">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="44380-118">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="44380-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="44380-119">**Child elements**</span></span>|<span data-ttu-id="44380-120">None</span><span class="sxs-lookup"><span data-stu-id="44380-120">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44380-121">예제</span><span class="sxs-lookup"><span data-stu-id="44380-121">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="44380-122">Description</span><span class="sxs-lookup"><span data-stu-id="44380-122">Description</span></span>  
 <span data-ttu-id="44380-123">다음 코드 예에서는 최대 튜닝 시간을 12시간으로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44380-123">The following code example shows how to set 12 hours as the maximum tuning time:</span></span>  
  
## <a name="code"></a><span data-ttu-id="44380-124">코드</span><span class="sxs-lookup"><span data-stu-id="44380-124">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44380-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44380-125">See Also</span></span>  
 [<span data-ttu-id="44380-126">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="44380-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
