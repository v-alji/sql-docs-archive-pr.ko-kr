---
title: Excel용 MDS 추가 기능의 데이터 품질 일치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 037e535452e7f19644837e0cbcfd02efec5422b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659503"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a><span data-ttu-id="afc42-102">Excel용 MDS 추가 기능의 데이터 품질 일치</span><span class="sxs-lookup"><span data-stu-id="afc42-102">Data Quality Matching in the MDS Add-in for Excel</span></span>
  <span data-ttu-id="afc42-103">시간이 지날수록 MDS 저장소에 추가하는 데이터가 늘어나게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="afc42-104">데이터를 추가하기 전에 새 데이터와 MDS에서 관리되는 기존 데이터를 비교하면 중복되거나 정확하지 않은 데이터가 추가되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure you are not adding duplicate or inaccurate data.</span></span>  
  
 <span data-ttu-id="afc42-105">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 DQS(Data Quality Services)를 사용하여 비슷한 데이터를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-105">The MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] uses the Data Quality Services (DQS) feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to match data that's similar.</span></span> <span data-ttu-id="afc42-106">추가 기능에 포함된 일치 기능을 사용하면 비슷한 레코드가 그룹화되고 결과의 정확성을 보여 주는 점수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-106">When you use the matching functionality in the Add-in, similar records are grouped together and a score that represents the accuracy of the result is displayed.</span></span> <span data-ttu-id="afc42-107">DQS가 제공하는 일치 기능에 대한 자세한 내용은 [Data Matching](../../data-quality-services/data-matching.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="afc42-107">For more information about the matching functionality provided by DQS, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
## <a name="workflow-for-data-quality-matching"></a><span data-ttu-id="afc42-108">데이터 품질 일치 워크플로</span><span class="sxs-lookup"><span data-stu-id="afc42-108">Workflow for Data Quality Matching</span></span>  
 <span data-ttu-id="afc42-109">DQS를 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]와 함께 사용하는 경우 다음 워크플로를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="afc42-109">When using DQS with the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use the following workflow:</span></span>  
  
1.  <span data-ttu-id="afc42-110">MDS 관리 데이터 목록을 검색하여 MDS에서 관리되지 않는 목록과 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-110">Retrieve a list of MDS-managed data and combine it with a list that is not managed in MDS.</span></span> <span data-ttu-id="afc42-111">자세한 내용은 [데이터 결합&#40;Excel용 MDS 추가 기능&#41;](combine-data-mds-add-in-for-excel.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="afc42-111">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="afc42-112">DQS 기술 자료를 사용하여 결합된 목록의 데이터를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-112">Use DQS knowledge to compare the data in the combined list.</span></span> <span data-ttu-id="afc42-113">자세한 내용은 [유사한 데이터 일치&#40;Excel용 MDS 추가 기능&#41;](match-similar-data-mds-add-in-for-excel.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="afc42-113">For more information, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
3.  <span data-ttu-id="afc42-114">DQS가 발견한 유사성에 대한 자세한 정보를 보려면 세부 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-114">To view more details about the similarities found by DQS, show the detail columns.</span></span>  
  
4.  <span data-ttu-id="afc42-115">결과를 모두 이동해 MDS 저장소에 추가되어야 하는 데이터와 중복된 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-115">Go through the results and determine which data should be added to the MDS repository and which data is duplicated.</span></span>  
  
5.  <span data-ttu-id="afc42-116">새 데이터 및/또는 업데이트된 데이터를 MDS 저장소에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-116">Publish the new and/or updated data to the MDS repository.</span></span>  
  
## <a name="knowledge-bases"></a><span data-ttu-id="afc42-117">기술 자료</span><span class="sxs-lookup"><span data-stu-id="afc42-117">Knowledge Bases</span></span>  
 <span data-ttu-id="afc42-118">추가 기능에 제공되는 일치 결과는 DQS 기술 자료를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-118">The matching results provided in the Add-in are based on a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="afc42-119">기본 기술 자료(DQS 데이터)는 DQS를 설치할 때 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-119">The default knowledge base (DQS Data) is created when DQS is installed.</span></span> <span data-ttu-id="afc42-120">Data Quality 클라이언트의 기본 기술 자료에 일치 정책을 추가하지 않고 기본 기술 자료를 사용하기로 선택할 경우 워크시트의 열을 기술 자료의 도메인에 매핑한 다음 선택한 도메인에 가중치 값을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-120">If you choose to use the default knowledge base (without adding a matching policy to the default knowledge base in the Data Quality Client), you must map columns in the worksheet to domains in the knowledge base, and then assign a weight value to the domains you choose.</span></span>  
  
-   <span data-ttu-id="afc42-121">Data Quality 클라이언트를 사용하여 일치 정책을 포함한 새 기술 자료를 만들거나, 기본 기술 자료에 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-121">You can use the Data Quality Client to create a new knowledge base with a matching policy, or to add a matching policy to the default knowledge base.</span></span> <span data-ttu-id="afc42-122">이 경우 가중치 값은 이미 만들어 둔 일치 정책에 따라 결정되므로 도메인에 열을 매핑하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-122">In this case, the weight values are determined by the matching policy you already created and you need only to map the columns to the domains.</span></span> <span data-ttu-id="afc42-123">자세한 내용은 [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afc42-123">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
 <span data-ttu-id="afc42-124">기술 자료에 대한 자세한 내용은 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="afc42-124">For more information about knowledge bases, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="afc42-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="afc42-125">Related Tasks</span></span>  
  
|<span data-ttu-id="afc42-126">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="afc42-126">Task Description</span></span>|<span data-ttu-id="afc42-127">항목</span><span class="sxs-lookup"><span data-stu-id="afc42-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="afc42-128">외부 데이터와 MDS 관리 데이터를 비교하기 전에 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-128">Combine external data with MDS-managed data in preparation to compare it.</span></span>|[<span data-ttu-id="afc42-129">데이터 결합&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="afc42-129">Combine Data &#40;MDS Add-in for Excel&#41;</span></span>](combine-data-mds-add-in-for-excel.md)|  
|<span data-ttu-id="afc42-130">DQS 기술 자료를 사용하여 데이터의 유사성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="afc42-130">Use DQS knowledge to find similarities in your data.</span></span>|[<span data-ttu-id="afc42-131">유사한 데이터 일치&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="afc42-131">Match Similar Data &#40;MDS Add-in for Excel&#41;</span></span>](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="afc42-132">관련 내용</span><span class="sxs-lookup"><span data-stu-id="afc42-132">Related Content</span></span>  
  
-   [<span data-ttu-id="afc42-133">데이터 &#40;Excel용 MDS 추가 기능&#41;게시</span><span class="sxs-lookup"><span data-stu-id="afc42-133">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="afc42-134">데이터 일치</span><span class="sxs-lookup"><span data-stu-id="afc42-134">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
