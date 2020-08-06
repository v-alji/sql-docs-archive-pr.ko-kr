---
title: 내 구독 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 491a85a3-f323-4155-a0a8-de2779899995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 891796ec491b157f3c9bb5b4adfd15daedbc7c88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739519"
---
# <a name="my-subscriptions-page-report-manager"></a><span data-ttu-id="1bceb-102">내 구독 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="1bceb-102">My Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="1bceb-103">내 구독 페이지를 사용하여 모든 구독을 한 곳에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-103">Use the My Subscriptions page to view all of your subscriptions in one place.</span></span> <span data-ttu-id="1bceb-104">이 페이지에서는 소유한 모든 구독을 액세스하고 수정 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-104">From this page, you can access and modify or delete any subscription that you own.</span></span> <span data-ttu-id="1bceb-105">사용자는 자신이 만든 구독만 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-105">You own only the subscriptions that you create.</span></span> <span data-ttu-id="1bceb-106">다른 사용자가 정의한 구독에는 액세스할 수 없을 뿐 아니라 사용하지만 소유하지 않는 구독(예: 다른 사용자가 정의한 기존 구독에 자신의 이름이 추가된 경우)에도 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-106">You cannot access those of other users, nor can you access subscriptions that you use but do not own (for example, if your name has been added to an existing subscription defined by another user).</span></span> <span data-ttu-id="1bceb-107">이 페이지에서 구독을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-107">You cannot create subscriptions from this page.</span></span> <span data-ttu-id="1bceb-108">구독을 만드는 방법에 대 한 자세한 내용은 [새 구독 또는 구독 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bceb-108">For more information about creating subscriptions, see the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1bceb-109">기본적으로 구독은 보고서 이름을 기준으로 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-109">By default, subscriptions are sorted in alphabetical order by report name.</span></span> <span data-ttu-id="1bceb-110">구독 정렬 방법을 변경하려면 다른 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-110">Click a different column heading to change how subscriptions are sorted.</span></span> <span data-ttu-id="1bceb-111">구독이 없거나 구독 생성 또는 관리 권한이 해제되어 있는 경우에는 이 페이지에 구독이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-111">If you have no subscriptions or if permission to create or manage subscriptions is disabled, no subscriptions appear on the page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bceb-112">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-112">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1bceb-113">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bceb-113">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1bceb-114">탐색</span><span class="sxs-lookup"><span data-stu-id="1bceb-114">Navigation</span></span>  
 <span data-ttu-id="1bceb-115">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="1bceb-115">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-my-subscriptions-page"></a><span data-ttu-id="1bceb-116">내 구독 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="1bceb-116">To open the My Subscriptions page</span></span>  
  
1.  <span data-ttu-id="1bceb-117">보고서 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-117">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="1bceb-118">페이지 맨 위에서 오른쪽 모퉁이에 있는 내 구독을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-118">At the top of the page, in the right-hand corner, click My Subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1bceb-119">구독 만들기 권한이 없는 경우에도 항상 내 구독을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-119">My Subscriptions is always available, even if you lack permission to create subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1bceb-120">옵션</span><span class="sxs-lookup"><span data-stu-id="1bceb-120">Options</span></span>  
 <span data-ttu-id="1bceb-121">**삭제**</span><span class="sxs-lookup"><span data-stu-id="1bceb-121">**Delete**</span></span>  
 <span data-ttu-id="1bceb-122">삭제할 각 구독 옆에 있는 확인란을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-122">Select the check box next to each subscription that you want to delete and click **Delete**.</span></span>  
  
 <span data-ttu-id="1bceb-123">**편집**</span><span class="sxs-lookup"><span data-stu-id="1bceb-123">**Edit**</span></span>  
 <span data-ttu-id="1bceb-124">설명을 보거나 편집하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-124">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="1bceb-125">**Report**</span><span class="sxs-lookup"><span data-stu-id="1bceb-125">**Report**</span></span>  
 <span data-ttu-id="1bceb-126">구독에 지정된 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-126">Shows the report that is specified in the subscription.</span></span> <span data-ttu-id="1bceb-127">보고서를 보려면 보고서 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-127">Click the report name to view the report.</span></span>  
  
 <span data-ttu-id="1bceb-128">**설명**</span><span class="sxs-lookup"><span data-stu-id="1bceb-128">**Description**</span></span>  
 <span data-ttu-id="1bceb-129">보고서에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-129">Shows a description of the subscription.</span></span> <span data-ttu-id="1bceb-130">보고서의 구독 정보를 보거나 편집하려면 설명을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-130">Click the description to view or edit the subscription information for the report.</span></span>  
  
 <span data-ttu-id="1bceb-131">**폴더**</span><span class="sxs-lookup"><span data-stu-id="1bceb-131">**Folder**</span></span>  
 <span data-ttu-id="1bceb-132">구독에 지정된 보고서를 포함하는 폴더를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-132">Shows the folder that contains the report that is specified in the subscription.</span></span> <span data-ttu-id="1bceb-133">폴더의 내용을 보려면 폴더 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-133">Click the folder name to view the contents of the folder.</span></span>  
  
 <span data-ttu-id="1bceb-134">**트리거**</span><span class="sxs-lookup"><span data-stu-id="1bceb-134">**Trigger**</span></span>  
 <span data-ttu-id="1bceb-135">구독을 실행하는 조건을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-135">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="1bceb-136">**TimedSubscription** 트리거는 구독이 실행되는 시기를 정의하는 일정을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-136">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="1bceb-137">**SnapshotUpdated** 트리거는 보고서 스냅샷에 대한 업데이트를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-137">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="1bceb-138">**마지막 실행**</span><span class="sxs-lookup"><span data-stu-id="1bceb-138">**Last Run**</span></span>  
 <span data-ttu-id="1bceb-139">구독이 마지막으로 처리된 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-139">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="1bceb-140">**상태**</span><span class="sxs-lookup"><span data-stu-id="1bceb-140">**Status**</span></span>  
 <span data-ttu-id="1bceb-141">구독 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-141">Shows the status of the subscription.</span></span> <span data-ttu-id="1bceb-142">일반적으로 상태 값은 "신규" 또는 구독이 마지막으로 실행된 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-142">Usually, the status value is either "New" or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="1bceb-143">"잘못된 데이터" 상태 값은 더 이상 유효하지 않은 암호화된 값, 즉 보고서를 실행하는 데 사용되는 저장된 자격 증명에 대한 포인터가 구독에 포함되어 있는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-143">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="1bceb-144">데이터를 암호화 및 해독하는 데 사용되는 대칭 키를 보고서 서버에서 다시 만들면 기존의 암호화된 값은 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-144">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="1bceb-145">비활성화된 구독은 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-145">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="1bceb-146">구독을 업데이트하고 작동시키려면 해당 구독을 열어서 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1bceb-146">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bceb-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bceb-147">See Also</span></span>  
 <span data-ttu-id="1bceb-148">[구독 및 배달&#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="1bceb-148">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="1bceb-149">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="1bceb-149">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
