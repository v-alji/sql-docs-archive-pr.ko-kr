---
title: 병합 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d1d35e92b5978016b6a53956e5b6f1f6642f5ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740179"
---
# <a name="merge-transformation"></a><span data-ttu-id="3ecc5-102">병합 변환</span><span class="sxs-lookup"><span data-stu-id="3ecc5-102">Merge Transformation</span></span>
  <span data-ttu-id="3ecc5-103">병합 변환은 두 개의 정렬된 데이터 세트를 단일 데이터 세트로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-103">The Merge transformation combines two sorted datasets into a single dataset.</span></span> <span data-ttu-id="3ecc5-104">각 데이터 세트의 행은 해당 키 열의 값을 기반으로 출력에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-104">The rows from each dataset are inserted into the output based on values in their key columns.</span></span>  
  
 <span data-ttu-id="3ecc5-105">데이터 흐름에 병합 변환을 포함하면 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-105">By including the Merge transformation in a data flow, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3ecc5-106">테이블 및 파일과 같은 데이터 원본 두 개의 데이터 병합</span><span class="sxs-lookup"><span data-stu-id="3ecc5-106">Merge data from two data sources, such as tables and files.</span></span>  
  
-   <span data-ttu-id="3ecc5-107">병합 변환을 중첩하여 복잡한 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-107">Create complex datasets by nesting Merge transformations.</span></span>  
  
-   <span data-ttu-id="3ecc5-108">데이터 오류를 수정한 후 행 다시 병합</span><span class="sxs-lookup"><span data-stu-id="3ecc5-108">Remerge rows after correcting errors in the data.</span></span>  
  
 <span data-ttu-id="3ecc5-109">병합 변환은 UNION ALL 변환과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-109">The Merge transformation is similar to the Union All transformations.</span></span> <span data-ttu-id="3ecc5-110">다음과 같은 경우 병합 변환 대신 UNION ALL 변환을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-110">Use the Union All transformation instead of the Merge transformation in the following situations:</span></span>  
  
-   <span data-ttu-id="3ecc5-111">변환 입력이 정렬되지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="3ecc5-111">The transformation inputs are not sorted.</span></span>  
  
-   <span data-ttu-id="3ecc5-112">결합된 출력을 정렬할 필요가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="3ecc5-112">The combined output does not need to be sorted.</span></span>  
  
-   <span data-ttu-id="3ecc5-113">변환에 둘 이상의 입력이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="3ecc5-113">The transformation has more than two inputs.</span></span>  
  
## <a name="input-requirements"></a><span data-ttu-id="3ecc5-114">입력 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3ecc5-114">Input Requirements</span></span>  
 <span data-ttu-id="3ecc5-115">병합 변환에는 정렬된 데이터를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-115">The Merge Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="3ecc5-116">이러한 중요 요구 사항에 대한 자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-116">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="3ecc5-117">또한 병합 변환에 입력한 병합된 열에는 일치하는 메타데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-117">The Merge transformation also requires that the merged columns in its inputs have matching metadata.</span></span> <span data-ttu-id="3ecc5-118">예를 들어 숫자 데이터 형식의 열을 문자 데이터 형식의 열과 병합할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-118">For example, you cannot merge a column that has a numeric data type with a column that has a character data type.</span></span> <span data-ttu-id="3ecc5-119">데이터가 문자열 데이터 형식이면 두 번째 입력의 열 길이는 함께 병합될 첫 번째 입력의 열 길이보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-119">If the data has a string data type, the length of the column in the second input must be less than or equal to the length of the column in the first input with which it is merged.</span></span>  
  
 <span data-ttu-id="3ecc5-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 병합 변환용 사용자 인터페이스는 동일한 메타데이터가 있는 열을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-120">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the user interface for the Merge transformation automatically maps columns that have the same metadata.</span></span> <span data-ttu-id="3ecc5-121">그런 다음 호환 가능한 데이터 형식의 다른 열을 수동으로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-121">You can then manually map other columns that have compatible data types.</span></span>  
  
 <span data-ttu-id="3ecc5-122">이 변환에는 두 개의 입력과 하나의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-122">This transformation has two inputs and one output.</span></span> <span data-ttu-id="3ecc5-123">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-123">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-merge-transformation"></a><span data-ttu-id="3ecc5-124">병합 변환 구성</span><span class="sxs-lookup"><span data-stu-id="3ecc5-124">Configuration of the Merge Transformation</span></span>  
 <span data-ttu-id="3ecc5-125">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-125">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3ecc5-126">**병합 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Merge Transformation Editor](../../merge-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-126">For more information about the properties that you can set in the **Merge Transformation Editor** dialog box, see [Merge Transformation Editor](../../merge-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="3ecc5-127">프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-127">For more information about the properties that you can programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3ecc5-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3ecc5-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="3ecc5-129">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="3ecc5-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3ecc5-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3ecc5-130">Related Tasks</span></span>  
 <span data-ttu-id="3ecc5-131">속성을 설정하는 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-131">For details about how to set properties, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3ecc5-132">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="3ecc5-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="3ecc5-133">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="3ecc5-133">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ecc5-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ecc5-134">See Also</span></span>  
 <span data-ttu-id="3ecc5-135">[병합 조인 변환](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3ecc5-135">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="3ecc5-136">[UNION ALL 변환](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3ecc5-136">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="3ecc5-137">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3ecc5-137">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="3ecc5-138">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="3ecc5-138">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
