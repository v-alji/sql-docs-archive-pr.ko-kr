---
title: MSSQLSERVER_4104 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4104 (Database Engine error)
ms.assetid: 52dc32d8-97ad-4ef0-834d-2e68f215d007
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbbc28a3e15af6fdc8fd44633ccbdfc46e49149d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653428"
---
# <a name="mssqlserver_4104"></a><span data-ttu-id="2d581-102">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="2d581-102">MSSQLSERVER_4104</span></span>
    
## <a name="details"></a><span data-ttu-id="2d581-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2d581-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d581-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2d581-104">Product Name</span></span>|<span data-ttu-id="2d581-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d581-105">SQL Server</span></span>|  
|<span data-ttu-id="2d581-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2d581-106">Event ID</span></span>|<span data-ttu-id="2d581-107">4104</span><span class="sxs-lookup"><span data-stu-id="2d581-107">4104</span></span>|  
|<span data-ttu-id="2d581-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2d581-108">Event Source</span></span>|<span data-ttu-id="2d581-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2d581-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2d581-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2d581-110">Component</span></span>|<span data-ttu-id="2d581-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2d581-111">SQLEngine</span></span>|  
|<span data-ttu-id="2d581-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2d581-112">Symbolic Name</span></span>|<span data-ttu-id="2d581-113">ALG_MULTI_ID_BAD</span><span class="sxs-lookup"><span data-stu-id="2d581-113">ALG_MULTI_ID_BAD</span></span>|  
|<span data-ttu-id="2d581-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2d581-114">Message Text</span></span>|<span data-ttu-id="2d581-115">여러 부분으로 구성된 식별자 "%.\*ls"은(는) 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-115">The multi-part identifier "%.\*ls" could not be bound.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d581-116">설명</span><span class="sxs-lookup"><span data-stu-id="2d581-116">Explanation</span></span>  
 <span data-ttu-id="2d581-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 엔터티 이름을 해당 엔터티의 *식별자*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-117">The name of an entity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is referred to as its *identifier*.</span></span> <span data-ttu-id="2d581-118">예를 들어 쿼리에서 열 및 테이블 이름을 지정하여 엔터티를 참조할 경우 항상 식별자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-118">You use identifiers whenever you reference entities, for example, by specifying column and table names in a query.</span></span> <span data-ttu-id="2d581-119">여러 부분으로 구성된 식별자에는 하나 이상의 한정자가 접두사로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-119">A multi-part identifier contains one or more qualifiers as a prefix for the identifier.</span></span> <span data-ttu-id="2d581-120">예를 들어 테이블 식별자는 해당 테이블이 들어 있는 데이터베이스 이름이나 스키마 이름 같은 한정자를 접두사로 사용하고 열 식별자는 테이블 이름이나 테이블 별칭 같은 한정자를 접두사로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-120">For example, a table identifier may be prefixed with qualifiers such as the database name and schema name in which the table is contained, or a column identifier may be prefixed with qualifiers such as a table name or table alias.</span></span>  
  
 <span data-ttu-id="2d581-121">오류 4104는 지정된 여러 부분으로 구성된 식별자가 기존 엔터티로 매핑될 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-121">Error 4104 indicates that the specified multi-part identifier could not be mapped to an existing entity.</span></span> <span data-ttu-id="2d581-122">이 오류는 다음과 같은 경우에 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-122">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="2d581-123">열 이름의 접두사로 제공된 한정자가 쿼리에 사용된 테이블 또는 별칭 이름과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-123">The qualifier supplied as a prefix for a column name does not correspond to any table or alias name used in the query.</span></span>  
  
     <span data-ttu-id="2d581-124">예를 들어 다음 문에서는 테이블 별칭(`Dept`)을 열 접두사로 사용하지만 테이블 별칭이 FROM 절에서 참조되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-124">For example, the following statement uses a table alias (`Dept`) as a column prefix, but the table alias is not referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department;  
    ```  
  
     <span data-ttu-id="2d581-125">다음 문에서는 여러 부분으로 구성된 열 식별자 `TableB.KeyCol`이 WHERE 절에 두 테이블 간 JOIN 조건의 일부로 지정되어 있지만 `TableB`가 쿼리에서 명시적으로 참조되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-125">In the following statements, a multi-part column identifier `TableB.KeyCol` is specified in the WHERE clause as part of a JOIN condition between two tables, however, `TableB` is not explicitly referenced in the query.</span></span>  
  
    ```  
    DELETE FROM TableA WHERE TableA.KeyCol = TableB.KeyCol;  
    ```  
  
    ```  
    SELECT 'X' FROM TableA WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="2d581-126">테이블의 별칭 이름이 FROM 절에 제공되어 있지만 열에 대해 제공된 한정자가 테이블 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-126">An alias name for the table is supplied in the FROM clause, but the qualifier supplied for a column is the table name.</span></span> <span data-ttu-id="2d581-127">예를 들어 다음 문에서는 테이블 이름 `Department`를 열 접두사로 사용하지만 테이블에는 FROM 절에서 참조된 별칭(`Dept`)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-127">For example, the following statement uses the table name `Department` as the column prefix; however, the table has an alias (`Dept`) referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department AS Dept;  
    ```  
  
     <span data-ttu-id="2d581-128">별칭을 사용하는 경우 문의 다른 위치에서 테이블 이름을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-128">When an alias is used, the table name cannot be used elsewhere in the statement.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2d581-129">에서 여러 부분으로 구성된 식별자가 테이블 이름을 접두사로 사용하는 열을 참조하는지 또는 열 이름을 접두사로 사용하는 CLR UDT(사용자 정의 데이터 형식)의 속성을 참조하는지 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-129">is unable to determine if the multi-part identifier refers to a column prefixed by a table or to a property of a CLR user-defined data type (UDT) prefixed by a column.</span></span> <span data-ttu-id="2d581-130">이는 열 이름의 접두사로 테이블 이름이 사용되는 것과 같은 방법으로 UDT 열의 속성이 열 이름과 속성 이름 사이에 마침표 구분 기호(.)를 사용하여 참조되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-130">This happens because properties of UDT columns are referenced by using the period separator (.) between the column name and the property name in the same way that a column name is prefixed with a table name.</span></span> <span data-ttu-id="2d581-131">다음 예에서는 두 개의 테이블 `a` 및 `b`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-131">The following example creates two tables, `a` and `b`.</span></span> <span data-ttu-id="2d581-132">`b` 테이블에는 CLR UDT `dbo.myudt2`를 데이터 형식으로 사용하는 `a` 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-132">Table `b` contains column `a`, which uses a CLR UDT `dbo.myudt2` as its data type.</span></span> <span data-ttu-id="2d581-133">SELECT 문에는 여러 부분으로 구성된 식별자 `a.c2`가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-133">The SELECT statement contains a multi-part identifier `a.c2`.</span></span>  
  
    ```  
    CREATE TABLE a (c2 int);   
    GO  
    ```  
  
    ```  
    CREATE TABLE b (a dbo.myudt2);   
    GO  
    ```  
  
    ```  
    SELECT a.c2 FROM a, b;   
    ```  
  
     <span data-ttu-id="2d581-134">UDT `myudt2`에 `c2`라는 속성이 없다고 가정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 `a.c2` 식별자가 `a` 테이블의 `c2` 열을 참조하는지 또는 `b` 테이블의 `a` 열과 `c2` 속성을 참조하는지 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-134">Assuming that the UDT `myudt2` does not have a property named `c2`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot determine whether identifier `a.c2`refers to column `c2` in table `a` or to the column `a`, property `c2` in table `b`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d581-135">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2d581-135">User Action</span></span>  
  
-   <span data-ttu-id="2d581-136">쿼리의 FROM 절에 지정된 테이블 이름 또는 별칭 이름과 열 접두사가 일치하도록 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d581-136">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="2d581-137">FROM 절에 테이블 이름의 별칭이 정의되어 있는 경우 해당 테이블과 연결된 열의 한정자로 이 별칭만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-137">If an alias is defined for a table name in the FROM clause, you can only use the alias as a qualifier for columns associated with that table.</span></span>  
  
     <span data-ttu-id="2d581-138">`HumanResources.Department` 테이블을 참조하는 위의 문은 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-138">The statements above that reference the `HumanResources.Department` table can be corrected as follows:</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department AS Dept;  
    GO  
    ```  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department;  
    GO  
    ```  
  
-   <span data-ttu-id="2d581-139">쿼리에 모든 테이블이 지정되어 있고 테이블 간의 JOIN 조건이 올바로 지정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-139">Ensure that all tables are specified in the query and that the JOIN conditions between tables are specified correctly.</span></span> <span data-ttu-id="2d581-140">위의 DELETE 문은 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-140">The DELETE statement above can be corrected as follows:</span></span>  
  
    ```  
    DELETE FROM dbo.TableA  
    WHERE TableA.KeyCol = (SELECT TableB.KeyCol   
                            FROM TableB   
                            WHERE TableA.KeyCol = TableB.KeyCol);  
    GO  
    ```  
  
     <span data-ttu-id="2d581-141">`TableA`에 대한 위의 SELECT 문은 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-141">The SELECT statement above for `TableA` can be corrected as follows:</span></span>  
  
    ```  
    SELECT 'X' FROM TableA, TableB WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
     <span data-ttu-id="2d581-142">또는</span><span class="sxs-lookup"><span data-stu-id="2d581-142">or</span></span>  
  
    ```  
    SELECT 'X' FROM TableA INNER JOIN TableB ON TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="2d581-143">식별자에 대해 고유하고 명확하게 정의된 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-143">Use unique, clearly defined names for identifiers.</span></span> <span data-ttu-id="2d581-144">이렇게 하면 코드를 보다 쉽게 읽고 유지 관리할 수 있으며 여러 엔터티를 모호하게 참조하는 위험을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d581-144">Doing so makes your code easier to read and maintain, and it also minimizes the risk of ambiguous references to multiple entities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d581-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d581-145">See Also</span></span>  
 <span data-ttu-id="2d581-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="2d581-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span></span>  
 [<span data-ttu-id="2d581-147">데이터베이스 식별자</span><span class="sxs-lookup"><span data-stu-id="2d581-147">Database Identifiers</span></span>](../databases/database-identifiers.md)  
  
  
