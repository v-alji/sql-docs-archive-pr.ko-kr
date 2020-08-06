---
title: 스냅숏 옵션 속성 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3025b23dfe498a92c2ce1d8535229d8d23dfd429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729012"
---
# <a name="snapshot-options-properties-page-report-manager"></a><span data-ttu-id="b4af9-102">스냅샷 옵션 속성 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="b4af9-102">Snapshot Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="b4af9-103">스냅샷 옵션 속성 페이지를 사용하여 보고서 스냅샷이 보고서 기록에 추가되는 일정을 예약할 수 있고 보고서 기록에 저장되는 보고서 스냅샷 수에 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-103">Use the Snapshot Options properties page to schedule report snapshots to be added to report history, and to set limits on the number of report snapshots that are stored in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4af9-104">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b4af9-105">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [추가 데이터베이스 서비스](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4af9-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Additional Database Services](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="b4af9-106">탐색</span><span class="sxs-lookup"><span data-stu-id="b4af9-106">Navigation</span></span>  
 <span data-ttu-id="b4af9-107">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4af9-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a><span data-ttu-id="b4af9-108">보고서의 스냅샷 옵션 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="b4af9-108">To open the Snapshot Options properties page for a report</span></span>  
  
1.  <span data-ttu-id="b4af9-109">보고서 관리자를 열고 보고서 스냅샷 속성을 구성할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-109">Open Report Manager, and locate the report for which you want to configure report snapshot properties.</span></span>  
  
2.  <span data-ttu-id="b4af9-110">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="b4af9-111">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="b4af9-112">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-112">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="b4af9-113">**스냅샷 옵션** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-113">Select the **Snapshot Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4af9-114">옵션</span><span class="sxs-lookup"><span data-stu-id="b4af9-114">Options</span></span>  
 <span data-ttu-id="b4af9-115">**수동으로 보고서 기록 작성 허용**</span><span class="sxs-lookup"><span data-stu-id="b4af9-115">**Allow report history to be created manually**</span></span>  
 <span data-ttu-id="b4af9-116">필요에 따라 스냅샷을 보고서 기록에 추가하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-116">Select this check box to add snapshots to report history as needed.</span></span> <span data-ttu-id="b4af9-117">이 확인란을 선택하면 기록 페이지에 **새 스냅샷** 단추가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-117">Selecting this check box causes the **New Snapshot** button to appear on the History page.</span></span>  
  
 <span data-ttu-id="b4af9-118">**모든 보고서 실행 스냅샷을 보고서 기록에 저장**</span><span class="sxs-lookup"><span data-stu-id="b4af9-118">**Store all report execution snapshots in report history**</span></span>  
 <span data-ttu-id="b4af9-119">보고서 실행 속성에 따라 생성하는 보고서 스냅샷을 보고서 기록에 복사하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-119">Select this check box to copy a report snapshot that you generate based on report execution properties to report history.</span></span> <span data-ttu-id="b4af9-120">생성된 스냅샷에서 보고서를 실행하도록 보고서 실행 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-120">You can set report execution properties to run a report from a generated snapshot.</span></span> <span data-ttu-id="b4af9-121">이 보고서 기록 속성을 설정하면 스냅샷의 복사본을 보고서 기록에 저장하여 시간에 따라 생성되는 모든 보고서 스냅샷에 대한 기록을 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-121">By setting this report history property, you can keep a record of all reports snapshots that are generated over time by placing copies of them in report history.</span></span>  
  
 <span data-ttu-id="b4af9-122">**다음 일정을 사용하여 스냅샷을 보고서 기록에 추가하십시오.**</span><span class="sxs-lookup"><span data-stu-id="b4af9-122">**Use the following schedule to add snapshots to report history**</span></span>  
 <span data-ttu-id="b4af9-123">일정에 따라 스냅샷을 보고서 기록에 추가하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-123">Select this check box to add snapshots to report history on a scheduled basis.</span></span> <span data-ttu-id="b4af9-124">이 용도로 사용되는 일정을 따로 만들 수도 있고 원하는 일정 정보가 포함된 경우 미리 정의된 공유 일정에서 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-124">You can create a schedule that is used exclusively for this purpose, or you can select a predefined shared schedule if one contains the schedule information you want.</span></span>  
  
 <span data-ttu-id="b4af9-125">**보관할 스냅샷 개수 선택**</span><span class="sxs-lookup"><span data-stu-id="b4af9-125">**Select the number of snapshots to keep**</span></span>  
 <span data-ttu-id="b4af9-126">보고서 기록에 보관되는 보고서 개수를 제어하려면 다음 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-126">Select from the following options to control the number of reports that are kept in report history.</span></span> <span data-ttu-id="b4af9-127">보고서 기록 설정은 보고서마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-127">Report history settings can vary for each report.</span></span>  
  
-   <span data-ttu-id="b4af9-128">기본 설정을 유지하려면 **기본 설정 사용** 을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4af9-128">Select **Use default setting** to retain the default setting.</span></span> <span data-ttu-id="b4af9-129">보고서 서버 관리자가 보고서 기록 스토리지에 대한 마스터 설정을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-129">The report server administrator controls a master setting for report history storage.</span></span> <span data-ttu-id="b4af9-130">이 옵션을 선택하는 경우 보존되는 스냅샷의 개수는 이 마스터 설정에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-130">If you choose this option, the number of snapshots that are retained is obtained from this master setting.</span></span>  
  
-   <span data-ttu-id="b4af9-131">모든 보고서 기록 스냅샷을 보존하려면 **보고서 기록에 스냅샷을 무제한 보관** 을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4af9-131">Select **Keep an unlimited number of snapshots in report history** to retain all report history snapshots.</span></span> <span data-ttu-id="b4af9-132">보고서 기록 크기를 줄이려면 스냅샷을 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-132">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
-   <span data-ttu-id="b4af9-133">설정된 개수의 스냅샷을 보존하려면 **보고서 기록의 복사본 개수 제한** 을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4af9-133">Select **Limit the copies of report history** to retain a set number of snapshots.</span></span> <span data-ttu-id="b4af9-134">한도에 이르면 새 복사본의 저장 공간을 만들기 위해 보고서 기록에서 오래된 복사본이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-134">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="b4af9-135">보고서 기록은 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-135">Report history is stored in the report server database.</span></span> <span data-ttu-id="b4af9-136">기록을 유지하려는 보고서의 수가 많거나 용량이 큰 경우 보고서 서버 데이터베이스의 디스크 공간 요구 사항을 관리하기 쉽도록 보고서 기록의 크기를 제한하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-136">If you have large reports or numerous reports for which you want to maintain history, consider limiting the amount of report history to help manage the disk space requirements of the report server database.</span></span>  
  
 <span data-ttu-id="b4af9-137">**적용**</span><span class="sxs-lookup"><span data-stu-id="b4af9-137">**Apply**</span></span>  
 <span data-ttu-id="b4af9-138">클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4af9-138">Click to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4af9-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4af9-139">See Also</span></span>  
 <span data-ttu-id="b4af9-140">[보고서 기록에 스냅숏을 추가 &#40;보고서 관리자&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b4af9-140">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="b4af9-141">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b4af9-141">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="b4af9-142">[보고서 기록에서 스냅샷 만들기, 수정 및 삭제](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span><span class="sxs-lookup"><span data-stu-id="b4af9-142">[Create, Modify, and Delete Snapshots in Report History](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span></span>  
 [<span data-ttu-id="b4af9-143">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="b4af9-143">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
