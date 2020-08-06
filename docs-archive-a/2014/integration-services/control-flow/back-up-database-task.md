---
title: 데이터베이스 백업 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648501"
---
# <a name="back-up-database-task"></a><span data-ttu-id="30ebe-102">데이터베이스 백업 태스크</span><span class="sxs-lookup"><span data-stu-id="30ebe-102">Back Up Database Task</span></span>
  <span data-ttu-id="30ebe-103">데이터베이스 백업 태스크는 여러 가지 유형의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-103">The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database backups.</span></span> <span data-ttu-id="30ebe-104">자세한 내용은 [SQL Server Database 백업 및 복원](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ebe-104">For more information, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="30ebe-105">데이터베이스 백업 태스크를 사용하면 패키지가 단일 데이터베이스나 여러 데이터베이스를 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-105">By using the Back Up Database task, a package can back up a single database or multiple databases.</span></span> <span data-ttu-id="30ebe-106">태스크에서 단일 데이터베이스만 백업하는 경우 데이터베이스 또는 데이터베이스 파일과 파일 그룹 등의 백업 구성 요소를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-106">If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.</span></span>  
  
## <a name="supported-recover-models-and-backup-types"></a><span data-ttu-id="30ebe-107">지원되는 복구 모델 및 백업 유형</span><span class="sxs-lookup"><span data-stu-id="30ebe-107">Supported Recover Models and Backup Types</span></span>  
 <span data-ttu-id="30ebe-108">다음 표에서는 데이터베이스 백업 태스크가 지원하는 복구 모델과 백업 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-108">The following table lists the recovery models and backup types that the Back Up Database task supports.</span></span>  
  
|<span data-ttu-id="30ebe-109">복구 모델</span><span class="sxs-lookup"><span data-stu-id="30ebe-109">Recovery model</span></span>|<span data-ttu-id="30ebe-110">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="30ebe-110">Database</span></span>|<span data-ttu-id="30ebe-111">데이터베이스 - 차등</span><span class="sxs-lookup"><span data-stu-id="30ebe-111">Database differential</span></span>|<span data-ttu-id="30ebe-112">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="30ebe-112">Transaction log</span></span>|<span data-ttu-id="30ebe-113">파일 또는 파일 차등</span><span class="sxs-lookup"><span data-stu-id="30ebe-113">File or file differential</span></span>|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|<span data-ttu-id="30ebe-114">간단한</span><span class="sxs-lookup"><span data-stu-id="30ebe-114">Simple</span></span>|<span data-ttu-id="30ebe-115">필수</span><span class="sxs-lookup"><span data-stu-id="30ebe-115">Required</span></span>|<span data-ttu-id="30ebe-116">옵션</span><span class="sxs-lookup"><span data-stu-id="30ebe-116">Optional</span></span>|<span data-ttu-id="30ebe-117">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="30ebe-117">Not supported</span></span>|<span data-ttu-id="30ebe-118">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="30ebe-118">Not supported</span></span>|  
|<span data-ttu-id="30ebe-119">전체</span><span class="sxs-lookup"><span data-stu-id="30ebe-119">Full</span></span>|<span data-ttu-id="30ebe-120">필수</span><span class="sxs-lookup"><span data-stu-id="30ebe-120">Required</span></span>|<span data-ttu-id="30ebe-121">옵션</span><span class="sxs-lookup"><span data-stu-id="30ebe-121">Optional</span></span>|<span data-ttu-id="30ebe-122">필수</span><span class="sxs-lookup"><span data-stu-id="30ebe-122">Required</span></span>|<span data-ttu-id="30ebe-123">옵션</span><span class="sxs-lookup"><span data-stu-id="30ebe-123">Optional</span></span>|  
|<span data-ttu-id="30ebe-124">대량 로그</span><span class="sxs-lookup"><span data-stu-id="30ebe-124">Bulk-logged</span></span>|<span data-ttu-id="30ebe-125">필수</span><span class="sxs-lookup"><span data-stu-id="30ebe-125">Required</span></span>|<span data-ttu-id="30ebe-126">옵션</span><span class="sxs-lookup"><span data-stu-id="30ebe-126">Optional</span></span>|<span data-ttu-id="30ebe-127">필수</span><span class="sxs-lookup"><span data-stu-id="30ebe-127">Required</span></span>|<span data-ttu-id="30ebe-128">옵션</span><span class="sxs-lookup"><span data-stu-id="30ebe-128">Optional</span></span>|  
  
 <span data-ttu-id="30ebe-129">데이터베이스 백업 태스크는 Transact-SQL BACKUP 문을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-129">The Back Up Database task encapsulates a Transact-SQL BACKUP statement.</span></span> <span data-ttu-id="30ebe-130">자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ebe-130">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
## <a name="configuration-of-the-back-up-database-task"></a><span data-ttu-id="30ebe-131">데이터베이스 백업 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="30ebe-131">Configuration of the Back Up Database Task</span></span>  
 <span data-ttu-id="30ebe-132">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-132">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="30ebe-133">이 태스크는 **디자이너의** 도구 상자 **에 있는** 유지 관리 계획 태스크 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 섹션에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ebe-133">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="30ebe-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="30ebe-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="30ebe-135">데이터베이스 백업 태스크&#40;유지 관리 계획&#41;</span><span class="sxs-lookup"><span data-stu-id="30ebe-135">Back Up Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 <span data-ttu-id="30ebe-136">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="30ebe-136">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="30ebe-137">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="30ebe-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
