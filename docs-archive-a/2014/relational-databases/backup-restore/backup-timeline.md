---
title: 백업 시간대 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.POINTINTIMERESTORE.F1
- sql12.swb.backuptimeline.f1
helpviewer_keywords:
- Backup Timeline
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b075f8c9ec32cfe483c64e34e9f9b4e4b6e80e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661194"
---
# <a name="backup-timeline"></a><span data-ttu-id="bbb2a-102">백업 시간대</span><span class="sxs-lookup"><span data-stu-id="bbb2a-102">Backup Timeline</span></span>
  <span data-ttu-id="bbb2a-103">**백업 시간대** 대화 상자를 사용하여 데이터베이스를 지정 시간으로 복원할 백업을 찾고 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-103">Use the **Backup Timeline** dialog box to locate and specify backups to restore a database to a point-in-time.</span></span> <span data-ttu-id="bbb2a-104">**데이터베이스 복원(일반 페이지)** 창에서 **시간대** 를 클릭하여 **백업 시간대** 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-104">The **Backup Timeline** dialog box is accessed by clicking **Timeline** on the **Restore Database (General Page)** pane.</span></span> <span data-ttu-id="bbb2a-105">이 대화 상자에서 데이터베이스에 대해 수행된 복원 작업의 시간대를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-105">This dialog box allows you to view a timeline of the restore operations performed on the database.</span></span>  
  
 <span data-ttu-id="bbb2a-106">데이터베이스 복구 관리자는 해당 시점에 복원하는 데 필요한 백업만 선택되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-106">The Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected.</span></span> <span data-ttu-id="bbb2a-107">이러한 선택된 백업은 복원 작업에 필요한 권장 복원 계획을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-107">These selected backups make up the recommended restore plan for your restore operation.</span></span> <span data-ttu-id="bbb2a-108">선택된 백업만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-108">You should use only the selected backups.</span></span> <span data-ttu-id="bbb2a-109">데이터베이스 복구 관리자에 대한 자세한 내용은 [복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-109">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
## <a name="restore-to"></a><span data-ttu-id="bbb2a-110">복원 위치</span><span class="sxs-lookup"><span data-stu-id="bbb2a-110">Restore to</span></span>  
 <span data-ttu-id="bbb2a-111">**수행한 마지막 백업** 은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-111">**Last backup taken** is selected by default.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bbb2a-112">에서는 데이터베이스를 복원하는 데 적절한 백업을 선택하고 데이터베이스를 마지막 백업 시점으로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-112">will select the appropriate backups to restore the database, and will restore the database to the point of the last backup.</span></span> <span data-ttu-id="bbb2a-113">특정 지정 시간을 선택하여 날짜와 시간을 수동으로 설정하려면 **특정 날짜 및 시간** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-113">Click **A specific date and time** to manually set the date and time (selecting a specific point in time).</span></span>  
  
 <span data-ttu-id="bbb2a-114">**특정 날짜 및 시간** 을 사용하여 선택한 날짜와 시간에서 복원을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-114">**Specific date and time** permits you stop the restore at a specific date and time that you select.</span></span> <span data-ttu-id="bbb2a-115">시간대에는 선택한 날짜 및 시간을 기준으로 24시간 이내에 수행된 백업 작업이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-115">The timeline shows a representation of the backup operations performed in the 24 hours around the select date and time.</span></span>  
  
 <span data-ttu-id="bbb2a-116">**Date**</span><span class="sxs-lookup"><span data-stu-id="bbb2a-116">**Date**</span></span>  
 <span data-ttu-id="bbb2a-117">날짜를 입력하거나 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-117">Enter or select a date from the drop-down list.</span></span>  
  
 <span data-ttu-id="bbb2a-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="bbb2a-118">**Time**</span></span>  
 <span data-ttu-id="bbb2a-119">날짜를 입력하거나 선택하여 복원을 중지할 특정 시점을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-119">Enter or select a date to designate the specific point-in-time for the restore to stop.</span></span>  
  
 <span data-ttu-id="bbb2a-120">**일정 기간**</span><span class="sxs-lookup"><span data-stu-id="bbb2a-120">**Timeline Interval**</span></span>  
 <span data-ttu-id="bbb2a-121">시간대에 표시할 수 있는 간격 유형 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-121">Displays the options for the interval types viewable on the timeline.</span></span>  
  
## <a name="timeline-and-legend"></a><span data-ttu-id="bbb2a-122">시간대 및 범례</span><span class="sxs-lookup"><span data-stu-id="bbb2a-122">Timeline and Legend</span></span>  
 <span data-ttu-id="bbb2a-123">시간대 아래에 있는 스크롤 막대를 사용하여 시간대를 따라 커서를 앞이나 뒤로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-123">Use the scroll bar beneath the timeline to move the cursor forward and backward along the timeline.</span></span> <span data-ttu-id="bbb2a-124">백업을 클릭하여 스크롤 막대를 백업의 끝으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-124">Click on a backup to move the scroll bar to the end of that backup.</span></span> <span data-ttu-id="bbb2a-125">마우스를 표식 위로 이동하면 선택한 백업 세트에 대한 정보를 제공하는 화면 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-125">Hover the mouse over a marker to display a ScreenTip providing information about the selected backup set.</span></span> <span data-ttu-id="bbb2a-126">다음 표식은 시간대에 백업 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-126">Backup information is shown on the timeline by the following markers.</span></span>  
  
 <span data-ttu-id="bbb2a-127">큰 삼각형</span><span class="sxs-lookup"><span data-stu-id="bbb2a-127">Larger triangle</span></span>  
 <span data-ttu-id="bbb2a-128">데이터베이스에 대해 수행된 전체 백업을 나타내며 각 전체 백업이 수행된 특정 지정 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-128">Represents the full backups performed on the database, denoting the specific point in time each full backup was performed.</span></span>  
  
 <span data-ttu-id="bbb2a-129">작은 삼각형</span><span class="sxs-lookup"><span data-stu-id="bbb2a-129">Smaller triangle</span></span>  
 <span data-ttu-id="bbb2a-130">데이터베이스에 대해 수행된 차등 백업을 나타내며 각 차등 백업이 수행된 특정 지정 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-130">Represents the differential backups performed on the database, denoting the specific point in time that each differential backup was performed.</span></span>  
  
 <span data-ttu-id="bbb2a-131">녹색 음영 영역</span><span class="sxs-lookup"><span data-stu-id="bbb2a-131">Green shaded areas</span></span>  
 <span data-ttu-id="bbb2a-132">트랜잭션 로그 백업의 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-132">Represents the transaction log backup coverage.</span></span>  
  
 <span data-ttu-id="bbb2a-133">빨강 선</span><span class="sxs-lookup"><span data-stu-id="bbb2a-133">Red line</span></span>  
 <span data-ttu-id="bbb2a-134">시간대에서 복원이 가능한 지점에만 놓일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-134">Can only be positioned along the timeline where the restore is possible.</span></span> <span data-ttu-id="bbb2a-135">시간대를 따라 빨강 선을 이동하면 **날짜** 및 **시간** 상자에 표시되는 날짜와 시간이 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbb2a-135">Moving the red line along the timeline adjusts the date and time displayed in the **Date** and **Time** boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb2a-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbb2a-136">See Also</span></span>  
 [<span data-ttu-id="bbb2a-137">데이터베이스 복원&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="bbb2a-137">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
