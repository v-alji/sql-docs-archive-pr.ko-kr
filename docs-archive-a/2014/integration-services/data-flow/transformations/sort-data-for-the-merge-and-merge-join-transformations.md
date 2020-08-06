---
title: 병합 및 병합 조인 변환을 위한 데이터 정렬 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bb4e91ad84c6baa52e1d7fb4b0104d835b7e4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728499"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a><span data-ttu-id="be063-102">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="be063-102">Sort Data for the Merge and Merge Join Transformations</span></span>
  <span data-ttu-id="be063-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 병합 및 병합 조인 변환에는 정렬된 데이터를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-103">In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the Merge and Merge Join transformations require sorted data for their inputs.</span></span> <span data-ttu-id="be063-104">입력 데이터는 물리적으로 정렬되어야 하며 출력 및 원본의 출력 열 또는 업스트림 변환에 정렬 옵션이 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-104">The input data must be sorted physically, and sort options must be set on the outputs and the output columns in the source or in the upstream transformation.</span></span> <span data-ttu-id="be063-105">정렬 옵션은 데이터가 정렬되었음을 나타내지만 데이터가 실제로 정렬되지 않은 경우에는 병합 또는 병합 조인 작업의 결과를 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-105">If the sort options indicate that the data is sorted, but the data is not actually sorted, the results of the merge or merge join operation are unpredictable.</span></span>  
  
## <a name="sorting-the-data"></a><span data-ttu-id="be063-106">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="be063-106">Sorting the Data</span></span>  
 <span data-ttu-id="be063-107">다음 방법 중 하나를 사용하여 이러한 데이터를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-107">You can sort this data by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="be063-108">원본에서 데이터를 로드하는 데 사용되는 명령문에 ORDER BY 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-108">In the source, use an ORDER BY clause in the statement that is used to load the data.</span></span>  
  
-   <span data-ttu-id="be063-109">데이터 흐름에서 병합 또는 병합 조인 변환 앞에 정렬 변환을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-109">In the data flow, insert a Sort transformation before the Merge or Merge Join transformation.</span></span>  
  
 <span data-ttu-id="be063-110">데이터가 문자열 데이터인 경우 병합 및 병합 조인 변환은 둘 다 Windows 데이터 정렬을 사용하여 문자열 값이 정렬된 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-110">If the data is string data, both the Merge and Merge Join transformations expect the string values to have been sorted by using Windows collation.</span></span> <span data-ttu-id="be063-111">병합 및 병합 조인 변환에 Windows 데이터 정렬을 사용하여 정렬된 문자열 값을 제공하려면 다음 절차를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-111">To provide string values to the Merge and Merge Join transformations that are sorted by using Windows collation, use the following procedure.</span></span>  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a><span data-ttu-id="be063-112">Windows 데이터 정렬을 사용하여 정렬되는 문자열 값을 제공하려면</span><span class="sxs-lookup"><span data-stu-id="be063-112">To provide string values that are sorted by using Windows collation</span></span>  
  
-   <span data-ttu-id="be063-113">정렬 변환을 사용하여 데이터를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-113">Use a Sort transformation to sort the data.</span></span>  
  
     <span data-ttu-id="be063-114">정렬 변환은 Windows 데이터 정렬을 사용하여 문자열 값을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-114">The Sort transformation uses Windows collation to sort string values.</span></span>  
  
     <span data-ttu-id="be063-115">또는</span><span class="sxs-lookup"><span data-stu-id="be063-115">-or-</span></span>  
  
-   <span data-ttu-id="be063-116">먼저 Transact-SQL CAST 연산자를 사용하여 `varchar` 값을 `nvarchar` 값으로 캐스팅한 다음 Transact-SQL ORDER BY 절을 사용하여 데이터를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-116">Use the Transact-SQL CAST operator to first cast `varchar` values to `nvarchar` values, and then use the Transact-SQL ORDER BY clause to sort the data.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="be063-117">ORDER BY 절은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 정렬을 사용하여 문자열 값을 정렬하므로 ORDER BY 절만 단독으로 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-117">You cannot use the ORDER BY clause alone because the ORDER BY clause uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation to sort string values.</span></span> <span data-ttu-id="be063-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 정렬을 사용하면 Windows 데이터 정렬을 사용하는 것과 다른 순서로 데이터가 정렬되므로 병합 또는 병합 조인 변환이 예기치 않은 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-118">The use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation might result in a different sort order than Windows collation, which can cause the Merge or Merge Join transformation to produce unexpected results.</span></span>  
  
## <a name="setting-sort-options-on-the-data"></a><span data-ttu-id="be063-119">데이터 정렬 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="be063-119">Setting Sort Options on the Data</span></span>  
 <span data-ttu-id="be063-120">병합 및 병합 조인 변환에 데이터를 제공하는 원본이나 업스트림 변환에 두 가지 중요한 정렬 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-120">There are two important sort properties that must be set for the source or upstream transformation that supplies data to the Merge and Merge Join transformations:</span></span>  
  
-   <span data-ttu-id="be063-121">데이터가 정렬되었는지 여부를 나타내는 출력의 `IsSorted` 속성.</span><span class="sxs-lookup"><span data-stu-id="be063-121">The `IsSorted` property of the output that indicates whether the data has been sorted.</span></span> <span data-ttu-id="be063-122">이 속성을 `True`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-122">This property must be set to `True`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="be063-123">`IsSorted` 속성의 값을 `True`로 설정해도 데이터가 정렬되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-123">Setting the value of the `IsSorted` property to `True` does not sort the data.</span></span> <span data-ttu-id="be063-124">이 속성은 데이터가 이전에 정렬되었다는 정보를 다운스트림 구성 요소에 제공하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-124">This property only provides a hint to downstream components that the data has been previously sorted.</span></span>  
  
-   <span data-ttu-id="be063-125">열이 정렬되었는지 여부, 열의 정렬 순서 및 여러 열이 정렬된 시퀀스를 나타내는 출력 열의 `SortKeyPosition` 속성.</span><span class="sxs-lookup"><span data-stu-id="be063-125">The `SortKeyPosition` property of output columns that indicates whether a column is sorted, the column's sort order, and the sequence in which multiple columns are sorted.</span></span> <span data-ttu-id="be063-126">정렬된 데이터의 각 열에 이 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-126">This property must be set for each column of sorted data.</span></span>  
  
 <span data-ttu-id="be063-127">정렬 변환을 사용하여 데이터를 정렬하면 이러한 두 속성이 병합 또는 병합 조인 변환에 필요한 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="be063-127">If you use a Sort transformation to sort the data, the Sort transformation sets both of these properties as required by the Merge or Merge Join transformation.</span></span> <span data-ttu-id="be063-128">즉, 출력의 `IsSorted` 속성이 `True`로 설정되고 출력 열의 `SortKeyPosition` 속성이 적절히 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="be063-128">That is, the Sort transformation sets the `IsSorted` property of its output to `True`, and sets the `SortKeyPosition` properties of its output columns.</span></span>  
  
 <span data-ttu-id="be063-129">그러나 정렬 변환을 사용하여 데이터를 정렬하지 않는 경우에는 원본 또는 업스트림 변환에서 이러한 정렬 속성을 수동으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-129">However, if you do not use a Sort transformation to sort the data, you must set these sort properties manually on the source or the upstream transformation.</span></span> <span data-ttu-id="be063-130">원본 또는 업스트림 변환에서 정렬 속성을 수동으로 설정하려면 다음 절차를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-130">To manually set the sort properties on the source or upstream transformation, use the following procedure.</span></span>  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a><span data-ttu-id="be063-131">원본 또는 변환 구성 요소의 정렬 특성을 수동으로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="be063-131">To manually set sort attributes on a source or transformation component</span></span>  
  
1.  <span data-ttu-id="be063-132">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be063-132">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="be063-133">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be063-133">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="be063-134">적절한 원본 또는 업스트림 변환을 **데이터 흐름** 탭에서 찾거나 **도구 상자** 에서 디자인 화면으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-134">On the **Data Flow** tab, locate the appropriate source or upstream transformation, or drag it from the **Toolbox** to the design surface.</span></span>  
  
4.  <span data-ttu-id="be063-135">구성 요소를 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-135">Right-click the component and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="be063-136">**입/출력 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-136">Click the **Input and Output Properties** tab.</span></span>  
  
6.  <span data-ttu-id="be063-137">\*\* \<component name> 출력\*\*을 클릭 하 고 `IsSorted` 속성을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-137">Click **\<component name> Output**, and set the `IsSorted` property to `True`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be063-138">수동으로 출력의 `IsSorted` 속성을 `True`로 설정했지만 데이터가 정렬되지 않았다면 패키지를 실행할 때 다운스트림 병합 또는 병합 조인 변환에 데이터가 누락되었거나 데이터 비교가 잘못되었기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be063-138">If you manually set the `IsSorted` property of the output to `True` and the data is not sorted, there might be missing data or bad data comparisons in the downstream Merge or Merge Join transformation when you run the package.</span></span>  
  
7.  <span data-ttu-id="be063-139">**출력 열**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-139">Expand **Output Columns**.</span></span>  
  
8.  <span data-ttu-id="be063-140">정렬된 것으로 표시할 열을 클릭하고 다음 지침에 따라 해당 `SortKeyPosition` 속성을 0이 아닌 정수 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-140">Click the column that you want to indicate is sorted and set its `SortKeyPosition` property to a nonzero integer value by following these guidelines:</span></span>  
  
    -   <span data-ttu-id="be063-141">정수 값은 1부터 시작하여 1씩 증가하는 숫자 시퀀스를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-141">The integer value must represent a numeric sequence, starting with 1 and incremented by 1.</span></span>  
  
    -   <span data-ttu-id="be063-142">양의 정수 값은 오름차순 정렬을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-142">A positive integer value indicates an ascending sort order.</span></span>  
  
    -   <span data-ttu-id="be063-143">음의 정수 값은 내림차순 정렬을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-143">A negative integer value indicates a descending sort order.</span></span> <span data-ttu-id="be063-144">음수로 설정하는 경우 숫자의 절대값은 정렬 시퀀스에서 열의 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-144">(If set to a negative number, the absolute value of the number determines the column's position in the sort sequence.)</span></span>  
  
    -   <span data-ttu-id="be063-145">기본값인 0은 열이 정렬되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-145">The default value of 0 indicates that the column is not sorted.</span></span> <span data-ttu-id="be063-146">출력 열이 정렬에 참여하지 않는 경우 값을 0으로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="be063-146">Leave the value of 0 for output columns that do not participate in the sort.</span></span>  
  
     <span data-ttu-id="be063-147">`SortKeyPosition` 속성을 설정하는 방법을 보여 주는 예는 원본에서 데이터를 로드하는 다음 Transact-SQL 문을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="be063-147">As an example of how to set the `SortKeyPosition` property, consider the following Transact-SQL statement that loads data in a source:</span></span>  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     <span data-ttu-id="be063-148">이 명령문의 경우 각 열의 `SortKeyPosition` 속성을 다음과 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-148">For this statement, you would set the `SortKeyPosition` property for each column as follows:</span></span>  
  
    -   <span data-ttu-id="be063-149">ColumnA의 `SortKeyPosition` 속성을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-149">Set the `SortKeyPosition` property of ColumnA to 1.</span></span> <span data-ttu-id="be063-150">이는 ColumnA가 정렬할 첫째 열이며 오름차순으로 정렬됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-150">This indicates that ColumnA is the first column to be sorted and is sorted in ascending order.</span></span>  
  
    -   <span data-ttu-id="be063-151">ColumnB의 `SortKeyPosition` 속성을 -2로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-151">Set the `SortKeyPosition` property of ColumnB to -2.</span></span> <span data-ttu-id="be063-152">이는 ColumnB가 두 번째로 정렬할 열이며 내림차순으로 정렬함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-152">This indicates that ColumnB is the second column to be sorted and is sorted in descending order</span></span>  
  
    -   <span data-ttu-id="be063-153">ColumnC의 `SortKeyPosition` 속성을 3으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-153">Set the `SortKeyPosition` property of ColumnC to 3.</span></span> <span data-ttu-id="be063-154">이는 ColumnC가 정렬할 셋째 열이며 오름차순으로 정렬됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="be063-154">This indicates that ColumnC is the third column to be sorted and is sorted in ascending order.</span></span>  
  
9. <span data-ttu-id="be063-155">정렬된 각 열에 대해 8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-155">Repeat step 8 for each sorted column.</span></span>  
  
10. <span data-ttu-id="be063-156">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-156">Click **OK**.</span></span>  
  
11. <span data-ttu-id="be063-157">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be063-157">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be063-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be063-158">See Also</span></span>  
 <span data-ttu-id="be063-159">[병합 변환](merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="be063-159">[Merge Transformation](merge-transformation.md) </span></span>  
 <span data-ttu-id="be063-160">[병합 조인 변환](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="be063-160">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="be063-161">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="be063-161">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="be063-162">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="be063-162">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="be063-163">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="be063-163">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
