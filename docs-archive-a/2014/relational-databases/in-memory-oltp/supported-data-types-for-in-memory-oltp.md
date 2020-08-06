---
title: 지원 되는 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a7dda500486c39a66f871d5934f957028fc51e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740984"
---
# <a name="supported-data-types"></a><span data-ttu-id="e2c38-102">지원되는 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-102">Supported Data Types</span></span>
  <span data-ttu-id="e2c38-103">다음은 메모리 최적화 테이블과 고유하게 컴파일된 저장 프로시저에서 **지원되는** 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c38-103">The following data types are **supported** in memory-optimized tables and natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="e2c38-104">**숫자 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-104">**Numeric Data Types**</span></span>  
  
|<span data-ttu-id="e2c38-105">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-105">Data type</span></span>|<span data-ttu-id="e2c38-106">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-106">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="e2c38-107">Int</span><span class="sxs-lookup"><span data-stu-id="e2c38-107">int</span></span>|[<span data-ttu-id="e2c38-108">int, bigint, smallint 및 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-108">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="e2c38-109">bigint</span><span class="sxs-lookup"><span data-stu-id="e2c38-109">bigint</span></span>|[<span data-ttu-id="e2c38-110">int, bigint, smallint 및 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-110">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="e2c38-111">smallint</span><span class="sxs-lookup"><span data-stu-id="e2c38-111">smallint</span></span>|[<span data-ttu-id="e2c38-112">int, bigint, smallint 및 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-112">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="e2c38-113">tinyint</span><span class="sxs-lookup"><span data-stu-id="e2c38-113">tinyint</span></span>|[<span data-ttu-id="e2c38-114">int, bigint, smallint 및 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-114">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="e2c38-115">decimal</span><span class="sxs-lookup"><span data-stu-id="e2c38-115">decimal</span></span>|[<span data-ttu-id="e2c38-116">decimal 및 numeric&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-116">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="e2c38-117">numeric</span><span class="sxs-lookup"><span data-stu-id="e2c38-117">numeric</span></span>|[<span data-ttu-id="e2c38-118">decimal 및 numeric&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-118">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="e2c38-119">float</span><span class="sxs-lookup"><span data-stu-id="e2c38-119">float</span></span>|[<span data-ttu-id="e2c38-120">float 및 real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-120">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="e2c38-121">real</span><span class="sxs-lookup"><span data-stu-id="e2c38-121">real</span></span>|[<span data-ttu-id="e2c38-122">float 및 real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-122">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="e2c38-123">money</span><span class="sxs-lookup"><span data-stu-id="e2c38-123">money</span></span>|[<span data-ttu-id="e2c38-124">money 및 smallmoney&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-124">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|<span data-ttu-id="e2c38-125">smallmoney</span><span class="sxs-lookup"><span data-stu-id="e2c38-125">smallmoney</span></span>|[<span data-ttu-id="e2c38-126">money 및 smallmoney&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-126">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 <span data-ttu-id="e2c38-127">**문자열 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-127">**String Data Types**</span></span>  
  
|<span data-ttu-id="e2c38-128">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-128">Data type</span></span>|<span data-ttu-id="e2c38-129">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-129">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="e2c38-130">char(n)</span><span class="sxs-lookup"><span data-stu-id="e2c38-130">char(n)</span></span>|[<span data-ttu-id="e2c38-131">char 및 varchar&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-131">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="e2c38-132">varchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2c38-132">varchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="e2c38-133">char 및 varchar&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-133">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="e2c38-134">nchar(n)</span><span class="sxs-lookup"><span data-stu-id="e2c38-134">nchar(n)</span></span>|[<span data-ttu-id="e2c38-135">nchar 및 nvarchar&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-135">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="e2c38-136">nvarchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2c38-136">nvarchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="e2c38-137">nchar 및 nvarchar&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-137">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="e2c38-138">sysname</span><span class="sxs-lookup"><span data-stu-id="e2c38-138">sysname</span></span>|[<span data-ttu-id="e2c38-139">nchar 및 nvarchar&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-139">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <span data-ttu-id="e2c38-140"><sup>1</sup> 제한은 가변 길이 형식의 계산 (n)을 통해 8060 바이트의 행 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c38-140"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="e2c38-141">지원되는 데이터 정렬에 대한 자세한 내용은 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2c38-141">For information about supported collations, see [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).</span></span>  
  
 <span data-ttu-id="e2c38-142">**날짜 및 시간 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-142">**Date and Time Data Types**</span></span>  
  
|<span data-ttu-id="e2c38-143">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-143">Data type</span></span>|<span data-ttu-id="e2c38-144">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-144">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="e2c38-145">date</span><span class="sxs-lookup"><span data-stu-id="e2c38-145">date</span></span>|[<span data-ttu-id="e2c38-146">date&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-146">date &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/date-transact-sql)|  
|<span data-ttu-id="e2c38-147">time</span><span class="sxs-lookup"><span data-stu-id="e2c38-147">time</span></span>|[<span data-ttu-id="e2c38-148">time &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-148">time &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/time-transact-sql)|  
|<span data-ttu-id="e2c38-149">Datetime</span><span class="sxs-lookup"><span data-stu-id="e2c38-149">datetime</span></span>|[<span data-ttu-id="e2c38-150">datetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-150">datetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime-transact-sql)|  
|<span data-ttu-id="e2c38-151">datetime2</span><span class="sxs-lookup"><span data-stu-id="e2c38-151">datetime2</span></span>|[<span data-ttu-id="e2c38-152">datetime2&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-152">datetime2 &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime2-transact-sql)|  
|<span data-ttu-id="e2c38-153">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="e2c38-153">smalldatetime</span></span>|[<span data-ttu-id="e2c38-154">smalldatetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-154">smalldatetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 <span data-ttu-id="e2c38-155">**이진 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-155">**Binary Data Types**</span></span>  
  
|<span data-ttu-id="e2c38-156">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-156">Data type</span></span>|<span data-ttu-id="e2c38-157">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-157">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="e2c38-158">bit</span><span class="sxs-lookup"><span data-stu-id="e2c38-158">bit</span></span>|[<span data-ttu-id="e2c38-159">bit &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-159">bit &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/bit-transact-sql)|  
|<span data-ttu-id="e2c38-160">binary(n)</span><span class="sxs-lookup"><span data-stu-id="e2c38-160">binary(n)</span></span>|[<span data-ttu-id="e2c38-161">binary 및 varbinary&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-161">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|<span data-ttu-id="e2c38-162">varbinary (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2c38-162">varbinary(n) <sup>1</sup></span></span>|[<span data-ttu-id="e2c38-163">binary 및 varbinary&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-163">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <span data-ttu-id="e2c38-164"><sup>1</sup> 제한은 가변 길이 형식의 계산 (n)을 통해 8060 바이트의 행 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c38-164"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="e2c38-165">**기타 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-165">**Other data types**</span></span>  
  
|<span data-ttu-id="e2c38-166">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e2c38-166">Data type</span></span>|<span data-ttu-id="e2c38-167">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-167">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="e2c38-168">uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="e2c38-168">uniqueidentifier</span></span>|[<span data-ttu-id="e2c38-169">uniqueidentifier&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c38-169">uniqueidentifier &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 <span data-ttu-id="e2c38-170">**지원되지 않는 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e2c38-170">**Unsupported Data Types**</span></span>  
  
 <span data-ttu-id="e2c38-171">다음 데이터 형식은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c38-171">The following data types are not supported:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2c38-172">DATETIMEOFFSET</span><span class="sxs-lookup"><span data-stu-id="e2c38-172">DATETIMEOFFSET</span></span>|<span data-ttu-id="e2c38-173">GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="e2c38-173">GEOGRAPHY</span></span>|<span data-ttu-id="e2c38-174">GEOMETRY</span><span class="sxs-lookup"><span data-stu-id="e2c38-174">GEOMETRY</span></span>|  
|<span data-ttu-id="e2c38-175">HIERARCHYID</span><span class="sxs-lookup"><span data-stu-id="e2c38-175">HIERARCHYID</span></span>|<span data-ttu-id="e2c38-176">LOB(Large Object).</span><span class="sxs-lookup"><span data-stu-id="e2c38-176">Large Objects (LOBs).</span></span> <span data-ttu-id="e2c38-177">예: varchar(max), nvarchar(max), varbinary(max), image, xml, text 및 ntext</span><span class="sxs-lookup"><span data-stu-id="e2c38-177">For example, varchar(max), nvarchar(max), varbinary(max), image, xml, text, and ntext.</span></span>|<span data-ttu-id="e2c38-178">ROWVERSION</span><span class="sxs-lookup"><span data-stu-id="e2c38-178">ROWVERSION</span></span>|  
|<span data-ttu-id="e2c38-179">sql_variant</span><span class="sxs-lookup"><span data-stu-id="e2c38-179">sql_variant</span></span>|<span data-ttu-id="e2c38-180">CLR 함수</span><span class="sxs-lookup"><span data-stu-id="e2c38-180">CLR functions</span></span>|<span data-ttu-id="e2c38-181">UDT(사용자 정의 형식)</span><span class="sxs-lookup"><span data-stu-id="e2c38-181">User-defined types (UDTs)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2c38-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2c38-182">See Also</span></span>  
 <span data-ttu-id="e2c38-183">[메모리 내 OLTP에 대한 Transact-SQL 지원](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="e2c38-183">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="e2c38-184">[메모리 액세스에 최적화 된 테이블에서 LOB 열 구현](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span><span class="sxs-lookup"><span data-stu-id="e2c38-184">[Implementing LOB Columns in a Memory-Optimized Table](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span></span>  
 [<span data-ttu-id="e2c38-185">메모리 액세스에 최적화된 테이블에서 SQL_VARIANT 구현</span><span class="sxs-lookup"><span data-stu-id="e2c38-185">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
