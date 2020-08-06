---
title: 병합 아티클용 사용자 지정 충돌 해결 프로그램 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e684213114f3c9bb2f1ad56de06fcfc89b819a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646880"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a><span data-ttu-id="904e7-102">병합 아티클용 사용자 지정 충돌 해결 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="904e7-102">Implement a Custom Conflict Resolver for a Merge Article</span></span>
  <span data-ttu-id="904e7-103">이 항목에서는 [또는 COM 기반 사용자 지정 해결 프로그램](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]을 사용하여[!INCLUDE[tsql](../../includes/tsql-md.md)] 의 병합 아티클을 위한 사용자 지정 충돌 해결 프로그램을 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-103">This topic describes how to implement custom conflict resolver for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or a [COM-based custom resolver](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
 <span data-ttu-id="904e7-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="904e7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="904e7-105">**다음을 사용하여 병합 아티클용 사용자 지정 충돌 해결 프로그램을 구현하려면**</span><span class="sxs-lookup"><span data-stu-id="904e7-105">**To implement custom conflict resolver for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="904e7-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="904e7-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="904e7-107">COM 기반 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="904e7-107">COM-based Resolver</span></span>](#COM)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="904e7-108">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="904e7-108">Using Transact-SQL</span></span>  
 <span data-ttu-id="904e7-109">각 게시자에서 사용자 지정 충돌 해결 프로그램을 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-109">You can write your own custom conflict resolver as a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure at each Publisher.</span></span> <span data-ttu-id="904e7-110">동기화하는 동안 해결 프로그램이 등록된 아티클에서 충돌이 발생하면 이 저장 프로시저가 호출되고 병합 에이전트가 충돌 행에 대한 정보를 프로시저의 필수 매개 변수에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-110">During synchronization, this stored procedure is invoked when conflicts are encountered in an article to which the resolver was registered, and information on the conflict row is passed by the Merge Agent to the required parameters of the procedure.</span></span> <span data-ttu-id="904e7-111">저장 프로시저 기반 사용자 지정 충돌 해결 프로그램은 항상 게시자에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-111">Stored procedure-based custom conflict resolvers are always created at the Publisher.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="904e7-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]저장 프로시저 해결 프로그램은 행 변경 기반 충돌을 처리 하기 위해서만 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure resolvers are only invoked to handle row change-based conflicts.</span></span> <span data-ttu-id="904e7-113">PRIMARY KEY 위반 또는 고유 인덱스 제약 조건 위반으로 인한 삽입 실패와 같은 다른 충돌 유형을 처리하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-113">They cannot be used to handle other types of conflicts such as insert failures due to PRIMARY KEY violations or unique index constraint violations.</span></span>  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a><span data-ttu-id="904e7-114">저장 프로시저 기반 사용자 지정 충돌 해결 프로그램을 만들려면</span><span class="sxs-lookup"><span data-stu-id="904e7-114">To create a stored procedure-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="904e7-115">게시 또는 **msdb** 데이터베이스에 있는 게시자에서 다음 필수 매개 변수를 구현하는 새 시스템 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-115">At the Publisher in either the publication or **msdb** database, create a new system stored procedure that implements the following required parameters:</span></span>  
  
    |<span data-ttu-id="904e7-116">매개 변수</span><span class="sxs-lookup"><span data-stu-id="904e7-116">Parameter</span></span>|<span data-ttu-id="904e7-117">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="904e7-117">Data type</span></span>|<span data-ttu-id="904e7-118">Description</span><span class="sxs-lookup"><span data-stu-id="904e7-118">Description</span></span>|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|<span data-ttu-id="904e7-119">충돌을 해결 중인 테이블의 소유자 이름.</span><span class="sxs-lookup"><span data-stu-id="904e7-119">Name of the owner of the table for which a conflict is being resolved.</span></span> <span data-ttu-id="904e7-120">게시 데이터베이스에 있는 테이블의 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-120">This is the owner for the table in the publication database.</span></span>|  
    |**@tablename**|`sysname`|<span data-ttu-id="904e7-121">충돌을 해결 중인 테이블의 이름</span><span class="sxs-lookup"><span data-stu-id="904e7-121">Name of the table for which a conflict is being resolved.</span></span>|  
    |**@rowguid**|`uniqueidentifier`|<span data-ttu-id="904e7-122">충돌이 있는 행의 고유 식별자</span><span class="sxs-lookup"><span data-stu-id="904e7-122">Unique identifier for the row having the conflict.</span></span>|  
    |**@subscriber**|`sysname`|<span data-ttu-id="904e7-123">충돌 변경 내용을 전파 중인 서버의 이름</span><span class="sxs-lookup"><span data-stu-id="904e7-123">Name of the server from where a conflicting change is being propagated.</span></span>|  
    |**@subscriber_db**|`sysname`|<span data-ttu-id="904e7-124">충돌 변경 내용을 전파 중인 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="904e7-124">Name of the database from where conflicting change is being propagated.</span></span>|  
    |<span data-ttu-id="904e7-125">**@log_conflict출력**</span><span class="sxs-lookup"><span data-stu-id="904e7-125">**@log_conflict OUTPUT**</span></span>|`int`|<span data-ttu-id="904e7-126">병합 프로세스에서 나중에 충돌을 해결할 수 있도록 충돌을 기록할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-126">Whether the merge process should log a conflict for later resolution:</span></span><br /><br /> <span data-ttu-id="904e7-127">**0** = 충돌을 기록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-127">**0** = Do not log the conflict.</span></span><br /><br /> <span data-ttu-id="904e7-128">**1** = 충돌 시 구독자의 변경 내용이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-128">**1** = Subscriber is the conflict loser.</span></span><br /><br /> <span data-ttu-id="904e7-129">**2** = 충돌 시 게시자의 변경 내용이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-129">**2** = Publisher is the conflict loser.</span></span>|  
    |<span data-ttu-id="904e7-130">**@conflict_message출력**</span><span class="sxs-lookup"><span data-stu-id="904e7-130">**@conflict_message OUTPUT**</span></span>|`nvarchar(512)`|<span data-ttu-id="904e7-131">충돌을 기록할 경우 해결 정보로 제공되는 메시지</span><span class="sxs-lookup"><span data-stu-id="904e7-131">Message to be given about the resolution if the conflict is logged.</span></span>|  
    |**@destowner**|`sysname`|<span data-ttu-id="904e7-132">구독자에 있는 게시된 테이블의 소유자</span><span class="sxs-lookup"><span data-stu-id="904e7-132">The owner of the published table at the Subscriber.</span></span>|  
  
     <span data-ttu-id="904e7-133">이 저장 프로시저는 병합 에이전트가 이 매개 변수에 전달한 값을 사용하여 사용자 지정 충돌 해결 논리를 구현합니다. 이 저장 프로시저는 기본 테이블과 구조가 같고 충돌 시 적용되는 행의 데이터 값을 포함하는 단일 행 결과 집합을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-133">This stored procedure uses the values passed by the Merge Agent to these parameters to implement your custom conflict resolution logic; it must return a single row result set that is identical in structure to the base table and contains the data values for the winning version of the row.</span></span>  
  
2.  <span data-ttu-id="904e7-134">게시자에 연결할 때 구독자가 사용하는 모든 로그인에 저장 프로시저에 대한 EXECUTE 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-134">Grant EXECUTE permissions on the stored procedure to any logins used by Subscribers to connect to the Publisher.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="904e7-135">새 테이블 아티클에 사용자 지정 충돌 해결 프로그램을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="904e7-135">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="904e7-136">\*\*\*\* 매개 변수에 **MicrosoftSQL@article_resolver** **Server Stored Procedure Resolver** 값, **@resolver_info** 매개 변수에 충돌 해결 프로그램 논리를 구현하는 저장 프로시저 이름을 지정하여 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행하고 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-136">Execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying a value of **MicrosoftSQL** **Server Stored Procedure Resolver** for the **@article_resolver** parameter and the name of the stored procedure that implements the conflict resolver logic for the **@resolver_info** parameter.</span></span> <span data-ttu-id="904e7-137">자세한 내용은 [아티클을 정의](publish/define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="904e7-137">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="904e7-138">기존 테이블 아티클에 사용자 지정 충돌 해결 프로그램을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="904e7-138">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="904e7-139">[Sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)를 실행 하 고,에 article_resolver 값을 지정 하 고,에 **@publication** **@article** **article_resolver** **@property** **MicrosoftSQL** **Server Stored ProcedureResolver** 값을 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-139">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and a value of **MicrosoftSQL** **Server Stored ProcedureResolver** for **@value**.</span></span>  
  
2.  <span data-ttu-id="904e7-140">[Sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)를 실행 하 고, **@publication** **@article** 에 **resolver_info** 값,에 **@property** 충돌 해결 프로그램 논리를 구현 하는 저장 프로시저의 이름을 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-140">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **resolver_info** for **@property**, and the name of the stored procedure that implements the conflict resolver logic for **@value**.</span></span>  
  
##  <a name="using-a-com-based-custom-resolver"></a><a name="COM"></a><span data-ttu-id="904e7-141">COM 기반 사용자 지정 해결 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="904e7-141">Using a COM-based Custom Resolver</span></span>  
 <span data-ttu-id="904e7-142"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 네임스페이스는 이벤트를 처리하고 병합 복제 동기화 프로세스 중에 발생하는 충돌을 해결하는 복잡한 비즈니스 논리를 작성할 수 있게 해주는 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-142">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events and resolve conflicts that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="904e7-143">자세한 내용은 [병합 아티클에 대한 비즈니스 논리 처리기 구현](implement-a-business-logic-handler-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="904e7-143">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span> <span data-ttu-id="904e7-144">네이티브 코드 기반 사용자 지정 비즈니스 논리를 직접 작성하여 충돌을 해결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-144">You can also write your own native code-based custom business logic to resolve conflicts.</span></span> <span data-ttu-id="904e7-145">이 논리는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++와 같은 제품을 사용하여 COM 구성 요소로 빌드되며 DLL(동적 연결 라이브러리)로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-145">This logic is built as a COM component and compiled into dynamic-link libraries (DLL), using products such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++.</span></span> <span data-ttu-id="904e7-146">이러한 COM 기반 사용자 지정 충돌 해결 프로그램은 충돌 해결을 위해 특별히 설계 된 **ICustomResolver** 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-146">Such a COM-based custom conflict resolver must implement the **ICustomResolver** interface, which is designed specifically for conflict resolution.</span></span>  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a><span data-ttu-id="904e7-147">COM 기반 사용자 지정 충돌 해결 프로그램을 만들고 등록하려면</span><span class="sxs-lookup"><span data-stu-id="904e7-147">To create and register a COM-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="904e7-148">COM 호환 제작 환경에서 사용자 지정 충돌 해결 프로그램 라이브러리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-148">In a COM-compatible authoring environment, add references to the Custom Conflict Resolver library.</span></span>  
  
2.  <span data-ttu-id="904e7-149">Visual C++ 프로젝트의 경우 #import 지시어를 사용하여 이 라이브러리를 프로젝트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-149">For a Visual C++ project, use the #import directive to import this library into your project.</span></span>  
  
3.  <span data-ttu-id="904e7-150">**ICustomResolver** 인터페이스를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-150">Create a class that implements the **ICustomResolver** interface.</span></span>  
  
4.  <span data-ttu-id="904e7-151">특정 메서드와 속성을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-151">Implement certain methods and properties.</span></span>  
  
5.  <span data-ttu-id="904e7-152">프로젝트를 빌드하여 사용자 지정 충돌 해결 프로그램 라이브러리 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-152">Build the project to create the custom conflict resolver library file.</span></span>  
  
6.  <span data-ttu-id="904e7-153">병합 에이전트 실행 파일이 포함된 디렉터리에 라이브러리를 배포합니다(일반적으로 \Microsoft SQL Server\100\COM).</span><span class="sxs-lookup"><span data-stu-id="904e7-153">Deploy the library in the directory containing the merge agent executable (usually \Microsoft SQL Server\100\COM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="904e7-154">사용자 지정 충돌 해결 프로그램은 끌어오기 구독의 경우 구독자에, 밀어넣기 구독의 경우 배포자에, 또는 웹 동기화에 사용되는 웹 서버에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-154">A custom conflict resolver must be deployed at the Subscriber for a pull subscription, at the Distributor for a push subscription, or at the Web server used with Web synchronization.</span></span>  
  
7.  <span data-ttu-id="904e7-155">배포 디렉터리에서 regsvr32.exe를 사용하여 다음과 같이 사용자 지정 충돌 해결 프로그램 라이브러리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-155">Register the custom conflict resolver library using regsvr32.exe from the deployment directory as follows:</span></span>  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  <span data-ttu-id="904e7-156">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하여 라이브러리가 이미 사용자 지정 충돌 해결 프로그램으로 등록되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-156">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the library is not already registered as a custom conflict resolver.</span></span>  
  
9. <span data-ttu-id="904e7-157">라이브러리를 사용자 지정 충돌 해결 프로그램으로 등록하려면 배포자에서 [sp_registercustomresolver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-157">To register the library as a custom conflict resolver, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), at the Distributor.</span></span> <span data-ttu-id="904e7-158">에 대 한 COM 개체의 이름 **@article_resolver** ,의 라이브러리 ID (CLSID) **@resolver_clsid** 및에 값을 지정 `false` **@is_dotnet_assembly** 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-158">Specify the friendly name of the COM object for **@article_resolver**, the library's ID (CLSID) for **@resolver_clsid**, and a value of `false` for **@is_dotnet_assembly**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="904e7-159">사용자 지정 충돌 해결 프로그램이 더 이상 필요하지 않으면 [sp_unregistercustomresolver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql)를 사용하여 등록을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-159">When no longer needed, a custom conflict resolver can be unregistered using [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql).</span></span>  
  
10. <span data-ttu-id="904e7-160">필요에 따라 클러스터에서 5-8 단계를 반복하여 클러스터의 모든 노드에 사용자 지정 해결 프로그램을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-160">(Optional) On a cluster, repeat steps 5-8 to register the custom resolver on all nodes of the cluster.</span></span> <span data-ttu-id="904e7-161">장애 조치 이후에 사용자 지정 해결 프로그램에서 조정자를 올바르게 로드하려면 이 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-161">This is required to ensure that the custom resolver will be able to properly load the reconciler following a failover.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="904e7-162">새 테이블 아티클에 사용자 지정 충돌 해결 프로그램을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="904e7-162">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="904e7-163">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하고 원하는 해결 프로그램의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-163">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="904e7-164">게시 데이터베이스의 게시자에서 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행하여 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-164">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article.</span></span> <span data-ttu-id="904e7-165">에 1 단계의 아티클 해결 프로그램 이름을 지정 **@article_resolver** 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-165">Specify the friendly name of the article resolver from step 1 for **@article_resolver**.</span></span> <span data-ttu-id="904e7-166">자세한 내용은 [아티클을 정의](publish/define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="904e7-166">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="904e7-167">기존 테이블 아티클에 사용자 지정 충돌 해결 프로그램을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="904e7-167">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="904e7-168">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하고 원하는 해결 프로그램의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-168">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="904e7-169">[Sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)를 실행 하 고 **@publication** ,에 **@article** **article_resolver** 값,에 **@property** 1 단계에서 가져온 아티클 해결 프로그램의 이름을 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-169">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the article resolver from step 1 for **@value**.</span></span>  
  
#### <a name="viewing-a-sample-custom-resolver"></a><span data-ttu-id="904e7-170">예제 사용자 지정 해결 프로그램 보기</span><span class="sxs-lookup"><span data-stu-id="904e7-170">Viewing a Sample Custom Resolver</span></span>  
  
1.  <span data-ttu-id="904e7-171">예제는 SQL Server 2000 예제 파일에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-171">A sample is available in the SQL Server 2000 sample files.</span></span> <span data-ttu-id="904e7-172">[**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip)를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-172">Download the [**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip).</span></span> <span data-ttu-id="904e7-173">이렇게 하면 3 개의 파일이 6.9 MB로 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-173">This downloads 3 files amounting to 6.9 MB.</span></span>  
  
2.  <span data-ttu-id="904e7-174">다운로드한 압축 .cab 파일에서 파일의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-174">Extract the files from downloaded compressed .cab file.</span></span>  
  
3.  <span data-ttu-id="904e7-175">**setup.exe** 실행</span><span class="sxs-lookup"><span data-stu-id="904e7-175">Run **setup.exe**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="904e7-176">설치 옵션을 선택할 때 **복제** 예제만 설치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-176">When choosing the installation options, it is only necessary to install the **Replication** samples.</span></span> <span data-ttu-id="904e7-177">기본 설치 경로는 \*\*C:\Program files (x86) \Microsoft SQL Server 2000 Samples\1033 \\ \*\*)입니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-177">(The default installation path is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\\**)</span></span>  
  
4.  <span data-ttu-id="904e7-178">설치 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-178">Go to installation folder.</span></span> <span data-ttu-id="904e7-179">기본 폴더는 **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**입니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-179">(The default folder is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span></span>  
  
5.  <span data-ttu-id="904e7-180">**unzip_sqlreplSP3.exe** 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-180">Run the **unzip_sqlreplSP3.exe** program.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="904e7-181">샘플 컴퓨터 해결 프로그램은 (기본적으로) **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** 폴더에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-181">The sample com resolver will install (by default) to the **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** folder.</span></span>  
  
6.  <span data-ttu-id="904e7-182">**subspres** 폴더에서 모든 원본 파일에 발생한 **#include sqlres.h** 를 찾고 **#import "replrec.dll" no_namespace, raw_interfaces_only**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="904e7-182">In the **subspres** folder, find all occurrences of **#include sqlres.h** in all of the source files and replace them with **#import "replrec.dll" no_namespace, raw_interfaces_only**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904e7-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="904e7-183">See Also</span></span>  
 <span data-ttu-id="904e7-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="904e7-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 <span data-ttu-id="904e7-185">[COM 기반 사용자 지정 해결 프로그램](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span><span class="sxs-lookup"><span data-stu-id="904e7-185">[COM-Based Custom Resolvers](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span></span>  
 [<span data-ttu-id="904e7-186">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="904e7-186">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
