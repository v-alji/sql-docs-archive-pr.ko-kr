---
title: Table의 Name 요소 (DTA) | Microsoft Docs
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fa8481cf8990fb63995abcb6300cd9a352c859a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653095"
---
# <a name="name-element-for-table-dta"></a><span data-ttu-id="bf26e-102">Table의 Name 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="bf26e-102">Name Element for Table (DTA)</span></span>
  <span data-ttu-id="bf26e-103">튜닝을 위한 테이블 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf26e-103">Specifies a table name for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf26e-104">구문</span><span class="sxs-lookup"><span data-stu-id="bf26e-104">Syntax</span></span>  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="bf26e-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="bf26e-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="bf26e-106">특성</span><span class="sxs-lookup"><span data-stu-id="bf26e-106">Characteristic</span></span>|<span data-ttu-id="bf26e-107">Description</span><span class="sxs-lookup"><span data-stu-id="bf26e-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="bf26e-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="bf26e-108">**Data type and length**</span></span>|<span data-ttu-id="bf26e-109">`string`, 1에서 255자 사이</span><span class="sxs-lookup"><span data-stu-id="bf26e-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="bf26e-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="bf26e-110">**Default value**</span></span>|<span data-ttu-id="bf26e-111">없음</span><span class="sxs-lookup"><span data-stu-id="bf26e-111">None.</span></span>|  
|<span data-ttu-id="bf26e-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="bf26e-112">**Occurrence**</span></span>|<span data-ttu-id="bf26e-113">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bf26e-113">Required.</span></span> <span data-ttu-id="bf26e-114">각 `Table` 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf26e-114">Once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="bf26e-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="bf26e-115">Element Relationships</span></span>  
  
|<span data-ttu-id="bf26e-116">관계</span><span class="sxs-lookup"><span data-stu-id="bf26e-116">Relationship</span></span>|<span data-ttu-id="bf26e-117">요소</span><span class="sxs-lookup"><span data-stu-id="bf26e-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="bf26e-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="bf26e-118">**Parent element**</span></span>|[<span data-ttu-id="bf26e-119">Schema의 Table 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="bf26e-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="bf26e-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="bf26e-120">**Child elements**</span></span>|<span data-ttu-id="bf26e-121">없음</span><span class="sxs-lookup"><span data-stu-id="bf26e-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf26e-122">예제</span><span class="sxs-lookup"><span data-stu-id="bf26e-122">Example</span></span>  
 <span data-ttu-id="bf26e-123">사용 예를 보려면 [Server 요소&#40;DTA&#41;](server-element-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf26e-123">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf26e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf26e-124">See Also</span></span>  
 [<span data-ttu-id="bf26e-125">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="bf26e-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
