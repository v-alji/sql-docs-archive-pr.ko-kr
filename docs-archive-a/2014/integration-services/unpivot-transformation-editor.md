---
title: 피벗 해제 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c3b93370b34440b73b4c9c78dc7d19fa4095275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647737"
---
# <a name="unpivot-transformation-editor"></a><span data-ttu-id="b3ca9-102">피벗 해제 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="b3ca9-102">Unpivot Transformation Editor</span></span>
  <span data-ttu-id="b3ca9-103">**피벗 해제 변환 편집기** 대화 상자를 사용하여 행에 피벗할 열을 선택하고 데이터 열 및 새 피벗 값 출력 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-103">Use the **Unpivot Transformation Editor** dialog box to select the columns to pivot into rows, and to specify the data column and the new pivot value output column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3ca9-104">이 항목에서는 [피벗 해제 변환](data-flow/transformations/unpivot-transformation.md) 에 설명된 피벗 해제 시나리오를 사용하여 옵션 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-104">This topic relies on the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) to illustrate the use of the options.</span></span>  
  
 <span data-ttu-id="b3ca9-105">피벗 해제 변환에 대한 자세한 내용은 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-105">To learn more about the Unpivot transformation, see [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b3ca9-106">옵션</span><span class="sxs-lookup"><span data-stu-id="b3ca9-106">Options</span></span>  
 <span data-ttu-id="b3ca9-107">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-107">**Available Input Columns**</span></span>  
 <span data-ttu-id="b3ca9-108">확인란을 사용하여 행에 피벗할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-108">Using the check boxes, specify the columns to pivot into rows.</span></span>  
  
 <span data-ttu-id="b3ca9-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-109">**Name**</span></span>  
 <span data-ttu-id="b3ca9-110">사용 가능한 입력 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-110">View the name of the available input column.</span></span>  
  
 <span data-ttu-id="b3ca9-111">**통과**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-111">**Pass Through**</span></span>  
 <span data-ttu-id="b3ca9-112">열을 피벗 해제된 출력에 포함할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-112">Indicate whether to include the column in the unpivoted output.</span></span>  
  
 <span data-ttu-id="b3ca9-113">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-113">**Input Column**</span></span>  
 <span data-ttu-id="b3ca9-114">각 행에 대해 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-114">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="b3ca9-115">선택 내용에 따라 **사용 가능한 입력 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-115">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="b3ca9-116">[Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)에 설명된 피벗 해제 시나리오에서 입력 열은 **햄**, **탄산음료**, **우유**, **맥주**및 **칩** 열입니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-116">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Input Columns are the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns.</span></span>  
  
 <span data-ttu-id="b3ca9-117">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-117">**Destination Column**</span></span>  
 <span data-ttu-id="b3ca9-118">데이터 열에 사용할 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-118">Provide a name for the data column.</span></span>  
  
 <span data-ttu-id="b3ca9-119">[피벗 해제 변환](data-flow/transformations/unpivot-transformation.md)에 설명된 피벗 해제 시나리오에서 대상 열은 수량(**Qty**) 열입니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-119">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Destination Column is the quantity (**Qty**) column.</span></span>  
  
 <span data-ttu-id="b3ca9-120">**피벗 키 값**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-120">**Pivot Key Value**</span></span>  
 <span data-ttu-id="b3ca9-121">피벗 값에 사용할 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-121">Provide a name for the pivot value.</span></span> <span data-ttu-id="b3ca9-122">기본값은 입력 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-122">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="b3ca9-123">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-123">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="b3ca9-124">[Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)에 설명된 피벗 해제 시나리오에서 피벗 값은 **피벗 키 값 열 이름** 옵션으로 지정한 새 제품 열에 **햄**, **탄산음료**, **우유**, **맥주**및 **칩**과 같은 텍스트 값으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-124">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Values will appear in the new Product column designated by the **Pivot Key Value Column Name** option, as the text values **Ham**, **Soda**, **Milk**, **Beer**, and **Chips**.</span></span>  
  
 <span data-ttu-id="b3ca9-125">**피벗 키 값 열 이름**</span><span class="sxs-lookup"><span data-stu-id="b3ca9-125">**Pivot Key Value Column Name**</span></span>  
 <span data-ttu-id="b3ca9-126">피벗 값 열에 사용할 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-126">Provide a name for the pivot value column.</span></span> <span data-ttu-id="b3ca9-127">기본값은 "피벗 키 값"이지만 알기 쉬운 임의의 고유 이름을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-127">The default is "Pivot Key Value"; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="b3ca9-128">[Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)에 설명된 피벗 해제 시나리오에서 피벗 키 값 열 이름은 **제품** 이며 **제품** , **탄산음료**, **우유**, **맥주**, **칩**열이 피벗 해제되는 새 **제품** 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3ca9-128">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Key Value Column Name is **Product** and designates the new **Product** column into which the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns are unpivoted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ca9-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3ca9-129">See Also</span></span>  
 <span data-ttu-id="b3ca9-130">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b3ca9-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="b3ca9-131">피벗 변환</span><span class="sxs-lookup"><span data-stu-id="b3ca9-131">Pivot Transformation</span></span>](data-flow/transformations/pivot-transformation.md)  
  
  
