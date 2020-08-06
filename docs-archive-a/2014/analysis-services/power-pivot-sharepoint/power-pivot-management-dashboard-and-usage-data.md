---
title: PowerPivot 관리 대시보드 및 사용 현황 데이터 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581ed571661d54b1cfe9a63224b05f4f8b0267e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651321"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a><span data-ttu-id="9d4aa-102">PowerPivot 관리 대시보드 및 사용량 현황 데이터</span><span class="sxs-lookup"><span data-stu-id="9d4aa-102">PowerPivot Management Dashboard and Usage Data</span></span>
  <span data-ttu-id="9d4aa-103">PowerPivot 관리 대시보드는 SharePoint 중앙 관리의 미리 정의된 보고서 및 웹 파트 컬렉션으로 이를 통해 SharePoint용 SQL Server PowerPivot 배포를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-103">PowerPivot Management Dashboard is a collection of predefined reports and web parts in SharePoint Central Administration that help you administer a SQL Server PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="9d4aa-104">관리 대시보드는 서버 상태, 통합 문서 작업 및 데이터 새로 고침과 관련된 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-104">The Management Dashboard provides information related to server health, workbook activity, and data refresh.</span></span> <span data-ttu-id="9d4aa-105">대시보드는 SharePoint 사용량 현황 데이터 컬렉션의 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-105">The dashboard uses data from the SharePoint usage data collection.</span></span>  
  
 [<span data-ttu-id="9d4aa-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9d4aa-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="9d4aa-107">대시보드 섹션 개요</span><span class="sxs-lookup"><span data-stu-id="9d4aa-107">Overview of the sections of the Dashboard</span></span>](#items)  
  
 [<span data-ttu-id="9d4aa-108">PowerPivot 관리 대시보드 열기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-108">Open PowerPivot Management Dashboard</span></span>](#open)  
  
 [<span data-ttu-id="9d4aa-109">대시보드의 원본 데이터</span><span class="sxs-lookup"><span data-stu-id="9d4aa-109">Source Data in Dashboards</span></span>](#sourcedata)  
  
 [<span data-ttu-id="9d4aa-110">PowerPivot 대시보드 편집</span><span class="sxs-lookup"><span data-stu-id="9d4aa-110">Edit PowerPivot Dashboard</span></span>](#edit)  
  
 [<span data-ttu-id="9d4aa-111">PowerPivot 관리 대시보드에 대한 사용자 지정 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-111">Create Custom Reports for PowerPivot Management Dashboard</span></span>](#reports)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="9d4aa-112">필수 조건</span><span class="sxs-lookup"><span data-stu-id="9d4aa-112">Prerequisites</span></span>  
 <span data-ttu-id="9d4aa-113">관리하는 PowerPivot 서비스 애플리케이션에 대해 PowerPivot 관리 대시보드를 열려면 서비스 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-113">You must be a service administrator to open PowerPivot Management Dashboard for a PowerPivot service application that you manage.</span></span>  
  
##  <a name="overview-of-the-sections-of-the-dashboard"></a><a name="items"></a> <span data-ttu-id="9d4aa-114">대시보드 섹션 개요</span><span class="sxs-lookup"><span data-stu-id="9d4aa-114">Overview of the sections of the Dashboard</span></span>  
 <span data-ttu-id="9d4aa-115">PowerPivot 관리 대시보드에는 웹 파트 및 특정 정보 카테고리로 드릴다운하는 포함된 보고서가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-115">PowerPivot Management Dashboard contains Web Parts and embedded reports that drill down into specific information categories.</span></span> <span data-ttu-id="9d4aa-116">다음 목록에서는 대시보드의 각 부분에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-116">The following list describes each part of the dashboard:</span></span>  
  
|<span data-ttu-id="9d4aa-117">대시보드</span><span class="sxs-lookup"><span data-stu-id="9d4aa-117">Dashboard</span></span>|<span data-ttu-id="9d4aa-118">Description</span><span class="sxs-lookup"><span data-stu-id="9d4aa-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d4aa-119">인프라 - 서버 상태</span><span class="sxs-lookup"><span data-stu-id="9d4aa-119">Infrastructure - Server Health</span></span>|<span data-ttu-id="9d4aa-120">시간의 경과에 따른 CPU 사용량, 메모리 사용 및 쿼리 응답 시간 추세를 표시하여 시스템 리소스가 최대 용량에서 실행되는지 또는 사용률이 낮은지를 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-120">Shows trends in CPU usage, memory consumption, and query response times over time so that you can assess whether system resources are nearing maximum capacity or are under utilized.</span></span>|  
|<span data-ttu-id="9d4aa-121">작업</span><span class="sxs-lookup"><span data-stu-id="9d4aa-121">Actions</span></span>|<span data-ttu-id="9d4aa-122">현재 서비스 애플리케이션, 서비스 애플리케이션 목록 및 사용 현황 로깅과 같은 중앙 관리의 다른 페이지에 대한 링크가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-122">Contains links to other pages in Central Administration including the current service application, a list of service applications, and usage logging.</span></span>|  
|<span data-ttu-id="9d4aa-123">통합 문서 작업 - 차트</span><span class="sxs-lookup"><span data-stu-id="9d4aa-123">Workbook Activity - Chart</span></span>|<span data-ttu-id="9d4aa-124">데이터 액세스 빈도를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-124">Reports on frequency of data access.</span></span> <span data-ttu-id="9d4aa-125">일별 또는 주별로 PowerPivot 데이터 원본에 대한 연결 빈도를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-125">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="9d4aa-126">통합 문서 작업 - 목록</span><span class="sxs-lookup"><span data-stu-id="9d4aa-126">Workbook Activity - Lists</span></span>|<span data-ttu-id="9d4aa-127">데이터 액세스 빈도를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-127">Reports on frequency of data access.</span></span> <span data-ttu-id="9d4aa-128">일별 또는 주별로 PowerPivot 데이터 원본에 대한 연결 빈도를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-128">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="9d4aa-129">데이터 새로 고침 - 최근 작업</span><span class="sxs-lookup"><span data-stu-id="9d4aa-129">Data Refresh - Recent Activity</span></span>|<span data-ttu-id="9d4aa-130">실행에 실패한 작업을 포함하여 데이터 새로 고침 작업에 대한 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-130">Reports on the status of data refresh jobs, including jobs that failed to run.</span></span> <span data-ttu-id="9d4aa-131">이 보고서는 애플리케이션 수준에서 데이터 새로 고침 작업에 대한 복합 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-131">This report provides a composite view into data refresh operations at the application level.</span></span> <span data-ttu-id="9d4aa-132">관리자는 이를 통해 전체 PowerPivot 서비스 애플리케이션에 정의되어 있는 데이터 새로 고침 작업의 수를 한눈에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-132">Administrators can see at a glance the number of data refresh jobs that are defined for the entire PowerPivot service application.</span></span>|  
|<span data-ttu-id="9d4aa-133">데이터 새로 고침 - 최근 실패</span><span class="sxs-lookup"><span data-stu-id="9d4aa-133">Data Refresh - Recent Failures</span></span>|<span data-ttu-id="9d4aa-134">데이터 새로 고침을 제대로 완료하지 못한 PowerPivot 통합 문서를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-134">Lists the PowerPivot workbooks that did not complete data refresh successfully.</span></span>|  
|<span data-ttu-id="9d4aa-135">보고서</span><span class="sxs-lookup"><span data-stu-id="9d4aa-135">Reports</span></span>|<span data-ttu-id="9d4aa-136">Excel에서 열 수 있는 보고서에 대한 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-136">Contains links to reports that you can open in Excel.</span></span>|  
  
##  <a name="open-powerpivot-management-dashboard"></a><a name="open"></a><span data-ttu-id="9d4aa-137">PowerPivot 관리 대시보드 열기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-137">Open PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="9d4aa-138">대시보드에는 한 번에 하나의 PowerPivot 서비스 애플리케이션에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-138">The dashboard shows information for one PowerPivot service application at a time.</span></span> <span data-ttu-id="9d4aa-139">서로 다른 두 위치에서 관리 대시보드를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-139">You can open the management dashboard from two different locations.</span></span>  
  
### <a name="open-the-dashboard-from-general-application-settings"></a><span data-ttu-id="9d4aa-140">일반 애플리케이션 설정에서 대시보드 열기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-140">Open the dashboard from General Application Settings</span></span>  
  
1.  <span data-ttu-id="9d4aa-141">중앙 관리의 **일반 애플리케이션 설정** 그룹에서 **PowerPivot 관리 대시보드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-141">In Central Administration, in the **General Application Settings** group, click **PowerPivot Management Dashboard**.</span></span>  
  
2.  <span data-ttu-id="9d4aa-142">기본 페이지에서 작업 데이터를 볼 PowerPivot 서비스 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-142">On the main page, select the PowerPivot service application for which you want to view operations data.</span></span>  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a><span data-ttu-id="9d4aa-143">PowerPivot 서비스 애플리케이션에서 대시보드 열기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-143">Open the dashboard from a PowerPivot service application</span></span>  
  
1.  <span data-ttu-id="9d4aa-144">중앙 관리의 **응용 프로그램 관리**에서 **서비스 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-144">In Central Administration, in **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="9d4aa-145">PowerPivot 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-145">Click the name of the PowerPivot service application.</span></span> <span data-ttu-id="9d4aa-146">PowerPivot 관리 대시보드에 현재 서비스 애플리케이션에 대한 작동 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-146">The PowerPivot Management Dashboard displays operational data for the current service application.</span></span>  
  
### <a name="change-the-current-service-application"></a><span data-ttu-id="9d4aa-147">현재 서비스 애플리케이션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-147">Change the current service application.</span></span>  
 <span data-ttu-id="9d4aa-148">관리 대시보드에서 현재 PowerPivot 서비스 애플리케이션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="9d4aa-148">To change current PowerPivot service application in the management dashboard:</span></span>  
  
1.  <span data-ttu-id="9d4aa-149">PowerPivot 관리 대시보드의 맨 위에서 현재 서비스 응용 프로그램의 이름 (예: **기본 Powerpivot 서비스 응용 프로그램**)을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-149">At the top of the PowerPivot management dashboard, note the name of the current service application, for example **Default PowerPivot Service Application**.</span></span>  
  
2.  <span data-ttu-id="9d4aa-150">**동작** 대시보드에서 **서비스 애플리케이션을 나열합니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-150">In the **Actions** dashboard, click **List Service Applications**.</span></span>  
  
3.  <span data-ttu-id="9d4aa-151">관리 대시보드 보고서를 보려는 PowerPivot 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-151">Click the name of the PowerPivot Service application for which you want to see management dashboard reports.</span></span>  
  
##  <a name="source-data-in-dashboards"></a><a name="sourcedata"></a> <span data-ttu-id="9d4aa-152">대시보드의 원본 데이터</span><span class="sxs-lookup"><span data-stu-id="9d4aa-152">Source Data in Dashboards</span></span>  
 <span data-ttu-id="9d4aa-153">대시보드, 보고서 및 웹 파트에는 시스템과 PowerPivot 애플리케이션 데이터베이스에서 데이터를 가져오는 내부 데이터 모델의 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-153">Dashboards, reports and web parts show data from an internal data model that pulls data from the system and PowerPivot application databases.</span></span> <span data-ttu-id="9d4aa-154">내부 데이터 모델은 중앙 관리 사이트에서 호스팅되는 PowerPivot 통합 문서에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-154">The internal data model is embedded in a PowerPivot workbook hosted in the Central Administration site.</span></span> <span data-ttu-id="9d4aa-155">데이터 모델의 구조는 고정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-155">The structure of the data model is fixed.</span></span> <span data-ttu-id="9d4aa-156">PowertPivot 통합 문서를 데이터 원본으로 사용할 수 있지만 데이터 원본을 사용하는 미리 정의된 보고서를 나누는 방식으로 구조를 수정해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-156">Although you can use the PowertPivot workbook as a data source to create new reports, you must not modify the structure in a way that breaks the predefined reports that use it.</span></span>  
  
 <span data-ttu-id="9d4aa-157">데이터 수집 방법에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-157">For more information about how data is collected, see the following:</span></span>  
  
-   [<span data-ttu-id="9d4aa-158">PowerPivot 사용량 현황 데이터 컬렉션</span><span class="sxs-lookup"><span data-stu-id="9d4aa-158">PowerPivot Usage Data Collection</span></span>](power-pivot-usage-data-collection.md)  
  
-   [<span data-ttu-id="9d4aa-159">&#40;SharePoint용 PowerPivot에 대 한 사용 현황 데이터 수집 구성</span><span class="sxs-lookup"><span data-stu-id="9d4aa-159">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 <span data-ttu-id="9d4aa-160">PowerPivot 서버 시스템에 대한 데이터를 캡처하려면 이벤트 메시징, 데이터 새로 고침 기록 및 기타 사용 기록이 각 PowerPivot 서비스 애플리케이션에 대해 설정되어 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-160">To capture data about the PowerPivot server system, verify event messaging, data refresh history, and other usage history is enabled for each PowerPivot service application.</span></span> <span data-ttu-id="9d4aa-161">정상적인 서버 작업 중에 수집된 서버 데이터 및 사용량 현황 데이터는 원본 데이터가 되며 최종적으로 내부 데이터 모델에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-161">The server and usage data gathered during normal server operations is the source data that ends up in the internal data model.</span></span> <span data-ttu-id="9d4aa-162">**참고:** 이벤트나 사용 기록을 해제하면 불완전하거나 오류가 있는 복합 보고서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-162">**Note:** If you turn off events or usage history, the composite reports will be incomplete or erroneous.</span></span>  
  
##  <a name="edit-powerpivot-dashboard"></a><a name="edit"></a><span data-ttu-id="9d4aa-163">PowerPivot 대시보드 편집</span><span class="sxs-lookup"><span data-stu-id="9d4aa-163">Edit PowerPivot Dashboard</span></span>  
 <span data-ttu-id="9d4aa-164">대시보드 개발이나 사용자 지정에 대한 전문 지식이 있는 경우 대시보드를 편집하여 새 웹 파트를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-164">If you have expertise in dashboard development or customization, you can edit the dashboard to include new web parts.</span></span> <span data-ttu-id="9d4aa-165">대시보드에 포함되는 웹 파트의 속성을 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-165">You can also edit the web part properties that are included in the dashboard.</span></span>  
  
##  <a name="create-custom-reports-for-powerpivot-management-dashboard"></a><a name="reports"></a><span data-ttu-id="9d4aa-166">PowerPivot 관리 대시보드에 대 한 사용자 지정 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="9d4aa-166">Create Custom Reports for PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="9d4aa-167">보고를 위해 PowerPivot 사용량 현황 데이터와 기록은 대시보드와 함께 만들어지고 구성되는 내부 PowerPivot 통합 문서에 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-167">For reporting purposes, PowerPivot usage data and history is kept in an internal PowerPivot workbook that is created and configured along with the dashboard.</span></span> <span data-ttu-id="9d4aa-168">기본 보고서에서 필요한 정보를 제공하지 않을 경우 통합 문서를 기반으로 Excel에서 사용자 지정 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-168">If the default reports do not provide the information you require, you can create custom reports in Excel based on the workbook.</span></span> <span data-ttu-id="9d4aa-169">나중에 PowerPivot 솔루션 파일을 업그레이드하거나 제거하더라도 통합 문서와 사용자 지정 보고서는 모두 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-169">Both the workbook and any custom reports that you create will be preserved if you upgrade or uninstall the PowerPivot solution files later.</span></span> <span data-ttu-id="9d4aa-170">통합 문서와 보고서는 중앙 관리 사이트의 PowerPivot 관리 라이브러리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-170">The workbook and reports are stored in the PowerPivot Management library within the Central Administration site.</span></span> <span data-ttu-id="9d4aa-171">이 라이브러리는 기본적으로 표시되지 않지만 사이트 작업의 모든 사이트 콘텐츠 보기 작업을 사용하여 라이브러리를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-171">This library is not visible by default, but you can view the library using the View All Site Content action under Site Actions.</span></span>  
  
 <span data-ttu-id="9d4aa-172">사용자 보고를 시작할 때 PowerPivot 관리 대시보드에서는 원본 통합 문서 연결을 위한 Office 데이터 연결 파일(.odc)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-172">To help you get started with custom reporting, PowerPivot Management Dashboard provides an Office Data Connection (.odc) file to connect to the source workbook.</span></span> <span data-ttu-id="9d4aa-173">예를 들어, .Excel에서 odc 파일을 사용하여 추가 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-173">Dor example, you can use the .odc file in Excel to create additional reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d4aa-174">Excel에서 .odc 파일을 사용하려고 할 때 다음과 같은 오류가 발생하지 않도록 파일을 편집합니다. "데이터 원본을 초기화하지 못했습니다."</span><span class="sxs-lookup"><span data-stu-id="9d4aa-174">Edit the file to avoid the following error when attempting to use the .odc file in Excel: "Initialization of the data source failed".</span></span> <span data-ttu-id="9d4aa-175">자동 생성된 .odc 파일에는 MSOLAP OLE DB 공급자에서 지원하지 않는 매개 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-175">The auto-generated .odc file includes a parameter that are not supported by the MSOLAP OLE DB provider.</span></span> <span data-ttu-id="9d4aa-176">다음 지침에서는 이러한 매개 변수를 제거하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-176">The following instructions provide the workaround for removing the parameters.</span></span>  
  
 <span data-ttu-id="9d4aa-177">중앙 관리에서 PowerPivot 통합 문서를 기반으로 하는 보고서를 작성하려면 팜 또는 서비스 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-177">You must be a farm or service administrator to build reports that are based on the PowerPivot workbook in Central Administration.</span></span>  
  
1.  <span data-ttu-id="9d4aa-178">PowerPivot 관리 대시보드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-178">Open the PowerPivot Management Dashboard.</span></span>  
  
2.  <span data-ttu-id="9d4aa-179">페이지 아래쪽의 **보고서** 섹션으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-179">Scroll to the **Reports** section at the bottom of the page.</span></span>  
  
3.  <span data-ttu-id="9d4aa-180">**PowerPivot 관리 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-180">Click **PowerPivot Management Data**.</span></span>  
  
4.  <span data-ttu-id="9d4aa-181">.odc 파일을 로컬 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-181">Save the .odc file to a local folder.</span></span>  
  
5.  <span data-ttu-id="9d4aa-182">텍스트 편집기에서 .odc 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-182">Open the .odc file in a text editor.</span></span>  
  
6.  <span data-ttu-id="9d4aa-183">`<odc:ConnectionString>` 요소에서 줄의 끝으로 스크롤한 다음 `Embedded Data=False`를 제거하고 `Edit Mode=0`을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-183">In the `<odc:ConnectionString>` element, scroll to the end of the line and remove `Embedded Data=False`, and then remove `Edit Mode=0`.</span></span> <span data-ttu-id="9d4aa-184">문자열의 마지막 문자가 세미콜론인 경우 지금 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-184">If the last character in the string is a semicolon, remove it now.</span></span>  
  
7.  <span data-ttu-id="9d4aa-185">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-185">Save the File.</span></span> <span data-ttu-id="9d4aa-186">나머지 단계는 사용 중인 PowerPivot 및 Excel의 버전에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-186">The remaining steps depend on which version of PowerPivot and Excel you are using.</span></span>  
  
8.  1.  <span data-ttu-id="9d4aa-187">Excel 2013 시작</span><span class="sxs-lookup"><span data-stu-id="9d4aa-187">Start Excel 2013</span></span>  
  
    2.  <span data-ttu-id="9d4aa-188">**PowerPivot** 리본에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-188">In the **PowerPivot** ribbon, click **Manage**.</span></span>  
  
    3.  <span data-ttu-id="9d4aa-189">**외부 데이터 가져오기** 를 클릭하고 **기존 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-189">Click **Get External Data** and then click **Existing connections**.</span></span>  
  
    4.  <span data-ttu-id="9d4aa-190">표시되는 .ODC 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-190">Click the .ODC file if you see it.</span></span> <span data-ttu-id="9d4aa-191">.ODC 파일이 표시되지 않으면 **더 찾아보기** 를 클릭하고 파일 경로에 .odc 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-191">If you do not see the .ODC file, click **Browse for More** and then in the file path, specify the .odc file.</span></span>  
  
    5.  <span data-ttu-id="9d4aa-192">**열기** 클릭</span><span class="sxs-lookup"><span data-stu-id="9d4aa-192">Click **Open**</span></span>  
  
    6.  <span data-ttu-id="9d4aa-193">연결되는지 확인하려면 **연결 테스트** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-193">Click **Test Connection** to verify the connection succeeds.</span></span>  
  
    7.  <span data-ttu-id="9d4aa-194">연결 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-194">Click type a name for the connection and then click **Next**.</span></span>  
  
    8.  <span data-ttu-id="9d4aa-195">MDX 쿼리 지정에서 **디자인** 을 클릭 하 여 mdx 쿼리 디자이너를 열고 작업할 데이터를 조합 합니다. "편집 모드 속성 이름의 형식이 올바르지 않습니다." 라는 **오류 메시지가 표시 되 면** 를 편집 했는지 확인 합니다. ODC 파일.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-195">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with **If you see the error message** "The Edit Mode property name is not formatted correctly.", verify you edits the .ODC file.</span></span>  
  
    9. <span data-ttu-id="9d4aa-196">**확인** 을 클릭 한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-196">Click **OK** and then click **Finish**.</span></span>  
  
    10. <span data-ttu-id="9d4aa-197">PivotTable 또는 PivotChart 보고서를 만들어 Excel에서 데이터를 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-197">Create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
9. 1.  <span data-ttu-id="9d4aa-198">Excel 2010을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-198">Start Excel 2010.</span></span>  
  
    2.  <span data-ttu-id="9d4aa-199">PowerPivot 리본에서 **PowerPivot 창 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-199">On the PowerPivot ribbon, click **Launch PowerPivot Window**.</span></span>  
  
    3.  <span data-ttu-id="9d4aa-200">PowerPivot 창의 디자인 리본에서 **기존 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-200">On the Design ribbon in the PowerPivot window, click **Existing Connections**.</span></span>  
  
    4.  <span data-ttu-id="9d4aa-201">**더 찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-201">Click **Browse for More**.</span></span>  
  
    5.  <span data-ttu-id="9d4aa-202">파일 경로에 .odc 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-202">In the file path, specify the .odc file.</span></span>  
  
    6.  <span data-ttu-id="9d4aa-203">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-203">Click **Open**.</span></span> <span data-ttu-id="9d4aa-204">사용량 현황 데이터가 포함된 PowerPivot 통합 문서에 대한 연결 문자열을 사용하여 테이블 가져오기 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-204">The Table Import Wizard starts, using the connection string to the PowerPivot workbook that contains usage data.</span></span>  
  
    7.  <span data-ttu-id="9d4aa-205">**연결 테스트** 를 클릭하여 액세스 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-205">Click **Test Connection** to verify that you have access.</span></span>  
  
    8.  <span data-ttu-id="9d4aa-206">연결에 대한 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-206">Enter a friendly name for the connection, and then click **Next**.</span></span>  
  
    9. <span data-ttu-id="9d4aa-207">MDX 쿼리 지정에서 **디자인** 을 클릭하여 MDX 쿼리 디자이너를 열고 작업할 데이터를 조합한 다음 Excel에서 데이터를 시각화할 PivotTable 또는 PivotChart 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d4aa-207">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with, and then create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4aa-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d4aa-208">See Also</span></span>  
 <span data-ttu-id="9d4aa-209">[SharePoint 2010를 사용 하 여 PowerPivot 데이터 새로 고침](../powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="9d4aa-209">[PowerPivot Data Refresh with SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 [<span data-ttu-id="9d4aa-210">&#40;SharePoint용 PowerPivot에 대 한 사용 현황 데이터 수집 구성</span><span class="sxs-lookup"><span data-stu-id="9d4aa-210">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
