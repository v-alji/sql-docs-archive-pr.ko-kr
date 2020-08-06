---
title: 업그레이드 프로세스 개요 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5da6dc3b3e6d6c7058193801100bf2552bfde7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742775"
---
# <a name="upgrade-process-overview"></a><span data-ttu-id="cda22-102">업그레이드 프로세스 개요</span><span class="sxs-lookup"><span data-stu-id="cda22-102">Upgrade Process Overview</span></span>
  <span data-ttu-id="cda22-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자를 사용하는 최선의 구현 방법과 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 위한 권장 프로세스에 대한 요약 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-103">This topic provides best practice information for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor and a summary of the recommended process for upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="upgrade-process"></a><span data-ttu-id="cda22-104">업그레이드 프로세스</span><span class="sxs-lookup"><span data-stu-id="cda22-104">Upgrade Process</span></span>  
 <span data-ttu-id="cda22-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]를 실행하는 서버를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-105">Servers that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cda22-106">일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소는 해당 위치에서 업그레이드할 수 있는 반면 일부 구성 요소는 마이그레이션해야 하며 또 다른 일부 구성 요소는 새 구성 요소로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-106">Whereas some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components can be upgraded in place, others must be migrated, and still others have been superseded by new components.</span></span> <span data-ttu-id="cda22-107">예를 들어 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]([!INCLUDE[ssIS](../../includes/ssis-md.md)])가 DTS(데이터 변환 서비스)를 대체하며 DTS는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-107">For example, starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) supersedes Data Transformation Services (DTS), and DTS is no longer supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cda22-108">업그레이드를 계획할 때는 현재 DTS 패키지를 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지로 업데이트하기 위한 계획을 세워야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-108">When you formulate your upgrade plan, you might need to plan for updating your current DTS packages to [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages.</span></span>  
  
 <span data-ttu-id="cda22-109">업그레이드 관리자를 사용하면 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치, 구성 요소 및 관련 파일을 평가하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드 또는 마이그레이션하는 동안이나 이후에 발생할 수 있는 알려진 문제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-109">Upgrade Advisor enables you to evaluate current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, components, and related files to identify known issues that will cause problems both during and after you upgrade or migrate to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cda22-110">이러한 알려진 문제 중 몇 가지는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-110">A few of these known issues block the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] upgrade.</span></span> <span data-ttu-id="cda22-111">업그레이드 관리자 보고서에서 이러한 문제는 업그레이드 블로커로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-111">In the Upgrade Advisor report, these issues are identified as Upgrade Blockers.</span></span> <span data-ttu-id="cda22-112">설치 프로그램을 실행하기 전에 업그레이드 블로커를 해결하지 않으면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치가 종료되고 업그레이드 관리자를 실행하여 업그레이드를 차단하는 특정 문제를 확인하도록 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-112">If you have not addressed the Upgrade Blockers before you run Setup, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup exits and recommends that you run Upgrade Advisor to identify the specific issues that are blocking the upgrade.</span></span>  
  
 <span data-ttu-id="cda22-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 데이터 및 시스템 설정을 백업하고 조직에 대해 정의된 운영 지침에 설명되어 있는 전략적 단계를 수행하는 것이 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-113">As a best practice before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you back up your data and system settings, and take strategic steps as outlined in the operational guidelines defined for your organization.</span></span> <span data-ttu-id="cda22-114">업그레이드를 완료하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="cda22-114">Use the following steps to complete the upgrade:</span></span>  
  
1.  <span data-ttu-id="cda22-115">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-115">Review [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="cda22-116">데이터 및 시스템 설정을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-116">Back up data and system settings.</span></span>  
  
3.  <span data-ttu-id="cda22-117">업그레이드 관리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-117">Run Upgrade Advisor.</span></span>  
  
     <span data-ttu-id="cda22-118">업그레이드 관리자는 데이터를 수정하거나 컴퓨터에 대한 설정을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-118">Upgrade Advisor does not modify your data or change settings on your computer.</span></span>  
  
4.  <span data-ttu-id="cda22-119">업그레이드 관리자 보고서에 나와 있는 문제를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-119">Review the issues identified in the Upgrade Advisor report.</span></span>  
  
5.  <span data-ttu-id="cda22-120">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로의 업그레이드를 방해하는 차단 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-120">Resolve any blocking issues that would prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="cda22-121">다른 모든 업그레이드 이전 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-121">Resolve any other pre-upgrade issues.</span></span>  
  
7.  <span data-ttu-id="cda22-122">업그레이드 관리자를 실행하여 모든 알려진 문제가 해결되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-122">Run Upgrade Advisor to verify that all known issues have been addressed.</span></span>  
  
8.  <span data-ttu-id="cda22-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-123">Run [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup.</span></span>  
  
9. <span data-ttu-id="cda22-124">모든 업그레이드 이후 및 마이그레이션 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="cda22-124">Resolve any post-upgrade and migration issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda22-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cda22-125">See Also</span></span>  
 <span data-ttu-id="cda22-126">[업그레이드 관리자 &#40;사용자 인터페이스를 실행 하는 중&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="cda22-126">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 <span data-ttu-id="cda22-127">[보고서 사용](../../../2014/sql-server/install/using-reports.md) </span><span class="sxs-lookup"><span data-stu-id="cda22-127">[Using Reports](../../../2014/sql-server/install/using-reports.md) </span></span>  
 [<span data-ttu-id="cda22-128">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="cda22-128">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
