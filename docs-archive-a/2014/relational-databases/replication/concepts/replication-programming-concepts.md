---
title: 복제 프로그래밍 개념 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- replication [SQL Server], planning
- programming [SQL Server replication], planning
- programming [SQL Server replication]
ms.assetid: 2cd846e7-5bf3-4144-8772-703c4f439a2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db4ab6196c138eaf21de08afc27731225df398e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650914"
---
# <a name="replication-programming-concepts"></a><span data-ttu-id="23a54-102">복제 프로그래밍 개념</span><span class="sxs-lookup"><span data-stu-id="23a54-102">Replication Programming Concepts</span></span>
  <span data-ttu-id="23a54-103">복제 기능을 사용하는 애플리케이션을 개발하려면 먼저 다음과 같은 일반적인 계획 단계를 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-103">Before developing an application that uses replication functionalities, you should follow the following general planning steps:</span></span>  
  
1.  <span data-ttu-id="23a54-104">복제 토폴로지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-104">Define your replication topology.</span></span>  
  
2.  <span data-ttu-id="23a54-105">애플리케이션 기능을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-105">Define application functionality.</span></span>  
  
3.  <span data-ttu-id="23a54-106">보안을 계획합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-106">Plan for security.</span></span>  
  
4.  <span data-ttu-id="23a54-107">개발 환경을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-107">Choose a development environment.</span></span>  
  
5.  <span data-ttu-id="23a54-108">적절한 복제 프로그래밍 인터페이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-108">Choose the appropriate replication programming interface.</span></span>  
  
 <span data-ttu-id="23a54-109">이 항목의 나머지 부분에서는 이러한 단계를 좀 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-109">The rest of this topic describes these steps in more detail.</span></span> <span data-ttu-id="23a54-110">이 항목에는 계획 프로세스에 대한 이해를 돕기 위해 예가 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-110">To help illustrate the planning process, an example has been included.</span></span>  
  
## <a name="defining-the-replication-topology"></a><span data-ttu-id="23a54-111">복제 토폴로지 정의</span><span class="sxs-lookup"><span data-stu-id="23a54-111">Defining the Replication Topology</span></span>  
 <span data-ttu-id="23a54-112">복제 프로그래밍의 첫 번째 단계는 애플리케이션의 복제 토폴로지를 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-112">The first step in programming replication is to define the replication topology for your application.</span></span> <span data-ttu-id="23a54-113">기존 구독자의 데이터에 액세스하는 클라이언트 애플리케이션과 같이 기존의 복제 토폴로지를 사용할 애플리케이션을 작성하는 경우에는 다음 단계로 진행하십시오.</span><span class="sxs-lookup"><span data-stu-id="23a54-113">If you are writing an application that will use an existing replication topology, such as a client application that accesses data at an existing subscriber, you should move onto the next step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23a54-114">경우에 따라서는 애플리케이션이 복제 토폴로지를 배포하는 용도로만 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-114">In some cases, deploying the replication topology will be the sole purpose of the application.</span></span>  
  
 <span data-ttu-id="23a54-115">복제 토폴로지 정의는 다음을 포함하여 여러 요인에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-115">The replication topology that you define depends on many factors, including the following:</span></span>  
  
-   <span data-ttu-id="23a54-116">복제된 데이터를 업데이트해야 하는지 여부 및 업데이트 수행자</span><span class="sxs-lookup"><span data-stu-id="23a54-116">Whether or not replicated data needs to be updated, and by whom.</span></span>  
  
-   <span data-ttu-id="23a54-117">일관성, 자율성 및 대기 시간 측면에서의 데이터 배포 요구 사항</span><span class="sxs-lookup"><span data-stu-id="23a54-117">Your data distribution needs regarding consistency, autonomy, and latency.</span></span>  
  
-   <span data-ttu-id="23a54-118">비즈니스 사용자, 기술 인프라, 네트워크와 보안, 데이터 특성 등을 포함한 복제 환경</span><span class="sxs-lookup"><span data-stu-id="23a54-118">The replication environment, including business users, technical infrastructure, network and security, and data characteristics.</span></span>  
  
-   <span data-ttu-id="23a54-119">복제 및 복제 옵션 유형</span><span class="sxs-lookup"><span data-stu-id="23a54-119">The types of replication and replication options.</span></span>  
  
-   <span data-ttu-id="23a54-120">복제 토폴로지 및 복제 토폴로지와 복제 유형의 관계</span><span class="sxs-lookup"><span data-stu-id="23a54-120">The replication topologies and how they align with the types of replication.</span></span>  
  
 <span data-ttu-id="23a54-121">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제를 처음 사용하는 경우 [복제 유형](../types-of-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23a54-121">If you are new to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication, see [Types of Replication](../types-of-replication.md).</span></span>  
  
## <a name="defining-application-functionality"></a><span data-ttu-id="23a54-122">애플리케이션 기능 정의</span><span class="sxs-lookup"><span data-stu-id="23a54-122">Defining Application Functionality</span></span>  
 <span data-ttu-id="23a54-123">복제 토폴로지를 정의한 후에는 애플리케이션이 제공할 기능을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-123">Once the replication topology has been defined, you should decide on the functionalities that your application will offer.</span></span> <span data-ttu-id="23a54-124">이러한 기능은 구독을 동기화하는 스크립트부터 복제를 구성하는 사용자 인터페이스가 포함된 애플리케이션에 이르기까지 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-124">These functionalities can range from a script that synchronizes a subscription to an application with a user interface to configure replication.</span></span> <span data-ttu-id="23a54-125">복제는 다음과 같은 일발적인 프로그래밍 태스크를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-125">Replication supports the following general programming tasks:</span></span>  
  
-   <span data-ttu-id="23a54-126">복제 설정</span><span class="sxs-lookup"><span data-stu-id="23a54-126">Setting up replication.</span></span>  
  
-   <span data-ttu-id="23a54-127">구독자 동기화</span><span class="sxs-lookup"><span data-stu-id="23a54-127">Synchronizing Subscribers.</span></span>  
  
-   <span data-ttu-id="23a54-128">복제 토폴로지 유지 관리</span><span class="sxs-lookup"><span data-stu-id="23a54-128">Maintaining a replication topology.</span></span>  
  
-   <span data-ttu-id="23a54-129">복제 토폴로지 모니터링</span><span class="sxs-lookup"><span data-stu-id="23a54-129">Monitoring a replication topology.</span></span>  
  
-   <span data-ttu-id="23a54-130">복제 문제 해결</span><span class="sxs-lookup"><span data-stu-id="23a54-130">Troubleshooting replication.</span></span>  
  
 <span data-ttu-id="23a54-131">복제 기능을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 제공하는 다른 기능과 결합하여 애플리케이션을 확장하는 방법도 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-131">It is also common extend your application by combining replication functionalities with other functionalities provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="23a54-132">다음 표에서는 복제 애플리케이션에 제공할 수 있는 몇 가지 확장 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-132">The following table highlights some extended functionalities that you might provide in your replication application.</span></span>  
  
|<span data-ttu-id="23a54-133">기능</span><span class="sxs-lookup"><span data-stu-id="23a54-133">Functionality</span></span>|<span data-ttu-id="23a54-134">예제</span><span class="sxs-lookup"><span data-stu-id="23a54-134">Example</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="23a54-135">SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects)를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="23a54-135">Server administration using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)</span></span>|<span data-ttu-id="23a54-136">관리자가 복제 토폴로지에 데이터베이스를 게시자로 연결하고 구성할 수 있는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-136">An application that enables an administrator to attach and configure a database as a Publisher in a replication topology.</span></span>|  
|<span data-ttu-id="23a54-137">ADO.NET을 사용하여 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="23a54-137">Data access using ADO.NET</span></span>|<span data-ttu-id="23a54-138">사용자가 오프라인 상태에서 프로그래밍 방식으로 로컬 구독자 데이터베이스의 복제된 판매 데이터에 액세스하고 데이터를 변경한 다음 단추를 클릭하여 다시 연결한 후 끌어오기 구독을 동기화할 수 있는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-138">An application that enables users to programmatically access and change replicated sales data in a local Subscriber database while offline and then connect and synchronize the pull subscription by clicking a button.</span></span>|  
  
## <a name="planning-for-security"></a><span data-ttu-id="23a54-139">보안 계획</span><span class="sxs-lookup"><span data-stu-id="23a54-139">Planning for Security</span></span>  
 <span data-ttu-id="23a54-140">보안은 모든 애플리케이션에서 중요하며 보안 계획은 코드 작성을 시작하기 전에 마쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-140">Security is important in any application, and planning for security should be completed before writing any code.</span></span> <span data-ttu-id="23a54-141">애플리케이션 보안은 데이터베이스 보안, 복제 보안 및 보안 코드 작성이라는 세 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-141">Application security can be divided into three main parts: securing the database, securing replication, and writing secure code.</span></span>  
  
 <span data-ttu-id="23a54-142">다음 항목에서는 보안에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-142">The following topics provide information on security:</span></span>  
  
-   [<span data-ttu-id="23a54-143">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="23a54-143">SQL Server Replication Security</span></span>](../security/view-and-modify-replication-security-settings.md)  
  
-   [<span data-ttu-id="23a54-144">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="23a54-144">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
## <a name="choosing-a-development-environment"></a><span data-ttu-id="23a54-145">개발 환경 선택</span><span class="sxs-lookup"><span data-stu-id="23a54-145">Choosing a Development Environment</span></span>  
 <span data-ttu-id="23a54-146">복제 애플리케이션을 개발할 때는 세 가지 기본적인 개발 환경을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-146">When developing a replication application, there are three basic development environments to consider.</span></span> <span data-ttu-id="23a54-147">각 개발 환경에서는 동일한 복제 기능에 액세스할 수 있지만, 몇 가지 예외도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-147">Each development environment has access to the same replication functionalities with some exceptions.</span></span> <span data-ttu-id="23a54-148">복제 애플리케이션은 다음과 같은 환경에서 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-148">Replication applications can be developed in each of the following environments.</span></span>  
  
-   <span data-ttu-id="23a54-149">**관리 코드**</span><span class="sxs-lookup"><span data-stu-id="23a54-149">**Managed code**</span></span>  
  
     <span data-ttu-id="23a54-150">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 프로그래밍과 .NET CLR(공용 언어 런타임)의 이점을 활용하는 개체 지향 개발 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-150">Object oriented development environment that leverages the benefits of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programming and the .NET common language runtime (CLR).</span></span> <span data-ttu-id="23a54-151">관리 코드는 .NET 개발 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 애플리케이션 모두에 대해 권장되는 프로그래밍 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-151">Managed code is the recommended programming environment for both .NET development and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications.</span></span> <span data-ttu-id="23a54-152">관리되는 복제 인터페이스를 사용하면 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 알지 못해도 개체 지향 방식으로 복제 관리 기능을 프로그래밍할 수 있으며 스크립트를 통해 사용할 수 없는 복제 에이전트를 실행할 때 몇 가지 콜백 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-152">Managed replication interfaces enable the programming of replication administration in an object-oriented manner without having to know [!INCLUDE[tsql](../../../includes/tsql-md.md)], and it also provides some callback functionalities when running replication agents that are not available from scripts.</span></span> <span data-ttu-id="23a54-153">관리 코드는 재사용 가능한 구성 요소와 사용자 인터페이스 애플리케이션을 개발하기 위한 최상의 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-153">Managed code is the best environment for developing reusable components and user interface applications.</span></span>  
  
-   <span data-ttu-id="23a54-154">**스크립팅**</span><span class="sxs-lookup"><span data-stu-id="23a54-154">**Scripting**</span></span>  
  
     <span data-ttu-id="23a54-155">일련의 명령을 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트의 복제 시스템 저장 프로시저로 실행하거나 배치 파일의 명령으로 실행하는 간단한 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-155">Simple applications that execute a series of commands as either replication system stored procedures in [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts or commands in batch files.</span></span> <span data-ttu-id="23a54-156">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 종속 프로세스 관리 공급자를 사용하여 관리되는 환경에서 스크립트를 실행할 수 있지만 콜백 기능을 제공하는 관리되는 복제 인터페이스를 사용하여 동일한 기능을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-156">While you can execute scripts in a managed environment using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in-process managed provider, the same functionality can obtained by using managed replication interfaces, which also provide callback functionalities.</span></span> <span data-ttu-id="23a54-157">스크립팅은 복제 서버 설치와 같이 콜백 기능이 필요하지 않고 몇 번만 실행할 태스크를 실행하는 데 가장 적합한 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-157">Scripting is the best environment for executing tasks that will run only a few times and where callback functionalities are not required, such as installing a replication server.</span></span>  
  
-   <span data-ttu-id="23a54-158">**네이티브 코드**</span><span class="sxs-lookup"><span data-stu-id="23a54-158">**Native code**</span></span>  
  
     <span data-ttu-id="23a54-159">CLR에서 코드를 관리하지 못하도록 시스템 또는 COM 개체에 대한 직접 액세스를 사용하는 개체 지향 개발 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-159">Object-oriented development environment that utilizes direct access to the system or COM objects such that code is not managed by the CLR.</span></span> <span data-ttu-id="23a54-160">네이티브 코드 복제 인터페이스는 더 이상 사용되지 않거나 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-160">Native code replication interfaces are deprecated or discontinued.</span></span> <span data-ttu-id="23a54-161">자세한 내용은 [SQL Server 복제에서 사용되지 않는 기능](../deprecated-features-in-sql-server-replication.md) 또는 [복제의 이전 버전과의 호환성](../replication-backward-compatibility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23a54-161">For more information, see [Deprecated Features in SQL Server Replication](../deprecated-features-in-sql-server-replication.md) or [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
## <a name="choose-the-appropriate-replication-programming-interface"></a><span data-ttu-id="23a54-162">적절한 복제 프로그래밍 인터페이스 선택</span><span class="sxs-lookup"><span data-stu-id="23a54-162">Choose the Appropriate Replication Programming Interface</span></span>  
 <span data-ttu-id="23a54-163">계획 프로세스의 마지막 단계는 선택한 개발 환경에서 원하는 복제 기능을 구현하는 적절한 복제 프로그래밍 인터페이스를 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-163">The final planning step is choosing the appropriate replication programming interface that implements the desired replication functionality for the chosen development environment.</span></span> <span data-ttu-id="23a54-164">다음 표에서는 사용할 수 있는 복제 프로그래밍 인터페이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-164">The following table shows the replication programming interfaces available.</span></span>  
  
|<span data-ttu-id="23a54-165">인터페이스</span><span class="sxs-lookup"><span data-stu-id="23a54-165">Interface</span></span>|<span data-ttu-id="23a54-166">Environment</span><span class="sxs-lookup"><span data-stu-id="23a54-166">Environment</span></span>|<span data-ttu-id="23a54-167">사용</span><span class="sxs-lookup"><span data-stu-id="23a54-167">Uses</span></span>|  
|---------------|-----------------|----------|  
|[<span data-ttu-id="23a54-168">복제 관리 개체 개념</span><span class="sxs-lookup"><span data-stu-id="23a54-168">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)|<span data-ttu-id="23a54-169">관리 코드</span><span class="sxs-lookup"><span data-stu-id="23a54-169">Managed code</span></span>|<span data-ttu-id="23a54-170">관리, 모니터링 및 동기화</span><span class="sxs-lookup"><span data-stu-id="23a54-170">Administration, monitoring, and synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication>|<span data-ttu-id="23a54-171">관리 코드</span><span class="sxs-lookup"><span data-stu-id="23a54-171">Managed code</span></span>|<span data-ttu-id="23a54-172">동기화</span><span class="sxs-lookup"><span data-stu-id="23a54-172">Synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|<span data-ttu-id="23a54-173">관리 코드</span><span class="sxs-lookup"><span data-stu-id="23a54-173">Managed code</span></span>|<span data-ttu-id="23a54-174">사용자 지정 논리를 병합 동기화 프로세스에 통합하기 위한 비즈니스 논리 처리기 생성</span><span class="sxs-lookup"><span data-stu-id="23a54-174">Creation of business logic handlers to integrate custom logic with the merge synchronization process.</span></span>|  
|[<span data-ttu-id="23a54-175">복제 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="23a54-175">Replication Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)|<span data-ttu-id="23a54-176">스크립팅</span><span class="sxs-lookup"><span data-stu-id="23a54-176">Scripting</span></span>|<span data-ttu-id="23a54-177">관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="23a54-177">Administration and monitoring.</span></span>|  
|[<span data-ttu-id="23a54-178">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="23a54-178">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)|<span data-ttu-id="23a54-179">스크립팅</span><span class="sxs-lookup"><span data-stu-id="23a54-179">Scripting</span></span>|<span data-ttu-id="23a54-180">동기화</span><span class="sxs-lookup"><span data-stu-id="23a54-180">Synchronization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="23a54-181">예제</span><span class="sxs-lookup"><span data-stu-id="23a54-181">Example</span></span>  
 <span data-ttu-id="23a54-182">[!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)]에서는 전 세계 200명의 영업 담당자에게 데이터를 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-182">At [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], data needs to be published for 200 sales representatives around the world.</span></span> <span data-ttu-id="23a54-183">영업 담당자들은 자주 이동하기 때문에 랩톱 컴퓨터나 PDA(개인용 정보 단말기)를 사용하여 고객 데이터를 변경하고 새 주문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-183">The sales representatives travel often and will need to use laptop computers or personal digital assistants (PDAs) to change customer data and add new orders.</span></span> <span data-ttu-id="23a54-184">변경 내용은 영업 담당자가 랩톱을 네트워크에 연결할 때 게시자에 동기화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-184">The changes will then need to be synchronized with the Publisher when the sales representative connects the laptop to the network.</span></span>  
  
 <span data-ttu-id="23a54-185">이 애플리케이션의 계획 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-185">For this application, the planning steps might look like the following:</span></span>  
  
1.  <span data-ttu-id="23a54-186">이 애플리케이션의 복제 토폴로지는 이미 있지만</span><span class="sxs-lookup"><span data-stu-id="23a54-186">The replication topology for this application already exists.</span></span> <span data-ttu-id="23a54-187">클라이언트에서 새 끌어오기 구독을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-187">However, a new pull subscription must be created at the client.</span></span> <span data-ttu-id="23a54-188">게시 작업에서는 매개 변수가 있는 필터를 사용하여 각 영업 담당자에게 고유한 데이터 집합을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-188">The publication should use parameterized filters to replicate a unique set of data to each sales representative.</span></span>  
  
2.  <span data-ttu-id="23a54-189">영업 애플리케이션에 필요한 일반적인 데이터 액세스 이외에 이 애플리케이션에서는 영업 사원이 단추를 클릭하여 필요할 때 끌어오기 구독을 동기화할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-189">In addition to the typical data access required for a sales application, this application should enable a salesperson to synchronize the pull subscription on demand by clicking a button.</span></span> <span data-ttu-id="23a54-190">이 애플리케이션은 영업 담당자가 설치하고 실행할 것이므로 클라이언트에서 구독을 구성하고 초기 스냅샷을 적용할 수 있는 기능도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-190">Since a sales representative will install and run the application, it also needs to be able to configure a subscription and apply the initial snapshot at the client.</span></span> <span data-ttu-id="23a54-191">필요한 경우 애플리케이션에서는 연결이 발견되면 구독을 자동으로 동기화할 수 있도록 Windows에서 제공하는 무선 연결 감지 인프라를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-191">Optionally, the application will use the infrastructure provided by Windows for sensing wireless connectivity to automatically synchronize the subscription when a connection is detected.</span></span>  
  
3.  <span data-ttu-id="23a54-192">게시자에 연결할 때 Windows 인증 및 VPN(가상 프라이빗 네트워크)을 사용하는 것을 포함하여 복제와 관련된 모든 보안 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-192">Follow all of the security guidelines for replication, including using Windows Authentication and a virtual private network (VPN) when connecting to the publisher.</span></span> <span data-ttu-id="23a54-193">웹 동기화를 구현하는 경우에는 SSL(Secure Sockets Layer) 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-193">If implementing Web synchronization, use a secure sockets layer (SSL) connection.</span></span> <span data-ttu-id="23a54-194">자세한 내용은 [Configure Web Synchronization](../configure-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23a54-194">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md).</span></span>  
  
4.  <span data-ttu-id="23a54-195">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]의 기능을 활용하려면 관리되는 코드 언어를 사용하여 애플리케이션을 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-195">In order to take advantage of the features of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], the application is developed using a managed code language.</span></span>  
  
5.  <span data-ttu-id="23a54-196">이러한 요구 사항을 고려했을 때 이 애플리케이션에 필요한 모든 복제 기능은 RMO(복제 관리 개체) 관리 인터페이스를 사용하여 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-196">Based on these requirements, the Replication Management Objects (RMO) managed interface can provide all of the needed replication functionality for this application.</span></span>  
  
 <span data-ttu-id="23a54-197">이 시나리오 예는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 포함된 예제 애플리케이션에서 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="23a54-197">This example scenario has been implemented in a sample application that ships with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
