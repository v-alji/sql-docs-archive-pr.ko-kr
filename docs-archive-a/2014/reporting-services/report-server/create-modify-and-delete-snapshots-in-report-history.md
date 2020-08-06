---
title: 보고서 기록에서 스냅샷 만들기, 수정 및 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ee091ad3361280c4da258eb86c83492ade8b3bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652581"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a><span data-ttu-id="1d0aa-102">보고서 기록에서 스냅샷 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="1d0aa-102">Create, Modify, and Delete Snapshots in Report History</span></span>
  <span data-ttu-id="1d0aa-103">보고서 기록은 보고서 스냅샷의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-103">Report history is a collection of report snapshots.</span></span> <span data-ttu-id="1d0aa-104">스냅샷을 추가하고 삭제하거나 보고서 기록 스토리지에 영향을 주는 속성을 수정하여 보고서 기록을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-104">You can maintain report history by adding and deleting snapshots, or by modifying properties that affect report history storage.</span></span> <span data-ttu-id="1d0aa-105">수동으로 또는 예약된 일정을 통해 보고서 기록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-105">You can create report history manually or on a schedule.</span></span>  
  
 <span data-ttu-id="1d0aa-106">보고서 기록을 만들려면 역할 할당에 "보고서 기록 관리" 태스크가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-106">To create report history, your role assignment must include the "Manage report history" task.</span></span> <span data-ttu-id="1d0aa-107">보고서 기록을 보려면 역할 할당에 "보고서 보기" 태스크가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-107">To view report history, your role assignment must include the "View reports" task.</span></span> <span data-ttu-id="1d0aa-108">보고서에 액세스할 수 있는 모든 사용자가 보고서 기록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-108">Report history is available to all users who have access to the report.</span></span> <span data-ttu-id="1d0aa-109">특정 사용자 그룹에 대해서만 보고서 기록을 설정하거나 해제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-109">You cannot selectively enable or disable report history for a subset of users.</span></span>  
  
 <span data-ttu-id="1d0aa-110">보고서 기록의 스냅샷은 작성 날짜와 시간으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-110">Snapshots in report history are identified by the date and time that they were created.</span></span> <span data-ttu-id="1d0aa-111">날짜와 시간은 쿼리 실행 시점을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-111">The date and time is based on when the query executed.</span></span>  
  
## <a name="creating-snapshots-in-report-history"></a><span data-ttu-id="1d0aa-112">보고서 기록에서 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="1d0aa-112">Creating Snapshots in Report History</span></span>  
 <span data-ttu-id="1d0aa-113">무인 모드에서 실행할 수 있는 모든 보고서에 대해 수동으로 또는 예약된 간격으로 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-113">Snapshots can be created manually or at scheduled intervals for any report that can run unattended.</span></span> <span data-ttu-id="1d0aa-114">무인 모드에서 실행하려면 보고서에서 저장된 자격 증명을 사용하거나 아무 자격 증명도 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-114">To run unattended, the report must use stored credentials or no credentials at all.</span></span> <span data-ttu-id="1d0aa-115">또한 보고서가 매개 변수를 사용하는 경우 보고서를 실행할 때 사용할 기본값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-115">Furthermore, if the report uses parameters, you must specify default values to use when the report runs.</span></span> <span data-ttu-id="1d0aa-116">보고서의 속성 페이지에서 저장된 자격 증명과 매개 변수 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-116">You can specify stored credentials and parameter values in the property pages for the report.</span></span> <span data-ttu-id="1d0aa-117">자세한 내용은 [매개 변수 속성 페이지&#40;보고서 관리자&#41;](../parameters-properties-page-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-117">For more information, see [Parameters Properties Page &#40;Report Manager&#41;](../parameters-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1d0aa-118">보고서 스냅샷을 만들면 다음 요소가 보고서 서버 데이터베이스의 보고서 스냅샷과 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-118">When you create a report snapshot, the following elements are stored along with the report snapshot in the report server database:</span></span>  
  
-   <span data-ttu-id="1d0aa-119">결과 집합(즉, 보고서의 데이터 원본 속성 페이지에서 지정된 자격 증명을 통해 검색된 보고서의 데이터)</span><span class="sxs-lookup"><span data-stu-id="1d0aa-119">The result set (that is, the data in the report, retrieved through the credentials specified in the Data Sources properties page of the report).</span></span>  
  
-   <span data-ttu-id="1d0aa-120">기본 보고서 정의(스냅샷 작성 시 존재하는 보고서 정의).</span><span class="sxs-lookup"><span data-stu-id="1d0aa-120">The underlying report definition, as it exists at the time the snapshot was created.</span></span> <span data-ttu-id="1d0aa-121">스냅샷 생성 후 보고서 정의가 수정되는 경우 해당 변경 내용은 스냅샷에 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-121">If the report definition is subsequently modified after the snapshot is generated, those changes are not reflected in the snapshot.</span></span>  
  
-   <span data-ttu-id="1d0aa-122">결과 집합을 구하거나 필터링하는 데 사용되는 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="1d0aa-122">Parameter values that are used to obtain or filter the result set.</span></span>  
  
-   <span data-ttu-id="1d0aa-123">이미지 등의 포함 리소스.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-123">Embedded resources, such as images.</span></span> <span data-ttu-id="1d0aa-124">보고서에 링크된 외부 리소스는 보고서 스냅샷에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-124">External resources that are linked to a report are not stored with the report snapshot.</span></span>  
  
 <span data-ttu-id="1d0aa-125">보고서 기록을 만들 수 있는 방법과 저장할 수 있는 보고서 스냅샷 수는 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-125">The ways in which report history can be created and the number of report snapshots that can be stored are determined by settings.</span></span>  
  
 <span data-ttu-id="1d0aa-126">보고서에서 오류가 발생하면 스냅샷이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-126">If a report produces an error, a snapshot is not created.</span></span> <span data-ttu-id="1d0aa-127">보고서에서 경고가 발생하지만 계속 실행되는 경우에는 스냅샷을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-127">Reports that produce warnings, yet still run, can be used to generate snapshots.</span></span>  
  
## <a name="modifying-properties-and-deleting-report-history"></a><span data-ttu-id="1d0aa-128">속성 수정 및 보고서 기록 삭제</span><span class="sxs-lookup"><span data-stu-id="1d0aa-128">Modifying Properties and Deleting Report History</span></span>  
 <span data-ttu-id="1d0aa-129">한번 생성된 보고서 스냅샷은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-129">Once a report snapshot exists, you cannot modify it.</span></span> <span data-ttu-id="1d0aa-130">그러나 보고서 기록을 삭제하는 방식으로 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-130">However, you can modify properties in a way that deletes report history.</span></span>  
  
 <span data-ttu-id="1d0aa-131">보고서 기록은 다음과 같은 방법으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-131">Report history can be deleted in the following ways:</span></span>  
  
-   <span data-ttu-id="1d0aa-132">스냅샷을 단독으로 또는 그룹으로 직접 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-132">Manually delete snapshots singly or in groups.</span></span>  
  
     <span data-ttu-id="1d0aa-133">보고서 관리자의 기록 페이지에서 스냅샷을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-133">You can delete snapshots from the History page in Report Manager.</span></span> <span data-ttu-id="1d0aa-134">보고서로 이동하고 기록을 클릭한 다음 삭제할 스냅샷 옆의 확인란을 선택한 후 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-134">Navigate to the report, click History, select the check box next to the snapshots that you want to delete, and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="1d0aa-135">보고서 기록 제한을 낮춰 저장되는 스냅샷 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-135">Lower the report history limit to reduce the number of snapshots that are stored.</span></span> <span data-ttu-id="1d0aa-136">보고서 기록 제한은 보고서 서버나 특정 보고서에 대해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-136">The report history limit can be set for the report server or for specific reports.</span></span> <span data-ttu-id="1d0aa-137">제한을 낮추면 기록에서 가장 오래된 스냅샷부터 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-137">When the limit is lowered, the oldest snapshots are deleted from history.</span></span>  
  
 <span data-ttu-id="1d0aa-138">보고서 서버에 저장된 보고서 기록을 대량 작업으로 모두 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-138">You cannot delete all report history stored on a report server in a bulk operation.</span></span>  
  
 <span data-ttu-id="1d0aa-139">보고서를 삭제하면 보고서 기록도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-139">Report history is also deleted when you delete a report.</span></span> <span data-ttu-id="1d0aa-140">예를 들어 월별 판매 보고서를 새 버전으로 바꾸기 위해 삭제하면 이 보고서와 연결된 보고서 기록도 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-140">For example, if you delete a monthly sales report because you are replacing it with a newer version, all report history that is associated with the report is also deleted.</span></span> <span data-ttu-id="1d0aa-141">그러나 보고서를 이동하면 모든 보고서 기록도 함께 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1d0aa-141">However, if you move a report, all report history moves with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0aa-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d0aa-142">See Also</span></span>  
 <span data-ttu-id="1d0aa-143">[보고서 기록 만들기&#40;SharePoint 통합 모드의 Reporting Services&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1d0aa-143">[Create Report History &#40;Reporting Services in SharePoint Integrated Mode&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="1d0aa-144">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1d0aa-144">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1d0aa-145">[보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;](report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1d0aa-145">[Report Server Content Management &#40;SSRS Native Mode&#41;](report-server-content-management-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1d0aa-146">[보고서 기록에 스냅샷 추가&#40;보고서 관리자&#41;](add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1d0aa-146">[Add a Snapshot to Report History &#40;Report Manager&#41;](add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="1d0aa-147">보고서 기록 제한&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="1d0aa-147">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)  
  
  
