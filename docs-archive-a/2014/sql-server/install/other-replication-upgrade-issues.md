---
title: 기타 복제 업그레이드 문제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e8ce3f35ead9d3322c636462f682ef391703cfe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659789"
---
# <a name="other-replication-upgrade-issues"></a><span data-ttu-id="c7392-102">기타 복제 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="c7392-102">Other Replication Upgrade Issues</span></span>
  <span data-ttu-id="c7392-103">이 항목에서는 업그레이드 관리자가 보고하지 않는 몇 가지 업그레이드 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-103">This topic covers a number of upgrade issues that are not reported by Upgrade Advisor.</span></span>  
  
## <a name="versions-supported"></a><span data-ttu-id="c7392-104">지원되는 버전</span><span class="sxs-lookup"><span data-stu-id="c7392-104">Versions Supported</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="c7392-105">은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복제된 데이터베이스를 업그레이드할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-105">supports upgrading replicated databases from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7392-106">따라서 노드 업그레이드 중에 다른 노드의 작업을 중지할 필요가 없으며</span><span class="sxs-lookup"><span data-stu-id="c7392-106">You do not have to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="c7392-107">한 토폴로지 내에서 지원되는 버전과 관련된 규칙만 잘 지키면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-107">Ensure that you adhere to the rules regarding which versions are supported in a topology.</span></span>  
  
 <span data-ttu-id="c7392-108">서로 다른 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 간에 복제하는 경우 가장 오래된 버전의 기능으로 제한되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-108">When you replicate between or among different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you are usually limited to the functionality of the earliest version that is being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7392-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 디스크상 스토리지 형식은 64비트 및 32비트 환경에서 동일하므로 복제 토폴로지가 32비트 환경에서 실행되는 서버 인스턴스와 64비트 환경에서 실행되는 서버 인스턴스를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-109">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments, a replication topology can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  
 <span data-ttu-id="c7392-110">모든 유형의 복제에서 배포자 버전은 게시자 버전과 같거나 그 이후 버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-110">For all types of replication, the Distributor version must be no earlier than the Publisher version.</span></span> <span data-ttu-id="c7392-111">배포자는 게시자와 동일한 인스턴스로 실행되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-111">(Frequently, the Distributor is the same instance as the Publisher.)</span></span>  
  
 <span data-ttu-id="c7392-112">트랜잭션 복제의 경우 트랜잭션 게시에 대한 구독자는 게시자의 두 가지 버전 중 어느 버전이든 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-112">For transactional replication, a Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span>  
  
 <span data-ttu-id="c7392-113">병합 복제의 경우 병합 게시에 대한 구독자는 게시자 버전과 같거나 이전 버전일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-113">For merge replication, a Subscriber to a merge publication can be any version no later than the Publisher version.</span></span>  
  
## <a name="merge-replication-batches-changes"></a><span data-ttu-id="c7392-114">병합 복제 일괄 처리 변경 내용</span><span class="sxs-lookup"><span data-stu-id="c7392-114">Merge Replication Batches Changes</span></span>  
 <span data-ttu-id="c7392-115">성능을 높이기 위해 병합 에이전트에서 수행된 변경 내용이 일괄 처리되므로 단일 문에서 둘 이상의 행을 삽입, 업데이트 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-115">Changes that are made by the Merge Agent are batched to improve performance; therefore, more than one row can be inserted, updated, or deleted within a single statement.</span></span> <span data-ttu-id="c7392-116">게시 또는 구독 데이터베이스의 게시된 테이블에 트리거가 있을 경우 해당 트리거에서 다중 행 삽입, 업데이트 및 삭제를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-116">If any published tables in the publication or subscription databases have triggers, ensure that the triggers can handle multirow inserts, updates, and deletes.</span></span> <span data-ttu-id="c7392-117">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "DML 트리거에 대한 다중 행 고려 사항"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7392-117">For more information, see "Multirow Considerations for DML Triggers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="activex-control-changes"></a><span data-ttu-id="c7392-118">ActiveX 컨트롤 변경 내용</span><span class="sxs-lookup"><span data-stu-id="c7392-118">ActiveX Control Changes</span></span>  
 <span data-ttu-id="c7392-119">복제 ActiveX 컨트롤에서 변경된 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-119">The following changes have been made for replication ActiveX controls:</span></span>  
  
-   <span data-ttu-id="c7392-120">모든 ActiveX 컨트롤은 스크립팅 및 초기화에 안전하지 않은 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-120">All ActiveX controls are marked as unsafe for scripting and initialization.</span></span>  
  
-   <span data-ttu-id="c7392-121">스냅샷 ActiveX 컨트롤은 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-121">The Snapshot ActiveX control has been dropped.</span></span> <span data-ttu-id="c7392-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하거나 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 스냅샷을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-122">You can create and manage snapshots by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or programmatically by using replication stored procedures.</span></span> <span data-ttu-id="c7392-123">자세한 내용은 온라인 설명서의 "방법: 초기 스냅숏 만들기 및 적용 ( [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] )" 및 "방법: 초기 스냅숏 만들기 (복제 Transact-sql 프로그래밍)" 항목을 참조 하십시오 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c7392-123">For more information, see the topics "How to: Create and Apply the Initial Snapshot ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)])" and "How to: Create the Initial Snapshot (Replication Transact-SQL Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="c7392-124">분산 ActiveX 컨트롤 및 병합 ActiveX 컨트롤은 이후에는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-124">The Distribution ActiveX control and Merge ActiveX control have been deprecated.</span></span> <span data-ttu-id="c7392-125">RMO(복제 관리 개체)를 사용한 관리 코드 애플리케이션에 비슷한 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7392-125">Similar functionality is provided for managed code applications using Replication Management Objects (RMO).</span></span> <span data-ttu-id="c7392-126">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "구독 동기화(RMO 프로그래밍)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7392-126">For more information, see "Synchronizing Subscriptions (RMO Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7392-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7392-127">See Also</span></span>  
 [<span data-ttu-id="c7392-128">복제 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="c7392-128">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
