---
title: SQL Server Management Studio에서 서버 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb2a6b9afba7d838cf71144f88ed7866c54ad796
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737521"
---
# <a name="administer-servers-with-sql-server-management-studio"></a><span data-ttu-id="578d0-102">SQL Server Management Studio에서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="578d0-102">Administer Servers with SQL Server Management Studio</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="578d0-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리자의 서버 관리 요구 사항을 충족 하도록 설계 된 풍부한 통합 관리 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is a rich, integrated administrative client designed to meet the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] administrator's server management requirements.</span></span> <span data-ttu-id="578d0-104">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에서는 개체 탐색기를 사용하여 관리 태스크를 수행합니다. 개체 탐색기에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 계열의 서버에 연결하여 서버에 포함된 내용을 도식적으로 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-104">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], administrative tasks are accomplished using Object Explorer, which allows you to connect to any server in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] family and graphically browse its contents.</span></span> <span data-ttu-id="578d0-105">서버는 [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 또는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 인스턴스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-105">A server can be an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="578d0-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 의 도구 구성 요소에는 등록된 서버, 개체 탐색기, 솔루션 탐색기, 템플릿 탐색기, 개체 탐색기 정보 페이지 및 문서 창이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-106">The tool components of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] include Registered Servers, Object Explorer, Solution Explorer, Template Explorer, the Object Explorer Details page, and the document window.</span></span> <span data-ttu-id="578d0-107">도구를 표시하려면 **보기** 메뉴에서 도구 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-107">To display a tool, on the **View** menu, click the tool name.</span></span> <span data-ttu-id="578d0-108">쿼리 편집기 도구를 표시하려면 도구 모음에서 **새 쿼리** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-108">To display the Query Editor tool, click the **New Query** button on the toolbar.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="578d0-109">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 와 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 간의 네트워크 트래픽은 기본적으로 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-109">Network traffic between [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is unencrypted by default.</span></span> <span data-ttu-id="578d0-110">암호화된 연결이 설정되지 않은 경우 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 에서 중요한 데이터(암호 포함)를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="578d0-110">Do not work with sensitive data (including passwords) in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] unless you have established an encrypted connection.</span></span> <span data-ttu-id="578d0-111">자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="578d0-111">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
 <span data-ttu-id="578d0-112">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-112">Use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="578d0-113">서버 등록</span><span class="sxs-lookup"><span data-stu-id="578d0-113">Register servers.</span></span>  
  
-   <span data-ttu-id="578d0-114">[!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs.md)] 또는 [!INCLUDE[ssIS](../includes/ssis-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-114">Connect to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs.md)], or [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
-   <span data-ttu-id="578d0-115">서버 속성 구성</span><span class="sxs-lookup"><span data-stu-id="578d0-115">Configure server properties.</span></span>  
  
-   <span data-ttu-id="578d0-116">큐브, 차원, 어셈블리 등의 [!INCLUDE[ssAS](../includes/ssas-md.md)] 개체 및 데이터베이스 관리</span><span class="sxs-lookup"><span data-stu-id="578d0-116">Manage database and [!INCLUDE[ssAS](../includes/ssas-md.md)] objects such as cubes, dimensions, and assemblies.</span></span>  
  
-   <span data-ttu-id="578d0-117">데이터베이스, 테이블, 큐브, 데이터베이스 사용자, 로그인 등의 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="578d0-117">Create objects, such as databases, tables, cubes, database users, and logins.</span></span>  
  
-   <span data-ttu-id="578d0-118">파일 및 파일 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="578d0-118">Manage files and filegroups.</span></span>  
  
-   <span data-ttu-id="578d0-119">데이터베이스 연결 또는 분리</span><span class="sxs-lookup"><span data-stu-id="578d0-119">Attach or detach databases.</span></span>  
  
-   <span data-ttu-id="578d0-120">스크립팅 도구 실행</span><span class="sxs-lookup"><span data-stu-id="578d0-120">Launch scripting tools.</span></span>  
  
-   <span data-ttu-id="578d0-121">보안 관리</span><span class="sxs-lookup"><span data-stu-id="578d0-121">Manage security.</span></span>  
  
-   <span data-ttu-id="578d0-122">시스템 로그 보기</span><span class="sxs-lookup"><span data-stu-id="578d0-122">View system logs.</span></span>  
  
-   <span data-ttu-id="578d0-123">현재 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="578d0-123">Monitor current activity.</span></span>  
  
-   <span data-ttu-id="578d0-124">복제 구성</span><span class="sxs-lookup"><span data-stu-id="578d0-124">Configure replication.</span></span>  
  
-   <span data-ttu-id="578d0-125">전체 텍스트 인덱스 관리</span><span class="sxs-lookup"><span data-stu-id="578d0-125">Manage full-text indexes.</span></span>  
  
 <span data-ttu-id="578d0-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 시작 및 중지하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="578d0-126">To start and stop [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="578d0-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="578d0-127">See Also</span></span>  
 <span data-ttu-id="578d0-128">[SQL Server Management Studio 사용](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="578d0-128">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="578d0-129">서버 속성 보기 또는 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="578d0-129">View or Change Server Properties &#40;SQL Server&#41;</span></span>](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
