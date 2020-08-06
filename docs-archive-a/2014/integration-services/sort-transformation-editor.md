---
title: 정렬 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f48c366f4337af29b03877f6bb20b804457a293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742351"
---
# <a name="sort-transformation-editor"></a><span data-ttu-id="6d444-102">정렬 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="6d444-102">Sort Transformation Editor</span></span>
  <span data-ttu-id="6d444-103">**정렬 변환 편집기** 대화 상자를 사용하여 정렬할 열을 선택하고, 정렬 순서를 설정하고, 중복을 제거할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-103">Use the **Sort Transformation Editor** dialog box to select the columns to sort, set the sort order, and specify whether duplicates are removed.</span></span>  
  
 <span data-ttu-id="6d444-104">정렬 변환에 대한 자세한 내용은 [Sort Transformation](data-flow/transformations/sort-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d444-104">To learn more about the Sort transformation, see [Sort Transformation](data-flow/transformations/sort-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d444-105">옵션</span><span class="sxs-lookup"><span data-stu-id="6d444-105">Options</span></span>  
 <span data-ttu-id="6d444-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="6d444-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="6d444-107">확인란을 사용하여 정렬할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-107">Using the check boxes, specify the columns to sort.</span></span>  
  
 <span data-ttu-id="6d444-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="6d444-108">**Name**</span></span>  
 <span data-ttu-id="6d444-109">사용 가능한 각 입력 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-109">View the name of each available input column.</span></span>  
  
 <span data-ttu-id="6d444-110">**통과**</span><span class="sxs-lookup"><span data-stu-id="6d444-110">**Passthrough**</span></span>  
 <span data-ttu-id="6d444-111">열을 정렬된 출력에 포함할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-111">Indicate whether to include the column in the sorted output.</span></span>  
  
 <span data-ttu-id="6d444-112">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="6d444-112">**Input Column**</span></span>  
 <span data-ttu-id="6d444-113">각 행에 대해 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="6d444-114">선택 내용에 따라 **사용 가능한 입력 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-114">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="6d444-115">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="6d444-115">**Output Alias**</span></span>  
 <span data-ttu-id="6d444-116">각 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-116">Type an alias for each output column.</span></span> <span data-ttu-id="6d444-117">기본값은 입력 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="6d444-118">**정렬 형식**</span><span class="sxs-lookup"><span data-stu-id="6d444-118">**Sort Type**</span></span>  
 <span data-ttu-id="6d444-119">오름차순으로 정렬할 것인지, 아니면 내림차순으로 정렬할 것인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-119">Indicate whether to sort in ascending or descending order.</span></span>  
  
 <span data-ttu-id="6d444-120">**정렬 순서**</span><span class="sxs-lookup"><span data-stu-id="6d444-120">**Sort Order**</span></span>  
 <span data-ttu-id="6d444-121">열을 정렬할 순서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-121">Indicate the order in which to sort columns.</span></span> <span data-ttu-id="6d444-122">이 옵션은 각 열에 대해 수동으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-122">This must be set manually for each column.</span></span>  
  
 <span data-ttu-id="6d444-123">**비교 플래그**</span><span class="sxs-lookup"><span data-stu-id="6d444-123">**Comparison Flags**</span></span>  
 <span data-ttu-id="6d444-124">문자열 비교 옵션에 대한 자세한 내용은 [문자열 데이터 비교](data-flow/comparing-string-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d444-124">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="6d444-125">**중복되는 정렬 값이 있는 행 제거**</span><span class="sxs-lookup"><span data-stu-id="6d444-125">**Remove rows with duplicate sort values**</span></span>  
 <span data-ttu-id="6d444-126">지정한 문자열 비교 옵션을 기반으로 변환에서 중복 행을 변환 출력에 복사할 것인지, 아니면 모든 중복에 대한 단일 항목을 만들 것인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d444-126">Indicate whether the transformation copies duplicate rows to the transformation output, or creates a single entry for all duplicates, based on the specified string comparison options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d444-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d444-127">See Also</span></span>  
 [<span data-ttu-id="6d444-128">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="6d444-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
