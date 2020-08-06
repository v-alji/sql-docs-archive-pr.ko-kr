---
title: 클러스터형 인덱스의 크기 예측 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d224c5ae55cc5ec7690ca0962cbc2130bac22e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742191"
---
# <a name="estimate-the-size-of-a-clustered-index"></a><span data-ttu-id="72bab-102">클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="72bab-102">Estimate the Size of a Clustered Index</span></span>
  <span data-ttu-id="72bab-103">다음 단계를 사용하여 클러스터형 인덱스에 데이터를 저장하는 데 필요한 공간을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-103">You can use the following steps to estimate the amount of space that is required to store data in a clustered index:</span></span>  
  
1.  <span data-ttu-id="72bab-104">클러스터형 인덱스의 리프 수준에 데이터를 저장하는 데 사용되는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-104">Calculate the space used to store data in the leaf level of the clustered index.</span></span>  
  
2.  <span data-ttu-id="72bab-105">클러스터형 인덱스에 대한 인덱스 정보를 저장하는 데 사용되는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-105">Calculate the space used to store index information for the clustered index.</span></span>  
  
3.  <span data-ttu-id="72bab-106">계산된 값을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-106">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a><span data-ttu-id="72bab-107">1단계.</span><span class="sxs-lookup"><span data-stu-id="72bab-107">Step 1.</span></span> <span data-ttu-id="72bab-108">리프 수준에 데이터를 저장하는 데 사용되는 공간 계산</span><span class="sxs-lookup"><span data-stu-id="72bab-108">Calculate the Space Used to Store Data in the Leaf Level</span></span>  
  
1.  <span data-ttu-id="72bab-109">테이블의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-109">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="72bab-110">***Num_Rows***  = 테이블의 행 수</span><span class="sxs-lookup"><span data-stu-id="72bab-110">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="72bab-111">고정 길이 및 가변 길이 열 수를 지정하고 이러한 열을 스토리지하는 데 필요한 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-111">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="72bab-112">이러한 각 열 그룹이 데이터 행 내에서 차지하는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-112">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="72bab-113">열 크기는 지정된 데이터 형식과 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-113">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="72bab-114">***Num_Cols***  = 열의 총 수(고정 길이 및 가변 길이)</span><span class="sxs-lookup"><span data-stu-id="72bab-114">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="72bab-115">***Fixed_Data_Size***  = 모든 고정 길이 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="72bab-115">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="72bab-116">***Num_Variable_Cols***  = 가변 길이 열의 수</span><span class="sxs-lookup"><span data-stu-id="72bab-116">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="72bab-117">***Max_Var_Size***  = 모든 가변 길이 열의 최대 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="72bab-117">***Max_Var_Size***  = maximum byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="72bab-118">클러스터형 인덱스가 고유하지 않은 경우 *uniqueifier* 열을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-118">If the clustered index is nonunique, account for the *uniqueifier* column:</span></span>  
  
     <span data-ttu-id="72bab-119">uniqueifier는 Null을 허용하는 가변 길이 열입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-119">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="72bab-120">고유하지 않은 키 값이 있는 행에서 이 열은 Null이 아니며 크기는 4바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-120">It will be nonnull and 4 bytes in size in rows that have nonunique key values.</span></span> <span data-ttu-id="72bab-121">이 값은 인덱스 키의 일부이며 모든 행에 고유 키 값이 있는지 확인하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-121">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="72bab-122">***Num_Cols***  = ***Num_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="72bab-122">***Num_Cols***  = ***Num_Cols*** + 1</span></span>  
  
     <span data-ttu-id="72bab-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="72bab-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span></span>  
  
     <span data-ttu-id="72bab-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="72bab-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span></span>  
  
     <span data-ttu-id="72bab-125">이러한 수정에서는 모든 값이 고유하지 않다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-125">These modifications assume that all values will be nonunique.</span></span>  
  
4.  <span data-ttu-id="72bab-126">행의 Null 비트맵 부분은 열의 Null 허용 여부 관리를 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-126">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="72bab-127">다음과 같이 이 부분의 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-127">Calculate its size:</span></span>  
  
     <span data-ttu-id="72bab-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="72bab-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="72bab-129">위 식의 정수 부분만 사용하고 나머지는 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-129">Only the integer part of the previous expression should be used; discard any remainder.</span></span>  
  
5.  <span data-ttu-id="72bab-130">가변 길이 데이터 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-130">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="72bab-131">테이블에 가변 길이 열이 있는 경우에는 해당 행 안에 열을 저장하는 데 사용되는 공간을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-131">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="72bab-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="72bab-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="72bab-133">***Max_Var_Size*** 에 추가된 바이트는 각 변수 열을 추적하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-133">The bytes added to ***Max_Var_Size*** are for tracking each variable column.</span></span> <span data-ttu-id="72bab-134">이 수식에서는 모든 가변 길이 열이 100% 꽉 찬 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-134">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="72bab-135">사용할 가변 길이 열 스토리지 공간 비율이 더 적을 것으로 예상되는 경우 해당 비율로 ***Max_Var_Size*** 값을 조정하여 전체 테이블 크기를 보다 정확하게 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-135">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72bab-136">정의된 총 테이블 너비가 8,060바이트를 초과하는 `varchar`, `nvarchar`, `varbinary` 또는 `sql_variant` 열을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-136">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="72bab-137">이러한 각 열의 길이는 `varchar`, `varbinary` 또는 `sql_variant` 열의 경우 8,000바이트 이내여야 하고 `nvarchar` 열의 경우 4,000바이트 이내여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-137">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="72bab-138">그러나 결합된 너비는 테이블의 8,060바이트 제한을 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-138">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="72bab-139">가변 길이 열이 없는 경우에는 ***Variable_Data_Size*** 를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-139">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="72bab-140">전체 행 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-140">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="72bab-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="72bab-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="72bab-142">값 4는 데이터 행의 행 머리글 오버헤드입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-142">The value 4 is the row header overhead of a data row.</span></span>  
  
7.  <span data-ttu-id="72bab-143">페이지당 행 수를 계산합니다. 페이지당 사용 가능한 바이트 수는 8,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-143">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="72bab-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="72bab-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="72bab-145">행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 행 수는 가장 근사한 정수 값으로 내림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-145">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="72bab-146">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-146">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
8.  <span data-ttu-id="72bab-147">지정한 [채우기 비율](../indexes/specify-fill-factor-for-an-index.md) 을 기준으로 페이지당 예약된 사용 가능한 행 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-147">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="72bab-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="72bab-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="72bab-149">계산에 사용되는 채우기 비율은 백분율이 아닌 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-149">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="72bab-150">행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 행 수는 가장 근사한 정수 값으로 내림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-150">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="72bab-151">채우기 비율이 클수록 각 페이지에 더 많은 데이터가 저장되고 페이지 수는 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-151">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="72bab-152">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-152">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
9. <span data-ttu-id="72bab-153">모든 행을 저장하는 데 필요한 페이지 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-153">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="72bab-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="72bab-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="72bab-155">예상 페이지 수는 가장 근사한 전체 페이지로 올림되어 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-155">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
10. <span data-ttu-id="72bab-156">리프 수준에 데이터를 저장하는 데 필요한 공간을 계산합니다. 페이지당 총 바이트 수는 8,192바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-156">Calculate the amount of space that is required to store the data in the leaf level (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="72bab-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="72bab-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a><span data-ttu-id="72bab-158">2단계.</span><span class="sxs-lookup"><span data-stu-id="72bab-158">Step 2.</span></span> <span data-ttu-id="72bab-159">인덱스 정보를 저장하는 데 사용되는 공간 계산</span><span class="sxs-lookup"><span data-stu-id="72bab-159">Calculate the Space Used to Store Index Information</span></span>  
 <span data-ttu-id="72bab-160">다음 단계를 사용하여 인덱스의 상위 수준을 저장하는 데 필요한 공간을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-160">You can use the following steps to estimate the amount of space that is required to store the upper levels of the index:</span></span>  
  
1.  <span data-ttu-id="72bab-161">인덱스 키의 고정 길이 및 가변 길이 열 수를 지정하고 이러한 열을 스토리지하는 데 필요한 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-161">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="72bab-162">인덱스의 키 열은 고정 길이 및 가변 길이 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-162">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="72bab-163">내부 수준 인덱스 행 크기를 예측하려면 인덱스 행 내에서 이러한 각 열 그룹이 차지하는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-163">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="72bab-164">열 크기는 지정된 데이터 형식과 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-164">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="72bab-165">***Num_Key_Cols***  = 키 열의 총 수(고정 길이 및 가변 길이)</span><span class="sxs-lookup"><span data-stu-id="72bab-165">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="72bab-166">***Fixed_Key_Size***  = 모든 고정 길이 키 열의 총 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="72bab-166">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="72bab-167">***Num_Variable_Key_Cols***  = 가변 길이 키 열의 수</span><span class="sxs-lookup"><span data-stu-id="72bab-167">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="72bab-168">***Max_Var_Key_Size***  = 모든 가변 길이 키 열의 최대 바이트 크기</span><span class="sxs-lookup"><span data-stu-id="72bab-168">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
2.  <span data-ttu-id="72bab-169">인덱스가 고유하지 않은 경우 필요한 uniqueifier를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-169">Account for any uniqueifier needed if the index is nonunique:</span></span>  
  
     <span data-ttu-id="72bab-170">uniqueifier는 Null을 허용하는 가변 길이 열입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-170">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="72bab-171">고유하지 않은 인덱스 키 값이 있는 행에서 이 열은 Null이 아니며 크기는 4바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-171">It will be nonnull and 4 bytes in size in rows that have nonunique index key values.</span></span> <span data-ttu-id="72bab-172">이 값은 인덱스 키의 일부이며 모든 행에 고유 키 값이 있는지 확인하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-172">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="72bab-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="72bab-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="72bab-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="72bab-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="72bab-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="72bab-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span></span>  
  
     <span data-ttu-id="72bab-176">이러한 수정에서는 모든 값이 고유하지 않다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-176">These modifications assume that all values will be nonunique.</span></span>  
  
3.  <span data-ttu-id="72bab-177">Null 비트맵 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-177">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="72bab-178">인덱스 키에 Null을 허용하는 열이 있으면 인덱스 행의 일부가 Null 비트맵용으로 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-178">If there are nullable columns in the index key, part of the index row is reserved for the null bitmap.</span></span> <span data-ttu-id="72bab-179">다음과 같이 이 부분의 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-179">Calculate its size:</span></span>  
  
     <span data-ttu-id="72bab-180">***Index_Null_Bitmap***  = 2 + ((인덱스 행의 열 수 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="72bab-180">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="72bab-181">위 식의 정수 부분만 사용하고</span><span class="sxs-lookup"><span data-stu-id="72bab-181">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="72bab-182">나머지는 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-182">Discard any remainder.</span></span>  
  
     <span data-ttu-id="72bab-183">Null을 허용하는 키 열이 없으면 ***Index_Null_Bitmap*** 을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-183">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
4.  <span data-ttu-id="72bab-184">가변 길이 데이터 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-184">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="72bab-185">인덱스에 가변 길이 열이 있는 경우에는 해당 인덱스 행 안에 열을 저장하는 데 사용되는 공간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-185">If there are variable-length columns in the index, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="72bab-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="72bab-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="72bab-187">***Max_Var_Key_Size*** 에 추가된 바이트는 각 가변 길이 열을 추적하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-187">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="72bab-188">이 수식에서는 모든 가변 길이 열이 100% 꽉 찬 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-188">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="72bab-189">사용할 가변 길이 열 스토리지 공간 비율이 더 적을 것으로 예상되는 경우 해당 비율로 ***Max_Var_Key_Size*** 값을 조정하여 전체 테이블 크기를 보다 정확하게 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-189">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="72bab-190">가변 길이 열이 없는 경우에는 ***Variable_Key_Size*** 를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-190">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="72bab-191">인덱스 행 크기를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-191">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="72bab-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1(인덱스 행의 행 머리글 오버헤드) + 6(자식 페이지 ID 포인터)</span><span class="sxs-lookup"><span data-stu-id="72bab-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="72bab-193">페이지당 인덱스 행 수를 계산합니다. 페이지당 사용 가능한 바이트 수는 8,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-193">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="72bab-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="72bab-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="72bab-195">인덱스 행이 여러 페이지에 걸쳐 배치되지는 않으므로 페이지당 인덱스 행 수는 가장 근사한 정수 값으로 버림하여 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-195">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="72bab-196">수식에서 값 2는 페이지의 슬롯 배열에서 행의 입력을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-196">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="72bab-197">인덱스의 수준 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-197">Calculate the number of levels in the index:</span></span>  
  
     <span data-ttu-id="72bab-198">***비 leaf_Levels*** = 1 + 로그 Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="72bab-198">***Non-leaf_Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="72bab-199">이 값을 가장 근사한 정수로 올립니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-199">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="72bab-200">클러스터형 인덱스의 리프 수준은 이 값에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-200">This value does not include the leaf level of the clustered index.</span></span>  
  
8.  <span data-ttu-id="72bab-201">인덱스의 비-리프 페이지 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-201">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="72bab-202">***Num_Index_Pages =*** ∑ level ***(Num_Leaf_Pages/(Index_Rows_Per_Page***<sup>수준</sup>***))***</span><span class="sxs-lookup"><span data-stu-id="72bab-202">***Num_Index_Pages =*** ∑Level ***(Num_Leaf_Pages / (Index_Rows_Per_Page***<sup>Level</sup>***))***</span></span>  
  
     <span data-ttu-id="72bab-203">여기서 1 <= Level <= ***Non-leaf_Levels***</span><span class="sxs-lookup"><span data-stu-id="72bab-203">where 1 <= Level <= ***Non-leaf_Levels***</span></span>  
  
     <span data-ttu-id="72bab-204">각 피가수를 가장 근사한 정수로 올립니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-204">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="72bab-205">간단한 예로, ***Num_Leaf_Pages*** = 1000 및 ***Index_Rows_Per_Page*** = 25인 인덱스를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-205">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="72bab-206">리프 수준 위 첫 번째 인덱스 수준에 인덱스 행이 1000개 저장되고 리프 페이지당 인덱스 행 1개씩, 각 페이지마다 인덱스 행 25개가 들어갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-206">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="72bab-207">이러한 경우 인덱스 행 1000개를 저장하는 데 40페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-207">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="72bab-208">인덱스의 다음 수준에서는 40개 행을 저장해야 하므로</span><span class="sxs-lookup"><span data-stu-id="72bab-208">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="72bab-209">2페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-209">This means it requires 2 pages.</span></span> <span data-ttu-id="72bab-210">인덱스의 최종 수준에서는 2개 행을 저장해야 하므로</span><span class="sxs-lookup"><span data-stu-id="72bab-210">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="72bab-211">한 페이지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-211">This means it requires 1 page.</span></span> <span data-ttu-id="72bab-212">결과적으로 비-리프 인덱스 페이지 43개가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-212">This gives 43 non-leaf index pages.</span></span> <span data-ttu-id="72bab-213">앞의 수식에 이 숫자들을 사용하면 다음과 같은 결과가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-213">When these numbers are used in the previous formulas, the outcome is as follows:</span></span>  
  
     <span data-ttu-id="72bab-214">***비 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="72bab-214">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="72bab-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>) + 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43 (예제에 설명 된 페이지 수)</span><span class="sxs-lookup"><span data-stu-id="72bab-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
9. <span data-ttu-id="72bab-216">인덱스 크기를 계산합니다. 페이지당 총 바이트 수는 8,192바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="72bab-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="72bab-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-3-total-the-calculated-values"></a><span data-ttu-id="72bab-218">3단계.</span><span class="sxs-lookup"><span data-stu-id="72bab-218">Step 3.</span></span> <span data-ttu-id="72bab-219">계산된 값을 더하기</span><span class="sxs-lookup"><span data-stu-id="72bab-219">Total the Calculated Values</span></span>  
 <span data-ttu-id="72bab-220">위의 두 단계에서 얻은 값을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-220">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="72bab-221">클러스터형 인덱스 크기(바이트) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="72bab-221">Clustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="72bab-222">이 계산에서 다음 사항은 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-222">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="72bab-223">분할</span><span class="sxs-lookup"><span data-stu-id="72bab-223">Partitioning</span></span>  
  
     <span data-ttu-id="72bab-224">분할에 따른 공간 오버헤드는 최소 수준이지만 계산하기 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-224">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="72bab-225">분할의 포함 여부는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-225">It is not important to include.</span></span>  
  
-   <span data-ttu-id="72bab-226">할당 페이지</span><span class="sxs-lookup"><span data-stu-id="72bab-226">Allocation pages</span></span>  
  
     <span data-ttu-id="72bab-227">힙에 할당된 페이지를 추적하는 데 사용되는 IAM 페이지가 하나 이상 있지만 공간 오버헤드가 최소 수준이며 사용될 IAM 페이지 수를 정확하게 계산할 수 있는 알고리즘이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-227">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="72bab-228">LOB(Large Object) 값</span><span class="sxs-lookup"><span data-stu-id="72bab-228">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="72bab-229">LOB 데이터 형식 `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml` 및 `image` 값을 저장하는 데 사용될 공간을 정확하게 측정하는 알고리즘은 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-229">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="72bab-230">예상되는 LOB 값의 평균 크기를 더하고 ***Num_Rows***를 곱한 후 해당 값을 총 클러스터형 인덱스 크기에 더하는 것만으로도 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-230">It is sufficient to just add the average size of the LOB values that are expected, multiply by ***Num_Rows***, and add that to the total clustered index size.</span></span>  
  
-   <span data-ttu-id="72bab-231">압축</span><span class="sxs-lookup"><span data-stu-id="72bab-231">Compression</span></span>  
  
     <span data-ttu-id="72bab-232">압축된 인덱스 크기를 미리 계산할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bab-232">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="72bab-233">스파스 열</span><span class="sxs-lookup"><span data-stu-id="72bab-233">Sparse columns</span></span>  
  
     <span data-ttu-id="72bab-234">스파스 열의 공간 요구 사항은 [Use Sparse Columns](../tables/use-sparse-columns.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="72bab-234">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bab-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72bab-235">See Also</span></span>  
 <span data-ttu-id="72bab-236">[클러스터형 및 비클러스터형 인덱스 소개](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-236">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="72bab-237">[테이블 크기 예측](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-237">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="72bab-238">[클러스터형 인덱스 만들기](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-238">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="72bab-239">[비클러스터형 인덱스 만들기](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-239">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="72bab-240">[비클러스터형 인덱스의 크기 예측](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-240">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 <span data-ttu-id="72bab-241">[힙 크기 예측](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="72bab-241">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="72bab-242">데이터베이스 크기 예측</span><span class="sxs-lookup"><span data-stu-id="72bab-242">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
