---
title: 피어 투 피어 토폴로지 관리(복제 Transact-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a73af1c1f3a7196d87f77681ee9d62a3ef248a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648963"
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a><span data-ttu-id="ed0d7-102">피어 투 피어 토폴로지 관리(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="ed0d7-102">Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="ed0d7-103">피어 투 피어 토폴로지를 관리하는 것은 일반적인 트랜잭션 복제 토폴로지를 관리하는 것과 비슷하지만 특별히 고려해야 하는 영역도 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-103">Administering a peer-to-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations.</span></span> <span data-ttu-id="ed0d7-104">피어 투 피어 토폴로지 관리에서 주요한 차이점은 몇 가지 변경 작업의 경우 시스템을 *정지*해야 한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-104">The principal difference in administering a peer-to-peer topology is that some changes require the system to be *quiesced*.</span></span> <span data-ttu-id="ed0d7-105">시스템 정지 과정에서는 모든 노드에서 게시된 테이블에 대한 작업을 중지하고 각 노드가 다른 모든 노드의 변경 내용을 받았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-105">Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="ed0d7-106">자세한 내용은 [복제 토폴로지 정지&#40;복제 Transact-SQL 프로그래밍&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-106">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed0d7-107">피어 투 피어 토폴로지에서는 배포자가 끌어오기 구독자보다 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-107">In a peer-to-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] than a pull subscriber.</span></span>  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a><span data-ttu-id="ed0d7-108">기존 구성에 아티클을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ed0d7-108">To add an article to an existing configuration</span></span>  
  
1.  <span data-ttu-id="ed0d7-109">시스템을 정지합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-109">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="ed0d7-110">토폴로지의 각 노드에서 배포 에이전트를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-110">Stop the Distribution Agent at each node in the topology.</span></span> <span data-ttu-id="ed0d7-111">자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) 또는 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-111">For more information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="ed0d7-112">CREATE TABLE 문을 실행하여 토폴로지의 각 노드에 새 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-112">Execute the CREATE TABLE statement to add the new table at each node in the topology.</span></span>  
  
4.  <span data-ttu-id="ed0d7-113">[bcp 유틸리티](../../../tools/bcp-utility.md)를 사용하여 새 테이블의 데이터를 모든 노드에 수동으로 대량 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-113">Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../../tools/bcp-utility.md).</span></span>  
  
5.  <span data-ttu-id="ed0d7-114">[sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 을 실행하여 토폴로지의 각 노드에 새 아티클을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-114">Execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) to create the new article at each node in the topology.</span></span> <span data-ttu-id="ed0d7-115">자세한 내용은 [아티클을 정의](../publish/define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-115">For more information, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ed0d7-116">[sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 이 실행된 후에는 복제를 통해 토폴로지의 구독에 아티클이 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-116">After [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) is executed, replication automatically adds the article to the subscriptions in the topology.</span></span>  
  
6.  <span data-ttu-id="ed0d7-117">토폴로지의 각 노드에서 배포 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-117">Restart the Distribution Agents at each node in the topology.</span></span>  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a><span data-ttu-id="ed0d7-118">게시 데이터베이스의 스키마를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ed0d7-118">To make schema changes to a publication database</span></span>  
  
1.  <span data-ttu-id="ed0d7-119">시스템을 정지합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-119">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="ed0d7-120">DDL(데이터 정의 언어) 문을 실행하여 게시된 테이블의 스키마를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-120">Execute the data definition language (DDL) statements to modify the schema of published tables.</span></span> <span data-ttu-id="ed0d7-121">지원되는 스키마 변경에 대한 자세한 내용은 [게시 데이터베이스의 스키마 변경](../publish/make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-121">For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
3.  <span data-ttu-id="ed0d7-122">게시된 테이블에 대한 작업을 다시 시작하기 전에 시스템을 다시 정지합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-122">Before you resume activity on published tables, quiesce the system again.</span></span> <span data-ttu-id="ed0d7-123">이렇게 하면 새 데이터 변경 내용을 복제하기 전에 모든 노드에서 스키마 변경 내용을 받도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-123">This ensures that schema changes have been received by all nodes before any new data changes are replicated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0d7-124">예제</span><span class="sxs-lookup"><span data-stu-id="ed0d7-124">Example</span></span>  
 <span data-ttu-id="ed0d7-125">다음 예제에서는 두 개의 노드가 있는 기존 피어 투 피어 복제 토폴로지에 새 테이블 아티클을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed0d7-125">The following example demonstrates how to add a new table article to an existing peer-to-peer replication topology that has two nodes.</span></span>  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createtables)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_cmdline)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createarticle)]  
  
## <a name="see-also"></a><span data-ttu-id="ed0d7-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed0d7-126">See Also</span></span>  
 <span data-ttu-id="ed0d7-127">[복제 관리 FAQ](frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="ed0d7-127">[Replication Administration FAQ](frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="ed0d7-128">[SQL Server 데이터베이스 백업 및 복원](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ed0d7-128">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="ed0d7-129">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="ed0d7-129">Peer-to-Peer Transactional Replication</span></span>](../transactional/peer-to-peer-transactional-replication.md)  
  
  
