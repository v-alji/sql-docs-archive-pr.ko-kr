---
title: Server의 Name 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 202258c3c87f8a35d1ee30b19880f5e9423fa394
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653098"
---
# <a name="name-element-for-server-dta"></a><span data-ttu-id="be35e-102">Server의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="be35e-102">Name Element for Server (DTA)</span></span>
  <span data-ttu-id="be35e-103">튜닝할 데이터베이스가 상주하는 서버의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="be35e-103">Contains the name of the server where the databases you want to tune reside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be35e-104">구문</span><span class="sxs-lookup"><span data-stu-id="be35e-104">Syntax</span></span>  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="be35e-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="be35e-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="be35e-106">특성</span><span class="sxs-lookup"><span data-stu-id="be35e-106">Characteristic</span></span>|<span data-ttu-id="be35e-107">Description</span><span class="sxs-lookup"><span data-stu-id="be35e-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="be35e-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="be35e-108">**Data type and length**</span></span>|<span data-ttu-id="be35e-109">`string`, 1에서 255자 사이</span><span class="sxs-lookup"><span data-stu-id="be35e-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="be35e-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="be35e-110">**Default value**</span></span>|<span data-ttu-id="be35e-111">없음</span><span class="sxs-lookup"><span data-stu-id="be35e-111">None.</span></span>|  
|<span data-ttu-id="be35e-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="be35e-112">**Occurrence**</span></span>|<span data-ttu-id="be35e-113">**Server** 요소마다 한 번만 지정해야 함</span><span class="sxs-lookup"><span data-stu-id="be35e-113">Required once per **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="be35e-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="be35e-114">Element Relationships</span></span>  
  
|<span data-ttu-id="be35e-115">관계</span><span class="sxs-lookup"><span data-stu-id="be35e-115">Relationship</span></span>|<span data-ttu-id="be35e-116">요소</span><span class="sxs-lookup"><span data-stu-id="be35e-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="be35e-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="be35e-117">**Parent element**</span></span>|[<span data-ttu-id="be35e-118">Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="be35e-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="be35e-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="be35e-119">**Child elements**</span></span>|<span data-ttu-id="be35e-120">없음</span><span class="sxs-lookup"><span data-stu-id="be35e-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="be35e-121">예제</span><span class="sxs-lookup"><span data-stu-id="be35e-121">Example</span></span>  
 <span data-ttu-id="be35e-122">이 **Name** 요소의 사용 예는 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be35e-122">For an example of how this **Name** element is used, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be35e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be35e-123">See Also</span></span>  
 [<span data-ttu-id="be35e-124">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="be35e-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
