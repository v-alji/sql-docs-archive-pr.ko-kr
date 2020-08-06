---
title: 데이터 새로 고침(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 49b6e7bc19c41911c626965b9d1de132796367f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741112"
---
# <a name="refreshing-data-mds-add-in-for-excel"></a><span data-ttu-id="3db3d-102">데이터 새로 고침(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="3db3d-102">Refreshing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="3db3d-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 데이터를 새로 고쳐 새 워크시트를 열지 않고도 MDS 리포지토리에서 최신 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], refresh data when you want to get the latest information from the MDS repository without opening a new worksheet.</span></span> <span data-ttu-id="3db3d-104">모든 셀이나 선택한 셀을 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-104">You can refresh either all cells or a selection of cells.</span></span> <span data-ttu-id="3db3d-105">이 방법은 사용자 지정 수식이나 MDS에서 관리되지 않는 기타 데이터가 포함된 열을 삽입했으며 이를 보존하려는 경우에 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-105">This can be useful when you have inserted columns with custom formulas or other data that is not managed in MDS and you want to preserve it.</span></span>  
  
## <a name="when-you-can-refresh-mds-managed-data"></a><span data-ttu-id="3db3d-106">MDS 관리 데이터를 새로 고칠 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="3db3d-106">When You Can Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="3db3d-107">활성 워크시트에 MDS 관리 데이터가 이미 포함된 경우 활성 워크시트에서 MDS 관리 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-107">You can refresh MDS-managed data in an active worksheet if the active worksheet already contains MDS-managed data.</span></span> <span data-ttu-id="3db3d-108">워크시트에 멤버를 추가했거나 특성 값을 변경한 경우 변경 내용을 새로 고치려면 먼저 변경 내용을 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-108">If you have changed attribute values or added members to the worksheet, you must publish your changes before you can refresh.</span></span>  
  
## <a name="refreshing-a-selection"></a><span data-ttu-id="3db3d-109">선택한 내용 새로 고침</span><span class="sxs-lookup"><span data-stu-id="3db3d-109">Refreshing a Selection</span></span>  
 <span data-ttu-id="3db3d-110">모든 셀을 새로 고칠 수도 있고 선택한 셀만 새로 고칠 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-110">You have the choice of refreshing all cells or refreshing only selected cells.</span></span> <span data-ttu-id="3db3d-111">연속된 셀을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-111">The selected cells must be contiguous.</span></span> <span data-ttu-id="3db3d-112">연속된 셀 집합을 선택하면 서버에 현재 저장된 값을 표시하도록 해당 집합의 모든 MDS 관리 셀이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-112">If a set of contiguous cells is selected, all MDS managed cells in that set will be updated to display the values currently stored on the server.</span></span> <span data-ttu-id="3db3d-113">MDS로 관리되지 않는 변경되지 않은 행과 열은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-113">Unchanged rows and columns that are not managed by MDS are not affected in any way.</span></span>  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a><span data-ttu-id="3db3d-114">MDS 관리 데이터를 새로 고치는 경우 수행되는 작업</span><span class="sxs-lookup"><span data-stu-id="3db3d-114">What Happens When You Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="3db3d-115">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 데이터를 새로 고칠 때 시트의 MDS 관리 데이터에 대해 수행되는 작업은 마지막으로 데이터를 로드한 후 MDS 리포지토리에서 변경된 내용에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-115">When you refresh data in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], what happens to the MDS-managed data in the sheet depends on what has changed in the MDS repository since you last loaded the data.</span></span>  
  
-   <span data-ttu-id="3db3d-116">새 멤버가 저장소에 추가된 경우 워크시트의 끝에 추가되고 녹색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-116">If new members have been added to repository, they are added to the end of the worksheet and are highlighted in green.</span></span>  
  
-   <span data-ttu-id="3db3d-117">멤버가 저장소에서 삭제된 경우 워크시트에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-117">If members were deleted from the repository, they are deleted from the worksheet.</span></span>  
  
-   <span data-ttu-id="3db3d-118">MDS 저장소에서 특성 값이 변경된 경우 워크시트의 값이 MDS 저장소의 값으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-118">If an attribute value has changed in the MDS repository, the value in the worksheet is updated with value from the MDS repository.</span></span> <span data-ttu-id="3db3d-119">셀 색은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-119">The cell color does not change.</span></span>  
  
> [!WARNING]
>  -   <span data-ttu-id="3db3d-120">활성 워크시트에서 관리되지 않는 데이터가 MDS 관리 데이터 아래의 행에 있으면 관리되지 않는 데이터를 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-120">In the active worksheet, if non-managed data exists in rows beneath the MDS-managed data, the non-managed data may be overwritten.</span></span> <span data-ttu-id="3db3d-121">이 경우는 시트를 새로 고치고 관리되지 않는 데이터와 겹치는 MDS 관리 데이터의 새 행이 추가될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-121">This occurs when you refresh the sheet and new rows of MDS-managed data, which overlap with the non-managed data, are added.</span></span>  
> -   <span data-ttu-id="3db3d-122">게시하면 MDS 관리 셀에 대한 주석이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-122">When you refresh, comments on MDS-managed cells are deleted.</span></span>  
  
## <a name="how-to-refresh-mds-managed-data"></a><span data-ttu-id="3db3d-123">MDS 관리 데이터를 새로 고치는 방법</span><span class="sxs-lookup"><span data-stu-id="3db3d-123">How to Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="3db3d-124">리본의 **연결 및 로드** 그룹에서 **새로 고침** 단추에는 **모두 새로 고침** 및 **선택 영역 새로 고침**의 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-124">In the **Connect and Load** group on the ribbon, the **Refresh** button has two options, **Refresh All** and **Refresh Selection**.</span></span> <span data-ttu-id="3db3d-125">리본 버튼의 기본 동작은 **모두 새로 고침**입니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-125">The default action of the ribbon button is **Refresh All**.</span></span> <span data-ttu-id="3db3d-126">전체 시트를 서버 값으로 새로 고치려면 **새로 고침** 단추를 클릭하거나 **모두 새로 고침** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-126">To refresh the entire sheet with values from the server, click the **Refresh** button or choose the **Refresh All** option.</span></span> <span data-ttu-id="3db3d-127">시트에서 일부 셀만 새로 고치려면 해당 셀(하나의 연속 선택 영역이어야 함)을 선택하고 **선택 영역 새로 고침** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-127">To refresh only some of the cells in a sheet, select the cells (must be one contiguous selection) and choose the **Refresh Selection** option.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3db3d-128">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3db3d-128">Related Tasks</span></span>  
  
|<span data-ttu-id="3db3d-129">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="3db3d-129">Task Description</span></span>|<span data-ttu-id="3db3d-130">항목</span><span class="sxs-lookup"><span data-stu-id="3db3d-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="3db3d-131">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-131">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="3db3d-132">MDS 리포지토리에 연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="3db3d-132">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="3db3d-133">MDS 데이터를 Excel로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3db3d-133">Load MDS data into Excel.</span></span>|[<span data-ttu-id="3db3d-134">MDS에서 Excel로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="3db3d-134">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="3db3d-135">관련 내용</span><span class="sxs-lookup"><span data-stu-id="3db3d-135">Related Content</span></span>  
  
-   [<span data-ttu-id="3db3d-136">연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="3db3d-136">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="3db3d-137">데이터 &#40;Excel용 MDS 추가 기능&#41;로드</span><span class="sxs-lookup"><span data-stu-id="3db3d-137">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="3db3d-138">Microsoft Excel용 Master Data Services 추가 기능</span><span class="sxs-lookup"><span data-stu-id="3db3d-138">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
