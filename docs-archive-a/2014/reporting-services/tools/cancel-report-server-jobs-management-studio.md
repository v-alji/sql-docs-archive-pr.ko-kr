---
title: 보고서 서버 작업 취소(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0ef8ada32aab4ac368871da711d0fe63fff7620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737911"
---
# <a name="cancel-report-server-jobs-management-studio"></a><span data-ttu-id="5cae1-102">보고서 서버 작업 취소(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5cae1-102">Cancel Report Server Jobs (Management Studio)</span></span>
  <span data-ttu-id="5cae1-103">**보고서 서버 작업 취소** 대화 상자를 사용하여 진행 중인 보고서를 보거나 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-103">Use the **Cancel Report Server Jobs** dialog box to view or cancel in-progress reports.</span></span> <span data-ttu-id="5cae1-104">이 대화 상자에는 현재 보고서 서버에서 실행 중인 모든 작업이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-104">This dialog box shows all jobs that are currently running on the report server.</span></span> <span data-ttu-id="5cae1-105">현재 처리 중인 작업을 일시 중지하거나 다시 시작할 수는 없지만 완료하는 데 오랜 시간이 걸릴 경우 모든 작업 또는 개별 작업을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-105">Although you cannot pause or restart jobs that are currently processing, you can cancel all jobs or individual jobs if they are taking too long to complete.</span></span>  
  
 <span data-ttu-id="5cae1-106">사용자 작업과 시스템 작업을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-106">You can cancel user jobs and system jobs.</span></span>  
  
-   <span data-ttu-id="5cae1-107">사용자 작업은 개별 사용자가 시작한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-107">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="5cae1-108">여기에는 요청 시 보고서 실행, 보고서 기록 스냅샷 수동 작성, 보고서 실행 스냅샷 수동 작성 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-108">This includes running a report on-demand, manually creating a report history snapshot, or manually creating report execution snapshot.</span></span> <span data-ttu-id="5cae1-109">진행 중인 표준 구독도 사용자 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-109">An in-progress standard subscription is also a user job.</span></span>  
  
-   <span data-ttu-id="5cae1-110">시스템 작업은 보고서 서버에서 시작하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-110">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="5cae1-111">시스템 작업에는 예약된 보고서 처리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-111">System jobs include scheduled report processing.</span></span>  
  
 <span data-ttu-id="5cae1-112">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 열고 보고서 서버에 연결한 다음 **작업**을 마우스 오른쪽 단추로 클릭하고 **모든 작업 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Jobs**, and then click **Cancel All Jobs**.</span></span> <span data-ttu-id="5cae1-113">**작업**을 열고 보고서 서버에서 실행 중인 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 취소**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-113">You can also open **Jobs**, right-click a job that is running on the report server, and select **Cancel Job(s)**.</span></span>  
  
 <span data-ttu-id="5cae1-114">작업을 취소하기 전에 해당 작업의 속성을 보면 작업이 시작된 시점을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-114">Before cancelling a job, you can view its properties to determine when the job started.</span></span> <span data-ttu-id="5cae1-115">자세한 내용은 [작업 속성&#40;Management Studio&#41;](job-properties-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cae1-115">For more information, see [Job Properties &#40;Management Studio&#41;](job-properties-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5cae1-116">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services에서는 이 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-116">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="5cae1-117">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]를 실행하는 경우 페이지가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-117">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="5cae1-118">옵션</span><span class="sxs-lookup"><span data-stu-id="5cae1-118">Options</span></span>  
 <span data-ttu-id="5cae1-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="5cae1-119">**Name**</span></span>  
 <span data-ttu-id="5cae1-120">보고서 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-120">Shows the name of the report.</span></span> <span data-ttu-id="5cae1-121">구독은 설명으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-121">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="5cae1-122">**형식**</span><span class="sxs-lookup"><span data-stu-id="5cae1-122">**Type**</span></span>  
 <span data-ttu-id="5cae1-123">유효한 값은 **사용자** 와 **시스템**입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-123">Valid values are **User** and **System**.</span></span>  
  
 <span data-ttu-id="5cae1-124">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="5cae1-124">**Start Time**</span></span>  
 <span data-ttu-id="5cae1-125">작업이 시작된 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-125">Shows when the job started.</span></span>  
  
 <span data-ttu-id="5cae1-126">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="5cae1-126">**User Name**</span></span>  
 <span data-ttu-id="5cae1-127">사용자가 시작한 작업인 경우 이 열에서 사용자 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-127">For jobs that are initiated by a user, this column shows the name of the user.</span></span>  
  
 <span data-ttu-id="5cae1-128">**상태**</span><span class="sxs-lookup"><span data-stu-id="5cae1-128">**Status**</span></span>  
 <span data-ttu-id="5cae1-129">작업 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-129">Shows the status of the job.</span></span> <span data-ttu-id="5cae1-130">유효한 값은 **신규** 와 **실행 중**입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-130">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="5cae1-131">작업이 시작될 때의 상태는 항상 **새 항목** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-131">Status is always **New** when the job begins.</span></span> <span data-ttu-id="5cae1-132">60초 후에 상태는 **실행 중**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-132">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="5cae1-133">변경 내용을 표시하려면 페이지를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-133">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="5cae1-134">**확인**</span><span class="sxs-lookup"><span data-stu-id="5cae1-134">**OK**</span></span>  
 <span data-ttu-id="5cae1-135">하나의 작업 또는 여러 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-135">Cancel a single job or multiple jobs.</span></span> <span data-ttu-id="5cae1-136">작업은 즉시 취소되며 재개할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-136">The jobs are cancelled immediately and cannot be resumed.</span></span> <span data-ttu-id="5cae1-137">작업을 실수로 취소한 경우 보고서 또는 구독을 다시 요청하여 새 작업을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cae1-137">If you mistakenly cancel a job, you must request the report or subscription again to start a new job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cae1-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cae1-138">See Also</span></span>  
 <span data-ttu-id="5cae1-139">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5cae1-139">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="5cae1-140">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5cae1-140">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="5cae1-141">실행 중인 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="5cae1-141">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
