---
title: Oracle 게시 개요 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b59b12dfcba1472cb6f9d6ecfc51a7df8104fb0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653273"
---
# <a name="oracle-publishing-overview"></a><span data-ttu-id="ea599-102">Oracle Publishing Overview</span><span class="sxs-lookup"><span data-stu-id="ea599-102">Oracle Publishing Overview</span></span>
  <span data-ttu-id="ea599-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터는 복제 토폴로지에 Oracle 버전 9i 이상의 Oracle 게시자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-103">Beginning with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you can include Oracle Publishers in your replication topology, starting with Oracle version 9i.</span></span> <span data-ttu-id="ea599-104">게시 서버는 모든 Oracle 지원 하드웨어 및 운영 체제에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-104">Publishing servers can be deployed on any Oracle supported hardware and operating system.</span></span> <span data-ttu-id="ea599-105">이 기능은 잘 설정된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 스냅샷 복제 및 트랜잭션 복제의 토대 위에 구축되었으므로 비슷한 성능과 유용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-105">The feature is built on the well-established foundation of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot replication and transactional replication, providing similar performance and usability.</span></span>  
  
 <span data-ttu-id="ea599-106">Oracle 게시는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="ea599-107">SQL Server 이외의 구독자에 대한 다른 유형의 복제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-107">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="ea599-108">데이터를 이동하려면 변경 데이터 캡처 및 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]를 사용하여 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a><span data-ttu-id="ea599-109">Oracle의 스냅샷 복제</span><span class="sxs-lookup"><span data-stu-id="ea599-109">Snapshot Replication for Oracle</span></span>  
 <span data-ttu-id="ea599-110">Oracle 스냅샷 게시는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 스냅샷 게시와 비슷한 방식으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-110">Oracle snapshot publications are implemented in a manner similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot publications.</span></span> <span data-ttu-id="ea599-111">Oracle 게시에 대해 스냅샷 에이전트가 실행되면 해당 에이전트는 Oracle 게시자에 연결한 다음 게시의 각 테이블을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-111">When the Snapshot Agent runs for an Oracle publication, it connects to the Oracle Publisher and processes each table in the publication.</span></span> <span data-ttu-id="ea599-112">이 에이전트는 각 테이블을 처리할 때 테이블 행을 검색하고 스키마 스크립트를 만듭니다. 이 스크립트는 게시의 스냅샷 공유에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-112">When processing each table, the agent retrieves the table rows and creates schema scripts, which are then stored on the publication's snapshot share.</span></span> <span data-ttu-id="ea599-113">스냅샷 에이전트가 실행될 때마다 전체 데이터 집합이 생성되므로 트랜잭션 복제의 경우처럼 Oracle 테이블에 변경 내용 추적 트리거가 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-113">The entire set of data is created each time the Snapshot Agent runs, so change tracking triggers are not added to the Oracle tables as they are with transactional replication.</span></span> <span data-ttu-id="ea599-114">스냅샷 복제를 사용하면 게시 시스템에 미치는 영향을 최소화하면서 데이터를 편리하게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-114">Snapshot replication provides a convenient way to migrate data with minimal impact on the publishing system.</span></span>  
  
## <a name="transactional-replication-for-oracle"></a><span data-ttu-id="ea599-115">Oracle의 트랜잭션 복제</span><span class="sxs-lookup"><span data-stu-id="ea599-115">Transactional Replication for Oracle</span></span>  
 <span data-ttu-id="ea599-116">Oracle 트랜잭션 게시는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 트랜잭션 게시 아키텍처를 사용하여 구현되지만 변경 내용은 Oracle 데이터베이스에 대한 데이터베이스 트리거와 로그 판독기 에이전트를 함께 사용하여 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-116">Oracle transactional publications are implemented using the transactional publishing architecture of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; however, changes are tracked using a combination of database triggers on the Oracle database and the Log Reader Agent.</span></span> <span data-ttu-id="ea599-117">Oracle 트랜잭션 게시에 대한 구독자는 스냅샷 복제를 사용하여 자동으로 초기화됩니다. 후속 변경 내용이 발생하면 로그 판독기 에이전트를 통해 추적된 후 구독자로 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-117">Subscribers to an Oracle transactional publication are automatically initialized using snapshot replication; subsequent changes are tracked and delivered to Subscribers as they occur via the Log Reader Agent.</span></span>  
  
 <span data-ttu-id="ea599-118">Oracle 게시가 생성되면 Oracle 데이터베이스 내의 게시된 각 테이블에 대해 트리거 및 추적 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-118">When an Oracle publication is created, triggers and tracking tables are created for each published table within the Oracle database.</span></span> <span data-ttu-id="ea599-119">게시된 테이블의 데이터가 변경되면 테이블에 대해 데이터베이스 트리거가 발생되고 수정된 각 행에 대한 정보가 복제 추적 테이블에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-119">When data changes are made to the published tables, the database triggers on the tables fire and insert information into the replication tracking tables for each modified row.</span></span> <span data-ttu-id="ea599-120">그런 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에 대한 로그 판독기 에이전트가 추적 테이블의 데이터 변경 정보를 배포자의 배포 데이터베이스로 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-120">The Log Reader Agent on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor then moves the data change information from the tracking tables to the distribution database on the Distributor.</span></span> <span data-ttu-id="ea599-121">마지막으로 표준 트랜잭션 복제의 경우처럼 배포 에이전트가 배포자에서 구독자로 변경 내용을 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="ea599-121">Finally, as in standard transactional replication, the Distribution Agent moves changes from the Distributor to the Subscribers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea599-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea599-122">See Also</span></span>  
 <span data-ttu-id="ea599-123">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="ea599-123">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="ea599-124">[Oracle 게시를 위한 용어 설명](glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="ea599-124">[Glossary of Terms for Oracle Publishing](glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="ea599-125">다른 유형의 데이터베이스 복제</span><span class="sxs-lookup"><span data-stu-id="ea599-125">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
