---
title: 집계 변환을 사용하여 데이터 세트의 값 집계 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de918c6c2adf194d5808ccd1b64c77a94a52e357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728524"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a><span data-ttu-id="8dd84-102">집계 변환을 사용하여 데이터 세트의 값 집계</span><span class="sxs-lookup"><span data-stu-id="8dd84-102">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>
  <span data-ttu-id="8dd84-103">집계 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-103">To add and configure an Aggregate transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-aggregate-values-in-a-dataset"></a><span data-ttu-id="8dd84-104">데이터 세트의 값을 집계하려면</span><span class="sxs-lookup"><span data-stu-id="8dd84-104">To aggregate values in a dataset</span></span>  
  
1.  <span data-ttu-id="8dd84-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8dd84-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8dd84-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 집계 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Aggregate transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="8dd84-108">원본이나 이전 변환에서 연결선을 집계 변환으로 끌어서 집계 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-108">Connect the Aggregate transformation to the data flow by dragging a connector from the source or the previous transformation to the Aggregate transformation.</span></span>  
  
5.  <span data-ttu-id="8dd84-109">변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-109">Double-click the transformation.</span></span>  
  
6.  <span data-ttu-id="8dd84-110">**집계 변환 편집기** 대화 상자에서 **집계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-110">In the **Aggregate Transformation Editor** dialog box, click the **Aggregations** tab.</span></span>  
  
7.  <span data-ttu-id="8dd84-111">**사용 가능한 입력 열** 목록에서 값을 집계하려는 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-111">In the **Available Input Columns** list, select the check box by the columns on which you want to aggregate values.</span></span> <span data-ttu-id="8dd84-112">선택한 열이 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-112">The selected columns appear in the table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dd84-113">열에 다중 변환을 사용하면 한 열을 여러 번 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-113">You can select a column multiple times, applying multiple transformations to the column.</span></span> <span data-ttu-id="8dd84-114">집계를 고유하게 식별하기 위해 열의 출력 별칭 기본 이름에 숫자가 붙여집니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-114">To uniquely identify aggregations, a number is appended to the default name of the output alias of the column.</span></span>  
  
8.  <span data-ttu-id="8dd84-115">선택적으로 **출력 별칭** 열의 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-115">Optionally, modify the value in the **Output Alias** columns.</span></span>  
  
9. <span data-ttu-id="8dd84-116">기본 집계 작업인 **Group by**를 변경하려면 **작업** 목록에서 다른 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-116">To change the default aggregation operation, **Group by**, select a different operation in the **Operation** list.</span></span>  
  
10. <span data-ttu-id="8dd84-117">기본 비교를 변경하려면 **비교 플래그** 열에서 나열된 개별 비교 플래그를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-117">To change the default comparison, select the individual comparison flags listed in the **Comparison Flags** column.</span></span> <span data-ttu-id="8dd84-118">기본적으로 비교는 대/소문자, 가나 형식, 공백 없는 문자 및 문자 너비를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-118">By default, a comparison ignores case, kana type, non-spacing characters, and character width.</span></span>  
  
11. <span data-ttu-id="8dd84-119">선택적으로 **Count distinct** 집계에 대해 **고유 키 수** 열에서 정확한 고유 값 수를 지정하거나 **고유 수 배율** 열에서 대략적인 수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-119">Optionally, for the **Count distinct** aggregation, specify an exact number of distinct values in the **Count Distinct Keys** column, or select an approximate count in the **Count Distinct Scale** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dd84-120">정확하게든 또는 대략적으로든 고유 값 수를 제공하면 변환을 통해 작업을 수행할 수 있도록 해당 메모리 양을 미리 할당할 수 있으므로 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-120">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
12. <span data-ttu-id="8dd84-121">선택적으로 **고급** 을 클릭하여 집계 변환 출력의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-121">Optionally, click **Advanced** and update the name of the Aggregate transformation output.</span></span> <span data-ttu-id="8dd84-122">집계에 작업이 포함 된 경우 키 `Group By` **배율** 열에서 키 값 그룹화의 대략적인 개수를 선택 하거나 키 열에서 정확 하 게 그룹화 된 키 값 수를 지정할 수 **Keys** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-122">If the aggregations include a `Group By` operation, you can select an approximate count of grouping key values in the **Keys Scale** column or specify an exact number of grouping key values in the **Keys** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dd84-123">정확하게든 또는 대략적으로든 고유 값 수를 제공하면 변환을 통해 작업을 수행할 수 있도록 해당 메모리 양을 미리 할당할 수 있으므로 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-123">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dd84-124">**키 배율** 및 **키** 옵션은 상호 배타적입니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-124">The **Keys Scale** and **Keys** options are mutually exclusive.</span></span> <span data-ttu-id="8dd84-125">두 열 모두에 값을 입력하면 **키 배율** 또는 **키** 값 중에서 더 큰 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-125">If you enter values in both columns, the larger value in either **Keys Scale** or **Keys** is used.</span></span>  
  
13. <span data-ttu-id="8dd84-126">선택적으로 **고급** 탭을 클릭하고 집계 변환이 수행하는 모든 작업을 최적화하는 데 적용되는 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-126">Optionally, click the **Advanced** tab and set the attributes that apply to optimizing all the operations that the Aggregate transformation performs.</span></span>  
  
14. <span data-ttu-id="8dd84-127">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-127">Click **OK**.</span></span>  
  
15. <span data-ttu-id="8dd84-128">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8dd84-128">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd84-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8dd84-129">See Also</span></span>  
 <span data-ttu-id="8dd84-130">[집계 변환](aggregate-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="8dd84-130">[Aggregate Transformation](aggregate-transformation.md) </span></span>  
 <span data-ttu-id="8dd84-131">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="8dd84-131">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="8dd84-132">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="8dd84-132">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="8dd84-133">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="8dd84-133">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
