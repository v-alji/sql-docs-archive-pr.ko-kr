---
title: 데이터 결합(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc2d5bffb6d7a12164a8643e9a790b32538f8979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730799"
---
# <a name="combine-data-mds-add-in-for-excel"></a><span data-ttu-id="a4ef6-102">데이터 결합(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="a4ef6-102">Combine Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a4ef6-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 두 워크시트의 데이터를 결합하여 데이터를 게시하기 전에 둘을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combine data from two worksheets when you want to compare data before publishing.</span></span> <span data-ttu-id="a4ef6-104">이 절차에서는 두 워크시트의 데이터를 한 워크시트에 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-104">In this procedure, you combine data from a two worksheets into one.</span></span> <span data-ttu-id="a4ef6-105">그런 다음 추가 비교를 수행하여 MDS 저장소에 게시할 데이터를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-105">Then you can perform further comparisons and determine which data, if any, to publish to the MDS repository.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a4ef6-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="a4ef6-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="a4ef6-107">MDS 관리 데이터가 포함된 워크시트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-107">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="a4ef6-108">자세한 내용은 [MDS에서 Excel로 데이터 로드](export-data-to-excel-from-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-108">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a4ef6-109">MDS 관리 데이터와 결합할 데이터가 포함된 워크시트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-109">You must have a worksheet that contains data you want to combine with MDS-managed data.</span></span> <span data-ttu-id="a4ef6-110">이 시트에는 머리글 행이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-110">This sheet must have a header row.</span></span>  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a><span data-ttu-id="a4ef6-111">관리되지 않는 데이터를 MDS 관리 시트에 결합하려면</span><span class="sxs-lookup"><span data-stu-id="a4ef6-111">To combine non-managed data into an MDS-managed sheet</span></span>  
  
1.  <span data-ttu-id="a4ef6-112">MDS 관리 데이터가 포함된 시트의 **게시 및 유효성 검사** 그룹에서 **데이터 결합**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-112">On the sheet that contains MDS-managed data, in the **Publish and Validate** group, click **Combine Data**.</span></span>  
  
2.  <span data-ttu-id="a4ef6-113">**데이터 결합** 대화 상자에서 **MDS 데이터와 결합할 범위** 입력란 옆에 있는 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-113">In the **Combine Data** dialog box, next to the **Range to combine with MDS data** text box, click the icon.</span></span> <span data-ttu-id="a4ef6-114">대화 상자가 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-114">The dialog box contracts.</span></span>  
  
3.  <span data-ttu-id="a4ef6-115">결합할 데이터가 포함된 시트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-115">Click the sheet that contains the data you want to combine.</span></span>  
  
4.  <span data-ttu-id="a4ef6-116">머리글 행을 포함하여 결합할 시트에 있는 모든 셀을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-116">Highlight all cells on the sheet that you want to combine, including the header row.</span></span>  
  
5.  <span data-ttu-id="a4ef6-117">**데이터 결합** 대화 상자에서 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-117">In the **Combine Data** dialog box, click the icon.</span></span> <span data-ttu-id="a4ef6-118">대화 상자가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-118">The dialog box expands.</span></span>  
  
6.  <span data-ttu-id="a4ef6-119">MDS 엔터티에 대해 나열된 열에 대해 **해당 열**아래의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-119">For a column listed for the MDS entity, select a column under **Corresponding Column**.</span></span> <span data-ttu-id="a4ef6-120">모든 MDS 열에 해당 열이 필요하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-120">All MDS columns do not need corresponding columns.</span></span>  
  
7.  <span data-ttu-id="a4ef6-121">**결합**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-121">Click **Combine**.</span></span> <span data-ttu-id="a4ef6-122">데이터가 MDS의 데이터인지 외부 원본에서 가져온 데이터인지를 나타내는 **원본** 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-122">A **SOURCE** column is displayed, indicating whether the data is from MDS or an external source.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a4ef6-123">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a4ef6-123">Next Steps</span></span>  
  
-   <span data-ttu-id="a4ef6-124">MDS 관리 데이터와 외부 데이터 간의 유사성을 찾으려면 [유사한 데이터 일치&#40;Excel용 MDS 추가 기능&#41;](match-similar-data-mds-add-in-for-excel.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a4ef6-124">To find similarities between the MDS-managed and external data, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ef6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4ef6-125">See Also</span></span>  
 <span data-ttu-id="a4ef6-126">[데이터 &#40;Excel용 MDS 추가 기능&#41;로드](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="a4ef6-126">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="a4ef6-127">Excel용 MDS 추가 기능의 데이터 품질 일치</span><span class="sxs-lookup"><span data-stu-id="a4ef6-127">Data Quality Matching in the MDS Add-in for Excel</span></span>](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
