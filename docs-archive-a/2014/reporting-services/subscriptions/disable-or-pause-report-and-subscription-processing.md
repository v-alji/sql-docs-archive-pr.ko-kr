---
title: 보고서 및 구독 처리 일시 중지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736011"
---
# <a name="pause-report-and-subscription-processing"></a><span data-ttu-id="827bb-102">보고서 및 구독 처리 일시 중지</span><span class="sxs-lookup"><span data-stu-id="827bb-102">Pause Report and Subscription Processing</span></span>
  <span data-ttu-id="827bb-103">보고서나 구독을 직접 일시 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-103">You cannot pause a report or subscription directly.</span></span> <span data-ttu-id="827bb-104">그러나 프로세스가 시작되거나 데이터 원본 연결이 만들어지기 전에 보고서 및 구독 처리를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-104">However, you can interrupt report and subscription processing prior to the process starting or when a data source connection is made.</span></span> <span data-ttu-id="827bb-105">사용자가 보고서나 구독에 액세스하지 못하도록 하여 보고서나 구독 처리를 중단할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-105">You can also prevent a report or subscription from processing by making it inaccessible to users.</span></span>  
  
 <span data-ttu-id="827bb-106">다음 방법으로 프로세스를 일시적으로 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-106">The following strategies can be used to temporarily prevent a process from occurring.</span></span>  
  
## <a name="modify-role-assignments-to-prevent-access"></a><span data-ttu-id="827bb-107">역할 할당을 수정하여 액세스 금지</span><span class="sxs-lookup"><span data-stu-id="827bb-107">Modify Role Assignments to Prevent Access</span></span>  
 <span data-ttu-id="827bb-108">보고서를 사용할 수 없도록 하는 최선의 방법은 보고서에 액세스할 수 있는 권한을 제공하는 역할 할당을 일시적으로 제거하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-108">The best way to make a report unavailable is to temporarily remove the role assignment that provides access to the report.</span></span> <span data-ttu-id="827bb-109">이 방법은 데이터 원본 연결이 생성되는 방법에 관계없이 모든 보고서에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-109">This approach can be used on all reports regardless of how the data source connection is made.</span></span> <span data-ttu-id="827bb-110">이 방법은 다른 보고서나 항목의 작업에 영향을 주지 않고 해당 보고서에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-110">This approach targets only the report, without affecting the operation of other reports or items.</span></span>  
  
 <span data-ttu-id="827bb-111">역할 할당을 제거하려면 보고서 관리자에서 보고서의 보안 속성 페이지를 여십시오.</span><span class="sxs-lookup"><span data-stu-id="827bb-111">To remove the role assignment, open the Security Properties page of the report in Report Manager.</span></span> <span data-ttu-id="827bb-112">보고서가 부모 보고서에서 보안 설정을 상속받은 경우 **항목 보안 편집** 을 클릭하여 광범위한 액세스를 제공하는 역할 할당은 포함하지 않는 제한적인 보안 정책을 만들 수 있습니다. 예를 들어 Everyone에게 액세스를 제공하는 역할 할당은 제거하고 Administrators와 같은 일부 사용자에게만 액세스를 제공하는 역할 할당은 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-112">If the report inherits security from a parent, you can click **Edit Item Security** to create a restrictive security policy that omits role assignments that provide widespread access (for example, you can remove a role assignment that provides access to Everyone, and keep the role assignment that provides access to a small group of users, such as Administrators).</span></span>  
  
## <a name="disable-a-shared-data-source"></a><span data-ttu-id="827bb-113">공유 데이터 원본 해제</span><span class="sxs-lookup"><span data-stu-id="827bb-113">Disable a Shared Data Source</span></span>  
 <span data-ttu-id="827bb-114">공유 데이터 원본 사용 시 이점은 보고서나 데이터 기반 구독이 실행되지 않도록 공유 데이터 원본을 해제할 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-114">One advantage to using shared data sources is that you can disable it to prevent a report or data-driven subscription from running.</span></span> <span data-ttu-id="827bb-115">공유 데이터 원본을 해제하면 보고서와 외부 원본의 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-115">Disabling a shared data source disconnects the report from its external source.</span></span> <span data-ttu-id="827bb-116">해제되어 있는 동안에는 데이터 원본을 사용하는 모든 보고서와 구독에서 해당 데이터 원본을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-116">While it is disabled, the data source is unavailable to all reports and subscriptions that use it.</span></span> <span data-ttu-id="827bb-117">공유 데이터 원본을 해제하려면 보고서 관리자에서 데이터 원본을 열고 **이 데이터 원본 사용** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-117">To disable a shared data source, open the data source in Report Manager and clear the **Enable this data source** check box.</span></span>  
  
 <span data-ttu-id="827bb-118">데이터 원본을 사용할 수 없는 경우에도 보고서는 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-118">Note that the report still loads even if the data source is unavailable.</span></span> <span data-ttu-id="827bb-119">보고서에는 데이터가 포함되지 않지만 적절한 권한이 있는 사용자는 보고서에 연결된 속성 페이지, 보안 설정, 보고서 기록 및 구독 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-119">The report does not contain data, but users with appropriate permissions can access the property pages, security settings, report history, and subscription information associated with the report.</span></span>  
  
## <a name="pause-a-shared-schedule"></a><span data-ttu-id="827bb-120">공유 일정 일시 중지</span><span class="sxs-lookup"><span data-stu-id="827bb-120">Pause a Shared Schedule</span></span>  
 <span data-ttu-id="827bb-121">보고서나 구독을 공유 일정에 따라 실행하는 경우 일정을 일시 중지하여 처리를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-121">If a report or subscription runs from a shared schedule, you can pause the schedule to prevent processing.</span></span> <span data-ttu-id="827bb-122">일정에 따라 진행되는 모든 보고서와 구독 처리는 일정을 다시 시작할 때까지 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="827bb-122">All report and subscription processing that is driven by the schedule is deferred until the schedule is resumed.</span></span> <span data-ttu-id="827bb-123">자세한 내용은 [공유 일정 일시 중지 및 다시 시작](schedules.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="827bb-123">For more information, see [Pause and Resume Shared Schedules](schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827bb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="827bb-124">See Also</span></span>  
 <span data-ttu-id="827bb-125">[Reporting Services 보고서 서버&#40;기본 모드&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="827bb-125">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="827bb-126">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="827bb-126">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="827bb-127">보안 속성 페이지, 항목&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="827bb-127">Security Properties Page, Items &#40;Report Manager&#41;</span></span>](../security-properties-page-items-report-manager.md)  
  
  
