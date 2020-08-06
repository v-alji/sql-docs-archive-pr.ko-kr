---
title: 배너 요소 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742724"
---
# <a name="banner-element-ssbdiagnose"></a><span data-ttu-id="9e31c-102">Banner 요소(ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="9e31c-102">Banner Element (ssbdiagnose)</span></span>
  <span data-ttu-id="9e31c-103">**ssbdiagnose** 출력 XML 파일을 생성한 유틸리티를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9e31c-103">Identifies which utility generated the **ssbdiagnose** output XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e31c-104">구문</span><span class="sxs-lookup"><span data-stu-id="9e31c-104">Syntax</span></span>  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="9e31c-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="9e31c-105">Element Attributes</span></span>  
  
|<span data-ttu-id="9e31c-106">attribute</span><span class="sxs-lookup"><span data-stu-id="9e31c-106">Attribute</span></span>|<span data-ttu-id="9e31c-107">Description</span><span class="sxs-lookup"><span data-stu-id="9e31c-107">Description</span></span>|  
|---------------|-----------------|  
|`title`|<span data-ttu-id="9e31c-108">**ssbdiagnose** XML 출력 파일을 생성한 유틸리티를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9e31c-108">Identifies the utility that generated the **ssbdiagnose** XML output file.</span></span>|  
|`product`|<span data-ttu-id="9e31c-109">**ssbdiagnose** XML 출력 파일을 생성한 제품을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9e31c-109">Identifies the product that generated the **ssbdiagnose** XML output file.</span></span>|  
|`version`|<span data-ttu-id="9e31c-110">XML 출력 파일을 생성한 유틸리티의 버전을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9e31c-110">Identifies which version of the utility generated the XML output file.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="9e31c-111">요소 특징</span><span class="sxs-lookup"><span data-stu-id="9e31c-111">Element Characteristics</span></span>  
  
|<span data-ttu-id="9e31c-112">특성</span><span class="sxs-lookup"><span data-stu-id="9e31c-112">Characteristic</span></span>|<span data-ttu-id="9e31c-113">Description</span><span class="sxs-lookup"><span data-stu-id="9e31c-113">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9e31c-114">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="9e31c-114">**Data type and length**</span></span>|<span data-ttu-id="9e31c-115">없음</span><span class="sxs-lookup"><span data-stu-id="9e31c-115">None.</span></span>|  
|<span data-ttu-id="9e31c-116">**기본값**</span><span class="sxs-lookup"><span data-stu-id="9e31c-116">**Default value**</span></span>|<span data-ttu-id="9e31c-117">없음</span><span class="sxs-lookup"><span data-stu-id="9e31c-117">None.</span></span>|  
|<span data-ttu-id="9e31c-118">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="9e31c-118">**Occurrence**</span></span>|<span data-ttu-id="9e31c-119">**ssbdiagnose** 출력 XML 파일당 한 번</span><span class="sxs-lookup"><span data-stu-id="9e31c-119">Occurs once per **ssbdiagnose** output XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9e31c-120">요소 관계</span><span class="sxs-lookup"><span data-stu-id="9e31c-120">Element Relationships</span></span>  
  
|<span data-ttu-id="9e31c-121">관계</span><span class="sxs-lookup"><span data-stu-id="9e31c-121">Relationship</span></span>|<span data-ttu-id="9e31c-122">요소</span><span class="sxs-lookup"><span data-stu-id="9e31c-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9e31c-123">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="9e31c-123">**Parent element**</span></span>|[<span data-ttu-id="9e31c-124">DiagnosticInformation 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="9e31c-124">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="9e31c-125">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="9e31c-125">**Child elements**</span></span>|<span data-ttu-id="9e31c-126">없음</span><span class="sxs-lookup"><span data-stu-id="9e31c-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9e31c-127">예제</span><span class="sxs-lookup"><span data-stu-id="9e31c-127">Example</span></span>  
 <span data-ttu-id="9e31c-128">다음은 Banner 요소의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9e31c-128">This is an example of a banner element.</span></span>  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e31c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e31c-129">See Also</span></span>  
 [<span data-ttu-id="9e31c-130">ssbdiagnose 유틸리티&#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="9e31c-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
