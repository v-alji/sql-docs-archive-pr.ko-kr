---
title: 비클러스터형 인덱스의 크기 예측 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 097c0e5568ba17b12f83d09e347eb3bf8b0bd7da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736376"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a><span data-ttu-id="6ac14-102">비클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="6ac14-102">Estimate the Size of a Nonclustered Index</span></span>
  <span data-ttu-id="6ac14-103">다음 단계에 따라 비클러스터형 인덱스를 저장하는 데 필요한 공간을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-103">Follow these steps to estimate the amount of space that is required to store a nonclustered index:</span></span>  
  
1.  <span data-ttu-id="6ac14-104">2단계와 3단계에서 사용할 변수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-104">Calculate variables for use in steps 2 and 3.</span></span>  
  
2.  <span data-ttu-id="6ac14-105">비클러스터형 인덱스의 리프 수준에 인덱스 정보를 저장하는 데 사용되는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-105">Calculate the space used to store index information in the leaf level of the nonclustered index.</span></span>  
  
3.  <span data-ttu-id="6ac14-106">비클러스터형 인덱스의 리프가 아닌 수준에서 인덱스 정보를 저장하는 데 사용되는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-106">Calculate the space used to store index information in the non-leaf levels of the nonclustered index.</span></span>  
  
4.  <span data-ttu-id="6ac14-107">계산된 값을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-107">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a><span data-ttu-id="6ac14-108">1단계.</span><span class="sxs-lookup"><span data-stu-id="6ac14-108">Step 1.</span></span> <span data-ttu-id="6ac14-109">2단계와 3단계에 사용할 변수 계산</span><span class="sxs-lookup"><span data-stu-id="6ac14-109">Calculate Variables for Use in Steps 2 and 3</span></span>  
 <span data-ttu-id="6ac14-110">다음 단계를 사용하여 인덱스의 상위 수준 저장에 필요한 공간을 예측하는 데 사용되는 변수를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-110">You can use the following steps to calculate variables that are used to estimate the amount of space that is required to store the upper levels of the index.</span></span>  
  
1.  <span data-ttu-id="6ac14-111">테이블의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-111">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="6ac14-112">***Num_Rows***  = 테이블의 행 수</span><span class="sxs-lookup"><span data-stu-id="6ac14-112">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="6ac14-113">인덱스 키의 고정 길이 및 가변 길이 열 수를 지정하고 이러한 열을 스토리지하는 데 필요한 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-113">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="6ac14-114">인덱스의 키 열은 고정 길이 및 가변 길이 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-114">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="6ac14-115">내부 수준 인덱스 행 크기를 예측하려면 인덱스 행 내에서 이러한 각 열 그룹이 차지하는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-115">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="6ac14-116">열 크기는 지정된 데이터 형식과 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-116">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="6ac14-117">***Num_Key_Cols***  = 키 열의 총 수(고정 길이 및 가변 길이)</span><span class="sxs-lookup"><span data-stu-id="6ac14-117">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="6ac14-118">***Fixed_Key_Size***  = 모든 고정 길이 키 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="6ac14-118">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="6ac14-119">***Num_Variable_Key_Cols***  = 가변 길이 키 열의 수</span><span class="sxs-lookup"><span data-stu-id="6ac14-119">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="6ac14-120">***Max_Var_Key_Size***  = 모든 가변 길이 키 열의 최대 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="6ac14-120">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
3.  <span data-ttu-id="6ac14-121">인덱스가 고유하지 않은 경우 필요한 데이터 행 로케이터를 다음과 같이 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-121">Account for the data row locator that is required if the index is nonunique:</span></span>  
  
     <span data-ttu-id="6ac14-122">비클러스터형 인덱스가 고유하지 않은 경우 데이터 행 로케이터가 비클러스터형 인덱스 키와 결합되어 각 행에 대한 고유 키 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-122">If the nonclustered index is nonunique, the data row locator is combined with the nonclustered index key to produce a unique key value for every row.</span></span>  
  
     <span data-ttu-id="6ac14-123">비클러스터형 인덱스가 힙에 있는 경우 데이터 행 로케이터는 힙 RID입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-123">If the nonclustered index is over a heap, the data row locator is the heap RID.</span></span> <span data-ttu-id="6ac14-124">크기는 8바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-124">This is a size of 8 bytes.</span></span>  
  
     <span data-ttu-id="6ac14-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="6ac14-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="6ac14-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="6ac14-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="6ac14-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="6ac14-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span></span>  
  
     <span data-ttu-id="6ac14-128">비클러스터형 인덱스가 클러스터형 인덱스에 있는 경우 데이터 행 로케이터는 클러스터링 키입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-128">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="6ac14-129">비클러스터형 인덱스 키와 결합되어야 하는 열은 비클러스터형 인덱스 키 열 집합에 아직 없는 클러스터링 키의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-129">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="6ac14-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + 비클러스터형 인덱스 키 열 집합에 없는 클러스터링 키 열의 수 + 1(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="6ac14-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + 비클러스터형 인덱스 키 열 집합에 없는 고정 길이 클러스터링 키 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="6ac14-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="6ac14-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 비클러스터형 인덱스 키 열 집합에 없는 가변 길이 클러스터링 키 열의 수 + 1(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="6ac14-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 비클러스터형 인덱스 키 열 집합에 없는 가변 길이 클러스터링 키 열의 최대 바이트 크기 + 4(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
4.  <span data-ttu-id="6ac14-134">행의 Null 비트맵 부분은 열의 Null 허용 여부 관리를 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-134">Part of the row, known as the null bitmap, may be reserved to manage column nullability.</span></span> <span data-ttu-id="6ac14-135">다음과 같이 이 부분의 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-135">Calculate its size:</span></span>  
  
     <span data-ttu-id="6ac14-136">인덱스 키에 Null을 허용하는 열이 있으면 1.3단계에서 설명한 것처럼 필요한 모든 클러스터링 키 열을 포함하여 인덱스 행의 일부가 Null 비트맵용으로 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-136">If there are nullable columns in the index key, including any necessary clustering key columns as described in Step 1.3, part of the index row is reserved for the null bitmap.</span></span>  
  
     <span data-ttu-id="6ac14-137">***Index_Null_Bitmap***  = 2 + ((인덱스 행의 열 수 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="6ac14-137">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="6ac14-138">위 식의 정수 부분만 사용하고</span><span class="sxs-lookup"><span data-stu-id="6ac14-138">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="6ac14-139">나머지는 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-139">Discard any remainder.</span></span>  
  
     <span data-ttu-id="6ac14-140">Null을 허용하는 키 열이 없으면 ***Index_Null_Bitmap*** 을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-140">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
5.  <span data-ttu-id="6ac14-141">가변 길이 데이터 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-141">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="6ac14-142">인덱스 키에 가변 길이 열이 있는 경우에는 필요한 모든 클러스터형 인덱스 키 열을 포함하여 해당 인덱스 행 안에 열을 저장하는 데 사용되는 공간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-142">If there are variable-length columns in the index key, including any necessary clustered index key columns, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="6ac14-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="6ac14-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="6ac14-144">***Max_Var_Key_Size*** 에 추가된 바이트는 각 변수 열을 추적하기 위한 것입니다. 이 수식에서는 모든 가변 길이 열이 100% 꽉 찬 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-144">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="6ac14-145">사용할 가변 길이 열 스토리지 공간 비율이 더 적을 것으로 예상되는 경우 해당 비율로 ***Max_Var_Key_Size*** 값을 조정하여 전체 테이블 크기를 보다 정확하게 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-145">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="6ac14-146">가변 길이 열이 없는 경우에는 ***Variable_Key_Size*** 를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-146">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="6ac14-147">인덱스 행 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-147">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="6ac14-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1(인덱스 행의 행 머리글 오버헤드) + 6(자식 페이지 ID 포인터)</span><span class="sxs-lookup"><span data-stu-id="6ac14-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
7.  <span data-ttu-id="6ac14-149">페이지당 인덱스 행 수를 계산합니다. 페이지당 사용 가능한 바이트 수는 8,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-149">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="6ac14-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="6ac14-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="6ac14-151">인덱스 행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 인덱스 행 수는 가장 근사한 정수 값으로 버림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-151">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="6ac14-152">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-152">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a><span data-ttu-id="6ac14-153">2단계.</span><span class="sxs-lookup"><span data-stu-id="6ac14-153">Step 2.</span></span> <span data-ttu-id="6ac14-154">리프 수준에 인덱스 정보를 저장하는 데 사용되는 공간 계산</span><span class="sxs-lookup"><span data-stu-id="6ac14-154">Calculate the Space Used to Store Index Information in the Leaf Level</span></span>  
 <span data-ttu-id="6ac14-155">다음 단계를 사용하여 인덱스의 리프 수준을 저장하는 데 필요한 공간을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-155">You can use the following steps to estimate the amount of space that is required to store the leaf level of the index.</span></span> <span data-ttu-id="6ac14-156">이 단계를 완료하려면 1단계에서 보관된 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-156">You will need the values preserved from Step 1 to complete this step.</span></span>  
  
1.  <span data-ttu-id="6ac14-157">리프 수준의 고정 길이 및 가변 길이 열 수를 지정하고 이러한 열을 스토리지하는 데 필요한 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-157">Specify the number of fixed-length and variable-length columns at the leaf level and calculate the space that is required for their storage:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ac14-158">인덱스 키 열과 함께 키가 아닌 열을 포함하여 비클러스터형 인덱스를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-158">You can extend a nonclustered index by including nonkey columns in addition to the index key columns.</span></span> <span data-ttu-id="6ac14-159">이러한 추가 열은 비클러스터형 인덱스의 리프 수준에만 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-159">These additional columns are only stored at the leaf level of the nonclustered index.</span></span> <span data-ttu-id="6ac14-160">자세한 내용은 [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ac14-160">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ac14-161">정의된 총 테이블 너비가 8,060바이트를 초과하는 `varchar`, `nvarchar`, `varbinary` 또는 `sql_variant` 열을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-161">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="6ac14-162">이러한 각 열의 길이는 `varchar`, `varbinary` 또는 `sql_variant` 열의 경우 8,000바이트 이내여야 하고 `nvarchar` 열의 경우 4,000바이트 이내여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-162">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="6ac14-163">그러나 결합된 너비는 테이블의 8,060바이트 제한을 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-163">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span> <span data-ttu-id="6ac14-164">이 규정은 포괄 열이 있는 비클러스터형 인덱스 리프 행에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-164">This also applies to nonclustered index leaf rows that have included columns.</span></span>  
  
     <span data-ttu-id="6ac14-165">비클러스터형 인덱스에 포괄 열이 없는 경우 1단계의 값을 사용하되 해당 값에 1.3단계에서 결정된 모든 수정 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-165">If the nonclustered index does not have any included columns, use the values from Step 1, including any modifications determined in Step 1.3:</span></span>  
  
     <span data-ttu-id="6ac14-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="6ac14-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span></span>  
  
     <span data-ttu-id="6ac14-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="6ac14-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span></span>  
  
     <span data-ttu-id="6ac14-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="6ac14-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span></span>  
  
     <span data-ttu-id="6ac14-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="6ac14-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="6ac14-170">비클러스터형 인덱스에 포괄 열이 있는 경우 1.3단계에서 결정된 모든 수정 내용이 적용된 1단계의 값에 적절한 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-170">If the nonclustered index does have included columns, add the appropriate values to the values from Step 1, including any modifications in Step 1.3.</span></span> <span data-ttu-id="6ac14-171">열 크기는 지정된 데이터 형식과 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-171">The size of a column depends on the data type and length specification.</span></span> <span data-ttu-id="6ac14-172">자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ac14-172">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
     <span data-ttu-id="6ac14-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + 포괄 열의 수</span><span class="sxs-lookup"><span data-stu-id="6ac14-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + number of included columns</span></span>  
  
     <span data-ttu-id="6ac14-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + 고정 길이 포괄 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="6ac14-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length included columns</span></span>  
  
     <span data-ttu-id="6ac14-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + 가변 길이 포괄 열의 수</span><span class="sxs-lookup"><span data-stu-id="6ac14-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length included columns</span></span>  
  
     <span data-ttu-id="6ac14-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + 가변 길이 포괄 열의 최대 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="6ac14-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length included columns</span></span>  
  
2.  <span data-ttu-id="6ac14-177">다음과 같이 데이터 행 로케이터를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-177">Account for the data row locator:</span></span>  
  
     <span data-ttu-id="6ac14-178">비클러스터형 인덱스가 고유하지 않은 경우 데이터 행 로케이터의 오버헤드는 1.3단계에서 이미 고려되어 추가적인 수정이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-178">If the nonclustered index is nonunique, the overhead for the data row locator has already been considered in Step 1.3 and no additional modifications are required.</span></span> <span data-ttu-id="6ac14-179">다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-179">Go to the next step.</span></span>  
  
     <span data-ttu-id="6ac14-180">비클러스터형 인덱스가 고유한 경우 리프 수준의 모든 행에 대해 데이터 행 로케이터를 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-180">If the nonclustered index is unique, the data row locator must be accounted for in all rows at the leaf level.</span></span>  
  
     <span data-ttu-id="6ac14-181">비클러스터형 인덱스가 힙에 있는 경우 데이터 행 로케이터는 힙 RID(크기 8바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-181">If the nonclustered index is over a heap, the data row locator is the heap RID (size 8 bytes).</span></span>  
  
     <span data-ttu-id="6ac14-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="6ac14-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="6ac14-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="6ac14-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="6ac14-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="6ac14-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span></span>  
  
     <span data-ttu-id="6ac14-185">비클러스터형 인덱스가 클러스터형 인덱스에 있는 경우 데이터 행 로케이터는 클러스터링 키입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-185">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="6ac14-186">비클러스터형 인덱스 키와 결합되어야 하는 열은 비클러스터형 인덱스 키 열 집합에 아직 없는 클러스터링 키의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-186">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="6ac14-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 비클러스터형 인덱스 키 열 집합에 없는 클러스터링 키 열의 수 + 1(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="6ac14-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + 비클러스터형 인덱스 키 열 집합에 없는 고정 길이 클러스터링 키 열의 수</span><span class="sxs-lookup"><span data-stu-id="6ac14-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + number of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="6ac14-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 비클러스터형 인덱스 키 열 집합에 없는 가변 길이 클러스터링 키 열의 수 + 1(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="6ac14-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 비클러스터형 인덱스 키 열 집합에 없는 가변 길이 클러스터링 키 열의 바이트 크기 + 4(클러스터형 인덱스가 고유하지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="6ac14-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + size in bytes of the variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
3.  <span data-ttu-id="6ac14-191">Null 비트맵 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-191">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="6ac14-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="6ac14-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="6ac14-193">위 식의 정수 부분만 사용하고</span><span class="sxs-lookup"><span data-stu-id="6ac14-193">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="6ac14-194">나머지는 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-194">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="6ac14-195">가변 길이 데이터 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-195">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="6ac14-196">인덱스 키에 가변 길이 열이 있는 경우에는 2.2단계에서 이미 설명한 것처럼 필요한 클러스터링 키 열을 포함하여 해당 인덱스 행 내에 열을 저장하는 데 사용되는 공간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-196">If there are variable-length columns in the index key, including any necessary clustering key columns as described previously in Step 2.2, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="6ac14-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span><span class="sxs-lookup"><span data-stu-id="6ac14-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span></span>  
  
     <span data-ttu-id="6ac14-198">***Max_Var_Key_Size*** 에 추가된 바이트는 각 변수 열을 추적하기 위한 것입니다. 이 수식에서는 모든 가변 길이 열이 100% 꽉 찬 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-198">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="6ac14-199">사용할 가변 길이 열 스토리지 공간 비율이 더 적을 것으로 예상되는 경우 해당 비율로 ***Max_Var_Leaf_Size*** 값을 조정하여 전체 테이블 크기를 보다 정확하게 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-199">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Leaf_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="6ac14-200">가변 길이 열이 없는 경우에는 ***Variable_Leaf_Size*** 를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-200">If there are no variable-length columns, set ***Variable_Leaf_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="6ac14-201">인덱스 행 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-201">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="6ac14-202">***Leaf_Row_Size***   =  ***Fixed_Leaf_Size***  +  ***Variable_Leaf_Size***  +  ***Leaf_Null_Bitmap*** + 1 (인덱스 행의 행 머리글 오버 헤드) + 6 (자식 페이지 ID 포인터)</span><span class="sxs-lookup"><span data-stu-id="6ac14-202">***Leaf_Row_Size***  = ***Fixed_Leaf_Size*** + ***Variable_Leaf_Size*** + ***Leaf_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="6ac14-203">페이지당 인덱스 행 수를 계산합니다. 페이지당 사용 가능한 바이트 수는 8,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-203">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="6ac14-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="6ac14-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="6ac14-205">인덱스 행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 인덱스 행 수는 가장 근사한 정수 값으로 버림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-205">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="6ac14-206">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-206">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="6ac14-207">지정한 [채우기 비율](../indexes/specify-fill-factor-for-an-index.md) 을 기준으로 페이지당 예약된 사용 가능한 행 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-207">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="6ac14-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="6ac14-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="6ac14-209">계산에 사용되는 채우기 비율은 백분율이 아닌 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-209">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="6ac14-210">행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 행 수는 가장 근사한 정수 값으로 내림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-210">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="6ac14-211">채우기 비율이 클수록 각 페이지에 더 많은 데이터가 저장되고 페이지 수는 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-211">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="6ac14-212">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-212">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
8.  <span data-ttu-id="6ac14-213">모든 행을 저장하는 데 필요한 페이지 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-213">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="6ac14-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="6ac14-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="6ac14-215">예상 페이지 수는 가장 근사한 전체 페이지로 올림되어 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-215">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
9. <span data-ttu-id="6ac14-216">인덱스 크기를 계산합니다. 페이지당 총 바이트 수는 8,192바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="6ac14-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="6ac14-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a><span data-ttu-id="6ac14-218">3단계.</span><span class="sxs-lookup"><span data-stu-id="6ac14-218">Step 3.</span></span> <span data-ttu-id="6ac14-219">리프가 아닌 수준에 인덱스 정보를 저장하는 데 사용되는 공간 계산</span><span class="sxs-lookup"><span data-stu-id="6ac14-219">Calculate the Space Used to Store Index Information in the Non-leaf Levels</span></span>  
 <span data-ttu-id="6ac14-220">다음 단계에 따라 중간 및 루트 수준의 인덱스를 저장하는 데 필요한 공간을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-220">Follow these steps to estimate the amount of space that is required to store the intermediate and root levels of the index.</span></span> <span data-ttu-id="6ac14-221">이 단계를 완료하려면 2단계 및 3단계에서 보관된 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-221">You will need the values preserved from steps 2 and 3 to complete this step.</span></span>  
  
1.  <span data-ttu-id="6ac14-222">인덱스의 리프가 아닌 수준의 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-222">Calculate the number of non-leaf levels in the index:</span></span>  
  
     <span data-ttu-id="6ac14-223">***리프가 아닌 수준*** = 1 + 로그 Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="6ac14-223">***Non-leaf Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="6ac14-224">이 값을 가장 근사한 정수로 올립니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-224">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="6ac14-225">비클러스터형 인덱스의 리프 수준은 이 값에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-225">This value does not include the leaf level of the nonclustered index.</span></span>  
  
2.  <span data-ttu-id="6ac14-226">인덱스의 비-리프 페이지 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-226">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="6ac14-227">***Num_Index_Pages*** = ∑ level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>수준</sup>) 여기서 1 <***= 수준 <= 수준***</span><span class="sxs-lookup"><span data-stu-id="6ac14-227">***Num_Index_Pages***  = ∑Level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>Level</sup>)where 1 <= Level <= ***Levels***</span></span>  
  
     <span data-ttu-id="6ac14-228">각 피가수를 가장 근사한 정수로 올립니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-228">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="6ac14-229">간단한 예로, ***Num_Leaf_Pages*** = 1000 및 ***Index_Rows_Per_Page*** = 25인 인덱스를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-229">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="6ac14-230">리프 수준 위 첫 번째 인덱스 수준에 인덱스 행이 1000개 저장되고 리프 페이지당 인덱스 행 1개씩, 각 페이지마다 인덱스 행 25개가 들어갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-230">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="6ac14-231">이러한 경우 인덱스 행 1000개를 저장하는 데 40페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-231">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="6ac14-232">인덱스의 다음 수준에서는 40개 행을 저장해야 하므로</span><span class="sxs-lookup"><span data-stu-id="6ac14-232">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="6ac14-233">2페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-233">This means that it requires 2 pages.</span></span> <span data-ttu-id="6ac14-234">인덱스의 최종 수준에서는 2개 행을 저장해야 하므로</span><span class="sxs-lookup"><span data-stu-id="6ac14-234">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="6ac14-235">1페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-235">This means that it requires 1 page.</span></span> <span data-ttu-id="6ac14-236">결과적으로 비-리프 인덱스 페이지가 43개 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-236">This yields 43 non-leaf index pages.</span></span> <span data-ttu-id="6ac14-237">앞의 수식에 이 숫자들을 사용하면 다음 결과가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-237">When these numbers are used in the previous formulas, the result is as follows:</span></span>  
  
     <span data-ttu-id="6ac14-238">***비 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="6ac14-238">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="6ac14-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>) + 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43 (예제에 설명 된 페이지 수)</span><span class="sxs-lookup"><span data-stu-id="6ac14-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
3.  <span data-ttu-id="6ac14-240">인덱스 크기를 계산합니다. 페이지당 총 바이트 수는 8,192바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-240">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="6ac14-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="6ac14-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-4-total-the-calculated-values"></a><span data-ttu-id="6ac14-242">4단계.</span><span class="sxs-lookup"><span data-stu-id="6ac14-242">Step 4.</span></span> <span data-ttu-id="6ac14-243">계산된 값을 더하기</span><span class="sxs-lookup"><span data-stu-id="6ac14-243">Total the Calculated Values</span></span>  
 <span data-ttu-id="6ac14-244">위의 두 단계에서 얻은 값을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-244">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="6ac14-245">비클러스터형 인덱스 크기(바이트) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="6ac14-245">Nonclustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="6ac14-246">이 계산에서 다음 사항은 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-246">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="6ac14-247">분할</span><span class="sxs-lookup"><span data-stu-id="6ac14-247">Partitioning</span></span>  
  
     <span data-ttu-id="6ac14-248">분할에 따른 공간 오버헤드는 최소 수준이지만 계산하기 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-248">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="6ac14-249">분할의 포함 여부는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-249">It is not important to include.</span></span>  
  
-   <span data-ttu-id="6ac14-250">할당 페이지</span><span class="sxs-lookup"><span data-stu-id="6ac14-250">Allocation pages</span></span>  
  
     <span data-ttu-id="6ac14-251">힙에 할당된 페이지를 추적하는 데 사용되는 IAM 페이지가 하나 이상 있지만 공간 오버헤드가 최소 수준이며 사용될 IAM 페이지 수를 정확하게 계산할 수 있는 알고리즘이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-251">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="6ac14-252">LOB(Large Object) 값</span><span class="sxs-lookup"><span data-stu-id="6ac14-252">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="6ac14-253">LOB 데이터 형식 `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml` 및 `image` 값을 저장하는 데 사용될 공간을 정확하게 측정하는 알고리즘은 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-253">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="6ac14-254">예상되는 LOB 값의 평균 크기를 더하고 ***Num_Rows***를 곱한 후 해당 값을 총 비클러스터형 인덱스 크기에 더하는 것만으로도 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-254">It is sufficient to just add the average size of the LOB values expected, multiply by ***Num_Rows***, and add that to the total nonclustered index size.</span></span>  
  
-   <span data-ttu-id="6ac14-255">압축</span><span class="sxs-lookup"><span data-stu-id="6ac14-255">Compression</span></span>  
  
     <span data-ttu-id="6ac14-256">압축된 인덱스 크기를 미리 계산할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac14-256">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="6ac14-257">스파스 열</span><span class="sxs-lookup"><span data-stu-id="6ac14-257">Sparse columns</span></span>  
  
     <span data-ttu-id="6ac14-258">스파스 열의 공간 요구 사항은 [Use Sparse Columns](../tables/use-sparse-columns.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ac14-258">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac14-259">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ac14-259">See Also</span></span>  
 <span data-ttu-id="6ac14-260">[클러스터형 및 비클러스터형 인덱스 소개](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-260">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="6ac14-261">[비클러스터형 인덱스 만들기](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-261">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="6ac14-262">[클러스터형 인덱스 만들기](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-262">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="6ac14-263">[테이블 크기 예측](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-263">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="6ac14-264">[클러스터형 인덱스의 크기 예측](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-264">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="6ac14-265">[힙 크기 예측](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="6ac14-265">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="6ac14-266">데이터베이스 크기 예측</span><span class="sxs-lookup"><span data-stu-id="6ac14-266">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
