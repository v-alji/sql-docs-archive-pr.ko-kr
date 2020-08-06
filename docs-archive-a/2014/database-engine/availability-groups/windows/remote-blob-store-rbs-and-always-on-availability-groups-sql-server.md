---
title: RBS (Remote Blob Store) 및 AlwaysOn 가용성 그룹 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12a11162d286731b2b510a9051183e6c3025b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648604"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="63e7a-102">RBS(Remote Blob Store) 및 AlwaysOn 가용성 그룹(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63e7a-102">Remote Blob Store (RBS) and AlwaysOn Availability Groups (SQL Server)</span></span>
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="63e7a-103">는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [RBS (Remote blob Store)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) blob 개체에 대 한 고가용성 및 재해 복구 솔루션을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-103">can provide a high-availability and disaster recovery solution for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Remote Blob Store (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) BLOB objects (blobs).</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="63e7a-104">은 가용성 데이터베이스에 저장된 RBS 메타데이터 및 스키마를 보조 복제본에 복제하여 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-104">protects any RBS metadata and schemas stored in an availability database by replicating them to the secondary replicas.</span></span> <span data-ttu-id="63e7a-105">다음은 SharePoint 콘텐츠 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-105">This is the SharePoint Content Database.</span></span> <span data-ttu-id="63e7a-106">일반적으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 은 BLOB에서 이 RBS 메타데이터를 독립적으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-106">Generally speaking, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stores this RBS metadata independently from the blob.</span></span>  
  
 <span data-ttu-id="63e7a-107">RBD BLOB 데이터 보호는 다음과 같이 BLOB 저장소 위치에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-107">The protection for RBD BLOB data depends on the BLOB Store Location, as follows:</span></span>  
  
|<span data-ttu-id="63e7a-108">BLOB 저장소 위치</span><span class="sxs-lookup"><span data-stu-id="63e7a-108">BLOB Store Location</span></span>|<span data-ttu-id="63e7a-109">가용성 그룹이 이 BLOB 데이터를 보호할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="63e7a-109">Can Availability Groups Protect This BLOB Data?</span></span>|  
|-------------------------|-----------------------------------------------------|  
|<span data-ttu-id="63e7a-110">RBS 메타데이터를 포함하는 동일한 데이터베이스(RBS 원격 FILESTREAM 공급자를 사용하여 저장)</span><span class="sxs-lookup"><span data-stu-id="63e7a-110">The same database that contains the RBS metadata  (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="63e7a-111">예</span><span class="sxs-lookup"><span data-stu-id="63e7a-111">Yes</span></span>|  
|<span data-ttu-id="63e7a-112">동일한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 있는 다른 데이터베이스(RBS 원격 FILESTREAM 공급자를 사용하여 저장)</span><span class="sxs-lookup"><span data-stu-id="63e7a-112">Another database in the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="63e7a-113">예</span><span class="sxs-lookup"><span data-stu-id="63e7a-113">Yes</span></span><br /><br /> <span data-ttu-id="63e7a-114">RBS 메타데이터를 포함하는 데이터베이스와 동일한 가용성 그룹에 이 데이터베이스를 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-114">We recommend that you put this database in the same availability group as the database that contains the RBS metadata.</span></span>|  
|<span data-ttu-id="63e7a-115">다른 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 있는 다른 데이터베이스(RBS 원격 FILESTREAM 공급자를 사용하여 저장)</span><span class="sxs-lookup"><span data-stu-id="63e7a-115">Another database in a different instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="63e7a-116">예</span><span class="sxs-lookup"><span data-stu-id="63e7a-116">Yes</span></span><br /><br /> <span data-ttu-id="63e7a-117">이 데이터베이스는 별도의 가용성 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-117">This database must be in a separate availability group.</span></span>|  
|<span data-ttu-id="63e7a-118">타사 BLOB 저장소</span><span class="sxs-lookup"><span data-stu-id="63e7a-118">A third-party BLOB store</span></span>|<span data-ttu-id="63e7a-119">아니요</span><span class="sxs-lookup"><span data-stu-id="63e7a-119">No</span></span><br /><br /> <span data-ttu-id="63e7a-120">이 BLOB 데이터를 보호하려면 BLOB 저장소 공급자의 고가용성 메커니즘을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="63e7a-120">To protect this BLOB data, use the high-availability mechanisms of the BLOB store provider.</span></span>|  
  
##  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="63e7a-121">제한 사항</span><span class="sxs-lookup"><span data-stu-id="63e7a-121">Limitations</span></span>  
  
-   <span data-ttu-id="63e7a-122">RBS 유지 관리자는 주 복제본에서 대상이 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-122">RBS maintainers need to be targeted on the primary replica.</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="63e7a-123">권장 사항</span><span class="sxs-lookup"><span data-stu-id="63e7a-123">Recommendations</span></span>  
  
-   <span data-ttu-id="63e7a-124">가용성 그룹 수신기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63e7a-124">Use an availability group listener.</span></span> <span data-ttu-id="63e7a-125">자세한 내용은 [가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63e7a-125">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="63e7a-126">관련 내용</span><span class="sxs-lookup"><span data-stu-id="63e7a-126">Related Content</span></span>  
  
-   <span data-ttu-id="63e7a-127">[온라인 설명서의](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) Remote BLOB Store 유지 관리 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63e7a-127">[Maintaining Remote BLOB Store](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
-   <span data-ttu-id="63e7a-128">[RBS 유지 관리자 실행](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (블로그)</span><span class="sxs-lookup"><span data-stu-id="63e7a-128">[Running RBS Maintainer](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (blog)</span></span>  
  
-   <span data-ttu-id="63e7a-129">[FILESTREAM 공급자를 사용하여 RBS(Remote BLOB Storage) 구성(SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (블로그)</span><span class="sxs-lookup"><span data-stu-id="63e7a-129">[Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e7a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63e7a-130">See Also</span></span>  
 <span data-ttu-id="63e7a-131">[AlwaysOn 클라이언트 연결 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63e7a-131">[AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span></span>  
 [<span data-ttu-id="63e7a-132">RBS&#40;Remote Blob Store&#41;&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63e7a-132">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
