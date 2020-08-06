---
title: Analysis Services 구성-데이터 디렉터리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e0711c6998e8f931e7d561bb388a0d7809733a44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650531"
---
# <a name="analysis-services-configuration---data-directories"></a><span data-ttu-id="3b517-102">Analysis Services 구성 - 데이터 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-102">Analysis Services Configuration - Data Directories</span></span>
  <span data-ttu-id="3b517-103">다음 표의 기본 디렉터리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 사용자가 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-103">The default directories in the following table are user-configurable during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="3b517-104">이러한 파일에 대 한 액세스 권한은 설치 중에 만들어지고 프로 비전 되는 SQLServerMSASUser $ 보안 그룹의 멤버와 로컬 관리자에 게 부여 됩니다 \<instance> .</span><span class="sxs-lookup"><span data-stu-id="3b517-104">Permission to access these files is granted to local administrators and to members of the SQLServerMSASUser$\<instance> security group that is created and provisioned during Setup.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3b517-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="3b517-105">UI element list</span></span>  
  
|<span data-ttu-id="3b517-106">Description</span><span class="sxs-lookup"><span data-stu-id="3b517-106">Description</span></span>|<span data-ttu-id="3b517-107">기본 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-107">Default directory</span></span>|<span data-ttu-id="3b517-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="3b517-108">Recommendations</span></span>|  
|-----------------|-----------------------|---------------------|  
|<span data-ttu-id="3b517-109">데이터 루트 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-109">Data root directory</span></span>|<span data-ttu-id="3b517-110">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Data \| files\Microsoft SQL Server \ 폴더가 제한 된 권한으로 보호 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-110">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Data\|Ensure that the \Program files\Microsoft SQL Server\ folder is protected with limited permissions.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3b517-111">성능은 대부분의 구성에서 데이터 디렉터리가 있는 스토리지의 성능에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-111">performance depends, in many configurations, on the performance of the storage on which the data directory is located.</span></span> <span data-ttu-id="3b517-112">이 디렉터리는 시스템에 연결된 성능이 가장 높은 스토리지에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="3b517-112">Place this directory on the highest performing storage that is attached to the system.</span></span> <span data-ttu-id="3b517-113">장애 조치(Failover) 클러스터 설치의 경우 공유 디스크에 데이터 디렉터리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-113">For failover cluster installations, ensure that data directories are placed on the shared disk.</span></span>|  
|<span data-ttu-id="3b517-114">로그 파일 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-114">Log file directory</span></span>|<span data-ttu-id="3b517-115">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Log \| 로그 파일에 대 한 디렉터리 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 이며 디렉터리 이며 flightrecorder 로그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-115">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Log\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] log files, and it includes the FlightRecorder log.</span></span> <span data-ttu-id="3b517-116">비행 레코더 기간을 늘려야 하는 경우 로그 디렉터리에 적절한 공간이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b517-116">If you increase the flight recorder duration, ensure that the log directory has adequate space.</span></span>|  
|<span data-ttu-id="3b517-117">임시 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-117">Temp directory</span></span>|<span data-ttu-id="3b517-118">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Temp \| 는 고성능 저장소 하위 시스템에 임시 디렉터리를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-118">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Temp\|Place the Temp directory on the high performance storage subsystem.</span></span>|  
|<span data-ttu-id="3b517-119">백업 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-119">Backup directory</span></span>|<span data-ttu-id="3b517-120">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Backup \| 이 디렉터리는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 기본 백업 파일의 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-120">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Backup\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] default backup files.</span></span> <span data-ttu-id="3b517-121">SharePoint용 PowerPivot 설치 시에는 PowerPivot 시스템 서비스에서 PowerPivot 데이터 파일도 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-121">For PowerPivot for SharePoint installations, it also where the PowerPivot System Services caches PowerPivot data files.</span></span><br /><br /> <span data-ttu-id="3b517-122">데이터 손실을 방지할 수 있도록 적절한 권한을 설정하고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서비스를 위한 사용자 그룹에 백업 디렉터리에 대한 적절한 쓰기 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b517-122">Ensure appropriate permissions are set to prevent data loss, and that the user group for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service has adequate permissions to write to the backup directory.</span></span> <span data-ttu-id="3b517-123">백업 디렉터리에는 매핑된 드라이브를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-123">Using a mapped drive for backup directories is not supported.</span></span>|  
  
## <a name="notes"></a><span data-ttu-id="3b517-124">메모</span><span class="sxs-lookup"><span data-stu-id="3b517-124">Notes</span></span>  
  
-   <span data-ttu-id="3b517-125">SharePoint 팜에 배포된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 애플리케이션 파일, 데이터 파일 및 속성을 콘텐츠 데이터베이스와 서비스 애플리케이션 데이터베이스에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-125">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instances that are deployed on a SharePoint farm store application files, data files, and properties in content databases and service application databases.</span></span>  
  
-   <span data-ttu-id="3b517-126">기존 설치에 기능을 추가할 경우 이전에 설치한 기능의 위치를 변경하거나 새 기능의 위치를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-126">When you add features to an existing installation, you cannot change the location of a previously installed feature, nor can you specify the location for a new feature.</span></span>  
  
-   <span data-ttu-id="3b517-127">기본이 아닌 설치 디렉터리를 지정하는 경우 설치 폴더가 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대해 고유한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-127">If you specify non-default installation directories, ensure that the installation folders are unique to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b517-128">이 대화 상자의 어떠한 디렉터리도 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 디렉터리와 공유되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-128">None of the directories in this dialog box should be shared with directories from other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b517-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 내의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소도 별도의 디렉터리에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-129">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components within an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should also be installed to separate directories.</span></span>  
  
-   <span data-ttu-id="3b517-130">다음과 같은 위치에는 프로그램 파일 및 데이터 파일을 설치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b517-130">Program files and data files cannot be installed in the following situations:</span></span>  
  
    -   <span data-ttu-id="3b517-131">이동식 디스크 드라이브</span><span class="sxs-lookup"><span data-stu-id="3b517-131">On a removable disk drive</span></span>  
  
    -   <span data-ttu-id="3b517-132">압축 파일 시스템</span><span class="sxs-lookup"><span data-stu-id="3b517-132">On a file system that uses compression</span></span>  
  
    -   <span data-ttu-id="3b517-133">시스템 파일이 있는 디렉터리</span><span class="sxs-lookup"><span data-stu-id="3b517-133">To a directory where system files are located</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b517-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b517-134">See Also</span></span>  
 [<span data-ttu-id="3b517-135">SQL Server 기본 인스턴스 및 명명된 인스턴스의 파일 위치</span><span class="sxs-lookup"><span data-stu-id="3b517-135">File Locations for Default and Named Instances of SQL Server</span></span>](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
