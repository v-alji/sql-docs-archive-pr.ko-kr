---
title: Configuration의 Database 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 69ce1a0ac9912907f6d22916dd6243621e0778db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727655"
---
# <a name="database-element-for-configuration-dta"></a><span data-ttu-id="15a4a-102">Configuration의 Database 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="15a4a-102">Database Element for Configuration (DTA)</span></span>
  <span data-ttu-id="15a4a-103">데이터베이스 엔진 튜닝 관리자가 가상 구성(`Configuration` 요소에 의해 지정됨)을 평가하게 하려는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a4a-103">Specifies the database against which you want the Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a4a-104">구문</span><span class="sxs-lookup"><span data-stu-id="15a4a-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="15a4a-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="15a4a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="15a4a-106">특성</span><span class="sxs-lookup"><span data-stu-id="15a4a-106">Characteristic</span></span>|<span data-ttu-id="15a4a-107">Description</span><span class="sxs-lookup"><span data-stu-id="15a4a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="15a4a-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="15a4a-108">**Data type and length**</span></span>|<span data-ttu-id="15a4a-109">없음</span><span class="sxs-lookup"><span data-stu-id="15a4a-109">None.</span></span>|  
|<span data-ttu-id="15a4a-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="15a4a-110">**Default value**</span></span>|<span data-ttu-id="15a4a-111">없음</span><span class="sxs-lookup"><span data-stu-id="15a4a-111">None.</span></span>|  
|<span data-ttu-id="15a4a-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="15a4a-112">**Occurrence**</span></span>|<span data-ttu-id="15a4a-113">`Server` 요소마다 한 번 이상 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15a4a-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="15a4a-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="15a4a-114">Element Relationships</span></span>  
  
|<span data-ttu-id="15a4a-115">관계</span><span class="sxs-lookup"><span data-stu-id="15a4a-115">Relationship</span></span>|<span data-ttu-id="15a4a-116">요소</span><span class="sxs-lookup"><span data-stu-id="15a4a-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="15a4a-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="15a4a-117">**Parent element**</span></span>|[<span data-ttu-id="15a4a-118">Configuration의 Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="15a4a-118">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
|<span data-ttu-id="15a4a-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="15a4a-119">**Child elements**</span></span>|[<span data-ttu-id="15a4a-120">Database의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="15a4a-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="15a4a-121">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="15a4a-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="15a4a-122">Recommendation 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="15a4a-122">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="15a4a-123">설명</span><span class="sxs-lookup"><span data-stu-id="15a4a-123">Remarks</span></span>  
 <span data-ttu-id="15a4a-124">데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **DatabaseTypecomplexType** 입니다.</span><span class="sxs-lookup"><span data-stu-id="15a4a-124">This element is of the **DatabaseTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="15a4a-125">이 `Database` 요소와 XML 입력 파일의 맨 위에서 발생하는 `Server` 요소가 루트 부모인 요소를 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="15a4a-125">Do not confuse this `Database` element with the one whose root parent is the `Server` element, which occurs at the top of the XML input file.</span></span> <span data-ttu-id="15a4a-126">자세한 내용은 [Server의 Database 요소&#40;DTA&#41;](database-element-for-server-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15a4a-126">For more information, see [Database Element for Server &#40;DTA&#41;](database-element-for-server-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15a4a-127">예제</span><span class="sxs-lookup"><span data-stu-id="15a4a-127">Example</span></span>  
 <span data-ttu-id="15a4a-128">이 요소의 사용 예를 `Database` 보려면 [DTA&#41;&#40;사용자 지정 구성이 포함 된 XML 입력 파일 샘플 ](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15a4a-128">For a usage example of this `Database` element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a4a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15a4a-129">See Also</span></span>  
 [<span data-ttu-id="15a4a-130">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="15a4a-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
