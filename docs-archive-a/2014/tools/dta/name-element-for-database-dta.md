---
title: Database의 Name 요소 (DTA) | Microsoft Docs
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
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: c692e31b9175bf05dcfb0504ea79e98cbb82f36b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727619"
---
# <a name="name-element-for-database-dta"></a><span data-ttu-id="8dc7a-102">Database의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="8dc7a-102">Name Element for Database (DTA)</span></span>
  <span data-ttu-id="8dc7a-103">튜닝할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc7a-103">Specifies the name of a database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc7a-104">구문</span><span class="sxs-lookup"><span data-stu-id="8dc7a-104">Syntax</span></span>  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="8dc7a-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="8dc7a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="8dc7a-106">특성</span><span class="sxs-lookup"><span data-stu-id="8dc7a-106">Characteristic</span></span>|<span data-ttu-id="8dc7a-107">Description</span><span class="sxs-lookup"><span data-stu-id="8dc7a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8dc7a-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="8dc7a-108">**Data type and length**</span></span>|<span data-ttu-id="8dc7a-109">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="8dc7a-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="8dc7a-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="8dc7a-110">**Default value**</span></span>|<span data-ttu-id="8dc7a-111">없음</span><span class="sxs-lookup"><span data-stu-id="8dc7a-111">None.</span></span>|  
|<span data-ttu-id="8dc7a-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="8dc7a-112">**Occurrence**</span></span>|<span data-ttu-id="8dc7a-113">각 `Database` 요소 당 한 번씩만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc7a-113">Required once per `Database` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8dc7a-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="8dc7a-114">Element Relationships</span></span>  
  
|<span data-ttu-id="8dc7a-115">관계</span><span class="sxs-lookup"><span data-stu-id="8dc7a-115">Relationship</span></span>|<span data-ttu-id="8dc7a-116">요소</span><span class="sxs-lookup"><span data-stu-id="8dc7a-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8dc7a-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="8dc7a-117">**Parent element**</span></span>|[<span data-ttu-id="8dc7a-118">Server의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="8dc7a-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="8dc7a-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="8dc7a-119">**Child elements**</span></span>|<span data-ttu-id="8dc7a-120">없음</span><span class="sxs-lookup"><span data-stu-id="8dc7a-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8dc7a-121">예제</span><span class="sxs-lookup"><span data-stu-id="8dc7a-121">Example</span></span>  
 <span data-ttu-id="8dc7a-122">이 요소의 사용 예는 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8dc7a-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc7a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8dc7a-123">See Also</span></span>  
 [<span data-ttu-id="8dc7a-124">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="8dc7a-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
