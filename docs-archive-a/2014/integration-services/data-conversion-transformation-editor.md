---
title: 데이터 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b893f04dcca2dd2a1a5874b55c1c1c608aaeb12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742475"
---
# <a name="data-conversion-transformation-editor"></a><span data-ttu-id="17e8b-102">데이터 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="17e8b-102">Data Conversion Transformation Editor</span></span>
  <span data-ttu-id="17e8b-103">**데이터 변환 편집기** 대화 상자를 사용하여 변환할 열을 선택하고, 열이 변환될 데이터 형식을 선택하고, 변환 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-103">Use the **Data Conversion Transformation Editor** dialog box to select the columns to convert, select the data type to which the column is converted, and set conversion attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17e8b-104">데이터 변환 `FastParse` 의 출력 열 속성은 **데이터 변환 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-104">The `FastParse` property of the output columns of the Data Conversion transformation is not available in the **Data Conversion Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="17e8b-105">이 속성에 대한 자세한 내용은 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)의 데이터 변환 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e8b-105">For more information on this property, see the Data Conversion Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="17e8b-106">데이터 변환에 대한 자세한 내용은 [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e8b-106">To learn more about the Data Conversion transformation, see [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="17e8b-107">옵션</span><span class="sxs-lookup"><span data-stu-id="17e8b-107">Options</span></span>  
 <span data-ttu-id="17e8b-108">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="17e8b-108">**Available Input Columns**</span></span>  
 <span data-ttu-id="17e8b-109">확인란을 사용하여 변환할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-109">Select columns to convert by using the check boxes.</span></span> <span data-ttu-id="17e8b-110">선택한 항목은 아래의 입력 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-110">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="17e8b-111">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="17e8b-111">**Input Column**</span></span>  
 <span data-ttu-id="17e8b-112">사용 가능한 입력 열 목록에서 변환할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-112">Select columns to convert from the list of available input columns.</span></span> <span data-ttu-id="17e8b-113">선택 내용에 따라 위의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-113">Your selections are reflected in the check box selections above.</span></span>  
  
 <span data-ttu-id="17e8b-114">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="17e8b-114">**Output Alias**</span></span>  
 <span data-ttu-id="17e8b-115">각 새 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-115">Type an alias for each new column.</span></span> <span data-ttu-id="17e8b-116">기본값은 `Copy of` 뒤에 입력 열 이름이 오는 형식이지만 설명이 포함된 고유 이름을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-116">The default is `Copy of` followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="17e8b-117">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="17e8b-117">**Data Type**</span></span>  
 <span data-ttu-id="17e8b-118">목록에서 사용 가능한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-118">Select an available data type from the list.</span></span> <span data-ttu-id="17e8b-119">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17e8b-119">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="17e8b-120">**길이**</span><span class="sxs-lookup"><span data-stu-id="17e8b-120">**Length**</span></span>  
 <span data-ttu-id="17e8b-121">문자열 데이터의 열 길이를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-121">Set the column length for string data.</span></span>  
  
 <span data-ttu-id="17e8b-122">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="17e8b-122">**Precision**</span></span>  
 <span data-ttu-id="17e8b-123">숫자 데이터의 전체 자릿수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-123">Set the precision for numeric data.</span></span>  
  
 <span data-ttu-id="17e8b-124">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="17e8b-124">**Scale**</span></span>  
 <span data-ttu-id="17e8b-125">숫자 데이터의 소수 자릿수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-125">Set the scale for numeric data.</span></span>  
  
 <span data-ttu-id="17e8b-126">**코드 페이지**</span><span class="sxs-lookup"><span data-stu-id="17e8b-126">**Code page**</span></span>  
 <span data-ttu-id="17e8b-127">DT_STR 유형의 열에 적절한 코드 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-127">Select the appropriate code page for columns of type DT_STR.</span></span>  
  
 <span data-ttu-id="17e8b-128">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="17e8b-128">**Configure error output**</span></span>  
 <span data-ttu-id="17e8b-129">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 하위 수준 오류를 처리하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e8b-129">Specify how to handle row-level errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e8b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17e8b-130">See Also</span></span>  
 <span data-ttu-id="17e8b-131">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="17e8b-131">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="17e8b-132">데이터 변환을 사용하여 데이터를 다른 데이터 형식으로 변환</span><span class="sxs-lookup"><span data-stu-id="17e8b-132">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
