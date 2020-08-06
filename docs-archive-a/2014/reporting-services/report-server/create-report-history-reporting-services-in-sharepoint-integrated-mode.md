---
title: 보고서 기록 만들기(SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 996202580bbacc24080460c2c43218db27294d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652577"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="68fdc-102">보고서 기록 만들기(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="68fdc-102">Create Report History (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="68fdc-103">보고서 기록은 시간에 따라 만든 보고서 스냅샷의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="68fdc-104">각 스냅샷은 생성 당시의 상태를 그대로 나타내는 보고서 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-104">Each snapshot is a copy of the report as it existed when it was created.</span></span> <span data-ttu-id="68fdc-105">스냅샷 생성 당시의 보고서 레이아웃 및 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-105">It includes the layout and data that was current for the report when the snapshot was created.</span></span> <span data-ttu-id="68fdc-106">렌더링 정보는 스냅샷에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-106">Rendering information is not stored with the snapshot.</span></span> <span data-ttu-id="68fdc-107">보고서 기록의 스냅샷을 열면 보고서 뷰어 웹 파트에 HTML로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-107">When you open a snapshot in report history, it opens in HTML in the Report Viewer Web Part.</span></span> <span data-ttu-id="68fdc-108">렌더링된 후 스냅숏을 다른 애플리케이션 형식으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-108">After it is rendered, you can export it to other application formats.</span></span>  
  
 <span data-ttu-id="68fdc-109">보고서 기록을 만들려면 보고서가 무인 모드로 실행될 수 있어야 합니다. 즉, 보고서 서버가 사용자와 상호 작용하지 않고 보고서를 실행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-109">To create report history, the report must be able to run unattended (that is, the report server must be able to run the report without user interaction).</span></span> <span data-ttu-id="68fdc-110">해당 보고서가 포함된 라이브러리에 대한 항목 편집 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-110">You must have Edit Items permission on the library that contains the report.</span></span> <span data-ttu-id="68fdc-111">보고서 기록을 보거나 삭제하려면 버전 보기 또는 버전 삭제 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-111">To view or delete report history, you must have View Versions or Delete Versions permissions.</span></span>  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a><span data-ttu-id="68fdc-112">요청 시 스냅샷 또는 보고서 기록을 만들려면</span><span class="sxs-lookup"><span data-stu-id="68fdc-112">To create a snapshot or report history on demand</span></span>  
  
1.  <span data-ttu-id="68fdc-113">보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-113">Point to the report.</span></span>  
  
2.  <span data-ttu-id="68fdc-114">클릭하여 아래쪽 화살표를 표시한 다음 **보고서 기록 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-114">Click to display the down arrow, and then select **View Report History**.</span></span>  
  
3.  <span data-ttu-id="68fdc-115">**새 스냅샷**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-115">Click **New Snapshot**.</span></span> <span data-ttu-id="68fdc-116">단추가 표시되지 않는 경우 보고서 기록에 스냅샷을 만들 수 있는 권한이 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-116">If the button is not visible, it is because you do not have permission to create snapshots in report history.</span></span>  
  
4.  <span data-ttu-id="68fdc-117">방금 만든 스냅샷을 보려면 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-117">To view the snapshot you just created, select it from the list.</span></span> <span data-ttu-id="68fdc-118">각 스냅샷은 스냅샷이 생성된 시기를 보여 주는 타임스탬프로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-118">Each snapshot is identified by a timestamp that shows when the snapshot was created.</span></span> <span data-ttu-id="68fdc-119">스냅샷의 이름을 바꾸거나, 다른 위치로 이동하거나, 수정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-119">You cannot rename the snapshot, move it to another location, or modify it.</span></span>  
  
### <a name="to-schedule-report-history"></a><span data-ttu-id="68fdc-120">보고서 기록을 예약하려면</span><span class="sxs-lookup"><span data-stu-id="68fdc-120">To schedule report history</span></span>  
  
1.  <span data-ttu-id="68fdc-121">보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-121">Point to the report.</span></span>  
  
2.  <span data-ttu-id="68fdc-122">클릭하여 아래쪽 화살표를 표시한 다음 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-122">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="68fdc-123">**기록 스냅샷 옵션**에서 **일정에 따라 보고서 기록 스냅샷 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-123">In **History Snapshot Options**, click **Create report history snapshots on a schedule**.</span></span>  
  
4.  <span data-ttu-id="68fdc-124">사용할 일정 정보가 포함된 공유 일정이 있는 경우 **공유 일정** 을 클릭하고 사용할 일정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-124">If you have a shared schedule that contains the schedule information you want to use, click **On a shared schedule** and select the schedule you want to use.</span></span> <span data-ttu-id="68fdc-125">또는 **사용자 지정 일정**, **구성** 을 차례로 클릭하여 되풀이 일정으로 보고서 기록을 만드는 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-125">Otherwise, click **On a custom schedule**, and then click **Configure** to specify options to create report history on a recurring schedule.</span></span>  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a><span data-ttu-id="68fdc-126">보고서에서 데이터를 새로 고칠 때 보고서 기록을 만들려면</span><span class="sxs-lookup"><span data-stu-id="68fdc-126">To create report history when data is refreshed in a report</span></span>  
  
1.  <span data-ttu-id="68fdc-127">보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-127">Point to the report.</span></span>  
  
2.  <span data-ttu-id="68fdc-128">클릭하여 아래쪽 화살표를 표시한 다음 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-128">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="68fdc-129">**기록 스냅샷 옵션**에서 **보고서 기록에 모든 보고서 데이터 스냅샷 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68fdc-129">In **History Snapshot Options**, click **Store all report data snapshots in report history**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fdc-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68fdc-130">See Also</span></span>  
 [<span data-ttu-id="68fdc-131">처리 옵션 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="68fdc-131">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
