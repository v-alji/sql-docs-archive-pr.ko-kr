---
title: SQL 기록기 서비스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- VDI [SQL Server]
- restoring [SQL Server], SQL Writer Service
- backups [SQL Server], while SQL Server running
- Volume Shadow Copy Service
- volume backups while running [SQL Server]
- Virtual Backup Device Interface [SQL Server]
- SQL Writer Service
- services [SQL Server], SQL Writer
- MSDE Writer
- VSS
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 310722c6617c7a2c9e0f384ec23ae371ab230536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646631"
---
# <a name="sql-writer-service"></a><span data-ttu-id="7a8e8-102">SQL 기록기 서비스</span><span class="sxs-lookup"><span data-stu-id="7a8e8-102">SQL Writer Service</span></span>
  <span data-ttu-id="7a8e8-103">SQL 기록기 서비스는 볼륨 섀도 복사본 서비스 프레임워크를 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 백업 및 복원을 위한 추가 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-103">The SQL Writer Service provides added functionality for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the Volume Shadow Copy Service framework.</span></span>  
  
 <span data-ttu-id="7a8e8-104">SQL 기록기 서비스는 자동으로 설치되며</span><span class="sxs-lookup"><span data-stu-id="7a8e8-104">The SQL Writer Service is installed automatically.</span></span> <span data-ttu-id="7a8e8-105">VSS(볼륨 섀도 복사본 서비스) 애플리케이션이 백업 또는 복원을 요청할 때 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-105">It must be running when the Volume Shadow Copy Service (VSS) application requests a backup or restore.</span></span> <span data-ttu-id="7a8e8-106">서비스를 구성하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 서비스 애플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-106">To configure the service, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services applet.</span></span> <span data-ttu-id="7a8e8-107">SQL 기록기 서비스는 모든 운영 체제에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-107">The SQL Writer Service installs on all operating systems.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="7a8e8-108">목적</span><span class="sxs-lookup"><span data-stu-id="7a8e8-108">Purpose</span></span>  
 <span data-ttu-id="7a8e8-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 실행 중에 데이터 파일을 잠그고 이 파일에 독점적으로 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-109">When running, [!INCLUDE[ssDE](../../includes/ssde-md.md)] locks and has exclusive access to the data files.</span></span> <span data-ttu-id="7a8e8-110">SQL 기록기 서비스가 실행 중이 아니면 Windows에서 실행 중인 백업 프로그램이 데이터 파일에 액세스할 수 없으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업을 사용하여 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-110">When the SQL Writer Service is not running, backup programs running in Windows do not have access to the data files, and backups must be performed using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup.</span></span>  
  
 <span data-ttu-id="7a8e8-111">SQL 기록기 서비스를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 동안에도 Windows 백업 프로그램이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 파일을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-111">Use the SQL Writer Service to permit Windows backup programs to copy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
## <a name="volume-shadow-copy-service"></a><span data-ttu-id="7a8e8-112">볼륨 섀도 복사본 서비스</span><span class="sxs-lookup"><span data-stu-id="7a8e8-112">Volume Shadow Copy Service</span></span>  
 <span data-ttu-id="7a8e8-113">VSS는 시스템의 애플리케이션이 볼륨에 계속 쓰는 동안 볼륨 백업을 수행할 수 있도록 프레임워크를 구현하는 COM API 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-113">The VSS is a set of COM APIs that implements a framework to allow volume backups to be performed while applications on a system continue to write to the volumes.</span></span> <span data-ttu-id="7a8e8-114">VSS는 디스크의 데이터를 업데이트하는 사용자 애플리케이션(기록자)과 애플리케이션을 백업하는 사용자 애플리케이션(요청자) 간 조정을 허용하는 일관된 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-114">The VSS provides a consistent interface that allows coordination between user applications that update data on disk (writers) and those that back up applications (requestors).</span></span>  
  
 <span data-ttu-id="7a8e8-115">VSS는 제공하는 서비스의 성능과 안정성을 저하시키지 않고도 실행 중인 시스템, 특히 서버에서 안정적인 백업용 이미지를 캡처하고 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-115">The VSS captures and copies stable images for backup on running systems, particularly servers, without unduly degrading the performance and stability of the services they provide.</span></span> <span data-ttu-id="7a8e8-116">VSS에 대한 자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-116">For more information on the VSS, see your Windows documentation.</span></span>  
  
## <a name="virtual-backup-device-interface-vdi"></a><span data-ttu-id="7a8e8-117">VDI(Virtual Backup Device Interface)</span><span class="sxs-lookup"><span data-stu-id="7a8e8-117">Virtual Backup Device Interface (VDI)</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7a8e8-118">에서는 독립 소프트웨어 공급업체들이 백업 및 복원 작업을 지원하기 위해 해당 제품에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 통합할 수 있도록 하는 VDI(Virtual Backup Device Interface)라는 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-118">provides an API called Virtual Backup Device Interface (VDI) that enables independent software vendors to integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into their products for providing support for backup and restore operations.</span></span> <span data-ttu-id="7a8e8-119">이러한 API는 최고의 안정성과 성능을 제공하도록 설계되었으며 모든 최신 기능과 스냅샷 백업 기능을 비롯하여 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-119">These APIs are engineered to provide maximum reliability and performance, and support the full range of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore functionality, including the full range of hot and snapshot backup capabilities.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="7a8e8-120">사용 권한</span><span class="sxs-lookup"><span data-stu-id="7a8e8-120">Permissions</span></span>  
 <span data-ttu-id="7a8e8-121">SQL 기록기 서비스는 **로컬 시스템** 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-121">The SQL Writer service must run under the **Local System** account.</span></span> <span data-ttu-id="7a8e8-122">SQL 기록기 서비스는 **NT Service\SQLWriter** 로그인을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-122">The SQL Writer service uses the **NT Service\SQLWriter** login to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7a8e8-123">**NT Service\SQLWriter** 로그인을 사용하면 SQL 기록기 프로세스가 **로그인 없음**으로 지정된 계정에서 보다 낮은 권한 수준으로 실행될 수 있으므로 취약성이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-123">Using the **NT Service\SQLWriter** login allows the SQL Writer process to run at a lower privilege level in an account designated as **no login**, which limits vulnerability.</span></span> <span data-ttu-id="7a8e8-124">SQL 기록기 서비스를 사용하지 않도록 설정하면 System Center Data Protection Manager와 같이 VSS 스냅샷에 의존하는 모든 유틸리티와 일부 타사 제품이 손상되거나 저하되며 일관성이 없는 데이터베이스 백업을 수행할 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-124">If the SQL Writer service is disabled, then any utility which in relies on VSS snapshots, such as System Center Data Protection Manager, as well as some other 3rd-party products, would be broken, or worse, at risk of taking backups of databases which were not consistent.</span></span> <span data-ttu-id="7a8e8-125">SQL 기록기 서비스가 실행되는 시스템인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](과)와 호스트 시스템(가상 머신의 경우)에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 백업을 제외한 어떤 것도 사용할 필요가 없는 경우 SQL 기록기 서비스를 사용하지 않도록 설정해도 괜찮으며 로그인을 제거해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-125">If neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the system it runs on, nor the host system (in the event of a virtual machine), need to use anything besides [!INCLUDE[tsql](../../includes/tsql-md.md)] backup, then the SQL Writer service can be safely disabled and the login removed.</span></span>  <span data-ttu-id="7a8e8-126">SQL 기록기 서비스는 시스템 또는 볼륨 수준 백업에서 호출될 수 있습니다. 이때 백업이 직접 스냅샷을 기반으로 하는지 여부는 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-126">Note that the SQL Writer service may be invoked by a system or volume level backup, whether the backup is directly snapshot-based or not.</span></span> <span data-ttu-id="7a8e8-127">일부 시스템 백업 제품은 VSS를 사용하여 열려 있거나 잠긴 파일에 의해 차단되는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-127">Some system backup products use VSS to avoid being blocked by open or locked files.</span></span> <span data-ttu-id="7a8e8-128">SQL 기록기 서비스는 작업 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 모든 I/O를 잠깐 중지시키기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 승격된 권한을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8e8-128">The SQL Writer service needs elevated permissions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because in the course of its activities it briefly freezes all I/O for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="features"></a><span data-ttu-id="7a8e8-129">기능</span><span class="sxs-lookup"><span data-stu-id="7a8e8-129">Features</span></span>  
 <span data-ttu-id="7a8e8-130">SQL 기록기에서 지원하는 기능</span><span class="sxs-lookup"><span data-stu-id="7a8e8-130">SQL Writer supports:</span></span>  
  
-   <span data-ttu-id="7a8e8-131">전체 텍스트 카탈로그를 포함한 전체 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="7a8e8-131">Full database backup and restore including full-text catalogs</span></span>  
  
-   <span data-ttu-id="7a8e8-132">차등 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="7a8e8-132">Differential backup and restore</span></span>  
  
-   <span data-ttu-id="7a8e8-133">복원(이동)</span><span class="sxs-lookup"><span data-stu-id="7a8e8-133">Restore with move</span></span>  
  
-   <span data-ttu-id="7a8e8-134">데이터베이스 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="7a8e8-134">Database rename</span></span>  
  
-   <span data-ttu-id="7a8e8-135">복사 전용 백업</span><span class="sxs-lookup"><span data-stu-id="7a8e8-135">Copy-only backup</span></span>  
  
-   <span data-ttu-id="7a8e8-136">데이터베이스 스냅샷 자동 복구</span><span class="sxs-lookup"><span data-stu-id="7a8e8-136">Auto-recovery of database snapshot</span></span>  
  
 <span data-ttu-id="7a8e8-137">SQL 기록기에서 지원하지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="7a8e8-137">SQL Writer does not support:</span></span>  
  
-   <span data-ttu-id="7a8e8-138">로그 백업</span><span class="sxs-lookup"><span data-stu-id="7a8e8-138">Log backups</span></span>  
  
-   <span data-ttu-id="7a8e8-139">파일 및 파일 그룹 백업</span><span class="sxs-lookup"><span data-stu-id="7a8e8-139">File and filegroup backup</span></span>  
  
-   <span data-ttu-id="7a8e8-140">페이지 복원</span><span class="sxs-lookup"><span data-stu-id="7a8e8-140">Page restore</span></span>  
  
  
