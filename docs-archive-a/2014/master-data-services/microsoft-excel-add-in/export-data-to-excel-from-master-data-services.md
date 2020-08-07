---
title: MDS에서 Excel로 데이터 로드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35672807d5bb108e9386f892aea1847d45ebeb33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731803"
---
# <a name="load-data-from-mds-into-excel"></a><span data-ttu-id="6bfa9-102">MDS에서 Excel로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="6bfa9-102">Load Data from MDS into Excel</span></span>
  <span data-ttu-id="6bfa9-103">에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 데이터를 사용 하려면 MDS 저장소에서 데이터를 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository in order to work with it.</span></span>  
  
 <span data-ttu-id="6bfa9-104">로드 하기 전에 데이터 집합을 필터링 하려는 경우에는 [&#40;Excel용 MDS 추가 기능&#41;를 로드 하기 전에 데이터 필터링](filter-data-before-exporting-mds-add-in-for-excel.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-104">If you want to filter the dataset before loading, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) instead.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6bfa9-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6bfa9-105">Prerequisites</span></span>  
 <span data-ttu-id="6bfa9-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="6bfa9-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6bfa9-107">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-load-data-from-mds-into-excel"></a><span data-ttu-id="6bfa9-108">MDS에서 Excel로 데이터를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="6bfa9-108">To load data from MDS into Excel</span></span>  
  
1.  <span data-ttu-id="6bfa9-109">Excel을 열고 **마스터 데이터** 탭에서 MDS 저장소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-109">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="6bfa9-110">자세한 내용은 [MDS 리포지토리에 연결&#40;Excel용 MDS 추가 기능&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-110">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="6bfa9-111">**마스터 데이터 탐색기** 창에서 모델 및 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-111">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="6bfa9-112">엔터티 목록이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-112">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="6bfa9-113">**마스터 데이터 탐색기** 창이 표시되지 않으면 **연결 및 로드** 그룹에서 **탐색기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-113">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="6bfa9-114">**마스터 데이터 탐색기** 창이 해제되어 있으면 기존 시트에 이미 MDS 관리 데이터가 포함되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-114">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="6bfa9-115">창을 활성화하려면 새 워크시트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-115">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="6bfa9-116">**마스터 데이터 탐색기** 창의 엔터티 목록에서 로드할 엔터티를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-116">In the **Master Data Explorer** pane, in the list of entities, double-click the entity you want to load.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="6bfa9-117">처음 100만 개의 멤버만 Excel에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-117">Only the first one million members are loaded into Excel.</span></span> <span data-ttu-id="6bfa9-118">로드하기 전에 목록을 필터링하려면 리본의 **연결 및 로드** 그룹에서 **필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-118">To filter the list before loading, on the ribbon in the **Connect and Load** group, click **Filter**.</span></span>  
    > -   <span data-ttu-id="6bfa9-119">제약된 목록(도메인 기반 특성)의 열에는 처음 25,000개의 값만 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-119">In columns that are constrained lists (domain-based attributes), only the first 25,000 values are loaded.</span></span> <span data-ttu-id="6bfa9-120">이 숫자는 Excel이 설치된 컴퓨터에 있는 excelusersettings.config 파일의 MaximumDbaEntitySize 속성에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-120">You can change this number in the MaximumDbaEntitySize property in the excelusersettings.config file located on the computer that Excel is installed on.</span></span> <span data-ttu-id="6bfa9-121">이 파일은 C:\Users \\<user \> \AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="6bfa9-121">This file is located in C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6bfa9-122">32비트 Excel에서 Microsoft Excel용 추가 기능을 사용하여 텍스트 구분 데이터를 로드하면 **로드할 셀 개** 및 **게시할 셀 개수** 속성에 대한 설정이 모두 최대값 1000으로 설정되어 메모리 부족 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-122">When you load text-delimited data using the Add-in for Microsoft Excel with 32-bit Excel, and the settings for the **Cell Count to Load** and **Cell Count to Publish** properties are both set to the maximum of 1000, an out-of-memory error will occur.</span></span> <span data-ttu-id="6bfa9-123">**로드할 셀 개수** 및 **게시할 셀 개수**에 대한 최대값 설정을 사용하려면 64비트 Excel을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bfa9-123">You have to use 64-bit Excel to use the maximum settings for **Cell Count to Load** and **Cell Count to Publish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6bfa9-124">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6bfa9-124">Next Steps</span></span>  
 [<span data-ttu-id="6bfa9-125">Excel의 데이터를 MDS &#40;Excel용 MDS 추가 기능에 게시&#41;</span><span class="sxs-lookup"><span data-stu-id="6bfa9-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="6bfa9-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bfa9-126">See Also</span></span>  
 <span data-ttu-id="6bfa9-127">[데이터 &#40;Excel용 MDS 추가 기능&#41;로드](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6bfa9-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="6bfa9-128">[필터 대화 상자 &#40;Excel용 MDS 추가 기능&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6bfa9-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="6bfa9-129">데이터 &#40;Excel용 MDS 추가 기능&#41;게시</span><span class="sxs-lookup"><span data-stu-id="6bfa9-129">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
