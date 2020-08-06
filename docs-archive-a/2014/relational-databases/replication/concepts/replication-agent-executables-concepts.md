---
title: 복제 에이전트 실행 파일 개념 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73f9fe0d1a98fa1afc813cd113dcced685b4f98a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741855"
---
# <a name="replication-agent-executables-concepts"></a><span data-ttu-id="ee8b2-102">복제 에이전트 실행 파일 개념</span><span class="sxs-lookup"><span data-stu-id="ee8b2-102">Replication Agent Executables Concepts</span></span>
  <span data-ttu-id="ee8b2-103">다음과 같은 방법으로 복제 에이전트를 프로그래밍 방식으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-103">Replication agents can be controlled programmatically in the following ways:</span></span>  
  
-   <span data-ttu-id="ee8b2-104"><xref:Microsoft.SqlServer.Replication> 네임스페이스의 관리되는 에이전트 프로그래밍 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-104">Using the managed agent programming interfaces in the <xref:Microsoft.SqlServer.Replication> Namespace.</span></span>  
  
-   <span data-ttu-id="ee8b2-105">제공된 매개 변수 집합을 사용하여 명령 프롬프트에서 에이전트 실행 파일을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-105">Invoking agent executable files from the command prompt with a supplied set of parameters.</span></span>  
  
 <span data-ttu-id="ee8b2-106">명령 프롬프트에서 복제 에이전트를 직접 호출하면 배치 파일의 명령줄 스크립팅을 통해 에이전트에 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-106">Directly invoking replication agents from the command prompt enables agents to be programmatically accessed from command-line scripting in batch files.</span></span> <span data-ttu-id="ee8b2-107">명령 프롬프트에서 호출된 에이전트는 에이전트를 호출하거나 배치 파일을 시작한 사용자의 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 보안 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-107">When an agent is invoked from the command prompt, it runs under the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows security account of the user that invoked the agent or started the batch file.</span></span>  
  
 <span data-ttu-id="ee8b2-108">실행 파일을 사용하면 다음과 같은 복제 에이전트 인스턴스를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-108">Instances of the following replication agents can be run using executable files.</span></span>  
  
-   [<span data-ttu-id="ee8b2-109">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="ee8b2-109">Replication Distribution Agent</span></span>](../agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="ee8b2-110">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="ee8b2-110">Replication Log Reader Agent</span></span>](../agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="ee8b2-111">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="ee8b2-111">Replication Merge Agent</span></span>](../agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="ee8b2-112">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="ee8b2-112">Replication Queue Reader Agent</span></span>](../agents/replication-queue-reader-agent.md)  
  
-   [<span data-ttu-id="ee8b2-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="ee8b2-113">Replication Snapshot Agent</span></span>](../agents/replication-snapshot-agent.md)  
  
 <span data-ttu-id="ee8b2-114">복제 에이전트를 호출할 때 성능 프로필을 사용하여 에이전트 실행 파일에 정의된 매개 변수 집합을 자동으로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-114">When invoking replication agents, you can use performance profiles to automatically pass a defined set of parameters to the agent executable.</span></span> <span data-ttu-id="ee8b2-115">자세한 내용은 [Replication Agent Profiles](../agents/replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-115">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ee8b2-116">예</span><span class="sxs-lookup"><span data-stu-id="ee8b2-116">Examples</span></span>  
 <span data-ttu-id="ee8b2-117">다음 예에서는 명령 프롬프트에서 복제 에이전트를 호출하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-117">The following examples show how to invoke replication agents from the command prompt.</span></span> <span data-ttu-id="ee8b2-118">RMO(복제 관리 개체)를 사용하여 복제 에이전트를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-118">Replication agents can also be invoked using Replication Management Objects (RMO).</span></span> <span data-ttu-id="ee8b2-119">자세한 내용은 [구독 동기화&#40;복제&#41;](../synchronize-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-119">For more information, see [Synchronize Subscriptions &#40;Replication&#41;](../synchronize-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee8b2-120">이 예에서는 가독성을 높이기 위해 줄 바꿈이 추가되었지만</span><span class="sxs-lookup"><span data-stu-id="ee8b2-120">Line breaks in these examples were added to improve readability.</span></span> <span data-ttu-id="ee8b2-121">배치 파일에서 명령은 단일 행으로 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-121">In a batch file, commands must be made in a single line.</span></span>  
  
### <a name="running-the-snapshot-agent"></a><span data-ttu-id="ee8b2-122">스냅샷 에이전트 실행</span><span class="sxs-lookup"><span data-stu-id="ee8b2-122">Running the Snapshot Agent</span></span>  
 <span data-ttu-id="ee8b2-123">이 예제 배치 파일은 명령 프롬프트에서 스냅샷 에이전트를 호출하여 **AdvWorksSalesOrdersMerge** 게시에 대한 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-123">This example batch file invokes the Snapshot Agent from the command prompt to generate a snapshot for the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a><span data-ttu-id="ee8b2-124">배포 에이전트 실행</span><span class="sxs-lookup"><span data-stu-id="ee8b2-124">Running the Distribution Agent</span></span>  
 <span data-ttu-id="ee8b2-125">이 예제 배치 파일은 명령 프롬프트에서 배포 에이전트를 호출하여 **AdvWorksProductTran** 게시의 변경 내용을 밀어넣기 구독자에게 계속 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-125">This example batch file invokes the Distribution Agent from the command prompt to continuously replicate changes from the **AdvWorksProductTran** publication to a push subscriber.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a><span data-ttu-id="ee8b2-126">병합 에이전트 실행</span><span class="sxs-lookup"><span data-stu-id="ee8b2-126">Running the Merge Agent</span></span>  
 <span data-ttu-id="ee8b2-127">이 예제 배치 파일은 명령 프롬프트에서 병합 에이전트를 호출하여 끌어오기 구독을 **AdvWorksSalesOrdersMerge** 게시에 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ee8b2-127">This example batch file invokes the Merge Agent from the command prompt to synchronize a pull subscription to the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
