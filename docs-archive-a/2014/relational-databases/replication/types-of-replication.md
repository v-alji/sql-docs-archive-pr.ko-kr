---
title: 복제 유형 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5576331004eca44bc32dbde8f430284f75e6eb70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733844"
---
# <a name="types-of-replication"></a><span data-ttu-id="9d404-102">복제 유형</span><span class="sxs-lookup"><span data-stu-id="9d404-102">Types of Replication</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9d404-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 분산 애플리케이션에서 사용할 수 있는 다음 유형의 복제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following types of replication for use in distributed applications:</span></span>  
  
-   <span data-ttu-id="9d404-104">트랜잭션 복제.</span><span class="sxs-lookup"><span data-stu-id="9d404-104">Transactional replication.</span></span> <span data-ttu-id="9d404-105">자세한 내용은 [트랜잭션 복제](transactional/transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d404-105">For more information, see [Transactional Replication](transactional/transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="9d404-106">병합 복제.</span><span class="sxs-lookup"><span data-stu-id="9d404-106">Merge replication.</span></span> <span data-ttu-id="9d404-107">병합 복제에 대한 자세한 내용은 [병합 복제](merge/merge-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d404-107">For more information, see [Merge Replication](merge/merge-replication.md).</span></span>  
  
-   <span data-ttu-id="9d404-108">스냅샷 복제.</span><span class="sxs-lookup"><span data-stu-id="9d404-108">Snapshot replication.</span></span> <span data-ttu-id="9d404-109">스냅샷 복제에 대한 자세한 내용은 [스냅샷 복제](snapshot-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d404-109">For more information, see [Snapshot Replication](snapshot-replication.md).</span></span>  
  
 <span data-ttu-id="9d404-110">애플리케이션에 대한 복제 유형 선택은 물리적 복제 환경, 복제할 데이터 형식 및 양, 데이터가 구독자에서 업데이트되는지 여부를 포함한 여러 요인에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-110">The type of replication you choose for an application depends on many factors, including the physical replication environment, the type and quantity of data to be replicated, and whether the data is updated at the Subscriber.</span></span> <span data-ttu-id="9d404-111">물리적 환경에는 복제와 관련된 컴퓨터 수 및 위치와 이러한 컴퓨터가 클라이언트(워크스테이션, 랩톱 또는 핸드헬드 디바이스)인지 또는 서버인지 여부가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-111">The physical environment includes the number and location of computers involved in replication and whether these computers are clients (workstations, laptops, or handheld devices) or servers.</span></span>  
  
 <span data-ttu-id="9d404-112">일반적으로 각 복제 유형은 게시자와 구독자 간에 게시된 개체의 초기 동기화로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-112">Each type of replication typically begins with an initial synchronization of the published objects between the Publisher and Subscribers.</span></span> <span data-ttu-id="9d404-113">이러한 초기 동기화는 게시에 의해 지정된 모든 개체 및 데이터의 복사본인 *스냅샷*이 있는 복제로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-113">This initial synchronization can be performed by replication with a *snapshot*, which is a copy of all of the objects and data specified by a publication.</span></span> <span data-ttu-id="9d404-114">스냅샷은 생성된 후 구독자로 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-114">After the snapshot is created, it is delivered to the Subscribers.</span></span> <span data-ttu-id="9d404-115">스냅샷 복제만 필요한 애플리케이션도 있고,</span><span class="sxs-lookup"><span data-stu-id="9d404-115">For some applications, snapshot replication is all that is required.</span></span> <span data-ttu-id="9d404-116">시간에 따라 증분 방식으로 후속 데이터 변경 내용을 구독자로 보내야 하는 애플리케이션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-116">For other types of applications, it is important that subsequent data changes flow to the Subscriber incrementally over time.</span></span> <span data-ttu-id="9d404-117">또한 일부 애플리케이션에서는 변경 내용을 구독자에서 게시자로 다시 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-117">Some applications also require that changes flow from the Subscriber back to the Publisher.</span></span> <span data-ttu-id="9d404-118">트랜잭션 복제 및 병합 복제는 이러한 유형의 애플리케이션에 대한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-118">Transactional replication and merge replication provide options for these types of applications.</span></span>  
  
 <span data-ttu-id="9d404-119">스냅샷 복제에 대한 데이터 변경 내용은 추적되지 않으며 스냅샷이 적용될 때마다 이 스냅샷은 기존 데이터를 완전히 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-119">Data changes are not tracked for snapshot replication; each time a snapshot is applied, it completely overwrites the existing data.</span></span> <span data-ttu-id="9d404-120">트랜잭션 복제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 트랜잭션 로그를 통해 변경 내용을 추적하고 병합 복제는 트리거 및 메타데이터 테이블을 통해 변경 내용을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="9d404-120">Transactional replication tracks changes through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, and merge replication tracks changes through triggers and metadata tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d404-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d404-121">See Also</span></span>  
 [<span data-ttu-id="9d404-122">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="9d404-122">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
