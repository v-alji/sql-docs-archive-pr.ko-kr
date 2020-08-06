---
title: Microsoft 복제 충돌 뷰어(트랜잭션 복제) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cc3f2ea3d1d2b29fba9c9d9121e23bf4bcd88bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638690"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a><span data-ttu-id="ee9f4-102">Microsoft 복제 충돌 뷰어(트랜잭션 복제)</span><span class="sxs-lookup"><span data-stu-id="ee9f4-102">Microsoft Replication Conflict Viewer (Transactional Replication)</span></span>
  <span data-ttu-id="ee9f4-103">복제 충돌 뷰어에서는 지연 업데이트 구독을 사용하는 트랜잭션 복제 및 피어 투 피어 트랜잭션 복제에서 동기화 중 발생한 충돌을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-103">The Replication Conflict Viewer enables you to view conflicts that have occurred during synchronization for peer-to-peer transactional replication and transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="ee9f4-104">자세한 내용은 [트랜잭션 게시의 데이터 충돌 확인&#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-104">For more information, see [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee9f4-105">복제 충돌 뷰어에는 병합 복제 및 트랜잭션 복제에서 발생하는 충돌이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-105">The Replication Conflict Viewer displays conflicts that occur in merge replication and in transactional replication.</span></span> <span data-ttu-id="ee9f4-106">트랜잭션 복제의 경우 복제 충돌 뷰어를 사용하여 충돌 데이터를 볼 수는 있지만 충돌에 대한 다른 해결 방법을 선택할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-106">For transactional replication, you can use Replication Conflict Viewer to view conflict data, but you cannot choose a different resolution for the conflict.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee9f4-107">옵션</span><span class="sxs-lookup"><span data-stu-id="ee9f4-107">Options</span></span>  
 <span data-ttu-id="ee9f4-108">복제 충돌 뷰어는 두 개의 섹션으로 나뉘어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-108">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="ee9f4-109">대화 상자의 위쪽 섹션에 선택한 테이블의 충돌 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-109">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="ee9f4-110">충돌 목록에서 항목을 클릭하면 대화 상자의 아래쪽 섹션에 해당 충돌에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-110">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="ee9f4-111">아래쪽 섹션에서 충돌 데이터는**충돌 시 적용되는 내용** 및 **충돌 시 변경 내용 무시**중 해당하는 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-111">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="ee9f4-112">업데이트된 데이터와 삭제된 데이터 간에 충돌이 있다면 충돌 시 삭제된 쪽을 표시하는 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-112">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="ee9f4-113">이 경우 복제 충돌 뷰어에서는 행이 한 위치에서 삭제되었고 다른 위치에서는 업데이트되었음을 나타내는 메시지를 열 중 하나에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-113">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="ee9f4-114">권장 해결 방법도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-114">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="ee9f4-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-115">**Database**</span></span>  
 <span data-ttu-id="ee9f4-116">충돌이 발생한 게시가 포함된 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-116">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="ee9f4-117">**게시**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-117">**Publication**</span></span>  
 <span data-ttu-id="ee9f4-118">충돌이 발생한 테이블이 포함된 게시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-118">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="ee9f4-119">**테이블**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-119">**Table**</span></span>  
 <span data-ttu-id="ee9f4-120">충돌이 발생한 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-120">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="ee9f4-121">**필터 정의**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-121">**Define Filter**</span></span>  
 <span data-ttu-id="ee9f4-122">**필터 정의** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-122">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="ee9f4-123">**필터 적용 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-123">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="ee9f4-124">**필터 정의** 대화 상자에서 정의한 필터를 적용하거나 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-124">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="ee9f4-125">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-125">**Select All**</span></span>  
 <span data-ttu-id="ee9f4-126">표에 나열된 모든 충돌을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-126">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="ee9f4-127">**없음 선택**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-127">**Select None**</span></span>  
 <span data-ttu-id="ee9f4-128">표에 나열된 모든 충돌의 선택을 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-128">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="ee9f4-129">**제거**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-129">**Remove**</span></span>  
 <span data-ttu-id="ee9f4-130">선택한 충돌을 뷰어에서 제거하고 연결된 메타데이터를 복제 시스템 테이블에서 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-130">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span>  
  
 <span data-ttu-id="ee9f4-131">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-131">**Show all columns**</span></span>  
 <span data-ttu-id="ee9f4-132">테이블의 모든 열을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-132">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="ee9f4-133">**처음 다섯 개의 열 및 충돌하는 데이터를 포함하는 기타 열 표시**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-133">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="ee9f4-134">처음 5개 열과 충돌이 발생한 기타 모든 열을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-134">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="ee9f4-135">이 옵션은 테이블에 많은 열이 있지만 충돌 해결에 가장 도움이 되는 열만 보려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-135">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="ee9f4-136">기본 키 또는 이름 필드와 같이 행을 식별하는 필드가 테이블의 앞쪽 열에 포함되어 있는 경우가 많으므로 처음 5개 열은 항상 이 뷰에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-136">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="ee9f4-137">**열 정보 표시**(**…**)</span><span class="sxs-lookup"><span data-stu-id="ee9f4-137">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="ee9f4-138">열 정보를 보려면 **테이블 이름**, **열 이름**, **데이터 형식**및 **열 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-138">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span>  
  
 <span data-ttu-id="ee9f4-139">**이 충돌 정보 기록**</span><span class="sxs-lookup"><span data-stu-id="ee9f4-139">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="ee9f4-140">자세한 충돌 정보를 파일에 기록하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-140">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="ee9f4-141">파일 위치를 지정하려면 **보기** 메뉴를 가리키고 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-141">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="ee9f4-142">값을 입력하거나 찾아보기 (**...**)를 클릭한 다음 해당 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-142">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="ee9f4-143">**확인** 을 클릭하여 **옵션** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ee9f4-143">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9f4-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee9f4-144">See Also</span></span>  
 <span data-ttu-id="ee9f4-145">[피어 투 피어 복제에서 충돌 검색](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ee9f4-145">[Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span></span>  
 [<span data-ttu-id="ee9f4-146">트랜잭션 게시의 데이터 충돌 확인&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ee9f4-146">View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;</span></span>](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
