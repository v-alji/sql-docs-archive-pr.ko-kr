---
title: 유사한 데이터 일치(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70dea36de557c6fda909d06ee19ff8fa2ed6908d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731795"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a><span data-ttu-id="ee54e-102">유사한 데이터 일치(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="ee54e-102">Match Similar Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="ee54e-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 DQS(Data Quality Services) 기능을 사용하여 데이터의 유사성을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use Data Quality Services (DQS) functionality to find similarities in your data.</span></span>  
  
 <span data-ttu-id="ee54e-104">이 절차를 수행하기 위해 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-104">To perform this procedure, you can:</span></span>  
  
-   <span data-ttu-id="ee54e-105">기본 Data Quality Services 기술 자료를 사용합니다. 또는</span><span class="sxs-lookup"><span data-stu-id="ee54e-105">Use the default Data Quality Services knowledge base, or</span></span>  
  
-   <span data-ttu-id="ee54e-106">고유의 사용자 지정 DQS 기술 자료 및 일치 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-106">Create your own custom DQS knowledge base and matching policy.</span></span> <span data-ttu-id="ee54e-107">자세한 내용은 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee54e-107">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ee54e-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ee54e-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="ee54e-109">MDS 관리 데이터가 포함된 워크시트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-109">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="ee54e-110">자세한 내용은 [MDS에서 Excel로 데이터 로드](export-data-to-excel-from-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ee54e-110">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="ee54e-111">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-111">Optional.</span></span> <span data-ttu-id="ee54e-112">유사성을 검사하기 전에 다른 데이터와 MDS 관리 데이터를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-112">You can combine other data with the MDS-managed data before checking for similarities.</span></span> <span data-ttu-id="ee54e-113">자세한 내용은 [데이터 결합&#40;Excel용 MDS 추가 기능&#41;](combine-data-mds-add-in-for-excel.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee54e-113">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a><span data-ttu-id="ee54e-114">기본 기술 자료를 사용하여 유사성을 찾으려면</span><span class="sxs-lookup"><span data-stu-id="ee54e-114">To find similarities by using the default knowledge base</span></span>  
  
1.  <span data-ttu-id="ee54e-115">MDS 관리 데이터가 포함된 워크시트의 **데이터 품질** 그룹에서 **데이터 일치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-115">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="ee54e-116">**데이터 일치** 대화 상자의 **DQS 기술 자료** 목록에서 **DQS 데이터(기본값)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-116">In the **Match Data** dialog box, from the **DQS Knowledge Base** list, select **DQS Data (default)**.</span></span>  
  
3.  <span data-ttu-id="ee54e-117">대화 상자에서 일치시킬 데이터가 포함된 각 열에 대해 행을 하나씩 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-117">For each column that contains data you want to match, add a row in the dialog box.</span></span> <span data-ttu-id="ee54e-118">이 대화 상자의 필드에 대한 자세한 내용은 [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee54e-118">For information about the fields in this dialog box, see [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).</span></span>  
  
4.  <span data-ttu-id="ee54e-119">모든 가중치 값의 합계가 100%이면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-119">When the total of all weight values equals 100 percent, click **OK**.</span></span>  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a><span data-ttu-id="ee54e-120">사용자 지정 기술 자료를 사용하여 유사성을 찾으려면</span><span class="sxs-lookup"><span data-stu-id="ee54e-120">To find similarities by using a custom knowledge base</span></span>  
  
1.  <span data-ttu-id="ee54e-121">MDS 관리 데이터가 포함된 워크시트의 **데이터 품질** 그룹에서 **데이터 일치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-121">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="ee54e-122">**DQS 기술 자료** 목록에서 사용자 지정 기술 자료의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-122">From the **DQS Knowledge Base** list, select the name of your custom knowledge base.</span></span>  
  
3.  <span data-ttu-id="ee54e-123">워크시트의 각 열에 대해 DQS 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-123">For each column in the worksheet, select a DQS domain.</span></span>  
  
4.  <span data-ttu-id="ee54e-124">모든 DQS 도메인을 워크시트의 열에 매핑했으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-124">When all DQS domains are mapped to columns in the worksheet, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee54e-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ee54e-125">Next Steps</span></span>  
  
-   <span data-ttu-id="ee54e-126">추가 정보를 보고 어떤 데이터가 비슷한지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee54e-126">View additional information to determine which data is similar.</span></span> <span data-ttu-id="ee54e-127">자세한 내용은 [데이터 품질 일치 열&#40;Excel용 MDS 추가 기능&#41;](data-quality-matching-columns-mds-add-in-for-excel.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee54e-127">For more information, see [Data Quality Matching Columns &#40;MDS Add-in for Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee54e-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee54e-128">See Also</span></span>  
 <span data-ttu-id="ee54e-129">[Excel용 MDS 추가 기능의 데이터 품질 일치](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ee54e-129">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="ee54e-130">데이터 일치</span><span class="sxs-lookup"><span data-stu-id="ee54e-130">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
