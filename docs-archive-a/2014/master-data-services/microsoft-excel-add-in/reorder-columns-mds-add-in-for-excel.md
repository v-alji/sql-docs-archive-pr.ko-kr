---
title: 열 순서 바꾸기(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f0c47a631ffe699936a8d45bcc4e47e0b6f0a985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730791"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a><span data-ttu-id="26201-102">열 순서 바꾸기(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="26201-102">Reorder Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="26201-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 로드하기 전에 목록을 필터링하여 열의 순서를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26201-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you can reorder columns by filtering the list before loading.</span></span>  
  
 <span data-ttu-id="26201-104">**필터** 대화 상자에서 특성의 순서를 조정하면 데이터가 새 순서로 Excel에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="26201-104">When you reorder attributes in the **Filter** dialog box, the data is loaded into Excel with the new order.</span></span> <span data-ttu-id="26201-105">하지만 다음에 특성 데이터를 필터링하면 순서가 원래 디자인된 순서로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="26201-105">However, the next time that you filter the attribute data, the order will revert to the order in the original design.</span></span> <span data-ttu-id="26201-106">순서를 영구적으로 변경하려면 관리자가 마스터 데이터 관리자의 **시스템 관리** 영역에서 순서를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-106">To change the order permanently, an administrator should change the order in the **System Administration** area of Master Data Manager.</span></span> <span data-ttu-id="26201-107">자세한 내용은 [Change the Order of Attributes](../change-the-order-of-attributes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26201-107">For more information, see [Change the Order of Attributes](../change-the-order-of-attributes.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26201-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="26201-108">Prerequisites</span></span>  
 <span data-ttu-id="26201-109">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="26201-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="26201-110">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-110">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-reorder-mds-managed-columns"></a><span data-ttu-id="26201-111">MDS 관리 열의 순서를 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="26201-111">To reorder MDS-managed columns</span></span>  
  
1.  <span data-ttu-id="26201-112">Excel을 열고 **마스터 데이터** 탭에서 MDS 저장소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-112">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="26201-113">자세한 내용은 [MDS 리포지토리에 연결&#40;Excel용 MDS 추가 기능&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26201-113">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="26201-114">**마스터 데이터 탐색기** 창에서 모델 및 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-114">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="26201-115">엔터티 목록이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="26201-115">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="26201-116">**마스터 데이터 탐색기** 창이 표시되지 않으면 **연결 및 로드** 그룹에서 **탐색기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-116">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="26201-117">**마스터 데이터 탐색기** 창이 해제되어 있으면 기존 시트에 이미 MDS 관리 데이터가 포함되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="26201-117">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="26201-118">창을 활성화하려면 새 워크시트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26201-118">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="26201-119">**마스터 데이터 탐색기** 창에서 엔터티를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-119">In the **Master Data Explorer** pane, click an entity.</span></span>  
  
4.  <span data-ttu-id="26201-120">**연결 및 로드** 그룹에서 **필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-120">In the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="26201-121">**필터** 대화 상자의 **열** 섹션에 있는 특성 목록에서 이동하려는 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-121">In the **Filter** dialog box, in the **Columns** section, in the list of attributes, click the attribute you want to move.</span></span>  
  
6.  <span data-ttu-id="26201-122">목록 오른쪽에서 **위쪽** 또는 **아래쪽** 화살표를 클릭하여 워크시트에서 특성을 왼쪽 및 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-122">To the right of the list, click the **Up** or **Down** arrow to move the attribute left and right in the worksheet.</span></span>  
  
7.  <span data-ttu-id="26201-123">워크시트에서 원하는 왼쪽-오른쪽 순서에 맞게 위쪽-아래쪽 순서가 정렬될 때까지 각 특성에 대해 7단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-123">Repeat step 7 for each attribute until the top-to-bottom order represents the left-to-right order you want in the worksheet.</span></span>  
  
8.  <span data-ttu-id="26201-124">**데이터 로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26201-124">Click **Load Data**.</span></span> <span data-ttu-id="26201-125">시트에 MDS 관리 데이터가 채워지고 사용자가 지정한 순서에 따라 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26201-125">The sheet is populated with MDS-managed data and the columns are displayed in the order you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26201-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26201-126">See Also</span></span>  
 [<span data-ttu-id="26201-127">데이터 &#40;Excel용 MDS 추가 기능&#41;로드</span><span class="sxs-lookup"><span data-stu-id="26201-127">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
