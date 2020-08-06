---
title: 유지 관리 정리 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4d39dd775402adadbe51eaadc530f4feb288ab9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649614"
---
# <a name="maintenance-cleanup-task"></a><span data-ttu-id="1efc2-102">유지 관리 정리 태스크</span><span class="sxs-lookup"><span data-stu-id="1efc2-102">Maintenance Cleanup Task</span></span>
  <span data-ttu-id="1efc2-103">유지 관리 정리 태스크는 유지 관리 계획에서 만든 데이터베이스 백업 파일 및 보고서를 비롯하여 유지 관리 계획과 관련된 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-103">The Maintenance Cleanup task removes files related to maintenance plans, including database backup files and reports created by maintenance plans.</span></span> <span data-ttu-id="1efc2-104">자세한 내용은 [유지 관리 계획](../../relational-databases/maintenance-plans/maintenance-plans.md) 및 [SQL Server 데이터베이스 백업 및 복원](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1efc2-104">For more information, see [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md) and [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="1efc2-105">유지 관리 정리 태스크를 사용하여 패키지에서 지정한 서버의 백업 파일 또는 유지 관리 계획 보고서를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-105">By using the Maintenance Cleanup task, a package can remove the backup files or maintenance plan reports on the specified server.</span></span> <span data-ttu-id="1efc2-106">유지 관리 정리 태스크는 특정 파일을 제거하거나 폴더에 있는 파일 그룹을 제거하는 옵션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-106">The Maintenance Cleanup task includes an option to remove a specific file or remove a group of files in a folder.</span></span> <span data-ttu-id="1efc2-107">필요에 따라 삭제할 파일의 확장명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-107">Optionally you can specify the extension of the files to delete.</span></span>  
  
 <span data-ttu-id="1efc2-108">백업 파일을 제거하도록 유지 관리 정리 태스크를 구성할 때 기본 파일 이름 확장명은 BAK이며</span><span class="sxs-lookup"><span data-stu-id="1efc2-108">When you configure the Maintenance Cleanup task to remove backup files, the default file name extension is BAK.</span></span> <span data-ttu-id="1efc2-109">보고서 파일의 경우 기본 파일 이름 확장명은 TXT입니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-109">For report files, the default file name extension is TXT.</span></span> <span data-ttu-id="1efc2-110">필요에 맞게 확장명을 업데이트할 수 있으며 확장명이 256자 미만이기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-110">You can update the extensions to suit your needs; the only limitation is that extensions must be less than 256 characters long.</span></span>  
  
 <span data-ttu-id="1efc2-111">일반적으로 더 이상 필요하지 않은 기존 파일을 제거하며 유지 관리 정리 태스크를 구성하여 지정된 보존 기간에 도달한 파일을 삭제하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-111">Typically, you want to remove old files that are no longer needed, and the Maintenance Cleanup task can be configured to delete files that have reached a specified age.</span></span> <span data-ttu-id="1efc2-112">예를 들면 4주 이상된 파일을 삭제하도록 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-112">For example, the task can be configured to delete files that are older than four weeks.</span></span> <span data-ttu-id="1efc2-113">일, 주, 월 또는 년을 사용하여 삭제할 파일의 보존 기간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-113">You can specify the age of files to delete by using days, weeks, months, or years.</span></span> <span data-ttu-id="1efc2-114">삭제할 파일의 최소 보존 기간을 지정하지 않으면 지정한 형식의 파일이 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-114">If you do not specify the minimum age of files to delete, all files of the specified type are deleted.</span></span>  
  
 <span data-ttu-id="1efc2-115">이전 버전의 유지 관리 정리 태스크와 달리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전의 태스크에서는 지정된 디렉터리의 하위 디렉터리에 있는 파일이 자동으로 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-115">In contrast to earlier versions of the Maintenance Cleanup task, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version of the task does not automatically delete files in the subdirectories of the specified directory.</span></span> <span data-ttu-id="1efc2-116">이러한 제약 조건으로 인해 유지 관리 정리 태스크의 기능을 이용하여 파일을 악의적으로 삭제할 수 있는 공격에 대한 노출 영역이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-116">This constraint reduces the surface area of any attack that could exploit the functionality of the Maintenance Cleanup task to delete files maliciously.</span></span> <span data-ttu-id="1efc2-117">첫 번째 수준의 하위 폴더를 삭제하려면 **유지 관리 정리 태스크** 대화 상자에서 **첫 번째 수준의 하위 폴더 포함** 옵션을 선택하여 이 작업을 수행하도록 명시적으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-117">To delete the first-level subfolders, you must explicitly elect to do this by checking the **Include first-level subfolders** option in the **Maintenance Cleanup Task** dialog box.</span></span>  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a><span data-ttu-id="1efc2-118">유지 관리 정리 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="1efc2-118">Configuration of the Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="1efc2-119">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1efc2-120">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc2-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1efc2-121">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1efc2-121">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1efc2-122">유지 관리 정리 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="1efc2-122">Maintenance Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="1efc2-123">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1efc2-123">Related Tasks</span></span>  
 <span data-ttu-id="1efc2-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법에 대한 자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1efc2-124">For details about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efc2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1efc2-125">See Also</span></span>  
 <span data-ttu-id="1efc2-126">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="1efc2-126">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="1efc2-127">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="1efc2-127">Control Flow</span></span>](control-flow.md)  
  
  
