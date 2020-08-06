---
title: 유지 관리 계획 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2f614e2cfad78cb1efddc49cc897ca57087fec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638763"
---
# <a name="maintenance-plans"></a><span data-ttu-id="41c18-102">유지 관리 계획</span><span class="sxs-lookup"><span data-stu-id="41c18-102">Maintenance Plans</span></span>
  <span data-ttu-id="41c18-103">유지 관리 계획은 데이터베이스를 최적화하고 정기적으로 백업하며 불일치를 제거하는 데 필요한 태스크의 워크플로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-103">Maintenance plans create a workflow of the tasks required to make sure that your database is optimized, regularly backed up, and free of inconsistencies.</span></span> <span data-ttu-id="41c18-104">유지 관리 계획 마법사에서도 중요한 유지 관리 계획을 만들지만 이러한 계획을 수동으로 만들면 유연성을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-104">The Maintenance Plan Wizard also creates core maintenance plans, but creating plans manually gives you much more flexibility.</span></span>  
  
## <a name="benefits-of-maintenance-plans"></a><span data-ttu-id="41c18-105">유지 관리 계획의 이점</span><span class="sxs-lookup"><span data-stu-id="41c18-105">Benefits of Maintenance Plans</span></span>  
 <span data-ttu-id="41c18-106">[!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)]의 유지 관리 계획은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에이전트 작업으로 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-106">In [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)], maintenance plans create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, which is run by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="41c18-107">유지 관리 계획은 예약된 간격으로 수동 또는 자동으로 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-107">Maintenance plans can be run manually or automatically at scheduled intervals.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="41c18-108">유지 관리 계획에서는 다음 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-108">maintenance plans provide the following features:</span></span>  
  
-   <span data-ttu-id="41c18-109">다양한 일반 유지 관리 태스크를 사용한 워크플로 만들기.</span><span class="sxs-lookup"><span data-stu-id="41c18-109">Workflow creation using a variety of typical maintenance tasks.</span></span> <span data-ttu-id="41c18-110">사용자 고유의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-110">You can also create your own custom [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span>  
  
-   <span data-ttu-id="41c18-111">개념 계층.</span><span class="sxs-lookup"><span data-stu-id="41c18-111">Conceptual hierarchies.</span></span> <span data-ttu-id="41c18-112">각 계획을 통해 태스크 워크플로를 만들거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-112">Each plan lets you create or edit task workflows.</span></span> <span data-ttu-id="41c18-113">각 계획의 태스크를 서로 다른 시간에 실행되도록 예약할 수 있는 하위 계획으로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-113">Tasks in each plan can be grouped into subplans, which can be scheduled to run at different times.</span></span>  
  
-   <span data-ttu-id="41c18-114">마스터 서버/대상 서버 환경에서 사용할 수 있는 다중 서버 계획에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="41c18-114">Support for multiserver plans that can be used in master server/target server environments.</span></span>  
  
-   <span data-ttu-id="41c18-115">원격 서버에 계획 기록을 로깅하는 작업에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="41c18-115">Support for logging plan history to remote servers.</span></span>  
  
-   <span data-ttu-id="41c18-116">Windows 인증 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 지원</span><span class="sxs-lookup"><span data-stu-id="41c18-116">Support for Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a><span data-ttu-id="41c18-117">유지 관리 계획 기능</span><span class="sxs-lookup"><span data-stu-id="41c18-117">Maintenace Plan Functionality</span></span>  
 <span data-ttu-id="41c18-118">다음 태스크를 수행하도록 유지 관리 계획을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-118">Maintenance plans can be created to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="41c18-119">새로운 채우기 비율을 사용하여 인덱스를 다시 만들어 데이터 및 인덱스 페이지에서 데이터를 재구성합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-119">Reorganize the data on the data and index pages by rebuilding indexes with a new fill factor.</span></span> <span data-ttu-id="41c18-120">새로운 채우기 비율을 사용하여 인덱스를 다시 만들면 데이터베이스 페이지에 동일하게 분산된 데이터와 사용 가능한 공간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-120">Rebuilding indexes with a new fill factor makes sure that database pages contain an equally distributed amount of data and free space.</span></span> <span data-ttu-id="41c18-121">또한 향후 더 빠르게 증가되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-121">It also enables faster growth in the future.</span></span> <span data-ttu-id="41c18-122">자세한 내용은 [인덱스의 채우기 비율 지정](../indexes/specify-fill-factor-for-an-index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41c18-122">For more information, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
-   <span data-ttu-id="41c18-123">빈 데이터베이스 페이지를 삭제하여 데이터 파일을 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-123">Compress data files by removing empty database pages.</span></span>  
  
-   <span data-ttu-id="41c18-124">쿼리 최적화 프로그램에 테이블 내 데이터 값의 배포에 대한 최신 정보가 있는지 확인하도록 인덱스 통계를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-124">Update index statistics to make sure the query optimizer has current information about the distribution of data values in the tables.</span></span> <span data-ttu-id="41c18-125">따라서 쿼리 최적화 프로그램은 데이터베이스에 저장된 데이터에 대한 더 많은 정보를 갖게 되므로 데이터에 대한 최상의 액세스 방법을 더 잘 판단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-125">This enables the query optimizer to make better judgments about the best way to access data, because it has more information about the data stored in the database.</span></span> <span data-ttu-id="41c18-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 정기적으로 인덱스 통계를 자동으로 업데이트하지만 이 옵션을 사용하여 통계를 즉시 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-126">Although index statistics are automatically updated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically, this option can force the statistics to update immediately.</span></span>  
  
-   <span data-ttu-id="41c18-127">시스템 또는 소프트웨어 문제로 인해 데이터가 손상되지 않았는지 확인하기 위해 데이터베이스 내의 데이터 및 데이터 페이지에 대해 내부 일관성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-127">Perform internal consistency checks of the data and data pages within the database to make sure that a system or software problem has not damaged data.</span></span>  
  
-   <span data-ttu-id="41c18-128">데이터베이스 및 트랜잭션 로그 파일을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-128">Back up the database and transaction log files.</span></span> <span data-ttu-id="41c18-129">데이터베이스 및 로그 백업은 지정된 기간 동안 보존될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-129">Database and log backups can be retained for a specified period.</span></span> <span data-ttu-id="41c18-130">따라서 데이터베이스를 마지막 데이터베이스 백업 이전 시간으로 복원해야 할 경우 사용될 백업의 기록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-130">This lets you create a history of backups to be used if you have to restore the database to a time earlier than the last database backup.</span></span> <span data-ttu-id="41c18-131">차등 백업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-131">You can also perform differential backups.</span></span>  
  
-   <span data-ttu-id="41c18-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-132">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="41c18-133">이는 다양한 동작을 수행하는 작업과 이러한 작업을 실행하도록 하는 유지 관리 계획을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-133">This can be used to create jobs that perform a variety of actions and the maintenance plans to run those jobs.</span></span>  
  
 <span data-ttu-id="41c18-134">유지 관리 태스크에 따라 생성된 결과는 텍스트 파일에 보고서로 기록되거나 `sysmaintplan_log`의 유지 관리 계획 테이블(`sysmaintplan_logdetail` 및 `msdb`)에 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-134">The results generated by the maintenance tasks can be written as a report to a text file or to the maintenance plan tables (`sysmaintplan_log` and `sysmaintplan_logdetail`) in `msdb`.</span></span> <span data-ttu-id="41c18-135">로그 파일 뷰어에서 이 결과를 보려면 **유지 관리 계획**을 마우스 오른쪽 단추로 클릭하고 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-135">To view the results in the log file viewer, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="41c18-136">관련 작업</span><span class="sxs-lookup"><span data-stu-id="41c18-136">Related Tasks</span></span>  
 <span data-ttu-id="41c18-137">유지 관리 계획을 시작하려면 다음 항목을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="41c18-137">Use the following topics to get started with maintenance plans.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41c18-138">**설명**</span><span class="sxs-lookup"><span data-stu-id="41c18-138">**Description**</span></span>|<span data-ttu-id="41c18-139">**항목**</span><span class="sxs-lookup"><span data-stu-id="41c18-139">**Topic**</span></span>|  
|<span data-ttu-id="41c18-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 유지 관리 계획을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-140">Describes how to create a maintenance plan by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|[<span data-ttu-id="41c18-141">유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="41c18-141">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)|  
|<span data-ttu-id="41c18-142">유지 관리 계획 디자인 화면을 사용하여 유지 관리 계획을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-142">Describes how to create a maintenance plan by using the Maintenance Plan Design Surface.</span></span>|[<span data-ttu-id="41c18-143">유지 관리 계획 만들기&#40;유지 관리 계획 디자인 화면&#41;</span><span class="sxs-lookup"><span data-stu-id="41c18-143">Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;</span></span>](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|<span data-ttu-id="41c18-144">개체 탐색기에서 사용할 수 있는 유지 관리 계획 기능을 문서화합니다.</span><span class="sxs-lookup"><span data-stu-id="41c18-144">Documents maintenance plan functionality available in Object Explorer.</span></span>|[<span data-ttu-id="41c18-145">유지 관리 계획 노드&#40;개체 탐색기&#41;</span><span class="sxs-lookup"><span data-stu-id="41c18-145">Maintenance Plans Node &#40;Object Explorer&#41;</span></span>](../../ssms/object/object-explorer.md)|  
  
  
