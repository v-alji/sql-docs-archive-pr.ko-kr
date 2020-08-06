---
title: 데이터 경고 관리자에서 SharePoint 사이트의 모든 데이터 경고 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b41fdbd18a0b1b4a7a69a3ca202de1c555c070de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736123"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a><span data-ttu-id="d5439-102">데이터 경고 관리자에서 SharePoint 사이트의 모든 데이터 경고 관리</span><span class="sxs-lookup"><span data-stu-id="d5439-102">Manage All Data Alerts on a SharePoint Site in Data Alert Manager</span></span>
  <span data-ttu-id="d5439-103">SharePoint 경고 관리자는 사이트 사용자가 만든 데이터 경고 목록과 경고에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-103">SharePoint alerting administrators can view a list of the data alerts that were created by any site user and information about the alerts.</span></span> <span data-ttu-id="d5439-104">경고 관리자는 경고를 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-104">Alerting administrators can also delete alerts.</span></span> <span data-ttu-id="d5439-105">다음 그림에서는 데이터 경고 관리자에서 경고 담당자가 사용할 수 있는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-105">The following picture shows the features available to alerting administrators in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="d5439-106">![SharePoint 사이트 관리자용 경고 관리자](media/rs-alertmanagersite.gif "SharePoint 사이트 관리자용 경고 관리자")</span><span class="sxs-lookup"><span data-stu-id="d5439-106">![Alert Manager for SharePoin tsite administrators](media/rs-alertmanagersite.gif "Alert Manager for SharePoin tsite administrators")</span></span>  
  
### <a name="to-view-a-list-of-alerts-created-by-a-site-user"></a><span data-ttu-id="d5439-107">사이트 사용자가 만든 경고 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="d5439-107">To view a list of alerts created by a site user</span></span>  
  
1.  <span data-ttu-id="d5439-108">데이터 경고 정의가 저장된 SharePoint 사이트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-108">Go to the SharePoint site where data alerts definitions are saved.</span></span>  
  
2.  <span data-ttu-id="d5439-109">홈 페이지에서 **사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-109">On the Home page, click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="d5439-110">목록 아래로 스크롤하고 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-110">Scroll to the bottom of the list and click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="d5439-111">**Reporting Services**아래에서 **데이터 경고 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-111">Under **Reporting Services**, click **Manage Data Alerts**.</span></span>  
  
5.  <span data-ttu-id="d5439-112">**사용자 경고 보기** 목록 옆에서 아래쪽 화살표를 클릭하고 보려는 경고를 소유하는 사용자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-112">Click the down arrow by the **View alerts for user** list and select the user whose alerts you want to view.</span></span>  
  
6.  <span data-ttu-id="d5439-113">**보고서 경고 보기** 목록 옆에서 아래쪽 화살표를 클릭하고 보려는 특정 경고를 선택하거나 **모두 표시** 를 클릭하여 선택한 사용자가 만든 모든 경고를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-113">Click the down arrow next to the **View alerts for report** list and select a specific alert to view, or click **Show All** to list all alerts created by the selected user.</span></span>  
  
     <span data-ttu-id="d5439-114">테이블에 이름, 보고서 이름, 데이터 경고를 만든 사용자 이름, 데이터 경고를 보낸 횟수, 데이터 경고 정의가 마지막으로 수정된 시간 및 데이터 경고 상태가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-114">A table lists the name, report name, name of the person who created the data alert, the number times the data alert was sent, the last time the data alert definition was modified, and the status of the data alert.</span></span> <span data-ttu-id="d5439-115">데이터 경고를 생성하거나 보낼 수 없으면 상태 열에 오류에 대한 정보가 포함되어 문제를 해결하도록 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-115">If the data alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="d5439-116">경고 정의를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="d5439-116">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="d5439-117">삭제할 데이터 경고를 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-117">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d5439-118">경고를 삭제하면 더 이상 경고 메시지가 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-118">After you delete the alert, no further alert messages are sent.</span></span> <span data-ttu-id="d5439-119">하지만 경고 데이터베이스를 쿼리하면 경고 정의가 계속 존재하는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-119">However, if you query the alerting database you might find that the alert definition still exists.</span></span> <span data-ttu-id="d5439-120">경고 서비스는 예약에 따라 정리를 수행하며 다음 정리 작업 시 경고 정의가 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-120">The alerting service performs clean up on a schedule and the alert definition is deleted permanently in the next cleanup.</span></span> <span data-ttu-id="d5439-121">기본 정리 간격은 20분입니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-121">The default cleanup interval is 20 minutes.</span></span> <span data-ttu-id="d5439-122">이러한 정리 간격은 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5439-122">This and other cleanup intervals are configurable.</span></span> <span data-ttu-id="d5439-123">자세한 내용은 [Reporting Services 데이터 경고](../ssms/agent/alerts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5439-123">For more information, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5439-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5439-124">See Also</span></span>  
 <span data-ttu-id="d5439-125">[경고 담당자를 위한 데이터 경고 관리자](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="d5439-125">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="d5439-126">Reporting Services 데이터 경고</span><span class="sxs-lookup"><span data-stu-id="d5439-126">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
