---
title: 패키지 백업 및 복원 (SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660052"
---
# <a name="package-backup-and-restore-ssis-service"></a><span data-ttu-id="f1d6c-102">패키지 백업 및 복원(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="f1d6c-102">Package Backup and Restore (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="f1d6c-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="f1d6c-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="f1d6c-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f1d6c-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지는 파일 시스템, msdb 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 시스템 데이터베이스에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages can be saved to the file system or msdb, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system database.</span></span> <span data-ttu-id="f1d6c-107">msdb에 저장한 패키지는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원 기능을 사용하여 백업하거나 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-107">Packages saved to msdb can be backed up and restored using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore features.</span></span>  
  
 <span data-ttu-id="f1d6c-108">msdb 데이터베이스 백업 및 복원에 대한 자세한 내용은 다음 항목을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-108">For more information about backing up and restoring the msdb database, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f1d6c-109">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="f1d6c-109">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [<span data-ttu-id="f1d6c-110">시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f1d6c-110">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="f1d6c-111">에는 패키지 관리에 사용할 수 있는 **dtutil** 명령 프롬프트 유틸리티(dtutil.exec)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-111">includes the **dtutil** command-prompt utility (dtutil.exec), which you can use to manage packages.</span></span> <span data-ttu-id="f1d6c-112">자세한 내용은 [dtutil Utility](dtutil-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-112">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f1d6c-113">구성 파일</span><span class="sxs-lookup"><span data-stu-id="f1d6c-113">Configuration Files</span></span>  
 <span data-ttu-id="f1d6c-114">패키지에 포함된 모든 구성 파일은 파일 시스템에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-114">Any configuration files that the packages include are stored in the file system.</span></span> <span data-ttu-id="f1d6c-115">msdb 데이터베이스를 백업할 때는 이러한 파일이 함께 백업되지 않으므로 msdb에 저장된 패키지의 보안을 설정하는 계획의 일부로 주기적으로 구성 파일을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-115">These files are not backed up when you back up the msdb database; therefore, you should make sure that the configuration files are backed up regularly as part of your plan for securing packages saved to msdb.</span></span> <span data-ttu-id="f1d6c-116">msdb 데이터베이스의 백업에 구성을 포함시키려면 파일 기반 구성 대신 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 유형 사용을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-116">To include configurations in the backup of the msdb database, you should consider using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type instead of file-based configurations.</span></span>  
  
## <a name="packages-stored-in-the-file-system"></a><span data-ttu-id="f1d6c-117">파일 시스템에 저장된 패키지</span><span class="sxs-lookup"><span data-stu-id="f1d6c-117">Packages Stored in the File System</span></span>  
 <span data-ttu-id="f1d6c-118">파일 시스템에 저장한 패키지의 백업은 서버의 파일 시스템 백업 계획에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-118">The backup of packages that are saved to the file system should be included in the plan for backing up the file system of the server.</span></span> <span data-ttu-id="f1d6c-119">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스 구성 파일의 기본 이름은 MsDtsSrvr.ini.xml이며 서비스에서 모니터링하는 서버의 폴더를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-119">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service configuration file, which has the default name MsDtsSrvr.ini.xml, lists the folders on the server that the service monitors.</span></span> <span data-ttu-id="f1d6c-120">이러한 폴더는 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-120">You should make sure these folders are backed up.</span></span> <span data-ttu-id="f1d6c-121">또한 패키지를 서버의 다른 폴더에 저장할 수 있으며 이러한 폴더도 백업에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d6c-121">Additionally, packages may be stored in other folders on the server and you should make sure to include these folders in the backup.</span></span>  
  
  
