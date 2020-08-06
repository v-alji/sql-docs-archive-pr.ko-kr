---
title: 어셈블리 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cb3818ed644eede3cf4f2c256a0dcb94ec58c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735351"
---
# <a name="implementing-assemblies"></a><span data-ttu-id="eaf84-102">어셈블리 구현</span><span class="sxs-lookup"><span data-stu-id="eaf84-102">Implementing Assemblies</span></span>
  <span data-ttu-id="eaf84-103">이 항목에서는 사용자가 데이터베이스에서 어셈블리를 구현하고 사용하는 데 도움이 되는 다음 영역에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-103">This topic provides information about the following areas to help you implement and work with assemblies in the database:</span></span>  
  
-   <span data-ttu-id="eaf84-104">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="eaf84-104">Creating assemblies</span></span>  
  
-   <span data-ttu-id="eaf84-105">어셈블리 수정</span><span class="sxs-lookup"><span data-stu-id="eaf84-105">Modifying assemblies</span></span>  
  
-   <span data-ttu-id="eaf84-106">어셈블리 삭제, 해제 및 설정</span><span class="sxs-lookup"><span data-stu-id="eaf84-106">Dropping, disabling, and enabling assemblies</span></span>  
  
-   <span data-ttu-id="eaf84-107">어셈블리 버전 관리</span><span class="sxs-lookup"><span data-stu-id="eaf84-107">Managing assembly versions</span></span>  
  
## <a name="creating-assemblies"></a><span data-ttu-id="eaf84-108">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="eaf84-108">Creating Assemblies</span></span>  
 <span data-ttu-id="eaf84-109">어셈블리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 문을 사용하여 만들고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 Assembly Assisted Editor를 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-109">Assemblies are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, or in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="eaf84-110">또한에 SQL Server 프로젝트를 배포 하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 해당 프로젝트에 대해 지정 된 데이터베이스에 어셈블리가 등록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-110">Additionally, deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="eaf84-111">자세한 내용은 [Deploying CLR Database Objects](deploying-clr-database-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf84-111">For more information, see [Deploying CLR Database Objects](deploying-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="eaf84-112">**Transact-SQL을 사용하여 어셈블리를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-112">**To create an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="eaf84-113">CREATE ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
 <span data-ttu-id="eaf84-114">**SQL Server Management Studio를 사용하여 어셈블리를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-114">**To create an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="eaf84-115">어셈블리 속성 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-115">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a><span data-ttu-id="eaf84-116">어셈블리 수정</span><span class="sxs-lookup"><span data-stu-id="eaf84-116">Modifying Assemblies</span></span>  
 <span data-ttu-id="eaf84-117">어셈블리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 문을 사용하여 수정하고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 Assembly Assisted Editor를 사용하여 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-117">Assemblies are modified in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement or in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="eaf84-118">다음을 수행할 때 어셈블리를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-118">You can modify an assembly when you want to do the following:</span></span>  
  
-   <span data-ttu-id="eaf84-119">새로운 버전의 어셈블리 바이너리를 업로드하여 어셈블리 구현을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-119">Change the implementation of the assembly by uploading a newer version of the binaries of the assembly.</span></span> <span data-ttu-id="eaf84-120">자세한 내용은이 항목의 뒷부분에 나오는 [어셈블리 버전 관리](#_managing) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf84-120">For more information, see [Managing Assembly Versions](#_managing) later in this topic.</span></span>  
  
-   <span data-ttu-id="eaf84-121">어셈블리의 권한 집합을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-121">Change the permission set of the assembly.</span></span> <span data-ttu-id="eaf84-122">자세한 내용은 [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf84-122">For more information, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
-   <span data-ttu-id="eaf84-123">어셈블리의 표시 여부를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-123">Change the visibility of the assembly.</span></span> <span data-ttu-id="eaf84-124">표시되는 어셈블리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 참조할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-124">Visible assemblies are available for referencing in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eaf84-125">표시되지 않는 어셈블리는 데이터베이스에 업로드했더라도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-125">Nonvisible assemblies are not available, even if they have been uploaded in the database.</span></span> <span data-ttu-id="eaf84-126">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 업로드된 어셈블리가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-126">By default, assemblies uploaded to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are visible.</span></span>  
  
-   <span data-ttu-id="eaf84-127">해당 어셈블리와 관련된 디버그 또는 원본 파일을 추가하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-127">Add or drop a debug or source file associated with the assembly.</span></span>  
  
 <span data-ttu-id="eaf84-128">**Transact-SQL을 사용하여 어셈블리를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-128">**To modify an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="eaf84-129">ALTER ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
 <span data-ttu-id="eaf84-130">**SQL Server Management Studio를 사용하여 어셈블리를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-130">**To modify an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="eaf84-131">어셈블리 속성 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-131">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a><span data-ttu-id="eaf84-132">어셈블리 삭제, 해제 및 설정</span><span class="sxs-lookup"><span data-stu-id="eaf84-132">Dropping, Disabling, and Enabling Assemblies</span></span>  
 <span data-ttu-id="eaf84-133">어셈블리는 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY 문이나 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-133">Assemblies are dropped by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY statement or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="eaf84-134">**Transact-SQL을 사용하여 어셈블리를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-134">**To drop an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="eaf84-135">DROP ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="eaf84-136">**SQL Server Management Studio를 사용하여 어셈블리를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-136">**To drop an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="eaf84-137">개체 삭제</span><span class="sxs-lookup"><span data-stu-id="eaf84-137">Delete Objects</span></span>](../../ssms/object/delete-objects.md)  
  
 <span data-ttu-id="eaf84-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 생성된 어셈블리는 모두 기본적으로 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-138">By default, all assemblies that are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are disabled from executing.</span></span> <span data-ttu-id="eaf84-139">**Sp_configure** 시스템 저장 프로시저의 **clr enabled** 옵션을 사용 하 여에 업로드 된 모든 어셈블리를 사용 하지 않도록 설정 하거나 실행할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="eaf84-139">You can use the **clr enabled** option of the **sp_configure** system stored procedure to disable or enable the execution of all assemblies that are uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eaf84-140">어셈블리 실행을 해제하면 CLR(공용 언어 런타임) 함수, 저장 프로시저, 트리거, 집계 및 사용자 정의 유형이 실행되지 않고 현재 실행 중인 경우 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-140">Disabling assembly execution prevents common language runtime (CLR) functions, stored procedures, triggers, aggregates, and user-defined types from executing, and stops those that are currently executing.</span></span> <span data-ttu-id="eaf84-141">어셈블리 실행을 해제하더라도 어셈블리를 만들거나, 변경하거나, 삭제하는 기능은 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-141">Disabling assembly execution does not disable the ability to create, alter, or drop assemblies.</span></span> <span data-ttu-id="eaf84-142">자세한 내용은 [clr 사용 서버 구성 옵션](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf84-142">For more information, see [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eaf84-143">**어셈블리 실행을 해제하거나 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-143">**To disable and enable assembly execution**</span></span>  
  
-   [<span data-ttu-id="eaf84-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a><span data-ttu-id="eaf84-145">어셈블리 버전 관리</span><span class="sxs-lookup"><span data-stu-id="eaf84-145">Managing Assembly Versions</span></span>  
 <span data-ttu-id="eaf84-146">어셈블리가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 업로드되면 데이터베이스 시스템 카탈로그에 저장되어 이 카탈로그에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-146">When an assembly is uploaded to an instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly is stored and managed within the database system catalogs.</span></span> <span data-ttu-id="eaf84-147">에서 어셈블리의 정의에 대 한 모든 변경 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터베이스 카탈로그에 저장 된 어셈블리로 전파 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-147">Any changes made to the definition of the assembly in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] should be propagated to the assembly that is stored in the database catalog.</span></span>  
  
 <span data-ttu-id="eaf84-148">어셈블리를 수정해야 할 경우 ALTER ASSEMBLY 문을 실행하여 데이터베이스의 어셈블리를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-148">When you have to modify an assembly, you must issue an ALTER ASSEMBLY statement to update the assembly in the database.</span></span> <span data-ttu-id="eaf84-149">이렇게 하면 어셈블리가 해당 구현을 보유하고 있는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 모듈의 최신 복사본으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-149">This will update the assembly to the latest copy of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] modules holding its implementation.</span></span>  
  
 <span data-ttu-id="eaf84-150">ALTER ASSEMBLY 문의 WITH UNCHECKED DATA 절은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 데이터베이스의 지속형 데이터가 종속되어 있는 어셈블리도 새로 고치도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-150">The WITH UNCHECKED DATA clause of the ALTER ASSEMBLY statement instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to refresh even those assemblies upon which persisted data in the database is dependent.</span></span> <span data-ttu-id="eaf84-151">특히 다음 중 하나가 존재하는 경우 WITH UNCHECKED DATA를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-151">Specifically, you must specify WITH UNCHECKED DATA if any of the following exist:</span></span>  
  
-   <span data-ttu-id="eaf84-152">어셈블리에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수나 메서드를 통해 직접 또는 간접적으로 메서드를 참조하는 지속형 계산 열</span><span class="sxs-lookup"><span data-stu-id="eaf84-152">Persisted computed columns that reference methods in the assembly, either directly, or indirectly, through [!INCLUDE[tsql](../../includes/tsql-md.md)] functions or methods.</span></span>  
  
-   <span data-ttu-id="eaf84-153">어셈블리에 종속된 CLR 사용자 정의 유형의 열 - 이 유형은 **UserDefined**(비**네이티브**) 직렬화 형식을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-153">Columns of a CLR user-defined type that depend on the assembly, and the type implements a **UserDefined** (non-**Native**) serialization format.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="eaf84-154">WITH UNCHECKED DATA를 지정하지 않으면 새 어셈블리 버전이 테이블, 인덱스 또는 다른 영구 사이트의 기존 데이터에 영향을 주는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 ALTER ASSEMBLY를 실행하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-154">If WITH UNCHECKED DATA is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to prevent ALTER ASSEMBLY from executing if the new assembly version affects existing data in tables, indexes, or other persistent sites.</span></span> <span data-ttu-id="eaf84-155">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 CLR 어셈블리를 업데이트할 때 계산 열, 인덱스, 인덱싱된 뷰 또는 식이 기본 루틴 및 유형과 일치하도록 보장하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-155">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not guarantee that computed columns, indexes, indexed views, or expressions will be consistent with the underlying routines and types when the CLR assembly is updated.</span></span> <span data-ttu-id="eaf84-156">ALTER ASSEMBLY를 실행할 때는 어셈블리에 저장된 이 식을 기반으로 하는 값과 식의 결과가 일치하는지 주의해서 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf84-156">Be careful when you execute ALTER ASSEMBLY to make sure that there is no mismatch between the result of an expression and a value that is based on that expression stored in the assembly.</span></span>  
  
 <span data-ttu-id="eaf84-157">**Db_owner** 및 **db_ddlowner** 고정 데이터베이스 역할의 멤버만 WITH UNCHECKED DATA 절을 사용 하 여 ALTER ASSEMBLY 실행을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-157">Only members of the **db_owner** and **db_ddlowner** fixed database role can execute run ALTER ASSEMBLY by using the WITH UNCHECKED DATA clause.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="eaf84-158">는 어셈블리가 테이블의 검사하지 않은 데이터로 수정되었다는 메시지를 Windows 애플리케이션 이벤트 로그에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-158">posts a message to the Windows application event log that the assembly has been modified with unchecked data in the tables.</span></span> <span data-ttu-id="eaf84-159">그러면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 해당 어셈블리에 종속된 데이터가 들어 있는 테이블에 검사하지 않은 데이터가 있다고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] then marks any tables that contain data dependent on the assembly as having unchecked data.</span></span> <span data-ttu-id="eaf84-160">**Sys. tables** 카탈로그 뷰의 **has_unchecked_assembly_data** 열에는 선택 되지 않은 데이터가 포함 된 테이블의 경우 값 1이 포함 되 고, 확인 되지 않은 데이터가 없는 테이블의 경우에는 0이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-160">The **has_unchecked_assembly_data** column of the **sys.tables** catalog view contains the value 1 for tables that contain unchecked data, and 0 for tables without unchecked data.</span></span>  
  
 <span data-ttu-id="eaf84-161">검사하지 않은 데이터의 무결성을 확인하려면 검사하지 않은 데이터가 있는 각 테이블에 대해 DBCC CHECKTABLE을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-161">To resolve the integrity of unchecked data, run DBCC CHECKTABLE against each table that has unchecked data.</span></span> <span data-ttu-id="eaf84-162">DBCC CHECKTABLE이 실패하면 잘못된 테이블 행을 삭제하거나 어셈블리 코드를 수정하여 문제를 해결한 다음 추가 ALTER ASSEMBLY 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-162">If DBCC CHECKTABLE fails, you must either delete the table rows that are not valid or modify the assembly code to address problems, and then issue additional ALTER ASSEMBLY statements.</span></span>  
  
 <span data-ttu-id="eaf84-163">ALTER ASSEMBLY는 어셈블리 버전을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-163">ALTER ASSEMBLY changes the assembly version.</span></span> <span data-ttu-id="eaf84-164">어셈블리의 문화권 및 공개 키 토큰은 동일 하 게 유지 됩니다. SQL Server는 동일한 이름, 문화권 및 공개 키를 사용 하 여 서로 다른 버전의 어셈블리를 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-164">The culture and public key token of the assembly remain the same.SQL Server does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a><span data-ttu-id="eaf84-165">버전 바인딩을 위해 컴퓨터 차원의 정책과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="eaf84-165">Interactions with Computer-wide Policy for Version Binding</span></span>  
 <span data-ttu-id="eaf84-166">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장되어 있는 어셈블리에 대한 참조가 게시자 정책 또는 컴퓨터 차원의 관리자 정책을 사용하여 특정 버전으로 리디렉션된 경우에는 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-166">If references to assemblies stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are redirected to specific versions by using publisher policy or computer-wide administrator policy, you must do either of the following:</span></span>  
  
-   <span data-ttu-id="eaf84-167">이렇게 리디렉션된 새 버전이 데이터베이스에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-167">Make sure the new version to which this redirection is made is in the database.</span></span>  
  
-   <span data-ttu-id="eaf84-168">컴퓨터 또는 게시자 정책의 외부 정책 파일로 문을 수정하여 이러한 파일이 데이터베이스에 있는 특정 버전을 참조하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-168">Modify any statements to the external policy files of the computer or publisher policy to make sure that they reference the specific version that is in the database.</span></span>  
  
 <span data-ttu-id="eaf84-169">그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 새 어셈블리 버전을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf84-169">Otherwise, an attempt to load a new assembly version to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will fail.</span></span>  
  
 <span data-ttu-id="eaf84-170">**어셈블리의 버전을 업데이트하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf84-170">**To update the version of an assembly**</span></span>  
  
-   [<span data-ttu-id="eaf84-171">ALTER ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf84-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="eaf84-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eaf84-172">See Also</span></span>  
 <span data-ttu-id="eaf84-173">[어셈블리 &#40;데이터베이스 엔진&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="eaf84-173">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="eaf84-174">어셈블리에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eaf84-174">Getting Information About Assemblies</span></span>](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
