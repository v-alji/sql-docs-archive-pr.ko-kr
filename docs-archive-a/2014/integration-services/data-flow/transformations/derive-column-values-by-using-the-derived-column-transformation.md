---
title: 파생 열 변환을 사용하여 열 값 파생 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- columns [Integration Services]
- derived columns
- columns [Integration Services], values
- Derived Column transformation
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 837ec552144697b40cf649bc0403edfe4dc57a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646564"
---
# <a name="derive-column-values-by-using-the-derived-column-transformation"></a><span data-ttu-id="8efb1-102">파생 열 변환을 사용하여 열 값 파생</span><span class="sxs-lookup"><span data-stu-id="8efb1-102">Derive Column Values by Using the Derived Column Transformation</span></span>
  <span data-ttu-id="8efb1-103">파생 열 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-103">To add and configure a Derived Column transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
 <span data-ttu-id="8efb1-104">파생 열 변환은 식을 사용하여 기존 열의 값을 업데이트하거나 새 열에 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-104">The Derived Column transformation uses expressions to update the values of existing or to add values to new columns.</span></span> <span data-ttu-id="8efb1-105">새 열에 값을 추가하는 경우 **파생 열 변환 편집기** 대화 상자에서 식을 계산하고 열의 메타데이터를 적절히 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-105">When you choose to add values to new columns, the **Derived Column Transformation Editor** dialog box evaluates the expression and defines the metadata of the columns accordingly.</span></span> <span data-ttu-id="8efb1-106">예를 들어 식에서 각각 데이터 형식이 DT_WSTR이고 길이가 50인 두 개의 열을 해당 두 열 값 사이의 공백으로 연결할 경우 새 열은 데이터 형식이 DT_WSTR이고 길이는 101이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-106">For example, if an expression concatenates two columns-each with the DT_WSTR data type and a length of 50-with a space between the two column values, the new column has the DT_WSTR data type and a length of 101.</span></span> <span data-ttu-id="8efb1-107">새 열의 데이터 형식을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-107">You can update the data type of new columns.</span></span> <span data-ttu-id="8efb1-108">유일한 요구 사항은 데이터 형식이 삽입된 데이터와 호환되어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-108">The only requirement is that data type be compatible with the inserted data.</span></span> <span data-ttu-id="8efb1-109">예를 들어 정수 데이터 형식이 있는 열에 데이터 값을 할당할 경우 **파생 열 변환 편집기** 대화 상자에서 유효성 검사 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-109">For example, the **Derived Column Transformation Editor** dialog box generates a validation error when you assign a date value to a column with an integer data type.</span></span> <span data-ttu-id="8efb1-110">선택한 데이터 형식에 따라 열의 길이, 전체 자릿수, 소수 자릿수 및 코드 페이지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-110">Depending on the data type that you selected, you can specify the length, precision, scale, and code page of the column.</span></span>  
  
### <a name="to-derive-column-values"></a><span data-ttu-id="8efb1-111">열 값을 파생하려면</span><span class="sxs-lookup"><span data-stu-id="8efb1-111">To derive column values</span></span>  
  
1.  <span data-ttu-id="8efb1-112">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-112">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8efb1-113">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-113">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8efb1-114">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 파생 열 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-114">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Derived Column transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="8efb1-115">원본이나 이전 변환에서 연결선을 파생 열 변환으로 끌어서 파생 열 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-115">Connect the Derived Column transformation to the data flow by dragging the connector from the source or the previous transformation to the Derived Column transformation.</span></span>  
  
5.  <span data-ttu-id="8efb1-116">파생 열 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-116">Double-click the Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="8efb1-117">**파생 열 변환 편집기** 대화 상자에서 변수, 열, 함수 및 연산자를 표의 **식** 열로 끌어서 조건에 따라 사용할 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-117">In the **Derived Column Transformation Editor** dialog box, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Expression** column in the grid.</span></span> <span data-ttu-id="8efb1-118">또는 **식** 열에 식을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-118">Alternatively, you can type the expression in the **Expression** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8efb1-119">식이 올바르지 않으면 식 텍스트가 강조 표시되고 열의 도구 설명에 오류에 대한 설명이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-119">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="8efb1-120">**파생 열** 목록에서 **\<add as new column>** 를 선택하여 식의 계산 결과를 새 열에 기록하거나 기존 열을 선택하여 평가 결과를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-120">In the **Derived Column** list, select **\<add as new column>** to write the evaluation result of the expression to a new column, or select an existing column to update with the evaluation result.</span></span>  
  
     <span data-ttu-id="8efb1-121">새 열을 사용하는 경우 **파생 열 변환 편집기** 대화 상자는 식을 계산하고 데이터 형식, 길이, 전체 자릿수, 소수 자릿수 및 코드 페이지에 따라 열에 데이터 형식을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-121">If you chose to use a new column, the **Derived Column Transformation Editor** dialog box evaluates the expression and assigns a data type to the column, depending on the data type, length, precisions, scale, and code page.</span></span>  
  
8.  <span data-ttu-id="8efb1-122">새 열을 사용하는 경우 **데이터 형식** 목록에서 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-122">If using a new column, select a data type in the **Data Type** list.</span></span> <span data-ttu-id="8efb1-123">선택한 데이터 형식에 따라 선택적으로 **길이**, **전체 자릿수**, **소수 자릿수**및 **코드 페이지** 열에서 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-123">Depending on the selected data type, optionally update the values in the **Length**, **Precision**, **Scale**, and **Code Page** columns.</span></span> <span data-ttu-id="8efb1-124">기존 열의 메타데이터는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-124">Metadata of existing columns cannot be changed.</span></span>  
  
9. <span data-ttu-id="8efb1-125">선택적으로 **파생 열 이름** 열의 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-125">Optionally, modify the values in the **Derived Column Name** column.</span></span>  
  
10. <span data-ttu-id="8efb1-126">오류 출력을 구성하려면 **오류 출력 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-126">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="8efb1-127">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8efb1-127">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="8efb1-128">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-128">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8efb1-129">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8efb1-129">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efb1-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8efb1-130">See Also</span></span>  
 <span data-ttu-id="8efb1-131">[Derived Column Transformation](derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="8efb1-131">[Derived Column Transformation](derived-column-transformation.md) </span></span>  
 <span data-ttu-id="8efb1-132">[Integration Services 데이터 형식](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="8efb1-132">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="8efb1-133">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="8efb1-133">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="8efb1-134">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="8efb1-134">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="8efb1-135">[데이터 흐름 태스크](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="8efb1-135">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="8efb1-136">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="8efb1-136">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
