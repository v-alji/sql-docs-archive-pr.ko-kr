---
title: Database의 Schema 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7653177878f3a832abd2d1ca266bc5feb17b9a29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647409"
---
# <a name="schema-element-for-database-dta"></a><span data-ttu-id="3d595-102">Database의 Schema 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="3d595-102">Schema Element for Database (DTA)</span></span>
  <span data-ttu-id="3d595-103">튜닝할 데이터베이스의 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d595-103">Specifies the schema of the database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d595-104">구문</span><span class="sxs-lookup"><span data-stu-id="3d595-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="3d595-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="3d595-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="3d595-106">특성</span><span class="sxs-lookup"><span data-stu-id="3d595-106">Characteristic</span></span>|<span data-ttu-id="3d595-107">Description</span><span class="sxs-lookup"><span data-stu-id="3d595-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3d595-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="3d595-108">**Data type and length**</span></span>|<span data-ttu-id="3d595-109">없음</span><span class="sxs-lookup"><span data-stu-id="3d595-109">None.</span></span>|  
|<span data-ttu-id="3d595-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="3d595-110">**Default value**</span></span>|<span data-ttu-id="3d595-111">없음</span><span class="sxs-lookup"><span data-stu-id="3d595-111">None.</span></span>|  
|<span data-ttu-id="3d595-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="3d595-112">**Occurrence**</span></span>|<span data-ttu-id="3d595-113">**Server** 요소 아래 지정된 **Database** 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d595-113">Required once for the **Database** element that is specified under the **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="3d595-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="3d595-114">Element Relationships</span></span>  
  
|<span data-ttu-id="3d595-115">관계</span><span class="sxs-lookup"><span data-stu-id="3d595-115">Relationship</span></span>|<span data-ttu-id="3d595-116">요소</span><span class="sxs-lookup"><span data-stu-id="3d595-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="3d595-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="3d595-117">**Parent element**</span></span>|[<span data-ttu-id="3d595-118">Server의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3d595-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="3d595-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="3d595-119">**Child elements**</span></span>|[<span data-ttu-id="3d595-120">Schema의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3d595-120">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)<br /><br /> [<span data-ttu-id="3d595-121">Schema의 Table 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3d595-121">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="3d595-122">예제</span><span class="sxs-lookup"><span data-stu-id="3d595-122">Example</span></span>  
 <span data-ttu-id="3d595-123">이 요소의 사용 예는 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d595-123">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d595-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d595-124">See Also</span></span>  
 [<span data-ttu-id="3d595-125">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="3d595-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
