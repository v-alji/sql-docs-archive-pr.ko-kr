---
title: PowerShell을 사용 하 여 구독 소유자를 변경 하 고 Reporting Services 나열 하 고 구독을 실행 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b274dc190d8830a2cf7b55110f15267a00c581e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651463"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a><span data-ttu-id="4f7e1-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span><span class="sxs-lookup"><span data-stu-id="4f7e1-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span></span>
  <span data-ttu-id="4f7e1-103">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 부터 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구독 소유권을 프로그래밍 방식으로 한 사용자에서 다른 사용자에게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-103">Starting with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] you can programmatically transfer the ownership of a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription from one user to another.</span></span> <span data-ttu-id="4f7e1-104">이 항목에서는 구독 소유권을 변경하거나 단순히 나열할 수 있는 여러 가지 Windows PowerShell 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-104">This topic provides several Windows PowerShell scripts you can use to change or simply list subscription ownership.</span></span> <span data-ttu-id="4f7e1-105">각 샘플에는 기본 모드 및 SharePoint 모드에 대한 샘플 구문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-105">Each sample includes sample syntax for both Native mode and SharePoint mode.</span></span> <span data-ttu-id="4f7e1-106">구독 소유자를 변경한 후 구독은 새 소유자의 보안 컨텍스트에서 실행되고, 보고서의 User!UserID 필드에 새 소유자 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-106">After you change the subscription owner, the subscription will then execute in the security context of the new owner, and the User!UserID field in the report will display the value of new owner.</span></span> <span data-ttu-id="4f7e1-107">PowerShell 샘플의 개체 모델에 대한 자세한 내용은 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="4f7e1-107">For more information on the object model the PowerShell samples call, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>

 <span data-ttu-id="4f7e1-108">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="4f7e1-108">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

||
|-|
|<span data-ttu-id="4f7e1-109">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="4f7e1-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="4f7e1-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4f7e1-110">**In this topic:**</span></span>

-   [<span data-ttu-id="4f7e1-111">스크립트 사용 방법</span><span class="sxs-lookup"><span data-stu-id="4f7e1-111">How to use the scripts</span></span>](#bkmk_how_to)

-   [<span data-ttu-id="4f7e1-112">스크립트: 모든 구독의 소유권 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-112">Script: List the ownership of all subscriptions</span></span>](#bkmk_list_ownership_all)

-   [<span data-ttu-id="4f7e1-113">스크립트: 특정 사용자가 소유하는 모든 구독 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-113">Script: List all subscriptions owned by a specific user</span></span>](#bkmk_list_all_one_user)

-   [<span data-ttu-id="4f7e1-114">스크립트: 특정 사용자가 소유하는 모든 구독의 소유권 변경</span><span class="sxs-lookup"><span data-stu-id="4f7e1-114">Script: Change ownership for all subscriptions owned by a specific user</span></span>](#bkmk_change_all)

-   [<span data-ttu-id="4f7e1-115">스크립트: 특정 보고서와 연결된 모든 구독 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-115">Script: List all subscriptions associated with a specific report</span></span>](#bkmk_list_for_1_report)

-   [<span data-ttu-id="4f7e1-116">스크립트: 특정 구독의 소유권 변경</span><span class="sxs-lookup"><span data-stu-id="4f7e1-116">Script: Change ownership of a specific subscription</span></span>](#bkmk_change_all_1_subscription)

-   [<span data-ttu-id="4f7e1-117">스크립트: 단일 구독 실행</span><span class="sxs-lookup"><span data-stu-id="4f7e1-117">Script: Run (fire) a single subscription</span></span>](#bkmk_run_1_subscription)

##  <a name="how-to-use-the-scripts"></a><a name="bkmk_how_to"></a> <span data-ttu-id="4f7e1-118">스크립트 사용 방법</span><span class="sxs-lookup"><span data-stu-id="4f7e1-118">How to use the scripts</span></span>

### <a name="permissions"></a><span data-ttu-id="4f7e1-119">사용 권한</span><span class="sxs-lookup"><span data-stu-id="4f7e1-119">Permissions</span></span>
 <span data-ttu-id="4f7e1-120">이 섹션에서는 기본 모드와 SharePoint 모드 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 각 메서드를 사용하기 위해 필요한 권한 수준을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-120">This section summarizes the permission levels required to use each of the methods for both Native and SharePoint mode [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4f7e1-121">이 항목의 스크립트는 다음 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-121">The scripts in this topic use the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] methods:</span></span>

-   [<span data-ttu-id="4f7e1-122">ReportingService2010.ListSubscriptions 메서드</span><span class="sxs-lookup"><span data-stu-id="4f7e1-122">ReportingService2010.ListSubscriptions Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)

-   [<span data-ttu-id="4f7e1-123">ReportingService2010.ChangeSubscriptionOwner 메서드</span><span class="sxs-lookup"><span data-stu-id="4f7e1-123">ReportingService2010.ChangeSubscriptionOwner Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)

-   [<span data-ttu-id="4f7e1-124">ReportingService2010.ListChildren</span><span class="sxs-lookup"><span data-stu-id="4f7e1-124">ReportingService2010.ListChildren</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)

-   <span data-ttu-id="4f7e1-125">[ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) 메서드는 실행하는 특정 구독을 트리거하기 위해 마지막 스크립트에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-125">The method [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) is only used in the last script to trigger a specific subscription to run.</span></span> <span data-ttu-id="4f7e1-126">해당 스크립트를 사용하지 않으려면 FireEvent 메서드에 대한 권한 요구 사항을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-126">If you do not plan to use that script you can ignore the permission requirements for the FireEvent method.</span></span>

 <span data-ttu-id="4f7e1-127">**기본 모드:**</span><span class="sxs-lookup"><span data-stu-id="4f7e1-127">**Native mode:**</span></span>

-   <span data-ttu-id="4f7e1-128">구독 나열: (HYPERLINK " https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx " 보고서의 readsubscription 및 사용자가 구독 소유자입니다.) 또는 ReadAnySubscription</span><span class="sxs-lookup"><span data-stu-id="4f7e1-128">List Subscriptions: ( HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription on the report AND the user is the subscription owner) OR ReadAnySubscription</span></span>

-   <span data-ttu-id="4f7e1-129">구독 변경: 사용자는 BUILTIN\Administrators 그룹의 구성원여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-129">Change Subscriptions: The user must be a member of the BUILTIN\Administrators group</span></span>

-   <span data-ttu-id="4f7e1-130">자식 나열: 항목의 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="4f7e1-130">List Children: ReadProperties on Item</span></span>

-   <span data-ttu-id="4f7e1-131">이벤트 발생: GenerateEvents(System)</span><span class="sxs-lookup"><span data-stu-id="4f7e1-131">Fire Event: GenerateEvents (System)</span></span>

 <span data-ttu-id="4f7e1-132">**SharePoint 모드:**</span><span class="sxs-lookup"><span data-stu-id="4f7e1-132">**SharePoint mode:**</span></span>

-   <span data-ttu-id="4f7e1-133">구독 나열: ManageAlerts OR (HYPERLINK " https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx " 보고서의 createalerts 및 사용자는 구독 소유자 이며 구독은 정기 구독)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-133">List Subscriptions: ManageAlerts OR ( HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts on the report AND the user is the subscription owner and the subscription is a timed subscription).</span></span>

-   <span data-ttu-id="4f7e1-134">구독 변경: ManageWeb</span><span class="sxs-lookup"><span data-stu-id="4f7e1-134">Change Subscriptions: ManageWeb</span></span>

-   <span data-ttu-id="4f7e1-135">자식 나열: ViewListItems</span><span class="sxs-lookup"><span data-stu-id="4f7e1-135">List Children: ViewListItems</span></span>

-   <span data-ttu-id="4f7e1-136">이벤트 발생: ManageWeb</span><span class="sxs-lookup"><span data-stu-id="4f7e1-136">Fire Event: ManageWeb</span></span>

 <span data-ttu-id="4f7e1-137">자세한 내용은 [Reporting Services의 역할 및 작업과 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-137">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>

### <a name="script-usage"></a><span data-ttu-id="4f7e1-138">스크립트 사용자</span><span class="sxs-lookup"><span data-stu-id="4f7e1-138">Script usage</span></span>
 <span data-ttu-id="4f7e1-139">**스크립트 파일(.ps1) 만들기**</span><span class="sxs-lookup"><span data-stu-id="4f7e1-139">**Create Script files (.ps1)**</span></span>

1.  <span data-ttu-id="4f7e1-140">이름이 **c:\scripts**인 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-140">Create a folder named **c:\scripts**.</span></span> <span data-ttu-id="4f7e1-141">다른 폴더를 선택하는 경우 예제 명령줄 구문에 사용된 폴더 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-141">If you choose a different folder then modify the folder name used in the example command line syntax statements.</span></span>

2.  <span data-ttu-id="4f7e1-142">각 스크립트의 텍스트 파일을 만들고 c:\scripts 폴더에 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-142">Create a text file for each script and save the files to the c:\scripts folder.</span></span> <span data-ttu-id="4f7e1-143">.ps1 파일을 만들 때 각 예제 명령줄 구문의 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-143">When you create the .ps1 files, use the name from each example command line syntax.</span></span>

3.  <span data-ttu-id="4f7e1-144">관리자 권한으로 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-144">Open a command prompt with administrative privileges.</span></span>

4.  <span data-ttu-id="4f7e1-145">각 예제에 제공된 샘플 명령줄 구문을 사용하여 각 스크립트 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-145">Run each script file, using the sample command line syntax provided with each example.</span></span>

 <span data-ttu-id="4f7e1-146">**테스트 완료된 환경**</span><span class="sxs-lookup"><span data-stu-id="4f7e1-146">**Tested environments**</span></span>

 <span data-ttu-id="4f7e1-147">이 항목의 스크립트는 PowerShell 버전 3 및 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 다음 버전에서 테스트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-147">The scripts in this topic were tested on PowerShell version 3 and with the following versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:</span></span>

-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]

##  <a name="script-list-the-ownership-of-all-subscriptions"></a><a name="bkmk_list_ownership_all"></a> <span data-ttu-id="4f7e1-148">스크립트: 모든 구독의 소유권 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-148">Script: List the ownership of all subscriptions</span></span>
 <span data-ttu-id="4f7e1-149">이 스크립트는 사이트의 모든 구독을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-149">This script lists all of the subscriptions on a site.</span></span> <span data-ttu-id="4f7e1-150">이 스크립트를 사용하여 연결을 테스트하거나 다른 스크립트에서 사용하는 보고서 경로 및 구독 ID를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-150">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="4f7e1-151">또한 어떤 구독이 존재하며 누가 소유하는지 간단하게 감사할 수 있는 유용한 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-151">This is also a useful script to simply audit what subscriptions exist and who owns them.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-152">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-152">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-153">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-153">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="4f7e1-154">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-154">Script</span></span>

```powershell
# Parameters
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)

Param(
    [string]$server,
    [string]$site
   )

$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site

Write-Host " "
Write-Host "----- $server's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status
```

> [!TIP]
>  <span data-ttu-id="4f7e1-155">SharePoint 모드에서 사이트 URL을 확인하려면 SharePoint cmdlet **Get-SPSite**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-155">To verify site URLS in SharePoint mode, use the SharePoint cmdlet **Get-SPSite**.</span></span> <span data-ttu-id="4f7e1-156">자세한 내용은 [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-156">For more information, see [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).</span></span>

##  <a name="script-list-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_list_all_one_user"></a> <span data-ttu-id="4f7e1-157">스크립트: 특정 사용자가 소유하는 모든 구독 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-157">Script: List all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="4f7e1-158">이 스크립트는 특정 사용자가 소유하는 모든 구독을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-158">This script lists all of the subscriptions owned by a specific user.</span></span> <span data-ttu-id="4f7e1-159">이 스크립트를 사용하여 연결을 테스트하거나 다른 스크립트에서 사용하는 보고서 경로 및 구독 ID를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-159">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="4f7e1-160">이 스크립트는 조직의 누군가가 떠나고 이들이 소유하고 있던 구독을 확인하여 소유자를 변경하거나 구독을 삭제하려고 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-160">This script is useful when someone in your organization leaves and you want to verify what subscriptions they owned so you can change the owner or delete the subscription.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-161">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-161">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-162">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-162">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="4f7e1-163">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-163">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
Param(
    [string]$currentOwner,
    [string]$server,
    [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $currentOwner's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}
```

##  <a name="script-change-ownership-for-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_change_all"></a> <span data-ttu-id="4f7e1-164">스크립트: 특정 사용자가 소유하는 모든 구독의 소유권 변경</span><span class="sxs-lookup"><span data-stu-id="4f7e1-164">Script: Change ownership for all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="4f7e1-165">이 스크립트는 특정 소유자가 소유하는 모든 구독의 소유권을 새 소유자 매개 변수로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-165">This script changes the ownership for all subscriptions owned by a specific user to the new owner parameter.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-166">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-166">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-167">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-167">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"
```

### <a name="script"></a><span data-ttu-id="4f7e1-168">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-168">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)

Param(
    [string]$currentOwner,
    [string]$newOwner,
    [string]$server
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$items = $rs2010.ListChildren("/", $true);

$subscriptions = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);
        ForEach ($curRepSub in $curRepSubs)
        {
            if ($curRepSub.Owner -eq $currentOwner)
            {
                $subscriptions += $curRepSub;
            }
        }
    }
}

Write-Host " "
Write-Host " "
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize

ForEach ($sub in $subscriptions)
{
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);
}

$subs2 = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $subs2 += $rs2010.ListSubscriptions($item.Path);
    }
}
```

##  <a name="script-list-all-subscriptions-associated-with-a-specific-report"></a><a name="bkmk_list_for_1_report"></a> <span data-ttu-id="4f7e1-169">스크립트: 특정 보고서와 연결된 모든 구독 나열</span><span class="sxs-lookup"><span data-stu-id="4f7e1-169">Script: List all subscriptions associated with a specific report</span></span>
 <span data-ttu-id="4f7e1-170">이 스크립트는 특정 보고서와 연결된 모든 구독을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-170">This script lists all of the subscriptions associated with a specific report.</span></span> <span data-ttu-id="4f7e1-171">보고서 경로 구문은 전체 URL이 필요한 다른 SharePoint 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-171">The report path syntax is different SharePoint mode which requires a full URL.</span></span> <span data-ttu-id="4f7e1-172">구문 예제에서 사용된 보고서 이름은 "title only"이며 공백을 포함하고 있으므로 보고서 이름을 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-172">In the syntax examples, the report name used is "title only", which contains a space and therefore requires the single quotes around the report name.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-173">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-173">Native mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-174">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-174">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="4f7e1-175">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-175">Script</span></span>

```powershell
# Parameters:
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"
#    site        - use "/" for default native mode site
Param
(
      [string]$server,
      [string]$reportpath,
      [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $reportpath 's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}
```

##  <a name="script-change-ownership-of-a-specific-subscription"></a><a name="bkmk_change_all_1_subscription"></a> <span data-ttu-id="4f7e1-176">스크립트: 특정 구독의 소유권 변경</span><span class="sxs-lookup"><span data-stu-id="4f7e1-176">Script: Change ownership of a specific subscription</span></span>
 <span data-ttu-id="4f7e1-177">이 스크립트는 특정 구독의 소유권을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-177">This script changes the ownership for a specific subscription.</span></span> <span data-ttu-id="4f7e1-178">구독은 스크립트에 전달하는 SubscriptionID로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-178">The subscription is identified by the SubscriptionID that you pass into the script.</span></span> <span data-ttu-id="4f7e1-179">구독 나열 스크립트 중 하나를 사용하여 올바른 SubscriptionID를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-179">You can use one of the list subscription scripts to determine the correct SubscriptionID.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-180">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-180">Native mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-181">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-181">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"
```

### <a name="script"></a><span data-ttu-id="4f7e1-182">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-182">Script</span></span>

```powershell
# Parameters:
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
#    subscriptionID - guid for the single subscription to change

Param(
    [string]$newOwner,
    [string]$server,
    [string]$site,
    [string]$subscriptionid
   )
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;

$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};

Write-Host " "
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status

$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)

#refresh the list
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status
```

##  <a name="script-run-fire-a-single-subscription"></a><a name="bkmk_run_1_subscription"></a> <span data-ttu-id="4f7e1-183">스크립트: 단일 구독 실행</span><span class="sxs-lookup"><span data-stu-id="4f7e1-183">Script: Run (fire) a single subscription</span></span>
 <span data-ttu-id="4f7e1-184">이 스크립트는 FireEvent 메서드를 사용하여 특정 구독을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-184">This script will run a specific subscription using the FireEvent method.</span></span> <span data-ttu-id="4f7e1-185">이 스크립트는 구독에 구성된 일정에 상관없이 구독을 즉시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-185">The script will immediately run the subscription regardless of the schedule configured for the subscription.</span></span> <span data-ttu-id="4f7e1-186">EventType은 보고서 서버 구성 파일 **rsreportserver.config** 에 정의된 알려진 이벤트 집합과 일치합니다. 이 스크립트는 표준 구독에 대해 다음 이벤트 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-186">The EventType is matched against the known set of events that are defined in the report server configuration file **rsreportserver.config** The script uses the following event type for standard subscriptions:</span></span>

 `<Event>`

 `<Type>TimedSubscription</Type>`

 `</Event>`

 <span data-ttu-id="4f7e1-187">구성 파일에 대한 자세한 내용은 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-187">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>

 <span data-ttu-id="4f7e1-188">스크립트에는 지연 논리 "`Start-Sleep -s 6`"이 포함되어 있으므로, 업데이트된 상태가 ListSubscription 메서드를 통해 사용 가능할 수 있도록 이벤트 발생 후 시간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f7e1-188">The script includes delay logic "`Start-Sleep -s 6`" so there is time after the event fires, for the updated status to be available with the ListSubscription method.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="4f7e1-189">기본 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-189">Native mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="4f7e1-190">SharePoint 모드 구문</span><span class="sxs-lookup"><span data-stu-id="4f7e1-190">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"
```

### <a name="script"></a><span data-ttu-id="4f7e1-191">스크립트</span><span class="sxs-lookup"><span data-stu-id="4f7e1-191">Script</span></span>

```powershell
# Parameters
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site           - use $null for a native mode server
#    subscriptionid - subscription guid

Param(
  [string]$server,
  [string]$site,
  [string]$subscriptionid
  )

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
#event type is case sensative to what is in the rsreportserver.config
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)

Write-Host " "
Write-Host "----- Subscription ($subscriptionid) status: "
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted
$subscriptions = $rs2010.ListSubscriptions($site); 
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}
```

## <a name="see-also"></a><span data-ttu-id="4f7e1-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f7e1-192">See Also</span></span>
 <span data-ttu-id="4f7e1-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="4f7e1-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span> 
 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>
