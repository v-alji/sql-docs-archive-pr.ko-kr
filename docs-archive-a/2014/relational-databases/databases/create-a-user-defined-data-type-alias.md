---
title: 사용자 정의 데이터 형식 별칭 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.userdefineddatatype.general.f1
- sql12.swb.new.datatype.properties.general.f1
helpviewer_keywords:
- alias data types [SQL Server], creating
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35db332c23e2df5a8e67c3677cd2411768816765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638832"
---
# <a name="create-a-user-defined-data-type-alias"></a><span data-ttu-id="d3b2c-102">사용자 정의 데이터 형식 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="d3b2c-102">Create a User-Defined Data Type Alias</span></span>
  <span data-ttu-id="d3b2c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 새 사용자 정의 데이터 형식 별칭을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-103">This topic describes how to create a new user-defined data type alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d3b2c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d3b2c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d3b2c-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d3b2c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d3b2c-107">보안</span><span class="sxs-lookup"><span data-stu-id="d3b2c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d3b2c-108">**사용자 정의 데이터 형식 별칭을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-108">**To create a user-defined data type alias, using:**</span></span>  
  
     [<span data-ttu-id="d3b2c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d3b2c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d3b2c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d3b2c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d3b2c-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d3b2c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d3b2c-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d3b2c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d3b2c-113">사용자 정의 데이터 형식 별칭의 이름은 식별자에 대한 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-113">The name of a user-defined data type alias must comply with the rules for identifiers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d3b2c-114">보안</span><span class="sxs-lookup"><span data-stu-id="d3b2c-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d3b2c-115">권한</span><span class="sxs-lookup"><span data-stu-id="d3b2c-115">Permissions</span></span>  
 <span data-ttu-id="d3b2c-116">현재 데이터베이스에 대한 CREATE TYPE 권한 및 *schema_name*에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-116">Requires CREATE TYPE permission in the current database and ALTER permission on *schema_name*.</span></span> <span data-ttu-id="d3b2c-117">*schema_name* 을 지정하지 않으면 현재 사용자에 대한 스키마를 결정하는 기본 이름 확인 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-117">If *schema_name* is not specified, the default name resolution rules for determining the schema for the current user apply.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d3b2c-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d3b2c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-user-defined-data-type"></a><span data-ttu-id="d3b2c-119">사용자 정의 데이터 형식을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d3b2c-119">To create a user-defined data type</span></span>  
  
1.  <span data-ttu-id="d3b2c-120">개체 탐색기에서 **데이터베이스**를 확장하고 목록에서 원하는 데이터베이스를 확장한 다음, **프로그래밍 기능**과 **유형**을 차례로 확장하고 **사용자 정의 데이터 형식**을 마우스 오른쪽 단추로 클릭한 다음 **새 사용자 정의 데이터 형식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-120">In Object Explorer, expand **Databases**, expand a database, expand **Programmability**, expand **Types**, right-click **User-Defined Data Types**, and then click **New User-Defined Data Type**.</span></span>  
  
     <span data-ttu-id="d3b2c-121">**NULL 허용**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-121">**Allow NULLs**</span></span>  
     <span data-ttu-id="d3b2c-122">사용자 정의 데이터 형식에 NULL 값이 허용되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-122">Specify whether the user-defined data type can accept NULL values.</span></span> <span data-ttu-id="d3b2c-123">기존 사용자 정의 데이터 형식의 Null 허용 여부는 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-123">The nullability of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="d3b2c-124">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-124">**Data type**</span></span>  
     <span data-ttu-id="d3b2c-125">목록 상자에서 기본 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-125">Select the base data type from the list box.</span></span> <span data-ttu-id="d3b2c-126">목록 상자에는 `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` 및 `xml` 데이터 형식을 제외한 모든 데이터 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-126">The list box displays all data types except for the `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` , and `xml` data types.</span></span> <span data-ttu-id="d3b2c-127">기존 사용자 정의 데이터 형식의 데이터 형식은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-127">The data type of an existing user-defined data type is not editable.</span></span>  
  
     <span data-ttu-id="d3b2c-128">**기본값**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-128">**Default**</span></span>  
     <span data-ttu-id="d3b2c-129">필요에 따라 사용자 정의 데이터 형식 별칭에 바인딩할 규칙 또는 기본값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-129">Optionally select a rule or a default to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="d3b2c-130">**길이/전체 자릿수**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-130">**Length/Precision**</span></span>  
     <span data-ttu-id="d3b2c-131">데이터 형식에 적용되는 길이 또는 전체 자릿수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-131">Displays the length or precision of the data type as applicable.</span></span> <span data-ttu-id="d3b2c-132">**길이** 는 문자 기반 사용자 정의 데이터 형식에 적용되고 **전체 자릿수** 는 숫자 기반 사용자 정의 데이터 형식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-132">**Length** applies to character-based user-defined data types; **Precision** applies only to numeric-based user-defined data types.</span></span> <span data-ttu-id="d3b2c-133">이 옵션의 레이블은 이전에 선택한 데이터 형식에 따라 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-133">The label changes depending on the data type selected earlier.</span></span> <span data-ttu-id="d3b2c-134">선택한 데이터 형식의 길이 또는 전체 자릿수가 고정된 경우에는 이 상자를 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-134">This box is not editable if the length or precision of the selected data type is fixed.</span></span>  
  
     <span data-ttu-id="d3b2c-135">`nvarchar(max)`, `varchar(max)` 또는 `varbinary(max)` 데이터 형식의 경우에는 길이가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-135">Length is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
     <span data-ttu-id="d3b2c-136">**이름**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-136">**Name**</span></span>  
     <span data-ttu-id="d3b2c-137">새 사용자 정의 데이터 형식 별칭을 만드는 경우 데이터베이스에서 사용자 정의 데이터 형식을 나타내는 데 사용할 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-137">If you are creating a new user-defined data type alias, type a unique name to be used across the database to represent the user-defined data type.</span></span> <span data-ttu-id="d3b2c-138">최대 문자 수는 시스템 데이터 형식과 일치 해야 합니다 `sysname` .</span><span class="sxs-lookup"><span data-stu-id="d3b2c-138">The maximum number of characters must match the system `sysname` data type.</span></span> <span data-ttu-id="d3b2c-139">기존 사용자 정의 데이터 형식 별칭의 이름은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-139">The name of an existing user-defined data type alias is not editable.</span></span>  
  
     <span data-ttu-id="d3b2c-140">**규칙**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-140">**Rule**</span></span>  
     <span data-ttu-id="d3b2c-141">필요에 따라 사용자 정의 데이터 형식 별칭에 바인딩할 규칙을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-141">Optionally select a rule to bind to the user-defined data type alias.</span></span>  
  
     <span data-ttu-id="d3b2c-142">**규모**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-142">**Scale**</span></span>  
     <span data-ttu-id="d3b2c-143">소수점의 오른쪽에 저장될 수 있는 최대 자릿수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-143">Specify the maximum number of decimal digits that can be stored to the right of the decimal point.</span></span>  
  
     <span data-ttu-id="d3b2c-144">**스키마**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-144">**Schema**</span></span>  
     <span data-ttu-id="d3b2c-145">현재 사용자가 사용할 수 있는 모든 스키마의 목록에서 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-145">Select a schema from a list of all schemas available to the current user.</span></span> <span data-ttu-id="d3b2c-146">현재 사용자에 대한 기본 스키마가 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-146">The default selection is the default schema for the current user.</span></span>  
  
     <span data-ttu-id="d3b2c-147">**스토리지**</span><span class="sxs-lookup"><span data-stu-id="d3b2c-147">**Storage**</span></span>  
     <span data-ttu-id="d3b2c-148">사용자 정의 데이터 형식 별칭에 대한 최대 스토리지 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-148">Displays the maximum storage size for the user-defined data type alias.</span></span> <span data-ttu-id="d3b2c-149">최대 스토리지 크기는 전체 자릿수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-149">Maximum storage sizes vary, based on precision.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="d3b2c-150">1 - 9</span><span class="sxs-lookup"><span data-stu-id="d3b2c-150">1 - 9</span></span>|<span data-ttu-id="d3b2c-151">5</span><span class="sxs-lookup"><span data-stu-id="d3b2c-151">5</span></span>|  
    |<span data-ttu-id="d3b2c-152">10 - 19</span><span class="sxs-lookup"><span data-stu-id="d3b2c-152">10 - 19</span></span>|<span data-ttu-id="d3b2c-153">9</span><span class="sxs-lookup"><span data-stu-id="d3b2c-153">9</span></span>|  
    |<span data-ttu-id="d3b2c-154">20 - 28</span><span class="sxs-lookup"><span data-stu-id="d3b2c-154">20 - 28</span></span>|<span data-ttu-id="d3b2c-155">13</span><span class="sxs-lookup"><span data-stu-id="d3b2c-155">13</span></span>|  
    |<span data-ttu-id="d3b2c-156">29 - 38</span><span class="sxs-lookup"><span data-stu-id="d3b2c-156">29 - 38</span></span>|<span data-ttu-id="d3b2c-157">17</span><span class="sxs-lookup"><span data-stu-id="d3b2c-157">17</span></span>|  
  
     <span data-ttu-id="d3b2c-158">`nchar`및 `nvarchar` 데이터 형식의 경우 저장소 값은 항상 **길이**값의 두 배입니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-158">For `nchar` and `nvarchar` data types, the storage value is always two times the value in **Length**.</span></span>  
  
     <span data-ttu-id="d3b2c-159">`nvarchar(max)`, `varchar(max)` 또는 `varbinary(max)` 데이터 형식의 경우에는 스토리지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-159">Storage is not displayed for `nvarchar(max)`, `varchar(max)`, or `varbinary(max)` data types.</span></span>  
  
2.  <span data-ttu-id="d3b2c-160">**새 사용자 정의 데이터 형식** 대화 상자의 **스키마** 상자에 이 데이터 형식 별칭을 소유할 스키마를 입력하거나 찾아보기 단추를 사용하여 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-160">In the **New User-defined Data Type** dialog box, in the **Schema** box, type the schema to own this data type alias, or use the browse button to select the schema.</span></span>  
  
3.  <span data-ttu-id="d3b2c-161">**이름** 상자에 새 데이터 형식 별칭의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-161">In the **Name** box, type a name for the new data type alias.</span></span>  
  
4.  <span data-ttu-id="d3b2c-162">**데이터 형식** 상자에서 어떤 데이터 형식을 기반으로 새 데이터 형식 별칭을 만들 것인지 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-162">In the **Data type** box, select the data type that the new data type alias will be based on.</span></span>  
  
5.  <span data-ttu-id="d3b2c-163">해당 데이터 형식에 맞게 적절히 **길이**, **전체 자릿수**및 **소수 자릿수** 상자를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-163">Complete the **Length**, **Precision**, and **Scale** boxes if appropriate for that data type.</span></span>  
  
6.  <span data-ttu-id="d3b2c-164">새 데이터 형식 별칭에 NULL 값을 허용하려면 **NULL 허용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-164">Check **Allow NULLs** if the new data type alias can permit NULL values.</span></span>  
  
7.  <span data-ttu-id="d3b2c-165">기본값이나 규칙을 새 데이터 형식 별칭에 바인딩하려면 **바인딩** 영역에서 **기본값** 또는 **규칙** 상자를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-165">In the **Binding** area, complete the **Default** or **Rule** boxes if you want to bind a default or rule to the new data type alias.</span></span> <span data-ttu-id="d3b2c-166">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 기본값과 규칙을 만들 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="d3b2c-166">Defaults and rules cannot be created in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d3b2c-167">대신 [!INCLUDE[tsql](../../includes/tsql-md.md)]를</span><span class="sxs-lookup"><span data-stu-id="d3b2c-167">Use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d3b2c-168">기본값과 규칙을 만드는 예제 코드는 템플릿 탐색기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-168">Example code for creating defaults and rules are available in Template Explorer.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d3b2c-169">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d3b2c-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-user-defined-data-type-alias"></a><span data-ttu-id="d3b2c-170">사용자 정의 데이터 형식 별칭을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d3b2c-170">To create a user-defined data type alias</span></span>  
  
1.  <span data-ttu-id="d3b2c-171">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-171">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3b2c-172">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-172">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d3b2c-173">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-173">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d3b2c-174">이 예에서는 시스템이 제공하는 `varchar` 데이터 형식을 기반으로 데이터 형식 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-174">This example creates a data type alias based on the system-supplied `varchar` data type.</span></span> <span data-ttu-id="d3b2c-175">`ssn` 데이터 형식 별칭은 11자리의 주민 등록 번호(999-99-9999)를 보유하는 열에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-175">The `ssn` data type alias is used for columns holding 11-digit social security numbers (999-99-9999).</span></span> <span data-ttu-id="d3b2c-176">이 열은 NULL이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b2c-176">The column cannot be NULL.</span></span>  
  
```sql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3b2c-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3b2c-177">See Also</span></span>  
 <span data-ttu-id="d3b2c-178">[데이터베이스 식별자](database-identifiers.md) </span><span class="sxs-lookup"><span data-stu-id="d3b2c-178">[Database Identifiers](database-identifiers.md) </span></span>  
 [<span data-ttu-id="d3b2c-179">CREATE TYPE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d3b2c-179">CREATE TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-type-transact-sql)  
  
  
