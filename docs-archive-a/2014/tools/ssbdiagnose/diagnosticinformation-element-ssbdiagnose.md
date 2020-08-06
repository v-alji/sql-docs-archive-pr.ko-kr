---
title: DiagnosticInformation 요소 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92d76a065c24ddc1fc8d85989ed3202308571951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648250"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a><span data-ttu-id="26768-102">DiagnosticInformation 요소(ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="26768-102">DiagnosticInformation Element (ssbdiagnose)</span></span>
  <span data-ttu-id="26768-103">**DiagnosticInformation** 요소에는  유틸리티가 발견한 진단 정보를 보고하는 모든 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="26768-103">The **DiagnosticInformation** element contains all elements that report the diagnostic information found by the utility.</span></span> <span data-ttu-id="26768-104">**DiagnosticInformation** 은 **ssbdiagnostic** XML 출력 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="26768-104">**DiagnosticInformation** is the root element of a **ssbdiagnostic** XML output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26768-105">구문</span><span class="sxs-lookup"><span data-stu-id="26768-105">Syntax</span></span>  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="26768-106">요소 특성</span><span class="sxs-lookup"><span data-stu-id="26768-106">Element Attributes</span></span>  
  
|<span data-ttu-id="26768-107">attribute</span><span class="sxs-lookup"><span data-stu-id="26768-107">Attribute</span></span>|<span data-ttu-id="26768-108">Description</span><span class="sxs-lookup"><span data-stu-id="26768-108">Description</span></span>|  
|---------------|-----------------|  
|`None`|<span data-ttu-id="26768-109">해당 없음</span><span class="sxs-lookup"><span data-stu-id="26768-109">N/A</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="26768-110">요소 특징</span><span class="sxs-lookup"><span data-stu-id="26768-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="26768-111">특성</span><span class="sxs-lookup"><span data-stu-id="26768-111">Characteristic</span></span>|<span data-ttu-id="26768-112">Description</span><span class="sxs-lookup"><span data-stu-id="26768-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="26768-113">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="26768-113">**Data type and length**</span></span>|<span data-ttu-id="26768-114">없음</span><span class="sxs-lookup"><span data-stu-id="26768-114">None.</span></span>|  
|<span data-ttu-id="26768-115">**기본값**</span><span class="sxs-lookup"><span data-stu-id="26768-115">**Default value**</span></span>|<span data-ttu-id="26768-116">없음</span><span class="sxs-lookup"><span data-stu-id="26768-116">None.</span></span>|  
|<span data-ttu-id="26768-117">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="26768-117">**Occurrence**</span></span>|<span data-ttu-id="26768-118">**ssbdiagnose** XML 출력 파일당 한 번</span><span class="sxs-lookup"><span data-stu-id="26768-118">Once per **ssbdiagnose** XML output file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="26768-119">요소 관계</span><span class="sxs-lookup"><span data-stu-id="26768-119">Element Relationships</span></span>  
  
|<span data-ttu-id="26768-120">관계</span><span class="sxs-lookup"><span data-stu-id="26768-120">Relationship</span></span>|<span data-ttu-id="26768-121">요소</span><span class="sxs-lookup"><span data-stu-id="26768-121">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="26768-122">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="26768-122">**Parent element**</span></span>|<span data-ttu-id="26768-123">없음</span><span class="sxs-lookup"><span data-stu-id="26768-123">None.</span></span>|  
|<span data-ttu-id="26768-124">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="26768-124">**Child elements**</span></span>|[<span data-ttu-id="26768-125">Banner 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="26768-125">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)<br /><br /> [<span data-ttu-id="26768-126">Issue 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="26768-126">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a><span data-ttu-id="26768-127">설명</span><span class="sxs-lookup"><span data-stu-id="26768-127">Remarks</span></span>  
 <span data-ttu-id="26768-128">XML 네임스페이스에 대한 자세한 내용은 [MSDN Library의](https://go.microsoft.com/fwlink/?LinkId=7341) XML 문서의 네임스페이스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26768-128">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26768-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26768-129">See Also</span></span>  
 [<span data-ttu-id="26768-130">ssbdiagnose 유틸리티&#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="26768-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
