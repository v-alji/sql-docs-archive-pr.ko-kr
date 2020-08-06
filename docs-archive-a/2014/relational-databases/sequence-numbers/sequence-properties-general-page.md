---
title: 시퀀스 속성(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sequence.general.f1
ms.assetid: 0187f413-cdf0-48a2-b2e6-9b3578cd5811
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc969dc09663da8150461529ad1e1f1fb094539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741683"
---
# <a name="sequence-properties-general-page"></a><span data-ttu-id="19b72-102">시퀀스 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="19b72-102">Sequence Properties (General Page)</span></span>
  <span data-ttu-id="19b72-103">시퀀스 개체를 만들고 해당 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-103">Creates a sequence object and specifies its properties.</span></span> <span data-ttu-id="19b72-104">시퀀스는 시퀀스를 만들 때 사용된 사양에 따라 숫자 값의 시퀀스를 생성하는 사용자 정의 스키마 바운드 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-104">A sequence is a user-defined schema bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="19b72-105">숫자 값의 시퀀스는 정의된 간격에 따라 오름차순이나 내림차순으로 생성되며, 시퀀스가 모두 사용되면 다시 시작(순환)되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-105">The sequence of numeric values is generated in an ascending or descending order at a defined interval and can be configured to restart (cycle) when exhausted.</span></span> <span data-ttu-id="19b72-106">ID 열과 달리 시퀀스는 특정 테이블과 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-106">Sequences, unlike identity columns, are not associated with specific tables.</span></span> <span data-ttu-id="19b72-107">애플리케이션에서는 시퀀스 개체를 참조하여 다음 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-107">Applications refer to a sequence object to retrieve its next value.</span></span> <span data-ttu-id="19b72-108">시퀀스와 테이블 간의 관계는 애플리케이션에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-108">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="19b72-109">사용자 애플리케이션에서는 시퀀스 개체를 참조하고 여러 행 및 테이블에서 값을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-109">User applications can reference a sequence object and coordinate the values across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="19b72-110">행을 삽입할 때 생성되는 ID 열 값과는 달리 애플리케이션에서는 [NEXT VALUE FOR 함수](/sql/t-sql/functions/next-value-for-transact-sql)를 호출하여 행을 삽입하지 않고도 다음 시퀀스 번호를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-110">Unlike identity columns values which are generated at the time of insert, an application can obtain the next sequence number without inserting the row by calling the [NEXT VALUE FOR function](/sql/t-sql/functions/next-value-for-transact-sql).</span></span> <span data-ttu-id="19b72-111">여러 시퀀스 번호를 한 번에 가져오려면 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-111">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="19b72-112">**CREATE SEQUENCE** 및 **NEXT VALUE FOR** 함수를 함께 사용하는 시나리오에 대한 자세한 내용은 [시퀀스 번호](sequence-numbers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19b72-112">For information and scenarios that use both **CREATE SEQUENCE** and the **NEXT VALUE FOR** function, see [Sequence Numbers](sequence-numbers.md).</span></span>  
  
 <span data-ttu-id="19b72-113">이 페이지는 개체 탐색기에서 **시퀀스** 를 마우스 오른쪽 단추로 클릭한 다음 **새 시퀀스**를 클릭하거나 기존 시퀀스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하는 두 가지 방법으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-113">This page is accessed in two ways: either by right-clicking **Sequences** in Object Explorer and clicking **New Sequence**, or by right-clicking an existing sequence and clicking **Properties**.</span></span> <span data-ttu-id="19b72-114">기존 시퀀스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 경우에는 옵션을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-114">When you right-click an existing sequence and click **Properties**, the options are not editable.</span></span> <span data-ttu-id="19b72-115">시퀀스 옵션을 변경하려면 [ALTER SEQUENCE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) 문을 사용하거나 시퀀스 개체를 삭제한 후 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-115">To change the sequence options use the [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) statement or drop and recreate the sequence object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19b72-116">옵션</span><span class="sxs-lookup"><span data-stu-id="19b72-116">Options</span></span>  
 <span data-ttu-id="19b72-117">**시퀀스 이름**</span><span class="sxs-lookup"><span data-stu-id="19b72-117">**Sequence name**</span></span>  
 <span data-ttu-id="19b72-118">시퀀스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-118">Enter the sequence name here.</span></span>  
  
 <span data-ttu-id="19b72-119">**시퀀스 스키마**</span><span class="sxs-lookup"><span data-stu-id="19b72-119">**Sequence schema**</span></span>  
 <span data-ttu-id="19b72-120">이 시퀀스를 소유할 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-120">Specify the schema that will own this sequence.</span></span>  
  
 <span data-ttu-id="19b72-121">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="19b72-121">**Data type**</span></span>  
 <span data-ttu-id="19b72-122">시퀀스는 모든 정수 유형으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-122">A sequence can be defined as any integer type.</span></span> <span data-ttu-id="19b72-123">다음 내용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-123">This includes:</span></span>  
  
|<span data-ttu-id="19b72-124">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="19b72-124">Data type</span></span>|<span data-ttu-id="19b72-125">범위</span><span class="sxs-lookup"><span data-stu-id="19b72-125">Range</span></span>|  
|---------------|-----------|  
|`tinyint`|<span data-ttu-id="19b72-126">0 ~ 255</span><span class="sxs-lookup"><span data-stu-id="19b72-126">0 to 255</span></span>|  
|`smallint`|<span data-ttu-id="19b72-127">–32,768 ~ 32,767</span><span class="sxs-lookup"><span data-stu-id="19b72-127">-32,768 to 32,767</span></span>|  
|`int`|<span data-ttu-id="19b72-128">–2,147,483,648 ~ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="19b72-128">-2,147,483,648 to 2,147,483,647</span></span>|  
|`bigint`|<span data-ttu-id="19b72-129">–9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="19b72-129">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|  
  
-   <span data-ttu-id="19b72-130">`decimal` 또는 소수 자릿수가 0인 `numeric`</span><span class="sxs-lookup"><span data-stu-id="19b72-130">`decimal` or `numeric` with a scale of 0.</span></span>  
  
-   <span data-ttu-id="19b72-131">다음 형식 중 하나에 기반을 둔 사용자 정의 데이터 형식(별칭 유형)</span><span class="sxs-lookup"><span data-stu-id="19b72-131">Any user-defined data type (alias type) that is based on one of these types.</span></span>  
  
 <span data-ttu-id="19b72-132">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="19b72-132">**Precision**</span></span>  
 <span data-ttu-id="19b72-133">`decimal` 또는 `numeric` 데이터 형식의 경우 전체 자릿수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-133">For `decimal` or `numeric` data types, specify the precision.</span></span> <span data-ttu-id="19b72-134">소수 자릿수는 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-134">(The scale is always 0.)</span></span>  
  
 <span data-ttu-id="19b72-135">**시작 값**</span><span class="sxs-lookup"><span data-stu-id="19b72-135">**Start with value**</span></span>  
 <span data-ttu-id="19b72-136">시퀀스 개체가 반환할 첫 번째 값입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-136">The first value that will be returned by the sequence object.</span></span> <span data-ttu-id="19b72-137">**START** 값은 시퀀스 개체의 최대값보다 작거나 같고 최소값보다 크거나 같은 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-137">The **START** value must be a value that is less than or equal to the maximum and greater than or equal to the minimum value of the sequence object.</span></span> <span data-ttu-id="19b72-138">새 시퀀스 개체의 기본 시작 값은 오름차순 시퀀스 개체에 대해서는 최소값이고, 내림차순 시퀀스 개체에 대해서는 최대값입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-138">The default start value for a new sequence object is the minimum value for an ascending sequence object and the maximum value for a descending sequence object.</span></span>  
  
 <span data-ttu-id="19b72-139">**증가값**</span><span class="sxs-lookup"><span data-stu-id="19b72-139">**Increment by**</span></span>  
 <span data-ttu-id="19b72-140">각각의 **NEXT VALUE FOR** 함수 호출에 대해 시퀀스 개체의 값을 증가시키거나 감소시키는(음수인 경우) 데 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-140">The value that is used to increment (or decrement if negative) the value of the sequence object for each call to the **NEXT VALUE FOR** function.</span></span> <span data-ttu-id="19b72-141">증가값이 음수이면 시퀀스 개체가 내림차순이고, 그렇지 않으면 오름차순입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-141">If the increment is a negative value the sequence object is descending, otherwise, it is ascending.</span></span> <span data-ttu-id="19b72-142">증가값은 0일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-142">The increment cannot be 0.</span></span>  
  
 <span data-ttu-id="19b72-143">**최솟값**</span><span class="sxs-lookup"><span data-stu-id="19b72-143">**Minimum value**</span></span>  
 <span data-ttu-id="19b72-144">시퀀스 개체의 경계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-144">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="19b72-145">새 시퀀스 개체의 기본 최소값은 해당 시퀀스 개체의 데이터 형식에 대한 최소값입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-145">The default minimum value for a new sequence object is the minimum value of the data type of the sequence object.</span></span> <span data-ttu-id="19b72-146">`tinyint` 형식에 대해서는 0이고 다른 모든 데이터 형식에 대해서는 음수입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-146">This is zero for the `tinyint` data type and a negative number for all other data types.</span></span>  
  
 <span data-ttu-id="19b72-147">**최댓값**</span><span class="sxs-lookup"><span data-stu-id="19b72-147">**Maximum value**</span></span>  
 <span data-ttu-id="19b72-148">시퀀스 개체의 경계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-148">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="19b72-149">새 시퀀스 개체의 기본 최대값은 해당 시퀀스 개체의 데이터 형식에 대한 최대값입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-149">The default maximum value for a new sequence object is the maximum value of the data type of the sequence object.</span></span>  
  
 <span data-ttu-id="19b72-150">**제한에 도달하면 시퀀스 순환 다시 시작**</span><span class="sxs-lookup"><span data-stu-id="19b72-150">**Cycle-sequence will restart on reaching limit**</span></span>  
 <span data-ttu-id="19b72-151">최소값 또는 최대값을 초과하는 경우 시퀀스 개체가 최소값 또는 최대값(내림차순 시퀀스 개체의 경우)에서 다시 시작할 수 있도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-151">Select to allow the sequence object to restart from the minimum value (or maximum for descending sequence objects) when its minimum or maximum value is exceeded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19b72-152">시작 값이 아니라 최소값/최대값에서 순환이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-152">Cycling does not restart from the start value but rather from the minimum/maximum value.</span></span>  
  
 <span data-ttu-id="19b72-153">**캐시 옵션**</span><span class="sxs-lookup"><span data-stu-id="19b72-153">**Cache options**</span></span>  
 <span data-ttu-id="19b72-154">시퀀스 값 캐시를 만들면 시퀀스 번호를 만드는 데 필요한 디스크 I/O 수를 최소화하여 시퀀스 개체를 사용하는 애플리케이션의 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-154">Creating a cache of sequence values can increase performance for applications that use sequence objects by minimizing the number of disk IOs that are required to create sequence numbers.</span></span>  
  
-   <span data-ttu-id="19b72-155">기본 캐시 크기 - [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 크기를 선택하지만 선택의 일관성이 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-155">Default cache size - The [!INCLUDE[ssDE](../../includes/ssde-md.md)] will select a size, however users should not rely upon the selection being consistent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="19b72-156">는 캐시 크기 계산 방법을 예고 없이 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-156">might change the method of calculating the cache size without notice.</span></span>  
  
-   <span data-ttu-id="19b72-157">캐시 없음 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 시퀀스 번호를 캐시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-157">No cache - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will not cache sequence numbers.</span></span>  
  
-   <span data-ttu-id="19b72-158">캐시 크기 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 시퀀스 값을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-158">Cache with size - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will cache sequence values.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="19b72-159">는 현재 값 및 캐시에 남아 있는 값의 개수를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-159">keeps track of the current value and the number of values left in the cache.</span></span> <span data-ttu-id="19b72-160">따라서 캐시 저장에 필요한 메모리 양은 항상 시퀀스 개체 데이터 형식의 인스턴스 두 개입니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-160">Therefore, the amount of memory that is required to store the cache is always two instances of the data type of the sequence object</span></span>  
  
 <span data-ttu-id="19b72-161">CACHE 옵션을 사용하여 만들 경우 전원 오류와 같은 예기치 않은 종료로 인해 캐시의 시퀀스 번호가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-161">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="19b72-162">CREATE SEQUENCE 옵션에 대한 자세한 내용은 [CREATE SEQUENCE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19b72-162">For additional information about the create sequence options, see [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="19b72-163">사용 권한</span><span class="sxs-lookup"><span data-stu-id="19b72-163">Permissions</span></span>  
 <span data-ttu-id="19b72-164">SCHEMA에 대한 **CREATE SEQUENCE**, **ALTER**또는 **CONTROL** 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="19b72-164">Requires **CREATE SEQUENCE**, **ALTER**, or **CONTROL** permission on the SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b72-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19b72-165">See Also</span></span>  
 [<span data-ttu-id="19b72-166">sys.sequences&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19b72-166">sys.sequences &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)  
  
  
