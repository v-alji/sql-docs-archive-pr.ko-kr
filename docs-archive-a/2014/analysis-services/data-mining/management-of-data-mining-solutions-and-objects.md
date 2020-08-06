---
title: 데이터 마이닝 솔루션 및 개체 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae3e672932dd320c6b369f23f03c1f056d30d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639109"
---
# <a name="management-of-data-mining-solutions-and-objects"></a><span data-ttu-id="2315a-102">데이터 마이닝 솔루션 및 개체 관리</span><span class="sxs-lookup"><span data-stu-id="2315a-102">Management of Data Mining Solutions and Objects</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="2315a-103">는 기존 마이닝 구조와 마이닝 모델을 관리하는 데 활용할 수 있는 클라이언트 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-103">provides client tools that you can use to manage existing mining structures and mining models.</span></span> <span data-ttu-id="2315a-104">이 섹션에서는 각 환경을 사용하여 수행할 수 있는 관리 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-104">This section describes the management operations that you can perform using each environment.</span></span>  
  
 <span data-ttu-id="2315a-105">이러한 도구 외에도 AMO를 사용하여 프로그래밍 방식으로 데이터 마이닝 개체를 관리하거나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2007용 데이터 마이닝 추가 기능과 같이 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 데이터베이스에 연결되는 다른 클라이언트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-105">In addition to these tools, you can manage data mining objects programmatically, by using AMO, or use other clients that connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2315a-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2315a-106">In this Section</span></span>  
 [<span data-ttu-id="2315a-107">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="2315a-107">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 [<span data-ttu-id="2315a-108">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="2315a-108">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
 [<span data-ttu-id="2315a-109">SQL Server Profiler를 사용하여 데이터 마이닝 모니터링&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="2315a-109">Using SQL Server Profiler to Monitor Data Mining &#40;Analysis Services - Data Mining&#41;</span></span>](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a><span data-ttu-id="2315a-110">데이터 마이닝 개체 위치</span><span class="sxs-lookup"><span data-stu-id="2315a-110">Location of Data Mining Objects</span></span>  
 <span data-ttu-id="2315a-111">처리된 마이닝 구조 및 모델은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-111">Mining structures and models that have been processed are stored in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2315a-112">데이터 마이닝 개체를 개발할 때 모드에서 데이터베이스에 대 한 연결을 만드는 경우 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Immediate` 만드는 모든 개체는 작업 하는 동안 서버에 즉시 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-112">If you create a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in `Immediate` mode when developing your data mining objects, any objects that you create are immediately added to the server as you work.</span></span> <span data-ttu-id="2315a-113">그러나 \*\*\*\* 에서 작업할 때의 기본 설정인 오프라인 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]모드에서 데이터 마이닝 개체를 디자인하는 경우에는 만드는 마이닝 개체가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스로 배포되기 전까지 메타데이터 컨테이너일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-113">However, if you design data mining objects in **Offline** mode, which is the default when you work in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the mining objects that you create are only metadata containers until you deploy them to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="2315a-114">따라서 개체를 변경할 때마다 해당 개체를 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버로 다시 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-114">Therefore, any time that you make a change to an object, you must redeploy the object to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="2315a-115">데이터 마이닝 아키텍처에 대한 자세한 내용은 [물리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;](physical-architecture-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2315a-115">For more information about data mining architecture, see [Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2315a-116">[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007용 데이터 마이닝 추가 기능과 같은 일부 클라이언트를 사용하면 인스턴스에 대한 연결을 사용하지만 마이닝 구조 및 모델을 세션 기간 동안만 서버에 저장하는 세션 마이닝 모델 및 마이닝 구조를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-116">Some clients, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, also let you create session mining models and mining structures, which use a connection to an instance but store the mining structure and models on the server only for the duration of the session.</span></span> <span data-ttu-id="2315a-117">이러한 모델도 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 저장된 구조 및 모델과 같이 여전히 클라이언트를 통해 관리할 수 있지만 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스와의 연결을 끊은 후에는 개체가 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-117">You can still manage these models through the client, the same as you would structures and models stored in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but the objects are not persisted after you disconnect from the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a><span data-ttu-id="2315a-118">SQL Server Data Tools에서 데이터 마이닝 개체 관리</span><span class="sxs-lookup"><span data-stu-id="2315a-118">Managing Data Mining Objects in SQL Server Data Tools</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="2315a-119">는 데이터 마이닝 개체를 쉽게 만들고, 찾아보고, 편집할 수 있는 여러 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-119">offers features that make it easy to create, browse, and edit data mining objects.</span></span>  
  
 <span data-ttu-id="2315a-120">다음 링크에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 데이터 마이닝 개체를 수정하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-120">The following links provide information on how you can modify data mining objects by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="2315a-121">마이닝 구조에 사용되는 데이터 원본 뷰 편집</span><span class="sxs-lookup"><span data-stu-id="2315a-121">Edit the Data Source View used for a Mining Structure</span></span>](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [<span data-ttu-id="2315a-122">마이닝 구조 속성 변경</span><span class="sxs-lookup"><span data-stu-id="2315a-122">Change the Properties of a Mining Structure</span></span>](change-the-properties-of-a-mining-structure.md)  
  
-   [<span data-ttu-id="2315a-123">마이닝 모델의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="2315a-123">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="2315a-124">모델링 플래그 확인 또는 변경&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="2315a-124">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="2315a-125">알고리즘 매개 변수 확인 또는 변경</span><span class="sxs-lookup"><span data-stu-id="2315a-125">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
 <span data-ttu-id="2315a-126">일반적으로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 도구로 활용하여 새 프로젝트를 개발한 후 기존 프로젝트에 추가한 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]와 같은 도구를 사용하여 배포된 프로젝트와 개체를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-126">Typically you will use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] as a tool for developing new projects and adding to existing projects, and then manage projects and objects that have been deployed by using tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2315a-127">`Immediate` 옵션을 사용하고 온라인 모드로 서버에 연결하여 ssASnoversion 인스턴스에 이미 배포된 개체를 직접 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-127">However, you can directly modify objects that are already deployed to an instance of ssASnoversion by using the `Immediate` option and connecting to the server in Online mode.</span></span> <span data-ttu-id="2315a-128">자세한 내용은 [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2315a-128">For more information, see [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2315a-129">이름 또는 설명과 같은 메타데이터를 변경하는 작업을 비롯하여 마이닝 구조 또는 마이닝 모델을 변경하는 모든 작업을 수행한 후에는 구조나 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-129">All changes to a mining structure or mining model, including changes to metadata such as a name or description, require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="2315a-130">데이터 마이닝 프로젝트 또는 개체를 만드는 데 사용된 솔루션 파일이 없는 경우 Analysis Services 가져오기 마법사를 사용하여 서버에서 기존 프로젝트를 가져와서 개체를 수정한 다음 `Incremental` 옵션을 사용하여 다시 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-130">If you do not have the solution file that was used to create the data mining project or objects, you can import the existing project from the server using the Analysis Services Import wizard, make modifications to the objects, and then redeploy using the `Incremental` option.</span></span> <span data-ttu-id="2315a-131">자세한 내용은 [Analysis Services 가져오기 마법사를 사용하여 데이터 마이닝 프로젝트 가져오기](import-a-data-mining-project-using-the-analysis-services-import-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2315a-131">For more information, see [Import a Data Mining Project using the Analysis Services Import Wizard](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a><span data-ttu-id="2315a-132">SQL Server Management Studio에서 데이터 마이닝 개체 관리</span><span class="sxs-lookup"><span data-stu-id="2315a-132">Managing Data Mining Objects in SQL Server Management Studio</span></span>  
 <span data-ttu-id="2315a-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 마이닝 구조 및 마이닝 모델을 스크립팅, 처리 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can script, process, or delete mining structures and mining models.</span></span> <span data-ttu-id="2315a-134">개체 탐색기를 사용하여 제한된 속성 집합만 볼 수 있지만 **DMX 쿼리** 창을 열고 마이닝 구조를 선택하면 마이닝 모델에 대한 추가 메타데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-134">You can view only a limited set of properties by using Object Explorer; however, you can view additional metadata about mining models by opening a **DMX Query** window and selecting a mining structure.</span></span>  
  
-   [<span data-ttu-id="2315a-135">SQL Server Management Studio에서 DMX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="2315a-135">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a><span data-ttu-id="2315a-136">프로그래밍 방식으로 데이터 마이닝 개체 관리</span><span class="sxs-lookup"><span data-stu-id="2315a-136">Managing Data Mining Objects Programmatically</span></span>  
 <span data-ttu-id="2315a-137">다음과 같은 프로그래밍 언어를 사용하여 데이터 마이닝 개체를 생성, 변경, 처리 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-137">You can create, alter, process, and delete data mining objects by using the following programming languages.</span></span> <span data-ttu-id="2315a-138">각 언어는 서로 다른 태스크를 위해 설계되었으므로 수행할 수 있는 작업의 유형에는 제한이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-138">Each language is designed for different tasks and as a result, there might be restrictions on the type of operations that you can perform.</span></span> <span data-ttu-id="2315a-139">예를 들어 데이터 마이닝 개체의 일부 속성을 변경하는 데는 DMX(Data Mining Extensions)를 사용할 수 없고 XMLA나 AMO를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-139">For example, some properties of data mining objects cannot be changed by using Data Mining Extensions (DMX); you must use XMLA or AMO.</span></span>  
  
### <a name="analysis-management-objects-amo"></a><span data-ttu-id="2315a-140">AMO(Analysis Management Objects)</span><span class="sxs-lookup"><span data-stu-id="2315a-140">Analysis Management Objects (AMO)</span></span>  
 <span data-ttu-id="2315a-141">AMO(Analysis Management Objects)는 XMLA의 최상위에 작성되며 데이터 마이닝 개체를 완전히 제어할 수 있게 하는 개체 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-141">Analysis Management Objects (AMO) is an object model built on top of XMLA that gives you full control over data mining objects.</span></span> <span data-ttu-id="2315a-142">AMO를 사용하여 마이닝 구조와 마이닝 모델을 생성, 배포 및 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-142">By using AMO, you can create, deploy, and monitor mining structures and mining models</span></span>  
  
-   [<span data-ttu-id="2315a-143">AMO 개념 및 개체 모델</span><span class="sxs-lookup"><span data-stu-id="2315a-143">AMO Concepts and Object Model</span></span>](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 <span data-ttu-id="2315a-144">**제한 사항:** 없음</span><span class="sxs-lookup"><span data-stu-id="2315a-144">**Restrictions:** None.</span></span>  
  
### <a name="data-mining-extensions-dmx"></a><span data-ttu-id="2315a-145">DMX(Data Mining Extensions)</span><span class="sxs-lookup"><span data-stu-id="2315a-145">Data Mining Extensions (DMX)</span></span>  
 <span data-ttu-id="2315a-146">DMX(Data Mining Extensions)를 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 또는 ADOMD.Net 등의 다른 명령 인터페이스와 함께 사용하여 마이닝 구조와 마이닝 모델을 생성, 삭제 및 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-146">Data Mining Extensions (DMX) can be used with other command interfaces such as [!INCLUDE[vstecado](../../includes/vstecado-md.md)] or ADOMD.Net to create, delete, and query mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="2315a-147">DMX&#40;Data Mining Extensions&#41; 데이터 정의 문</span><span class="sxs-lookup"><span data-stu-id="2315a-147">Data Mining Extensions &#40;DMX&#41; Data Definition Statements</span></span>](/sql/dmx/dmx-statements-data-definition)  
  
 <span data-ttu-id="2315a-148">**제한 사항:** 일부 속성은 DMX를 사용하여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-148">**Restrictions:** Some properties cannot be changed by using DMX.</span></span>  
  
### <a name="xml-for-analysis-xmla"></a><span data-ttu-id="2315a-149">XMLA(XML for Analysis)</span><span class="sxs-lookup"><span data-stu-id="2315a-149">XML for Analysis (XMLA)</span></span>  
 <span data-ttu-id="2315a-150">XMLA(XML for Analysis)는 모든 Analysis Services에 대한 데이터 정의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-150">XML for Analysis (XMLA) is the data definition language for all of Analysis Services.</span></span> <span data-ttu-id="2315a-151">XMLA를 사용하면 대부분의 데이터 마이닝 개체와 서버 작업을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-151">XMLA gives you control over most data mining objects and server operations.</span></span> <span data-ttu-id="2315a-152">클라이언트와 서버 간의 모든 관리 작업은 XMLA를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-152">All management operations between the client and the server can be performed by using XMLA.</span></span> <span data-ttu-id="2315a-153">편의상 ASSL( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language)을 사용하여 XML을 래핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-153">For convenience, you can use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) to wrap the XML.</span></span>  
  
 <span data-ttu-id="2315a-154">**제한 사항:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 생성하는 일부 XMLA 문은 내부 용도로만 사용할 수 있고 XML DDL 스크립트에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2315a-154">**Restrictions:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates some XMLA statements that are supported for internal use only, and cannot be used in XML DDL scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2315a-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2315a-155">See Also</span></span>  
 [<span data-ttu-id="2315a-156">개발자 가이드 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2315a-156">Developer's Guide &#40;Analysis Services&#41;</span></span>](../analysis-services-developer-documentation.md)  
  
  
