---
title: 호환성 수준 (SSAS 테이블 형식 SP1) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2853cd5509b66dbfaadd78c578b9676399e81977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741332"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a><span data-ttu-id="df18c-102">호환성 수준(SSAS 테이블 형식 SP1)</span><span class="sxs-lookup"><span data-stu-id="df18c-102">Compatibility Level (SSAS Tabular SP1)</span></span>
  <span data-ttu-id="df18c-103">새 테이블 형식 모델 프로젝트를 만들 때, 기존 테이블 형식 모델 프로젝트를 업그레이드할 때, 기존에 배포 된 테이블 형식 모델 데이터베이스를 업그레이드할 때 또는 PowerPivot 통합 문서를 가져올 때 *호환성 수준을* 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-103">You can specify *Compatibility Level* when creating new Tabular model projects, when upgrading existing Tabular model projects, when upgrading existing deployed Tabular model databases, or when importing PowerPivot workbooks.</span></span>  
  
## <a name="compatibility-level"></a><span data-ttu-id="df18c-104">호환성 수준</span><span class="sxs-lookup"><span data-stu-id="df18c-104">Compatibility Level</span></span>  
 <span data-ttu-id="df18c-105">일반적으로 새 버전과 서비스 팩은 프로덕션 컴퓨터에 설치하기 전에 개발 및 테스트 컴퓨터에 먼저 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-105">It is common to install new versions and service packs on development and test computers prior to installing on production computers.</span></span> <span data-ttu-id="df18c-106">이 경우 두 새 테이블 형식 모델 프로젝트에 대한 호환성 수준과 프로덕션 환경에 이미 배포된 기존 프로젝트에 대한 호환성 수준을 설정하는 방법을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-106">In such cases, it is important to understand setting compatibility level for both new Tabular model projects as well as those that have already been deployed into a production environment.</span></span>  
  
 <span data-ttu-id="df18c-107">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services 인스턴스는 다음 호환성 수준(데이터베이스 버전)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-107">A [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services instance supports the following compatibility levels (database version):</span></span>  
  
-   <span data-ttu-id="df18c-108">SQL Server 2012 (1100)</span><span class="sxs-lookup"><span data-stu-id="df18c-108">SQL Server 2012 (1100)</span></span>  
  
-   <span data-ttu-id="df18c-109">SQL Server 2012 SP1(1103)</span><span class="sxs-lookup"><span data-stu-id="df18c-109">SQL Server 2012 SP1 (1103)</span></span>  
  
-   <span data-ttu-id="df18c-110">SQL Server 2014 (1103)</span><span class="sxs-lookup"><span data-stu-id="df18c-110">SQL Server 2014 (1103)</span></span>  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a><span data-ttu-id="df18c-111">새 테이블 형식 모델 프로젝트를 만들 때 호환성 수준 설정</span><span class="sxs-lookup"><span data-stu-id="df18c-111">Set compatibility level when creating a new Tabular model project</span></span>  
 <span data-ttu-id="df18c-112">SQL Server Data Tools (SSDT)에서 새 테이블 형식 모델 프로젝트를 만들 때 **새 테이블 형식 프로젝트 옵션** 대화 상자에서 호환성 수준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-112">When creating a new Tabular model project in SQL Server Data Tools (SSDT), on the **New Tabular project options** dialog you can specify the compatibility level.</span></span> <span data-ttu-id="df18c-113">새 프로젝트를 만들 때 해당 프로젝트를 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 이상의 Analysis Services 인스턴스에 배포할지 또는 SQL Server 2012 Analysis Services 인스턴스(서비스 팩 1 없음)에 배포할지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-113">You can choose between creating a new project to be deployed to an [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later Analysis Services instance or to an SQL Server 2012 Analysis Services instance (without Service Pack 1).</span></span>  
  
 <span data-ttu-id="df18c-114">또한 **이 메시지를 다시 표시 안 함** 옵션을 선택하여 기본 호환성 수준을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-114">You can also specify a default compatibility level by selecting the **Do not show this message again** option.</span></span> <span data-ttu-id="df18c-115">모든 후속 프로젝트는 지정된 호환성 수준을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-115">All subsequent projects will use the compatibility level you specified.</span></span> <span data-ttu-id="df18c-116">SSDT의 옵션에서 기본 호환성 수준을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-116">You can change the default compatibility level in SSDT in Options.</span></span>  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a><span data-ttu-id="df18c-117">기존 테이블 형식 모델 프로젝트를 1103 호환성 수준으로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="df18c-117">Upgrade an existing Tabular model project to 1103 compatibility level</span></span>  
 <span data-ttu-id="df18c-118">이상 버전을 설치 하기 전에 SSDT에서 만든 테이블 형식 모델 프로젝트를 업그레이드 하려면 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 모델 **속성** 창의 **호환성 수준** 속성을 사용 하 여 데이터베이스 버전 1103을 호환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-118">You can upgrade a Tabular model project created in SSDT prior to installing [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later to be database version 1103 compatible by using the **Compatibility Level** property in the model **Properties** window.</span></span> <span data-ttu-id="df18c-119">테이블 형식 모델 프로젝트를 업그레이드하려면 SSDT가 설치된 컴퓨터에 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 이상을 설치해야 하며 작업 영역 데이터베이스가 상주하는 Analysis Services 인스턴스에도 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 이상을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-119">In order to upgrade a Tabular model project, the computer on which SSDT is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed and the Analysis Services instance on which the workspace database resides must also have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="df18c-120">이전 버전으로 다운그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-120">You cannot downgrade to an earlier version.</span></span>  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a><span data-ttu-id="df18c-121">배포된 테이블 형식 모델 데이터베이스를 1103 호환성 수준으로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="df18c-121">Upgrade a deployed Tabular model database to 1103 compatibility level</span></span>  
 <span data-ttu-id="df18c-122">**데이터베이스 속성**의 **호환성 수준** 속성을 사용 하 여 배포 된 기존 테이블 형식 모델 데이터베이스를 SSMS (SQL Server Management Studio)와 호환 되는 데이터베이스 버전 1103로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-122">You can upgrade an existing deployed Tabular model database to database version 1103 compatible in SQL Server Management Studio (SSMS) by using the **Compatibility Level** property in **Database Properties**.</span></span> <span data-ttu-id="df18c-123">업그레이드하려면 SQL Server Analysis Services 인스턴스가 설치된 컴퓨터에 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 이상을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-123">In order to upgrade, the computer on which the SQL Server Analysis Services instance is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="df18c-124">배포된 테이블 형식 모델 데이터베이스를 이전 버전으로 다운그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-124">You cannot downgrade a deployed Tabular model database to an earlier version.</span></span>  
  
### <a name="import-from-powerpivot"></a><span data-ttu-id="df18c-125">PowerPivot에서 가져오기</span><span class="sxs-lookup"><span data-stu-id="df18c-125">Import from PowerPivot</span></span>  
 <span data-ttu-id="df18c-126">PowerPivot에서 가져오는 방식으로 새 테이블 형식 모델 프로젝트를 만들 때는 호환성 수준을 기본 호환성 수준(이전에 SSDT에서 구성한 경우)으로 업그레이드할지 아니면 PowerPivot 통합 문서에 이미 지정된 호환성 수준을 그대로 사용할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-126">When creating a new Tabular model project by importing from PowerPivot, you can specify if you want to upgrade the compatibility level to the default compatibility level (if previously configured in SSDT) or leave the compatibility level to that already specified in the PowerPivot workbook.</span></span>  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a><span data-ttu-id="df18c-127">SSMS에서 테이블 형식 모델 데이터베이스에 대한 호환성 수준 확인</span><span class="sxs-lookup"><span data-stu-id="df18c-127">Check compatibility level for a Tabular model database in SSMS</span></span>  
 <span data-ttu-id="df18c-128">데이터베이스 속성의 **호환성 수준** 속성 (의 새로운 기능)을 확인 하 여 SSMS의 테이블 형식 모델 데이터베이스에 대 한 호환성 수준을 확인할 수 있습니다 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] . **Database Properties**</span><span class="sxs-lookup"><span data-stu-id="df18c-128">You can check the compatibility level for a Tabular model database in SSMS by viewing the **Compatibility Level** property (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Database Properties**.</span></span>  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a><span data-ttu-id="df18c-129">SSMS에서 Analysis Services 인스턴스에 대해 지원되는 호환성 수준 확인</span><span class="sxs-lookup"><span data-stu-id="df18c-129">Check supported compatibility level for an Analysis Services instance in SSMS</span></span>  
 <span data-ttu-id="df18c-130">Analysis Services 속성의 **정보** 페이지 (의 새로 만들기)에서 **지원 되는 호환성 수준** 속성을 보면 SSMS에서 지원 되는 호환성 수준을 확인할 수 있습니다 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] **Analysis Services Properties**.</span><span class="sxs-lookup"><span data-stu-id="df18c-130">You can check the supported compatibility level in SSMS by viewing the **Supported Compatibility Level** property on the **Information** page (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Services Properties**.</span></span> <span data-ttu-id="df18c-131">지원되는 호환성 수준 1103은 SQL Server SP1 이상이 설치되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-131">A supported compatibility level of 1103 indicates SQL Server SP1 or later is installed.</span></span> <span data-ttu-id="df18c-132">지원되는 호환성 수준은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df18c-132">The supported compatibility level cannot be changed.</span></span>  
  
  
