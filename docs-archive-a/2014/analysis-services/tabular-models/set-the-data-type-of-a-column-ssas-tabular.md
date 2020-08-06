---
title: 열의 데이터 형식 설정 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727372"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a><span data-ttu-id="2f337-102">열 데이터 형식 설정(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2f337-102">Set the Data Type of a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="2f337-103">모델에 데이터를 가져오거나 붙여넣을 때 모델 디자이너에서 자동으로 데이터 형식을 감지하고 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-103">When you import data or paste data into a model, the model designer will automatically detect and apply data types.</span></span> <span data-ttu-id="2f337-104">모델에 데이터를 추가한 후 열의 데이터 형식을 수동으로 수정하여 데이터가 저장되는 방법을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-104">After you have added the data to the model, you can manually modify the data type of a column to change how data is stored.</span></span> <span data-ttu-id="2f337-105">원하는 경우 데이터 저장 방식은 변경하지 않고 데이터 표시 방식의 형식만 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-105">If you just want to change the format of how the data is displayed without changing the way it is stored, you can do that instead.</span></span>  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a><span data-ttu-id="2f337-106">열의 데이터 형식 또는 표시 형식을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f337-106">To change the data type or display format for a column</span></span>  
  
1.  <span data-ttu-id="2f337-107">모델 디자이너에서 데이터 형식 또는 서식을 변경할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-107">In the model designer, select the column for which you want to change the data type or display format.</span></span>  
  
2.  <span data-ttu-id="2f337-108">열 **속성** 창에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-108">In the column **Properties** window, do one of the following:</span></span>  
  
    -   <span data-ttu-id="2f337-109">**데이터 서식** 속성에서 다른 데이터 서식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-109">In the **Data Format** property, select a different data format.</span></span>  
  
    -   <span data-ttu-id="2f337-110">**데이터 형식** 속성에서 다른 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-110">In the **Data Type** property, select a different data type.</span></span>  
  
## <a name="considerations-when-changing-data-types"></a><span data-ttu-id="2f337-111">데이터 형식을 변경할 때의 고려 사항</span><span class="sxs-lookup"><span data-stu-id="2f337-111">Considerations when Changing Data Types</span></span>  
 <span data-ttu-id="2f337-112">열의 데이터 형식을 변경하거나 데이터 변환을 선택할 때 다음 오류 중 하나가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-112">Sometimes when you try to change the data type of a column or select a data conversion, one of the following errors might occur:</span></span>  
  
-   <span data-ttu-id="2f337-113">데이터 형식을 변경하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-113">Failed to change data type</span></span>  
  
-   <span data-ttu-id="2f337-114">열 데이터 형식을 변경하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-114">Failed to change column data type</span></span>  
  
 <span data-ttu-id="2f337-115">데이터 형식 드롭다운 목록에 데이터 형식이 옵션으로 표시되는 경우에도 이러한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-115">These errors might occur even if the data type is available as an option in the Data Type dropdown list.</span></span> <span data-ttu-id="2f337-116">이 섹션에서는 이러한 오류 메시지의 원인 및 이를 해결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-116">This section explains the cause of these errors and how you can correct them.</span></span>  
  
### <a name="understanding-automatically-determined-data-types"></a><span data-ttu-id="2f337-117">자동으로 결정되는 데이터 형식 이해</span><span class="sxs-lookup"><span data-stu-id="2f337-117">Understanding Automatically Determined Data Types</span></span>  
 <span data-ttu-id="2f337-118">모델에 데이터를 추가하면 모델 디자이너에서 데이터 열을 검사하여 각 열에 포함된 데이터 형식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-118">When you add data to a model, the model designer checks the columns of data to see what data types each column contains.</span></span> <span data-ttu-id="2f337-119">해당 열의 데이터가 일치하면 가장 정확한 데이터 형식이 열에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-119">If the data in that column is consistent, is assigns the most precise data type to the column.</span></span>  
  
 <span data-ttu-id="2f337-120">그러나 Excel 또는 각 열에 단일 데이터 형식 사용을 적용하지 않는 기타 원본에서 데이터를 추가하는 경우 모델 디자이너에서 열의 모든 값을 수용하는 데이터 형식을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-120">However, if you add data from Excel or another source that does not enforce the use of a single data type within each column, the model designer will assign a data type that accommodates all values within the column.</span></span> <span data-ttu-id="2f337-121">따라서 정수, 긴 숫자, 통화 등의 여러 형식이 열에 포함되어 있으면 모델 디자이너에서 10진수 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-121">Therefore, if a column contains numbers of different types, such as integers, long numbers, and currency, the model designer will use a decimal data type.</span></span> <span data-ttu-id="2f337-122">또는 열에서 숫자와 텍스트를 함께 사용하는 경우 모델 디자이너에서 텍스트 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-122">Alternatively, if a column mixes numbers and text, the model designer will use the text data type.</span></span> <span data-ttu-id="2f337-123">모델 디자이너는 Excel에서 사용 가능한 일반 데이터 형식과 비슷한 데이터 형식을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-123">The model designer does not provide a data type similar to the General data type available in Excel.</span></span>  
  
 <span data-ttu-id="2f337-124">따라서 열에 숫자와 텍스트 값이 모두 포함되어 있으면 열을 숫자 데이터 형식으로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-124">Therefore, if a column contains both numbers and text values, you will not be able to convert the column to a numeric data type.</span></span>  
  
 <span data-ttu-id="2f337-125">모델비즈니스 인텔리전스 의미 체계 모델에서는 다음과 같은 데이터 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-125">The following data types are available in business intelligence semantic models:</span></span>  
  
|<span data-ttu-id="2f337-126">모델 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2f337-126">Model data types</span></span>|  
|----------------------|  
|<span data-ttu-id="2f337-127">텍스트</span><span class="sxs-lookup"><span data-stu-id="2f337-127">Text</span></span><br /><br /> <span data-ttu-id="2f337-128">10진수</span><span class="sxs-lookup"><span data-stu-id="2f337-128">Decimal Number</span></span><br /><br /> <span data-ttu-id="2f337-129">정수</span><span class="sxs-lookup"><span data-stu-id="2f337-129">Whole Number</span></span><br /><br /> <span data-ttu-id="2f337-130">Currency</span><span class="sxs-lookup"><span data-stu-id="2f337-130">Currency</span></span><br /><br /> <span data-ttu-id="2f337-131">TRUE/FALSE</span><span class="sxs-lookup"><span data-stu-id="2f337-131">TRUE/FALSE</span></span><br /><br /> <span data-ttu-id="2f337-132">Date</span><span class="sxs-lookup"><span data-stu-id="2f337-132">Date</span></span>|  
  
 <span data-ttu-id="2f337-133">데이터의 데이터 형식이 잘못되었거나 적어도 하나 이상의 데이터 형식이 원하는 형식과 다를 경우 다음과 같은 여러 가지 옵션 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-133">If you find that your data has a wrong data type, or at least a different one than you wanted, you have several options:</span></span>  
  
-   <span data-ttu-id="2f337-134">데이터를 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-134">You can re-import the data.</span></span> <span data-ttu-id="2f337-135">이렇게 하려면 데이터 원본에 대한 기존 연결을 열고 열을 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-135">To do this, open the existing connection to the data source and re-import the column.</span></span> <span data-ttu-id="2f337-136">데이터 원본 유형에 따라 가져오는 동안 필터를 적용하여 문제가 되는 값을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-136">Depending on the data source type, you might be able to apply a filter during import to remove problem values.</span></span>  
  
-   <span data-ttu-id="2f337-137">계산 열에 DAX 수식을 만들어 원하는 데이터 형식의 새 값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-137">You can create a DAX formula in a calculated column to create a new value of the desired data type.</span></span> <span data-ttu-id="2f337-138">예를 들어 TRUNC 함수를 사용하여 10진수를 정수로 변경하거나 정보 함수와 논리 함수를 결합하여 값을 테스트하고 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-138">For example, the TRUNC function can be used to change a decimal number to a whole integer, or you can combine information functions and logical functions to test and convert values.</span></span>  
  
### <a name="understanding-data-conversion"></a><span data-ttu-id="2f337-139">데이터 변환 이해</span><span class="sxs-lookup"><span data-stu-id="2f337-139">Understanding Data Conversion</span></span>  
 <span data-ttu-id="2f337-140">데이터 변환 옵션을 선택할 때 오류가 발생하면 열의 현재 데이터 형식에서 지원하지 않는 변환을 선택했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-140">If an error occurs when you select a data conversion option, it might be that the current data type of the column does not support the selected conversion.</span></span> <span data-ttu-id="2f337-141">모든 데이터 형식에 모든 변환이 허용되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-141">Not all conversions are allowed for all data types.</span></span> <span data-ttu-id="2f337-142">예를 들어 열의 현재 데이터 형식이 숫자(정수 또는 10진수) 또는 텍스트일 경우 열을 부울 데이터 형식으로만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-142">For example, you can only change a column to a Boolean data type if the current data type of the column is either a number (whole or decimal) or text.</span></span> <span data-ttu-id="2f337-143">따라서 열의 데이터에 적합한 데이터 형식을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-143">Therefore, you must choose an appropriate data type for the data in the column.</span></span>  
  
 <span data-ttu-id="2f337-144">적절한 데이터 형식을 선택하면 모델 디자이너에서 정밀도 손실이나 잘림과 같은 데이터 변경이 발생할 수 있음을 알리는 경고 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-144">After you choose an appropriate data type, the model designer will warn you about possible changes to your data, such as loss of precision, or truncation.</span></span> <span data-ttu-id="2f337-145">확인을 클릭하여 수락하고 데이터를 새 데이터 형식으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-145">Click OK to accept and change your data to the new data type.</span></span>  
  
 <span data-ttu-id="2f337-146">데이터 형식은 지원되지만 모델 디자이너에서 새 데이터 형식에 맞지 않는 값을 발견할 경우에는 다른 오류가 표시되며 계속하기 전에 데이터 값을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f337-146">If the data type is supported, but the model designer finds values that are not supported within the new data type, you will get another error, and will need to correct the data values before proceeding.</span></span>  
  
 <span data-ttu-id="2f337-147">비즈니스 인텔리전스 의미 체계 모델에서 사용되는 데이터 형식, 이러한 데이터 형식이 암시적으로 변환되는 방법 및 수식에서 다양한 데이터 형식이 사용되는 방법에 대한 자세한 내용은 [지원되는 데이터 형식&#40;SSAS 테이블 형식&#41;](data-types-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f337-147">For detailed information about the data types used in business intelligence semantic models, how they are implicitly converted, and how different data types are used in formulas, see [Data Types Supported &#40;SSAS Tabular&#41;](data-types-supported-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f337-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f337-148">See Also</span></span>  
 [<span data-ttu-id="2f337-149">지원되는 데이터 형식&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2f337-149">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](data-types-supported-ssas-tabular.md)  
  
  
