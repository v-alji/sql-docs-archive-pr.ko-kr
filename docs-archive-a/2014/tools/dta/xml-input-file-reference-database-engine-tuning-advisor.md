---
title: XML 입력 파일 참조(데이터베이스 엔진 튜닝 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3bbd38299e4921db33cbaf318883c2f0a9041d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741496"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a><span data-ttu-id="0f3e4-102">XML 입력 파일 참조(데이터베이스 엔진 튜닝 관리자)</span><span class="sxs-lookup"><span data-stu-id="0f3e4-102">XML Input File Reference (Database Engine Tuning Advisor)</span></span>
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="0f3e4-103">튜닝 관리자는 XML 입력 파일을 사용하여 데이터베이스를 튜닝할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-103">Tuning Advisor can use an XML input file to tune a database.</span></span> <span data-ttu-id="0f3e4-104">이 XML 파일은 튜닝 세션에 사용할 데이터베이스, 테이블, 작업 파일 또는 테이블 및 튜닝 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-104">This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session.</span></span> <span data-ttu-id="0f3e4-105">또한 이 파일을 사용하면 "가정(what-if)" 분석을 수행하기 위한 사용자 지정 구성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-105">You can also use this file to specify a user-specified configuration to perform "what-if" analysis.</span></span>  
  
 <span data-ttu-id="0f3e4-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 입력 파일은 튜닝 세션 설정을 지정하는 텍스트 또는 기타 요소가 각각 포함되어 있는 XML 요소의 계층을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-106">A [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings.</span></span> <span data-ttu-id="0f3e4-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 입력 파일은 올바른 형식의 XML에 대한 표준을 따라야 하므로 모든 요소 이름이 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive.</span></span> <span data-ttu-id="0f3e4-108">요소는 파스칼 대/소문자를 사용하여 지정하는 데 이는 첫 글자가 대문자이고 이후의 모든 연결 단어의 첫 글자가 대문자라는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-108">Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.</span></span>  
  
 <span data-ttu-id="0f3e4-109">모든 요소 값은 XML 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-109">All element values must conform to XML naming conventions.</span></span> <span data-ttu-id="0f3e4-110">이러한 규칙에 대한 자세한 내용은 MSDN Library에서 [XML 텍스트 콘텐츠(XML Textual Content)](https://go.microsoft.com/fwlink/?LinkId=7614) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-110">For more information about these conventions, see [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.</span></span>  
  
 <span data-ttu-id="0f3e4-111">이 참조에서 전체 내용을 다루지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-111">Note that this reference is not comprehensive.</span></span> <span data-ttu-id="0f3e4-112">XML 입력을 정의하는 데 사용할 수 있는 모든 요소에 대한 자세한 내용은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마 DTASchema.xsd를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0f3e4-112">For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema, DTASchema.xsd.</span></span>  
  
## <a name="xml-declaration"></a><span data-ttu-id="0f3e4-113">XML 선언</span><span class="sxs-lookup"><span data-stu-id="0f3e4-113">XML Declaration</span></span>  
  
-   [<span data-ttu-id="0f3e4-114">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-114">XML Data &#40;SQL Server&#41;</span></span>](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a><span data-ttu-id="0f3e4-115">DTAXML 루트 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-115">DTAXML Root Element</span></span>  
  
-   [<span data-ttu-id="0f3e4-116">DTAXML 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-116">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a><span data-ttu-id="0f3e4-117">DTAInput 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-117">DTAInput Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-118">DTAInput 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-119">Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-119">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-120">Workload 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-121">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-121">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-122">Configuration 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-122">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)  
  
## <a name="server-elements"></a><span data-ttu-id="0f3e4-123">Server 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-123">Server Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-124">Server의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-124">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)  
  
-   [<span data-ttu-id="0f3e4-125">Server의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-125">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a><span data-ttu-id="0f3e4-126">Workload 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-126">Workload Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-127">File 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-127">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-128">Workload의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-128">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)  
  
-   [<span data-ttu-id="0f3e4-129">EventString 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-129">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a><span data-ttu-id="0f3e4-130">튜닝 옵션 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-130">Tuning Options Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-131">TuningTimeInMin 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-131">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-132">StorageBoundInMB 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-132">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-133">TestServer 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-133">TestServer Element &#40;DTA&#41;</span></span>](testserver-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-134">FeatureSet 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-134">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-135">Partitioning 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-135">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-136">DropOnlyMode 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-136">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-137">KeepExisting 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-137">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-138">OnlineIndexOperation 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-138">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-139">DatabaseToConnect 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-139">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a><span data-ttu-id="0f3e4-140">Configuration 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-140">Configuration Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-141">Configuration의 Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-141">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="0f3e4-142">Configuration의 Database 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-142">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="0f3e4-143">Recommendation 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-143">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-144">Create 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-144">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-145">Index 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-145">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)  
  
-   [<span data-ttu-id="0f3e4-146">Index의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-146">Name Element for Index &#40;DTA&#41;</span></span>](name-element-for-index-dta.md)  
  
-   [<span data-ttu-id="0f3e4-147">Index의 Column 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-147">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)  
  
-   [<span data-ttu-id="0f3e4-148">Column의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-148">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)  
  
-   [<span data-ttu-id="0f3e4-149">Index의 Filegroup 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-149">Filegroup Element for Index &#40;DTA&#41;</span></span>](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a><span data-ttu-id="0f3e4-150">Database 요소</span><span class="sxs-lookup"><span data-stu-id="0f3e4-150">Database Elements</span></span>  
  
-   [<span data-ttu-id="0f3e4-151">Database의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-151">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)  
  
-   [<span data-ttu-id="0f3e4-152">Database의 Schema 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-152">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)  
  
-   [<span data-ttu-id="0f3e4-153">Schema의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-153">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="0f3e4-154">Schema의 Table 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-154">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="0f3e4-155">Table의 Name 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0f3e4-155">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f3e4-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f3e4-156">See Also</span></span>  
 [<span data-ttu-id="0f3e4-157">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="0f3e4-157">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
