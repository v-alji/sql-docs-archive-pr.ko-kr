---
title: 고유하게 컴파일된 저장 프로시저 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648385"
---
# <a name="creating-natively-compiled-stored-procedures"></a><span data-ttu-id="b9af6-102">고유하게 컴파일된 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="b9af6-102">Creating Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="b9af6-103">고유하게 컴파일된 저장 프로시저는 전체 [!INCLUDE[tsql](../../includes/tsql-md.md)] 프로그래밍 기능 및 쿼리 노출 영역을 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-103">Natively compiled stored procedures do not implement the full [!INCLUDE[tsql](../../includes/tsql-md.md)] programmability and query surface area.</span></span> <span data-ttu-id="b9af6-104">일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 고유하게 컴파일된 저장 프로시저 내에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-104">There are certain [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs that cannot be used inside natively compiled stored procedures.</span></span> <span data-ttu-id="b9af6-105">자세한 내용은 고유 하 게 [컴파일된 저장 프로시저에서 지원 되는 구문](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9af6-105">For more information, see [Supported Constructs in Natively Compiled Stored Procedures](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).</span></span>  
  
 <span data-ttu-id="b9af6-106">하지만 몇 가지 [!INCLUDE[tsql](../../includes/tsql-md.md)] 기능은 고유하게 컴파일된 저장 프로시저에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-106">There are, however, several [!INCLUDE[tsql](../../includes/tsql-md.md)] features that are only supported for natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="b9af6-107">ATOMIC 블록</span><span class="sxs-lookup"><span data-stu-id="b9af6-107">Atomic blocks.</span></span> <span data-ttu-id="b9af6-108">자세한 내용은 [Atomic Blocks](atomic-blocks-in-native-procedures.md)을(를) 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9af6-108">For more information, see [Atomic Blocks](atomic-blocks-in-native-procedures.md).</span></span>  
  
-   <span data-ttu-id="b9af6-109">고유하게 컴파일된 저장 프로시저에서 매개 변수와 변수에 대한 `NOT NULL` 제약 조건.</span><span class="sxs-lookup"><span data-stu-id="b9af6-109">`NOT NULL` constraints on parameters of and variables in natively compiled stored procedures.</span></span> <span data-ttu-id="b9af6-110">`NULL` 값을 `NOT NULL`로 선언된 매개 변수 또는 변수에 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-110">You cannot assign `NULL` values to parameters or variables declared as `NOT NULL`.</span></span> <span data-ttu-id="b9af6-111">자세한 내용은 [DECLARE @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9af6-111">For more information, see [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).</span></span>  
  
-   <span data-ttu-id="b9af6-112">고유하게 컴파일된 저장 프로시저의 스키마 바인딩</span><span class="sxs-lookup"><span data-stu-id="b9af6-112">Schema binding of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="b9af6-113">고유하게 컴파일된 저장 프로시저는 [CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)를 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-113">Natively compiled stored procedures are created using [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span> <span data-ttu-id="b9af6-114">다음 예에서는 메모리 최적화 테이블과 해당 테이블에 행을 삽입하는 데 사용되는 고유하게 컴파일된 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-114">The following example shows a memory-optimized table and a natively compiled stored procedure used for inserting rows into the table.</span></span>  
  
```sql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 <span data-ttu-id="b9af6-115">코드 샘플에서 `NATIVE_COMPILATION`은 이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저가 고유하게 컴파일된 저장 프로시저임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-115">In the code sample, `NATIVE_COMPILATION` indicates that this [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure is a natively compiled stored procedure.</span></span> <span data-ttu-id="b9af6-116">다음 옵션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-116">The following options are required:</span></span>  
  
|<span data-ttu-id="b9af6-117">옵션</span><span class="sxs-lookup"><span data-stu-id="b9af6-117">Option</span></span>|<span data-ttu-id="b9af6-118">Description</span><span class="sxs-lookup"><span data-stu-id="b9af6-118">Description</span></span>|  
|------------|-----------------|  
|`SCHEMABINDING`|<span data-ttu-id="b9af6-119">고유하게 컴파일된 저장 프로시저는 참조하는 개체의 스키마에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-119">Natively compiled stored procedures must be bound to the schema of the objects it references.</span></span> <span data-ttu-id="b9af6-120">이는 프로시저에서 참조하는 테이블을 삭제할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-120">This means that table references by the procedure cannot be dropped.</span></span> <span data-ttu-id="b9af6-121">프로시저에서 참조 되는 테이블은 해당 스키마 이름을 포함 해야 하며 쿼리에 와일드 카드 ( \* )를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-121">Tables referenced in the procedure must include their schema name, and wildcards (\*) are not allowed in queries.</span></span> <span data-ttu-id="b9af6-122">`SCHEMABINDING`은 이 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 고유하게 컴파일된 저장 프로시저에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-122">`SCHEMABINDING` is only supported for natively compiled stored procedures in this version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|`EXECUTE AS`|<span data-ttu-id="b9af6-123">고유하게 컴파일된 저장 프로시저는 기본 실행 컨텍스트인 `EXECUTE AS CALLER`를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-123">Natively compiled stored procedures do not support `EXECUTE AS CALLER`, which is the default execution context.</span></span> <span data-ttu-id="b9af6-124">따라서 실행 컨텍스트를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-124">Therefore, specifying the execution context is required.</span></span> <span data-ttu-id="b9af6-125">`EXECUTE AS OWNER` `EXECUTE AS` *사용자*및 옵션이 `EXECUTE AS SELF` 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-125">The options `EXECUTE AS OWNER`, `EXECUTE AS`*user*, and `EXECUTE AS SELF` are supported.</span></span>|  
|`BEGIN ATOMIC`|<span data-ttu-id="b9af6-126">고유하게 컴파일된 저장 프로시저의 본문은 단 하나의 ATOMIC 블록으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-126">The natively compiled stored procedure body must consist of exactly one atomic block.</span></span> <span data-ttu-id="b9af6-127">ATOMIC 블록은 저장 프로시저의 원자성 실행을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-127">Atomic blocks guarantee atomic execution of the stored procedure.</span></span> <span data-ttu-id="b9af6-128">프로시저가 활성 트랜잭션의 컨텍스트 외부에서 호출되면 새 트랜잭션을 시작하며 ATOMIC 블록의 끝에서 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-128">If the procedure is invoked outside the context of an active transaction, it will start a new transaction, which commits at the end of the atomic block.</span></span> <span data-ttu-id="b9af6-129">고유하게 컴파일된 저장 프로시저의 ATOMIC 블록에는 다음과 같은 두 가지 필수 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-129">Atomic blocks in natively compiled stored procedures have two required options:</span></span><br /><br /> <span data-ttu-id="b9af6-130">`TRANSACTION ISOLATION LEVEL`.</span><span class="sxs-lookup"><span data-stu-id="b9af6-130">`TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="b9af6-131">지원 되는 격리 수준에 대 한 [트랜잭션 격리 수준](../../database-engine/transaction-isolation-levels.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9af6-131">See [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for supported isolation levels.</span></span><br /><br /> <span data-ttu-id="b9af6-132">`LANGUAGE`.</span><span class="sxs-lookup"><span data-stu-id="b9af6-132">`LANGUAGE`.</span></span> <span data-ttu-id="b9af6-133">저장 프로시저의 언어는 사용 가능한 언어 또는 언어 별칭 중 하나로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-133">The language for the stored procedure must be set to one of the available languages or language aliases.</span></span>|  
  
 <span data-ttu-id="b9af6-134">`EXECUTE AS` 및 Windows 로그인과 관련하여 `EXECUTE AS`를 통해 수행된 가장 때문에 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-134">Regarding `EXECUTE AS` and Windows logins, an error can occur because of the impersonation done through `EXECUTE AS`.</span></span> <span data-ttu-id="b9af6-135">사용자 계정이 Windows 인증을 사용하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 사용되는 서비스 계정과 Windows 로그인의 도메인 간에는 완전 신뢰 관계가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-135">If a user account uses Windows Authentication, there must be full trust between the service account used for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and the domain of the Windows login.</span></span> <span data-ttu-id="b9af6-136">완전 신뢰가 없는 경우 고유 하 게 컴파일된 저장 프로시저를 만들 때 다음과 같은 오류 메시지가 반환 됩니다. 메시지 15404, Windows NT 그룹/사용자 ' 사용자 이름 '에 대 한 정보를 가져올 수 없습니다. 오류 코드 0x5.</span><span class="sxs-lookup"><span data-stu-id="b9af6-136">If there is not full trust, the following error message is returned when creating a natively compiled stored procedure: Msg 15404, Could not obtain information about Windows NT group/user 'username', error code 0x5.</span></span>  
  
 <span data-ttu-id="b9af6-137">이 오류를 해결하려면 다음 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-137">To resolve this error, use one of the following:</span></span>  
  
-   <span data-ttu-id="b9af6-138">Windows 사용자와 동일한 도메인에 있는 계정을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-138">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="b9af6-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 네트워크 서비스 또는 로컬 시스템과 같은 시스템 계정을 사용하는 경우 해당 컴퓨터가 Windows 사용자가 포함된 도메인에서 트러스트되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-139">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows user.</span></span>  
  
-   <span data-ttu-id="b9af6-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-140">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="b9af6-141">고유하게 컴파일된 저장 프로시저를 만들 때 오류 15517이 나타날 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-141">You may also see error 15517 when creating a natively compiled stored procedure.</span></span> <span data-ttu-id="b9af6-142">자세한 내용은 [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9af6-142">For more information, see [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).</span></span>  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a><span data-ttu-id="b9af6-143">고유하게 컴파일된 저장 프로시저 업데이트</span><span class="sxs-lookup"><span data-stu-id="b9af6-143">Updating a Natively Compiled Stored Procedure</span></span>  
 <span data-ttu-id="b9af6-144">고유하게 컴파일된 저장 프로시저에 대한 변경 작업 수행은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-144">Performing alter operations on natively compiled stored procedures is not supported.</span></span> <span data-ttu-id="b9af6-145">고유하게 컴파일된 저장 프로시저를 수정하는 한 가지 방법은 저장 프로시저를 삭제하고 다시 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-145">One way to modify a natively compiled stored procedure is to drop and recreate the stored procedure:</span></span>  
  
1.  <span data-ttu-id="b9af6-146">저장 프로시저 사용 권한에 대한 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-146">Generate script for the permissions on the stored procedure.</span></span>  
  
2.  <span data-ttu-id="b9af6-147">선택적으로 저장 프로시저에 대한 스크립트를 생성하고 백업으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-147">Optional, generate script for the stored procedure and save as a backup.</span></span>  
  
3.  <span data-ttu-id="b9af6-148">저장 프로시저를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-148">Drop the stored procedure.</span></span>  
  
4.  <span data-ttu-id="b9af6-149">변경된 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-149">Create the altered stored procedure.</span></span>  
  
5.  <span data-ttu-id="b9af6-150">스크립팅된 사용 권한을 저장 프로시저에 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-150">Re-apply the scripted permissions to the stored procedure.</span></span>  
  
 <span data-ttu-id="b9af6-151">이 절차의 단점은 3단계 시작과 5단계 완료 사이에 오프라인 시간이 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-151">The disadvantage to this procedure is the application will be offline from the start of step 3 through the completion of step 5.</span></span> <span data-ttu-id="b9af6-152">이 작업은 몇 초 정도 걸릴 수 있으며 애플리케이션을 사용하는 클라이언트에 오류 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-152">This may take a few seconds and the client using the application may see error messages.</span></span>  
  
 <span data-ttu-id="b9af6-153">고유하게 컴파일된 저장 프로시저를 효과적으로 수정하는 다른 방법은 먼저 저장 프로시저의 새 버전을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-153">Another way to (effectively) modify a natively compiled stored procedure is to first create a new version of the stored procedure.</span></span> <span data-ttu-id="b9af6-154">여기서 고유하게 컴파일된 저장 프로시저에는 연결된 버전 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-154">Here, the natively compiled stored procedure has an associated version number.</span></span> <span data-ttu-id="b9af6-155">기존 버전을 SP_Vold라고 하고 새 버전을 SP_Vnew라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-155">We will call the old version SP_Vold and the new version SP_Vnew.</span></span>  
  
1.  <span data-ttu-id="b9af6-156">SP_Vold의 사용 권한에 대한 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-156">Generate script for the permissions on SP_Vold.</span></span>  
  
2.  <span data-ttu-id="b9af6-157">SP_Vnew를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-157">Create SP_Vnew.</span></span>  
  
3.  <span data-ttu-id="b9af6-158">SP_Vold의 사용 권한을 SP_Vnew에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-158">Apply the permissions of SP_Vold to SP_Vnew.</span></span>  
  
4.  <span data-ttu-id="b9af6-159">SP_Vnew를 가리키도록 SP_Vold에 대한 참조를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-159">Update references to SP_Vold to point to SP_Vnew.</span></span> <span data-ttu-id="b9af6-160">이 작업은 다음과 같은 다양한 방법으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-160">This can be accomplished in different of ways, for example:</span></span>  
  
     <span data-ttu-id="b9af6-161">래퍼(디스크 기반) 저장 프로시저를 사용하고 SP_Vnew를 가리키도록 해당 프로시저를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-161">Use a wrapper (disk-based) stored procedure, and alter that procedure to point to SP_Vnew.</span></span> <span data-ttu-id="b9af6-162">이 방법의 단점은 간접 참조가 성능에 미치는 영향입니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-162">The disadvantage of this approach is the performance impact of the indirection.</span></span>  
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  <span data-ttu-id="b9af6-163">선택적으로 SP_Vold를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-163">Optional, drop SP_Vold.</span></span>  
  
 <span data-ttu-id="b9af6-164">이 방법의 장점은 애플리케이션이 오프라인으로 전환되지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-164">The advantage of this approach is that the application does not go offline.</span></span> <span data-ttu-id="b9af6-165">하지만 참조를 유지하고 참조가 항상 최신 버전의 저장 프로시저를 가리키는지 확인하는 데 더 많은 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af6-165">However, more work is required to maintain the references and make sure they always point to the latest version of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9af6-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9af6-166">See Also</span></span>  
 [<span data-ttu-id="b9af6-167">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b9af6-167">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
