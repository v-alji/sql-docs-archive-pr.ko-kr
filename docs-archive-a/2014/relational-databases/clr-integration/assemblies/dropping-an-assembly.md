---
title: 어셈블리 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 45d02cbb57459a4c1c11330446021c32dc897353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735331"
---
# <a name="dropping-an-assembly"></a><span data-ttu-id="97dcb-102">어셈블리 삭제</span><span class="sxs-lookup"><span data-stu-id="97dcb-102">Dropping an Assembly</span></span>
  <span data-ttu-id="97dcb-103">CREATE ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 등록한 어셈블리에서 제공하는 기능이 더 이상 필요 없는 경우 이 어셈블리를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement can be deleted, or dropped, when the functionality they provide is no longer needed.</span></span> <span data-ttu-id="97dcb-104">어셈블리를 삭제하면 데이터베이스에서 어셈블리뿐 아니라 디버그 파일 등의 모든 관련 파일이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-104">Dropping an assembly removes the assembly and all of its associated files, such as debug files, from the database.</span></span> <span data-ttu-id="97dcb-105">어셈블리를 삭제하려면 DROP ASSEMBLY 문을 다음 구문으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-105">To drop an assembly, use the DROP ASSEMBLY statement with the following syntax:</span></span>  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 <span data-ttu-id="97dcb-106">DROP ASSEMBLY는 현재 실행되고 있는 어셈블리를 참조하는 코드를 방해하지 않지만 DROP ASSEMBLY를 실행한 후 해당 어셈블리 코드를 호출하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-106">DROP ASSEMBLY does not interfere with any code referencing the assembly that is currently running, but after DROP ASSEMBLY executes, any attempts to invoke the assembly code fail.</span></span>  
  
 <span data-ttu-id="97dcb-107">어셈블리가 데이터베이스에 있는 다른 어셈블리에서 참조되거나 현재 데이터베이스의 CLR(공용 언어 런타임) 함수, 프로시저, 트리거, UDT(사용자 정의 형식) 또는 UDA(사용자 정의 집계)에서 사용되면 DROP ASSEMBLY가 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-107">DROP ASSEMBLY returns an error if the assembly is referenced by another assembly that exists in the database, or if it is used by common language runtime (CLR) functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs) in the current database.</span></span> <span data-ttu-id="97dcb-108">먼저 DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER 및 DROP TYPE 문을 사용하여 어셈블리에 포함된 관리되는 데이터베이스 개체를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-108">First use the DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER, and DROP TYPE statements to delete any managed database objects contained in the assembly.</span></span>  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="97dcb-109">데이터베이스에서 UDT 제거</span><span class="sxs-lookup"><span data-stu-id="97dcb-109">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="97dcb-110">DROP TYPE 문은 현재 데이터베이스에서 UDT를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-110">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="97dcb-111">UDT를 삭제한 경우 DROP ASSEMBLY 문을 사용하여 데이터베이스에서 어셈블리를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-111">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="97dcb-112">다음과 같이 개체가 UDT에 종속되어 있으면 DROP TYPE 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-112">The DROP TYPE statement fails if objects depend on the UDT, as in the following situations:</span></span>  
  
-   <span data-ttu-id="97dcb-113">UDT를 사용하여 정의한 열이 포함된 데이터베이스의 테이블</span><span class="sxs-lookup"><span data-stu-id="97dcb-113">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="97dcb-114">데이터베이스에 WITH SCHEMABINDING 절로 만든 함수, 저장 프로시저 또는 트리거가 있고 이러한 루틴이 UDT의 변수 또는 매개 변수를 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="97dcb-114">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="97dcb-115">UDT 종속성 찾기</span><span class="sxs-lookup"><span data-stu-id="97dcb-115">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="97dcb-116">따라서 먼저 모든 종속 개체를 삭제한 다음 DROP TYPE 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-116">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span> <span data-ttu-id="97dcb-117">다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리는 **AdventureWorks** 데이터베이스에서 UDT를 사용 하는 모든 열과 매개 변수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97dcb-117">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a><span data-ttu-id="97dcb-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97dcb-118">See Also</span></span>  
 <span data-ttu-id="97dcb-119">[CLR 통합 어셈블리 관리](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="97dcb-119">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="97dcb-120">[어셈블리 변경](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="97dcb-120">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="97dcb-121">[어셈블리 만들기](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="97dcb-121">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="97dcb-122">[DROP AGGREGATE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97dcb-122">[DROP AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span></span>  
 <span data-ttu-id="97dcb-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97dcb-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span></span>  
 <span data-ttu-id="97dcb-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97dcb-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="97dcb-125">[DROP TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97dcb-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="97dcb-126">DROP TYPE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97dcb-126">DROP TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
