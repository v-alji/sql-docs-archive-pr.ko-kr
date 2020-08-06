---
title: DatabaseToConnect 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c21b36319e4007264677d499b84964c7cb5ea7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727648"
---
# <a name="databasetoconnect-element-dta"></a><span data-ttu-id="723fe-102">DatabaseToConnect 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="723fe-102">DatabaseToConnect Element (DTA)</span></span>
  <span data-ttu-id="723fe-103">작업 튜닝 시 데이터베이스 엔진 튜닝 관리자가 연결되는 첫 번째 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="723fe-103">Specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723fe-104">구문</span><span class="sxs-lookup"><span data-stu-id="723fe-104">Syntax</span></span>  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="723fe-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="723fe-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="723fe-106">특성</span><span class="sxs-lookup"><span data-stu-id="723fe-106">Characteristic</span></span>|<span data-ttu-id="723fe-107">Description</span><span class="sxs-lookup"><span data-stu-id="723fe-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="723fe-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="723fe-108">**Data type and length**</span></span>|<span data-ttu-id="723fe-109">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="723fe-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="723fe-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="723fe-110">**Default value**</span></span>|<span data-ttu-id="723fe-111">없음</span><span class="sxs-lookup"><span data-stu-id="723fe-111">None.</span></span>|  
|<span data-ttu-id="723fe-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="723fe-112">**Occurrence**</span></span>|<span data-ttu-id="723fe-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="723fe-113">Optional.</span></span> <span data-ttu-id="723fe-114">각 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="723fe-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="723fe-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="723fe-115">Element Relationships</span></span>  
  
|<span data-ttu-id="723fe-116">관계</span><span class="sxs-lookup"><span data-stu-id="723fe-116">Relationship</span></span>|<span data-ttu-id="723fe-117">요소</span><span class="sxs-lookup"><span data-stu-id="723fe-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="723fe-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="723fe-118">**Parent element**</span></span>|[<span data-ttu-id="723fe-119">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="723fe-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="723fe-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="723fe-120">**Child elements**</span></span>|<span data-ttu-id="723fe-121">None</span><span class="sxs-lookup"><span data-stu-id="723fe-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="723fe-122">설명</span><span class="sxs-lookup"><span data-stu-id="723fe-122">Remarks</span></span>  
 <span data-ttu-id="723fe-123">`DatabaseToConnect`를 사용하여 데이터베이스 엔진 튜닝 관리자가 튜닝 세션을 시작할 때 연결되는 첫 번째 데이터베이스의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="723fe-123">Use `DatabaseToConnect` to specify the name of the first database to which you want Database Engine Tuning Advisor to connect when it starts the tuning session.</span></span> <span data-ttu-id="723fe-124">이 요소에서는 데이터베이스를 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="723fe-124">You can specify only one database with this element.</span></span> <span data-ttu-id="723fe-125">여러 데이터베이스 이름을 지정할 경우 데이터베이스 엔진 튜닝 관리자는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="723fe-125">If multiple database names are specified, Database Engine Tuning Advisor returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="723fe-126">예제</span><span class="sxs-lookup"><span data-stu-id="723fe-126">Example</span></span>  
 <span data-ttu-id="723fe-127">사용 예제를 보려면 [인라인 워크로드가 포함된 XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="723fe-127">For a usage example, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723fe-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="723fe-128">See Also</span></span>  
 [<span data-ttu-id="723fe-129">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="723fe-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
