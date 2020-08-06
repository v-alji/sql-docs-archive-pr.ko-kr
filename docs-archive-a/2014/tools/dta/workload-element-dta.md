---
title: 작업 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20184760c3fcb5eed6c02b8f8fd9b63f5586c9af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649881"
---
# <a name="workload-element-dta"></a><span data-ttu-id="cb30d-102">Workload 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="cb30d-102">Workload Element (DTA)</span></span>
  <span data-ttu-id="cb30d-103">튜닝 세션에 사용할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-103">Specifies the workload to be used for a tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb30d-104">구문</span><span class="sxs-lookup"><span data-stu-id="cb30d-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="cb30d-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="cb30d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="cb30d-106">특성</span><span class="sxs-lookup"><span data-stu-id="cb30d-106">Characteristic</span></span>|<span data-ttu-id="cb30d-107">Description</span><span class="sxs-lookup"><span data-stu-id="cb30d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cb30d-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="cb30d-108">**Data type and length**</span></span>|<span data-ttu-id="cb30d-109">없음</span><span class="sxs-lookup"><span data-stu-id="cb30d-109">None.</span></span>|  
|<span data-ttu-id="cb30d-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="cb30d-110">**Default value**</span></span>|<span data-ttu-id="cb30d-111">없음</span><span class="sxs-lookup"><span data-stu-id="cb30d-111">None.</span></span>|  
|<span data-ttu-id="cb30d-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="cb30d-112">**Occurrence**</span></span>|<span data-ttu-id="cb30d-113">각 `DTAInput` 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-113">Required once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="cb30d-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="cb30d-114">Element Relationships</span></span>  
  
|<span data-ttu-id="cb30d-115">관계</span><span class="sxs-lookup"><span data-stu-id="cb30d-115">Relationship</span></span>|<span data-ttu-id="cb30d-116">요소</span><span class="sxs-lookup"><span data-stu-id="cb30d-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="cb30d-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="cb30d-117">**Parent element**</span></span>|[<span data-ttu-id="cb30d-118">데이터베이스 엔진 튜닝 관리자 시작 및 사용</span><span class="sxs-lookup"><span data-stu-id="cb30d-118">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|<span data-ttu-id="cb30d-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="cb30d-119">**Child elements**</span></span>|[<span data-ttu-id="cb30d-120">File 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="cb30d-120">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)<br /><br /> [<span data-ttu-id="cb30d-121">Workload의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="cb30d-121">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)<br /><br /> [<span data-ttu-id="cb30d-122">EventString 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="cb30d-122">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="cb30d-123">설명</span><span class="sxs-lookup"><span data-stu-id="cb30d-123">Remarks</span></span>  
 <span data-ttu-id="cb30d-124">작업은 튜닝하려는 데이터베이스에 대해 실행되는 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-124">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="cb30d-125">데이터베이스 엔진 튜닝 관리자는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트, 추적 파일 및 추적 테이블을 작업으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-125">The Database Engine Tuning Advisor can use [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, trace files, and trace tables as workloads.</span></span>  
  
 <span data-ttu-id="cb30d-126">XML 입력 파일에 작업을 지정하고 **dta** 도구를 사용하여 명령줄에 작업을 지정할 경우 명령줄에 지정한 작업이 튜닝에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-126">If you specify a workload in an XML input file and a workload on the command line with the **dta** tool, the workload specified on the command line will be used for tuning.</span></span> <span data-ttu-id="cb30d-127">명령줄에 지정한 모든 튜닝 옵션은 XML 입력 파일에 지정된 옵션보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-127">All tuning options specified on the command line override those that are specified in an XML input file.</span></span> <span data-ttu-id="cb30d-128">단, 사용자 지정 구성을 XML 입력 파일에 평가 모드로 입력할 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-128">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="cb30d-129">예를 들어 XML 입력 파일의 `Configuration` 요소에 구성이 입력되었고 또한 `EvaluateConfiguration` 요소가 튜닝 옵션 중 하나로 지정될 경우 XML 입력 파일에 지정된 튜닝 옵션은 명령줄에 입력한 튜닝 옵션보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-129">For example, if a configuration is entered in the `Configuration` element of the XML input file and the `EvaluateConfiguration` element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered at the command line.</span></span>  
  
 <span data-ttu-id="cb30d-130">각 튜닝 세션에 대해 하나의 작업을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-130">One workload must be specified for each tuning session.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb30d-131">예제</span><span class="sxs-lookup"><span data-stu-id="cb30d-131">Example</span></span>  
 <span data-ttu-id="cb30d-132">다음 코드 예에서는 요소에 대 한 **Mydatabase. TuningTable001** 추적 테이블을 지정 합니다. `Workload`</span><span class="sxs-lookup"><span data-stu-id="cb30d-132">The following code example specifies the **MyDatabase.MyDBOwner.TuningTable001** trace table for the `Workload` element.</span></span> <span data-ttu-id="cb30d-133">**TuningTable001** 은 SQL Server 프로파일러로 튜닝 템플릿을 사용하여 추적 결과를 테이블로 저장하는 방식으로 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb30d-133">The **TuningTable001** was created by using the Tuning template with SQL Server Profiler and saving the trace output as a table.</span></span>  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb30d-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb30d-134">See Also</span></span>  
 [<span data-ttu-id="cb30d-135">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="cb30d-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
