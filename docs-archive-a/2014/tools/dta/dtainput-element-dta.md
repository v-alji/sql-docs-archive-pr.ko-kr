---
title: DTAInput 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7d2ff380a4ae1595e50aae472efc5fb4ac72efe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728996"
---
# <a name="dtainput-element-dta"></a><span data-ttu-id="d9668-102">DTAInput 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="d9668-102">DTAInput Element (DTA)</span></span>
  <span data-ttu-id="d9668-103">데이터베이스 엔진 튜닝 관리자에 대한 XML 입력의 정의를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d9668-103">Contains the definition of XML input for Database Engine Tuning Advisor.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9668-104">구문</span><span class="sxs-lookup"><span data-stu-id="d9668-104">Syntax</span></span>  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d9668-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="d9668-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d9668-106">특징</span><span class="sxs-lookup"><span data-stu-id="d9668-106">Characteristics</span></span>|<span data-ttu-id="d9668-107">Description</span><span class="sxs-lookup"><span data-stu-id="d9668-107">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d9668-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="d9668-108">**Data type and length**</span></span>|<span data-ttu-id="d9668-109">없음</span><span class="sxs-lookup"><span data-stu-id="d9668-109">None.</span></span>|  
|<span data-ttu-id="d9668-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="d9668-110">**Default value**</span></span>|<span data-ttu-id="d9668-111">없음</span><span class="sxs-lookup"><span data-stu-id="d9668-111">None.</span></span>|  
|<span data-ttu-id="d9668-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="d9668-112">**Occurrence**</span></span>|<span data-ttu-id="d9668-113">**DTAXML** 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="d9668-113">Optional once per **DTAXML** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d9668-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="d9668-114">Element Relationships</span></span>  
  
|<span data-ttu-id="d9668-115">관계</span><span class="sxs-lookup"><span data-stu-id="d9668-115">Relationship</span></span>|<span data-ttu-id="d9668-116">요소</span><span class="sxs-lookup"><span data-stu-id="d9668-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d9668-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="d9668-117">**Parent element**</span></span>|[<span data-ttu-id="d9668-118">DTAXML 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-118">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)|  
|<span data-ttu-id="d9668-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="d9668-119">**Child elements**</span></span>|[<span data-ttu-id="d9668-120">Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-120">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="d9668-121">Workload 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-121">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)<br /><br /> [<span data-ttu-id="d9668-122">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-122">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)<br /><br /> [<span data-ttu-id="d9668-123">Configuration 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-123">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="d9668-124">설명</span><span class="sxs-lookup"><span data-stu-id="d9668-124">Remarks</span></span>  
 <span data-ttu-id="d9668-125">이 요소는 데이터베이스 엔진 튜닝 관리자 입력 스키마 계층의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="d9668-125">This element is the root of the Database Engine Tuning Advisor input schema hierarchy.</span></span> <span data-ttu-id="d9668-126">데이터베이스 엔진 튜닝 관리자에 대한 입력은 튜닝할 데이터베이스가 있는 서버, 작업, 튜닝 옵션 또는 사용자 지정 구성을 지정하는 인수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9668-126">Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user-specified configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9668-127">예제</span><span class="sxs-lookup"><span data-stu-id="d9668-127">Example</span></span>  
 <span data-ttu-id="d9668-128">**DTAInput** 요소의 사용 예를 보려면 [단순 XML 입력 파일 샘플&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9668-128">For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9668-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9668-129">See Also</span></span>  
 [<span data-ttu-id="d9668-130">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="d9668-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
