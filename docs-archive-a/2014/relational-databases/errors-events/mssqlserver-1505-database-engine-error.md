---
title: MSSQLSERVER_1505 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c152404cf2d3710bbe98b29da7a96d86f58859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730727"
---
# <a name="mssqlserver_1505"></a><span data-ttu-id="21e56-102">MSSQLSERVER_1505</span><span class="sxs-lookup"><span data-stu-id="21e56-102">MSSQLSERVER_1505</span></span>
    
## <a name="details"></a><span data-ttu-id="21e56-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="21e56-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21e56-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="21e56-104">Product Name</span></span>|<span data-ttu-id="21e56-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="21e56-105">SQL Server</span></span>|  
|<span data-ttu-id="21e56-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="21e56-106">Event ID</span></span>|<span data-ttu-id="21e56-107">1505</span><span class="sxs-lookup"><span data-stu-id="21e56-107">1505</span></span>|  
|<span data-ttu-id="21e56-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="21e56-108">Event Source</span></span>|<span data-ttu-id="21e56-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="21e56-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="21e56-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="21e56-110">Component</span></span>|<span data-ttu-id="21e56-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="21e56-111">SQLEngine</span></span>|  
|<span data-ttu-id="21e56-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="21e56-112">Symbolic Name</span></span>|<span data-ttu-id="21e56-113">DUP_KEY</span><span class="sxs-lookup"><span data-stu-id="21e56-113">DUP_KEY</span></span>|  
|<span data-ttu-id="21e56-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="21e56-114">Message Text</span></span>|<span data-ttu-id="21e56-115">개체 이름 '%.\*ls' 및 인덱스 이름 '%.\*ls'에 키가 중복되므로 CREATE UNIQUE INDEX 문이 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-115">CREATE UNIQUE INDEX terminated because a duplicate key was found for object name '%.\*ls' and index name '%.\*ls'.</span></span>  <span data-ttu-id="21e56-116">중복 키 값은 %ls입니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-116">The duplicate key value is %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21e56-117">설명</span><span class="sxs-lookup"><span data-stu-id="21e56-117">Explanation</span></span>  
 <span data-ttu-id="21e56-118">이 오류는 고유 인덱스를 만들려고 했지만 테이블에 지정된 중복 값을 가진 행이 두 개 이상 있는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-118">This error occurs when you attempt to create a unique index and more than one row in the table contains the specified duplicate value.</span></span> <span data-ttu-id="21e56-119">고유 인덱스는 인덱스를 만들고 UNIQUE 키워드를 지정하거나 UNIQUE 제약 조건을 만들 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-119">A unique index is created when you create an index and specify the UNIQUE keyword, or when you create a UNIQUE constraint.</span></span> <span data-ttu-id="21e56-120">테이블은 인덱스 또는 제약 조건에 정의된 열에 중복 값이 있는 행을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-120">The table cannot contain any rows that have duplicate values in the columns defined in the index or constraint.</span></span>  
  
 <span data-ttu-id="21e56-121">다음과 같은 **Employee** 테이블의 데이터를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-121">Consider the data in the following **Employee** table:</span></span>  
  
|<span data-ttu-id="21e56-122">LastName</span><span class="sxs-lookup"><span data-stu-id="21e56-122">LastName</span></span>|<span data-ttu-id="21e56-123">FirstName</span><span class="sxs-lookup"><span data-stu-id="21e56-123">FirstName</span></span>|<span data-ttu-id="21e56-124">JobTitle</span><span class="sxs-lookup"><span data-stu-id="21e56-124">JobTitle</span></span>|<span data-ttu-id="21e56-125">HireDate</span><span class="sxs-lookup"><span data-stu-id="21e56-125">HireDate</span></span>|  
|--------------|---------------|--------------|--------------|  
|<span data-ttu-id="21e56-126">Walters</span><span class="sxs-lookup"><span data-stu-id="21e56-126">Walters</span></span>|<span data-ttu-id="21e56-127">Rob</span><span class="sxs-lookup"><span data-stu-id="21e56-127">Rob</span></span>|<span data-ttu-id="21e56-128">Senior Tool Designer</span><span class="sxs-lookup"><span data-stu-id="21e56-128">Senior Tool Designer</span></span>|<span data-ttu-id="21e56-129">2004-11-19</span><span class="sxs-lookup"><span data-stu-id="21e56-129">2004-11-19</span></span>|  
|<span data-ttu-id="21e56-130">Brown</span><span class="sxs-lookup"><span data-stu-id="21e56-130">Brown</span></span>|<span data-ttu-id="21e56-131">Kevin</span><span class="sxs-lookup"><span data-stu-id="21e56-131">Kevin</span></span>|<span data-ttu-id="21e56-132">Marketing Assistant</span><span class="sxs-lookup"><span data-stu-id="21e56-132">Marketing Assistant</span></span>|<span data-ttu-id="21e56-133">NULL</span><span class="sxs-lookup"><span data-stu-id="21e56-133">NULL</span></span>|  
|<span data-ttu-id="21e56-134">Brown</span><span class="sxs-lookup"><span data-stu-id="21e56-134">Brown</span></span>|<span data-ttu-id="21e56-135">Jo</span><span class="sxs-lookup"><span data-stu-id="21e56-135">Jo</span></span>|<span data-ttu-id="21e56-136">Design Engineer</span><span class="sxs-lookup"><span data-stu-id="21e56-136">Design Engineer</span></span>|<span data-ttu-id="21e56-137">NULL</span><span class="sxs-lookup"><span data-stu-id="21e56-137">NULL</span></span>|  
|<span data-ttu-id="21e56-138">Walters</span><span class="sxs-lookup"><span data-stu-id="21e56-138">Walters</span></span>|<span data-ttu-id="21e56-139">Rob</span><span class="sxs-lookup"><span data-stu-id="21e56-139">Rob</span></span>|<span data-ttu-id="21e56-140">Tool Designer</span><span class="sxs-lookup"><span data-stu-id="21e56-140">Tool Designer</span></span>|<span data-ttu-id="21e56-141">2001-08-09</span><span class="sxs-lookup"><span data-stu-id="21e56-141">2001-08-09</span></span>|  
  
 <span data-ttu-id="21e56-142">행에 중복 값이 있으므로 **LastName** 또는 **LastName**, **FirstName**의 열 조합에 고유 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-142">A unique index can not be created on the column combinations **LastName** or **LastName**, **FirstName** because of duplicate values in the rows.</span></span>  
  
 <span data-ttu-id="21e56-143">**HireDate** 열에서는 고유성 위반이 발생할 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-143">Less obvious is the potential for a uniqueness violation in the **HireDate** column.</span></span> <span data-ttu-id="21e56-144">인덱싱 작업에서 NULL 값은 동일한 값으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-144">For indexing purposes, NULL values compare as equal.</span></span> <span data-ttu-id="21e56-145">따라서 둘 이상의 행에서 키 값이 NULL인 경우에는 고유 인덱스 또는 제약 조건을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-145">Therefore, you cannot create a unique index or constraint if the key values are NULL in more than one row.</span></span> <span data-ttu-id="21e56-146">위와 같은 데이터의 경우 **HireDate** 또는 **LastName**, **HireDate** 열 조합에 고유 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-146">Given the data above, a unique index cannot be created on the column combinations **HireDate** or **LastName**, **HireDate**.</span></span>  
  
 <span data-ttu-id="21e56-147">오류 메시지 1505는 고유성 제약 조건을 위반한 첫 번째 행을 반환하므로</span><span class="sxs-lookup"><span data-stu-id="21e56-147">Error message 1505 returns the first row that violates the uniqueness constraint.</span></span> <span data-ttu-id="21e56-148">테이블에 다른 중복 행이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-148">There may be other duplicate rows in the table.</span></span> <span data-ttu-id="21e56-149">모든 중복 행을 찾으려면 지정된 테이블을 쿼리하고 GROUP BY 및 HAVING 절을 사용하여 중복 행을 반환하십시오.</span><span class="sxs-lookup"><span data-stu-id="21e56-149">To find all duplicate rows, query the specified table and use the GROUP BY and HAVING clauses to report the duplicate rows.</span></span> <span data-ttu-id="21e56-150">예를 들어 다음 쿼리는 **Employee** 테이블에서 이름과 성이 중복되는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-150">For example, the following query returns the rows in the **Employee** table that have duplicate first and last names.</span></span>  
  
 <span data-ttu-id="21e56-151">Dbo에서 LastName, FirstName, count ()를 선택 \* 합니다. LastName 별 직원 그룹, 개수 ()를 포함 하는 FirstName \* > 1;</span><span class="sxs-lookup"><span data-stu-id="21e56-151">SELECT LastName, FirstName, count(\*) FROM dbo.Employee GROUP BY LastName, FirstName HAVING count(\*) > 1;</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21e56-152">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="21e56-152">User Action</span></span>  
 <span data-ttu-id="21e56-153">다음과 같은 해결 방법을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="21e56-153">Consider the following solutions.</span></span>  
  
-   <span data-ttu-id="21e56-154">인덱스 또는 제약 조건 정의에서 열을 추가하거나 제거하여 고유 복합 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-154">Add or remove columns in the index or constraint definition to create a unique composite.</span></span> <span data-ttu-id="21e56-155">앞의 예에서는 인덱스 또는 제약 조건 정의에 **MiddleName** 열을 추가하여 중복 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-155">In the previous example, adding a **MiddleName** column to the index or constraint definition might resolve the duplication problem.</span></span>  
  
-   <span data-ttu-id="21e56-156">고유 인덱스 또는 제약 조건을 만들 열을 선택할 때는 NOT NULL로 정의된 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-156">Select columns that are defined as NOT NULL when you choose columns for a unique index or constraint.</span></span> <span data-ttu-id="21e56-157">이렇게 하면 둘 이상의 행에서 키 값이 NULL인 경우 발생하는 고유성 위반의 가능성을 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-157">This eliminates the possibility of a uniqueness violation caused when more than one row contains NULL in the key values.</span></span>  
  
-   <span data-ttu-id="21e56-158">중복 값이 데이터 입력 오류로 인한 것이면 데이터를 직접 수정한 다음 인덱스나 제약 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21e56-158">If the duplicate values are the result of data entry errors, manually correct the data and then create the index or constraint.</span></span> <span data-ttu-id="21e56-159">테이블에서 중복 행을 제거하는 방법에 대한 자세한 내용은 기술 자료 문서 139444: [SQL Server의 테이블에서 중복 행을 제거하는 방법](https://support.microsoft.com/kb/139444)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21e56-159">For information about removing duplicate rows in a table, see Knowledge Base article 139444: [How to remove duplicate rows from a table in SQL Server](https://support.microsoft.com/kb/139444).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e56-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21e56-160">See Also</span></span>  
 <span data-ttu-id="21e56-161">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="21e56-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="21e56-162">[고유 인덱스 만들기](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="21e56-162">[Create Unique Indexes](../indexes/indexes.md) </span></span>  
 [<span data-ttu-id="21e56-163">UNIQUE 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="21e56-163">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
