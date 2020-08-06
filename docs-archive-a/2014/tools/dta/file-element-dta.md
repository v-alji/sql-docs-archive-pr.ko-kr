---
title: File 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0eeb2bdcc9513ca6283447daca63c8bbc4fa1726
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735751"
---
# <a name="file-element-dta"></a><span data-ttu-id="d5da0-102">File 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="d5da0-102">File Element (DTA)</span></span>
  <span data-ttu-id="d5da0-103">작업 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-103">Specifies the workload file.</span></span> <span data-ttu-id="d5da0-104">작업은 튜닝하려는 데이터베이스에 대해 실행되는 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-104">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="d5da0-105">작업 파일은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트(.sql) 또는 추적 파일(.trc)이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-105">Workload files can be [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts (.sql) or trace files (.trc).</span></span> <span data-ttu-id="d5da0-106">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 시작 및 사용](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5da0-106">For more information, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5da0-107">구문</span><span class="sxs-lookup"><span data-stu-id="d5da0-107">Syntax</span></span>  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d5da0-108">요소 특징</span><span class="sxs-lookup"><span data-stu-id="d5da0-108">Element Characteristics</span></span>  
  
|<span data-ttu-id="d5da0-109">특성</span><span class="sxs-lookup"><span data-stu-id="d5da0-109">Characteristic</span></span>|<span data-ttu-id="d5da0-110">Description</span><span class="sxs-lookup"><span data-stu-id="d5da0-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d5da0-111">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="d5da0-111">**Data type and length**</span></span>|<span data-ttu-id="d5da0-112">`string` 데이터 형식을 사용하여 작업 파일의 디렉터리 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-112">Use the `string` data type to specify the directory path to your workload file.</span></span> <span data-ttu-id="d5da0-113">예:</span><span class="sxs-lookup"><span data-stu-id="d5da0-113">For example:</span></span><br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> <span data-ttu-id="d5da0-114">서버에서 지정하는 길이 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-114">Length limit is enforced by the server.</span></span>|  
|<span data-ttu-id="d5da0-115">**기본값**</span><span class="sxs-lookup"><span data-stu-id="d5da0-115">**Default value**</span></span>|<span data-ttu-id="d5da0-116">없음</span><span class="sxs-lookup"><span data-stu-id="d5da0-116">None.</span></span>|  
|<span data-ttu-id="d5da0-117">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="d5da0-117">**Occurrence**</span></span>|<span data-ttu-id="d5da0-118">다른 작업 유형이 지정되지 않은 경우 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-118">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="d5da0-119">**EventString**부모에 대해 **File**, **Database** 또는 **Workload** 자식 요소를 지정해야 하지만 한 유형만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-119">You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used.</span></span> <span data-ttu-id="d5da0-120">예를 들어 **File** 요소로 작업을 지정할 경우 동일한 XML 입력 파일에서 **Database** 요소로 작업을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5da0-120">For example, if you specify a workload with the **File** element, then you cannot also specify a workload with the **Database** element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d5da0-121">요소 관계</span><span class="sxs-lookup"><span data-stu-id="d5da0-121">Element Relationships</span></span>  
  
|<span data-ttu-id="d5da0-122">관계</span><span class="sxs-lookup"><span data-stu-id="d5da0-122">Relationship</span></span>|<span data-ttu-id="d5da0-123">요소</span><span class="sxs-lookup"><span data-stu-id="d5da0-123">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d5da0-124">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="d5da0-124">**Parent element**</span></span>|[<span data-ttu-id="d5da0-125">Workload 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d5da0-125">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="d5da0-126">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="d5da0-126">**Child elements**</span></span>|<span data-ttu-id="d5da0-127">없음</span><span class="sxs-lookup"><span data-stu-id="d5da0-127">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d5da0-128">예제</span><span class="sxs-lookup"><span data-stu-id="d5da0-128">Example</span></span>  
 <span data-ttu-id="d5da0-129">이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5da0-129">For a usage example of this element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5da0-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5da0-130">See Also</span></span>  
 [<span data-ttu-id="d5da0-131">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="d5da0-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
