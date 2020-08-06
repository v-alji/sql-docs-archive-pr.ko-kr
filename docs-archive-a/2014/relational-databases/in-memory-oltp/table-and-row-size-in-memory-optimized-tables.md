---
title: 메모리 액세스에 최적화된 테이블의 테이블 및 행 크기 | Microsoft 문서
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b0a248a4-4488-4cc8-89fc-46906a8c24a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 74cc40b7d1f2d0132d79d1e9ae15c2321ac9b74a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742048"
---
# <a name="table-and-row-size-in-memory-optimized-tables"></a><span data-ttu-id="a9074-102">메모리 액세스에 최적화된 테이블의 테이블 및 행 크기</span><span class="sxs-lookup"><span data-stu-id="a9074-102">Table and Row Size in Memory-Optimized Tables</span></span>
  <span data-ttu-id="a9074-103">메모리 최적화 테이블은 행의 컬렉션과 행에 대한 포인터를 포함하는 인덱스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-103">A memory-optimized table consists of a collection of rows and indexes that contain pointers to rows.</span></span> <span data-ttu-id="a9074-104">메모리 최적화 테이블에서 행은 8,060바이트를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-104">In a memory-optimized table, rows cannot be longer than 8,060 bytes.</span></span> <span data-ttu-id="a9074-105">메모리 최적화 테이블의 크기를 알면 컴퓨터 메모리가 충분한지 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-105">Understanding the size of a memory-optimized table will help you understand if your computer has enough memory.</span></span>  
  
 <span data-ttu-id="a9074-106">테이블과 행 크기를 계산하는 이유는 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-106">There are two reasons for computing table and row size:</span></span>  
  
-   <span data-ttu-id="a9074-107">테이블에서 사용하는 메모리의 양</span><span class="sxs-lookup"><span data-stu-id="a9074-107">How much memory does a table use?</span></span>  
  
    -   <span data-ttu-id="a9074-108">테이블에서 사용되는 메모리의 양은 정확하게 계산할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-108">The amount of memory used by the table cannot be calculated exactly.</span></span> <span data-ttu-id="a9074-109">여러 가지 요소들이 사용되는 메모리 양에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-109">Many factors affect the amount of memory used.</span></span> <span data-ttu-id="a9074-110">이러한 요소에는 페이지 기반 메모리 할당, 지역성, 캐시 및 패딩 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-110">Factors such as page-based memory allocation, locality, caching, and padding.</span></span> <span data-ttu-id="a9074-111">또한 연관된 활성 트랜잭션을 포함하는 행이나 가비지 수집을 대기 중인 행 등 여러 가지 버전의 행이 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-111">Also, multiple versions of rows that either have active transactions associated or that are waiting for garbage collection.</span></span>  
  
    -   <span data-ttu-id="a9074-112">테이블의 데이터 및 인덱스에 필요한 최소 크기는 아래에서 설명하는 [table size]에 대한 계산으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-112">The minimum size required for the data and indexes in the table is given by the calculation for [table size], discussed below.</span></span>  
  
    -   <span data-ttu-id="a9074-113">메모리 사용량에 대한 계산은 아무리 잘해도 근사값만 얻을 수 있으며, 배포 계획에 용량 계획을 포함하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-113">Calculating memory use is at best an approximation and you are advised to include capacity planning in your deployment plans.</span></span>  
  
-   <span data-ttu-id="a9074-114">행의 데이터 크기 및 8,060바이트 행 크기 제한에 맞는지 여부.</span><span class="sxs-lookup"><span data-stu-id="a9074-114">The data size of a row, and does it fit in the 8,060 byte row size limitation?</span></span> <span data-ttu-id="a9074-115">이 질문에 답변하려면 아래 설명된 [row body size] 계산을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-115">To answer these questions, use the computation for [row body size], discussed below.</span></span>  
  
 <span data-ttu-id="a9074-116">다음 그림에서는 인덱스 및 행을 포함하며 차례로 행 헤더와 본문을 가지는 테이블을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-116">The following figure illustrates a table with indexes and rows, which in turn have row headers and bodies:</span></span>  
  
 <span data-ttu-id="a9074-117">![메모리 액세스에 최적화된 테이블](../../database-engine/media/hekaton-guide-1.gif "메모리 최적화 테이블")</span><span class="sxs-lookup"><span data-stu-id="a9074-117">![Memory optimized table.](../../database-engine/media/hekaton-guide-1.gif "Memory optimized table.")</span></span>  
<span data-ttu-id="a9074-118">인덱스와 행으로 구성된 메모리 액세스에 최적화된 테이블</span><span class="sxs-lookup"><span data-stu-id="a9074-118">Memory-optimized table, consisting of indexes and rows.</span></span>  
  
 <span data-ttu-id="a9074-119">테이블의 메모리 내 크기(바이트)는 다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-119">The in-memory size of a table, in bytes, is computed as follows:</span></span>  
  
```  
[table size] = [size of index 1] + ... + [size of index n] + ([row size] * [row count])  
```  
  
 <span data-ttu-id="a9074-120">해시 인덱스의 크기는 테이블을 만들 때 고정되며 실제 버킷 수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-120">The size of a hash index is fixed at table creation time and depends on the actual bucket count.</span></span> <span data-ttu-id="a9074-121">인덱스 사양으로 지정된 bucket_count는 [실제 버킷 수]를 얻기 위해 가장 가까운 2의 제곱으로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-121">The bucket_count specified with the index specification is rounded up to the nearest power of 2 to obtain the [actual bucket count].</span></span> <span data-ttu-id="a9074-122">예를 들어, 지정된 bucket_count가 100000인 경우 인덱스의 [실제 버킷 수]는 131072입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-122">For example, if the specified bucket_count is 100000, the [actual bucket count] for the index is 131072.</span></span>  
  
```  
[hash index size] = 8 * [actual bucket count]  
```  
  
 <span data-ttu-id="a9074-123">행 크기는 헤더 및 본문을 추가하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-123">The row size is computed by adding the header and the body:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices]  
```  
  
 <span data-ttu-id="a9074-124">**행 본문 크기**</span><span class="sxs-lookup"><span data-stu-id="a9074-124">**Row body size**</span></span>  
  
 <span data-ttu-id="a9074-125">[row body size] 계산은 다음 표에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-125">The calculation of [row body size] is discussed in the following table.</span></span>  
  
 <span data-ttu-id="a9074-126">행 본문 크기는 계산된 크기 및 실제 크기의 두 가지 방식으로 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-126">There are two different computations for row body size: computed size and the actual size:</span></span>  
  
-   <span data-ttu-id="a9074-127">[computed row body size]로 표시되는 계산 크기는 행 크기 제한인 8,060바이트를 초과하는지 여부를 확인하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-127">The computed size, denoted with [computed row body size], is used to determine if the row size limitation of 8,060 bytes is exceeded.</span></span>  
  
-   <span data-ttu-id="a9074-128">[actual row body size]로 표시되는 실제 크기는 메모리 및 검사점 파일에서 행 본문의 실제 스토리지 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-128">The actual size, denoted with [actual row body size], is the actual storage size of the row body in memory and in the checkpoint files.</span></span>  
  
 <span data-ttu-id="a9074-129">[computed row body size] 및 [actual row body size]는 모두 비슷하게 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-129">Both [computed row body size] and [actual row body size] are calculated similarly.</span></span> <span data-ttu-id="a9074-130">유일한 차이점은 다음 표의 하단에 표시된 것처럼 (n)varchar(i) 및 varbinary(i) 열의 크기에 대한 계산입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-130">The only difference is the calculation of the size of (n)varchar(i) and varbinary(i) columns, as reflected at the bottom of the following table.</span></span> <span data-ttu-id="a9074-131">계산된 행 본문 크기는 선언된 크기인 *i* 를 열 크기로 사용하고, 실제 행 본문 크기는 데이터의 실제 크기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-131">The computed row body size uses the declared size *i* as the size of the column, while the actual row body size uses the actual size of the data.</span></span>  
  
 <span data-ttu-id="a9074-132">다음 표에서는 [actual row body size] = SUM([size of shallow types]) + 2 + 2 \* [number of deep type columns]와 같이 행 본문 크기의 계산에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-132">The following table describes the calculation of the row body size, given as [actual row body size] = SUM([size of shallow types]) + 2 + 2 \* [number of deep type columns].</span></span>  
  
|<span data-ttu-id="a9074-133">섹션</span><span class="sxs-lookup"><span data-stu-id="a9074-133">Section</span></span>|<span data-ttu-id="a9074-134">크기</span><span class="sxs-lookup"><span data-stu-id="a9074-134">Size</span></span>|<span data-ttu-id="a9074-135">주석</span><span class="sxs-lookup"><span data-stu-id="a9074-135">Comments</span></span>|  
|-------------|----------|--------------|  
|<span data-ttu-id="a9074-136">단순 형식 열</span><span class="sxs-lookup"><span data-stu-id="a9074-136">Shallow type columns</span></span>|<span data-ttu-id="a9074-137">SUM([size of shallow types])</span><span class="sxs-lookup"><span data-stu-id="a9074-137">SUM([size of shallow types])</span></span><br /><br /> <span data-ttu-id="a9074-138">**개별 형식의 크기는 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="a9074-138">**Size of the individual types is as follows:**</span></span><br /><br /> <span data-ttu-id="a9074-139">Bit &#124; 1</span><span class="sxs-lookup"><span data-stu-id="a9074-139">Bit &#124; 1</span></span><br /><br /> <span data-ttu-id="a9074-140">Tinyint &#124; 1</span><span class="sxs-lookup"><span data-stu-id="a9074-140">Tinyint &#124; 1</span></span><br /><br /> <span data-ttu-id="a9074-141">Smallint &#124; 2</span><span class="sxs-lookup"><span data-stu-id="a9074-141">Smallint &#124; 2</span></span><br /><br /> <span data-ttu-id="a9074-142">Int &#124; 4</span><span class="sxs-lookup"><span data-stu-id="a9074-142">Int &#124; 4</span></span><br /><br /> <span data-ttu-id="a9074-143">Real &#124; 4</span><span class="sxs-lookup"><span data-stu-id="a9074-143">Real &#124; 4</span></span><br /><br /> <span data-ttu-id="a9074-144">Smalldatetime &#124; 4</span><span class="sxs-lookup"><span data-stu-id="a9074-144">Smalldatetime &#124; 4</span></span><br /><br /> <span data-ttu-id="a9074-145">Smallmoney &#124; 4</span><span class="sxs-lookup"><span data-stu-id="a9074-145">Smallmoney &#124; 4</span></span><br /><br /> <span data-ttu-id="a9074-146">Bigint &#124; 8</span><span class="sxs-lookup"><span data-stu-id="a9074-146">Bigint &#124; 8</span></span><br /><br /> <span data-ttu-id="a9074-147">Datetime &#124; 8</span><span class="sxs-lookup"><span data-stu-id="a9074-147">Datetime &#124; 8</span></span><br /><br /> <span data-ttu-id="a9074-148">Datetime2 &#124; 8</span><span class="sxs-lookup"><span data-stu-id="a9074-148">Datetime2 &#124; 8</span></span><br /><br /> <span data-ttu-id="a9074-149">Float 8</span><span class="sxs-lookup"><span data-stu-id="a9074-149">Float 8</span></span><br /><br /> <span data-ttu-id="a9074-150">Money 8</span><span class="sxs-lookup"><span data-stu-id="a9074-150">Money 8</span></span><br /><br /> <span data-ttu-id="a9074-151">숫자 (전체 자릿수 <= 18) &#124; 8</span><span class="sxs-lookup"><span data-stu-id="a9074-151">Numeric (precision <=18) &#124; 8</span></span><br /><br /> <span data-ttu-id="a9074-152">Time &#124; 8</span><span class="sxs-lookup"><span data-stu-id="a9074-152">Time &#124; 8</span></span><br /><br /> <span data-ttu-id="a9074-153">숫자 (전체 자릿수>18) &#124; 16</span><span class="sxs-lookup"><span data-stu-id="a9074-153">Numeric(precision>18) &#124; 16</span></span><br /><br /> <span data-ttu-id="a9074-154">Uniqueidentifier &#124; 16</span><span class="sxs-lookup"><span data-stu-id="a9074-154">Uniqueidentifier &#124; 16</span></span>||  
|<span data-ttu-id="a9074-155">단순 열 패딩</span><span class="sxs-lookup"><span data-stu-id="a9074-155">Shallow column padding</span></span>|<span data-ttu-id="a9074-156">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-156">Possible values are:</span></span><br /><br /> <span data-ttu-id="a9074-157">전체 형식 열이 있고 단순 열의 총 데이터 크기가 홀수인 경우 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-157">1 if there are deep type columns and the total data size of the shallow columns is as odd number.</span></span><br /><br /> <span data-ttu-id="a9074-158">그렇지 않으면 0입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-158">0 otherwise</span></span>|<span data-ttu-id="a9074-159">전체 형식은 (var)binary 및 (n)(var)char 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-159">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="a9074-160">전체 형식 열의 오프셋 배열</span><span class="sxs-lookup"><span data-stu-id="a9074-160">Offset array for deep type columns</span></span>|<span data-ttu-id="a9074-161">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-161">Possible values are:</span></span><br /><br /> <span data-ttu-id="a9074-162">전체 형식 열이 없으면 0입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-162">0 if there are no deep type columns</span></span><br /><br /> <span data-ttu-id="a9074-163">그렇지 않으면 2 + 2 \* [number of deep type columns]입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-163">2 + 2 \* [number of deep type columns] otherwise</span></span>|<span data-ttu-id="a9074-164">전체 형식은 (var)binary 및 (n)(var)char 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-164">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="a9074-165">NULL 배열</span><span class="sxs-lookup"><span data-stu-id="a9074-165">NULL array</span></span>|<span data-ttu-id="a9074-166">[number of nullable columns]/8, 전체 바이트로 반올림</span><span class="sxs-lookup"><span data-stu-id="a9074-166">[number of nullable columns] / 8, rounded up to full bytes.</span></span>|<span data-ttu-id="a9074-167">null 허용 열당 1비트가 배열에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-167">The array has one bit per nullable column.</span></span> <span data-ttu-id="a9074-168">전체 바이트로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-168">This is rounded up to full bytes.</span></span>|  
|<span data-ttu-id="a9074-169">NULL 배열 패딩</span><span class="sxs-lookup"><span data-stu-id="a9074-169">NULL array padding</span></span>|<span data-ttu-id="a9074-170">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-170">Possible values are:</span></span><br /><br /> <span data-ttu-id="a9074-171">전체 형식 열이 있고 NULL 배열의 크기가 홀수 바이트인 경우 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-171">1 if there are deep type columns and the size of the NULL array is an odd number of bytes.</span></span><br /><br /> <span data-ttu-id="a9074-172">그렇지 않으면 0입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-172">0 otherwise</span></span>|<span data-ttu-id="a9074-173">전체 형식은 (var)binary 및 (n)(var)char 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-173">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="a9074-174">안쪽 여백</span><span class="sxs-lookup"><span data-stu-id="a9074-174">Padding</span></span>|<span data-ttu-id="a9074-175">전체 형식 열이 없으면 0</span><span class="sxs-lookup"><span data-stu-id="a9074-175">If there are no deep type columns: 0</span></span><br /><br /> <span data-ttu-id="a9074-176">전체 형식 열이 있는 경우, 단순 열에 필요한 최대 맞춤에 따라 0-7바이트의 패딩이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-176">If there are deep type columns, 0-7 bytes of padding is added, based on the largest alignment required by a shallow column.</span></span> <span data-ttu-id="a9074-177">각 단순 열에는 위에 설명한 대로 해당 크기와 동일한 맞춤이 필요하지만, GUID 열은 16바이트가 아니라 1바이트의 맞춤이 필요하고, 숫자 열에는 항상 16이 아닌 8바이트의 맞춤이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-177">Each shallow column requires alignment equal to its size as documented above, except that GUID columns need alignment of 1 byte (not 16) and numeric columns always need alignment of 8 bytes (never 16).</span></span> <span data-ttu-id="a9074-178">모든 단순 열 사이에 가장 높은 맞춤 요구 사항이 사용되며, 지금까지의 총 크기(전체 형식 열 없음)가 필요한 맞춤의 배수가 되도록 0-7바이트의 패딩이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-178">The largest alignment requirement among all shallow columns is used, and 0-7 bytes of padding is added in such a way that the total size so far (without the deep type columns) is a multiple of the required alignment.</span></span>|<span data-ttu-id="a9074-179">전체 형식은 (var)binary 및 (n)(var)char 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-179">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="a9074-180">고정 길이 전체 형식 열</span><span class="sxs-lookup"><span data-stu-id="a9074-180">Fixed-length deep type columns</span></span>|<span data-ttu-id="a9074-181">SUM([size of fixed length deep type columns])</span><span class="sxs-lookup"><span data-stu-id="a9074-181">SUM([size of fixed length deep type columns])</span></span><br /><br /> <span data-ttu-id="a9074-182">각 열의 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-182">The size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="a9074-183">char(i) 및 binary(i)의 경우 i</span><span class="sxs-lookup"><span data-stu-id="a9074-183">i for char(i) and binary(i).</span></span><br /><br /> <span data-ttu-id="a9074-184">nchar(i)의 경우 2 \* i</span><span class="sxs-lookup"><span data-stu-id="a9074-184">2 \* i for nchar(i)</span></span>|<span data-ttu-id="a9074-185">고정 길이 전체 형식 열은 char(i), nchar(i) 또는 binary(i) 유형의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-185">Fixed-length deep type columns are columns of type char(i), nchar(i), or binary(i).</span></span>|  
|<span data-ttu-id="a9074-186">가변 길이 전체 형식 열 [computed size]</span><span class="sxs-lookup"><span data-stu-id="a9074-186">Variable length deep type columns [computed size]</span></span>|<span data-ttu-id="a9074-187">SUM([computed size of variable length deep type columns])</span><span class="sxs-lookup"><span data-stu-id="a9074-187">SUM([computed size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="a9074-188">각 열에 대해 계산된 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-188">The computed size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="a9074-189">varchar(i) 및 varbinary(i)의 경우 i</span><span class="sxs-lookup"><span data-stu-id="a9074-189">i for varchar(i) and varbinary(i)</span></span><br /><br /> <span data-ttu-id="a9074-190">nvarchar(i)의 경우 2 \* i</span><span class="sxs-lookup"><span data-stu-id="a9074-190">2 \* i for nvarchar(i)</span></span>|<span data-ttu-id="a9074-191">이 행은 [computed row body size]에만 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-191">This row only applied to [computed row body size].</span></span><br /><br /> <span data-ttu-id="a9074-192">가변 길이 전체 형식 열은 varchar(i), nvarchar(i) 또는 varbinary(i) 유형의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-192">Variable-length deep type columns are columns of type varchar(i), nvarchar(i), or varbinary(i).</span></span> <span data-ttu-id="a9074-193">계산된 크기는 열의 최대 길이(i)에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-193">The computed size is determined by the max length (i) of the column.</span></span>|  
|<span data-ttu-id="a9074-194">가변 길이 전체 형식 열 [actual size]</span><span class="sxs-lookup"><span data-stu-id="a9074-194">Variable length deep type columns [actual size]</span></span>|<span data-ttu-id="a9074-195">SUM([actual size of variable length deep type columns])</span><span class="sxs-lookup"><span data-stu-id="a9074-195">SUM([actual size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="a9074-196">각 열의 실제 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-196">The actual size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="a9074-197">n, 여기서 n은 varchar(i)에 대해 열에 저장된 문자 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-197">n, where n is the number of characters stored in the column, for varchar(i).</span></span><br /><br /> <span data-ttu-id="a9074-198">2 \* n, 여기서 n은 nvarchar(i)에 대해 열에 저장된 문자 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-198">2 \* n, where n is the number of characters stored in the column, for nvarchar(i).</span></span><br /><br /> <span data-ttu-id="a9074-199">n, 여기서 n은 varbinary(i)에 대해 열에 저장된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-199">n, where n is the number of bytes stored in the column, for varbinary(i).</span></span>|<span data-ttu-id="a9074-200">이 행은 [actual row body size]에만 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-200">This row only applied to [actual row body size].</span></span><br /><br /> <span data-ttu-id="a9074-201">실제 크기는 행의 열에 저장된 데이터에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-201">The actual size is determined by the data stored in the columns in the row.</span></span>|  
  
##  <a name="row-structure"></a><a name="bkmk_RowStructure"></a><span data-ttu-id="a9074-202">행 구조</span><span class="sxs-lookup"><span data-stu-id="a9074-202">Row Structure</span></span>  
 <span data-ttu-id="a9074-203">메모리 최적화 테이블의 행에는 다음과 같은 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-203">The rows in a memory-optimized table have the following components:</span></span>  
  
-   <span data-ttu-id="a9074-204">행 머리글에는 행 버전 관리를 구현하는 데 필요한 타임스탬프가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-204">The row header contains the timestamp necessary to implement row versioning.</span></span> <span data-ttu-id="a9074-205">행 머리글에는 위에서 설명한 해시 버킷의 행 체인을 구현하는 인덱스 포인터도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-205">The row header also contains the index pointer to implement the row chaining in the hash buckets (described above).</span></span>  
  
-   <span data-ttu-id="a9074-206">행 본문에는 실제 열 데이터가 포함됩니다. 여기에는 Null 허용 열에 대한 Null 배열과 가변 길이 데이터 형식에 대한 오프셋 배열 같은 일부 보조 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-206">The row body contains the actual column data, which includes some auxiliary information like the null array for nullable columns and the offset array for variable-length data types.</span></span>  
  
 <span data-ttu-id="a9074-207">다음 그림에서는 두 개의 인덱스가 있는 테이블에 대한 행 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-207">The following figure illustrates the row structure for a table that has two indexes:</span></span>  
  
 <span data-ttu-id="a9074-208">![두 개의 인덱스가 있는 테이블의 행 구조](../../database-engine/media/hekaton-tables-4.gif "두 개의 인덱스가 있는 테이블의 행 구조")</span><span class="sxs-lookup"><span data-stu-id="a9074-208">![Row structure for a table that has two indexes.](../../database-engine/media/hekaton-tables-4.gif "Row structure for a table that has two indexes.")</span></span>  
  
 <span data-ttu-id="a9074-209">시작 및 종료 타임스탬프는 특정 행 버전의 유효 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-209">The begin and end timestamps indicate the period in which a particular row version is valid.</span></span> <span data-ttu-id="a9074-210">이 기간에 시작되는 트랜잭션은 이 행 버전을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-210">Transactions that start in this interval can see this row version.</span></span> <span data-ttu-id="a9074-211">자세한 내용은 [메모리 액세스에 최적화된 테이블의 트랜잭션](memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9074-211">For more details see [Transactions in Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="a9074-212">인덱스 포인터는 체인에서 해시 버킷에 속한 그 다음 행을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-212">The index pointers point to the next row in the chain belonging to the hash bucket.</span></span> <span data-ttu-id="a9074-213">다음 그림에서는 두 개의 열(이름, 도시)이 있는 테이블의 구조를 보여 줍니다. 여기에는 두 개의 인덱스가 있는데, 하나의 이름 열에 대한 것이고 다른 하나는 도시 열에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-213">The following figure illustrates the structure of a table with two columns (name, city), and with two indexes, one on the column name, and one on the column city.</span></span>  
  
 <span data-ttu-id="a9074-214">![두 개의 열과 인덱스가 있는 테이블의 구조](../../database-engine/media/hekaton-tables-5.gif "두 개의 열과 인덱스가 있는 테이블의 구조")</span><span class="sxs-lookup"><span data-stu-id="a9074-214">![Structure of a table with two columns and indexes.](../../database-engine/media/hekaton-tables-5.gif "Structure of a table with two columns and indexes.")</span></span>  
  
 <span data-ttu-id="a9074-215">이 그림에서는 John과 Jane이라는 이름이 첫 번째 버킷에 해시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-215">In this figure, the names John and Jane are hashed to the first bucket.</span></span> <span data-ttu-id="a9074-216">Susan은 두 번째 버킷에 해시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-216">Susan is hashed to the second bucket.</span></span> <span data-ttu-id="a9074-217">베이징과 보고타는 첫 번째 버킷에 해시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-217">The cities Beijing and Bogota are hashed to the first bucket.</span></span> <span data-ttu-id="a9074-218">파리와 프라하는 두 번째 버킷에 해시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-218">Paris and Prague are hashed to the second bucket.</span></span>  
  
 <span data-ttu-id="a9074-219">따라서 이름에 대한 해시 인덱스의 체인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-219">Thus, the chains for the hash index on name are as follows:</span></span>  
  
-   <span data-ttu-id="a9074-220">첫 번째 버킷: (John, 베이징), (John, 파리), (Jane, 프라하)</span><span class="sxs-lookup"><span data-stu-id="a9074-220">First bucket: (John, Beijing); (John, Paris); (Jane, Prague)</span></span>  
  
-   <span data-ttu-id="a9074-221">두 번째 버킷: (Susan, 보고타)</span><span class="sxs-lookup"><span data-stu-id="a9074-221">Second bucket: (Susan, Bogota)</span></span>  
  
 <span data-ttu-id="a9074-222">도시에 대한 인덱스의 체인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-222">The chains for the index on city are as follows:</span></span>  
  
-   <span data-ttu-id="a9074-223">첫 번째 버킷: (John, 베이징), (Susan, 보고타)</span><span class="sxs-lookup"><span data-stu-id="a9074-223">First bucket: (John, Beijing), (Susan, Bogota)</span></span>  
  
-   <span data-ttu-id="a9074-224">두 번째 버킷: (John, 파리), (Jane, 프라하)</span><span class="sxs-lookup"><span data-stu-id="a9074-224">Second bucket: (John, Paris), (Jane, Prague)</span></span>  
  
 <span data-ttu-id="a9074-225">종료 타임 스탬프 &#x221e; (infinity)는 현재 유효한 버전의 행 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-225">An end timestamp &#x221e; (infinity) indicates that this is the currently valid version of the row.</span></span> <span data-ttu-id="a9074-226">이 행 버전이 기록되었기 때문에 행은 업데이트되거나 삭제되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-226">The row has not been updated or deleted since this row version was written.</span></span>  
  
 <span data-ttu-id="a9074-227">200보다 큰 시간의 경우 테이블에 다음 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-227">For a time greater than 200, the table contains the following rows:</span></span>  
  
|<span data-ttu-id="a9074-228">Name</span><span class="sxs-lookup"><span data-stu-id="a9074-228">Name</span></span>|<span data-ttu-id="a9074-229">City</span><span class="sxs-lookup"><span data-stu-id="a9074-229">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="a9074-230">John</span><span class="sxs-lookup"><span data-stu-id="a9074-230">John</span></span>|<span data-ttu-id="a9074-231">베이징</span><span class="sxs-lookup"><span data-stu-id="a9074-231">Beijing</span></span>|  
|<span data-ttu-id="a9074-232">Jane</span><span class="sxs-lookup"><span data-stu-id="a9074-232">Jane</span></span>|<span data-ttu-id="a9074-233">프라하</span><span class="sxs-lookup"><span data-stu-id="a9074-233">Prague</span></span>|  
  
 <span data-ttu-id="a9074-234">그러나 시작 시간이 100인 활성 트랜잭션은 다음 버전의 테이블을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-234">However, any active transaction with begin time 100 will see the following version of the table:</span></span>  
  
|<span data-ttu-id="a9074-235">Name</span><span class="sxs-lookup"><span data-stu-id="a9074-235">Name</span></span>|<span data-ttu-id="a9074-236">City</span><span class="sxs-lookup"><span data-stu-id="a9074-236">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="a9074-237">John</span><span class="sxs-lookup"><span data-stu-id="a9074-237">John</span></span>|<span data-ttu-id="a9074-238">파리</span><span class="sxs-lookup"><span data-stu-id="a9074-238">Paris</span></span>|  
|<span data-ttu-id="a9074-239">Jane</span><span class="sxs-lookup"><span data-stu-id="a9074-239">Jane</span></span>|<span data-ttu-id="a9074-240">프라하</span><span class="sxs-lookup"><span data-stu-id="a9074-240">Prague</span></span>|  
|<span data-ttu-id="a9074-241">Susan</span><span class="sxs-lookup"><span data-stu-id="a9074-241">Susan</span></span>|<span data-ttu-id="a9074-242">보고타</span><span class="sxs-lookup"><span data-stu-id="a9074-242">Bogata</span></span>|  
  
##  <a name="example-table-and-row-size-computation"></a><a name="bkmk_ExampleComputation"></a> <span data-ttu-id="a9074-243">예제: 테이블 및 행 크기 계산</span><span class="sxs-lookup"><span data-stu-id="a9074-243">Example: Table and Row Size Computation</span></span>  
 <span data-ttu-id="a9074-244">해시 인덱스의 경우 실제 버킷 수는 가장 가까운 2의 제곱으로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-244">For hash indexes, the actual bucket count is rounded up to the nearest power of 2.</span></span> <span data-ttu-id="a9074-245">예를 들어, 지정된 bucket_count가 100000인 경우 인덱스의 실제 버킷 수는 131072입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-245">For example, if the specified bucket_count is 100000, the actual bucket count for the index is 131072.</span></span>  
  
 <span data-ttu-id="a9074-246">다음 정의의 Orders 테이블을 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="a9074-246">Consider an Orders table with the following definition:</span></span>  
  
```sql  
CREATE TABLE dbo.Orders (  
     OrderID int NOT NULL   
           PRIMARY KEY NONCLUSTERED,  
     CustomerID int NOT NULL   
           INDEX IX_CustomerID HASH WITH (BUCKET_COUNT=10000),  
     OrderDate datetime NOT NULL,  
     OrderDescription nvarchar(1000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="a9074-247">이 테이블에는 1개의 해시 인덱스와 1개의 비클러스터형 인덱스(기본 키)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-247">Notice that this table has one hash index and a nonclustered index (the primary key).</span></span> <span data-ttu-id="a9074-248">또한 3개의 고정 길이 열과 1개의 가변 길이 열이 포함되며, 이러한 열 중 하나는 Null 허용으로 구성됩니다(OrderDescription).</span><span class="sxs-lookup"><span data-stu-id="a9074-248">It also has three fixed-length columns and one variable-length column, with one of the columns being NULLable (OrderDescription).</span></span> <span data-ttu-id="a9074-249">Orders 테이블에는 8379 개의 행이 있고 OrderDescription 열에 있는 값의 평균 길이는 78 자 라고 가정 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-249">Let's assume the Orders table has 8379 rows, and the average length of the values in the OrderDescription column is 78 characters.</span></span>  
  
 <span data-ttu-id="a9074-250">테이블 크기를 결정하려면 먼저 인덱스 크기를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-250">To determine the table size, first determine the size of the indexes.</span></span> <span data-ttu-id="a9074-251">두 인덱스의 bucket_count는 10000으로 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-251">The bucket_count for both indexes is specified as 10000.</span></span> <span data-ttu-id="a9074-252">가장 가까운 2의 제곱인 16384로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-252">This is rounded up to the nearest power of 2: 16384.</span></span> <span data-ttu-id="a9074-253">따라서 Orders 테이블에서 인덱스의 총 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-253">Therefore, the total size of the indexes for the Orders table is:</span></span>  
  
```  
8 * 16384 = 131072 bytes  
```  
  
 <span data-ttu-id="a9074-254">남은 것은 테이블 데이터 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-254">What remains is the table data size, which is,</span></span>  
  
```  
[row size] * [row count] = [row size] * 8379  
```  
  
 <span data-ttu-id="a9074-255">예제 테이블에는 8379개 행이 있습니다. 이제 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-255">(The example table has 8379 rows.) Now, we have:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices] = 24 + 8 * 1 = 32 bytes  
```  
  
 <span data-ttu-id="a9074-256">그러면 이제 [actual row body size]를 계산해보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-256">Next, let's calculate [actual row body size]:</span></span>  
  
-   <span data-ttu-id="a9074-257">단순 형식 열:</span><span class="sxs-lookup"><span data-stu-id="a9074-257">Shallow type columns:</span></span>  
  
    ```  
    SUM([size of shallow types]) = 4 [int] + 4 [int] + 8 [datetime] = 16  
    ```  
  
-   <span data-ttu-id="a9074-258">총 단순 열 크기는 짝수이므로 단순 열 패딩은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-258">Shallow column padding is 0, as the total shallow column size is even.</span></span>  
  
-   <span data-ttu-id="a9074-259">전체 형식 열의 오프셋 배열:</span><span class="sxs-lookup"><span data-stu-id="a9074-259">Offset array for deep type columns:</span></span>  
  
    ```  
    2 + 2 * [number of deep type columns] = 2 + 2 * 1 = 4  
    ```  
  
-   <span data-ttu-id="a9074-260">NULL 배열은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-260">NULL array = 1</span></span>  
  
-   <span data-ttu-id="a9074-261">NULL 배열 크기가 홀수이고 전체 형식 열이 있으므로 NULL 배열 패딩은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-261">NULL array padding = 1, as the NULL array size is odd and there is a deep type column.</span></span>  
  
-   <span data-ttu-id="a9074-262">안쪽 여백</span><span class="sxs-lookup"><span data-stu-id="a9074-262">Padding</span></span>  
  
    -   <span data-ttu-id="a9074-263">가장 큰 맞춤 요구 사항은 8입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-263">8 is the largest alignment requirement.</span></span>  
  
    -   <span data-ttu-id="a9074-264">지금까지 크기는 16 + 0 + 4 + 1 + 1 = 22입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-264">Size so far is 16 + 0 + 4 + 1 + 1 = 22.</span></span>  
  
    -   <span data-ttu-id="a9074-265">8의 가장 가까운 배수는 24입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-265">Nearest multiple of 8 is 24.</span></span>  
  
    -   <span data-ttu-id="a9074-266">총 패딩은 24 - 22 = 2바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-266">Total padding is 24 - 22 = 2 bytes.</span></span>  
  
-   <span data-ttu-id="a9074-267">고정 길이 전체 형식 열은 없습니다(고정 길이 전체 형식 열은 0임).</span><span class="sxs-lookup"><span data-stu-id="a9074-267">There are no fixed-length deep type columns (Fixed-length deep type columns: 0.).</span></span>  
  
-   <span data-ttu-id="a9074-268">전체 형식 열의 실제 크기는 2 \* 78 = 156입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-268">The actual size of deep type column is 2 \* 78 = 156.</span></span> <span data-ttu-id="a9074-269">단일 전체 형식 열 OrderDescription의 형식은 nvarchar입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-269">The single deep type column OrderDescription has type nvarchar.</span></span>  
  
```  
[actual row body size] = 24 + 156 = 180 bytes  
```  
  
 <span data-ttu-id="a9074-270">계산을 완료하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-270">To complete the calculation:</span></span>  
  
```  
[row size] = 32 + 180 = 212 bytes  
[table size] = 8 * 16384 + 212 * 8379 = 131072 + 1776348 = 1907420  
```  
  
 <span data-ttu-id="a9074-271">메모리에서 총 테이블 크기는 약 2MB입니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-271">Total table size in memory is thus approximately 2 megabytes.</span></span> <span data-ttu-id="a9074-272">여기에는 메모리 할당으로 발생하는 잠재적인 오버헤드와 이 테이블에 액세스하는 트랜잭션에 필요한 행 버전 관리가 고려되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-272">This does not account for potential overhead incurred by memory allocation as well as any row versioning required for the transactions accessing this table.</span></span>  
  
 <span data-ttu-id="a9074-273">이 테이블 및 해당 인덱스에 할당되어 사용되는 실제 메모리는 다음 쿼리를 통해 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9074-273">The actual memory allocated for and used by this table and its indexes can be obtained through the following query:</span></span>  
  
```sql  
select * from sys.dm_db_xtp_table_memory_stats  
where object_id = object_id('dbo.Orders')  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9074-274">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9074-274">See Also</span></span>  
 [<span data-ttu-id="a9074-275">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="a9074-275">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
