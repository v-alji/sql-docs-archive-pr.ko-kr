---
title: Server의 Database 요소 (DTA) | Microsoft Docs
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
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a48d255898eff6bd780f8edf2c8d2da7229b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727652"
---
# <a name="database-element-for-server-dta"></a><span data-ttu-id="b5da0-102">Server의 Database 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="b5da0-102">Database Element for Server (DTA)</span></span>
  <span data-ttu-id="b5da0-103">특정 서버에서 튜닝할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5da0-103">Specifies the database you want to tune on a specific server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5da0-104">구문</span><span class="sxs-lookup"><span data-stu-id="b5da0-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="b5da0-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="b5da0-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="b5da0-106">특성</span><span class="sxs-lookup"><span data-stu-id="b5da0-106">Characteristic</span></span>|<span data-ttu-id="b5da0-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5da0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b5da0-108">데이터 형식 및 길이</span><span class="sxs-lookup"><span data-stu-id="b5da0-108">Data type and length</span></span>|<span data-ttu-id="b5da0-109">없음</span><span class="sxs-lookup"><span data-stu-id="b5da0-109">None.</span></span>|  
|<span data-ttu-id="b5da0-110">기본값</span><span class="sxs-lookup"><span data-stu-id="b5da0-110">Default value</span></span>|<span data-ttu-id="b5da0-111">없음</span><span class="sxs-lookup"><span data-stu-id="b5da0-111">None.</span></span>|  
|<span data-ttu-id="b5da0-112">발생 빈도</span><span class="sxs-lookup"><span data-stu-id="b5da0-112">Occurrence</span></span>|<span data-ttu-id="b5da0-113">`Server` 요소마다 한 번 이상 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5da0-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="b5da0-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="b5da0-114">Element Relationships</span></span>  
  
|<span data-ttu-id="b5da0-115">관계</span><span class="sxs-lookup"><span data-stu-id="b5da0-115">Relationship</span></span>|<span data-ttu-id="b5da0-116">요소</span><span class="sxs-lookup"><span data-stu-id="b5da0-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="b5da0-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b5da0-117">Parent element</span></span>|[<span data-ttu-id="b5da0-118">Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="b5da0-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="b5da0-119">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b5da0-119">Child elements</span></span>|[<span data-ttu-id="b5da0-120">Database의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="b5da0-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="b5da0-121">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="b5da0-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="b5da0-122">설명</span><span class="sxs-lookup"><span data-stu-id="b5da0-122">Remarks</span></span>  
 <span data-ttu-id="b5da0-123">데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **DatabaseDetailsTypecomplexType** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b5da0-123">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="b5da0-124">이 `Database` 요소와 `Configuration` 요소가 루트 부모인 요소를 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b5da0-124">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="b5da0-125">자세한 내용은 [Configuration의 Database 요소&#40;DTA&#41;](database-element-for-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5da0-125">For more information, see [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5da0-126">예제</span><span class="sxs-lookup"><span data-stu-id="b5da0-126">Example</span></span>  
 <span data-ttu-id="b5da0-127">요소의 사용 예제를 `Database` 보려면 [Server 요소 &#40;DTA&#41;](server-element-dta.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5da0-127">For a usage example of the `Database` element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5da0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5da0-128">See Also</span></span>  
 [<span data-ttu-id="b5da0-129">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="b5da0-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
