---
title: 포함된 데이터베이스 데이터 정렬 | Microsoft 문서
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- contained database, collations
ms.assetid: 4b44f6b9-2359-452f-8bb1-5520f2528483
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2648dbedea7708c4f39c922c56bba96cf38b0c0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734139"
---
# <a name="contained-database-collations"></a><span data-ttu-id="5f946-102">포함된 데이터베이스 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-102">Contained Database Collations</span></span>
  <span data-ttu-id="5f946-103">여러 가지 속성이 대/소문자 구분, 악센트 구분 및 사용되는 기본 언어를 비롯한 텍스트 데이터의 같음 의미 체계 및 정렬 순서에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-103">Various properties affect the sort order and equality semantics of textual data, including case sensitivity, accent sensitivity, and the base language being used.</span></span> <span data-ttu-id="5f946-104">이러한 사항은 데이터에 대한 데이터 정렬 선택을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-104">These qualities are expressed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the choice of collation for the data.</span></span> <span data-ttu-id="5f946-105">데이터 정렬에 대한 자세한 내용은 [데이터 정렬 및 유니코드 지원](../collations/collation-and-unicode-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f946-105">For a more in-depth discussion of collations themselves, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="5f946-106">데이터 정렬은 사용자 테이블에 저장된 데이터에 적용될 뿐만 아니라 메타데이터, 임시 개체, 변수 이름 등 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 처리하는 모든 텍스트에 적용됩니다. 이러한 항목의 처리 방식은 포함되지 않은 데이터베이스인지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-106">Collations apply not only to data stored in user tables, but to all text handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including metadata, temporary objects, variable names, etc. The handling of these differs in contained and non-contained databases.</span></span> <span data-ttu-id="5f946-107">이러한 변경 내용은 대부분의 사용자에게는 영향을 미치지 않지만 인스턴스 독립 및 일관성을 제공하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-107">This change will not affect many users, but helps provide instance independence and uniformity.</span></span> <span data-ttu-id="5f946-108">하지만 이로 인해 일부 혼란이 발생할 수도 있고 포함된 데이터베이스와 포함되지 않은 데이터베이스에 모두 액세스하는 세션의 경우에는 문제가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-108">But this may also cause some confusion, as well as problems for sessions that access both contained and non-contained databases.</span></span>  
  
 <span data-ttu-id="5f946-109">이 항목에서는 변경 내용에 대해 설명하고 변경으로 인해 문제가 발생할 수 있는 영역을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-109">This topic clarifies the content of the change, and examines areas where the change may cause problems.</span></span>  
  
## <a name="non-contained-databases"></a><span data-ttu-id="5f946-110">포함되지 않은 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5f946-110">Non-Contained Databases</span></span>  
 <span data-ttu-id="5f946-111">모든 데이터베이스는 기본 데이터 정렬이 있습니다. 기본 데이터 정렬은 데이터베이스를 만들거나 변경할 때 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-111">All databases have a default collation (which can be set when creating or altering a database.</span></span> <span data-ttu-id="5f946-112">이러한 데이터 정렬은 데이터베이스의 모든 메타데이터에 사용되며 데이터베이스 내 모든 문자열 열의 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-112">This collation is used for all metadata in the database, as well as the default for all string columns within the database.</span></span> <span data-ttu-id="5f946-113">사용자는 `COLLATE` 절을 사용하여 특정 열의 데이터 정렬을 다르게 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-113">Users can choose a different collation for any particular column by using the `COLLATE` clause.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="5f946-114">예 1</span><span class="sxs-lookup"><span data-stu-id="5f946-114">Example 1</span></span>  
 <span data-ttu-id="5f946-115">예를 들어 베이징에서 작업하는 경우 중국어 데이터 정렬을 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-115">For example, if we were working in Beijing, we might use a Chinese collation:</span></span>  
  
```sql  
ALTER DATABASE MyDB COLLATE Chinese_Simplified_Pinyin_100_CI_AS;  
```  
  
 <span data-ttu-id="5f946-116">이제 열을 만들면 이 열의 기본 데이터 정렬은 중국어 데이터 정렬이 되지만 원하는 경우 다른 데이터 정렬을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-116">Now if we create a column, its default collation will be this Chinese collation, but we can choose another one if we want:</span></span>  
  
```sql  
CREATE TABLE MyTable  
      (mycolumn1 nvarchar,  
      mycolumn2 nvarchar COLLATE Frisian_100_CS_AS);  
GO  
SELECT name, collation_name  
FROM sys.columns  
WHERE name LIKE 'mycolumn%' ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```sql  
name            collation_name  
--------------- ----------------------------------  
mycolumn1       Chinese_Simplified_Pinyin_100_CI_AS  
mycolumn2       Frisian_100_CS_AS  
```  
  
 <span data-ttu-id="5f946-117">이러한 방법은 상당히 간단해 보이지만 몇 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-117">This appears relatively simple, but several problems arise.</span></span> <span data-ttu-id="5f946-118">열에 대 한 데이터 정렬은 테이블이 만들어진 데이터베이스에 종속 되기 때문에에 저장 된 임시 테이블을 사용 하는 경우 문제가 발생 합니다 `tempdb` .</span><span class="sxs-lookup"><span data-stu-id="5f946-118">Because the collation for a column is dependent on the database in which the table is created, problems arise with the use of temporary tables which are stored in `tempdb`.</span></span> <span data-ttu-id="5f946-119">의 데이터 정렬은 `tempdb` 대개 인스턴스의 데이터 정렬과 일치 하며,이는 데이터베이스 데이터 정렬과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-119">The collation of `tempdb` usually matches the collation for the instance, which does not have to match the database collation.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="5f946-120">예제 2</span><span class="sxs-lookup"><span data-stu-id="5f946-120">Example 2</span></span>  
 <span data-ttu-id="5f946-121">예를 들어 **Latin1_General** 데이터 정렬을 사용하는 인스턴스에서 위의 중국어 데이터베이스가 사용되는 경우를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-121">For example, consider the (Chinese) database above when used on an instance with a **Latin1_General** collation:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max)) ;  
GO  
```  
  
 <span data-ttu-id="5f946-122">얼핏 보면 두 테이블이 동일한 스키마를 가지고 있는 것처럼 보이지만 데이터베이스의 데이터 정렬이 다르기 때문에 실제로는 값이 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-122">At first glance, these two tables look like they have the same schema, but since the collations of the databases differ, the values are actually incompatible:</span></span>  
  
```  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="5f946-123">메시지 468, 수준 16, 상태 9, 줄 2</span><span class="sxs-lookup"><span data-stu-id="5f946-123">Msg 468, Level 16, State 9, Line 2</span></span>  
  
 <span data-ttu-id="5f946-124">같음 연산에서 "Latin1_General_100_CI_AS_KS_WS_SC"와 "Chinese_Simplified_Pinyin_100_CI_AS" 사이의 데이터 정렬 충돌을 해결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-124">Cannot resolve the collation conflict between "Latin1_General_100_CI_AS_KS_WS_SC" and Chinese_Simplified_Pinyin_100_CI_AS" in the equal to operation.</span></span>  
  
 <span data-ttu-id="5f946-125">임시 테이블에 대해 명시적으로 데이터 정렬을 수행하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-125">We can fix this by explicitly collating the temporary table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5f946-126">에서 `DATABASE_DEFAULT` 절에 제공되는 `COLLATE` 키워드를 사용하면 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-126">makes this somewhat easier by providing the `DATABASE_DEFAULT` keyword for the `COLLATE` clause.</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max) COLLATE DATABASE_DEFAULT);  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="5f946-127">이 구문은 이제 오류 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-127">This now runs without error.</span></span>  
  
 <span data-ttu-id="5f946-128">변수와 관련된 데이터 정렬 종속 동작도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-128">We can also see collation-dependent behavior with variables.</span></span> <span data-ttu-id="5f946-129">다음과 같은 함수가 있다고 합시다.</span><span class="sxs-lookup"><span data-stu-id="5f946-129">Consider the following function:</span></span>  
  
```  
CREATE FUNCTION f(@x INT) RETURNS INT  
AS BEGIN   
      DECLARE @I INT = 1  
      DECLARE @?? INT = 2  
      RETURN @x * @i  
END;  
```  
  
 <span data-ttu-id="5f946-130">이 함수는 조금 특이한 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-130">This is a rather peculiar function.</span></span> <span data-ttu-id="5f946-131">대/소문자를 구분 하는 데이터 정렬에서 @i return 절의는 또는 @에 바인딩할 수 없습니다 @I ??.</span><span class="sxs-lookup"><span data-stu-id="5f946-131">In a case-sensitive collation, the @i in the return clause cannot bind to either @I or @??.</span></span> <span data-ttu-id="5f946-132">대/소문자를 구분하지 않는 Latin1_General 데이터 정렬에서 @i는 @I에 바인딩하고 함수는 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-132">In a case-insensitive Latin1_General collation, @i binds to @I, and the function returns 1.</span></span> <span data-ttu-id="5f946-133">하지만 대/소문자를 구분 하지 않는 터키어 데이터 정렬에서는 @i @??,에 바인딩되고 함수는 2를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-133">But in a case-insensitive Turkish collation, @i binds to @??, and the function returns 2.</span></span> <span data-ttu-id="5f946-134">이런 동작은 데이터 정렬이 다른 인스턴스 간을 이동하는 데이터베이스에 혼란을 초래합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-134">This can wreak havoc on a database that moves between instances with different collations.</span></span>  
  
## <a name="contained-databases"></a><span data-ttu-id="5f946-135">포함된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5f946-135">Contained Databases</span></span>  
 <span data-ttu-id="5f946-136">포함된 데이터베이스의 디자인 목표는 독립적인 데이터베이스를 만드는 것이므로 인스턴스 및 `tempdb` 데이터 정렬에 대한 종속성은 존재하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-136">Since a design objective of contained databases is to make them self-contained, the dependence on the instance and `tempdb` collations must be severed.</span></span> <span data-ttu-id="5f946-137">이러한 목표를 위해 포함된 데이터베이스에는 카탈로그 데이터 정렬이라는 개념이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-137">To do this, contained databases introduce the concept of the catalog collation.</span></span> <span data-ttu-id="5f946-138">카탈로그 데이터 정렬은 시스템 메타데이터 및 임시 개체에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-138">The catalog collation is used for system metadata and transient objects.</span></span> <span data-ttu-id="5f946-139">자세한 내용은 아래에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-139">Details are provided below.</span></span>  
  
 <span data-ttu-id="5f946-140">포함된 데이터베이스에서 카탈로그 데이터 정렬이 **Latin1_General_100_CI_AS_WS_KS_SC**라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-140">In a contained database, the catalog collation **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="5f946-141">이 데이터 정렬은 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 포함된 데이터베이스에서 동일하며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-141">This collation is the same for all contained databases on all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and cannot be changed.</span></span>  
  
 <span data-ttu-id="5f946-142">데이터베이스 데이터 정렬은 유지되지만 사용자 데이터의 기본 데이터 정렬로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-142">The database collation is retained, but is only used as the default collation for user data.</span></span> <span data-ttu-id="5f946-143">기본적으로 데이터베이스 데이터 정렬은 model 데이터베이스 데이터 정렬과 같지만 `CREATE` `ALTER DATABASE` 포함 되지 않은 데이터베이스와 마찬가지로 또는 명령을 통해 사용자가 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-143">By default, the database collation is equal to the model database collation, but can be changed by the user through a `CREATE` or `ALTER DATABASE` command as with non-contained databases.</span></span>  
  
 <span data-ttu-id="5f946-144">새 키워드 `CATALOG_DEFAULT`를 `COLLATE` 절에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-144">A new keyword, `CATALOG_DEFAULT`, is available in the `COLLATE` clause.</span></span> <span data-ttu-id="5f946-145">이 키워드는 포함된 데이터베이스와 포함되지 않은 데이터베이스 모두에서 현재 메타데이터 데이터 정렬에 대한 바로 가기로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-145">This is used as a shortcut to the current collation of metadata in both contained and non-contained databases.</span></span> <span data-ttu-id="5f946-146">즉, 포함되지 않은 데이터베이스에서 `CATALOG_DEFAULT`는 메타데이터가 데이터베이스 데이터 정렬로 정렬되기 때문에 현재 데이터베이스 데이터 정렬을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-146">That is, in a non-contained database, `CATALOG_DEFAULT` will return the current database collation, since metadata is collated in the database collation.</span></span> <span data-ttu-id="5f946-147">포함된 데이터베이스에서는 사용자가 카탈로그 데이터 정렬과 일치하지 않도록 데이터베이스 데이터 정렬을 변경할 수 있으므로 이 두 값이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-147">In a contained database, these two values may be different, since the user can change the database collation so that it does not match the catalog collation.</span></span>  
  
 <span data-ttu-id="5f946-148">포함된 데이터베이스와 포함되지 않은 데이터베이스의 여러 개체 동작은 다음 표에 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-148">The behavior of various objects in both non-contained and contained databases is summarized in this table:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="5f946-149">**항목**</span><span class="sxs-lookup"><span data-stu-id="5f946-149">**Item**</span></span>|<span data-ttu-id="5f946-150">**포함되지 않은 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="5f946-150">**Non-Contained Database**</span></span>|<span data-ttu-id="5f946-151">**포함된 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="5f946-151">**Contained Database**</span></span>|  
|<span data-ttu-id="5f946-152">사용자 데이터(기본값)</span><span class="sxs-lookup"><span data-stu-id="5f946-152">User Data (default)</span></span>|<span data-ttu-id="5f946-153">COLLATE</span><span class="sxs-lookup"><span data-stu-id="5f946-153">DATABASE_DEFAULT</span></span>|<span data-ttu-id="5f946-154">COLLATE</span><span class="sxs-lookup"><span data-stu-id="5f946-154">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-155">임시 데이터(기본값)</span><span class="sxs-lookup"><span data-stu-id="5f946-155">Temp Data (default)</span></span>|<span data-ttu-id="5f946-156">TempDB 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-156">TempDB Collation</span></span>|<span data-ttu-id="5f946-157">COLLATE</span><span class="sxs-lookup"><span data-stu-id="5f946-157">DATABASE_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-158">메타데이터</span><span class="sxs-lookup"><span data-stu-id="5f946-158">Metadata</span></span>|<span data-ttu-id="5f946-159">DATABASE_DEFAULT/CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-159">DATABASE_DEFAULT / CATALOG_DEFAULT</span></span>|<span data-ttu-id="5f946-160">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-160">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-161">임시 메타데이터</span><span class="sxs-lookup"><span data-stu-id="5f946-161">Temporary Metadata</span></span>|<span data-ttu-id="5f946-162">TempDB 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-162">tempdb Collation</span></span>|<span data-ttu-id="5f946-163">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-163">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-164">variables</span><span class="sxs-lookup"><span data-stu-id="5f946-164">Variables</span></span>|<span data-ttu-id="5f946-165">인스턴스 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-165">Instance Collation</span></span>|<span data-ttu-id="5f946-166">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-166">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-167">Goto 레이블</span><span class="sxs-lookup"><span data-stu-id="5f946-167">Goto Labels</span></span>|<span data-ttu-id="5f946-168">인스턴스 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-168">Instance Collation</span></span>|<span data-ttu-id="5f946-169">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-169">CATALOG_DEFAULT</span></span>|  
|<span data-ttu-id="5f946-170">커서 이름</span><span class="sxs-lookup"><span data-stu-id="5f946-170">Cursor Names</span></span>|<span data-ttu-id="5f946-171">인스턴스 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="5f946-171">Instance Collation</span></span>|<span data-ttu-id="5f946-172">CATALOG_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5f946-172">CATALOG_DEFAULT</span></span>|  
  
 <span data-ttu-id="5f946-173">앞에서 설명된 임시 테이블 예를 보면 이 데이터 정렬 동작 때문에 대부분의 임시 테이블 사용 시 명시적으로 `COLLATE` 절을 사용할 필요가 없음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-173">If we temp table example previously described, we can see that this collation behavior eliminates the need for an explicit `COLLATE` clause in most temp table uses.</span></span> <span data-ttu-id="5f946-174">포함된 데이터베이스에서 데이터베이스와 인스턴스 데이터 정렬이 다른 경우에도 이제 이 코드는 오류 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-174">In a contained database, this code now runs without error, even if the database and instance collations differ:</span></span>  
  
```sql  
CREATE TABLE T1 (T1_txt nvarchar(max)) ;  
GO  
CREATE TABLE #T2 (T2_txt nvarchar(max));  
GO  
SELECT T1_txt, T2_txt  
FROM T1   
JOIN #T2   
    ON T1.T1_txt = #T2.T2_txt ;  
```  
  
 <span data-ttu-id="5f946-175">`T1_txt` 와 `T2_txt` 가 포함된 데이터베이스의 데이터베이스 데이터 정렬로 정렬되기 때문에 이 코드는 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-175">This works because both `T1_txt` and `T2_txt` are collated in the database collation of the contained database.</span></span>  
  
## <a name="crossing-between-contained-and-uncontained-contexts"></a><span data-ttu-id="5f946-176">포함된 컨텍스트와 포함되지 않은 컨텍스트 간 교차</span><span class="sxs-lookup"><span data-stu-id="5f946-176">Crossing Between Contained and Uncontained Contexts</span></span>  
 <span data-ttu-id="5f946-177">포함된 데이터베이스의 세션은 포함된 상태로 유지되는 한 연결된 데이터베이스 내부에 남아 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-177">As long as a session in a contained database remains contained, it must remain within the database to which it connected.</span></span> <span data-ttu-id="5f946-178">이 경우의 동작은 매우 명확합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-178">In this case the behavior is very straightforward.</span></span> <span data-ttu-id="5f946-179">하지만 세션이 포함된 컨텍스트와 포함되지 않은 컨텍스트 사이를 교차하는 경우 두 규칙 집합이 중재되어야 하므로 동작은 더 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-179">But if a session crosses between contained and non-contained contexts, the behavior becomes more complex, since the two sets of rules must be bridged.</span></span> <span data-ttu-id="5f946-180">사용자가 `USE`를 통해 다른 데이터베이스를 사용할 수 있는 부분적으로 포함된 데이터베이스에서 이러한 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-180">This can happen in a partially-contained database, since a user may `USE` to another database.</span></span> <span data-ttu-id="5f946-181">이 경우 데이터 정렬 규칙의 차이는 다음 원칙에 따라 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-181">In this case, the difference in collation rules is handled by the following principle.</span></span>  
  
-   <span data-ttu-id="5f946-182">일괄 처리의 데이터 정렬 동작은 일괄 처리가 시작되는 데이터베이스에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-182">The collation behavior for a batch is determined by the database in which the batch begins.</span></span>  
  
 <span data-ttu-id="5f946-183">이러한 의사 결정은 최초의 `USE`를 포함하여 어떤 명령도 실행되기 이전에 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-183">Note that this decision is made before any commands are issued, including an initial `USE`.</span></span> <span data-ttu-id="5f946-184">즉, 일괄 처리가 포함된 데이터베이스에서 시작되지만 첫 번째 명령이 포함되지 않은 데이터베이스에 대한 `USE`인 경우 이 일괄 처리에 대해서는 포함된 데이터 정렬 동작이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-184">That is, if a batch begins in a contained database, but the first command is a `USE` to a non-contained database, the contained collation behavior will still be used for the batch.</span></span> <span data-ttu-id="5f946-185">이 점을 고려하면 예를 들어 변수에 대한 참조가 다음과 같은 여러 가지 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-185">Given this, a reference to a variable, for example, may have multiple possible outcomes:</span></span>  
  
-   <span data-ttu-id="5f946-186">참조가 일치하는 항목을 정확히 한 개 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-186">The reference may find exactly one match.</span></span> <span data-ttu-id="5f946-187">이 경우 참조는 오류 없이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-187">In this case, the reference will work without error.</span></span>  
  
-   <span data-ttu-id="5f946-188">참조가 이전에는 일치 항목이 있었던 현재 데이터 정렬에서 일치 항목을 찾지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-188">The reference may not find a match in the current collation where there was one before.</span></span> <span data-ttu-id="5f946-189">이런 경우 변수가 분명히 만들어졌음에도 불구하고 변수가 없음을 나타내는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-189">This will raise an error indicating that the variable does not exist, even though it was apparently created.</span></span>  
  
-   <span data-ttu-id="5f946-190">참조가 원래는 구별되었던 여러 개의 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-190">The reference may find multiple matches that were originally distinct.</span></span> <span data-ttu-id="5f946-191">이 경우에도 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-191">This will also raise an error.</span></span>  
  
 <span data-ttu-id="5f946-192">몇 가지 예를 들어 이러한 경우를 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-192">We'll illustrate this with a few examples.</span></span> <span data-ttu-id="5f946-193">이 경우 데이터베이스 데이터 정렬이 기본 데이터 정렬( `MyCDB` Latin1_General_100_CI_AS_WS_KS_SC **)로 설정된**라는 부분적으로 포함된 데이터베이스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-193">For these we assume there is a partially-contained database named `MyCDB` with its database collation set to the default collation, **Latin1_General_100_CI_AS_WS_KS_SC**.</span></span> <span data-ttu-id="5f946-194">인스턴스 데이터 정렬은 `Latin1_General_100_CS_AS_WS_KS_SC`라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-194">We assume that the instance collation is `Latin1_General_100_CS_AS_WS_KS_SC`.</span></span> <span data-ttu-id="5f946-195">두 데이터 정렬은 대/소문자 구분 여부에서만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-195">The two collations differ only in case sensitivity.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="5f946-196">예 1</span><span class="sxs-lookup"><span data-stu-id="5f946-196">Example 1</span></span>  
 <span data-ttu-id="5f946-197">다음 예에서는 참조가 일치하는 항목을 정확히 하나 찾는 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-197">The following example illustrates the case where the reference finds exactly one match.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #a VALUES(1);  
GO  
  
USE master;  
GO  
  
SELECT * FROM #a;  
GO  
  
Results:  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
x  
-----------  
1  
```  
  
 <span data-ttu-id="5f946-198">이 경우 식별된 #a는 대/소문자를 구분하지 않는 카탈로그 데이터 정렬과 대/소문자를 구분하는 인스턴스 데이터 정렬 모두에 바인딩하고 코드는 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-198">In this case, the identified #a binds in both the case-insensitive catalog collation and the case-sensitive instance collation, and the code works.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="5f946-199">예제 2</span><span class="sxs-lookup"><span data-stu-id="5f946-199">Example 2</span></span>  
 <span data-ttu-id="5f946-200">다음 예에서는 참조가 이전에는 일치하는 항목이 있었던 현재 데이터 정렬에서 일치하는 항목을 찾지 못하는 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-200">The following example illustrates the case where the reference does not find a match in the current collation where there was one before.</span></span>  
  
```  
USE MyCDB;  
GO  
  
CREATE TABLE #a(x int);  
INSERT INTO #A VALUES(1);  
GO  
```  
  
 <span data-ttu-id="5f946-201">여기에서 #A는 대/소문자를 구분하지 않는 기본 데이터 정렬에서 #a와 바인딩하고 삽입이 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-201">Here, the #A binds to #a in the case-insensitive default collation, and the insert works,</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="5f946-202">하지만 스크립트를 계속 실행하면...</span><span class="sxs-lookup"><span data-stu-id="5f946-202">But if we continue the script...</span></span>  
  
```  
USE master;  
GO  
  
SELECT * FROM #A;  
GO  
```  
  
 <span data-ttu-id="5f946-203">대/소문자를 구분하는 인스턴스 데이터 정렬에서 #A에 바인딩하려고 하는 동안 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-203">We get an error trying to bind to #A in the case-sensitive instance collation;</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="5f946-204">메시지 208, 수준 16, 상태 0, 줄 2</span><span class="sxs-lookup"><span data-stu-id="5f946-204">Msg 208, Level 16, State 0, Line 2</span></span>  
  
 <span data-ttu-id="5f946-205">개체 이름 '#A'이(가) 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-205">Invalid object name '#A'.</span></span>  
  
### <a name="example-3"></a><span data-ttu-id="5f946-206">예제 3</span><span class="sxs-lookup"><span data-stu-id="5f946-206">Example 3</span></span>  
 <span data-ttu-id="5f946-207">다음 예에서는 참조가 원래는 구별되었던 여러 개의 일치 항목을 찾는 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-207">The following example illustrates the case where the reference finds multiple matches that were originally distinct.</span></span> <span data-ttu-id="5f946-208">먼저 `tempdb` 인스턴스와 동일한 대/소문자 구분 데이터 정렬을 포함 하는에서 시작 하 여 다음 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-208">First, we start in `tempdb` (which has the same case-sensitive collation as our instance) and execute the following statements.</span></span>  
  
```  
USE tempdb;  
GO  
  
CREATE TABLE #a(x int);  
GO  
CREATE TABLE #A(x int);  
GO  
INSERT INTO #a VALUES(1);  
GO  
INSERT INTO #A VALUES(2);  
GO  
```  
  
 <span data-ttu-id="5f946-209">이 데이터 정렬에서는 테이블이 구별되므로 이 작업은 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-209">This succeeds, since the tables are distinct in this collation:</span></span>  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
(1 row(s) affected)  
```  
  
 <span data-ttu-id="5f946-210">하지만 포함된 데이터베이스로 넘어가면 이러한 테이블에 더 이상 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-210">If we move into our contained database, however, we find that we can no longer bind to these tables.</span></span>  
  
```  
USE MyCDB;  
GO  
SELECT * FROM #a;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 <span data-ttu-id="5f946-211">메시지 12800, 수준 16, 상태 1, 줄 2</span><span class="sxs-lookup"><span data-stu-id="5f946-211">Msg 12800, Level 16, State 1, Line 2</span></span>  
  
 <span data-ttu-id="5f946-212">임시 테이블 이름 '#a'에 대한 참조는 모호하며 해결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-212">The reference to temp table name '#a' is ambiguous and cannot be resolved.</span></span> <span data-ttu-id="5f946-213">가능한 후보는 '#a' 및 '#A'입니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-213">Possible candidates are '#a' and '#A'.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="5f946-214">결론</span><span class="sxs-lookup"><span data-stu-id="5f946-214">Conclusion</span></span>  
 <span data-ttu-id="5f946-215">포함된 데이터베이스의 데이터 정렬 동작은 포함되지 않은 데이터베이스의 데이터 정렬 동작과 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-215">The collation behavior of contained databases differs subtly from that in non-contained databases.</span></span> <span data-ttu-id="5f946-216">이 동작은 인스턴스 독립과 단순성을 제공하므로 일반적으로 유익합니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-216">This behavior is generally beneficial, providing instance-independence and simplicity.</span></span> <span data-ttu-id="5f946-217">포함된 데이터베이스와 포함되지 않은 데이터베이스에 세션이 모두 액세스하는 경우 일부 사용자에게 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f946-217">Some users may have issues, particularly when a session accesses both contained and non-contained databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f946-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f946-218">See Also</span></span>  
 [<span data-ttu-id="5f946-219">포함된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5f946-219">Contained Databases</span></span>](contained-databases.md)  
  
  
