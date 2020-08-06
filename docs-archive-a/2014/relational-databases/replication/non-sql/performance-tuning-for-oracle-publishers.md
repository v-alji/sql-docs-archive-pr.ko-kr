---
title: Oracle 게시자를 위한 성능 튜닝 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], performance tuning
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 83d660eee839d525fa0bdabf88a313da0ed44244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638653"
---
# <a name="performance-tuning-for-oracle-publishers"></a><span data-ttu-id="810aa-102">Oracle 게시자를 위한 성능 튜닝</span><span class="sxs-lookup"><span data-stu-id="810aa-102">Performance Tuning for Oracle Publishers</span></span>
  <span data-ttu-id="810aa-103">Oracle 게시 아키텍처는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 게시 아키텍처와 유사하므로 성능을 개선하기 위한 Oracle 복제 튜닝의 첫 단계는 [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md)의 일반 튜닝 권장 사항을 따르는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-103">The Oracle publishing architecture is similar to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publishing architecture; therefore the first step in tuning Oracle replication for performance requires following the general tuning recommendations found in [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md).</span></span>  
  
 <span data-ttu-id="810aa-104">또한 Oracle 게시자 성능과 관련된 다음 두 가지 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-104">In addition there are two options for Oracle Publishers that are performance related:</span></span>  
  
-   <span data-ttu-id="810aa-105">Oracle 또는 Oracle Gateway 중에서 적절한 게시 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="810aa-105">Specifying the appropriate publishing option: Oracle or Oracle Gateway.</span></span>  
  
-   <span data-ttu-id="810aa-106">적절한 간격으로 게시자의 변경 내용을 처리하도록 트랜잭션 세트 작업 구성</span><span class="sxs-lookup"><span data-stu-id="810aa-106">Configuring the transaction set job to process changes on the Publisher at an appropriate interval.</span></span>  
  
## <a name="specifying-the-appropriate-publishing-option"></a><span data-ttu-id="810aa-107">적절한 게시 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="810aa-107">Specifying the Appropriate Publishing Option</span></span>  
 <span data-ttu-id="810aa-108">Oracle Gateway 옵션은 Oracle Complete 옵션을 사용할 때보다 더 나은 성능을 제공하지만 여러 트랜잭션 게시에서 동일한 테이블을 게시할 때는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-108">The Oracle Gateway option provides improved performance over the Oracle Complete option; however, this option cannot be used to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="810aa-109">트랜잭션 게시의 경우 특정 테이블이 한 번만 나타날 수 있지만 스냅샷 게시의 경우에는 이러한 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-109">A table can appear in at most one transactional publication and any number of snapshot publications.</span></span> <span data-ttu-id="810aa-110">여러 트랜잭션 게시에서 동일한 테이블을 게시해야 할 경우에는 Oracle Complete 옵션을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="810aa-110">If you need to publish the same table in multiple transactional publications, choose the Oracle Complete option.</span></span> <span data-ttu-id="810aa-111">이 옵션은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에서 Oracle 게시자를 식별할 때 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-111">Specify this option when identifying the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="810aa-112">자세한 내용은 [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="810aa-112">For more information, see [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
## <a name="configuring-the-transaction-set-job"></a><span data-ttu-id="810aa-113">트랜잭션 세트 작업 구성</span><span class="sxs-lookup"><span data-stu-id="810aa-113">Configuring the Transaction Set Job</span></span>  
 <span data-ttu-id="810aa-114">게시된 Oracle 테이블에 대한 변경 내용은 트랜잭션 세트라는 그룹으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-114">Changes to published Oracle tables are processed in groups called transaction sets.</span></span> <span data-ttu-id="810aa-115">트랜잭션 일관성을 유지하려면 각 트랜잭션 세트를 배포 데이터베이스에 단일 트랜잭션으로 커밋해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-115">To ensure transactional consistency, each transaction set is committed as a single transaction at the distribution database.</span></span> <span data-ttu-id="810aa-116">트랜잭션 세트가 너무 클 경우 단일 트랜잭션으로는 효율적으로 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-116">If the transaction set becomes too large, it cannot be processed efficiently as a single transaction.</span></span>  
  
 <span data-ttu-id="810aa-117">기본적으로 트랜잭션 세트는 로그 판독기 에이전트에서만 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-117">By default, transaction sets are created only by the Log Reader Agent.</span></span> <span data-ttu-id="810aa-118">변경 작업이 많이 수행되는 기간 동안 로그 판독기 에이전트가 실행되지 않거나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에서 Oracle 게시자로 연결할 수 없는 경우 트랜잭션 세트가 관리할 수 없을 정도로 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-118">If, during periods of high change activity, the Log Reader Agent does not run or cannot connect from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher, transaction sets can become unmanageably large.</span></span> <span data-ttu-id="810aa-119">이러한 문제를 방지하려면 로그 판독기 에이전트가 실행되지 않거나 Oracle 게시자에 연결할 수 없는 경우에도 트랜잭션 세트를 정기적으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-119">To prevent this problem, ensure that transaction sets are created at regular intervals, even if the Log Reader Agent does not run or cannot connect to the Oracle Publisher.</span></span>  
  
 <span data-ttu-id="810aa-120">트랜잭션 세트는 로그 판독기 에이전트가 세트를 만들 때 사용하는 메커니즘과 동일한 메커니즘을 사용하는 Xactset 작업(복제 시 설치되는 Oracle 데이터베이스 작업)을 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-120">Transaction sets can be created with the Xactset job (an Oracle database job installed by replication), which uses the same mechanism that the Log Reader Agent does to create sets.</span></span> <span data-ttu-id="810aa-121">작업이 실행될 때마다 새 트랜잭션 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-121">Each time the job runs, a new transaction set is created.</span></span> <span data-ttu-id="810aa-122">다음에 로그 판독기 에이전트가 실행되면 해당 에이전트는 생성된 모든 세트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-122">The next time that the Log Reader Agent runs, the agent processes any sets that have been created.</span></span> <span data-ttu-id="810aa-123">기존의 트랜잭션 세트가 모두 처리된 다음에도 보류 중인 변경 내용이 남아 있는 경우 로그 판독기 에이전트에서 하나 이상의 트랜잭션 세트를 추가로 만들어서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="810aa-123">If there are still pending changes after all existing transaction sets have been processed, the Log Reader Agent creates and processes one or more additional transaction sets.</span></span>  
  
 <span data-ttu-id="810aa-124">트랜잭션 집합 작업을 구성하려면 [Oracle 게시자에 대한 트랜잭션 집합 작업 구성&#40;복제 Transact-SQL 프로그래밍&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="810aa-124">To configure the transaction set job, see [Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810aa-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="810aa-125">See Also</span></span>  
 <span data-ttu-id="810aa-126">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="810aa-126">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="810aa-127">Oracle 게시 개요</span><span class="sxs-lookup"><span data-stu-id="810aa-127">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
