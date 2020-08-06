---
title: 데이터 품질 일치 열(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 939ec9727cc81ce3b206b8bc7ca3ed8dd62c3877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638872"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a><span data-ttu-id="f4a10-102">데이터 품질 일치 열(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="f4a10-102">Data Quality Matching Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="f4a10-103">에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 데이터를 일치 시킨 후 리본의 **데이터 품질** 그룹에서 **자세한 정보 표시** 를 클릭 하 여 일치 하는 세부 정보를 제공 하는 열을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.</span></span>  
  
 <span data-ttu-id="f4a10-104">다음 표에는 데이터 일치를 수행할 때 표시되는 열이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-104">The following table shows the columns that are displayed when matching data.</span></span>  
  
|<span data-ttu-id="f4a10-105">Name</span><span class="sxs-lookup"><span data-stu-id="f4a10-105">Name</span></span>|<span data-ttu-id="f4a10-106">Description</span><span class="sxs-lookup"><span data-stu-id="f4a10-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="f4a10-107">**CLUSTER_ID**</span><span class="sxs-lookup"><span data-stu-id="f4a10-107">**CLUSTER_ID**</span></span>|<span data-ttu-id="f4a10-108">비슷한 레코드를 그룹화하는 데 사용되는 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-108">A unique identifier used to group similar records.</span></span> <span data-ttu-id="f4a10-109">비슷한 행은 모두 동일한 **CLUSTER_ID**를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-109">All rows that are similar have the same **CLUSTER_ID**.</span></span> <span data-ttu-id="f4a10-110">행에 대해 **CLUSTER_ID** 가 표시되지 않으면 비슷한 레코드를 찾지 못한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-110">If no **CLUSTER_ID** is displayed for a row, then no similar records were found.</span></span>|  
|<span data-ttu-id="f4a10-111">**RECORD_ID**</span><span class="sxs-lookup"><span data-stu-id="f4a10-111">**RECORD_ID**</span></span>|<span data-ttu-id="f4a10-112">레코드를 식별하는 데 사용되는 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-112">A unique identifier used to identify records.</span></span> <span data-ttu-id="f4a10-113">MDS 저장소에 저장된 코드 값과 마찬가지로 레코드를 식별하는 데 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-113">Similar to the Code value stored in the MDS repository, it is a value used to identify a record.</span></span> <span data-ttu-id="f4a10-114">이 식별자는 일치 작업이 수행될 때마다 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-114">It is generated automatically each time matching takes place.</span></span>|  
|<span data-ttu-id="f4a10-115">**PIVOT_MARK**</span><span class="sxs-lookup"><span data-stu-id="f4a10-115">**PIVOT_MARK**</span></span>|<span data-ttu-id="f4a10-116">다른 레코드를 비교할 때 기준으로 사용되는 임의의 레코드이며 점수 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-116">An arbitrary record that other records are compared to; it does not have a score value.</span></span>|  
|<span data-ttu-id="f4a10-117">**점수**</span><span class="sxs-lookup"><span data-stu-id="f4a10-117">**SCORE**</span></span>|<span data-ttu-id="f4a10-118">그룹의 레코드가 피벗 레코드와 어느 정도나 유사한지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-118">Represents how similar the records in the group are to the pivot record.</span></span> <span data-ttu-id="f4a10-119">이 점수는 DQS에서 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-119">This score is determined by DQS.</span></span> <span data-ttu-id="f4a10-120">레코드가 다른 레코드의 피벗 레코드이거나 일치 항목을 찾을 수 없으면 점수가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a10-120">If no score is displayed, either the record is the pivot for other records, or no matches were found.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4a10-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4a10-121">See Also</span></span>  
 <span data-ttu-id="f4a10-122">[Excel용 MDS 추가 기능의 데이터 품질 일치](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f4a10-122">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="f4a10-123">[유사한 데이터 &#40;Excel용 MDS 추가 기능 일치 시킵니다&#41;](match-similar-data-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f4a10-123">[Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="f4a10-124">데이터 일치</span><span class="sxs-lookup"><span data-stu-id="f4a10-124">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
