---
title: 데이터 마이닝 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728931"
---
# <a name="data-mining-programming"></a><span data-ttu-id="ccd3c-102">데이터 마이닝 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="ccd3c-102">Data Mining Programming</span></span>
  <span data-ttu-id="ccd3c-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 기본 제공 도구 및 뷰어가 사용자의 요구 사항을 충족시키지 못할 경우 사용자 고유의 확장을 코딩하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-103">If you find that the built-in tools and viewers in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="ccd3c-104">이 경우 다음 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-104">In this approach, you have two options:</span></span>  
  
-   <span data-ttu-id="ccd3c-105">**XMLA**</span><span class="sxs-lookup"><span data-stu-id="ccd3c-105">**XMLA**</span></span>  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ccd3c-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]에서는 클라이언트 응용 프로그램과의 통신을 위한 프로토콜로 XMLA (XML for Analysis)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] supports XML for Analysis (XMLA) as a protocol for communication with client applications.</span></span> <span data-ttu-id="ccd3c-107">추가 명령은 XML for Analysis 사양을 확장한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-107">Additional commands are supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that extend the XML for Analysis specification.</span></span>  
  
     <span data-ttu-id="ccd3c-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 데이터 정의, 데이터 조작 및 데이터 제어 지원을 위해 XMLA를 사용하므로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 제공하는 비주얼 도구를 사용하여 마이닝 구조 및 마이닝 모델을 만든 다음 DMX(Data Mining Extensions) 및 ASSL(Analysis Services Scripting Language) 스크립트를 사용하여 만든 데이터 마이닝 개체를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-108">Because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses XMLA for data definition, data manipulation, and data control support, you can create mining structures and mining models by using the visual tools provided by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then extend the data mining objects that you have created by using Data Mining Extensions (DMX) and Analysis Services Scripting Language (ASSL) scripts.</span></span>  
  
     <span data-ttu-id="ccd3c-109">데이터 마이닝 개체를 XMLA 스크립트에서 전적으로 만들고 수정할 수 있으며, 사용자 고유의 애플리케이션에서 모델에 대한 예측 쿼리를 프로그래밍 방식으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-109">You can create and modify data mining objects entirely in XMLA scripts, and run prediction queries against the models programmatically from your own applications.</span></span>  
  
-   <span data-ttu-id="ccd3c-110">**AMO(Analysis Management Objects)**</span><span class="sxs-lookup"><span data-stu-id="ccd3c-110">**Analysis Management Objects (AMO)**</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="ccd3c-111">는 또한 타사 데이터 마이닝 공급자가 데이터 마이닝 개체를 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 통합할 수 있도록 하는 완전한 프레임워크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-111">also provides a complete framework that enables third-party data mining providers to integrate the data mining objects into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="ccd3c-112">AMO를 사용하여 마이닝 구조와 마이닝 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-112">You can create mining structures and mining models by using AMO.</span></span> <span data-ttu-id="ccd3c-113">CodePlex의 다음 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-113">See the following samples in CodePlex:</span></span>  
  
    -   <span data-ttu-id="ccd3c-114">AMO Browser</span><span class="sxs-lookup"><span data-stu-id="ccd3c-114">AMO Browser</span></span>  
  
         <span data-ttu-id="ccd3c-115">지정한 SSAS 인스턴스에 연결하고 마이닝 구조 및 마이닝 모델을 비롯한 모든 서버 개체와 해당 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-115">Connects to the SSAS instance you specify and lists all server objects and their properties, including mining structure and mining models.</span></span>  
  
    -   <span data-ttu-id="ccd3c-116">AMO Simple Sample</span><span class="sxs-lookup"><span data-stu-id="ccd3c-116">AMO Simple Sample</span></span>  
  
         <span data-ttu-id="ccd3c-117">AS Simple Sample은 대부분의 주요 개체에 대한 프로그래밍 방식 액세스를 다루며 메타데이터 찾아보기 및 개체 값에 대한 액세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-117">The AS Simple Sample covers programmatic access to most major objects, and demonstrates metadata browsing, and access to the values in objects.</span></span>  
  
         <span data-ttu-id="ccd3c-118">또한 데이터 마이닝 구조 및 모델을 만들고 처리하는 방법과 기존 데이터 마이닝 모델을 찾아보는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-118">The sample also demonstrates how to create and process a data mining structure and model, as well as browse an existing data mining model.</span></span>  
  
-   <span data-ttu-id="ccd3c-119">**DMX**</span><span class="sxs-lookup"><span data-stu-id="ccd3c-119">**DMX**</span></span>  
  
     <span data-ttu-id="ccd3c-120">DMX를 사용하여 명령 문, 예측 쿼리 및 메타데이터 쿼리를 캡슐화할 수 있으며, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버에 대한 연결을 만들었다고 가정하고 표 형식으로 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-120">You can use DMX to encapsulate command statements, prediction queries, and metadata queries and return results in a tabular format, assuming you have created a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ccd3c-121">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ccd3c-121">In This Section</span></span>  
 [<span data-ttu-id="ccd3c-122">데이터 마이닝용 OLE DB</span><span class="sxs-lookup"><span data-stu-id="ccd3c-122">OLE DB for Data Mining</span></span>](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 <span data-ttu-id="ccd3c-123">데이터 마이닝 및 다차원 데이터를 지원할 수 있도록 새로운 스키마 행 집합 및 열, 마이닝 구조를 만들고 관리하는 데 사용할 수 있는 DMX(Data Mining Extensions) 언어 등 사양에 새로 추가된 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-123">Describes additions to the specification to support data mining and multidimensional data: new schema rowsets and columns, Data Mining Extensions (DMX) language for creating and managing mining structures.</span></span>  
  
## <a name="related-reference"></a><span data-ttu-id="ccd3c-124">관련 참조</span><span class="sxs-lookup"><span data-stu-id="ccd3c-124">Related Reference</span></span>  
 [<span data-ttu-id="ccd3c-125">ADOMD.NET를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="ccd3c-125">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 <span data-ttu-id="ccd3c-126">ADOMD.NET 클라이언트 및 서버 프로그래밍 개체를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-126">Introduces ADOMD.NET client and server programming objects.</span></span>  
  
 [<span data-ttu-id="ccd3c-127">AMO&#40;Analysis Management Objects&#41;를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="ccd3c-127">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 <span data-ttu-id="ccd3c-128">AMO 프로그래밍 라이브러리를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-128">Introduces the AMO programming library.</span></span>  
  
 [<span data-ttu-id="ccd3c-129">ASSL&#40;Analysis Services Scripting Language&#41;을 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="ccd3c-129">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 <span data-ttu-id="ccd3c-130">XMLA(XML for Analysis) 및 해당 확장을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd3c-130">Introduces XML for Analysis (XMLA) and its extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd3c-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccd3c-131">See Also</span></span>  
 <span data-ttu-id="ccd3c-132">[개발자 가이드 &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="ccd3c-132">[Developer's Guide &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span></span>  
 [<span data-ttu-id="ccd3c-133">DMX&#40;Data Mining Extensions&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="ccd3c-133">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
