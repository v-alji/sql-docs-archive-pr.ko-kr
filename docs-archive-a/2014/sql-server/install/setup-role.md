---
title: 설치 역할 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
ms.openlocfilehash: add000eed671303c78ab0500303f826bafe4ab77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650448"
---
# <a name="setup-role"></a><span data-ttu-id="2a0a8-102">설치 역할</span><span class="sxs-lookup"><span data-stu-id="2a0a8-102">Setup Role</span></span>
  <span data-ttu-id="2a0a8-103">이 페이지를 통해 기능 선택 페이지를 사용하여 개별 기능을 선택할지 설치 역할을 사용하여 설치할지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-103">Use this page to specify whether to use the Feature Selection page to select individual features, or to install using a setup role.</span></span>  
  
 <span data-ttu-id="2a0a8-104">`setup role`은 미리 정의된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성을 구현하는 데 필요한 모든 기능 및 공유 구성 요소의 고정된 선택 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-104">A `setup role` is a fixed selection of all the features and shared components that are required to implement a predefined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a0a8-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2a0a8-105">Options</span></span>  
 <span data-ttu-id="2a0a8-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]기능 설치**</span><span class="sxs-lookup"><span data-stu-id="2a0a8-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**</span></span>  
 <span data-ttu-id="2a0a8-107">이 옵션을 선택하여 개별 기능과 공유 구성 요소를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-107">Choose this option to select individual features and shared components.</span></span> <span data-ttu-id="2a0a8-108">인스턴스 기능에는 데이터베이스 엔진 서비스, Analysis Services(기본 모드) 및 Reporting Services가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-108">Instance features include Database Engine Services, Analysis Services (native mode), and Reporting Services.</span></span>  
  
 <span data-ttu-id="2a0a8-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SharePoint용 PowerPivot**</span><span class="sxs-lookup"><span data-stu-id="2a0a8-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for SharePoint**</span></span>  
 <span data-ttu-id="2a0a8-110">이 옵션을 선택하여 SharePoint 2010 팜에 Analysis Services 서버 구성 요소를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-110">Choose this option to install Analysis Services server components in a SharePoint 2010 farm.</span></span> <span data-ttu-id="2a0a8-111">이 옵션은 팜에 PowerPivot 시스템 서비스와 Analysis Services 서버를 배포하여, 포함된 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터가 들어 있는 게시된 Excel 통합 문서에 대해 쿼리 및 데이터 처리가 가능하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-111">This option deploys the PowerPivot System Service and the Analysis Services server in a farm, enabling query and data processing for published Excel workbooks that contain embedded [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span>  
  
 <span data-ttu-id="2a0a8-112">SharePoint 팜에서 데이터베이스를 호스팅해야 하는 경우 필요에 따라 설치에 관계형 데이터베이스 엔진 인스턴스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-112">Optionally, you can add a relational database engine instance to your installation if you require it to host databases in a SharePoint farm.</span></span> <span data-ttu-id="2a0a8-113">팜이 이미 구성되어 있는 경우 이 옵션을 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-113">If the farm is already configured, you can skip this option.</span></span>  
  
 <span data-ttu-id="2a0a8-114">설치가 완료 되 면 PowerPivot 구성 도구, PowerShell cmdlet 또는 SharePoint 2010 중앙 관리 방법 중 하나를 사용 하 여 소프트웨어를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-114">After Setup is finished, you must configure the software using one of the following approaches: PowerPivot Configuration tool, PowerShell cmdlets, or SharePoint 2010 Central Administration.</span></span> <span data-ttu-id="2a0a8-115">이전 릴리스와 달리 설치 프로그램에서는 더 이상 PowerPivot 설치에 대한 구성 작업을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-115">In contrast with previous releases, Setup no longer performs any configuration tasks for a PowerPivot installation.</span></span>  
  
 <span data-ttu-id="2a0a8-116">역할 기반 설치에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel 클라이언트 애플리케이션이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-116">A role-based installation does not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel client application.</span></span> <span data-ttu-id="2a0a8-117">클라이언트 애플리케이션은 별도로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-117">The client application is installed separately.</span></span>  
  
 <span data-ttu-id="2a0a8-118">**모든 기능을 기본값으로 설치**</span><span class="sxs-lookup"><span data-stu-id="2a0a8-118">**All Features With Defaults**</span></span>  
 <span data-ttu-id="2a0a8-119">이 설치 역할을 선택하여 이번 릴리스에 사용할 수 있는 모든 기능을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-119">Choose this setup role to install all features that are available for this release.</span></span> <span data-ttu-id="2a0a8-120">SharePoint용 PowerPivot은 이 역할에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-120">Note that PowerPivot for SharePoint is excluded from this role.</span></span> <span data-ttu-id="2a0a8-121">이 기능을 설치하려면 SharePoint용 PowerPivot 설치 역할을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-121">You must use the PowerPivot for SharePoint setup role to install that feature.</span></span>  
  
 <span data-ttu-id="2a0a8-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 **NT AUTHORITY\NETWORK SERVICE** 계정을 사용하여 시작되도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-122">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to start using the **NT AUTHORITY\NETWORK SERVICE** account.</span></span> <span data-ttu-id="2a0a8-123">현재 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** 역할의 멤버로 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-123">The current user will be provisioned as a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** role.</span></span> <span data-ttu-id="2a0a8-124">이 옵션으로 설정한 값은 추가 명령줄 매개 변수를 지정하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-124">Values set by this option can be overridden by specifying additional command line parameters.</span></span>  
  
 <span data-ttu-id="2a0a8-125">운영 체제가 도메인 컨트롤러가 아닌 경우, 기본적으로 데이터베이스 엔진 및 Reporting Services는 NTAUTHORITY\NETWORK SERVICE 계정을 사용하고 Integration Services는 NTAUTHORITY\NETWORK SERVICE 계정을 사용하고 SQL 전체 텍스트 필터 데몬 시작 관리자는 NTAUTHORITY\LOCAL SERVICE 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a0a8-125">When the operating system is not a domain controller, by default the Database Engine and Reporting Services will use the NTAUTHORITY\NETWORK SERVICE account, Integration Services will use the NTAUTHORITY\NETWORK SERVICE account, and the SQL Full text Filter Daemon Launcher will use the NTAUTHORITY\LOCAL SERVICE account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0a8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a0a8-126">See Also</span></span>  
 <span data-ttu-id="2a0a8-127">[SharePoint용 PowerPivot 설치](https://go.microsoft.com/fwlink/?LinkId=206906) </span><span class="sxs-lookup"><span data-stu-id="2a0a8-127">[Installing PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span></span>  
 <span data-ttu-id="2a0a8-128">[하드웨어 및 소프트웨어 요구 사항 (SharePoint용 PowerPivot](https://go.microsoft.com/fwlink/?LinkId=216823) </span><span class="sxs-lookup"><span data-stu-id="2a0a8-128">[Hardware and Software Requirements (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span></span>  
 [<span data-ttu-id="2a0a8-129">기능 선택</span><span class="sxs-lookup"><span data-stu-id="2a0a8-129">Feature Selection</span></span>](../../../2014/sql-server/install/feature-selection.md)  
  
  
