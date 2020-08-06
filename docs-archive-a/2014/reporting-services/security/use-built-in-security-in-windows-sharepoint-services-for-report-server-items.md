---
title: 보고서 서버 항목에 대해 Windows SharePoint Services의 기본 제공 보안 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
- security [Reporting Services], SharePoint integrated mode
ms.assetid: 9577e88d-c22b-4934-936f-e0f1400cedf5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ac4eb124593b8adac7b9d7ea4de6b1c2d455025b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730080"
---
# <a name="use-built-in-security-in-windows-sharepoint-services-for-report-server-items"></a><span data-ttu-id="7e7d8-102">보고서 서버 항목에 대해 Windows SharePoint Services의 기본 제공 보안 사용</span><span class="sxs-lookup"><span data-stu-id="7e7d8-102">Use Built-in Security in Windows SharePoint Services for Report Server Items</span></span>
  <span data-ttu-id="7e7d8-103">SharePoint는 SharePoint 사이트와 라이브러리에서 보고서 서버 항목에 액세스하는 데 사용할 수 있는 기본 제공 보안 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-103">SharePoint provides built-in security features that you can use to access report server items from SharePoint sites and libraries.</span></span> <span data-ttu-id="7e7d8-104">이미 사용자에게 사이트 및 목록 사용 권한을 할당한 경우 SharePoint와 보고서 서버 간의 통합 설정을 구성하면 즉시 해당 사용자가 보고서 서버 항목과 작업에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-104">If you already assigned site and list permissions to users, those same users will have access to report server items and operations immediately after you configure the integration settings between SharePoint and a report server.</span></span>  
  
## <a name="securable-items"></a><span data-ttu-id="7e7d8-105">보안 개체 항목</span><span class="sxs-lookup"><span data-stu-id="7e7d8-105">Securable Items</span></span>  
 <span data-ttu-id="7e7d8-106">사이트나 라이브러리에 정의된 사용 권한을 사용하여 보고서 서버 항목에 대한 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-106">Permissions that are defined on the site or library can be used to grant access to report server items.</span></span> <span data-ttu-id="7e7d8-107">하지만 개별 항목의 보안을 설정하려는 경우 다음 콘텐츠 형식에 사용 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-107">However, if you want to secure individual items, you can set permissions on the following content types:</span></span>  
  
|<span data-ttu-id="7e7d8-108">파일 형식</span><span class="sxs-lookup"><span data-stu-id="7e7d8-108">File type</span></span>|<span data-ttu-id="7e7d8-109">Description</span><span class="sxs-lookup"><span data-stu-id="7e7d8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e7d8-110">.rdl</span><span class="sxs-lookup"><span data-stu-id="7e7d8-110">.rdl</span></span>|<span data-ttu-id="7e7d8-111">데이터 검색에 사용되는 명령과 보고서 레이아웃을 정의하는 보고서 정의 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-111">A report definition file that defines the report layout and the commands used to retrieve data.</span></span> <span data-ttu-id="7e7d8-112">보고서 정의는 보고서를 처리할 때 데이터 원본 연결 정보를 사용하여 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-112">A report definition uses data source connection information to retrieve data when the report is processed.</span></span> <span data-ttu-id="7e7d8-113">보고서 정의가 보고서 작성기에서 만든 임시 보고서인 경우 렌더링된 보고서에 데이터 탐색 범위를 설정하는 보고서 모델 파일(.smdl)과 보고서가 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-113">If the report definition is an ad hoc report that was created in Report Builder, the report is paired with a report model (.smdl) file that sets the scope on data exploration in the rendered report.</span></span>|  
|<span data-ttu-id="7e7d8-114">.smdl</span><span class="sxs-lookup"><span data-stu-id="7e7d8-114">.smdl</span></span>|<span data-ttu-id="7e7d8-115">데이터 구조와 관계를 설명하는 보고서 모델 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-115">A report model file that describes data structures and how they relate.</span></span> <span data-ttu-id="7e7d8-116">이 파일은 보고서 작성기 보고서를 만들고 실행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-116">It is used to create and run Report Builder reports.</span></span>|  
|<span data-ttu-id="7e7d8-117">.rsds</span><span class="sxs-lookup"><span data-stu-id="7e7d8-117">.rsds</span></span>|<span data-ttu-id="7e7d8-118">외부 데이터 원본에 대한 연결 정보를 지정하는 공유 데이터 원본 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-118">A shared data source file that specifies connection information to an external data source.</span></span> <span data-ttu-id="7e7d8-119">이 파일은 보고서 정의 파일(.rdl) 및 보고서 모델 파일(.smdl)에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-119">It is used by report definitions (.rdl) and report model (.smdl) files.</span></span> <span data-ttu-id="7e7d8-120">보고서 모델은 항상 .rsds 파일을 사용하여 기본 데이터 원본에 대한 연결 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-120">Report models always use .rsds files to get connection information to an underlying data source.</span></span> <span data-ttu-id="7e7d8-121">보고서 정의는 .rsds 파일 또는 보고서의 데이터 원본 속성에 정의된 연결 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-121">Report definitions can use .rsds files, or connection information that is defined in data source properties on the report.</span></span>|  
|<span data-ttu-id="7e7d8-122">.rsc</span><span class="sxs-lookup"><span data-stu-id="7e7d8-122">.rsc</span></span>|<span data-ttu-id="7e7d8-123">보고서 항목 또는 데이터 영역의 레이아웃과 구조를 정의하는 보고서 파트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-123">A report part file that defines the layout and structure of a report item or data region.</span></span> <span data-ttu-id="7e7d8-124">다른 보고서 만든 이가 보고서 파트 갤러리에서 항목을 다시 사용할 수 있도록 보고서 파트를 서버에 게시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-124">It is used to publish the report part to a server so the item can be re-used by other report authors from the Report Part Gallery.</span></span>|  
|<span data-ttu-id="7e7d8-125">.rsd</span><span class="sxs-lookup"><span data-stu-id="7e7d8-125">.rsd</span></span>|<span data-ttu-id="7e7d8-126">데이터 세트에 대한 쿼리 구문과 속성을 정의하는 공유 데이터 세트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-126">A shared dataset file that defines query syntax and properties for a dataset.</span></span> <span data-ttu-id="7e7d8-127">공유 데이터 세트를 보고서 외부에서 공유, 저장, 처리 및 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-127">Shared datasets can be shared, stored, processed, and cached external from a report.</span></span>|  
  
 <span data-ttu-id="7e7d8-128">일정, 구독 및 보고서 기록은 보안 개체 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-128">Schedules, subscriptions, and report history are not securable items.</span></span> <span data-ttu-id="7e7d8-129">사용자가 일정, 구독 및 보고서 기록을 만들거나 사용할 수 있는지 결정하는 사용 권한을 사이트나 라이브러리에 설정할 수 있지만 이러한 항목의 보안을 직접 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-129">You can set permissions on the site or library that determine whether a user can create or use schedules, subscriptions, and report history, but you cannot secure those items directly.</span></span>  
  
 <span data-ttu-id="7e7d8-130">개별 항목의 보안을 설정하려면 라이브러리에서 해당 항목을 선택하고 아래쪽 화살표를 클릭한 다음 **사용 권한 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-130">To secure individual items, select the item in the library, click the down arrow, and select **Manage Permissions**.</span></span> <span data-ttu-id="7e7d8-131">**동작** 메뉴에서 **사용 권한 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-131">In the **Actions** menu, select **Edit Permissions**.</span></span>  
  
## <a name="using-built-in-groups-and-permission-levels-to-access-report-server-items"></a><span data-ttu-id="7e7d8-132">기본 제공 그룹 및 사용 권한 수준을 사용하여 보고서 서버 항목에 액세스</span><span class="sxs-lookup"><span data-stu-id="7e7d8-132">Using built-in groups and permission levels to access report server items</span></span>  
 <span data-ttu-id="7e7d8-133">사용 권한 상속과 표준 SharePoint 그룹을 사용하는 경우 보고서 서버와 SharePoint 인스턴스에서 통합 설정을 구성한 후 즉시 보고서 서버 작업에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-133">When you use permission inheritance and standard SharePoint groups, you can access most report server operations immediately after you configure integration settings on the report server and SharePoint instances.</span></span>  
  
 <span data-ttu-id="7e7d8-134">SharePoint는 SharePoint 사이트의 문서와 페이지에 액세스하는 방법을 결정하는 미리 정의된 사용 권한 수준에 매핑되는 표준 그룹을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-134">SharePoint provides standard groups that map to predefined permission levels that determine how you access documents and pages on a SharePoint site.</span></span> <span data-ttu-id="7e7d8-135">표준 그룹과 기본 사용 권한 수준을 사용 중이며 사용 권한을 상속하도록 사이트가 구성된 경우 다음 방식으로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-135">If you are using standard groups and default permission levels, and your sites are configured to inherit permissions, you can expect to work with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features in the following ways:</span></span>  
  
|<span data-ttu-id="7e7d8-136">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-136">**SharePoint Groups**</span></span>|<span data-ttu-id="7e7d8-137">**사용 권한 수준**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-137">**Permission level**</span></span>|<span data-ttu-id="7e7d8-138">**요약**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-138">**Summary**</span></span>|<span data-ttu-id="7e7d8-139">**보고서 서버 액세스**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-139">**Report Server Access**</span></span>|  
|---------------------------|--------------------------|-----------------|------------------------------|  
|<span data-ttu-id="7e7d8-140">**소유자**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-140">**Owners**</span></span>|<span data-ttu-id="7e7d8-141">모든 권한</span><span class="sxs-lookup"><span data-stu-id="7e7d8-141">Full Control</span></span>|<span data-ttu-id="7e7d8-142">소유자는 보고서 서버 항목 및 작업을 만들고 관리하며 보안을 설정할 수 있는 모든 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-142">Owners have full permissions to create, manage, and secure report server items and operations.</span></span>|<span data-ttu-id="7e7d8-143">사이트 전체 라이브러리에 저장된 모든 보고서 서버 항목에 대한 액세스를 제어하는 사용 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-143">Set permissions that control access to all report server items stored in libraries throughout the site.</span></span> <span data-ttu-id="7e7d8-144">보고서 모델 내의 사용 권한을 설정합니다(모델 항목 보안).</span><span class="sxs-lookup"><span data-stu-id="7e7d8-144">Set permissions within a report model (also referred to as model item security).</span></span> <span data-ttu-id="7e7d8-145">보고서 뷰어 웹 파트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-145">Customize a Report Viewer Web Part.</span></span> <span data-ttu-id="7e7d8-146">라이브러리에 보고서 및 기타 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-146">Add reports and other items to libraries.</span></span> <span data-ttu-id="7e7d8-147">보고서 및 기타 문서에 대한 항목 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-147">Edit item properties for reports and other documents.</span></span> <span data-ttu-id="7e7d8-148">보고서 및 기타 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-148">Delete reports and other items.</span></span> <span data-ttu-id="7e7d8-149">데이터 탐색을 위해 보고서 모델을 사용하는 보고서 등 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-149">View reports, including reports that use report models for data exploration.</span></span> <span data-ttu-id="7e7d8-150">보고서의 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-150">Set parameters on reports.</span></span> <span data-ttu-id="7e7d8-151">보고서의 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-151">Set processing options on a report.</span></span> <span data-ttu-id="7e7d8-152">보고서 모델을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-152">Generate report models.</span></span> <span data-ttu-id="7e7d8-153">보고서 작성기에서 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-153">Create reports in Report Builder.</span></span> <span data-ttu-id="7e7d8-154">공유 데이터 원본을 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-154">Create and manage shared data sources.</span></span> <span data-ttu-id="7e7d8-155">모든 사용자가 소유하는 구독을 만들고 변경 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-155">Create, change, and delete subscriptions that are owned by any user.</span></span> <span data-ttu-id="7e7d8-156">사이트 전체에서 사용되는 공유 일정을 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-156">Create and manage shared schedules used throughout the site.</span></span> <span data-ttu-id="7e7d8-157">보고서 기록을 포함하여 문서 버전을 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-157">Create and manage versions of a document, including report history.</span></span> <span data-ttu-id="7e7d8-158">보고서 정의나 보고서 모델의 원본 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-158">Download the source file for a report definition or a report model.</span></span> <span data-ttu-id="7e7d8-159">보고서 정의, 보고서 모델, 공유 데이터 원본 또는 리소스를 바꿉니다(항목 속성 및 사용 권한 유지).</span><span class="sxs-lookup"><span data-stu-id="7e7d8-159">Replace a report definition, report model, shared data source, or resource (preserving item properties and permissions).</span></span>|  
|<span data-ttu-id="7e7d8-160">**멤버**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-160">**Members**</span></span>|<span data-ttu-id="7e7d8-161">기고</span><span class="sxs-lookup"><span data-stu-id="7e7d8-161">Contribute</span></span>|<span data-ttu-id="7e7d8-162">멤버는 새 항목을 만들고 디자인 도구에서 SharePoint 라이브러리로 항목 보고서와 모델을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-162">Members can create new items and publish items reports and models from design tools to a SharePoint library.</span></span>|<span data-ttu-id="7e7d8-163">라이브러리에 보고서 및 기타 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-163">Add reports and other items to libraries.</span></span> <span data-ttu-id="7e7d8-164">보고서 및 기타 문서에 대한 항목 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-164">Edit item properties for reports and other documents.</span></span> <span data-ttu-id="7e7d8-165">보고서 및 기타 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-165">Delete reports and other items.</span></span> <span data-ttu-id="7e7d8-166">데이터 탐색을 위해 보고서 모델을 사용하는 보고서 등 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-166">View reports, including reports that use report models for data exploration.</span></span> <span data-ttu-id="7e7d8-167">보고서 기록 스냅샷을 비롯한 문서의 이전 버전을 봅니다. 이 경우 보고서 기록이 생성된 보고서를 열 권한이 사용자에게 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-167">View past versions of a document, including report history snapshots (requires that a user also has permission to open the report for which report history was created).</span></span> <span data-ttu-id="7e7d8-168">보고서의 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-168">Set parameters on reports.</span></span> <span data-ttu-id="7e7d8-169">보고서의 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-169">Set processing options on a report.</span></span> <span data-ttu-id="7e7d8-170">보고서 모델을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-170">Generate report models.</span></span> <span data-ttu-id="7e7d8-171">보고서 작성기에서 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-171">Create reports in Report Builder.</span></span> <span data-ttu-id="7e7d8-172">공유 데이터 원본을 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-172">Create and manage shared data sources.</span></span> <span data-ttu-id="7e7d8-173">해당 사용자가 소유하는 구독을 만들고 변경 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-173">Create, change, and delete subscriptions that are owned by the user.</span></span> <span data-ttu-id="7e7d8-174">구독에 공유 일정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-174">Use shared schedules with a subscription.</span></span> <span data-ttu-id="7e7d8-175">보고서 기록을 포함하여 문서 버전을 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-175">Create and manage versions of a document, including report history.</span></span> <span data-ttu-id="7e7d8-176">보고서 정의나 보고서 모델의 원본 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-176">Download the source file for a report definition or a report model.</span></span> <span data-ttu-id="7e7d8-177">보고서 정의, 보고서 모델, 공유 데이터 원본 또는 리소스를 바꿉니다(항목 속성 및 사용 권한 유지).</span><span class="sxs-lookup"><span data-stu-id="7e7d8-177">Replace a report definition, report model, shared data source, or resource (preserving item properties and permissions).</span></span>|  
|<span data-ttu-id="7e7d8-178">**방문자** 및 **뷰어**</span><span class="sxs-lookup"><span data-stu-id="7e7d8-178">**Visitors** and **Viewers**</span></span>|<span data-ttu-id="7e7d8-179">읽기</span><span class="sxs-lookup"><span data-stu-id="7e7d8-179">Read</span></span>|<span data-ttu-id="7e7d8-180">방문자는 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-180">Visitors can view reports</span></span>|<span data-ttu-id="7e7d8-181">데이터 탐색을 위해 보고서 모델을 사용하는 보고서 등 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-181">View reports, including reports that use report models for data exploration.</span></span>|  
  
 <span data-ttu-id="7e7d8-182">기본 제공 그룹과 사용 권한 수준을 사용하지 않는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능에 액세스하려면 특정 사용 권한을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-182">If you are not using the built-in groups and permission levels, you must include specific permissions in order to access [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="7e7d8-183">자세한 내용은 [SharePoint 웹 애플리케이션에서 보고서 서버 작업에 대한 사용 권한 설정](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e7d8-183">For more information, see [Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7d8-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e7d8-184">See Also</span></span>  
 <span data-ttu-id="7e7d8-185">[SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="7e7d8-185">[Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="7e7d8-186">[Reporting Services의 역할 및 태스크와 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="7e7d8-186">[Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span></span>  
 <span data-ttu-id="7e7d8-187">[SharePoint 웹 애플리케이션에서 보고서 서버 작업에 대한 사용 권한 설정](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span><span class="sxs-lookup"><span data-stu-id="7e7d8-187">[Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span></span>  
 [<span data-ttu-id="7e7d8-188">SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="7e7d8-188">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  