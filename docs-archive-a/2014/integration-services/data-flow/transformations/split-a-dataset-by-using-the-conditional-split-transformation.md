---
title: 조건부 분할 변환을 사용하여 데이터 세트 분할 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2efbc3973db1ab1b6b61f6de879e451319b50e49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659556"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a><span data-ttu-id="8eddc-102">조건부 분할 변환을 사용하여 데이터 세트 분할</span><span class="sxs-lookup"><span data-stu-id="8eddc-102">Split a Dataset by Using the Conditional Split Transformation</span></span>
  <span data-ttu-id="8eddc-103">조건부 분할 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-103">To add and configure a Conditional Split transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-conditionally-split-a-dataset"></a><span data-ttu-id="8eddc-104">데이터 세트를 조건적으로 분할하려면</span><span class="sxs-lookup"><span data-stu-id="8eddc-104">To conditionally split a dataset</span></span>  
  
1.  <span data-ttu-id="8eddc-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8eddc-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8eddc-107">**데이터 흐름** 탭을 클릭하고 **도구 상자**에서 조건부 분할 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-107">Click the **Data Flow** tab, and, from the **Toolbox**, drag the Conditional Split transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="8eddc-108">데이터 원본이나 이전 변환에서 연결선을 조건부 분할 변환으로 끌어서 조건부 분할 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-108">Connect the Conditional Split transformation to the data flow by dragging the connector from the data source or the previous transformation to the Conditional Split transformation.</span></span>  
  
5.  <span data-ttu-id="8eddc-109">조건부 분할 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-109">Double-click the Conditional Split transformation.</span></span>  
  
6.  <span data-ttu-id="8eddc-110">**조건부 분할 변환 편집기**에서 변수, 열, 함수 및 연산자를 표의 **조건** 열로 끌어서 조건에 따라 사용할 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-110">In the **Conditional Split Transformation Editor**, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Condition** column in the grid.</span></span> <span data-ttu-id="8eddc-111">또는 **조건** 열에 식을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-111">Or, you can type the expression in the **Condition** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eddc-112">변수 또는 열은 여러 식에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-112">A variable or column can be used in multiple expressions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eddc-113">식이 올바르지 않으면 식 텍스트가 강조 표시되고 열의 도구 설명에 오류에 대한 설명이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-113">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="8eddc-114">선택적으로 **출력 이름** 열의 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-114">Optionally, modify the values in the **Output Name** column.</span></span> <span data-ttu-id="8eddc-115">기본 이름은 사례 1, 사례 2 등과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-115">The default names are Case 1, Case 2, and so forth.</span></span>  
  
8.  <span data-ttu-id="8eddc-116">조건이 평가되는 순서를 수정하려면 위 또는 아래 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-116">To modify the sequence in which the conditions are evaluated, click the up arrow or down arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eddc-117">발생할 가능성이 가장 높은 조건을 목록의 위쪽에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="8eddc-117">Place the conditions that are most likely to be encountered at the top of the list.</span></span>  
  
9. <span data-ttu-id="8eddc-118">선택적으로 어떤 조건에도 부합되지 않는 데이터 행에 대한 기본 출력의 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-118">Optionally, modify the name of the default output for data rows that do not match any condition.</span></span>  
  
10. <span data-ttu-id="8eddc-119">오류 출력을 구성하려면 **오류 출력 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-119">To configure an error output, click **Configure Error Output**.</span></span> <span data-ttu-id="8eddc-120">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8eddc-120">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="8eddc-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8eddc-122">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eddc-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eddc-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8eddc-123">See Also</span></span>  
 <span data-ttu-id="8eddc-124">[Conditional Split Transformation](conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="8eddc-124">[Conditional Split Transformation](conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="8eddc-125">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="8eddc-125">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="8eddc-126">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="8eddc-126">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="8eddc-127">[Integration Services 데이터 형식](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="8eddc-127">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="8eddc-128">[데이터 흐름 태스크](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="8eddc-128">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="8eddc-129">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="8eddc-129">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
