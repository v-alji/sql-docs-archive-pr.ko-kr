---
title: 데이터베이스 요구 사항(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b17c04db6805ea412b70644d2ee2c0b7da93b2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660011"
---
# <a name="database-requirements-master-data-services"></a><span data-ttu-id="31247-102">데이터베이스 요구 사항(MDS(Master Data Services))</span><span class="sxs-lookup"><span data-stu-id="31247-102">Database Requirements (Master Data Services)</span></span>
  <span data-ttu-id="31247-103">모든 마스터 데이터는 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="31247-103">All master data is stored in a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="31247-104">이 데이터베이스를 호스팅하는 컴퓨터는의 인스턴스를 실행 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="31247-104">The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="31247-105">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 를 사용하여 로컬 또는 원격 컴퓨터에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-105">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database on either a local or a remote computer.</span></span> <span data-ttu-id="31247-106">여러 환경 간에 데이터베이스를 이동하는 경우 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 서비스 및 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 를 새 위치의 데이터베이스에 연결하여 새 환경에서 정보를 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-106">If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service and [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to the database in its new location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31247-107">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 의 구성 요소를 설치할 모든 컴퓨터는 사용 허가를 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31247-107">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="31247-108">자세한 내용은 EULA(최종 사용자 사용권 계약)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31247-108">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31247-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="31247-109">Requirements</span></span>  
 <span data-ttu-id="31247-110">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스를 만들기 전에 다음 요구 사항이 충족되는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="31247-110">Before you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, ensure the following requirements are met.</span></span>  
  
### <a name="sql-server-edition"></a><span data-ttu-id="31247-111">SQL Server 버전</span><span class="sxs-lookup"><span data-stu-id="31247-111">SQL Server Edition</span></span>  
 <span data-ttu-id="31247-112">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스는 다음 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-112">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="31247-113">Business Intelligence(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-113">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="31247-114">Enterprise(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-114">Enterprise (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="31247-115">Developer(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-115">Developer (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="31247-116">Business Intelligence(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-116">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="31247-117">Enterprise(64비트) x64 – [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise에서만 업그레이드</span><span class="sxs-lookup"><span data-stu-id="31247-117">Enterprise (64-bit) x64 - Upgrade from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise only</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="31247-118">Developer(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-118">Developer (64-bit) x64</span></span>  
  
-   <span data-ttu-id="31247-119">Microsoft SQL Server 2008 R2 Enterprise(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-119">Microsoft SQL Server 2008 R2 Enterprise (64-bit) x64</span></span>  
  
-   <span data-ttu-id="31247-120">Microsoft SQL Server 2008 R2 Developer(64비트) x64</span><span class="sxs-lookup"><span data-stu-id="31247-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span></span>  
  
 <span data-ttu-id="31247-121">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31247-121">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="31247-122">운영 체제</span><span class="sxs-lookup"><span data-stu-id="31247-122">Operating System</span></span>  
 <span data-ttu-id="31247-123">의 지원 되는 Windows 운영 체제 및 기타 요구 사항에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [SQL Server 2014를 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31247-123">For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="31247-124">계정 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="31247-124">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="31247-125">Type</span><span class="sxs-lookup"><span data-stu-id="31247-125">Type</span></span>|<span data-ttu-id="31247-126">Description</span><span class="sxs-lookup"><span data-stu-id="31247-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="31247-127">사용자 계정</span><span class="sxs-lookup"><span data-stu-id="31247-127">User account</span></span>|<span data-ttu-id="31247-128">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 호스팅하기 위해 Windows 계정 또는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 계정을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-128">In [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="31247-129">사용자 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에서 **sysadmin** 서버 역할에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31247-129">The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="31247-130">**sysadmin** 역할에 대한 자세한 내용은 [서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31247-130">For more information about the **sysadmin** role, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="31247-131">관리자 계정</span><span class="sxs-lookup"><span data-stu-id="31247-131">administrator account</span></span>|<span data-ttu-id="31247-132">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스를 만들 때 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 시스템 관리자가 될 도메인 사용자 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31247-132">When you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="31247-133">이 데이터베이스에 연결된 모든 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션에 대해 이 사용자는 모든 기능 영역에서 모든 모델과 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-133">For all [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications associated with this database, this user can update all models and all data in all functional areas.</span></span> <span data-ttu-id="31247-134">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31247-134">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>|  
  
### <a name="database-backup"></a><span data-ttu-id="31247-135">데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="31247-135">Database Backup</span></span>  
 <span data-ttu-id="31247-136">매일 작업량이 적은 시간에 전체 데이터베이스를 백업하고 사용자 환경의 요구 사항에 따라 트랜잭션 로그를 보다 자주 백업하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="31247-136">As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment.</span></span> <span data-ttu-id="31247-137">데이터베이스 백업에 대한 자세한 내용은 [백업 개요&#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31247-137">For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31247-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31247-138">See Also</span></span>  
 <span data-ttu-id="31247-139">[MDS(Master Data Services) 설치](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="31247-139">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="31247-140">[MDS(Master Data Services) 데이터베이스 만들기](create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="31247-140">[Create a Master Data Services Database](create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="31247-141">[MDS(Master Data Services) 데이터베이스](../master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="31247-141">[Master Data Services Database](../master-data-services-database.md) </span></span>  
 <span data-ttu-id="31247-142">[MDS(Master Data Services) 데이터베이스에 연결 대화 상자](../connect-to-a-master-data-services-database-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="31247-142">[Connect to a Master Data Services Database Dialog Box](../connect-to-a-master-data-services-database-dialog-box.md) </span></span>  
 [<span data-ttu-id="31247-143">데이터베이스 만들기 마법사&#40;Master Data Services 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="31247-143">Create Database Wizard &#40;Master Data Services Configuration Manager&#41;</span></span>](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
