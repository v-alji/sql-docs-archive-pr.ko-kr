---
title: 구독 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c67895babe99c92b7c09afd8cb75ca88d5cd7553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734928"
---
# <a name="subscriptions-page-report-manager"></a><span data-ttu-id="8c947-102">구독 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="8c947-102">Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="8c947-103">구독 페이지를 사용하여 현재 보고서나 공유 데이터 원본의 구독을 모두 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-103">Use the Subscriptions page to list all of the subscriptions for the current report or shared data source.</span></span> <span data-ttu-id="8c947-104">모든 구독 태스크 관리가 뜻하는 바와 같이 충분한 권한이 있으면 모든 사용자의 구독을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-104">If you have sufficient permission (as conveyed by the "Manage all subscriptions" task), you can view the subscriptions of all users.</span></span> <span data-ttu-id="8c947-105">그렇지 않으면 이 페이지는 사용자가 소유하는 구독만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-105">Otherwise, this page shows only the subscriptions that you own.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c947-106">다른 페이지에서도 구독 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-106">Other pages also contain subscription information.</span></span> <span data-ttu-id="8c947-107">자세한 내용은 구독을 만들거나 편집 하기 위해 한 곳에서 모든 구독에 액세스 하거나, [새 구독 또는 구독 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) 에서 모든 구독에 액세스 하려면 [내 구독 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c947-107">For more information, see [My Subscriptions Page &#40;Report Manager&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md) to access all your subscriptions in one place or the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) to create or edit a subscription.</span></span>  
  
 <span data-ttu-id="8c947-108">일부 옵션은 작업할 기존 구독이 있는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-108">Some options are visible only if there are existing subscriptions to work with.</span></span> <span data-ttu-id="8c947-109">정의된 구독이 없는 경우 보고서에서 이 페이지를 액세스하면 페이지에 **새 구독** 및 **새 데이터 기반 구독** 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-109">If no subscriptions are defined and you are accessing this page from a report, the **New Subscription** and **New Data-Driven Subscription** are the only options on the page.</span></span>  
  
 <span data-ttu-id="8c947-110">새 구독을 만들기 전에 보고서 데이터 원본에서 저장된 자격 증명을 사용하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-110">Before you can create a new subscription, you must verify that the report data source uses stored credentials.</span></span> <span data-ttu-id="8c947-111">자격 증명을 저장하려면 데이터 원본 속성 페이지를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c947-111">Use the Data Sources properties page to store credentials.</span></span> <span data-ttu-id="8c947-112">자세한 내용은 [데이터 원본 속성 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c947-112">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c947-113">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8c947-114">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c947-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="8c947-115">탐색</span><span class="sxs-lookup"><span data-stu-id="8c947-115">Navigation</span></span>  
 <span data-ttu-id="8c947-116">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c947-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-subscriptions-page-for-report"></a><span data-ttu-id="8c947-117">보고서의 구독 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="8c947-117">To open the Subscriptions page for report</span></span>  
  
1.  <span data-ttu-id="8c947-118">보고서 관리자를 열고 구독을 보거나 구성하려는 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-118">Open Report Manager, and locate the report for which you want to view or configure a subscription.</span></span>  
  
2.  <span data-ttu-id="8c947-119">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="8c947-120">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-120">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="8c947-121">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-121">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="8c947-122">**구독** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-122">Select the **Subscriptions** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c947-123">옵션</span><span class="sxs-lookup"><span data-stu-id="8c947-123">Options</span></span>  
 <span data-ttu-id="8c947-124">**Delete**</span><span class="sxs-lookup"><span data-stu-id="8c947-124">**Delete**</span></span>  
 <span data-ttu-id="8c947-125">구독을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-125">Click to delete a subscription.</span></span> <span data-ttu-id="8c947-126">구독을 삭제하기 전에 삭제할 각 구독 옆의 확인란을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c947-126">Before you can delete a subscription, select the check box next to each subscription that you want to delete.</span></span>  
  
 <span data-ttu-id="8c947-127">**새 구독**</span><span class="sxs-lookup"><span data-stu-id="8c947-127">**New Subscription**</span></span>  
 <span data-ttu-id="8c947-128">현재 보고서에 대한 새 구독을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-128">Click to create a new subscription to the current report.</span></span> <span data-ttu-id="8c947-129">이 단추는 보고서에서 저장된 자격 증명을 사용하는 경우나 자격 증명을 사용하지 않는 경우에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-129">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="8c947-130">공유 데이터 원본에 대한 구독 페이지를 여는 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-130">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="8c947-131">**새 데이터 기반 구독**</span><span class="sxs-lookup"><span data-stu-id="8c947-131">**New Data-Driven Subscription**</span></span>  
 <span data-ttu-id="8c947-132">해당 정보를 포함하는 데이터 저장소에 대한 쿼리나 명령을 통해 구독자 목록과 배달 옵션을 생성하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-132">Click to generate a subscriber list and delivery options from a command or query against a data store that contains this information.</span></span> <span data-ttu-id="8c947-133">이 단추는 보고서에서 저장된 자격 증명을 사용하는 경우나 자격 증명을 사용하지 않는 경우에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-133">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="8c947-134">공유 데이터 원본에 대한 구독 페이지를 여는 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-134">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="8c947-135">**편집**</span><span class="sxs-lookup"><span data-stu-id="8c947-135">**Edit**</span></span>  
 <span data-ttu-id="8c947-136">설명을 보거나 편집하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-136">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="8c947-137">**Report**</span><span class="sxs-lookup"><span data-stu-id="8c947-137">**Report**</span></span>  
 <span data-ttu-id="8c947-138">공유 데이터 원본에서 이 페이지를 열면 이 열은 구독이 정의된 보고서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-138">When you open this page from a shared data source, this column identifies the report for which the subscription is defined.</span></span> <span data-ttu-id="8c947-139">**폴더** 열은 보고서 위치를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-139">The **Folder** column identifies the location of the report.</span></span>  
  
 <span data-ttu-id="8c947-140">**설명**</span><span class="sxs-lookup"><span data-stu-id="8c947-140">**Description**</span></span>  
 <span data-ttu-id="8c947-141">보고서에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-141">Shows a description of the subscription.</span></span>  
  
 <span data-ttu-id="8c947-142">**트리거**</span><span class="sxs-lookup"><span data-stu-id="8c947-142">**Trigger**</span></span>  
 <span data-ttu-id="8c947-143">구독을 실행하는 조건을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-143">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="8c947-144">**TimedSubscription** 트리거는 구독이 실행되는 시기를 정의하는 일정을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-144">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="8c947-145">**SnapshotUpdated** 트리거는 보고서 스냅샷에 대한 업데이트를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-145">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="8c947-146">**소유자**</span><span class="sxs-lookup"><span data-stu-id="8c947-146">**Owner**</span></span>  
 <span data-ttu-id="8c947-147">구독을 만든 사용자 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-147">Shows the name of the user who created the subscription.</span></span>  
  
 <span data-ttu-id="8c947-148">**마지막 실행**</span><span class="sxs-lookup"><span data-stu-id="8c947-148">**Last Run**</span></span>  
 <span data-ttu-id="8c947-149">구독이 마지막으로 처리된 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-149">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="8c947-150">**상태**</span><span class="sxs-lookup"><span data-stu-id="8c947-150">**Status**</span></span>  
 <span data-ttu-id="8c947-151">구독 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-151">Shows the status of the subscription.</span></span> <span data-ttu-id="8c947-152">일반적으로 상태 값은 신규 또는 구독이 마지막으로 실행된 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-152">Usually, the status value is either New or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="8c947-153">"잘못된 데이터" 상태 값은 더 이상 유효하지 않은 암호화된 값, 즉 보고서를 실행하는 데 사용되는 저장된 자격 증명에 대한 포인터가 구독에 포함되어 있는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-153">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="8c947-154">데이터를 암호화 및 해독하는 데 사용되는 대칭 키를 보고서 서버에서 다시 만들면 기존의 암호화된 값은 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-154">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="8c947-155">비활성화된 구독은 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-155">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="8c947-156">구독을 업데이트하고 작동시키려면 해당 구독을 열어서 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c947-156">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c947-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c947-157">See Also</span></span>  
 <span data-ttu-id="8c947-158">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8c947-158">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="8c947-159">[기본 모드에서 표준 구독을 만들고, 수정 하 고, 삭제 &#40;Reporting Services&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="8c947-159">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="8c947-160">[일정 만들기, 수정 및 삭제](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="8c947-160">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="8c947-161">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="8c947-161">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
