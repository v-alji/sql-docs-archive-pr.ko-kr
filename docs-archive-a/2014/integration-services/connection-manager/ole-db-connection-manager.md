---
title: OLE DB 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5431de956a1039c2978688982792f190b0abc544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652262"
---
# <a name="ole-db-connection-manager"></a><span data-ttu-id="b33a9-102">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="b33a9-102">OLE DB Connection Manager</span></span>
  <span data-ttu-id="b33a9-103">OLE DB 연결 관리자를 사용하면 패키지에서 OLE DB Provider를 사용하여 데이터 원본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-103">An OLE DB connection manager enables a package to connect to a data source by using an OLE DB provider.</span></span> <span data-ttu-id="b33a9-104">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결되는 OLE DB 연결 관리자에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-104">For example, an OLE DB connection manager that connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b33a9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB 공급자는 다중 서브넷 장애 조치(Failover) 클러스터링에 대한 새 연결 문자열 키워드(MultiSubnetFailover=True)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB provider does not support the new connection string key words (MultiSubnetFailover=True) for Multi-Subnet Failover Clustering.</span></span> <span data-ttu-id="b33a9-106">자세한 내용은 www.mattmasson.com의 릴리스 정보 및 블로그 게시물 인 [AlwaysOn 다중 서브넷 장애 조치 (Failover) 및 SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)(영문)를 [SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b33a9-106">For more information, see the [SQL Server Release  Notes](https://go.microsoft.com/fwlink/?LinkId=247824) and the blog post, [AlwaysOn Multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/), on www.mattmasson.com.</span></span>  
  
 <span data-ttu-id="b33a9-107">여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 태스크 및 데이터 흐름 구성 요소는 OLE DB 연결 관리자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-107">Several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and data flow components use an OLE DB connection manager.</span></span> <span data-ttu-id="b33a9-108">예를 들어 OLE DB 원본과 OLE DB 대상에서는 이 연결 관리자를 사용하여 데이터를 추출 및 로드하고, SQL 실행 태스크에서는 이 연결 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하고 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-108">For example, the OLE DB source and OLE DB destination use this connection manager to extract and load data, and the Execute SQL task can use this connection manager to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to run queries.</span></span>  
  
 <span data-ttu-id="b33a9-109">OLE DB 연결 관리자는 또한 C++와 같은 언어를 사용하는 비관리 코드로 작성된 사용자 지정 태스크의 OLE DB 데이터 원본에 액세스하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-109">The OLE DB connection manager is also used to access OLE DB data sources in custom tasks written in unmanaged code that uses a language such as C++.</span></span>  
  
 <span data-ttu-id="b33a9-110">패키지에 OLE DB 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 OLE DB 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-110">When you add an OLE DB connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an OLE DB connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="b33a9-111">연결 관리자의 `ConnectionManagerType` 속성이 `OLEDB`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-111">The `ConnectionManagerType` property of the connection manager is set to `OLEDB`.</span></span>  
  
 <span data-ttu-id="b33a9-112">다음과 같은 방법으로 OLE DB 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-112">The OLE DB connection manager can be configured in the following ways:</span></span>  
  
-   <span data-ttu-id="b33a9-113">선택된 공급자에 대한 요구 사항을 만족하도록 구성된 특정 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-113">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="b33a9-114">공급자에 따라 연결할 데이터 원본의 이름을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-114">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="b33a9-115">선택된 공급자에 적합한 보안 자격 증명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-115">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="b33a9-116">연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-116">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="b33a9-117">로깅</span><span class="sxs-lookup"><span data-stu-id="b33a9-117">Logging</span></span>  
 <span data-ttu-id="b33a9-118">OLE DB 연결 관리자가 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-118">You can log the calls that the OLE DB connection manager makes to external data providers.</span></span> <span data-ttu-id="b33a9-119">이 로깅 기능을 사용하여 OLE DB 연결 관리자가 수행하는 외부 데이터 원본에 대한 연결 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-119">You can use this logging capability to troubleshoot the connections that the OLE DB connection manager makes to external data sources.</span></span> <span data-ttu-id="b33a9-120">OLE DB 연결 관리자가 외부 데이터 공급자에 대해 수행 하는 호출을 로깅하려면 패키지 로깅을 사용 하도록 설정 하 고 패키지 수준에서 **진단** 이벤트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-120">To log the calls that the OLE DB connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="b33a9-121">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b33a9-121">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuration-of-the-oledb-connection-manager"></a><span data-ttu-id="b33a9-122">OLEDB 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="b33a9-122">Configuration of the OLEDB Connection Manager</span></span>  
 <span data-ttu-id="b33a9-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33a9-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="b33a9-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [OLE DB 연결 관리자 구성](../configure-ole-db-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b33a9-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Configure OLE DB Connection Manager](../configure-ole-db-connection-manager.md).</span></span> <span data-ttu-id="b33a9-125">프로그래밍 방식으로 연결 관리자를 구성하는 방법은 개발자 가이드에서 **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** 클래스에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b33a9-125">For information about configuring a connection manager programmatically, see the documentation for **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** class in the Developer Guide.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b33a9-126">관련 내용</span><span class="sxs-lookup"><span data-stu-id="b33a9-126">Related Content</span></span>  
  
-   <span data-ttu-id="b33a9-127">Wiki 문서, social.technet.microsoft.com의 [Oracle 커넥터를 사용 하는 SSIS](https://go.microsoft.com/fwlink/?LinkId=220670) .</span><span class="sxs-lookup"><span data-stu-id="b33a9-127">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) on social.technet.microsoft.com.</span></span>  
  
-   <span data-ttu-id="b33a9-128">carlprothman.net의 기술 문서 [OLE DB 공급자에 대한 연결 문자열](https://go.microsoft.com/fwlink/?LinkId=220744)</span><span class="sxs-lookup"><span data-stu-id="b33a9-128">Technical article, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744), on carlprothman.net.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b33a9-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b33a9-129">See Also</span></span>  
 <span data-ttu-id="b33a9-130">[OLE DB 원본](../data-flow/ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="b33a9-130">[OLE DB Source](../data-flow/ole-db-source.md) </span></span>  
 <span data-ttu-id="b33a9-131">[OLE DB 대상](../data-flow/ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="b33a9-131">[OLE DB Destination](../data-flow/ole-db-destination.md) </span></span>  
 <span data-ttu-id="b33a9-132">[SQL 실행 태스크](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="b33a9-132">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="b33a9-133">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="b33a9-133">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
