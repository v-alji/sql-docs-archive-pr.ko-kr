---
title: SQL Server 설치 계획 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, planning
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5b1dae9d2ef32298a9ddf2eeed1530e5ae97683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653717"
---
# <a name="planning-a-sql-server-installation"></a><span data-ttu-id="bcea8-102">SQL Server 설치 계획</span><span class="sxs-lookup"><span data-stu-id="bcea8-102">Planning a SQL Server Installation</span></span>
  <span data-ttu-id="bcea8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="bcea8-103">To install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], follow these steps:</span></span>  
  
-   <span data-ttu-id="bcea8-104">설치 요구 사항, 시스템 구성 검사 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치를 위한 보안 고려 사항을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-104">Review installation requirements, system configuration checks, and security considerations for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
-   <span data-ttu-id="bcea8-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램을 실행하여 설치하거나 이후 버전으로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-105">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to install or upgrade to a later version.</span></span>  
  
-   <span data-ttu-id="bcea8-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilities to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bcea8-107">소프트웨어 사용이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 볼륨 라이선스 계약 또는 공급 업체와의 ISV  또는 OEM  계약과 같은 별도의 계약에 의해 관리되지 않는 한 설치 방법에 상관없이 개인 또는 업체 대표로서 소프트웨어 사용 조건에 대한 동의를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-107">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="bcea8-108">사용 조건은 검토 및 동의를 위해 설치 프로그램 사용자 인터페이스에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-108">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="bcea8-109">/Q 또는 /QS 매개 변수를 사용한 무인 설치는 /IAcceptSQLServerLicenseTerms 매개 변수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-109">Unattended installations (using the /Q or /QS parameters) must include the /IAcceptSQLServerLicenseTerms parameter.</span></span> <span data-ttu-id="bcea8-110">[Microsoft 소프트웨어 사용권 계약(Microsoft Software License Terms)](https://go.microsoft.com/fwlink/?LinkID=148209)에서 사용 조건을 별도로 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-110">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkID=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcea8-111">소프트웨어의 수령 방법(예: [!INCLUDE[msCoName](../../includes/msconame-md.md)] 볼륨 라이선스를 통해 수령)에 따라 사용자의 소프트웨어 사용에 추가 조건이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-111">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcea8-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="bcea8-112">In This Section</span></span>  
 [<span data-ttu-id="bcea8-113">SQL Server 설치의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="bcea8-113">What's New in SQL Server Installation</span></span>](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md)  
 <span data-ttu-id="bcea8-114">이 항목에서는 이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]버전의 새로운 기능 및 향상된 기능에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-114">This topic describes the details about the new or improved features of installation in this version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-115">SQL Server 2014 설치에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bcea8-115">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
 <span data-ttu-id="bcea8-116">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스를 설치 및 실행하기 위한 최소 하드웨어 및 소프트웨어 요구 사항을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-116">This topic lists the minimum hardware and software requirements to install and run an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-117">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="bcea8-117">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 <span data-ttu-id="bcea8-118">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치하기 전과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치한 후에 고려해야 하는 보안 권장 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-118">This topic describes some security best practices that you should consider before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-119">Windows 서비스 계정 및 권한 구성</span><span class="sxs-lookup"><span data-stu-id="bcea8-119">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 <span data-ttu-id="bcea8-120">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이 릴리스에서 기본 서비스 구성과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 그리고 설치 후에 설정할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 대한 구성 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-120">This topic describes the default configuration of services in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services that you can set during and after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 [<span data-ttu-id="bcea8-121">네트워크 프로토콜 및 네트워크 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bcea8-121">Network Protocols and Network Libraries</span></span>](../../../2014/sql-server/install/network-protocols-and-network-libraries.md)  
 <span data-ttu-id="bcea8-122">이 항목에서는 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]릴리스의 네트워크 프로토콜 기본 구성과 사용 가능한 구성 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-122">This topic describes the default configuration of network protocols in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the configuration options available.</span></span>  
  
 [<span data-ttu-id="bcea8-123">SQL Server의 여러 버전 및 인스턴스 작업</span><span class="sxs-lookup"><span data-stu-id="bcea8-123">Work with Multiple Versions and Instances of SQL Server</span></span>](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 <span data-ttu-id="bcea8-124">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 여러 버전 및 인스턴스를 설치할 때 고려해야 할 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-124">This topic describes the considerations for installing multiple versions and instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-125">SQL Server의 로컬 언어 버전</span><span class="sxs-lookup"><span data-stu-id="bcea8-125">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
 <span data-ttu-id="bcea8-126">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 지역화된 버전에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-126">This topic describes about the localized versions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bcea8-127">관련 단원</span><span class="sxs-lookup"><span data-stu-id="bcea8-127">Related Sections</span></span>  
 [<span data-ttu-id="bcea8-128">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="bcea8-128">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
 <span data-ttu-id="bcea8-129">이 섹션에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]설치를 위해 필요한 여러 설치 옵션에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-129">This section provides an overview of different installation options we have for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-130">SQL Server 2014 BI 기능 설치</span><span class="sxs-lookup"><span data-stu-id="bcea8-130">Install SQL Server 2014 BI Features</span></span>](install-sql-server-business-intelligence-features.md)  
 <span data-ttu-id="bcea8-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 설명서 중 이 섹션에서는 Microsoft BI 플랫폼의 일부인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 설치하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-131">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that are part of the Microsoft BI platform.</span></span>  
  
 [<span data-ttu-id="bcea8-132">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="bcea8-132">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
 <span data-ttu-id="bcea8-133">이 섹션에서는 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전의 인스턴스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-133">The section provides an overview of upgrading instances of previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-134">SQL Server 2014 제거</span><span class="sxs-lookup"><span data-stu-id="bcea8-134">Uninstall SQL Server 2014</span></span>](uninstall-sql-server.md)  
 <span data-ttu-id="bcea8-135">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 기존 인스턴스를 완전히 제거하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 설치할 수 있도록 시스템을 준비하려면 이 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bcea8-135">Refer this section to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bcea8-136">SQL Server 장애 조치(Failover) 클러스터 설치</span><span class="sxs-lookup"><span data-stu-id="bcea8-136">SQL Server Failover Cluster Installation</span></span>](../failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="bcea8-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 설명서 중 이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터를 설치 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcea8-137">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcea8-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcea8-138">See Also</span></span>  
 <span data-ttu-id="bcea8-139">[SQL Server 2014의 빠른 시작 설치](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="bcea8-139">[Quick-Start Installation of SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="bcea8-140">[명령 프롬프트에서 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="bcea8-140">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="bcea8-141">[고가용성 솔루션&#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bcea8-141">[High Availability Solutions &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 <span data-ttu-id="bcea8-142">[장애 조치 (Failover) 클러스터링을 설치 하기 전에](../failover-clusters/install/before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="bcea8-142">[Before Installing Failover Clustering](../failover-clusters/install/before-installing-failover-clustering.md) </span></span>  
 [<span data-ttu-id="bcea8-143">설치 마법사 &#40;사용 하 여 SQL Server 2014로 업그레이드&#41;</span><span class="sxs-lookup"><span data-stu-id="bcea8-143">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
