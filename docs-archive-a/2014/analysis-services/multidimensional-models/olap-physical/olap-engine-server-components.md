---
title: OLAP 엔진 서버 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740545"
---
# <a name="olap-engine-server-components"></a><span data-ttu-id="3a864-102">OLAP 엔진 서버 구성 요소</span><span class="sxs-lookup"><span data-stu-id="3a864-102">OLAP Engine Server Components</span></span>
  <span data-ttu-id="3a864-103">의 서버 구성 요소는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Windows 서비스로 실행 되는 **msmdsrv.exe** 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-103">The server component of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is the **msmdsrv.exe** application, which runs as a Windows service.</span></span> <span data-ttu-id="3a864-104">이 애플리케이션은 보안 구성 요소, XMLA(XML for Analysis) 수신기 구성 요소, 쿼리 프로세서 구성 요소 및 다음 기능을 수행하는 다른 많은 내부 구성 요소로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-104">This application consists of security components, an XML for Analysis (XMLA) listener component, a query processor component and numerous other internal components that perform the following functions:</span></span>

-   <span data-ttu-id="3a864-105">클라이언트로부터 수신한 문 구문 분석</span><span class="sxs-lookup"><span data-stu-id="3a864-105">Parsing statements received from clients</span></span>

-   <span data-ttu-id="3a864-106">메타데이터 관리</span><span class="sxs-lookup"><span data-stu-id="3a864-106">Managing metadata</span></span>

-   <span data-ttu-id="3a864-107">트랜잭션 처리</span><span class="sxs-lookup"><span data-stu-id="3a864-107">Handling transactions</span></span>

-   <span data-ttu-id="3a864-108">계산 처리</span><span class="sxs-lookup"><span data-stu-id="3a864-108">Processing calculations</span></span>

-   <span data-ttu-id="3a864-109">차원 및 셀 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="3a864-109">Storing dimension and cell data</span></span>

-   <span data-ttu-id="3a864-110">집계 생성</span><span class="sxs-lookup"><span data-stu-id="3a864-110">Creating aggregations</span></span>

-   <span data-ttu-id="3a864-111">쿼리 일정 예약</span><span class="sxs-lookup"><span data-stu-id="3a864-111">Scheduling queries</span></span>

-   <span data-ttu-id="3a864-112">개체 캐싱</span><span class="sxs-lookup"><span data-stu-id="3a864-112">Caching objects</span></span>

-   <span data-ttu-id="3a864-113">서버 리소스 관리</span><span class="sxs-lookup"><span data-stu-id="3a864-113">Managing server resources</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="3a864-114">아키텍처 다이어그램</span><span class="sxs-lookup"><span data-stu-id="3a864-114">Architectural Diagram</span></span>
 <span data-ttu-id="3a864-115">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스는 독립 실행형 서비스로 실행되며 서비스와의 통신은 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis)를 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-115">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span> <span data-ttu-id="3a864-116">AMO는 사용자 애플리케이션과 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 사이에 있는 계층으로,</span><span class="sxs-lookup"><span data-stu-id="3a864-116">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="3a864-117">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 관리 개체에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-117">This layer provides access to [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="3a864-118">AMO는 클라이언트 애플리케이션에서 명령을 가져와서 이 명령을 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 대한 XMLA 메시지로 변환하는 클래스 라이브러리이며,</span><span class="sxs-lookup"><span data-stu-id="3a864-118">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="3a864-119">명령을 실행하는 메서드 멤버 및 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 개체에 대한 데이터를 포함하는 속성 멤버와 함께 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 개체를 최종 사용자에게 클래스로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-119">AMO presents [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="3a864-120">다음 그림은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 내에서 실행되는 모든 주요 요소와 이 인스턴스와 상호 작용하는 모든 사용자 구성 요소를 비롯한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 구성 요소 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-120">The following illustration shows the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] components architecture, including all major elements running within the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance and all user components that interact with the instance.</span></span> <span data-ttu-id="3a864-121">또한 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis) 수신기를 통해서만 이 인스턴스에 액세스할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-121">The illustration also shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

 <span data-ttu-id="3a864-122">![Analysis Services 시스템 아키텍처 다이어그램](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 시스템 아키텍처 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="3a864-122">![Analysis Services System Architecture Diagram](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="xmla-listener"></a><span data-ttu-id="3a864-123">XMLA 수신기</span><span class="sxs-lookup"><span data-stu-id="3a864-123">XMLA Listener</span></span>
 <span data-ttu-id="3a864-124">XMLA 수신기 구성 요소는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 와 클라이언트 간의 모든 XMLA 통신을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-124">The XMLA listener component handles all XMLA communications between [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] and its clients.</span></span> <span data-ttu-id="3a864-125">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini 파일의 구성 설정을 사용 하 여 인스턴스가 수신 하는 포트를 지정할 수 있습니다 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a864-125">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` configuration setting in the msmdsrv.ini file can be used to specify a port on which an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance listens.</span></span> <span data-ttu-id="3a864-126">이 파일의 값이 0이면 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 기본 포트에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-126">A value of 0 in this file indicates that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] listen on the default port.</span></span> <span data-ttu-id="3a864-127">달리 지정하지 않는 한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서는 다음 기본 TCP 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-127">Unless otherwise specified, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the following default TCP ports:</span></span>

|<span data-ttu-id="3a864-128">포트</span><span class="sxs-lookup"><span data-stu-id="3a864-128">Port</span></span>|<span data-ttu-id="3a864-129">Description</span><span class="sxs-lookup"><span data-stu-id="3a864-129">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="3a864-130">2383</span><span class="sxs-lookup"><span data-stu-id="3a864-130">2383</span></span>|<span data-ttu-id="3a864-131">의 기본 인스턴스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a864-131">Default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="3a864-132">2382</span><span class="sxs-lookup"><span data-stu-id="3a864-132">2382</span></span>|<span data-ttu-id="3a864-133">의 다른 인스턴스에 대 한 리디렉터 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a864-133">Redirector for other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="3a864-134">서버 시작 시 동적으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a864-134">Dynamically assigned at server startup</span></span>|<span data-ttu-id="3a864-135">의 명명 된 인스턴스입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a864-135">Named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|

 <span data-ttu-id="3a864-136">자세한 내용은 [Analysis Services 액세스를 허용 하도록 Windows 방화벽 구성을](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a864-136">See [Configure the Windows Firewall to Allow Analysis Services Access](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for more details.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a864-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a864-137">See Also</span></span>
 <span data-ttu-id="3a864-138">[개체 명명 규칙은 Analysis Services&#41;](object-naming-rules-analysis-services.md) [물리적 아키텍처 &#40;Analysis Services-다차원 데이터&#41;](understanding-microsoft-olap-physical-architecture.md) [논리 아키텍처 &#40;Analysis Services 다차원 데이터](../olap-logical/understanding-microsoft-olap-logical-architecture.md) 를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="3a864-138">[Object Naming Rules &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;](understanding-microsoft-olap-physical-architecture.md) [Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span></span>


