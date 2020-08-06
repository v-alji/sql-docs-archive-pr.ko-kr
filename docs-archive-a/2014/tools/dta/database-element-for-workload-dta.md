---
title: 작업 (DTA)의 Database 요소 | Microsoft Docs
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
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2774bc7ed981c84c966a394c95347208cbc6d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727656"
---
# <a name="database-element-for-workload-dta"></a><span data-ttu-id="c70f0-102">Workload의 Database 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="c70f0-102">Database Element for Workload (DTA)</span></span>
  <span data-ttu-id="c70f0-103">작업 추적 테이블이 위치하는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c70f0-103">Specifies the database where the workload trace table is located.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c70f0-104">구문</span><span class="sxs-lookup"><span data-stu-id="c70f0-104">Syntax</span></span>  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c70f0-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="c70f0-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="c70f0-106">특성</span><span class="sxs-lookup"><span data-stu-id="c70f0-106">Characteristic</span></span>|<span data-ttu-id="c70f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="c70f0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c70f0-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="c70f0-108">**Data type and length**</span></span>|<span data-ttu-id="c70f0-109">없음</span><span class="sxs-lookup"><span data-stu-id="c70f0-109">None.</span></span>|  
|<span data-ttu-id="c70f0-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="c70f0-110">**Default value**</span></span>|<span data-ttu-id="c70f0-111">없음</span><span class="sxs-lookup"><span data-stu-id="c70f0-111">None.</span></span>|  
|<span data-ttu-id="c70f0-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="c70f0-112">**Occurrence**</span></span>|<span data-ttu-id="c70f0-113">다른 작업 유형이 지정되지 않은 경우 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70f0-113">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="c70f0-114">`EventString` 부모에 대해 `File`, `Database` 또는 `Workload` 자식 요소를 지정해야 하지만 한 유형만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70f0-114">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="c70f0-115">예를 들어 `Database` 요소로 작업을 지정할 경우 동일한 XML 입력 파일에서 `File` 요소로 작업을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c70f0-115">For example, if you specify a workload with the `Database` element, you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c70f0-116">요소 관계</span><span class="sxs-lookup"><span data-stu-id="c70f0-116">Element Relationships</span></span>  
  
|<span data-ttu-id="c70f0-117">관계</span><span class="sxs-lookup"><span data-stu-id="c70f0-117">Relationship</span></span>|<span data-ttu-id="c70f0-118">요소</span><span class="sxs-lookup"><span data-stu-id="c70f0-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c70f0-119">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="c70f0-119">**Parent element**</span></span>|[<span data-ttu-id="c70f0-120">Workload 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="c70f0-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="c70f0-121">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="c70f0-121">**Child elements**</span></span>|[<span data-ttu-id="c70f0-122">Database의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="c70f0-122">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="c70f0-123">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="c70f0-123">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="c70f0-124">설명</span><span class="sxs-lookup"><span data-stu-id="c70f0-124">Remarks</span></span>  
 <span data-ttu-id="c70f0-125">데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **DatabaseDetailsTypecomplexType** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c70f0-125">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="c70f0-126">이 `Database` 요소와 `Configuration` 요소가 루트 부모인 요소를 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c70f0-126">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="c70f0-127">[Configuration의 Database 요소&#40;DTA&#41;](database-element-for-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c70f0-127">(See [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).)</span></span>  
  
## <a name="example"></a><span data-ttu-id="c70f0-128">예제</span><span class="sxs-lookup"><span data-stu-id="c70f0-128">Example</span></span>  
 <span data-ttu-id="c70f0-129">이 요소의 사용 예는 `Database` [DTA&#41;&#40;작업 요소 ](workload-element-dta.md)의 코드 예제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70f0-129">For a usage example of this `Database` element, see the code example in [Workload Element &#40;DTA&#41;](workload-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70f0-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c70f0-130">See Also</span></span>  
 [<span data-ttu-id="c70f0-131">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="c70f0-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
