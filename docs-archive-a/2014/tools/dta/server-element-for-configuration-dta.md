---
title: Configuration의 Server 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88182cdad2e7313f0910a106ee37d727d840bfed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653087"
---
# <a name="server-element-for-configuration-dta"></a><span data-ttu-id="a4f51-102">Configuration의 Server 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="a4f51-102">Server Element for Configuration (DTA)</span></span>
  <span data-ttu-id="a4f51-103">데이터베이스 엔진 튜닝 관리자가 가상 구성(`Configuration` 요소에 의해 지정됨)을 평가하는 서버에 대한 식별 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a4f51-103">Contains the identifying information for the server where you want Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f51-104">구문</span><span class="sxs-lookup"><span data-stu-id="a4f51-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="a4f51-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="a4f51-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="a4f51-106">특성</span><span class="sxs-lookup"><span data-stu-id="a4f51-106">Characteristic</span></span>|<span data-ttu-id="a4f51-107">Description</span><span class="sxs-lookup"><span data-stu-id="a4f51-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a4f51-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="a4f51-108">**Data type and length**</span></span>|<span data-ttu-id="a4f51-109">없음</span><span class="sxs-lookup"><span data-stu-id="a4f51-109">None.</span></span>|  
|<span data-ttu-id="a4f51-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="a4f51-110">**Default value**</span></span>|<span data-ttu-id="a4f51-111">없음</span><span class="sxs-lookup"><span data-stu-id="a4f51-111">None.</span></span>|  
|<span data-ttu-id="a4f51-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="a4f51-112">**Occurrence**</span></span>|<span data-ttu-id="a4f51-113">각 `Configuration` 요소 당 한 번씩만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a4f51-113">Required once per `Configuration` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a4f51-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="a4f51-114">Element Relationships</span></span>  
  
|<span data-ttu-id="a4f51-115">관계</span><span class="sxs-lookup"><span data-stu-id="a4f51-115">Relationship</span></span>|<span data-ttu-id="a4f51-116">요소</span><span class="sxs-lookup"><span data-stu-id="a4f51-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a4f51-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="a4f51-117">**Parent element**</span></span>|[<span data-ttu-id="a4f51-118">Configuration 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f51-118">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
|<span data-ttu-id="a4f51-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="a4f51-119">**Child elements**</span></span>|[<span data-ttu-id="a4f51-120">Server의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f51-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="a4f51-121">Configuration의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f51-121">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="a4f51-122">설명</span><span class="sxs-lookup"><span data-stu-id="a4f51-122">Remarks</span></span>  
 <span data-ttu-id="a4f51-123">`Server`요소에 대해 요소를 하나만 지정할 수 있습니다 `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="a4f51-123">You can specify only one `Server` element for the `Configuration` element.</span></span> <span data-ttu-id="a4f51-124">**데이터베이스 엔진 튜닝 관리자 XML 스키마** 에서 이 요소의 이름은 [ServerTypecomplexType](https://go.microsoft.com/fwlink/?linkid=43100)입니다.</span><span class="sxs-lookup"><span data-stu-id="a4f51-124">This element is of the **ServerTypecomplexType** name in the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span> <span data-ttu-id="a4f51-125">이 `Server` 요소와 `DTAInput` 요소의 자식 요소를 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="a4f51-125">Do not confuse this `Server` element with the one that is the child of the `DTAInput` element.</span></span> <span data-ttu-id="a4f51-126">자세한 내용은 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4f51-126">For more information, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f51-127">예제</span><span class="sxs-lookup"><span data-stu-id="a4f51-127">Example</span></span>  
 <span data-ttu-id="a4f51-128">사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4f51-128">For a usage example, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f51-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4f51-129">See Also</span></span>  
 [<span data-ttu-id="a4f51-130">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f51-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
