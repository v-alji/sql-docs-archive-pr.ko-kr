---
title: 기록 정리 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84bc697b7fb18269fc581cea51e111aebc82c15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638942"
---
# <a name="history-cleanup-task"></a><span data-ttu-id="de026-102">기록 정리 태스크</span><span class="sxs-lookup"><span data-stu-id="de026-102">History Cleanup Task</span></span>
  <span data-ttu-id="de026-103">기록 정리 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 데이터베이스의 다음 기록 테이블에서 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="de026-103">The History Cleanup task deletes entries in the following history tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
-   <span data-ttu-id="de026-104">backupfile</span><span class="sxs-lookup"><span data-stu-id="de026-104">backupfile</span></span>  
  
-   <span data-ttu-id="de026-105">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="de026-105">backupfilegroup</span></span>  
  
-   <span data-ttu-id="de026-106">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="de026-106">backupmediafamily</span></span>  
  
-   <span data-ttu-id="de026-107">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="de026-107">backupmediaset</span></span>  
  
-   <span data-ttu-id="de026-108">backupset</span><span class="sxs-lookup"><span data-stu-id="de026-108">backupset</span></span>  
  
-   <span data-ttu-id="de026-109">restorefile</span><span class="sxs-lookup"><span data-stu-id="de026-109">restorefile</span></span>  
  
-   <span data-ttu-id="de026-110">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="de026-110">restorefilegroup</span></span>  
  
-   <span data-ttu-id="de026-111">restorehistory</span><span class="sxs-lookup"><span data-stu-id="de026-111">restorehistory</span></span>  
  
 <span data-ttu-id="de026-112">기록 정리 태스크를 사용하면 패키지가 백업 및 복원 작업, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 및 데이터베이스 유지 관리 계획과 관련된 기록 데이터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de026-112">By using the History Cleanup task, a package can delete historical data related to backup and restore activities, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, and database maintenance plans.</span></span>  
  
 <span data-ttu-id="de026-113">이 태스크는 sp_delete_backuphistory 시스템 저장 프로시저를 캡슐화하고 지정한 날짜를 프로시저에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="de026-113">This task encapsulates the sp_delete_backuphistory system stored procedure and passes the specified date to the procedure as an argument.</span></span> <span data-ttu-id="de026-114">자세한 내용은 [sp_delete_backuphistory&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de026-114">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
## <a name="configuration-of-the-history-cleanup-task"></a><span data-ttu-id="de026-115">기록 정리 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="de026-115">Configuration of the History Cleanup Task</span></span>  
 <span data-ttu-id="de026-116">이 태스크에는 기록 테이블에 보관되는 데이터의 가장 오래된 날짜를 지정하는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de026-116">The task includes a property for specifying the oldest date of data retained in the history tables.</span></span> <span data-ttu-id="de026-117">현재 날짜로부터의 일, 주, 월 또는 연 수로 날짜를 지정하면 태스크에서 자동으로 이 간격이 특정 날짜로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="de026-117">You can indicate the date by number of days, weeks, months, or years from the current day, and the task automatically translates the interval to a date.</span></span>  
  
 <span data-ttu-id="de026-118">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de026-118">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="de026-119">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de026-119">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="de026-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="de026-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="de026-121">기록 정리 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="de026-121">History Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 <span data-ttu-id="de026-122">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="de026-122">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="de026-123">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="de026-123">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="de026-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de026-124">See Also</span></span>  
 <span data-ttu-id="de026-125">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="de026-125">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="de026-126">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="de026-126">Control Flow</span></span>](control-flow.md)  
  
  
