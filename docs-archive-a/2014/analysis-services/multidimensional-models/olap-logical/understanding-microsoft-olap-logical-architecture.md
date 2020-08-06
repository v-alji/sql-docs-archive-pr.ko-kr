---
title: 논리적 아키텍처 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
ms.openlocfilehash: d93361fb14bc6544ffa7376439c2da0c8e06c3fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653596"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a><span data-ttu-id="da3b7-102">논리적 아키텍처(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="da3b7-102">Logical Architecture (Analysis Services - Multidimensional Data)</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="da3b7-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서는 서버 및 클라이언트 구성 요소를 모두 사용 하 여 비즈니스 인텔리전스 응용 프로그램에 대 한 OLAP (온라인 분석 처리) 및 데이터 마이닝 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses both server and client components to supply online analytical processing (OLAP) and data mining functionality for business intelligence applications:</span></span>  
  
-   <span data-ttu-id="da3b7-104">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 의 서버 구성 요소는 Microsoft Windows 서비스로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-104">The server component of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is implemented as a Microsoft Windows service.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="da3b7-105">는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 동일한 컴퓨터에서 여러 인스턴스를 지원 하며 각 인스턴스는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 별도의 Windows 서비스 인스턴스로 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-105">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>  
  
-   <span data-ttu-id="da3b7-106">클라이언트는 웹 서비스로 노출되어 명령을 실행하고 응답을 수신하는 SOAP 기반 프로토콜인 공용 표준 XMLA(XML for Analysis)를 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-106">Clients communicate with [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="da3b7-107">또한 XMLA를 통해 클라이언트 개체 모델이 제공되며 이는 ADOMD.NET과 같은 관리 공급자나 네이티브 OLE DB 공급자 중 하나를 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>  
  
-   <span data-ttu-id="da3b7-108">쿼리 명령은 SQL, 분석용 업계 표준 쿼리 언어인 MDX(Multidimensional Expressions) 또는 데이터 마이닝 지향 업계 표준 쿼리 언어인 DMX(Data Mining Extensions)를 사용하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-108">Query commands can be issued using the following languages: SQL; Multidimensional Expressions (MDX), an industry standard query language for analysis; or Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="da3b7-109">또한 ASSL(Analysis Services Scripting Language)을 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터베이스 개체를 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database objects.</span></span>  
  
 <span data-ttu-id="da3b7-110">또한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서는 서로 연결되지 않은 여러 클라이언트의 애플리케이션이 로컬에 저장된 다차원 데이터를 검색할 수 있도록 하는 로컬 큐브 엔진을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="da3b7-110">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] also supports a local cube engine that enables applications on disconnected clients to browse locally stored multidimensional data.</span></span> <span data-ttu-id="da3b7-111">자세한 내용은 [Analysis Services 개발을 위한 클라이언트 아키텍처 요구 사항](../olap-physical/client-architecture-requirements-for-analysis-services-development.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da3b7-111">For more information, see [Client Architecture Requirements for Analysis Services Development](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da3b7-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="da3b7-112">In This Section</span></span>  
 <span data-ttu-id="da3b7-113">**논리적 아키텍처 개요**</span><span class="sxs-lookup"><span data-stu-id="da3b7-113">**Logical Architecture Overview**</span></span>  
 [<span data-ttu-id="da3b7-114">논리적 아키텍처 개요 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-114">Logical Architecture Overview &#40;Analysis Services - Multidimensional Data&#41;</span></span>](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="da3b7-115">**서버 개체**</span><span class="sxs-lookup"><span data-stu-id="da3b7-115">**Server Objects**</span></span>  
 [<span data-ttu-id="da3b7-116">서버 개체 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-116">Server Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](server-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="da3b7-117">**데이터베이스 개체**</span><span class="sxs-lookup"><span data-stu-id="da3b7-117">**Database Objects**</span></span>  
 [<span data-ttu-id="da3b7-118">데이터베이스 개체&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-118">Database Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](database-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="da3b7-119">**차원 개체**</span><span class="sxs-lookup"><span data-stu-id="da3b7-119">**Dimension Objects**</span></span>  
 [<span data-ttu-id="da3b7-120">차원 개체 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-120">Dimension Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="da3b7-121">**큐브 개체**</span><span class="sxs-lookup"><span data-stu-id="da3b7-121">**Cube Objects**</span></span>  
 [<span data-ttu-id="da3b7-122">큐브 개체는 Analysis Services 다차원 데이터를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-122">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="da3b7-123">**사용자 액세스 보안**</span><span class="sxs-lookup"><span data-stu-id="da3b7-123">**User Access Security**</span></span>  
 [<span data-ttu-id="da3b7-124">사용자 액세스 보안 아키텍처</span><span class="sxs-lookup"><span data-stu-id="da3b7-124">User Access Security Architecture</span></span>](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a><span data-ttu-id="da3b7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da3b7-125">See Also</span></span>  
 <span data-ttu-id="da3b7-126">[Microsoft OLAP 아키텍처 이해](../olap-physical/understanding-microsoft-olap-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="da3b7-126">[Understanding Microsoft OLAP Architecture](../olap-physical/understanding-microsoft-olap-architecture.md) </span></span>  
 [<span data-ttu-id="da3b7-127">물리적 아키텍처&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="da3b7-127">Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
