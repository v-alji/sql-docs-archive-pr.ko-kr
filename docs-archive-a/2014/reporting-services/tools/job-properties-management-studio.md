---
title: 작업 속성(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4d309ba78a21114cf51c48f0a5c5b3b2f7c2500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732347"
---
# <a name="job-properties-management-studio"></a><span data-ttu-id="602ae-102">작업 속성(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="602ae-102">Job Properties (Management Studio)</span></span>
  <span data-ttu-id="602ae-103">**작업 속성** 페이지를 사용하여 진행 중인 보고서 또는 구독을 취소하기 전에 이에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-103">Use the **Job Properties** page to view information about an in-progress report or subscription before you cancel it.</span></span>  
  
 <span data-ttu-id="602ae-104">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버에 연결한 다음 **작업** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, and open the **Jobs** folder.</span></span> <span data-ttu-id="602ae-105">실행 중인 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-105">Right-click a job that is running, and then click **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="602ae-106">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services에서는 이 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-106">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="602ae-107">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]를 실행하는 경우 페이지가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-107">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="602ae-108">작업</span><span class="sxs-lookup"><span data-stu-id="602ae-108">Tasks</span></span>  
 <span data-ttu-id="602ae-109">작업에 대한 정보를 보려면 페이지를 새로 고쳐 현재 보고서 서버에서 실행 중인 작업에 대한 정보를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-109">Before you can view information about a job, refresh the page to retrieve information about jobs that are currently running on the report server:</span></span>  
  
1.  <span data-ttu-id="602ae-110">보고서 서버 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-110">Open the report server folder.</span></span>  
  
2.  <span data-ttu-id="602ae-111">**작업**을 마우스 오른쪽 단추로 클릭한 다음 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-111">Right-click **Jobs**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="602ae-112">작업이 표시되면 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-112">If a job is listed, right-click the job, and then click **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="602ae-113">옵션</span><span class="sxs-lookup"><span data-stu-id="602ae-113">Options</span></span>  
 <span data-ttu-id="602ae-114">**작업 ID**</span><span class="sxs-lookup"><span data-stu-id="602ae-114">**Job ID**</span></span>  
 <span data-ttu-id="602ae-115">작업이 처리되는 중에 작업에 할당된 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-115">A GUID that is assigned to a job while it is processing.</span></span> <span data-ttu-id="602ae-116">이 값은 보고서 또는 구독이 실행될 때마다 임의로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-116">The value is randomly generated each time a report or subscription runs.</span></span>  
  
 <span data-ttu-id="602ae-117">**작업 상태**</span><span class="sxs-lookup"><span data-stu-id="602ae-117">**Job Status**</span></span>  
 <span data-ttu-id="602ae-118">유효한 값은 **신규** 와 **실행 중**입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-118">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="602ae-119">작업이 시작될 때의 상태는 항상 **새 항목** 입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-119">Status is always **New** when the job begins.</span></span> <span data-ttu-id="602ae-120">60초 후에 상태는 **실행 중**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-120">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="602ae-121">변경 내용을 표시하려면 페이지를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-121">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="602ae-122">**작업 유형**</span><span class="sxs-lookup"><span data-stu-id="602ae-122">**Job Type**</span></span>  
 <span data-ttu-id="602ae-123">유효한 값은 **사용자** 와 **시스템**입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-123">Valid values are **User** and **System**.</span></span> <span data-ttu-id="602ae-124">사용자 작업은 개별 사용자가 시작한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-124">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="602ae-125">여기에는 요청 시 보고서 실행, 보고서 기록 스냅샷 수동 생성, 보고서 실행 스냅샷 수동 생성 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-125">This includes running a report on-demand, manually generating a report history snapshot, or manually creating a report execution snapshot.</span></span> <span data-ttu-id="602ae-126">진행 중인 표준 구독도 사용자 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-126">An in-progress standard subscription is also a user job.</span></span> <span data-ttu-id="602ae-127">시스템 작업은 보고서 서버에서 시작하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-127">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="602ae-128">시스템 작업에는 예약에 따라 트리거되는 보고서 처리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-128">System jobs include report processing that is triggered by a schedule.</span></span>  
  
 <span data-ttu-id="602ae-129">**작업 동작**</span><span class="sxs-lookup"><span data-stu-id="602ae-129">**Job Action**</span></span>  
 <span data-ttu-id="602ae-130">보고서의 경우 이 열에서 진행 중인 보고서 실행 프로세스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-130">For reports, this column shows which report execution processes are underway.</span></span> <span data-ttu-id="602ae-131">이 값은 항상 **렌더링**입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-131">This value is always **Render**.</span></span>  
  
 <span data-ttu-id="602ae-132">**작업 설명**</span><span class="sxs-lookup"><span data-stu-id="602ae-132">**Job Description**</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="602ae-133">에서는 기본적으로 작업 설명이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-133">does not provide job descriptions by default.</span></span>  
  
 <span data-ttu-id="602ae-134">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="602ae-134">**Server Name**</span></span>  
 <span data-ttu-id="602ae-135">작업을 처리 중인 보고서 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-135">Shows the name of the report server that is processing the job.</span></span> <span data-ttu-id="602ae-136">스케일 아웃 배포를 구성한 경우 이 값은 작업을 처리 중인 서버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-136">If you configured a scale-out deployment, this value will show which server is processing the job.</span></span>  
  
 <span data-ttu-id="602ae-137">**보고서 이름**</span><span class="sxs-lookup"><span data-stu-id="602ae-137">**Report Name**</span></span>  
 <span data-ttu-id="602ae-138">보고서 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-138">Shows the name of the report.</span></span> <span data-ttu-id="602ae-139">구독은 설명으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-139">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="602ae-140">**보고서 경로**</span><span class="sxs-lookup"><span data-stu-id="602ae-140">**Report Path**</span></span>  
 <span data-ttu-id="602ae-141">보고서 서버 폴더 계층에 있는 보고서의 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-141">Shows the path of the report in the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="602ae-142">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="602ae-142">**Start Time**</span></span>  
 <span data-ttu-id="602ae-143">프로세스를 시작한 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-143">Shows when the process started.</span></span>  
  
 <span data-ttu-id="602ae-144">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="602ae-144">**User Name**</span></span>  
 <span data-ttu-id="602ae-145">사용자가 시작한 프로세스인 경우 이 열에서 사용자 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-145">For processes initiated by a user, this column shows the name of the user.</span></span> <span data-ttu-id="602ae-146">시스템 작업의 경우 보고서 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="602ae-146">For system jobs, this is the name of the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602ae-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="602ae-147">See Also</span></span>  
 <span data-ttu-id="602ae-148">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="602ae-148">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="602ae-149">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="602ae-149">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="602ae-150">실행 중인 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="602ae-150">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
