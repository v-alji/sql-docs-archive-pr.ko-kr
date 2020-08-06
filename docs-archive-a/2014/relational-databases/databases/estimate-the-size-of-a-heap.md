---
title: 힙 크기 예측 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- estimating heap size
- size [SQL Server], heap
- space [SQL Server], indexes
- heaps
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
author: stevestein
ms.author: sstein
ms.openlocfilehash: f32432d07a9731d849ceb793daf209cfc505b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661132"
---
# <a name="estimate-the-size-of-a-heap"></a><span data-ttu-id="aa643-102">힙 크기 예측</span><span class="sxs-lookup"><span data-stu-id="aa643-102">Estimate the Size of a Heap</span></span>
  <span data-ttu-id="aa643-103">다음 단계에 따라 힙에 데이터를 저장하는 데 필요한 공간의 크기를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-103">You can use the following steps to estimate the amount of space that is required to store data in a heap:</span></span>  
  
1.  <span data-ttu-id="aa643-104">테이블의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-104">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="aa643-105">***Num_Rows***  = 테이블의 행 수</span><span class="sxs-lookup"><span data-stu-id="aa643-105">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="aa643-106">고정 길이 및 가변 길이 열 수를 지정하고 이러한 열을 스토리지하는 데 필요한 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-106">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="aa643-107">이러한 각 열 그룹이 데이터 행 내에서 차지하는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-107">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="aa643-108">열 크기는 지정된 데이터 형식과 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-108">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="aa643-109">***Num_Cols***  = 열의 총 수(고정 길이 및 가변 길이)</span><span class="sxs-lookup"><span data-stu-id="aa643-109">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="aa643-110">***Fixed_Data_Size***  = 모든 고정 길이 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="aa643-110">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="aa643-111">***Num_Variable_Cols***  = 가변 길이 열의 수</span><span class="sxs-lookup"><span data-stu-id="aa643-111">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="aa643-112">***Max_Var_Size***  = 모든 가변 길이 열의 전체 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="aa643-112">***Max_Var_Size***  = maximum total byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="aa643-113">행의 Null 비트맵 부분은 열의 Null 허용 여부 관리를 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-113">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="aa643-114">다음과 같이 이 부분의 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-114">Calculate its size:</span></span>  
  
     <span data-ttu-id="aa643-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="aa643-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="aa643-116">이 식의 정수 부분만 사용하고</span><span class="sxs-lookup"><span data-stu-id="aa643-116">Only the integer part of this expression should be used.</span></span> <span data-ttu-id="aa643-117">나머지는 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-117">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="aa643-118">가변 길이 데이터 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-118">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="aa643-119">테이블에 가변 길이 열이 있는 경우에는 해당 행 안에 열을 저장하는 데 사용되는 공간을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-119">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="aa643-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="aa643-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="aa643-121">***Max_Var_Size***에 추가된 바이트는 각 가변 길이 열을 추적하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-121">The bytes added to ***Max_Var_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="aa643-122">이 수식에서는 모든 가변 길이 열이 100% 꽉 찬 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-122">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="aa643-123">사용할 가변 길이 열 스토리지 공간 비율이 더 적을 것으로 예상되는 경우 해당 비율로 ***Max_Var_Size*** 값을 조정하여 전체 테이블 크기를 보다 정확하게 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-123">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aa643-124">정의된 총 테이블 너비가 8,060바이트를 초과하는 `varchar`, `nvarchar`, `varbinary` 또는 `sql_variant` 열을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-124">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="aa643-125">이러한 열 각각의 길이는 `varchar` , 또는 열에 대해 8000 바이트 이내로 제한 되어야 합니다 `nvarchar,``varbinary` `sql_variant` .</span><span class="sxs-lookup"><span data-stu-id="aa643-125">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `nvarchar,``varbinary`, or `sql_variant` column.</span></span> <span data-ttu-id="aa643-126">그러나 결합된 너비는 테이블의 8,060바이트 제한을 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-126">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="aa643-127">가변 길이 열이 없는 경우에는 ***Variable_Data_Size*** 를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-127">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="aa643-128">전체 행 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-128">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="aa643-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="aa643-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="aa643-130">이 수식에서 값 4는 데이터 행의 행 머리글 오버헤드입니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-130">The value 4 in the formula is the row header overhead of the data row.</span></span>  
  
6.  <span data-ttu-id="aa643-131">페이지당 행 수를 계산합니다. 페이지당 사용 가능한 바이트 수는 8,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-131">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="aa643-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="aa643-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="aa643-133">행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 행 수는 가장 근사한 정수 값으로 내림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-133">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="aa643-134">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-134">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
7.  <span data-ttu-id="aa643-135">모든 행을 저장하는 데 필요한 페이지 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-135">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="aa643-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span><span class="sxs-lookup"><span data-stu-id="aa643-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span></span>  
  
     <span data-ttu-id="aa643-137">예상 페이지 수는 가장 근사한 전체 페이지로 올림되어 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-137">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
8.  <span data-ttu-id="aa643-138">힙에 데이터를 저장하는 데 필요한 공간의 크기를 계산합니다(페이지당 총 8192바이트임).</span><span class="sxs-lookup"><span data-stu-id="aa643-138">Calculate the amount of space that is required to store the data in the heap (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="aa643-139">힙 크기(바이트) = 8192 x ***Num_Pages***</span><span class="sxs-lookup"><span data-stu-id="aa643-139">Heap size (bytes) = 8192 x ***Num_Pages***</span></span>  
  
 <span data-ttu-id="aa643-140">이 계산에서 다음 사항은 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-140">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="aa643-141">분할</span><span class="sxs-lookup"><span data-stu-id="aa643-141">Partitioning</span></span>  
  
     <span data-ttu-id="aa643-142">분할에 따른 공간 오버헤드는 최소 수준이지만 계산하기 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-142">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="aa643-143">분할의 포함 여부는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-143">It is not important to include.</span></span>  
  
-   <span data-ttu-id="aa643-144">할당 페이지</span><span class="sxs-lookup"><span data-stu-id="aa643-144">Allocation pages</span></span>  
  
     <span data-ttu-id="aa643-145">힙에 할당된 페이지를 추적하는 데 사용되는 IAM 페이지가 하나 이상 있지만 공간 오버헤드가 최소 수준이며 사용될 IAM 페이지 수를 정확하게 계산할 수 있는 알고리즘이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-145">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="aa643-146">LOB(Large Object) 값</span><span class="sxs-lookup"><span data-stu-id="aa643-146">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="aa643-147">LOB 데이터 형식,,, `varchar(max)` `varbinary(max)` `nvarchar(max)` `text` , **ntextxml**및 값을 저장 하는 데 사용 되는 공간을 정확 하 게 결정 하는 알고리즘은 `image` 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-147">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, **ntextxml**, and `image` values is complex.</span></span> <span data-ttu-id="aa643-148">LOB 값의 예상 평균 크기만 전체 힙 크기에 추가해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-148">It is sufficient to just add the average size of the LOB values that are expected and add that to the total heap size.</span></span>  
  
-   <span data-ttu-id="aa643-149">압축</span><span class="sxs-lookup"><span data-stu-id="aa643-149">Compression</span></span>  
  
     <span data-ttu-id="aa643-150">압축된 힙 크기를 미리 계산할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa643-150">You cannot pre-calculate the size of a compressed heap.</span></span>  
  
-   <span data-ttu-id="aa643-151">스파스 열</span><span class="sxs-lookup"><span data-stu-id="aa643-151">Sparse columns</span></span>  
  
     <span data-ttu-id="aa643-152">스파스 열의 공간 요구 사항은 [Use Sparse Columns](../tables/use-sparse-columns.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aa643-152">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa643-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa643-153">See Also</span></span>  
 <span data-ttu-id="aa643-154">[힙&#40;클러스터형 인덱스가 없는 테이블&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-154">[Heaps &#40;Tables without Clustered Indexes&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span></span>  
 <span data-ttu-id="aa643-155">[클러스터형 및 비클러스터형 인덱스 소개](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-155">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="aa643-156">[클러스터형 인덱스 만들기](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-156">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="aa643-157">[비클러스터형 인덱스 만들기](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-157">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="aa643-158">[테이블 크기 예측](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-158">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="aa643-159">[클러스터형 인덱스의 크기 예측](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-159">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="aa643-160">[비클러스터형 인덱스의 크기 예측](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="aa643-160">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 [<span data-ttu-id="aa643-161">데이터베이스 크기 예측</span><span class="sxs-lookup"><span data-stu-id="aa643-161">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
