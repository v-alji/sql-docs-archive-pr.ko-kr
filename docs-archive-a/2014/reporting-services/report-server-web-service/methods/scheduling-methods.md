---
title: 일정 예약 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 735da4f22d523fd40dd031f55e203fa9a4204f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647425"
---
# <a name="scheduling-methods"></a><span data-ttu-id="ce8fa-102">일정 예약 메서드</span><span class="sxs-lookup"><span data-stu-id="ce8fa-102">Scheduling Methods</span></span>
  <span data-ttu-id="ce8fa-103">이러한 메서드는 보고서 실행 및 전달을 위한 공유 일정을 만들고 관리하는 데 사용할 수 있으며 보고서 서버에서 사용하는 캐시 새로 고침 계획에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-103">You can use these methods to create and manage shared schedules for report execution and delivery, and to cache refresh plans utilized by the report server.</span></span>  
  
|<span data-ttu-id="ce8fa-104">방법</span><span class="sxs-lookup"><span data-stu-id="ce8fa-104">Method</span></span>|<span data-ttu-id="ce8fa-105">작업</span><span class="sxs-lookup"><span data-stu-id="ce8fa-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|<span data-ttu-id="ce8fa-106">항목에 대한 캐시 새로 고침 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-106">Creates a cache refresh plan for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|<span data-ttu-id="ce8fa-107">새 공유 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-107">Creates a new shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|<span data-ttu-id="ce8fa-108">캐시 새로 고침 계획을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-108">Deletes a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|<span data-ttu-id="ce8fa-109">특정 일정 ID를 기준으로 공유 일정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-109">Deletes a shared schedule based on a specific schedule ID.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<span data-ttu-id="ce8fa-110">지정된 캐시 새로 고침 계획의 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-110">Returns the properties of the specified cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|<span data-ttu-id="ce8fa-111">공유 일정의 속성 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-111">Returns the values of properties of a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|<span data-ttu-id="ce8fa-112">카탈로그 항목과 연결된 캐시 새로 고침 계획의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-112">Returns a list of the cache refresh plans associated with a catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|<span data-ttu-id="ce8fa-113">공유 일정과 연결된 항목 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-113">Returns a list of items that are associated with a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<span data-ttu-id="ce8fa-114">보고서 서버 또는 SharePoint 사이트의 모든 공유 일정 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-114">Returns a list of all shared schedules at the report server or the SharePoint site.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|<span data-ttu-id="ce8fa-115">지원되는 일정 상태 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-115">Returns a list of supported schedule states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|<span data-ttu-id="ce8fa-116">지정된 일정의 실행을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-116">Pauses the execution of a given schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|<span data-ttu-id="ce8fa-117">일시 중지된 공유 일정을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-117">Resumes a shared schedule that has been paused.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|<span data-ttu-id="ce8fa-118">캐시 새로 고침 계획의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-118">Sets the properties of a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|<span data-ttu-id="ce8fa-119">공유 일정의 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-119">Sets the value of properties of a shared schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce8fa-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce8fa-120">See Also</span></span>  
 <span data-ttu-id="ce8fa-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="ce8fa-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="ce8fa-122">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="ce8fa-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="ce8fa-123">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="ce8fa-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="ce8fa-124">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ce8fa-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
