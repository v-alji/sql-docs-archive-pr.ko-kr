---
title: 물리적 아키텍처 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- server architecture [Analysis Services]
- architecture [Analysis Services]
ms.assetid: 25eeecf0-6e85-4527-b94d-5503d27edaed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 787ca28c08dc41a6b9561251077716a406358c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734632"
---
# <a name="physical-architecture-analysis-services---data-mining"></a><span data-ttu-id="f80bc-102">물리적 아키텍처(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="f80bc-102">Physical Architecture (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f80bc-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]는 서버 및 클라이언트 구성 요소를 모두 사용 하 여 비즈니스 인텔리전스 응용 프로그램에 대 한 데이터 마이닝 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses both server and client components to supply data mining functionality for business intelligence applications:</span></span>

-   <span data-ttu-id="f80bc-104">서버 구성 요소는 Microsoft Windows 서비스로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-104">The server component is implemented as a Microsoft Windows service.</span></span> <span data-ttu-id="f80bc-105">동일한 컴퓨터에서 각각 별개의 Windows 서비스 인스턴스로 구현된 여러 개의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-105">You can have multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>

-   <span data-ttu-id="f80bc-106">클라이언트는 웹 서비스로 노출되어 명령을 실행하고 응답을 수신하는 SOAP 기반 프로토콜인 공용 표준 XMLA(XML for Analysis)를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-106">Clients communicate with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="f80bc-107">또한 XMLA를 통해 클라이언트 개체 모델이 제공되며 이는 ADOMD.NET과 같은 관리 공급자나 네이티브 OLE DB 공급자 중 하나를 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>

-   <span data-ttu-id="f80bc-108">쿼리 명령은 데이터 마이닝 지향 업계 표준 쿼리 언어인 DMX(Data Mining Extensions)를 사용하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-108">Query commands can be issued using Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="f80bc-109">또한 ASSL(Analysis Services Scripting Language)을 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 개체를 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database objects.</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="f80bc-110">아키텍처 다이어그램</span><span class="sxs-lookup"><span data-stu-id="f80bc-110">Architectural Diagram</span></span>
 <span data-ttu-id="f80bc-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 독립 실행형 서비스로 실행되며 서비스와의 통신은 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis)를 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-111">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span>

 <span data-ttu-id="f80bc-112">AMO는 사용자 애플리케이션과 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리 개체에 대한 액세스를 제공하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 사이의 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-112">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that provides access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="f80bc-113">AMO는 클라이언트 애플리케이션에서 명령을 가져와서 이 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 XMLA 메시지로 변환하는 클래스 라이브러리이며,</span><span class="sxs-lookup"><span data-stu-id="f80bc-113">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f80bc-114">명령을 실행하는 메서드 멤버 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에 대한 데이터를 포함하는 속성 멤버와 함께 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 개체를 최종 사용자에게 클래스로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-114">AMO presents [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="f80bc-115">다음 그림은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 내의 서비스 및 이 인스턴스와 상호 작용하는 사용자 구성 요소를 비롯한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 구성 요소 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-115">The following illustration shows the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components architecture, including services within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and user components that interact with the instance.</span></span>

 <span data-ttu-id="f80bc-116">또한 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis) 수신기를 통해서만 이 인스턴스에 액세스할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-116">The illustration shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

> [!WARNING]
>  <span data-ttu-id="f80bc-117">DSO는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-117">DSO has been deprecated.</span></span> <span data-ttu-id="f80bc-118">솔루션을 개발할 때 DSO를 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-118">You should not use DSO to develop solutions.</span></span>

 <span data-ttu-id="f80bc-119">![Analysis Services 시스템 아키텍처 다이어그램](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 시스템 아키텍처 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="f80bc-119">![Analysis Services System Architecture Diagram](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="server-configuration"></a><span data-ttu-id="f80bc-120">서버 구성</span><span class="sxs-lookup"><span data-stu-id="f80bc-120">Server Configuration</span></span>
 <span data-ttu-id="f80bc-121">하나의 서버 인스턴스는 각각 클라이언트 요청에 응답하고 개체를 처리하는 고유의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서비스 인스턴스가 있는 여러 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-121">One server instance can support multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, each with its own instance of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that responds to client requests and processes objects.</span></span>

 <span data-ttu-id="f80bc-122">테이블 형식 모델과 데이터 마이닝 및/또는 다차원 모델을 사용하려면 별도의 인스턴스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-122">Separate instances must be installed if you want to work with both tabular models and data mining and/or multidimensional models.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="f80bc-123">에서는 테이블 형식 모드(xVelocity 메모리 내 분석 엔진(VertiPaq) 스토리지 엔진 사용)로 실행되는 인스턴스와 기존 OLAP, MOLAP 또는 ROLAP 구성 중 하나로 실행되는 인스턴스의 단계별 설치를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-123">supports side-by-side installation of instances running in tabular mode (which uses the xVelocity in-memory analytics engine (VertiPaq) storage engine) and instances running in one of the conventional OLAP, MOLAP, or ROLAP configurations.</span></span> <span data-ttu-id="f80bc-124">자세한 내용은 [Analysis Services 인스턴스의 서버 모드 확인](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f80bc-124">For more information, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>

 <span data-ttu-id="f80bc-125">클라이언트와 Analysis Services 서버 간의 모든 통신은 플랫폼 독립적, 언어 독립적인 프로토콜인 XMLA를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-125">All communications between a client and the Analysis Services server use XMLA, which is a platform-independent and language-independent protocol.</span></span> <span data-ttu-id="f80bc-126">클라이언트의 요청이 수신되면 Analysis Services는 이 요청이 OLAP과 관련된 것인지 또는 데이터 마이닝과 관련된 것인지 판단하고 이 판단에 따라 요청을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="f80bc-126">When a request is received from a client, Analysis Services determines whether the request relates to OLAP or data mining, and routes the request appropriately.</span></span> <span data-ttu-id="f80bc-127">자세한 내용은 [OLAP 엔진 서버 구성 요소](../multidimensional-models/olap-physical/olap-engine-server-components.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f80bc-127">For more information, see [OLAP Engine Server Components](../multidimensional-models/olap-physical/olap-engine-server-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f80bc-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f80bc-128">See Also</span></span>
 [<span data-ttu-id="f80bc-129">논리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f80bc-129">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)


