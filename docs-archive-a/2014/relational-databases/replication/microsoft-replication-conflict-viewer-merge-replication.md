---
title: Microsoft 복제 충돌 뷰어(병합 복제) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvmerge.f1
ms.assetid: bfef5e21-ac04-4bc5-a55e-595421e34923
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1354a35e06f58b56f9678267338917a272ff8b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646365"
---
# <a name="microsoft-replication-conflict-viewer-merge-replication"></a><span data-ttu-id="bf92f-102">Microsoft 복제 충돌 뷰어(병합 게시)</span><span class="sxs-lookup"><span data-stu-id="bf92f-102">Microsoft Replication Conflict Viewer (Merge Replication)</span></span>
  <span data-ttu-id="bf92f-103">복제 충돌 뷰어를 사용하면 복제 동기화를 수행하는 동안 발생한 모든 충돌을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-103">The Replication Conflict Viewer allows you to view any conflicts that have occurred during replication synchronization.</span></span> <span data-ttu-id="bf92f-104">충돌은 게시자와 구독자 또는 두 구독자 등 두 위치에서 같은 데이터를 동시에 변경할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-104">Conflicts occur when the same data is modified at two separate servers, for example, at a Publisher and Subscriber, or at two different Subscribers.</span></span> <span data-ttu-id="bf92f-105">복제는 아티클을 만들 때 선택한 충돌 해결 프로그램을 사용하여 충돌을 자동으로 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-105">Replication automatically resolves conflicts using the conflict resolver you selected when the article was created.</span></span> <span data-ttu-id="bf92f-106">그러나 필요한 경우 복제 충돌 뷰어를 사용하여 충돌 해결에 다른 해결 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-106">However, the Replication Conflict Viewer allows you to choose a different resolution for the conflict when necessary.</span></span> <span data-ttu-id="bf92f-107">다음과 같은 두 가지 충돌이 일어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-107">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="bf92f-108">업데이트 충돌.</span><span class="sxs-lookup"><span data-stu-id="bf92f-108">Update conflicts.</span></span> <span data-ttu-id="bf92f-109">업데이트 충돌은 같은 데이터를 두 위치에서 변경할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-109">Update conflicts occur when the same data is changed at two locations.</span></span> <span data-ttu-id="bf92f-110">이 경우 한 가지 변경 내용만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-110">One change wins, and the other one loses.</span></span> <span data-ttu-id="bf92f-111">기존 데이터를 유지하거나(이 경우 기존 데이터가 적용되는 데이터임) 기존 데이터와 충돌하는 데이터로 기존 데이터를 덮어쓰거나(이 경우 기존 데이터가 무시되는 데이터임) 두 데이터를 병합하여 기존 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-111">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="bf92f-112">삽입 충돌.</span><span class="sxs-lookup"><span data-stu-id="bf92f-112">Insert conflicts.</span></span> <span data-ttu-id="bf92f-113">삽입 충돌은 데이터 일관성 규칙을 일부 위반하는 행을 한 위치에서 삽입하고 이 행을 다른 위치에서 적용한 변경 내용과 병합할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-113">Insert conflicts occur when a row is inserted at one location that violates some data consistency rule when merged with changes at other locations.</span></span> <span data-ttu-id="bf92f-114">기존 데이터를 유지하거나(이 경우 기존 데이터가 적용되는 데이터임) 기존 데이터와 충돌하는 데이터로 기존 데이터를 덮어쓰거나(이 경우 기존 데이터가 무시되는 데이터임) 두 데이터를 병합하여 기존 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-114">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="bf92f-115">삭제 충돌.</span><span class="sxs-lookup"><span data-stu-id="bf92f-115">Delete conflicts.</span></span> <span data-ttu-id="bf92f-116">삭제 충돌은 한 위치에서 행을 삭제하고 다른 위치에서 같은 행을 변경할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-116">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="bf92f-117">동기화하는 동안 충돌이 해결될 때는 무시되는 행의 데이터가 충돌 테이블에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-117">When conflicts are resolved during synchronization, the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="bf92f-118">충돌 해결을 위해 원래 해결 방법을 적용하든지, 아니면 다른 해결 방법을 선택하든지에 관계없이 기록된 충돌 행은 충돌 테이블에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-118">Whether you accept the original resolution or choose a different resolution for the conflict, the logged conflict row is deleted from the conflict table.</span></span> <span data-ttu-id="bf92f-119">충돌 추적 테이블의 크기를 줄이려면 정기적으로 충돌을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-119">You should periodically review conflicts to help reduce the size of the conflict tracking tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf92f-120">논리적 레코드와 관련된 충돌은 충돌 뷰어에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-120">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="bf92f-121">이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-121">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="bf92f-122">자세한 내용은 [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](view-conflict-information-for-merge-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf92f-122">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf92f-123">옵션</span><span class="sxs-lookup"><span data-stu-id="bf92f-123">Options</span></span>  
 <span data-ttu-id="bf92f-124">복제 충돌 뷰어는 두 개의 섹션으로 나뉘어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-124">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="bf92f-125">대화 상자의 위쪽 섹션에 선택한 테이블의 충돌 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-125">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="bf92f-126">충돌 목록에서 항목을 클릭하면 대화 상자의 아래쪽 섹션에 해당 충돌에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-126">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="bf92f-127">충돌이 발생한 원인(예: 게시자 및 구독자 모두에서 같은 행 업데이트)에 대한 정보는 대화 상자의 아래쪽 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-127">Information describing why the conflict occurred (for example, the same row was updated at both the Publisher and the Subscriber) is displayed in the lower section of the dialog box.</span></span> <span data-ttu-id="bf92f-128">아래쪽 섹션에서 충돌 데이터는**충돌 시 적용되는 내용** 및 **충돌 시 변경 내용 무시**중 해당하는 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-128">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="bf92f-129">업데이트된 데이터와 삭제된 데이터 간에 충돌이 있다면 충돌 시 삭제된 쪽을 표시하는 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-129">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="bf92f-130">이 경우 복제 충돌 뷰어에서는 행이 한 위치에서 삭제되었고 다른 위치에서는 업데이트되었음을 나타내는 메시지를 열 중 하나에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-130">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating that the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="bf92f-131">권장 해결 방법도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-131">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="bf92f-132">복제 충돌 뷰어에서 편집할 수 없는 데이터(예: **rowguid** 데이터)는 회색으로 표시되며 읽기 전용으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-132">Data that cannot be edited in the Replication Conflict Viewer (for example, **rowguid** data) is displayed read-only with the box shaded.</span></span>  
  
 <span data-ttu-id="bf92f-133">**Database**</span><span class="sxs-lookup"><span data-stu-id="bf92f-133">**Database**</span></span>  
 <span data-ttu-id="bf92f-134">충돌이 발생한 게시가 포함된 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-134">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="bf92f-135">**게시**</span><span class="sxs-lookup"><span data-stu-id="bf92f-135">**Publication**</span></span>  
 <span data-ttu-id="bf92f-136">충돌이 발생한 테이블이 포함된 게시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-136">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="bf92f-137">**테이블**</span><span class="sxs-lookup"><span data-stu-id="bf92f-137">**Table**</span></span>  
 <span data-ttu-id="bf92f-138">충돌이 발생한 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-138">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="bf92f-139">**필터 정의**</span><span class="sxs-lookup"><span data-stu-id="bf92f-139">**Define Filter**</span></span>  
 <span data-ttu-id="bf92f-140">**필터 정의** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-140">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="bf92f-141">**필터 적용 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="bf92f-141">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="bf92f-142">**필터 정의** 대화 상자에서 정의한 필터를 적용하거나 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-142">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="bf92f-143">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="bf92f-143">**Select All**</span></span>  
 <span data-ttu-id="bf92f-144">표에 나열된 모든 충돌을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-144">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="bf92f-145">**없음 선택**</span><span class="sxs-lookup"><span data-stu-id="bf92f-145">**Select None**</span></span>  
 <span data-ttu-id="bf92f-146">표에 나열된 모든 충돌의 선택을 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-146">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="bf92f-147">**제거**</span><span class="sxs-lookup"><span data-stu-id="bf92f-147">**Remove**</span></span>  
 <span data-ttu-id="bf92f-148">선택한 충돌을 뷰어에서 제거하고 연결된 메타데이터를 복제 시스템 테이블에서 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-148">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span> <span data-ttu-id="bf92f-149">선택한 각 충돌에 대해 데이터를 변경하지 않고 적용되는 내용 전송 단추를 클릭하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-149">Equivalent to clicking the Submit Winner button (without making any changes to the data) for each selected conflict.</span></span>  
  
 <span data-ttu-id="bf92f-150">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="bf92f-150">**Show all columns**</span></span>  
 <span data-ttu-id="bf92f-151">테이블의 모든 열을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-151">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="bf92f-152">**처음 다섯 개의 열 및 충돌하는 데이터를 포함하는 기타 열 표시**</span><span class="sxs-lookup"><span data-stu-id="bf92f-152">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="bf92f-153">처음 5개 열과 충돌이 발생한 기타 모든 열을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-153">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="bf92f-154">이 옵션은 테이블에 많은 열이 있지만 충돌 해결에 가장 도움이 되는 열만 보려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-154">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="bf92f-155">기본 키 또는 이름 필드와 같이 행을 식별하는 필드가 테이블의 앞쪽 열에 포함되어 있는 경우가 많으므로 처음 5개 열은 항상 이 뷰에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-155">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="bf92f-156">**열 정보 표시**(**…**)</span><span class="sxs-lookup"><span data-stu-id="bf92f-156">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="bf92f-157">열 정보를 보려면 **테이블 이름**, **열 이름**, **데이터 형식**및 **열 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-157">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span> <span data-ttu-id="bf92f-158">**열 값** 은 읽기 전용으로 표시되지 않는 경우 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-158">**Column Value** is editable unless the value is displayed as read-only.</span></span>  
  
 <span data-ttu-id="bf92f-159">**적용되는 내용 전송**</span><span class="sxs-lookup"><span data-stu-id="bf92f-159">**Submit Winner**</span></span>  
 <span data-ttu-id="bf92f-160">충돌 해결 프로그램에서 적용되는 내용으로 결정한 행을 유지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-160">Click to keep the row the conflict resolver determined to be the winner.</span></span> <span data-ttu-id="bf92f-161">이 단추를 클릭하기 전에 읽기 전용으로 표시되지 않은 모든 열의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-161">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="bf92f-162">**무시되는 내용 전송**</span><span class="sxs-lookup"><span data-stu-id="bf92f-162">**Submit Loser**</span></span>  
 <span data-ttu-id="bf92f-163">충돌 해결 프로그램에서 무시되는 내용으로 결정한 행을 적용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-163">Click to accept the row the conflict resolver determined to be the loser.</span></span> <span data-ttu-id="bf92f-164">이 단추를 클릭하기 전에 읽기 전용으로 표시되지 않은 모든 열의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-164">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="bf92f-165">**이 충돌 정보 기록**</span><span class="sxs-lookup"><span data-stu-id="bf92f-165">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="bf92f-166">자세한 충돌 정보를 파일에 기록하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-166">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="bf92f-167">파일 위치를 지정하려면 **보기** 메뉴를 가리키고 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-167">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="bf92f-168">값을 입력하거나 찾아보기 (**...**)를 클릭한 다음 해당 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-168">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="bf92f-169">**확인** 을 클릭하여 **옵션** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="bf92f-169">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf92f-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf92f-170">See Also</span></span>  
 <span data-ttu-id="bf92f-171">[병합 게시에 대 한 데이터 충돌 보기 및 해결 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="bf92f-171">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 [<span data-ttu-id="bf92f-172">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="bf92f-172">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
