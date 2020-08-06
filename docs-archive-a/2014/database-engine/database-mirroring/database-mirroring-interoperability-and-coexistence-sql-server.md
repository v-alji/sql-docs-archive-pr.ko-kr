---
title: '데이터베이스 미러링: 상호 운용성 및 공존성 (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 057392842974c3342fc57d0ec113f8b1bb58b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649685"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="9f674-102">데이터베이스 미러링: 상호 운용성 및 공존성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9f674-102">Database Mirroring: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="9f674-103">데이터베이스 미러링은 다음의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]기능 또는 구성 요소와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f674-103">Database mirroring can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="9f674-104">AlwaysOn 장애 조치(Failover) 클러스터 인스턴스(SQL Server 장애 조치(Failover) 클러스터링)</span><span class="sxs-lookup"><span data-stu-id="9f674-104">AlwaysOn Failover Cluster Instances (SQL Server Failover Clustering)</span></span>](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [<span data-ttu-id="9f674-105">변경 데이터 캡처 및 변경 내용 추적</span><span class="sxs-lookup"><span data-stu-id="9f674-105">Change data capture (and change tracking)</span></span>](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [<span data-ttu-id="9f674-106">데이터베이스 스냅샷</span><span class="sxs-lookup"><span data-stu-id="9f674-106">Database snapshots</span></span>](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [<span data-ttu-id="9f674-107">전체 텍스트 카탈로그</span><span class="sxs-lookup"><span data-stu-id="9f674-107">Full-text catalogs</span></span>](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [<span data-ttu-id="9f674-108">로그 전달</span><span class="sxs-lookup"><span data-stu-id="9f674-108">Log shipping</span></span>](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="9f674-109">복제</span><span class="sxs-lookup"><span data-stu-id="9f674-109">Replication</span></span>](database-mirroring-and-replication-sql-server.md)  
  
 <span data-ttu-id="9f674-110">데이터베이스 미러링은 다음과 상호 운용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f674-110">Database mirroring does not interoperate with the following:</span></span>  
  
-   <span data-ttu-id="9f674-111">데이터베이스 간 트랜잭션/분산 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="9f674-111">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="9f674-112">해당 트랜잭션이 지원되지 않는 이유에 대한 자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f674-112">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f674-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f674-113">See Also</span></span>  
 [<span data-ttu-id="9f674-114">데이터베이스 미러링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9f674-114">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
