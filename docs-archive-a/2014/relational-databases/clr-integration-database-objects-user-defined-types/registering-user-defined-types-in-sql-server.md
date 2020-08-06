---
title: SQL Server에서 사용자 정의 형식 등록 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d24f7948e093335eff708f3c4a8a7361cfc156f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647709"
---
# <a name="registering-user-defined-types-in-sql-server"></a><span data-ttu-id="ca871-102">SQL Server의 사용자 정의 형식 등록</span><span class="sxs-lookup"><span data-stu-id="ca871-102">Registering User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="ca871-103">에서 UDT (사용자 정의 형식)를 사용 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-103">In order to use a user-defined type (UDT) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must register it.</span></span> <span data-ttu-id="ca871-104">UDT를 등록하려면 해당 형식을 사용할 데이터베이스에 어셈블리를 등록하고 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-104">Registering a UDT involves registering the assembly and creating the type in the database in which you wish to use it.</span></span> <span data-ttu-id="ca871-105">UDT는 범위가 단일 데이터베이스로 한정되며, 데이터베이스마다 동일한 어셈블리와 UDT를 등록하지 않는 한 여러 데이터베이스에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-105">UDTs are scoped to a single database, and cannot be used in multiple databases unless the identical assembly and UDT are registered with each database.</span></span> <span data-ttu-id="ca871-106">UDT 어셈블리가 등록되고 형식이 만들어지면 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 클라이언트 코드에 UDT를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-106">Once the UDT assembly is registered and the type created, you can use the UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)] and in client code.</span></span> <span data-ttu-id="ca871-107">자세한 내용은 [CLR 사용자 정의 형식](clr-user-defined-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca871-107">For more information, see [CLR User-Defined Types](clr-user-defined-types.md).</span></span>  
  
## <a name="using-visual-studio-to-deploy-udts"></a><span data-ttu-id="ca871-108">Visual Studio를 사용하여 UDT 배포</span><span class="sxs-lookup"><span data-stu-id="ca871-108">Using Visual Studio to Deploy UDTs</span></span>  
 <span data-ttu-id="ca871-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio를 사용하면 UDT를 간편하게 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-109">The easiest way to deploy your UDT is by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="ca871-110">그러나 배포 시나리오가 복잡하거나 높은 유연성이 요구되는 경우에는 이 항목에서 설명하는 대로 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-110">For more complex deployment scenarios and the greatest flexibility, however, use [!INCLUDE[tsql](../../includes/tsql-md.md)] as discussed later in this topic.</span></span>  
  
 <span data-ttu-id="ca871-111">다음 단계에 따라 Visual Studio를 사용하여 UDT를 만들고 배포하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca871-111">Follow these steps to create and deploy a UDT using Visual Studio:</span></span>  
  
1.  <span data-ttu-id="ca871-112">**Visual Basic** 또는 **Visual c #** 언어 노드에서 새 **데이터베이스** 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-112">Create a new **Database** project in the **Visual Basic** or **Visual C#** language nodes.</span></span>  
  
2.  <span data-ttu-id="ca871-113">UDT를 포함할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-113">Add a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the UDT.</span></span>  
  
3.  <span data-ttu-id="ca871-114">**사용자 정의 형식** 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-114">Add a **User-Defined Type** class.</span></span>  
  
4.  <span data-ttu-id="ca871-115">UDT를 구현하는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-115">Write code to implement the UDT.</span></span>  
  
5.  <span data-ttu-id="ca871-116">**빌드** 메뉴에서 **배포**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-116">From the **Build** menu, select **Deploy**.</span></span> <span data-ttu-id="ca871-117">그러면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 어셈블리가 등록되고 형식이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-117">This registers the assembly and creates the type in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
## <a name="using-transact-sql-to-deploy-udts"></a><span data-ttu-id="ca871-118">Transact-SQL을 사용하여 UDT 배포</span><span class="sxs-lookup"><span data-stu-id="ca871-118">Using Transact-SQL to Deploy UDTs</span></span>  
 <span data-ttu-id="ca871-119">UDT를 사용할 데이터베이스에 어셈블리를 등록할 때는 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-119">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY syntax is used to register the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="ca871-120">등록된 어셈블리는 파일 시스템에 외부적으로 저장되는 것이 아니라 데이터베이스 시스템 테이블에 내부적으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-120">It is stored internally in database system tables, not externally in the file system.</span></span> <span data-ttu-id="ca871-121">UDT가 외부 어셈블리에 종속되어 있는 경우 해당 어셈블리도 데이터베이스에 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-121">If the UDT is dependent on external assemblies, they too must be loaded into the database.</span></span> <span data-ttu-id="ca871-122">UDT를 사용할 데이터베이스에 UDT를 만들 때는 CREATE TYPE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-122">The CREATE TYPE statement is used to create the UDT in the database in which it is to be used.</span></span> <span data-ttu-id="ca871-123">자세한 내용은 [CREATE ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/create-assembly-transact-sql) 및 [Create TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca871-123">For more information, see [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql) and [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
### <a name="using-create-assembly"></a><span data-ttu-id="ca871-124">CREATE ASSEMBLY 사용</span><span class="sxs-lookup"><span data-stu-id="ca871-124">Using CREATE ASSEMBLY</span></span>  
 <span data-ttu-id="ca871-125">CREATE ASSEMBLY 구문은 UDT를 사용할 데이터베이스에 어셈블리를 등록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-125">The CREATE ASSEMBLY syntax registers the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="ca871-126">등록된 어셈블리에는 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-126">Once the assembly is registered, it has no dependencies.</span></span>  
  
 <span data-ttu-id="ca871-127">특정 데이터베이스에 같은 어셈블리를 여러 버전으로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-127">Creating multiple versions of the same assembly in a given database is not allowed.</span></span> <span data-ttu-id="ca871-128">그러나 특정 데이터베이스의 culture에 따라 같은 어셈블리를 여러 버전으로 만들 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-128">However, it is possible to create multiple versions of the same assembly based on culture in a given database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ca871-129">에서는 어셈블리의 여러 culture 버전을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 서로 다른 이름으로 등록하여 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-129">distinguishes multiple culture versions of an assembly by different names as registered in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ca871-130">자세한 내용은 .NET Framework SDK에서 "강력한 이름의 어셈블리 생성 및 사용"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca871-130">For more information, see "Creating and Using Strong-Named Assemblies" in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="ca871-131">SAFE 또는 EXTERNAL_ACCESS 권한 집합을 사용하여 CREATE ASSEMBLY를 실행하면 확인할 수 있으며 형식이 안전한지 여부에 대해 어셈블리 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-131">When CREATE ASSEMBLY is executed with the SAFE or EXTERNAL_ACCESS permission sets, the assembly is checked to make sure that it is verifiable and type safe.</span></span> <span data-ttu-id="ca871-132">권한 집합을 지정하지 않으면 SAFE가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-132">If you omit specifying a permission set, SAFE is assumed.</span></span> <span data-ttu-id="ca871-133">UNSAFE 권한 집합을 사용한 코드는 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-133">Code with the UNSAFE permission set is not checked.</span></span> <span data-ttu-id="ca871-134">어셈블리 권한 집합에 대한 자세한 내용은 [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca871-134">For more information about assembly permission sets, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="ca871-135">예제</span><span class="sxs-lookup"><span data-stu-id="ca871-135">Example</span></span>  
 <span data-ttu-id="ca871-136">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SAFE 권한 집합을 사용 하 여 **AdventureWorks** 데이터베이스의에 Point 어셈블리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-136">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the Point assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the **AdventureWorks** database, with the SAFE permission set.</span></span> <span data-ttu-id="ca871-137">WITH PERMISSION_SET 절을 생략하면 어셈블리가 SAFE 권한 집합을 사용하여 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-137">If the WITH PERMISSION_SET clause is omitted, the assembly is registered with the SAFE permission set.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="ca871-138">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 FROM 절에 *<assembly_bits>* 인수를 사용 하 여 어셈블리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the assembly using *<assembly_bits>* argument in the FROM clause.</span></span> <span data-ttu-id="ca871-139">이 `varbinary` 값은 파일을 바이트 스트림으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-139">This `varbinary` value represents the file as a stream of bytes.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 ... 21ac78  
```  
  
### <a name="using-create-type"></a><span data-ttu-id="ca871-140">CREATE TYPE 사용</span><span class="sxs-lookup"><span data-stu-id="ca871-140">Using CREATE TYPE</span></span>  
 <span data-ttu-id="ca871-141">어셈블리가 데이터베이스에 로드되면 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 문을 사용하여 형식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-141">Once the assembly is loaded into the database, you can then create the type using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement.</span></span> <span data-ttu-id="ca871-142">그러면 해당 데이터베이스에 사용 가능한 형식 목록에 해당 형식이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-142">This adds the type to the list of available types for that database.</span></span> <span data-ttu-id="ca871-143">형식은 범위가 데이터베이스로 제한되므로 해당 형식을 만든 데이터베이스에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-143">The type has database scope and the type can only be used in the database in which it was created.</span></span> <span data-ttu-id="ca871-144">데이터베이스에 해당 UDT가 이미 있으면 오류가 발생하며 CREATE TYPE 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-144">If the UDT already exists in the database, the CREATE TYPE statement fails with an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca871-145">CREATE TYPE 구문은 네이티브 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 별칭 데이터 형식을 만드는 데도 사용되며 별칭 데이터 형식을 만들기 위한 수단으로서 `sp_addtype`을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-145">The CREATE TYPE syntax is also used for creating native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types, and is intended to replace `sp_addtype` as a means of creating alias data types.</span></span> <span data-ttu-id="ca871-146">CREATE TYPE 구문의 일부 선택적 인수는 UDT 만들기와 관련이 있으며 기본 유형과 같은 별칭 데이터 형식을 만드는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-146">Some of the optional arguments in the CREATE TYPE syntax refer to creating UDTs, and are not applicable to creating alias data types (such as base type).</span></span>  
  
 <span data-ttu-id="ca871-147">자세한 내용은 [CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca871-147">For more information, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="ca871-148">예제</span><span class="sxs-lookup"><span data-stu-id="ca871-148">Example</span></span>  
 <span data-ttu-id="ca871-149">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 `Point` 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-149">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates the `Point` type.</span></span> <span data-ttu-id="ca871-150">외부 이름은 *AssemblyName*의 두 부분으로 구성 된 명명 구문을 사용 하 여 지정 됩니다. *UDTName*.</span><span class="sxs-lookup"><span data-stu-id="ca871-150">The EXTERNAL NAME is specified using the two-part naming syntax of *AssemblyName*.*UDTName*.</span></span>  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="ca871-151">데이터베이스에서 UDT 제거</span><span class="sxs-lookup"><span data-stu-id="ca871-151">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="ca871-152">DROP TYPE 문은 현재 데이터베이스에서 UDT를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-152">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="ca871-153">UDT를 삭제한 경우 DROP ASSEMBLY 문을 사용하여 데이터베이스에서 어셈블리를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-153">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="ca871-154">다음과 같은 상황에서는 DROP TYPE 문이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-154">The DROP TYPE statement does not execute in the following situations:</span></span>  
  
-   <span data-ttu-id="ca871-155">UDT를 사용하여 정의한 열이 포함된 데이터베이스의 테이블</span><span class="sxs-lookup"><span data-stu-id="ca871-155">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="ca871-156">데이터베이스에 WITH SCHEMABINDING 절로 만든 함수, 저장 프로시저 또는 트리거가 있고 이러한 루틴이 UDT의 변수 또는 매개 변수를 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="ca871-156">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ca871-157">예제</span><span class="sxs-lookup"><span data-stu-id="ca871-157">Example</span></span>  
 <span data-ttu-id="ca871-158">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]은 다음과 같은 순서로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-158">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] must execute in the following order.</span></span> <span data-ttu-id="ca871-159">먼저 `Point` UDT를 참조하는 테이블을 삭제한 다음 형식, 어셈블리를 차례로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-159">First the table which references the `Point` UDT must be dropped, then the type, and finally the assembly.</span></span>  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="ca871-160">UDT 종속성 찾기</span><span class="sxs-lookup"><span data-stu-id="ca871-160">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="ca871-161">UDT 열 정의가 있는 테이블과 같은 종속 개체가 있으면 DROP TYPE 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-161">If there are dependent objects, such as tables with UDT column definitions, the DROP TYPE statement fails.</span></span> <span data-ttu-id="ca871-162">또한 WITH SCHEMABINDING 절을 사용하여 데이터베이스에 만든 함수, 저장 프로시저 또는 트리거가 있고 이러한 루틴에서 사용자 정의 형식의 변수 및 매개 변수를 사용하는 경우에도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-162">It also fails if there are functions, stored procedures, or triggers created in the database using the WITH SCHEMABINDING clause, if these routines use variables or parameters of the user-defined type.</span></span> <span data-ttu-id="ca871-163">따라서 먼저 모든 종속 개체를 삭제한 다음 DROP TYPE 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-163">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span>  
  
 <span data-ttu-id="ca871-164">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리는 **AdventureWorks** 데이터베이스에서 UDT를 사용 하는 모든 열과 매개 변수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-164">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
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
  
## <a name="maintaining-udts"></a><span data-ttu-id="ca871-165">UDT 유지 관리</span><span class="sxs-lookup"><span data-stu-id="ca871-165">Maintaining UDTs</span></span>  
 <span data-ttu-id="ca871-166">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 만든 UDT는 수정할 수 없습니다. 단, 해당 형식의 기반이 되는 어셈블리는 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-166">You cannot modify a UDT once it is created in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, although you can alter the assembly on which the type is based.</span></span> <span data-ttu-id="ca871-167">대부분의 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE 문을 사용하여 데이터베이스에서 UDT를 제거하고 기본 어셈블리를 변경한 다음 ALTER ASSEMBLY 문을 사용하여 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-167">In most cases, you must remove the UDT from the database with the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE statement, make changes to the underlying assembly, and reload it using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="ca871-168">그런 다음 UDT와 모든 종속 개체를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-168">You then need to re-create the UDT and any dependent objects.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ca871-169">예제</span><span class="sxs-lookup"><span data-stu-id="ca871-169">Example</span></span>  
 <span data-ttu-id="ca871-170">UDT 어셈블리의 원본 코드를 변경하여 다시 컴파일한 후에는 ALTER ASSEMBLY 문이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-170">The ALTER ASSEMBLY statement is used after you have made changes to the source code in your UDT assembly and recompiled it.</span></span> <span data-ttu-id="ca871-171">이 문은 .dll 파일을 서버에 복사하고 새 어셈블리에 다시 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-171">It copies the .dll file to the server and rebinds to the new assembly.</span></span> <span data-ttu-id="ca871-172">전체 구문은 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca871-172">For the complete syntax, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
 <span data-ttu-id="ca871-173">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 문은 디스크의 지정된 위치에서 Point.dll 어셈블리를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement reloads the Point.dll assembly from the specified location on disk.</span></span>  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a><span data-ttu-id="ca871-174">ALTER ASSEMBLY를 사용하여 원본 코드 추가</span><span class="sxs-lookup"><span data-stu-id="ca871-174">Using ALTER ASSEMBLY to Add Source Code</span></span>  
 <span data-ttu-id="ca871-175">ALTER ASSEMBLY 구문의 ADD FILE 절은 CREATE ASSEMBLY에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-175">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="ca871-176">이 절을 사용하여 원본 코드나 어셈블리와 연결된 다른 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-176">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="ca871-177">이렇게 하면 파일이 원래 위치에서 복사되어 데이터베이스의 시스템 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-177">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="ca871-178">따라서 UDT의 현재 버전을 다시 만들거나 문서화해야 할 경우 간편하게 원본 코드나 기타 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-178">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="ca871-179">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 문은 UDT에 대 한 Point.cs 클래스 소스 코드를 추가 합니다 `Point` .</span><span class="sxs-lookup"><span data-stu-id="ca871-179">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement adds the Point.cs class source code for the `Point` UDT.</span></span> <span data-ttu-id="ca871-180">이 문은 Point.cs 파일에 있는 텍스트를 복사하여 "PointSource"라는 이름으로 데이터베이스에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-180">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 <span data-ttu-id="ca871-181">어셈블리 정보는 어셈블리가 설치 된 데이터베이스의 **sys. assembly_files** 테이블에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-181">Assembly information is stored in the **sys.assembly_files** table in the database where the assembly has been installed.</span></span> <span data-ttu-id="ca871-182">**Assembly_files** 테이블에는 다음 열이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-182">The **sys.assembly_files** table contains the following columns.</span></span>  
  
 <span data-ttu-id="ca871-183">**assembly_id**</span><span class="sxs-lookup"><span data-stu-id="ca871-183">**assembly_id**</span></span>  
 <span data-ttu-id="ca871-184">어셈블리에 대해 정의되는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-184">The identifier defined for the assembly.</span></span> <span data-ttu-id="ca871-185">해당 어셈블리와 관련한 모든 개체에 이 번호가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-185">This number is assigned to all objects relating to the same assembly.</span></span>  
  
 <span data-ttu-id="ca871-186">**name**</span><span class="sxs-lookup"><span data-stu-id="ca871-186">**name**</span></span>  
 <span data-ttu-id="ca871-187">개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-187">The name of the object.</span></span>  
  
 <span data-ttu-id="ca871-188">**file_id**</span><span class="sxs-lookup"><span data-stu-id="ca871-188">**file_id**</span></span>  
 <span data-ttu-id="ca871-189">지정 된 **assembly_id** 와 연결 된 첫 번째 개체의 값이 1 인 각 개체를 식별 하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-189">A number identifying each object, with the first object associated with a given **assembly_id** being given the value of 1.</span></span> <span data-ttu-id="ca871-190">동일한 **assembly_id**와 연결 된 개체가 여러 개 있는 경우 각 후속 **file_id** 값은 1 씩 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-190">If there are multiple objects associated with the same **assembly_id**, then each subsequent **file_id** value is incremented by 1.</span></span>  
  
 <span data-ttu-id="ca871-191">**content**</span><span class="sxs-lookup"><span data-stu-id="ca871-191">**content**</span></span>  
 <span data-ttu-id="ca871-192">어셈블리 또는 파일의 16진수 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-192">The hexadecimal representation of the assembly or file.</span></span>  
  
 <span data-ttu-id="ca871-193">CAST 또는 CONVERT 함수를 사용 하 여 **콘텐츠** 열의 내용을 읽을 수 있는 텍스트로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-193">You can use the CAST or CONVERT function to convert the contents of the **content** column to readable text.</span></span> <span data-ttu-id="ca871-194">다음 쿼리는 WHERE 절에 이름을 사용하여 결과 집합을 단일 행으로 제한함으로써 Point.cs 파일의 내용을 읽기 쉬운 텍스트로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-194">The following query converts the contents of the Point.cs file to readable text, using the name in the WHERE clause to restrict the result set to a single row.</span></span>  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 <span data-ttu-id="ca871-195">결과를 복사하여 텍스트 편집기에 붙여 넣으면 원래 내용에 있던 줄 바꿈과 공백이 그대로 유지되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-195">If you copy and paste the results in to a text editor, you will see that the line breaks and spaces that existed in the original have been preserved.</span></span>  
  
## <a name="managing-udts-and-assemblies"></a><span data-ttu-id="ca871-196">UDT 및 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="ca871-196">Managing UDTs and Assemblies</span></span>  
 <span data-ttu-id="ca871-197">UDT 구현을 계획할 때는 UDT 어셈블리 자체에 필요한 메서드와 별도의 어셈블리에 만들고 사용자 정의 함수 또는 저장 프로시저로 구현해야 할 메서드를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-197">When planning your implementation of UDTs, consider which methods are needed in the UDT assembly itself, and which methods should be created in separate assemblies and implemented as user-defined functions or stored procedures.</span></span> <span data-ttu-id="ca871-198">메서드를 별도의 어셈블리로 분리하면 테이블의 UDT 열에 저장되어 있을 수 있는 데이터에 영향을 주지 않고 코드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-198">Separating methods into separate assemblies allows you to update code without affecting data that may be stored in a UDT column in a table.</span></span> <span data-ttu-id="ca871-199">새 정의에서 변경되지 않은 형식의 이전 값과 서명을 읽을 수 있는 경우에만 UDT 열 및 기타 종속 개체를 삭제하지 않고 UDT 어셈블리를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-199">You can modify UDT assemblies without dropping UDT columns and other dependent objects only when the new definition can read the former values and the signature of the type does not change.</span></span>  
  
 <span data-ttu-id="ca871-200">변경될 수 있는 프로시저 코드를 UDT 구현에 필요한 코드와 분리하면 유지 관리가 훨씬 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-200">Separating procedural code that may change from the code required to implement the UDT greatly simplifies maintenance.</span></span> <span data-ttu-id="ca871-201">UDT 작동에 필요한 코드만 포함하고 UDT 정의를 가능한 한 단순하게 하면 코드 수정이나 버그 수정을 위해 UDT 자체를 데이터베이스에서 삭제해야 하는 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-201">Including only code that is necessary for the UDT to function, and keeping your UDT definitions as simple as possible, reduces the risk that the UDT itself may need to be dropped from the database for code revisions or bug fixes.</span></span>  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a><span data-ttu-id="ca871-202">Currency UDT 및 통화 변환 함수</span><span class="sxs-lookup"><span data-stu-id="ca871-202">The Currency UDT and Currency Conversion Function</span></span>  
 <span data-ttu-id="ca871-203">**AdventureWorks** 샘플 데이터베이스의 **CURRENCY** udt는 udt 및 관련 함수를 구성 하는 권장 방법의 유용한 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-203">The **Currency** UDT in the **AdventureWorks** sample database provides a useful example of the recommended way to structure a UDT and its associated functions.</span></span> <span data-ttu-id="ca871-204">**통화** UDT는 특정 문화권의 통화 시스템을 기준으로 money를 처리 하는 데 사용 되며 달러, 유로화 등의 다른 통화 유형을 저장할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-204">The **Currency** UDT is used for handling money based on the monetary system of a particular culture, and allows for storage of different currency types, such as dollars, euros, and so forth.</span></span> <span data-ttu-id="ca871-205">UDT 클래스는 culture 이름을 문자열로 표시하고 금액을 `decimal` 데이터 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-205">The UDT class exposes a culture name as a string, and an amount of money as a `decimal` data type.</span></span> <span data-ttu-id="ca871-206">필요한 모든 직렬화 메서드는 클래스를 정의하는 어셈블리에 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-206">All of the necessary serialization methods are contained within the assembly defining the class.</span></span> <span data-ttu-id="ca871-207">한 문화권에서 다른 문화권으로의 통화 변환을 구현 하는 함수는 **Convertcurrency**이라는 외부 함수로 구현 되며이 함수는 별도의 어셈블리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-207">The function that implements currency conversion from one culture to another is implemented as an external function named **ConvertCurrency**, and this function is located in a separate assembly.</span></span> <span data-ttu-id="ca871-208">**Convertcurrency** 함수는 **AdventureWorks** 데이터베이스의 테이블에서 변환 율을 검색 하 여 해당 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-208">The **ConvertCurrency** function does its work by retrieving the conversion rate from a table in the **AdventureWorks** database.</span></span> <span data-ttu-id="ca871-209">변환 비율의 소스를 변경 해야 하거나 기존 코드를 변경 해야 하는 경우에는 **Currency** UDT에 영향을 주지 않고 어셈블리를 쉽게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-209">If the source of the conversion rates should ever change, or if there should be any other changes to the existing code, the assembly can be easily modified without affecting the **Currency** UDT.</span></span>  
  
 <span data-ttu-id="ca871-210">CLR (공용 언어 런타임) 예제를 설치 하면 **Currency** UDT 및 **convertcurrency** 함수에 대 한 코드 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-210">The code listing for the **Currency** UDT and **ConvertCurrency** functions can be found by installing the common language runtime (CLR) samples.</span></span>  
  
### <a name="using-udts-across-databases"></a><span data-ttu-id="ca871-211">여러 데이터베이스에 UDT 사용</span><span class="sxs-lookup"><span data-stu-id="ca871-211">Using UDTs Across Databases</span></span>  
 <span data-ttu-id="ca871-212">UDT는 기본적으로 단일 데이터베이스로 범위가 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-212">UDTs are by definition scoped to a single database.</span></span> <span data-ttu-id="ca871-213">따라서 한 데이터베이스에 정의된 UDT를 다른 데이터베이스의 열 정의에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-213">Therefore, a UDT defined in one database cannot be used in a column definition in another database.</span></span> <span data-ttu-id="ca871-214">여러 데이터베이스에서 UDT를 사용하려면 각 데이터베이스의 동일한 어셈블리에서 CREATE ASSEMBLY 문과 CREATE TYPE 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-214">In order to use UDTs in multiple databases, you must execute the CREATE ASSEMBLY and CREATE TYPE statements in each database on identical assemblies.</span></span> <span data-ttu-id="ca871-215">어셈블리는 해당 이름, 강력한 이름, culture, 버전, 권한 집합 및 이진 내용이 같으면 동일한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-215">Assemblies are considered identical if they have the same name, strong name, culture, version, permission set, and binary contents.</span></span>  
  
 <span data-ttu-id="ca871-216">두 데이터베이스에 UDT가 등록되어 있고 액세스할 수 있는 경우 한 데이터베이스의 UDT 값을 다른 데이터베이스에서 사용할 수 있도록 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-216">Once the UDT is registered and accessible in both databases, you can convert a UDT value from one database for use in another.</span></span> <span data-ttu-id="ca871-217">다음 시나리오에서 여러 데이터베이스에 동일한 UDT를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-217">Identical UDTs can be used across databases in the following scenarios:</span></span>  
  
-   <span data-ttu-id="ca871-218">서로 다른 데이터베이스에 정의된 저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="ca871-218">Calling stored procedure defined in different databases.</span></span>  
  
-   <span data-ttu-id="ca871-219">서로 다른 데이터베이스에 정의된 여러 테이블 쿼리</span><span class="sxs-lookup"><span data-stu-id="ca871-219">Querying tables defined in different databases.</span></span>  
  
-   <span data-ttu-id="ca871-220">한 데이터베이스 테이블의 UDT 열에서 UDT 데이터를 선택하여 동일한 UDT 열이 있는 다른 한 데이터베이스에 삽입</span><span class="sxs-lookup"><span data-stu-id="ca871-220">Selecting UDT data from one database table UDT column and inserting it into a second database with an identical UDT column.</span></span>  
  
 <span data-ttu-id="ca871-221">이러한 시나리오에서는 필요한 변환이 서버에서 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-221">In these situations, any conversion required by the server occurs automatically.</span></span> <span data-ttu-id="ca871-222">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 함수나 CONVERT 함수를 사용하여 변환을 명시적으로 수행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-222">You are not able to perform the conversions explicitly using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions.</span></span>  
  
 <span data-ttu-id="ca871-223">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서 **tempdb** 시스템 데이터베이스에 작업 테이블을 만들 때는 udt 사용에 대 한 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-223">Note that you do not need to take any action for using UDTs when [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] creates work tables in the **tempdb** system database.</span></span> <span data-ttu-id="ca871-224">여기에는 커서, 테이블 변수 및 **tempdb**를 투명 하 게 사용 하는 udt를 포함 하는 사용자 정의 테이블 반환 함수를 처리 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-224">This includes the handling of cursors, table variables, and user-defined table-valued functions that include UDTs and that transparently make use of **tempdb**.</span></span> <span data-ttu-id="ca871-225">그러나 UDT 열을 정의 하는 **tempdb** 에 임시 테이블을 명시적으로 만드는 경우에는 사용자 데이터베이스와 동일한 방식으로 **tempdb** 에 udt를 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca871-225">However, if you explicitly create a temporary table in **tempdb** that defines a UDT column, then the UDT must be registered in **tempdb** the same way as for a user database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca871-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca871-226">See Also</span></span>  
 [<span data-ttu-id="ca871-227">CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="ca871-227">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
