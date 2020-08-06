---
title: AlwaysOn 가용성 그룹 (SQL Server)를 사용 하는 데이터베이스 스냅숏 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1e4307653b5b8150d71019a373ee073d15123f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736795"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="49144-102">AlwaysOn 가용성 그룹이 있는 데이터베이스 스냅샷(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="49144-102">Database Snapshots with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="49144-103">가용성 그룹의 주 데이터베이스 또는 보조 데이터베이스에서 데이터베이스 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-103">You can create a database snapshot on an primary or secondary database in an availability group.</span></span> <span data-ttu-id="49144-104">복제본 역할은 RESOLVING 상태가 아닌 PRIMARY 또는 SECONDARY 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49144-104">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
 <span data-ttu-id="49144-105">데이터베이스 동기화 상태가 SYNCHRONIZING 또는 SYNCHRONIZED인 상태에서 데이터베이스 스냅샷을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-105">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="49144-106">데이터베이스 동기화 상태가 NOT SYNCHRONIZING인 경우에도 데이터베이스 스냅샷을 만들 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-106">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
 <span data-ttu-id="49144-107">복제본이 주 복제본에서 DISCONNECTED된 경우 보조 복제본의 데이터베이스 스냅샷은 계속 작업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49144-107">A database snapshot on a secondary replica should continue to work if the replica is DISCONNECTED from the primary replica.</span></span>  
  
 <span data-ttu-id="49144-108">일부 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 조건에서는 원본 데이터베이스와 데이터베이스 스냅샷이 모두 다시 시작되어 일시적으로 사용자와의 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="49144-108">Some [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] conditions cause both the source database and its database snapshots to be restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="49144-109">이러한 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-109">These conditions are as follows:</span></span>  
  
-   <span data-ttu-id="49144-110">동일한 서버 인스턴스에서 현재 주 복제본이 오프라인으로 전환되었다가 다시 온라인으로 돌아오거나 가용성 그룹이 장애 조치를 수행하기 때문에 주 복제본이 역할을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="49144-110">The primary replica changes roles, whether because the current primary replica goes off line and comes back online on the same server instance or because the availability group fails over.</span></span>  
  
-   <span data-ttu-id="49144-111">데이터베이스가 보조 역할로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="49144-111">The database enters the secondary role.</span></span>  
  
 <span data-ttu-id="49144-112">데이터베이스 스냅샷을 호스팅하는 가용성 복제본이 장애 조치되는 경우 데이터베이스 스냅샷은 처음 만들어진 서버 인스턴스에 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="49144-112">If the availability replica that hosts database snapshots is failed over, the database snapshots remain on the server instance where they were created.</span></span> <span data-ttu-id="49144-113">사용자는 장애 조치 후에도 스냅샷을 계속 사용할 수 있습니다. 사용자 환경에서 성능이 중요한 경우 수동 장애 조치 모드에 대해 구성되는 보조 복제본에서 호스팅되는 보조 데이터베이스에서만 데이터베이스 스냅샷을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-113">Users can continue to use the snapshots after the failover.If performance is a concern in your environment, we recommend that you create database snapshots only on secondary databases that are hosted by a secondary replica that is configured for manual failover mode.</span></span>  <span data-ttu-id="49144-114">가용성 그룹을 이 보조 복제본으로 수동으로 장애 조치하는 경우 다른 보조 복제본에서 새 데이터베이스 스냅샷 집합을 만들고 클라이언트를 새 데이터베이스 스냅샷으로 리디렉션한 다음 새 주 데이터베이스의 모든 데이터베이스 스냅샷을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49144-114">If you ever manually fail over the availability group to this secondary replica, you can create a new set of database snapshots on another secondary replica, redirect clients to the new database snapshots, and drop all of the database snapshots from the now primary databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49144-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49144-115">See Also</span></span>  
 <span data-ttu-id="49144-116">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49144-116">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="49144-117">데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="49144-117">Database Snapshots &#40;SQL Server&#41;</span></span>](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
