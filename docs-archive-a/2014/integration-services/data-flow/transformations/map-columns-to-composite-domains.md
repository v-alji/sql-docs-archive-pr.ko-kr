---
title: 복합 도메인에 열 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a665b2096579c9da35a1b69be46c4ba6103610f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659560"
---
# <a name="map-columns-to-composite-domains"></a><span data-ttu-id="12c7c-102">복합 도메인에 열 매핑</span><span class="sxs-lookup"><span data-stu-id="12c7c-102">Map Columns to Composite Domains</span></span>
  <span data-ttu-id="12c7c-103">복합 도메인은 둘 이상의 단일 도메인으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-103">A composite domain consists of two or more single domains.</span></span> <span data-ttu-id="12c7c-104">여러 개의 열을 이 도메인에 매핑하거나 구분된 값이 포함된 단일 열을 이 도메인에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-104">You can map multiple columns to the domain, or you can map a single column with delimited values to the domain.</span></span>  
  
 <span data-ttu-id="12c7c-105">열이 여러 개 있는 경우 각 열을 복합 도메인의 각 단일 도메인에 매핑하여 데이터 정리에 복합 도메인 규칙을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-105">When you have multiple columns, you must map a column to each single domain in the composite domain to apply the composite domain rules to data cleansing.</span></span> <span data-ttu-id="12c7c-106">Data Quality 클라이언트에서 복합 도메인에 포함된 단일 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-106">You select the single domains contained in the composite domain, in the Data Quality Client.</span></span> <span data-ttu-id="12c7c-107">자세한 내용은 [복합 도메인 만들기](../../../data-quality-services/create-a-composite-domain.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12c7c-107">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="12c7c-108">구분된 값을 가진 단일 열이 있으면 이 단일 열을 복합 도메인에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-108">When you have a single column with delimited values, you must map the single column to the composite domain.</span></span> <span data-ttu-id="12c7c-109">값은 단일 도메인이 복합 도메인에 나타나는 순서와 동일한 순서로 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-109">The values must appear in the same order as the single domains appear in the composite domain.</span></span> <span data-ttu-id="12c7c-110">데이터 원본의 구분 기호는 복합 도메인 값을 구문 분석하는 데 사용되는 구분 기호와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-110">The delimiter in the data source must match the delimiter that is used to parse the composite domain values.</span></span> <span data-ttu-id="12c7c-111">Data Quality 클라이언트에서 복합 도메인의 구분 기호를 선택하고 다른 속성도 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-111">You select the delimiter for the composite domain, as well as set other properties, in the Data Quality Client.</span></span> <span data-ttu-id="12c7c-112">자세한 내용은 [복합 도메인 만들기](../../../data-quality-services/create-a-composite-domain.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12c7c-112">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a><span data-ttu-id="12c7c-113">여러 개의 열을 복합 도메인에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="12c7c-113">To map multiple columns to a composite domain</span></span>  
  
1.  <span data-ttu-id="12c7c-114">DQS 정리 변환을 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-114">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="12c7c-115">**연결 관리자** 탭에서 복합 도메인이 사용 가능한 도메인 목록에 나타나는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-115">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="12c7c-116">**매핑** 탭의 **사용 가능한 입력 열** 영역에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-116">On the **Mapping** tab, select the columns in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="12c7c-117">**입력 열** 필드의 각 열에 대해 **도메인** 필드에서 단일 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-117">For each column listed in the **Input Column** field, select a single domain in the **Domain** field.</span></span> <span data-ttu-id="12c7c-118">복합 도메인에 속해 있는 단일 도메인만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-118">Select only single domains that are in the composite domain.</span></span>  
  
5.  <span data-ttu-id="12c7c-119">필요에 따라 **원본 별칭**, **출력 별칭**및 **상태 별칭** 필드에 나타나는 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-119">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="12c7c-120">필요에 따라 **고급** 탭에서 속성을 설정합니다. 속성에 대한 자세한 내용은 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12c7c-120">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a><span data-ttu-id="12c7c-121">구분된 값을 가진 열을 복합 도메인에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="12c7c-121">To map a column with delimited values to a composite domain</span></span>  
  
1.  <span data-ttu-id="12c7c-122">DQS 정리 변환을 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-122">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="12c7c-123">**연결 관리자** 탭에서 복합 도메인이 사용 가능한 도메인 목록에 나타나는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-123">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="12c7c-124">**매핑** 탭의 **사용 가능한 입력 열** 영역에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-124">On the **Mapping** tab, select the column in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="12c7c-125">**입력 열** 필드의 열에 대해 **도메인** 필드에서 복합 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-125">For the column listed in the **Input Column** field, select the composite domain in the **Domain** field.</span></span>  
  
5.  <span data-ttu-id="12c7c-126">필요에 따라 **원본 별칭**, **출력 별칭**및 **상태 별칭** 필드에 나타나는 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="12c7c-126">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="12c7c-127">필요에 따라 **고급** 탭에서 속성을 설정합니다. 속성에 대한 자세한 내용은 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12c7c-127">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c7c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12c7c-128">See Also</span></span>  
 [<span data-ttu-id="12c7c-129">DQS 정리 변환</span><span class="sxs-lookup"><span data-stu-id="12c7c-129">DQS Cleansing Transformation</span></span>](dqs-cleansing-transformation.md)  
  
  
