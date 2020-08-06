---
title: TestServer 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d1f1fadf76a43caca262652254e8a778602183c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735747"
---
# <a name="testserver-element-dta"></a><span data-ttu-id="8ba60-102">TestServer 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="8ba60-102">TestServer Element (DTA)</span></span>
  <span data-ttu-id="8ba60-103">프로덕션 서버를 튜닝할 때 사용할 테스트 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba60-103">Specifies the test server to use when tuning a production server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba60-104">구문</span><span class="sxs-lookup"><span data-stu-id="8ba60-104">Syntax</span></span>  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8ba60-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="8ba60-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8ba60-106">특성</span><span class="sxs-lookup"><span data-stu-id="8ba60-106">Characteristic</span></span>|<span data-ttu-id="8ba60-107">Description</span><span class="sxs-lookup"><span data-stu-id="8ba60-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8ba60-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="8ba60-108">**Data type and length**</span></span>|<span data-ttu-id="8ba60-109">**string**, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="8ba60-109">**string**, unlimited length.</span></span>|  
|<span data-ttu-id="8ba60-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="8ba60-110">**Default value**</span></span>|<span data-ttu-id="8ba60-111">없음</span><span class="sxs-lookup"><span data-stu-id="8ba60-111">None.</span></span>|  
|<span data-ttu-id="8ba60-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="8ba60-112">**Occurrence**</span></span>|<span data-ttu-id="8ba60-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="8ba60-113">Optional.</span></span> <span data-ttu-id="8ba60-114">각 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba60-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8ba60-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="8ba60-115">Element Relationships</span></span>  
  
|<span data-ttu-id="8ba60-116">관계</span><span class="sxs-lookup"><span data-stu-id="8ba60-116">Relationship</span></span>|<span data-ttu-id="8ba60-117">요소</span><span class="sxs-lookup"><span data-stu-id="8ba60-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8ba60-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="8ba60-118">**Parent element**</span></span>|[<span data-ttu-id="8ba60-119">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba60-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="8ba60-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="8ba60-120">**Child elements**</span></span>|<span data-ttu-id="8ba60-121">없음</span><span class="sxs-lookup"><span data-stu-id="8ba60-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ba60-122">예제</span><span class="sxs-lookup"><span data-stu-id="8ba60-122">Example</span></span>  
 <span data-ttu-id="8ba60-123">이 요소의 사용 예제를 보려면 [프로덕션 서버 튜닝 로드 줄이기](../../relational-databases/performance/reduce-the-production-server-tuning-load.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba60-123">For a usage example of this element, see [Reduce the Production Server Tuning Load](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba60-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba60-124">See Also</span></span>  
 [<span data-ttu-id="8ba60-125">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="8ba60-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
