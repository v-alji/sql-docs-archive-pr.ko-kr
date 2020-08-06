---
title: 카탈로그 항목 삭제(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2a1824f2611165c9ae891fcb702418244f3621e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649931"
---
# <a name="delete-catalog-items-management-studio"></a><span data-ttu-id="09241-102">카탈로그 항목 삭제(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="09241-102">Delete Catalog Items (Management Studio)</span></span>
  <span data-ttu-id="09241-103">이 페이지를 사용하여 공유 일정 및 역할 정의를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09241-103">Use this page to delete shared schedules and role definitions.</span></span>  
  
 <span data-ttu-id="09241-104">여러 보고서 및 구독에 사용되는 공유 일정을 삭제하면 보고서 서버는 공유 일정을 사용하던 각 보고서 및 구독에 대해 개별적인 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="09241-104">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="09241-105">각 개별 일정에는 공유 일정에 지정되었던 날짜, 시간 및 되풀이 패턴이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="09241-105">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="09241-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 개별 일정을 중앙에서 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09241-106">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="09241-107">공유 일정을 삭제하면 개별 항목에 대한 일정 정보를 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-107">If you delete a shared schedule, you will now need to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="09241-108">공유 일정을 삭제하기 전에 [일정 속성(보고서 페이지)](schedule-properties-reports-page.md) 을 사용하여 현재 공유 일정을 사용하고 있는 보고서를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-108">Before deleting a shared schedule, use the [Reports page](schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
 <span data-ttu-id="09241-109">역할 정의의 경우 역할 할당에 현재 사용 중이 아닌 역할 정의만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09241-109">For role definitions, you can only delete those that are not actively used in a role assignment.</span></span> <span data-ttu-id="09241-110">현재 사용 중인 역할을 삭제하려고 시도하면 보고서 서버는 해당 역할을 삭제하지 않고 이에 대한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="09241-110">If you try to delete a role that is currently in use, the report server will not delete the role and you will see an error message to that effect.</span></span> <span data-ttu-id="09241-111">이 페이지에 현재 사용 중이 아닌 하나의 역할 정의만 있는 경우 **확인**을 클릭하면 이 역할 정의가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="09241-111">If this page contains a single role definition that is not currently in use, it will be deleted when you click **OK**.</span></span> <span data-ttu-id="09241-112">이 페이지에 여러 역할이 있는 경우 보관하거나 제거할 역할을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09241-112">If this page contains multiple roles, you cannot select which roles to keep or remove.</span></span> <span data-ttu-id="09241-113">**확인**을 클릭하면 사용되지 않는 모든 역할 정의가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="09241-113">All unused role definitions will be deleted when you click **OK**.</span></span>  
  
 <span data-ttu-id="09241-114">삭제 작업은 실행 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09241-114">You cannot undo a delete operation.</span></span> <span data-ttu-id="09241-115">삭제한 항목을 복구하려면 해당 항목을 다시 만들거나 보고서 서버 데이터베이스의 백업 복사본을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-115">If you want to recover an item that you deleted, you must either recreate it or restore a backup copy of the report server database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09241-116">옵션</span><span class="sxs-lookup"><span data-stu-id="09241-116">Options</span></span>  
 <span data-ttu-id="09241-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="09241-117">**Name**</span></span>  
 <span data-ttu-id="09241-118">삭제할 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-118">Specifies the name of the item you are deleting.</span></span>  
  
 <span data-ttu-id="09241-119">**형식**</span><span class="sxs-lookup"><span data-stu-id="09241-119">**Type**</span></span>  
 <span data-ttu-id="09241-120">삭제할 항목의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-120">Shows the type of item you are deleting.</span></span>  
  
 <span data-ttu-id="09241-121">**소유자**</span><span class="sxs-lookup"><span data-stu-id="09241-121">**Owner**</span></span>  
 <span data-ttu-id="09241-122">소유자의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-122">Shows the name of the owner.</span></span> <span data-ttu-id="09241-123">대부분의 경우 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="09241-123">In most cases, this is System.</span></span>  
  
 <span data-ttu-id="09241-124">**상태**</span><span class="sxs-lookup"><span data-stu-id="09241-124">**Status**</span></span>  
 <span data-ttu-id="09241-125">삭제 작업의 진행률 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-125">Shows progress information for a delete operation.</span></span>  
  
 <span data-ttu-id="09241-126">**오류**</span><span class="sxs-lookup"><span data-stu-id="09241-126">**Error**</span></span>  
 <span data-ttu-id="09241-127">항목을 삭제하는 동안 오류가 발생할 경우 오류 코드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09241-127">Displays an error code if an error occurs while deleting an item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09241-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09241-128">See Also</span></span>  
 <span data-ttu-id="09241-129">[항목 삭제&#40;Management Studio&#41;](delete-an-item-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="09241-129">[Delete an Item &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span></span>  
 <span data-ttu-id="09241-130">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="09241-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="09241-131">일정 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="09241-131">Create, Modify, and Delete Schedules</span></span>](../subscriptions/create-modify-and-delete-schedules.md)  
  
  
