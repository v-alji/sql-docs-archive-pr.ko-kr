---
title: 인덱싱된 뷰 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexed views [SQL Server], creating
- clustered indexes, views
- CREATE INDEX statement
- large_value_types_out_of_row option
- indexed views [SQL Server]
- views [SQL Server], indexed views
ms.assetid: f86dd29f-52dd-44a9-91ac-1eb305c1ca8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d33ff37caca04f46edd6ad92d0686713829bb270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646265"
---
# <a name="create-indexed-views"></a><span data-ttu-id="e8908-102">인덱싱된 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="e8908-102">Create Indexed Views</span></span>
  <span data-ttu-id="e8908-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱싱된 뷰를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-103">This topic describes how to create an indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e8908-104">뷰에 만들어지는 첫 번째 인덱스는 고유 클러스터형 인덱스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-104">The first index created on a view must be a unique clustered index.</span></span> <span data-ttu-id="e8908-105">고유 클러스터형 인덱스가 만들어진 후에 비클러스터형 인덱스를 더 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-105">After the unique clustered index has been created, you can create more nonclustered indexes.</span></span> <span data-ttu-id="e8908-106">뷰에 고유 클러스터형 인덱스를 만들면 클러스터형 인덱스가 있는 테이블의 저장 방식과 마찬가지로 데이터베이스에 뷰가 저장되므로 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-106">Creating a unique clustered index on a view improves query performance because the view is stored in the database in the same way a table with a clustered index is stored.</span></span> <span data-ttu-id="e8908-107">쿼리 최적화 프로그램은 인덱싱된 뷰를 사용하여 쿼리 실행 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-107">The query optimizer may use indexed views to speed up the query execution.</span></span> <span data-ttu-id="e8908-108">최적화 프로그램이 인덱싱된 뷰를 대신 사용하므로 쿼리에서 해당 뷰를 참조할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-108">The view does not have to be referenced in the query for the optimizer to consider that view for a substitution.</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8908-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e8908-109">Before You Begin</span></span>  
 <span data-ttu-id="e8908-110">다음 단계는 인덱싱된 뷰를 만들고 성공적으로 구현하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-110">The following steps are required to create an indexed view and are critical to the successful implementation of the indexed view:</span></span>  
  
1.  <span data-ttu-id="e8908-111">뷰에 참조될 기존의 모든 테이블에 대해 SET 옵션이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-111">Verify the SET options are correct for all existing tables that will be referenced in the view.</span></span>  
  
2.  <span data-ttu-id="e8908-112">테이블 및 뷰를 만들기 전에 세션에 SET 옵션이 올바르게 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-112">Verify that the SET options for the session are set correctly before you create any tables and the view.</span></span>  
  
3.  <span data-ttu-id="e8908-113">뷰 정의가 결정적인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-113">Verify that the view definition is deterministic.</span></span>  
  
4.  <span data-ttu-id="e8908-114">WITH SCHEMABINDING 옵션을 사용하여 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-114">Create the view by using the WITH SCHEMABINDING option.</span></span>  
  
5.  <span data-ttu-id="e8908-115">뷰에 고유 클러스터형 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-115">Create the unique clustered index on the view.</span></span>  
  
###  <a name="required-set-options-for-indexed-views"></a><a name="Restrictions"></a> <span data-ttu-id="e8908-116">인덱싱된 뷰에 필요한 SET 옵션</span><span class="sxs-lookup"><span data-stu-id="e8908-116">Required SET Options for Indexed Views</span></span>  
 <span data-ttu-id="e8908-117">쿼리가 실행될 때 다른 SET 옵션이 활성화되어 있으면 같은 식을 계산해도 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 다른 결과가 나올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-117">Evaluating the same expression can produce different results in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when different SET options are active when the query is executed.</span></span> <span data-ttu-id="e8908-118">예를 들어 SET 옵션 CONCAT_NULL_YIELDS_NULL이 ON으로 설정된 후 식 **'** abc **'** + NULL의 결과로 NULL 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-118">For example, after the SET option CONCAT_NULL_YIELDS_NULL is set to ON, the expression **'** abc **'** + NULL returns the value NULL.</span></span> <span data-ttu-id="e8908-119">그러나 CONCAT_NULL_YIEDS_NULL을 OFF로 설정한 후 같은 식의 결과는 **'** abc **'** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-119">However, after CONCAT_NULL_YIEDS_NULL is set to OFF, the same expression produces **'** abc **'**.</span></span>  
  
 <span data-ttu-id="e8908-120">뷰를 올바르게 유지하고 일관된 결과를 반환하게 하려면 인덱싱된 뷰는 몇 가지 SET 옵션에 대해 고정 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-120">To make sure that the views can be maintained correctly and return consistent results, indexed views require fixed values for several SET options.</span></span> <span data-ttu-id="e8908-121">다음 테이블의 SET 옵션은 다음 조건이 발생할 때마다 **Requiredvalue** 열에 표시 된 값으로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-121">The SET options in the following table must be set to the values shown in the **RequiredValue** column whenever the following conditions occur:</span></span>  
  
-   <span data-ttu-id="e8908-122">뷰와 뷰의 후속 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-122">The view and subsequent indexes on the view are created.</span></span>  
  
-   <span data-ttu-id="e8908-123">테이블을 만들 때 뷰에서 참조되는 기본 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-123">The base tables referenced in the view at the time the table is created.</span></span>  
  
-   <span data-ttu-id="e8908-124">인덱싱된 뷰에 참가하는 테이블에서 삽입, 업데이트 또는 삭제 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-124">There is any insert, update, or delete operation performed on any table that participates in the indexed view.</span></span> <span data-ttu-id="e8908-125">이 요구 사항에는 대량 복사, 복제, 분산 쿼리 등의 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-125">This requirement includes operations such as bulk copy, replication, and distributed queries.</span></span>  
  
-   <span data-ttu-id="e8908-126">쿼리 최적화 프로그램에서 인덱싱된 뷰를 사용하여 쿼리 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-126">The indexed view is used by the query optimizer to produce the query plan.</span></span>  
  
    |<span data-ttu-id="e8908-127">Set 옵션</span><span class="sxs-lookup"><span data-stu-id="e8908-127">SET options</span></span>|<span data-ttu-id="e8908-128">필수 값</span><span class="sxs-lookup"><span data-stu-id="e8908-128">Required value</span></span>|<span data-ttu-id="e8908-129">기본 서버 값</span><span class="sxs-lookup"><span data-stu-id="e8908-129">Default server value</span></span>|<span data-ttu-id="e8908-130">기본값</span><span class="sxs-lookup"><span data-stu-id="e8908-130">Default</span></span><br /><br /> <span data-ttu-id="e8908-131">OLE DB 및 ODBC 값</span><span class="sxs-lookup"><span data-stu-id="e8908-131">OLE DB and ODBC value</span></span>|<span data-ttu-id="e8908-132">기본값</span><span class="sxs-lookup"><span data-stu-id="e8908-132">Default</span></span><br /><br /> <span data-ttu-id="e8908-133">DB-Library 값</span><span class="sxs-lookup"><span data-stu-id="e8908-133">DB-Library value</span></span>|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |<span data-ttu-id="e8908-134">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="e8908-134">ANSI_NULLS</span></span>|<span data-ttu-id="e8908-135">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-135">ON</span></span>|<span data-ttu-id="e8908-136">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-136">ON</span></span>|<span data-ttu-id="e8908-137">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-137">ON</span></span>|<span data-ttu-id="e8908-138">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-138">OFF</span></span>|  
    |<span data-ttu-id="e8908-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="e8908-139">ANSI_PADDING</span></span>|<span data-ttu-id="e8908-140">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-140">ON</span></span>|<span data-ttu-id="e8908-141">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-141">ON</span></span>|<span data-ttu-id="e8908-142">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-142">ON</span></span>|<span data-ttu-id="e8908-143">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-143">OFF</span></span>|  
    |<span data-ttu-id="e8908-144">ANSI_WARNINGS\*</span><span class="sxs-lookup"><span data-stu-id="e8908-144">ANSI_WARNINGS\*</span></span>|<span data-ttu-id="e8908-145">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-145">ON</span></span>|<span data-ttu-id="e8908-146">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-146">ON</span></span>|<span data-ttu-id="e8908-147">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-147">ON</span></span>|<span data-ttu-id="e8908-148">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-148">OFF</span></span>|  
    |<span data-ttu-id="e8908-149">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="e8908-149">ARITHABORT</span></span>|<span data-ttu-id="e8908-150">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-150">ON</span></span>|<span data-ttu-id="e8908-151">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-151">ON</span></span>|<span data-ttu-id="e8908-152">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-152">OFF</span></span>|<span data-ttu-id="e8908-153">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-153">OFF</span></span>|  
    |<span data-ttu-id="e8908-154">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="e8908-154">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="e8908-155">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-155">ON</span></span>|<span data-ttu-id="e8908-156">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-156">ON</span></span>|<span data-ttu-id="e8908-157">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-157">ON</span></span>|<span data-ttu-id="e8908-158">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-158">OFF</span></span>|  
    |<span data-ttu-id="e8908-159">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="e8908-159">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="e8908-160">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-160">OFF</span></span>|<span data-ttu-id="e8908-161">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-161">OFF</span></span>|<span data-ttu-id="e8908-162">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-162">OFF</span></span>|<span data-ttu-id="e8908-163">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-163">OFF</span></span>|  
    |<span data-ttu-id="e8908-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="e8908-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="e8908-165">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-165">ON</span></span>|<span data-ttu-id="e8908-166">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-166">ON</span></span>|<span data-ttu-id="e8908-167">켜기</span><span class="sxs-lookup"><span data-stu-id="e8908-167">ON</span></span>|<span data-ttu-id="e8908-168">OFF</span><span class="sxs-lookup"><span data-stu-id="e8908-168">OFF</span></span>|  
  
     <span data-ttu-id="e8908-169">\*ANSI_WARNINGS를 ON으로 설정하면 암시적으로 ARITHABORT가 ON으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-169">\*Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON.</span></span>  
  
 <span data-ttu-id="e8908-170">OLE DB 또는 ODBC 서버 연결을 사용하는 경우 수정해야 하는 유일한 값은 ARITHABORT 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-170">If you are using an OLE DB or ODBC server connection, the only value that must be modified is the ARITHABORT setting.</span></span> <span data-ttu-id="e8908-171">모든 DB-Library 값은 **sp_configure** 를 사용하여 서버 수준에서 또는 SET 명령을 사용하여 애플리케이션에서 올바르게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-171">All DB-Library values must be set correctly either at the server level by using **sp_configure** or from the application by using the SET command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e8908-172">서버의 데이터베이스에서 계산 열에 첫 번째로 인덱싱된 뷰 또는 인덱스가 만들어지면 바로 서버 차원에서 ARITHABORT 사용자 옵션을 ON으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-172">We strongly recommend that you set the ARITHABORT user option to ON server-wide as soon as the first indexed view or index on a computed column is created in any database on the server.</span></span>  
  
### <a name="deterministic-views"></a><span data-ttu-id="e8908-173">결정적 뷰</span><span class="sxs-lookup"><span data-stu-id="e8908-173">Deterministic Views</span></span>  
 <span data-ttu-id="e8908-174">인덱싱된 뷰의 정의는 결정적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-174">The definition of an indexed view must be deterministic.</span></span> <span data-ttu-id="e8908-175">WHERE 및 GROUP BY 절뿐만 아니라 SELECT 목록의 모든 식이 결정적이면 뷰가 결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-175">A view is deterministic if all expressions in the select list, as well as the WHERE and GROUP BY clauses, are deterministic.</span></span> <span data-ttu-id="e8908-176">결정적 식은 특정 입력 값 집합을 사용하여 계산될 때마다 항상 같은 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-176">Deterministic expressions always return the same result any time they are evaluated with a specific set of input values.</span></span> <span data-ttu-id="e8908-177">결정적 함수만 결정적 식에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-177">Only deterministic functions can participate in deterministic expressions.</span></span> <span data-ttu-id="e8908-178">예를 들어 DATEADD 함수는 세 매개 변수에 지정된 인수 값 집합에 대해 항상 같은 결과를 반환하므로 결정적 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-178">For example, the DATEADD function is deterministic because it always returns the same result for any given set of argument values for its three parameters.</span></span> <span data-ttu-id="e8908-179">GETDATE는 항상 같은 인수로 호출되지만 실행될 때마다 반환하는 값이 바뀌므로 비결정적 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-179">GETDATE is not deterministic because it is always invoked with the same argument, but the value it returns changes each time it is executed.</span></span>  
  
 <span data-ttu-id="e8908-180">뷰 열이 결정적인지 여부를 확인하려면 **COLUMNPROPERTY** 함수의 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-180">To determine whether a view column is deterministic, use the **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function.</span></span> <span data-ttu-id="e8908-181">스키마 바인딩되어 있는 뷰의 결정적 열이 정확한지 여부를 확인하려면 COLUMNPROPERTY 함수의 **IsPrecise** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-181">To determine if a deterministic column in a view with schema binding is precise, use the **IsPrecise** property of the COLUMNPROPERTY function.</span></span> <span data-ttu-id="e8908-182">COLUMNPROPERTY는 TRUE이면 1을 반환하고 FALSE이면 0을 반환하며 입력이 잘못되면 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-182">COLUMNPROPERTY returns 1 if TRUE, 0 if FALSE, and NULL for input that is not valid.</span></span> <span data-ttu-id="e8908-183">이는 해당 열이 비결정적이거나 정확하지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-183">This means the column is not deterministic or not precise.</span></span>  
  
 <span data-ttu-id="e8908-184">식이 결정적인 경우에도 float 식이 포함되어 있으면 정확한 결과는 프로세서 아키텍처 또는 마이크로코드 버전에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-184">Even if an expression is deterministic, if it contains float expressions, the exact result may depend on the processor architecture or version of microcode.</span></span> <span data-ttu-id="e8908-185">데이터 무결성을 보장하기 위해 이런 식은 인덱싱된 뷰의 키가 아닌 열로만 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-185">To ensure data integrity, such expressions can participate only as non-key columns of indexed views.</span></span> <span data-ttu-id="e8908-186">float 식이 없는 결정적 식을 정확하다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-186">Deterministic expressions that do not contain float expressions are called precise.</span></span> <span data-ttu-id="e8908-187">정확한 결정적 식만 인덱싱된 뷰의 WHERE 또는 GROUP BY 절과 키 열에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-187">Only precise deterministic expressions can participate in key columns and in WHERE or GROUP BY clauses of indexed views.</span></span>  
  
### <a name="additional-requirements"></a><span data-ttu-id="e8908-188">추가 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e8908-188">Additional Requirements</span></span>  
 <span data-ttu-id="e8908-189">SET 옵션 및 결정적 함수 요구 사항 외에 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-189">In addition to the SET options and deterministic function requirements, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="e8908-190">CREATE INDEX를 실행하는 사용자는 뷰의 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-190">The user that executes CREATE INDEX must be the owner of the view.</span></span>  
  
-   <span data-ttu-id="e8908-191">인덱스를 만들 때 IGNORE_DUP_KEY 옵션은 OFF(기본 설정)로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-191">When you create the index, the IGNORE_DUP_KEY option must be set to OFF (the default setting).</span></span>  
  
-   <span data-ttu-id="e8908-192">테이블은 뷰 정의에서 _schema_ **.** _tablename_ 처럼 두 부분으로 구성된 이름으로 참조되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-192">Tables must be referenced by two-part names, _schema_**.**_tablename_ in the view definition.</span></span>  
  
-   <span data-ttu-id="e8908-193">뷰에서 참조하는 사용자 정의 함수는 WITH SCHEMABINDING 옵션을 사용하여 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-193">User-defined functions referenced in the view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="e8908-194">뷰에서 참조 되는 모든 사용자 정의 함수는 두 부분으로 구성 된 이름인 _schema_로 참조 되어야 합니다 **.** _함수_.</span><span class="sxs-lookup"><span data-stu-id="e8908-194">Any user-defined functions referenced in the view must be referenced by two-part names, _schema_**.**_function_.</span></span>  
  
-   <span data-ttu-id="e8908-195">사용자 정의 함수의 데이터 액세스 속성은 NO SQL이어야 하고 외부 액세스 속성은 NO여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-195">The data access property of a user-defined function must be NO SQL, and external access property must be NO.</span></span>  
  
-   <span data-ttu-id="e8908-196">CLR(공용 언어 런타임) 함수는 뷰의 SELECT 목록에 표시될 수 있지만 클러스터형 인덱스 키 정의의 일부일 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-196">Common language runtime (CLR) functions can appear in the select list of the view, but cannot be part of the definition of the clustered index key.</span></span> <span data-ttu-id="e8908-197">CLR 함수는 뷰의 WHERE 절이나 뷰에서 JOIN 연산의 ON 절에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-197">CLR functions cannot appear in the WHERE clause of the view or the ON clause of a JOIN operation in the view.</span></span>  
  
-   <span data-ttu-id="e8908-198">뷰 정의에서 사용된 CLR 사용자 정의 형식의 메서드 및 CLR 함수의 속성을 다음 표와 같이 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-198">CLR functions and methods of CLR user-defined types used in the view definition must have the properties set as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e8908-199">속성</span><span class="sxs-lookup"><span data-stu-id="e8908-199">Property</span></span>|<span data-ttu-id="e8908-200">참고</span><span class="sxs-lookup"><span data-stu-id="e8908-200">Note</span></span>|  
    |--------------|----------|  
    |<span data-ttu-id="e8908-201">DETERMINISTIC = TRUE</span><span class="sxs-lookup"><span data-stu-id="e8908-201">DETERMINISTIC = TRUE</span></span>|<span data-ttu-id="e8908-202">Microsoft .NET Framework 메서드의 특성으로 명시적으로 선언되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-202">Must be declared explicitly as an attribute of the Microsoft .NET Framework method.</span></span>|  
    |<span data-ttu-id="e8908-203">PRECISE = TRUE</span><span class="sxs-lookup"><span data-stu-id="e8908-203">PRECISE = TRUE</span></span>|<span data-ttu-id="e8908-204">.NET Framework 메서드의 특성으로 명시적으로 선언되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-204">Must be declared explicitly as an attribute of the .NET Framework method.</span></span>|  
    |<span data-ttu-id="e8908-205">DATA ACCESS = NO SQL</span><span class="sxs-lookup"><span data-stu-id="e8908-205">DATA ACCESS = NO SQL</span></span>|<span data-ttu-id="e8908-206">DataAccess 특성을 DataAccessKind.None으로 설정하고 SystemDataAccess 특성을 SystemDataAccessKind.None으로 설정함으로써 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-206">Determined by setting DataAccess attribute to DataAccessKind.None and SystemDataAccess attribute to SystemDataAccessKind.None.</span></span>|  
    |<span data-ttu-id="e8908-207">EXTERNAL ACCESS = NO</span><span class="sxs-lookup"><span data-stu-id="e8908-207">EXTERNAL ACCESS = NO</span></span>|<span data-ttu-id="e8908-208">CLR 루틴의 경우 이 속성의 기본값은 NO입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-208">This property defaults to NO for CLR routines.</span></span>|  
  
-   <span data-ttu-id="e8908-209">뷰는 WITH SCHEMABINDING 옵션을 사용하여 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-209">The view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="e8908-210">뷰는 뷰와 동일한 데이터베이스의 기본 테이블만 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-210">The view must reference only base tables that are in the same database as the view.</span></span> <span data-ttu-id="e8908-211">뷰는 다른 뷰를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-211">The view cannot reference other views.</span></span>  
  
-   <span data-ttu-id="e8908-212">뷰 정의의 SELECT 문에는 다음 Transact-SQL 요소가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-212">The SELECT statement in the view definition must not contain the following Transact-SQL elements:</span></span>  
  
    ||||  
    |-|-|-|  
    |<span data-ttu-id="e8908-213">COUNT</span><span class="sxs-lookup"><span data-stu-id="e8908-213">COUNT</span></span>|<span data-ttu-id="e8908-214">ROWSET 함수(OPENDATASOURCE, OPENQUERY, OPENROWSET 및 OPENXML)</span><span class="sxs-lookup"><span data-stu-id="e8908-214">ROWSET functions (OPENDATASOURCE, OPENQUERY, OPENROWSET, AND OPENXML)</span></span>|<span data-ttu-id="e8908-215">OUTER 조인(LEFT, RIGHT 또는 FULL)</span><span class="sxs-lookup"><span data-stu-id="e8908-215">OUTER joins (LEFT, RIGHT, or FULL)</span></span>|  
    |<span data-ttu-id="e8908-216">파생 테이블(FROM 절에서 SELECT 문을 지정하여 정의)</span><span class="sxs-lookup"><span data-stu-id="e8908-216">Derived table (defined by specifying a SELECT statement in the FROM clause)</span></span>|<span data-ttu-id="e8908-217">자체 조인</span><span class="sxs-lookup"><span data-stu-id="e8908-217">Self-joins</span></span>|<span data-ttu-id="e8908-218">SELECT \* 또는 SELECT *table_name*을 사용하여 열 지정\*</span><span class="sxs-lookup"><span data-stu-id="e8908-218">Specifying columns by using SELECT \* or SELECT *table_name*.\*</span></span>|  
    |<span data-ttu-id="e8908-219">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="e8908-219">DISTINCT</span></span>|<span data-ttu-id="e8908-220">STDEV, STDEVP, VAR, VARP 또는 AVG</span><span class="sxs-lookup"><span data-stu-id="e8908-220">STDEV, STDEVP, VAR, VARP, or AVG</span></span>|<span data-ttu-id="e8908-221">CTE(공통 테이블 식)</span><span class="sxs-lookup"><span data-stu-id="e8908-221">Common table expression (CTE)</span></span>|  
    |<span data-ttu-id="e8908-222">`float`\*,,,, `text` `ntext` `image` `XML` 또는 `filestream` 열</span><span class="sxs-lookup"><span data-stu-id="e8908-222">`float`\*, `text`, `ntext`, `image`, `XML`, or `filestream` columns</span></span>|<span data-ttu-id="e8908-223">하위 쿼리</span><span class="sxs-lookup"><span data-stu-id="e8908-223">Subquery</span></span>|<span data-ttu-id="e8908-224">순위 함수 또는 집계 창 함수를 포함하는 OVER 절</span><span class="sxs-lookup"><span data-stu-id="e8908-224">OVER clause, which includes ranking or aggregate window functions</span></span>|  
    |<span data-ttu-id="e8908-225">전체 텍스트 조건자(CONTAIN, FREETEXT)</span><span class="sxs-lookup"><span data-stu-id="e8908-225">Full-text predicates (CONTAIN, FREETEXT)</span></span>|<span data-ttu-id="e8908-226">Null 허용 식을 참조하는 SUM 함수</span><span class="sxs-lookup"><span data-stu-id="e8908-226">SUM function that references a nullable expression</span></span>|<span data-ttu-id="e8908-227">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e8908-227">ORDER BY</span></span>|  
    |<span data-ttu-id="e8908-228">CLR 사용자 정의 집계 함수</span><span class="sxs-lookup"><span data-stu-id="e8908-228">CLR user-defined aggregate function</span></span>|<span data-ttu-id="e8908-229">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="e8908-229">TOP</span></span>|<span data-ttu-id="e8908-230">CUBE, ROLLUP 또는 GROUPING SETS 연산자</span><span class="sxs-lookup"><span data-stu-id="e8908-230">CUBE, ROLLUP, or GROUPING SETS operators</span></span>|  
    |<span data-ttu-id="e8908-231">MIN, MAX</span><span class="sxs-lookup"><span data-stu-id="e8908-231">MIN, MAX</span></span>|<span data-ttu-id="e8908-232">UNION, EXCEPT 또는 INTERSECT 연산자</span><span class="sxs-lookup"><span data-stu-id="e8908-232">UNION, EXCEPT, or INTERSECT operators</span></span>|<span data-ttu-id="e8908-233">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="e8908-233">TABLESAMPLE</span></span>|  
    |<span data-ttu-id="e8908-234">테이블 변수</span><span class="sxs-lookup"><span data-stu-id="e8908-234">Table variables</span></span>|<span data-ttu-id="e8908-235">OUTER APPLY 또는 CROSS APPLY</span><span class="sxs-lookup"><span data-stu-id="e8908-235">OUTER APPLY or CROSS APPLY</span></span>|<span data-ttu-id="e8908-236">PIVOT, UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="e8908-236">PIVOT, UNPIVOT</span></span>|  
    |<span data-ttu-id="e8908-237">스파스 열 집합</span><span class="sxs-lookup"><span data-stu-id="e8908-237">Sparse column sets</span></span>|<span data-ttu-id="e8908-238">인라인 또는 다중 문 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="e8908-238">Inline or multi-statement table-valued functions</span></span>|<span data-ttu-id="e8908-239">OFFSET</span><span class="sxs-lookup"><span data-stu-id="e8908-239">OFFSET</span></span>|  
    |<span data-ttu-id="e8908-240">CHECKSUM_AGG</span><span class="sxs-lookup"><span data-stu-id="e8908-240">CHECKSUM_AGG</span></span>|||  
  
     <span data-ttu-id="e8908-241">\*인덱싱된 뷰에는 열이 포함 될 수 있지만 `float` 이러한 열은 클러스터형 인덱스 키에 포함 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-241">\*The indexed view can contain `float` columns; however, such columns cannot be included in the clustered index key.</span></span>  
  
-   <span data-ttu-id="e8908-242">GROUP BY가 있는 경우 VIEW 정의는 COUNT_BIG(\*)을 포함해야 하며 HAVING은 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-242">If GROUP BY is present, the VIEW definition must contain COUNT_BIG(\*) and must not contain HAVING.</span></span> <span data-ttu-id="e8908-243">이러한 GROUP BY 제약 조건은 인덱싱된 뷰 정의에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-243">These GROUP BY restrictions are applicable only to the indexed view definition.</span></span> <span data-ttu-id="e8908-244">쿼리는 이러한 GROUP BY 제약 조건을 충족하지 않는 경우에도 실행 계획에 인덱싱된 뷰를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-244">A query can use an indexed view in its execution plan even if it does not satisfy these GROUP BY restrictions.</span></span>  
  
-   <span data-ttu-id="e8908-245">뷰 정의에 GROUP BY 절이 들어 있으면 고유 클러스터형 인덱스의 키는 GROUP BY 절에 지정된 열만 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-245">If the view definition contains a GROUP BY clause, the key of the unique clustered index can reference only the columns specified in the GROUP BY clause.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e8908-246">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e8908-246">Recommendations</span></span>  
 <span data-ttu-id="e8908-247">인덱싱된 뷰의 `datetime` 및 `smalldatetime` 문자열 리터럴을 참조할 때 결정적 날짜 형식 스타일을 사용하여 리터럴을 원하는 날짜 유형으로 명시적으로 변환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-247">When you refer to `datetime` and `smalldatetime` string literals in indexed views, we recommend that you explicitly convert the literal to the date type you want by using a deterministic date format style.</span></span> <span data-ttu-id="e8908-248">결정적 날짜 형식 스타일 목록은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8908-248">For a list of the date format styles that are deterministic, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="e8908-249">문자열을 `datetime` 또는 `smalldatetime`으로 암시적으로 변환하는 작업과 관련된 식은 비결정적인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-249">Expressions that involve implicit conversion of character strings to `datetime` or `smalldatetime` are considered nondeterministic.</span></span> <span data-ttu-id="e8908-250">이는 서버 세션의 LANGUAGE 및 DATEFORMAT 설정에 따라 결과가 달라지기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-250">This is because the results depend on the LANGUAGE and DATEFORMAT settings of the server session.</span></span> <span data-ttu-id="e8908-251">예를 들어 ' `CONVERT (datetime, '30 listopad 1996', 113)` ' 문자열이 다른 언어에서는 다른 월을 의미하므로`listopad`식의 결과는 LANGUAGE 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-251">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`listopad`' means different months in different languages.</span></span> <span data-ttu-id="e8908-252">마찬가지로 `DATEADD(mm,3,'2000-12-01')`식에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 DATEFORMAT 설정을 기준으로 `'2000-12-01'` 문자열을 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-252">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
  
 <span data-ttu-id="e8908-253">데이터 정렬 간의 비유니코드 문자 데이터를 암시적으로 변환하는 작업도 비결정적인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-253">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic.</span></span>  
  
###  <a name="considerations"></a><a name="Considerations"></a> <span data-ttu-id="e8908-254">고려 사항</span><span class="sxs-lookup"><span data-stu-id="e8908-254">Considerations</span></span>  
 <span data-ttu-id="e8908-255">인덱싱된 뷰의 열에 대한 **large_value_types_out_of_row** 옵션의 설정은 기본 테이블의 해당 열에 대한 설정에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-255">The setting of the **large_value_types_out_of_row** option of columns in an indexed view is inherited from the setting of the corresponding column in the base table.</span></span> <span data-ttu-id="e8908-256">이 값은 [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)을 통해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-256">This value is set by using [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="e8908-257">식으로부터 구성된 열의 기본 설정은 0으로서</span><span class="sxs-lookup"><span data-stu-id="e8908-257">The default setting for columns formed from expressions is 0.</span></span> <span data-ttu-id="e8908-258">큰 값 유형이 행 내부에 저장됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-258">This means that large value types are stored in-row.</span></span>  
  
 <span data-ttu-id="e8908-259">인덱싱된 뷰는 분할된 테이블에서 만들 수 있으며 자신이 분할될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-259">Indexed views can be created on a partitioned table, and can themselves be partitioned.</span></span>  
  
 <span data-ttu-id="e8908-260">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 인덱싱된 뷰를 사용하지 않게 하려면 쿼리에 OPTION (EXPAND VIEW) 힌트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-260">To prevent the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from using indexed views, include the OPTION (EXPAND VIEWS) hint on the query.</span></span> <span data-ttu-id="e8908-261">또한 위에 표시된 옵션을 하나라도 잘못 설정하면 최적화 프로그램에서 뷰의 인덱스를 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-261">Also, if any of the listed options are incorrectly set, this will prevent the optimizer from using the indexes on the views.</span></span> <span data-ttu-id="e8908-262">OPTION (EXPAND VIEW) 힌트에 대한 자세한 내용은 [SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8908-262">For more information about the OPTION (EXPAND VIEWS) hint, see [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql).</span></span>  
  
 <span data-ttu-id="e8908-263">뷰가 삭제되면 뷰에 있는 모든 인덱스도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-263">All indexes on a view are dropped when the view is dropped.</span></span> <span data-ttu-id="e8908-264">클러스터형 인덱스가 삭제되면 뷰의 모든 비클러스터형 인덱스 및 자동 생성된 통계가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-264">All nonclustered indexes and auto-created statistics on the view are dropped when the clustered index is dropped.</span></span> <span data-ttu-id="e8908-265">사용자가 만든 뷰의 통계는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-265">User-created statistics on the view are maintained.</span></span> <span data-ttu-id="e8908-266">비클러스터형 인덱스는 개별적으로 삭제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-266">Nonclustered indexes can be individually dropped.</span></span> <span data-ttu-id="e8908-267">뷰에서 클러스터형 인덱스를 삭제하면 저장된 결과 집합도 삭제되고 최적화 프로그램이 표준 뷰와 같은 뷰의 처리 단계로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-267">Dropping the clustered index on the view removes the stored result set, and the optimizer returns to processing the view like a standard view.</span></span>  
  
 <span data-ttu-id="e8908-268">테이블 및 뷰의 인덱스를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-268">Indexes on tables and views can be disabled.</span></span> <span data-ttu-id="e8908-269">테이블의 클러스터형 인덱스가 비활성화되면 테이블과 관련된 뷰의 인덱스도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-269">When a clustered index on a table is disabled, indexes on views associated with the table are also disabled.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8908-270">보안</span><span class="sxs-lookup"><span data-stu-id="e8908-270">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8908-271">권한</span><span class="sxs-lookup"><span data-stu-id="e8908-271">Permissions</span></span>  
 <span data-ttu-id="e8908-272">데이터베이스에는 CREATE VIEW 권한이 필요하고 뷰를 만들 구성표에는 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-272">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e8908-273">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e8908-273">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-indexed-view"></a><span data-ttu-id="e8908-274">인덱싱된 뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e8908-274">To create an indexed view</span></span>  
  
1.  <span data-ttu-id="e8908-275">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8908-276">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8908-277">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e8908-278">예에서는 뷰를 만들고 이 뷰에 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-278">The example creates a view and an index on that view.</span></span> <span data-ttu-id="e8908-279">인덱싱된 뷰를 사용하는 두 개의 쿼리가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8908-279">Two queries are included that use the indexed view.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Set the options to support indexed views.  
    SET NUMERIC_ROUNDABORT OFF;  
    SET ANSI_PADDING, ANSI_WARNINGS, CONCAT_NULL_YIELDS_NULL, ARITHABORT,  
        QUOTED_IDENTIFIER, ANSI_NULLS ON;  
    GO  
    --Create view with schemabinding.  
    IF OBJECT_ID ('Sales.vOrders', 'view') IS NOT NULL  
    DROP VIEW Sales.vOrders ;  
    GO  
    CREATE VIEW Sales.vOrders  
    WITH SCHEMABINDING  
    AS  
        SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Revenue,  
            OrderDate, ProductID, COUNT_BIG(*) AS COUNT  
        FROM Sales.SalesOrderDetail AS od, Sales.SalesOrderHeader AS o  
        WHERE od.SalesOrderID = o.SalesOrderID  
        GROUP BY OrderDate, ProductID;  
    GO  
    --Create an index on the view.  
    CREATE UNIQUE CLUSTERED INDEX IDX_V1   
        ON Sales.vOrders (OrderDate, ProductID);  
    GO  
    --This query can use the indexed view even though the view is   
    --not specified in the FROM clause.  
    SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev,   
        OrderDate, ProductID  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND ProductID BETWEEN 700 and 800  
            AND OrderDate >= CONVERT(datetime,'05/01/2002',101)  
    GROUP BY OrderDate, ProductID  
    ORDER BY Rev DESC;  
    GO  
    --This query can use the above indexed view.  
    SELECT  OrderDate, SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND DATEPART(mm,OrderDate)= 3  
            AND DATEPART(yy,OrderDate) = 2002  
    GROUP BY OrderDate  
    ORDER BY OrderDate ASC;  
    GO  
    ```  
  
 <span data-ttu-id="e8908-280">자세한 내용은 [CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8908-280">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8908-281">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8908-281">See Also</span></span>  
 <span data-ttu-id="e8908-282">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="e8908-283">[SET ANSI_NULLS&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="e8908-284">[SET ANSI_PADDING&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 <span data-ttu-id="e8908-285">[SET ANSI_WARNINGS&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span></span>  
 <span data-ttu-id="e8908-286">[SET ARITHABORT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span></span>  
 <span data-ttu-id="e8908-287">[SET CONCAT_NULL_YIELDS_NULL&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span></span>  
 <span data-ttu-id="e8908-288">[SET NUMERIC_ROUNDABORT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8908-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span></span>  
 [<span data-ttu-id="e8908-289">SET QUOTED_IDENTIFIER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8908-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
  
