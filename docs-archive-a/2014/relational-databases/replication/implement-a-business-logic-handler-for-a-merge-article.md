---
title: 병합 아티클에 대한 비즈니스 논리 처리기 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2996a8ca8471ef59d4781e21239a72262daa759
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646882"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a><span data-ttu-id="5b8d0-102">병합 아티클에 대한 비즈니스 논리 처리기 구현</span><span class="sxs-lookup"><span data-stu-id="5b8d0-102">Implement a Business Logic Handler for a Merge Article</span></span>
  <span data-ttu-id="5b8d0-103">이 항목에서는 복제 프로그래밍 또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 병합 아티클에 대한 비즈니스 논리 처리기를 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-103">This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using replication programming or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="5b8d0-104"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 네임스페이스는 병합 복제 동기화 프로세스 중에 발생하는 이벤트를 처리하는 복잡한 비즈니스 논리를 작성할 수 있게 해주는 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-104">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="5b8d0-105">비즈니스 논리 처리기의 메서드는 동기화 중에 복제되는 각 변경된 행에 대해 복제 프로세스에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-105">Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.</span></span>  
  
 <span data-ttu-id="5b8d0-106">비즈니스 논리 처리기 구현을 위한 일반적인 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-106">The general process for implementing a business logic handler is:</span></span>  
  
1.  <span data-ttu-id="5b8d0-107">비즈니스 논리 처리기 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-107">Create the business logic hander assembly.</span></span>  
  
2.  <span data-ttu-id="5b8d0-108">어셈블리를 배포자에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-108">Register the assembly at the Distributor.</span></span>  
  
3.  <span data-ttu-id="5b8d0-109">병합 에이전트가 실행되는 서버에 어셈블리를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-109">Deploy the assembly at the server on which the Merge Agent runs.</span></span> <span data-ttu-id="5b8d0-110">끌어오기 구독의 경우 에이전트가 구독자에서 실행되고 밀어넣기 구독의 경우에는 배포자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-110">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="5b8d0-111">웹 동기화를 사용할 경우 에이전트는 웹 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-111">When you are using Web synchronization, the agent runs on the Web server.</span></span>  
  
4.  <span data-ttu-id="5b8d0-112">비즈니스 논리 처리기를 사용하는 아티클을 만들거나 기존 아티클을 수정하여 비즈니스 논리 처리기를 사용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-112">Create an article that uses the business logic handler or modify an existing article to use the business logic handler.</span></span>  
  
 <span data-ttu-id="5b8d0-113">사용자가 지정하는 비즈니스 논리 처리기는 동기화되는 모든 행에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-113">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="5b8d0-114">네트워크 서비스 또는 다른 애플리케이션에 대한 호출과 복잡한 논리가 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-114">Complex logic and calls to other applications or network services can impact performance.</span></span> <span data-ttu-id="5b8d0-115">비즈니스 논리 처리기에 대한 자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](merge/execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-115">For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="5b8d0-116">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5b8d0-116">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5b8d0-117">**다음을 사용하여 병합 아티클에 대한 비즈니스 논리 처리기를 구현하려면**</span><span class="sxs-lookup"><span data-stu-id="5b8d0-117">**To implement a business logic handler for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="5b8d0-118">복제 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="5b8d0-118">Replication Programming</span></span>](#ReplProg)  
  
     [<span data-ttu-id="5b8d0-119">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-119">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-replication-programming"></a><a name="ReplProg"></a> <span data-ttu-id="5b8d0-120">복제 프로그래밍 사용</span><span class="sxs-lookup"><span data-stu-id="5b8d0-120">Using Replication Programming</span></span>  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a><span data-ttu-id="5b8d0-121">비즈니스 논리 처리기를 만들고 배포하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-121">To create and deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="5b8d0-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio에서 비즈니스 논리 처리기를 구현하는 코드를 포함하는 .NET 어셈블리에 대한 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-122">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="5b8d0-123">다음 네임스페이스에 대해 이 프로젝트에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-123">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="5b8d0-124">어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="5b8d0-124">Assembly Reference</span></span>|<span data-ttu-id="5b8d0-125">위치</span><span class="sxs-lookup"><span data-stu-id="5b8d0-125">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="5b8d0-126">COM(기본 설치)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-126">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="5b8d0-127">GAC(.NET Framework 구성 요소)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-127">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="5b8d0-128">GAC(.NET Framework 구성 요소)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-128">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="5b8d0-129"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 클래스를 덮어쓰는 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-129">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="5b8d0-130"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 속성을 구현하여 처리된 변경 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-130">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="5b8d0-131"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 클래스의 다음 메서드 중 하나 이상을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-131">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="5b8d0-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 동기화 중에 데이터 변경이 커밋되는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="5b8d0-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - DELETE 문이 업로드 또는 다운로드될 때 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - DELETE 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - INSERT 문이 업로드 또는 다운로드될 때 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - INSERT 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 게시자와 구독자에서 UPDATE 문이 충돌하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="5b8d0-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 게시자와 구독자에서 UPDATE 문이 DELETE 문과 충돌하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="5b8d0-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - UPDATE 문이 업로드 또는 다운로드될 때 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - UPDATE 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
6.  <span data-ttu-id="5b8d0-141">프로젝트를 빌드하여 비즈니스 논리 처리기 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-141">Build the project to create the business logic handler assembly.</span></span>  
  
7.  <span data-ttu-id="5b8d0-142">어셈블리를 병합 에이전트 실행 파일(replmerg.exe)이 있는 디렉터리(기본 설치의 경우 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM)에 배포하거나 .NET GAC(전역 어셈블리 캐시)에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-142">Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, or install it in the .NET global assembly cache (GAC).</span></span> <span data-ttu-id="5b8d0-143">병합 에이전트 이외의 다른 애플리케이션에서 어셈블리에 액세스해야 하는 경우 어셈블리를 GAC에만 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-143">You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly.</span></span> <span data-ttu-id="5b8d0-144">.NET Framework SDK에 제공되는 전역 어셈블리 캐시 도구(**Gacutil.exe** )를 사용하여 GAC에 어셈블리를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-144">The assembly can be installed into the GAC using the Global Assembly Cache tool (**Gacutil.exe)** provided in the .NET Framework SDK.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b8d0-145">비즈니스 논리 처리기는 병합 에이전트가 실행되는 모든 서버에 배포해야 합니다. 여기에는 웹 동기화를 사용할 때 replisapi.dll을 호스팅하는 IIS 서버도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-145">A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="5b8d0-146">비즈니스 논리 처리기를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-146">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="5b8d0-147">게시자에서 [sp_enumcustomresolvers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)를 실행하여 어셈블리가 이미 비즈니스 논리 처리기로 등록되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-147">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the assembly has not already been registered as a business logic handler.</span></span>  
  
2.  <span data-ttu-id="5b8d0-148">배포자에서 [sp_registercustomresolver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)를 실행 하 고,에 대 한 비즈니스 논리 처리기의 이름,에 대 한 값,에 **@article_resolver** `true` **@is_dotnet_assembly** 어셈블리 이름 **@dotnet_assembly_name** ,에 대해 재정의 하는 클래스의 정규화 된 이름을 지정 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-148">At the Distributor, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), specifying a friendly name for the business logic handler for **@article_resolver**, a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b8d0-149">어셈블리가 병합 에이전트 실행 파일과 동일한 디렉터리에 배포 되지 않은 경우 병합 에이전트를 동기적으로 시작 하는 응용 프로그램과 동일한 디렉터리 또는 GAC (전역 어셈블리 캐시)에서 어셈블리 이름을 사용 하 여 전체 경로를 지정 해야 **@dotnet_assembly_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-149">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span> <span data-ttu-id="5b8d0-150">웹 동기화를 사용하는 경우 웹 서버에서 어셈블리의 위치를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-150">When using Web synchronization, you must specify the location of assembly at the Web server.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="5b8d0-151">새 테이블 아티클에서 비즈니스 논리 처리기를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-151">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="5b8d0-152">**@article_resolver**에 비즈니스 논리 처리기의 이름을 지정하여 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행하여 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-152">Execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying the friendly name of the business logic handler for **@article_resolver**.</span></span> <span data-ttu-id="5b8d0-153">자세한 내용은 [아티클을 정의](publish/define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-153">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="5b8d0-154">기존 테이블 아티클에서 비즈니스 논리 처리기를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-154">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="5b8d0-155">[Sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)를 실행 하 고, **@publication** 에 **@article** **article_resolver** 값,에 **@property** 비즈니스 논리 처리기의 이름을 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-155">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.</span></span>  
  
###  <a name="examples-replication-programming"></a><a name="TsqlExample"></a> <span data-ttu-id="5b8d0-156">예(복제 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-156">Examples (Replication Programming)</span></span>  
 <span data-ttu-id="5b8d0-157">이 예에서는 감사 로그를 만드는 비즈니스 논리 처리기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-157">This example shows a business logic handler that creates an audit log.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="5b8d0-158">다음 예에서는 배포자에 비즈니스 논리 처리기 어셈블리를 등록하고 기존 병합 아티클을 변경하여 이 사용자 지정 비즈니스 논리를 사용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-158">The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.</span></span>  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../snippets/tsql/SQL15/replication/howto/tsql/registerblh_10.sql#sp_registerblh_10)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="5b8d0-159">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="5b8d0-159">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-create-a-business-logic-handler"></a><span data-ttu-id="5b8d0-160">비즈니스 논리 처리기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-160">To create a business logic handler</span></span>  
  
1.  <span data-ttu-id="5b8d0-161">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio에서 비즈니스 논리 처리기를 구현하는 코드를 포함하는 .NET 어셈블리에 대한 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="5b8d0-162">다음 네임스페이스에 대해 이 프로젝트에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-162">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="5b8d0-163">어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="5b8d0-163">Assembly Reference</span></span>|<span data-ttu-id="5b8d0-164">위치</span><span class="sxs-lookup"><span data-stu-id="5b8d0-164">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="5b8d0-165">COM(기본 설치)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-165">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="5b8d0-166">GAC(.NET Framework 구성 요소)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-166">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="5b8d0-167">GAC(.NET Framework 구성 요소)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-167">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="5b8d0-168"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 클래스를 덮어쓰는 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-168">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="5b8d0-169"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 속성을 구현하여 처리된 변경 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-169">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="5b8d0-170"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 클래스의 다음 메서드 중 하나 이상을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-170">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="5b8d0-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 동기화 중에 데이터 변경이 커밋되는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="5b8d0-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - DELETE 문이 업로드 또는 다운로드되는 동안 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - DELETE 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - INSERT 문이 업로드 또는 다운로드될 때 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - INSERT 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 게시자와 구독자에서 UPDATE 문이 충돌하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="5b8d0-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 게시자와 구독자에서 UPDATE 문이 DELETE 문과 충돌하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="5b8d0-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - UPDATE 문이 업로드 또는 다운로드될 때 오류가 발생하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="5b8d0-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - UPDATE 문이 업로드 또는 다운로드될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b8d0-180">사용자 지정 비즈니스 논리에 의해 명시적으로 처리되지 않은 모든 아티클 충돌은 아티클에 대한 기본 해결 프로그램에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-180">Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.</span></span>  
  
6.  <span data-ttu-id="5b8d0-181">프로젝트를 빌드하여 비즈니스 논리 처리기 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-181">Build the project to create the business logic handler assembly.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="5b8d0-182">비즈니스 논리 처리기를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-182">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="5b8d0-183"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-183">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="5b8d0-184"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-184">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="5b8d0-185">1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-185">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
3.  <span data-ttu-id="5b8d0-186"><xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> 를 호출하고 반환되는 <xref:System.Collections.ArrayList> 개체를 검사하여 어셈블리가 아직 비즈니스 논리 처리기로 등록되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-186">Call <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> and check the returned <xref:System.Collections.ArrayList> object to ensure that the assembly has not already been registered as a business logic handler.</span></span>  
  
4.  <span data-ttu-id="5b8d0-187"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> class.</span></span> <span data-ttu-id="5b8d0-188">다음 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-188">Specify the following properties:</span></span>  
  
    -   <span data-ttu-id="5b8d0-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> -.NET 어셈블리의 이름.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - the name of the .NET assembly.</span></span> <span data-ttu-id="5b8d0-190">어셈블리가 병합 에이전트 실행 파일과 같은 디렉터리, 병합 에이전트를 동기적으로 시작하는 애플리케이션과 같은 디렉터리, 또는 GAC에 배포되지 않은 경우 어셈블리 이름에 전체 경로를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-190">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name.</span></span> <span data-ttu-id="5b8d0-191">웹 동기화에서 비즈니스 논리 처리기를 사용하는 경우 어셈블리 이름에 전체 경로를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-191">You must include the full path with the assembly name when using a business logic handler with Web synchronization.</span></span>  
  
    -   <span data-ttu-id="5b8d0-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 을 덮어쓰고 비즈니스 논리 처리기를 구현하는 클래스의 정규화된 이름</span><span class="sxs-lookup"><span data-stu-id="5b8d0-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> and implements the business logic handler.</span></span>  
  
    -   <span data-ttu-id="5b8d0-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - 비즈니스 논리 처리기에 액세스할 때 사용하는 이름</span><span class="sxs-lookup"><span data-stu-id="5b8d0-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - a friendly name you use when you access the business logic handler.</span></span>  
  
    -   <span data-ttu-id="5b8d0-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - `true` 값</span><span class="sxs-lookup"><span data-stu-id="5b8d0-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - a value of `true`.</span></span>  
  
#### <a name="to-deploy-a-business-logic-handler"></a><span data-ttu-id="5b8d0-195">비즈니스 논리 처리기를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-195">To deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="5b8d0-196">병합 에이전트가 실행되는 서버에서 비즈니스 논리 처리기가 배포자에 등록될 때 지정된 파일 위치에 어셈블리를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-196">Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor.</span></span> <span data-ttu-id="5b8d0-197">끌어오기 구독의 경우 에이전트가 구독자에서 실행되고 밀어넣기 구독의 경우에는 배포자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-197">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="5b8d0-198">웹 동기화를 사용할 경우 에이전트는 웹 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-198">When you are using Web synchronization, the agent runs on the Web server.</span></span> <span data-ttu-id="5b8d0-199">비즈니스 논리 처리기가 등록될 때 어셈블리 이름에 전체 경로를 포함하지 않은 경우 병합 에이전트 실행 파일과 같은 디렉터리, 병합 에이전트를 동기적으로 시작하는 애플리케이션과 같은 디렉터리에 어셈블리를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-199">If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent.</span></span> <span data-ttu-id="5b8d0-200">동일한 어셈블리를 사용하는 애플리케이션이 여러 개인 경우 GAC에 어셈블리를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-200">You may install the assembly in the GAC if there are multiple applications that use the same assembly.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="5b8d0-201">새 테이블 아티클에서 비즈니스 논리 처리기를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-201">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="5b8d0-202"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-202">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="5b8d0-203"><xref:Microsoft.SqlServer.Replication.MergeArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span> <span data-ttu-id="5b8d0-204">다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-204">Set the following properties:</span></span>  
  
    -   <span data-ttu-id="5b8d0-205"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>에 대한 아티클의 이름</span><span class="sxs-lookup"><span data-stu-id="5b8d0-205">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="5b8d0-206"><xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>에 대한 게시의 이름</span><span class="sxs-lookup"><span data-stu-id="5b8d0-206">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="5b8d0-207"><xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>에 대한 게시 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="5b8d0-207">The name of the publication database for <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="5b8d0-208"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>에 대한 비즈니스 논리 처리기의 이름( <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-208">The friendly name of the business logic handler (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span>  
  
3.  <span data-ttu-id="5b8d0-209"><xref:Microsoft.SqlServer.Replication.Article.Create%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-209">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span> <span data-ttu-id="5b8d0-210">자세한 내용은 [아티클을 정의](publish/define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-210">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="5b8d0-211">기존 테이블 아티클에서 비즈니스 논리 처리기를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5b8d0-211">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="5b8d0-212"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-212">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="5b8d0-213"><xref:Microsoft.SqlServer.Replication.MergeArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-213">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="5b8d0-214"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>및 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-214">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="5b8d0-215"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-215">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="5b8d0-216"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-216">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="5b8d0-217">이 메서드가 `false`를 반환하는 경우 3단계에서 아티클 속성이 올바르게 정의되지 않았거나 아티클이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-217">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span> <span data-ttu-id="5b8d0-218">자세한 내용은 [View and Modify Article Properties](publish/view-and-modify-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-218">For more information, see [View and Modify Article Properties](publish/view-and-modify-article-properties.md).</span></span>  
  
6.  <span data-ttu-id="5b8d0-219"><xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>에 대한 비즈니스 논리 처리기의 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-219">Set the friendly name of the business logic handler for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span> <span data-ttu-id="5b8d0-220">이 이름은 비즈니스 논리 처리기를 등록할 때 지정된 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-220">This is the value of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> property specified when registering the business logic handler.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="5b8d0-221">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="5b8d0-221">Examples (RMO)</span></span>  
 <span data-ttu-id="5b8d0-222">다음 예는 구독자에서의 삽입, 업데이트, 삭제에 대한 정보를 기록하는 비즈니스 논리 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-222">This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="5b8d0-223">다음 예에서는 배포자에 비즈니스 논리 처리기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-223">This example registers a business logic handler at the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 <span data-ttu-id="5b8d0-224">다음 예에서는 비즈니스 논리 처리기를 사용하도록 기존 아티클을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d0-224">This example changes an existing article to use the business logic handler.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="5b8d0-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b8d0-225">See Also</span></span>  
 <span data-ttu-id="5b8d0-226">[병합 아티클에 대 한 사용자 지정 충돌 해결 프로그램 구현](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d0-226">[Implement a Custom Conflict Resolver for a Merge Article](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="5b8d0-227">[비즈니스 논리 처리기를 디버그 하 &#40;복제 프로그래밍&#41;](debug-a-business-logic-handler-replication-programming.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d0-227">[Debug a Business Logic Handler &#40;Replication Programming&#41;](debug-a-business-logic-handler-replication-programming.md) </span></span>  
 <span data-ttu-id="5b8d0-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d0-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="5b8d0-229">복제 관리 개체 개념</span><span class="sxs-lookup"><span data-stu-id="5b8d0-229">Replication Management Objects Concepts</span></span>](concepts/replication-management-objects-concepts.md)  
  
  
