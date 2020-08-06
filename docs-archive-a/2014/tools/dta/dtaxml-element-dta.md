---
title: DTAXML 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f428cf996bb819ece74c13226fcd5116a19142b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734803"
---
# <a name="dtaxml-element-dta"></a><span data-ttu-id="d83e8-102">DTAXML 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="d83e8-102">DTAXML Element (DTA)</span></span>
  <span data-ttu-id="d83e8-103">데이터베이스 엔진 튜닝 관리자 XML 입력 또는 출력 파일의 핵심 요소인 **DTAXML** 에는 데이터베이스 엔진 튜닝 관리자가 생성하는 튜닝 입력 및 튜닝 출력을 설명하는 모든 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-103">The root element of a Database Engine Tuning Advisor XML input or output file, **DTAXML** contains all elements that describe tuning input and the tuning output that Database Engine Tuning Advisor generates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83e8-104">구문</span><span class="sxs-lookup"><span data-stu-id="d83e8-104">Syntax</span></span>  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="d83e8-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="d83e8-105">Element Attributes</span></span>  
  
|<span data-ttu-id="d83e8-106">attribute</span><span class="sxs-lookup"><span data-stu-id="d83e8-106">Attribute</span></span>|<span data-ttu-id="d83e8-107">설명</span><span class="sxs-lookup"><span data-stu-id="d83e8-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns:xsi`|<span data-ttu-id="d83e8-108">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-108">Required.</span></span> <span data-ttu-id="d83e8-109">XML 스키마 인스턴스 네임스페이스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-109">Identifies the XML Schema Instance namespace.</span></span> <span data-ttu-id="d83e8-110">이 네임스페이스의 특성은 데이터베이스 엔진 튜닝 관리자 XML 파일의 유효성을 검사하는 데 사용되는 스키마를 참조하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-110">Attributes from this namespace are used to reference the schema that is used to validate the Database Engine Tuning Advisor XML file.</span></span><br /><br /> <span data-ttu-id="d83e8-111">필요한 값: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span><span class="sxs-lookup"><span data-stu-id="d83e8-111">Required value: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span></span>|  
|`xmlns`|<span data-ttu-id="d83e8-112">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-112">Required.</span></span> <span data-ttu-id="d83e8-113">데이터베이스 엔진 튜닝 관리자 네임스페이스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-113">Identifies the Database Engine Tuning Advisor namespace.</span></span><br /><br /> <span data-ttu-id="d83e8-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 XML 편집기를 사용하여 데이터베이스 엔진 튜닝 관리자 XML 파일을 편집할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 가능한 참조 항목을 찾기 위해 F1 도움말과 동적 도움말에서 이 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-114">If you edit the Database Engine Tuning Advisor XML file using the XML editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this value is used by F1 Help and Dynamic Help to locate possible reference topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span><br /><br /> <span data-ttu-id="d83e8-115">필요한 값:</span><span class="sxs-lookup"><span data-stu-id="d83e8-115">Required value:</span></span><br /><br /> <span data-ttu-id="d83e8-116">[데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?LinkId=43100) 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="d83e8-116">[Database Engine Tuning Advisor XML Schema](https://go.microsoft.com/fwlink/?LinkId=43100) Namespace</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="d83e8-117">요소 특징</span><span class="sxs-lookup"><span data-stu-id="d83e8-117">Element Characteristics</span></span>  
  
|<span data-ttu-id="d83e8-118">특성</span><span class="sxs-lookup"><span data-stu-id="d83e8-118">Characteristic</span></span>|<span data-ttu-id="d83e8-119">Description</span><span class="sxs-lookup"><span data-stu-id="d83e8-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d83e8-120">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="d83e8-120">**Data type and length**</span></span>|<span data-ttu-id="d83e8-121">없음</span><span class="sxs-lookup"><span data-stu-id="d83e8-121">None.</span></span>|  
|<span data-ttu-id="d83e8-122">**기본값**</span><span class="sxs-lookup"><span data-stu-id="d83e8-122">**Default value**</span></span>|<span data-ttu-id="d83e8-123">없음</span><span class="sxs-lookup"><span data-stu-id="d83e8-123">None.</span></span>|  
|<span data-ttu-id="d83e8-124">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="d83e8-124">**Occurrence**</span></span>|<span data-ttu-id="d83e8-125">DTA XML 파일마다 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d83e8-125">Required once per DTA XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d83e8-126">요소 관계</span><span class="sxs-lookup"><span data-stu-id="d83e8-126">Element Relationships</span></span>  
  
|<span data-ttu-id="d83e8-127">관계</span><span class="sxs-lookup"><span data-stu-id="d83e8-127">Relationship</span></span>|<span data-ttu-id="d83e8-128">요소</span><span class="sxs-lookup"><span data-stu-id="d83e8-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d83e8-129">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="d83e8-129">**Parent element**</span></span>|<span data-ttu-id="d83e8-130">None</span><span class="sxs-lookup"><span data-stu-id="d83e8-130">None</span></span>|  
|<span data-ttu-id="d83e8-131">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="d83e8-131">**Child elements**</span></span>|[<span data-ttu-id="d83e8-132">DTAInput 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d83e8-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)<br /><br /> <span data-ttu-id="d83e8-133">`DTAOutput`요소 (자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://schemas.microsoft.com/sqlserver/) 참조)</span><span class="sxs-lookup"><span data-stu-id="d83e8-133">`DTAOutput` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d83e8-134">설명</span><span class="sxs-lookup"><span data-stu-id="d83e8-134">Remarks</span></span>  
 <span data-ttu-id="d83e8-135">XML 네임스페이스에 대한 자세한 내용은 [MSDN Library의](https://go.microsoft.com/fwlink/?LinkId=7341) XML 문서의 네임스페이스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d83e8-135">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d83e8-136">예제</span><span class="sxs-lookup"><span data-stu-id="d83e8-136">Example</span></span>  
 <span data-ttu-id="d83e8-137">일반적인 **DTAXML** 요소의 예는 [XML 입력 파일 예제&#40;DTA&#41;](xml-input-file-samples-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d83e8-137">For examples of typical **DTAXML** elements, see [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83e8-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d83e8-138">See Also</span></span>  
 <span data-ttu-id="d83e8-139">[XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="d83e8-139">[XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="d83e8-140">데이터베이스 엔진 튜닝 관리자 시작 및 사용</span><span class="sxs-lookup"><span data-stu-id="d83e8-140">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
