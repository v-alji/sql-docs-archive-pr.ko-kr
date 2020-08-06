---
title: 병합 조인 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0d15d1233c2e0ff836e9dbd17459e56c48183f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652201"
---
# <a name="merge-join-transformation-editor"></a><span data-ttu-id="a194a-102">병합 조인 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="a194a-102">Merge Join Transformation Editor</span></span>
  <span data-ttu-id="a194a-103">**병합 조인 변환 편집기** 대화 상자를 사용하여 조인 유형, 조인 열 및 조인으로 결합된 두 입력을 병합하기 위한 출력 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-103">Use the **Merge Join Transformation Editor** dialog box to specify the join type, the join columns, and the output columns for merging two inputs combined by a join.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a194a-104">병합 조인 변환에는 정렬된 데이터를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-104">The Merge Join Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="a194a-105">이러한 중요 요구 사항에 대한 자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a194a-105">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="a194a-106">병합 조인 변환에 대한 자세한 내용은 [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a194a-106">To learn more about the Merge Join transformation, see [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a194a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="a194a-107">Options</span></span>  
 <span data-ttu-id="a194a-108">**조인 유형**</span><span class="sxs-lookup"><span data-stu-id="a194a-108">**Join type**</span></span>  
 <span data-ttu-id="a194a-109">내부 조인, 왼쪽 우선 외부 조인 또는 완전 조인을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-109">Specify whether you want to use an inner join, left outer join, or full join.</span></span>  
  
 <span data-ttu-id="a194a-110">**입력 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="a194a-110">**Swap Inputs**</span></span>  
 <span data-ttu-id="a194a-111">**입력 바꾸기** 단추를 사용하여 입력 간에 순서를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-111">Switch the order between inputs by using the **Swap Inputs** button.</span></span> <span data-ttu-id="a194a-112">왼쪽 우선 외부 조인 옵션과 함께 사용하면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-112">This selection may be useful with the Left outer join option.</span></span>  
  
 <span data-ttu-id="a194a-113">**입력**</span><span class="sxs-lookup"><span data-stu-id="a194a-113">**Input**</span></span>  
 <span data-ttu-id="a194a-114">먼저 사용 가능한 입력 목록에서 병합된 출력에 포함할 각 열에 대한 입력을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-114">For each column that you want in the merged output, first select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="a194a-115">입력은 별도의 두 테이블에 따로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-115">Inputs are displayed in two separate tables.</span></span> <span data-ttu-id="a194a-116">출력에 포함할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-116">Select columns to include in the output.</span></span> <span data-ttu-id="a194a-117">열을 끌어 테이블 간에 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-117">Drag columns to create a join between the tables.</span></span> <span data-ttu-id="a194a-118">조인을 삭제하려면 조인을 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-118">To delete a join, select it and then press the DELETE key.</span></span>  
  
 <span data-ttu-id="a194a-119">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="a194a-119">**Input Column**</span></span>  
 <span data-ttu-id="a194a-120">선택한 입력의 사용 가능한 열 목록에서 병합 출력에 포함할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-120">Select a column to include in the merged output from the list of available columns on the selected input.</span></span>  
  
 <span data-ttu-id="a194a-121">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="a194a-121">**Output Alias**</span></span>  
 <span data-ttu-id="a194a-122">각 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-122">Type an alias for each output column.</span></span> <span data-ttu-id="a194a-123">기본값은 입력 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a194a-123">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a194a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a194a-124">See Also</span></span>  
 <span data-ttu-id="a194a-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a194a-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a194a-126">[병합 및 병합 조인 변환에 대 한 데이터 정렬](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a194a-126">[Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span></span>  
 <span data-ttu-id="a194a-127">[병합 조인 변환을 사용 하 여 데이터 집합 확장](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a194a-127">[Extend a Dataset by Using the Merge Join Transformation](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span></span>  
 <span data-ttu-id="a194a-128">[병합 변환](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a194a-128">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="a194a-129">UNION ALL 변환</span><span class="sxs-lookup"><span data-stu-id="a194a-129">Union All Transformation</span></span>](data-flow/transformations/union-all-transformation.md)  
  
  
