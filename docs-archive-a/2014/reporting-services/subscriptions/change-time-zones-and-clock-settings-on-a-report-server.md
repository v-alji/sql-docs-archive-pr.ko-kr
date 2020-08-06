---
title: 보고서 서버에서 표준 시간대 및 시계 설정 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 566e421cd120010ea32f6936853e4319ec2efa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739135"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a><span data-ttu-id="dbff5-102">보고서 서버에서 표준 시간대 및 시계 설정 변경</span><span class="sxs-lookup"><span data-stu-id="dbff5-102">Change Time Zones and Clock Settings on a Report Server</span></span>
  <span data-ttu-id="dbff5-103">보고서 서버는 항상 설치된 컴퓨터의 현지 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-103">A report server always uses the local time of the computer on which it is installed.</span></span> <span data-ttu-id="dbff5-104">다른 표준 시간대를 사용하도록 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-104">You cannot configure it to use a different time zone.</span></span> <span data-ttu-id="dbff5-105">클라이언트 애플리케이션이 다른 표준 시간대의 보고서 서버를 가리키는 경우 해당 보고서 서버의 표준 시간대를 사용하여 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-105">If a client application points to a report server in a different time zone, the report server time zone is used to execute a scheduled operation.</span></span> <span data-ttu-id="dbff5-106">보고서 관리자 및 SharePoint 관리 페이지에서 표준 시간대가 각 일정 페이지에 표시되므로 예약된 작업이 언제 수행되는지 정확히 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-106">In Report Manager and SharePoint management pages, the time zone is indicated on each scheduling page so that you know exactly when a scheduled operation will occur.</span></span> <span data-ttu-id="dbff5-107">예를 들어 사용자 지정 일정을 만들기 위한 페이지에 "시간은 (UTC-08: 00) 태평양 표준시(미국 및 캐나다)로 표시됩니다."라고 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-107">For example, the page for creating custom schedules will note "Times are expressed in (UTC-08:00) Pacific time (US and Canada)."</span></span>  
  
## <a name="changing-the-time-zone-native-mode"></a><span data-ttu-id="dbff5-108">표준 시간대(기본 모드) 변경</span><span class="sxs-lookup"><span data-stu-id="dbff5-108">Changing the Time Zone (Native Mode)</span></span>  
 <span data-ttu-id="dbff5-109">보고서 서버를 호스팅하는 컴퓨터의 표준 시간대를 변경하는 경우 보고서 서버 서비스를 다시 시작해야 표준 시간대의 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-109">If you change the time zone on a computer hosting a report server, you must restart the Report Server service in order for the time zone change to take effect.</span></span>  
  
 <span data-ttu-id="dbff5-110">기존 보고서 기록 스냅샷의 타임스탬프 값은 새 표준 시간대 설정으로 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-110">Timestamp values of existing report history snapshots are synchronized to the new time zone setting.</span></span> <span data-ttu-id="dbff5-111">오전 9시에 보고서 기록 스냅샷을 생성하고 표준 시간대를 1시간 늦춰 다시 설정한 경우 생성된 스냅샷의 타임스탬프는 오전 9시에서</span><span class="sxs-lookup"><span data-stu-id="dbff5-111">If you generated a report history snapshot at 9:00 A.M., and then reset the time zone ahead one time zone, the timestamp on the generated snapshot will change from 9:00 A.M.</span></span> <span data-ttu-id="dbff5-112">오전 10시로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-112">to 10:00 A.M.</span></span>  
  
 <span data-ttu-id="dbff5-113">일정은 새 표준 시간대로 매핑되는 것을 제외하고는 기존 설정을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-113">Schedules retain existing settings, except that they are mapped to the new time zone.</span></span> <span data-ttu-id="dbff5-114">예를 들어 일정이 태평양 표준시로 오전 2시에 실행되는 경우</span><span class="sxs-lookup"><span data-stu-id="dbff5-114">For example, if a schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="dbff5-115">표준 시간대를 동부 오스트레일리아 표준시로 변경하면 일정이 동부 오스트레일리아 표준시로</span><span class="sxs-lookup"><span data-stu-id="dbff5-115">Pacific Standard Time and you change the time zone to East Australia Standard Time, the schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="dbff5-116">오전 2시에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-116">East Australia Standard Time.</span></span>  
  
 <span data-ttu-id="dbff5-117">폴더나 링크된 보고서 항목이 생성되는 시간과 같은 속성 타임스탬프 값은 새 표준 시간대 설정으로 동기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-117">Property timestamp values (for example, the time at which a folder or linked report item is created) are not synchronized to a new time zone setting.</span></span> <span data-ttu-id="dbff5-118">6월 25일 오전 9시에 항목을 만들고 표준 시간대나 시계를 다시 설정해도 해당 타임스탬프는 6월 25일 오전 9시로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-118">If you create an item on June 25 at 9:00 A.M., and then reset the time zone or clock, the timestamp remains June 25 at 9:00 A.M.</span></span>  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a><span data-ttu-id="dbff5-119">표준 시간대(SharePoint 모드) 변경</span><span class="sxs-lookup"><span data-stu-id="dbff5-119">Changing the Time Zone (SharePoint Mode)</span></span>  
 <span data-ttu-id="dbff5-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 위한 표준 시간대 구성은 SharePoint 국가별 설정의 일부로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-120">The time zone configuration for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is managed as part of the SharePoint regional settings.</span></span> <span data-ttu-id="dbff5-121">자세한 내용은 [국가별 설정(SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dbff5-121">For more information, see [Regional settings (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx).</span></span>  
  
## <a name="changing-the-clock-settings"></a><span data-ttu-id="dbff5-122">시계 설정 변경</span><span class="sxs-lookup"><span data-stu-id="dbff5-122">Changing the Clock Settings</span></span>  
 <span data-ttu-id="dbff5-123">컴퓨터 시계를 변경해도 기존 타임스탬프 값에는 영향이 없습니다. 예를 들어 시계를 1시간 앞으로 이동해도 보고서 기록 스냅샷의 타임스탬프는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-123">Changing the computer clock has no effect on existing timestamp values (for example, if you move the clock forward an hour, the timestamps of report history snapshots do not change).</span></span> <span data-ttu-id="dbff5-124">10초 정도 경과 후 일정 예약 및 배달 프로세스에 새 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-124">There may be a delay of 10 seconds before the Scheduling and Delivery Processor uses the new setting.</span></span> <span data-ttu-id="dbff5-125">구성 파일의 폴링 간격 설정을 수정한 경우 실제 지연 시간이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbff5-125">The actual delay may vary if you modified polling interval settings in the configuration files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbff5-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbff5-126">See Also</span></span>  
 <span data-ttu-id="dbff5-127">[보고서 서버 서비스 시작 및 중지](../report-server/start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="dbff5-127">[Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="dbff5-128">일정</span><span class="sxs-lookup"><span data-stu-id="dbff5-128">Schedules</span></span>](schedules.md)  
  
  
