---
title: 데이터 로드 (Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c01bbbc90fcc68c3de976332721b69ad26e606e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660643"
---
# <a name="loading-data-mds-add-in-for-excel"></a><span data-ttu-id="a2268-102">데이터 로드(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="a2268-102">Loading Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a2268-103">에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 사용 하려면 먼저 MDS 저장소에서 활성 Excel 워크시트로 데이터를 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository into an active Excel worksheet before you can work with it.</span></span> <span data-ttu-id="a2268-104">데이터 사용을 마쳤으면 다른 사용자가 공유할 수 있도록 다시 MDS 저장소에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-104">When you are done working with the data, publish it to the MDS repository so other users can share it.</span></span>  
  
 <span data-ttu-id="a2268-105">로드할 수 있는 데이터는 액세스할 수 있는 권한이 있는 데이터로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-105">The data you can load is limited to the data you have permission to access.</span></span> <span data-ttu-id="a2268-106">데이터 액세스 권한은 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션에 설정되거나 프로그래밍 방식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-106">Permission to access data is set in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or set programmatically.</span></span>  
  
 <span data-ttu-id="a2268-107">많은 데이터를 로드할 때는 로드 시간이 오래 걸릴 수 있는 데이터를 로드할 때 표시되는 경고를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-107">When you load large amounts of data, you can set warnings that are displayed when the data that might take a long time to load.</span></span> <span data-ttu-id="a2268-108">이렇게 하려면 **옵션** 그룹에서 **설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-108">To do this, in the **Options** group, click **Settings**.</span></span> <span data-ttu-id="a2268-109">**데이터** 탭에서 **큰 데이터 집합에 대해 필터 경고 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-109">On the **Data** tab, select the **Display filter warning for large data sets**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a2268-110">MDS 지원 통합 문서는 Excel용 MDS 추가 기능을 사용하여 Excel에서만 열고 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-110">An MDS-enabled workbook must be opened and updated only in Excel with the MDS Add-in for Excel.</span></span> <span data-ttu-id="a2268-111">MDS 지원 통합 문서를 MDS Excel 추가 기능이 설치되지 않은 컴퓨터에서 Excel로 여는 작업은 지원되지 않으며 통합 문서 파일이 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-111">Opening an MDS-enabled workbook in Excel on a computer in which the MDS Excel Add-in is not installed is not supported, and could cause corruption of the workbook file.</span></span> <span data-ttu-id="a2268-112">데이터를 다른 사람과 공유하려면 워크시트를 저장해서 전자 메일로 보내는 대신 바로 가기 쿼리 파일을 해당 사용자에게 전자 메일로 보내십시오.</span><span class="sxs-lookup"><span data-stu-id="a2268-112">If you want to share data with someone else, email a shortcut query file to them, rather than saving the worksheet and emailing it.</span></span> <span data-ttu-id="a2268-113">쿼리에 대한 자세한 내용은 [바로 가기 쿼리 파일을 메일로 보내기&#40;Excel용 MDS 추가 기능&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2268-113">For more information on the query, see [Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).</span></span>  
  
## <a name="filtering-data"></a><span data-ttu-id="a2268-114">데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="a2268-114">Filtering Data</span></span>  
 <span data-ttu-id="a2268-115">로드 하기 전에 데이터를 필터링 하 여 다운로드할 데이터 양을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-115">You can filter data before loading to limit the amount of data that you're going to download.</span></span> <span data-ttu-id="a2268-116">여기에는 로드하려는 특성(열) 선택, 특성을 표시할 순서 및 사용하려는 멤버(데이터 행)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-116">This includes choosing which attributes (columns) you want to load, the order you want to display the attributes, and the members (rows of data) you want to work with.</span></span> <span data-ttu-id="a2268-117">자세한 내용은 [&#40;Excel용 MDS 추가 기능&#41;를 로드 하기 전에 데이터 필터링 ](filter-data-before-exporting-mds-add-in-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2268-117">For more info see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="a2268-118">자동으로 연결 및 자주 사용되는 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="a2268-118">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="a2268-119">항상 동일한 서버에 연결하고 동일한 데이터 집합을 로드하려는 경우 연결 및 필터 정보를 포함하는 바로 가기 쿼리 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-119">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="a2268-120">쿼리 파일에 대한 자세한 내용은 [바로 가기 쿼리 파일&#40;Excel용 MDS 추가 기능&#41;](shortcut-query-files-mds-add-in-for-excel.md)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-120">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="refreshing-data"></a><span data-ttu-id="a2268-121">데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="a2268-121">Refreshing Data</span></span>  
 <span data-ttu-id="a2268-122">로드한 후에는 MDS 저장소의 데이터를 다른 사용자가 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-122">Data in the MDS repository may be updated by other users after you load it.</span></span> <span data-ttu-id="a2268-123">MDS 이외의 데이터에 대해 변경한 내용을 손실하지 않고 이 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-123">You can retrieve this data without losing changes you've made to non-MDS data.</span></span> <span data-ttu-id="a2268-124">자세한 내용은 [데이터 새로 고침&#40;Excel용 MDS 추가 기능&#41;](refreshing-data-mds-add-in-for-excel.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2268-124">For more information, see [Refreshing Data &#40;MDS Add-in for Excel&#41;](refreshing-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a2268-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a2268-125">Related Tasks</span></span>  
  
|<span data-ttu-id="a2268-126">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="a2268-126">Task Description</span></span>|<span data-ttu-id="a2268-127">항목</span><span class="sxs-lookup"><span data-stu-id="a2268-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="a2268-128">MDS 데이터를 Excel에 로드하기 전에 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-128">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="a2268-129">&#40;Excel용 MDS 추가 기능를 로드 하기 전에 데이터를 필터링&#41;</span><span class="sxs-lookup"><span data-stu-id="a2268-129">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|<span data-ttu-id="a2268-130">MDS 데이터를 Excel로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-130">Load MDS data into Excel.</span></span>|[<span data-ttu-id="a2268-131">MDS에서 Excel로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="a2268-131">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="a2268-132">데이터를 다운로드하기 전에 열 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a2268-132">Change the order of columns before you download data.</span></span>|[<span data-ttu-id="a2268-133">열 순서 바꾸기&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="a2268-133">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="a2268-134">관련 내용</span><span class="sxs-lookup"><span data-stu-id="a2268-134">Related Content</span></span>  
  
-   [<span data-ttu-id="a2268-135">연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="a2268-135">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="a2268-136">바로 가기 쿼리 파일&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="a2268-136">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="a2268-137">Microsoft Excel용 Master Data Services 추가 기능</span><span class="sxs-lookup"><span data-stu-id="a2268-137">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="a2268-138">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a2268-138">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
