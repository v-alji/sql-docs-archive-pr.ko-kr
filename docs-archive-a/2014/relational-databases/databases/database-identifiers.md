---
title: 데이터베이스 식별자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- regular identifiers [SQL Server]
- identifiers [SQL Server]
- names [SQL Server], identifiers
- identifiers [SQL Server], about identifiers
- SQL Server identifiers
- Transact-SQL identifiers
- database objects [SQL Server], names
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 347b20c12a0ac5edd82172741377617aa0fe12c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650110"
---
# <a name="database-identifiers"></a><span data-ttu-id="bdd36-102">데이터베이스 식별자</span><span class="sxs-lookup"><span data-stu-id="bdd36-102">Database Identifiers</span></span>
  <span data-ttu-id="bdd36-103">데이터베이스 개체 이름을 그 개체의 식별자라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-103">The database object name is referred to as its identifier.</span></span> <span data-ttu-id="bdd36-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 모든 개체에는 식별자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-104">Everything in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can have an identifier.</span></span> <span data-ttu-id="bdd36-105">서버, 데이터베이스 그리고 테이블, 뷰, 열, 인덱스, 트리거, 프로시저, 제약 조건, 규칙 등과 같은 데이터베이스 개체도 식별자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-105">Servers, databases, and database objects, such as tables, views, columns, indexes, triggers, procedures, constraints, and rules, can have identifiers.</span></span> <span data-ttu-id="bdd36-106">식별자는 대부분의 개체에서 필수 항목이지만 제약 조건과 같은 일부 개체에서는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-106">Identifiers are required for most objects, but are optional for some objects such as constraints.</span></span>  
  
 <span data-ttu-id="bdd36-107">개체의 식별자는 개체를 정의할 때 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-107">An object identifier is created when the object is defined.</span></span> <span data-ttu-id="bdd36-108">만들어진 식별자는 개체를 참조하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-108">The identifier is then used to reference the object.</span></span> <span data-ttu-id="bdd36-109">예를 들어 다음 문은 식별자가 `TableX`인 테이블과 식별자가 `KeyCol` 및 `Description`인 두 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-109">For example, the following statement creates a table with the identifier `TableX`, and two columns with the identifiers `KeyCol` and `Description`:</span></span>  
  
```  
CREATE TABLE TableX  
(KeyCol INT PRIMARY KEY, Description nvarchar(80))  
```  
  
 <span data-ttu-id="bdd36-110">이 테이블에는 이름 없는 제약 조건도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-110">This table also has an unnamed constraint.</span></span> <span data-ttu-id="bdd36-111">`PRIMARY KEY` 제약 조건에는 식별자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-111">The `PRIMARY KEY` constraint has no identifier.</span></span>  
  
 <span data-ttu-id="bdd36-112">식별자의 데이터 정렬은 식별자가 정의된 수준에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-112">The collation of an identifier depends on the level at which it is defined.</span></span> <span data-ttu-id="bdd36-113">로그인과 데이터베이스 이름 등 인스턴스 수준 개체의 식별자에는 인스턴스의 기본 데이터 정렬이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-113">Identifiers of instance-level objects, such as logins and database names, are assigned the default collation of the instance.</span></span> <span data-ttu-id="bdd36-114">테이블, 뷰, 열 이름 등 데이터베이스에 있는 개체의 식별자에는 데이터베이스의 기본 데이터 정렬이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-114">Identifiers of objects in a database, such as tables, views, and column names, are assigned the default collation of the database.</span></span> <span data-ttu-id="bdd36-115">예를 들어 대/소문자만 다르고 이름은 동일한 두 테이블은 데이터 정렬이 대/소문자를 구분하는 데이터베이스에서는 만들 수 있지만 데이터 정렬이 대/소문자를 구분하지 않는 데이터베이스에서는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-115">For example, two tables with names that differ only in case can be created in a database that has case-sensitive collation, but cannot be created in a database that has case-insensitive collation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdd36-116">변수의 이름 또는 함수와 저장 프로시저의 매개 변수는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식별자의 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-116">The names of variables, or the parameters of functions and stored procedures must comply with the rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
## <a name="classes-of-identifiers"></a><span data-ttu-id="bdd36-117">식별자 클래스</span><span class="sxs-lookup"><span data-stu-id="bdd36-117">Classes of Identifiers</span></span>  
 <span data-ttu-id="bdd36-118">다음과 같이 두 가지 식별자 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-118">There are two classes of identifiers:</span></span>  
  
 <span data-ttu-id="bdd36-119">일반 식별자</span><span class="sxs-lookup"><span data-stu-id="bdd36-119">Regular identifiers</span></span>  
 <span data-ttu-id="bdd36-120">식별자 형식에 대한 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-120">Comply with the rules for the format of identifiers.</span></span> <span data-ttu-id="bdd36-121">일반 식별자는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 사용될 때 구분되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-121">Regular identifiers are not delimited when they are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
SELECT *  
FROM TableX  
WHERE KeyCol = 124  
```  
  
 <span data-ttu-id="bdd36-122">구분 식별자</span><span class="sxs-lookup"><span data-stu-id="bdd36-122">Delimited identifiers</span></span>  
 <span data-ttu-id="bdd36-123">큰따옴표(")나 대괄호([])로 묶여져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-123">Are enclosed in double quotation marks (") or brackets ([ ]).</span></span> <span data-ttu-id="bdd36-124">식별자 형식 규칙을 따르는 식별자는 구분되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-124">Identifiers that comply with the rules for the format of identifiers might not be delimited.</span></span> <span data-ttu-id="bdd36-125">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-125">For example:</span></span>  
  
```  
SELECT *  
FROM [TableX]         --Delimiter is optional.  
WHERE [KeyCol] = 124  --Delimiter is optional.  
```  
  
 <span data-ttu-id="bdd36-126">모든 식별자 규칙을 따르지 않는 식별자는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 구분되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-126">Identifiers that do not comply with all the rules for identifiers must be delimited in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="bdd36-127">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-127">For example:</span></span>  
  
```  
SELECT *  
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.  
WHERE [order] = 10   --Identifier is a reserved keyword.  
```  
  
 <span data-ttu-id="bdd36-128">일반 식별자 및 구분 식별자 모두는 1-128자의 문자로 이루어져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-128">Both regular and delimited identifiers must contain from 1 through 128 characters.</span></span> <span data-ttu-id="bdd36-129">로컬 임시 테이블의 경우에는 식별자에 116자까지 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-129">For local temporary tables, the identifier can have a maximum of 116 characters.</span></span>  
  
## <a name="rules-for-regular-identifiers"></a><span data-ttu-id="bdd36-130">일반 식별자 규칙</span><span class="sxs-lookup"><span data-stu-id="bdd36-130">Rules for Regular Identifiers</span></span>  
 <span data-ttu-id="bdd36-131">변수, 함수 및 저장 프로시저의 이름은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식별자의 다음 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-131">The names of variables, functions, and stored procedures must comply with the following rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
1.  <span data-ttu-id="bdd36-132">첫 문자는 다음 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-132">The first character must be one of the following:</span></span>  
  
    -   <span data-ttu-id="bdd36-133">Unicode Standard 3.2에서 정의한 문자.</span><span class="sxs-lookup"><span data-stu-id="bdd36-133">A letter as defined by the Unicode Standard 3.2.</span></span> <span data-ttu-id="bdd36-134">문자의 유니코드 정의에는 a-z, A-Z의 라틴어 문자와 다른 언어의 문자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-134">The Unicode definition of letters includes Latin characters from a through z, from A through Z, and also letter characters from other languages.</span></span>  
  
    -   <span data-ttu-id="bdd36-135">밑줄(_), at 기호(@) 또는 숫자 기호(#)</span><span class="sxs-lookup"><span data-stu-id="bdd36-135">The underscore (_), at sign (@), or number sign (#).</span></span>  
  
         <span data-ttu-id="bdd36-136">특정 기호는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 식별자의 맨 앞에 올 때 특별한 의미를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-136">Certain symbols at the beginning of an identifier have special meaning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bdd36-137">at 기호로 시작하는 일반 식별자는 항상 지역 변수나 매개 변수를 표시하며 다른 개체 유형의 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-137">A regular identifier that starts with the at sign always denotes a local variable or parameter and cannot be used as the name of any other type of object.</span></span> <span data-ttu-id="bdd36-138"># 기호로 시작하는 식별자는 임시 테이블 또는 프로시저를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-138">An identifier that starts with a number sign denotes a temporary table or procedure.</span></span> <span data-ttu-id="bdd36-139">이중 숫자 기호(##)로 시작하는 식별자는 전역 임시 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-139">An identifier that starts with double number signs (##) denotes a global temporary object.</span></span> <span data-ttu-id="bdd36-140">숫자 기호나 이중 숫자 기호를 사용하여 다른 개체 유형의 이름을 시작할 수 있지만 이 방법은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-140">Although the number sign or double number sign characters can be used to begin the names of other types of objects, we do not recommend this practice.</span></span>  
  
         <span data-ttu-id="bdd36-141">일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수는 두 개의 at 기호(@@)로 시작하는 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-141">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] functions have names that start with double at signs (@@).</span></span> <span data-ttu-id="bdd36-142">이러한 함수와 혼동하지 않도록 @@으로 시작하는 이름을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-142">To avoid confusion with these functions, you should not use names that start with @@.</span></span>  
  
2.  <span data-ttu-id="bdd36-143">후속 문자는 다음을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-143">Subsequent characters can include the following:</span></span>  
  
    -   <span data-ttu-id="bdd36-144">Unicode Standard 3.2에서 정의한 문자</span><span class="sxs-lookup"><span data-stu-id="bdd36-144">Letters as defined in the Unicode Standard 3.2.</span></span>  
  
    -   <span data-ttu-id="bdd36-145">기본 라틴 또는 기타 국가 스크립트의 10진수</span><span class="sxs-lookup"><span data-stu-id="bdd36-145">Decimal numbers from either Basic Latin or other national scripts.</span></span>  
  
    -   <span data-ttu-id="bdd36-146">at 기호(@), 달러 기호($), 숫자 기호 또는 밑줄</span><span class="sxs-lookup"><span data-stu-id="bdd36-146">The at sign, dollar sign ($), number sign, or underscore.</span></span>  
  
3.  <span data-ttu-id="bdd36-147">[!INCLUDE[tsql](../../includes/tsql-md.md)] 예약어는 식별자로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-147">The identifier must not be a [!INCLUDE[tsql](../../includes/tsql-md.md)] reserved word.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bdd36-148">에서 예약어는 대문자와 소문자가 모두 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-148">reserves both the uppercase and lowercase versions of reserved words.</span></span> <span data-ttu-id="bdd36-149">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 식별자를 사용하는 경우 이러한 규칙을 따르지 않는 식별자는 큰따옴표나 대괄호로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-149">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span> <span data-ttu-id="bdd36-150">예약되는 단어는 데이터베이스 호환성 수준에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-150">The words that are reserved depend on the database compatibility level.</span></span> <span data-ttu-id="bdd36-151">이 수준은 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) 문을 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-151">This level can be set by using the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) statement.</span></span>  
  
4.  <span data-ttu-id="bdd36-152">포함된 공백이나 특수 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-152">Embedded spaces or special characters are not allowed.</span></span>  
  
5.  <span data-ttu-id="bdd36-153">보충 문자도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-153">Supplementary characters are not allowed.</span></span>  
  
 <span data-ttu-id="bdd36-154">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 식별자를 사용하는 경우 이러한 규칙을 따르지 않는 식별자는 큰따옴표나 대괄호로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-154">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdd36-155">일반 식별자 형식의 일부 규칙은 데이터베이스 호환성 수준에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-155">Some rules for the format of regular identifiers depend on the database compatibility level.</span></span> <span data-ttu-id="bdd36-156">이 수준은 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdd36-156">This level can be set by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd36-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdd36-157">See Also</span></span>  
 <span data-ttu-id="bdd36-158">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-159">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-160">[CREATE DEFAULT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-161">[CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-162">[CREATE RULE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-163">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-164">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-165">[CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-166">[DECLARE @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-167">[DELETE&#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-168">[INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-169">[예약 키워드&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-169">[Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span></span>  
 <span data-ttu-id="bdd36-170">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdd36-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="bdd36-171">UPDATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdd36-171">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
