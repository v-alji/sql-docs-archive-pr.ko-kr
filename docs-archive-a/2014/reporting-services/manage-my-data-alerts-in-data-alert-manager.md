---
title: 데이터 경고 관리자에서 내 데이터 경고 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 371c62c2f97334e20280a659c8039ab20852ccfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736124"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a><span data-ttu-id="e4194-102">데이터 경고 관리자에서 내 데이터 경고 관리</span><span class="sxs-lookup"><span data-stu-id="e4194-102">Manage My Data Alerts in Data Alert Manager</span></span>
  <span data-ttu-id="e4194-103">SharePoint 사용자는 자신이 만든 데이터 경고 목록과 경고에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-103">SharePoint users can view a list of the data alerts that they created and information about the alerts.</span></span> <span data-ttu-id="e4194-104">또한 자신의 경고를 삭제하고, 데이터 경고 디자이너에서 편집할 경고 정의를 열고, 자신의 경고를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-104">Users can also delete their alerts, open alert definitions for edit in Data Alert Designer, and run their alerts.</span></span> <span data-ttu-id="e4194-105">다음 그림에서는 데이터 경고 관리자에서 사용자에게 제공되는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-105">The following picture shows the features available to users in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="e4194-106">![SharePoint 사용자용 경고 관리자 기능](media/rs-alertmanageriw.gif "SharePoint 사용자용 경고 관리자 기능")</span><span class="sxs-lookup"><span data-stu-id="e4194-106">![Alert Manager features for SharePoint users](media/rs-alertmanageriw.gif "Alert Manager features for SharePoint users")</span></span>  
  
### <a name="to-view-a-list-of-your-alerts"></a><span data-ttu-id="e4194-107">자신의 경고 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="e4194-107">To view a list of your alerts</span></span>  
  
1.  <span data-ttu-id="e4194-108">데이터 경고를 만든 보고서를 저장한 SharePoint 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-108">Go to the SharePoint library where you saved the reports on which you created data alerts.</span></span>  
  
2.  <span data-ttu-id="e4194-109">보고서에서 확장 드롭다운 메뉴 아이콘을 클릭하고 **데이터 경고 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-109">Click the icon for the expand drop-down menu on a report and click **Manage Data Alerts**.</span></span> <span data-ttu-id="e4194-110">다음 그림에서는 드롭다운 메뉴를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-110">The following picture shows the drop-down menu.</span></span>  
  
     <span data-ttu-id="e4194-111">![보고서 상황에 맞는 메뉴에서 경고 관리자 열기](media/rs-openalertmanager.gif "보고서 상황에 맞는 메뉴에서 경고 관리자 열기")</span><span class="sxs-lookup"><span data-stu-id="e4194-111">![Open Alert Manager from report context menu](media/rs-openalertmanager.gif "Open Alert Manager from report context menu")</span></span>  
  
     <span data-ttu-id="e4194-112">데이터 경고 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-112">Data Alert Manager opens.</span></span> <span data-ttu-id="e4194-113">기본적으로 라이브러리에서 선택된 보고서에 대한 경고가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-113">By default, it lists the alerts for the report that you selected in the library.</span></span>  
  
3.  <span data-ttu-id="e4194-114">**보고서 경고 보기** 목록 옆에서 아래쪽 화살표를 클릭하고 경고를 볼 보고서를 선택하거나 **모두 표시** 를 클릭하여 모든 경고를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-114">Click the down arrow next to the **View alerts for report** list and select a report to view its alerts, or click **Show All** to list all alerts.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4194-115">선택한 보고서에 경고가 없으면 경고가 있는 보고서를 찾아 선택하기 위해 SharePoint 라이브러리로 돌아가지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-115">If the report that you selected does not have any alerts, you do not have to return to the SharePoint library to locate and select a report that hasalerts.</span></span> <span data-ttu-id="e4194-116">대신, **모두 표시** 를 클릭하여 모든 경고 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-116">Instead, click **Show All** to see a list of all your alerts.</span></span>  
  
     <span data-ttu-id="e4194-117">테이블에 경고 이름, 보고서 이름, 경고를 만든 자신의 사용자 이름, 경고가 전송된 횟수, 경고 정의가 마지막으로 수정된 시간, 경고 상태가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-117">A table lists the alert name, report name, your name as the creator of the alert, the number the alert was sent, the last time the alert definition was modified, and the status of the alert.</span></span> <span data-ttu-id="e4194-118">경고를 생성하거나 보낼 수 없으면 상태 열에 오류에 대한 정보가 포함되어 문제를 해결하도록 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-118">If the alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-edit-an-alert-definition"></a><span data-ttu-id="e4194-119">경고 정의를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="e4194-119">To edit an alert definition</span></span>  
  
-   <span data-ttu-id="e4194-120">경고 정의를 편집할 데이터 경고를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-120">Right-click the data alert for which you want to edit the alert definition and click **Edit**.</span></span>  
  
     <span data-ttu-id="e4194-121">경고 정의가 데이터 경고 디자이너에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-121">The alert definition opens in Data Alert Designer.</span></span> <span data-ttu-id="e4194-122">자세한 내용은 [경고 디자이너에서 데이터 경고 편집](edit-a-data-alert-in-alert-designer.md) 및 [데이터 경고 디자이너](../../2014/reporting-services/data-alert-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4194-122">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md) and [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4194-123">데이터 경고 정의를 만든 사용자만 해당 정의를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-123">Only the user that created the data alert definition can edit it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4194-124">보고서가 변경되고 보고서에서 생성된 데이터 피드가 변경된 경우 경고 정의가 더 이상 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-124">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="e4194-125">이러한 예로는 해당 규칙에서 경고가 참조하는 열이 보고서에서 삭제되었거나, 데이터 형식을 변경하거나, 다른 데이터 피드에 포함되는 경우 또는 보고서가 삭제 또는 이동되는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-125">This occurs when a column that the alert references in its rules is deleted from the report, changes data type, or is included in a different data feed or the report is deleted or moved.</span></span> <span data-ttu-id="e4194-126">유효하지 않은 경고 정의를 열 수는 있지만 정의를 작성할 때 사용한 보고서 데이터 피드의 현재 버전을 기준으로 유효한 경고 정의만 다시 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-126">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="e4194-127">보고서에서 데이터 피드를 생성하는 방법은 [보고서에서 데이터 피드 생성&#40;보고서 작성기 및 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4194-127">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="e4194-128">경고 정의를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="e4194-128">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="e4194-129">삭제할 데이터 경고를 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-129">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
     <span data-ttu-id="e4194-130">경고를 삭제하면 더 이상 경고 메시지가 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-130">When you delete the alert, no further alert messages are sent.</span></span>  
  
### <a name="to-run-an-alert"></a><span data-ttu-id="e4194-131">경고를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="e4194-131">To run an alert</span></span>  
  
-   <span data-ttu-id="e4194-132">실행할 데이터 경고를 마우스 오른쪽 단추로 클릭하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-132">Right-click the data alert that you want to run and click **Run**.</span></span>  
  
     <span data-ttu-id="e4194-133">데이터 경고 디자이너에서 지정한 일정 옵션에 관계없이 경고 인스턴스가 생성되고 데이터 경고 메시지가 즉시 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-133">The alert instance is created and the data alert message is immediately sent, regardless of the schedule options you specified in Data Alert Designer.</span></span> <span data-ttu-id="e4194-134">예를 들어 매주, 그리고 결과가 변경된 경우에만 전송되도록 구성된 경고가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4194-134">For example, an alert configured to be sent weekly and then only if the results change is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4194-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4194-135">See Also</span></span>  
 <span data-ttu-id="e4194-136">[경고 담당자를 위한 데이터 경고 관리자](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="e4194-136">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="e4194-137">Reporting Services 데이터 경고</span><span class="sxs-lookup"><span data-stu-id="e4194-137">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
