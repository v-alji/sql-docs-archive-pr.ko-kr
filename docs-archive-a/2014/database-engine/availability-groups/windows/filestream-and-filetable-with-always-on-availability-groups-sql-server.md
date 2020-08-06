---
title: FILESTREAM 및 FileTable AlwaysOn 가용성 그룹 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7de7b4d66890bb5f1fe49799844f666de81f4db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650273"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="6b93c-102">AlwaysOn 가용성 그룹의 FILESTREAM 및 FileTable(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b93c-102">FILESTREAM and FileTable with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="6b93c-103">이 항목에는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]과 함께 FILESTREAM 및 FileTable 기능 사용에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-103">This topic contains information about the using the FILESTREAM and FileTable features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="6b93c-104">모든 FILESTREAM 기능이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-104">All FILESTREAM functionality is supported.</span></span> <span data-ttu-id="6b93c-105">장애 조치(Failover) 이후 FILESTREAM 데이터는 읽기 가능한 두 보조 복제본 및 새로운 주 복제본에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-105">After a failover, FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
 <span data-ttu-id="6b93c-106">FileTable 기능은 부분적으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-106">FileTable functionality is partially supported.</span></span> <span data-ttu-id="6b93c-107">장애 조치(Failover) 이후 FileTable 데이터는 주 복제본에서 액세스할 수 있지만 FileTable 데이터를 읽기 가능한 보조 복제본에서는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
 <span data-ttu-id="6b93c-108">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="6b93c-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="6b93c-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6b93c-109">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="6b93c-110">FILESTREAM 및 FileTable 액세스를 위해 VNNs (Virtual Network 이름) 사용</span><span class="sxs-lookup"><span data-stu-id="6b93c-110">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>](#vnn)  
  
-   [<span data-ttu-id="6b93c-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6b93c-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="6b93c-112">관련 내용</span><span class="sxs-lookup"><span data-stu-id="6b93c-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6b93c-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6b93c-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="6b93c-114">FileTable을 포함하거나 포함하지 않고 FILESTREAM을 사용하는 데이터베이스를 가용성 그룹에 추가하려면 먼저 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에 FILESTREAM이 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-114">Before adding a database that uses FILESTREAM, with or without FileTable, to an availability group, ensure that FILESTREAM is enabled on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="6b93c-115">자세한 내용은 [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b93c-115">For more information, see [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).</span></span>  
  
##  <a name="using-virtual-network-names-vnns-for-filestream-and-filetable-access"></a><a name="vnn"></a> <span data-ttu-id="6b93c-116">FILESTREAM 및 FileTable 액세스를 위한 VNN(가상 네트워크 이름) 사용</span><span class="sxs-lookup"><span data-stu-id="6b93c-116">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>  
 <span data-ttu-id="6b93c-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에 FILESTREAM을 설정하면 FILESTREAM 데이터에 대한 액세스를 제공하도록 인스턴스 수준의 공유가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-117">When you enable FILESTREAM on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], an instance-level share is created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="6b93c-118">이 공유에는 다음 형식의 컴퓨터 이름을 사용하여 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-118">You access this share by using the computer name in the following format:</span></span>  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 <span data-ttu-id="6b93c-119">하지만 AlwaysOn 가용성 그룹에서 컴퓨터 이름은 VNN(가상 네트워크 이름)을 사용하여 가상화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-119">In an AlwaysOn availability group, however, the name of the computer is virtualized by using a Virtual Network Name, or VNN.</span></span> <span data-ttu-id="6b93c-120">컴퓨터가 가용성 그룹에서 주 복제본이고, 가용성 그룹의 데이터베이스에 FILESTREAM 데이터가 포함되어 있으면 FILESTREAM 데이터에 대한 액세스를 제공하도록 VNN 범위의 공유도 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-120">When the computer is the primary replica in an availability group, and databases in the availability group contain FILESTREAM data, then a VNN-scoped share is also created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="6b93c-121">이러한 동작은 FILESTREAM 데이터에 대한 Transact-SQL 액세스에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-121">This does not affect Transact-SQL access to FILESTREAM data.</span></span> <span data-ttu-id="6b93c-122">하지만 파일 시스템 API를 사용하는 애플리케이션은 다음 형식의 경로가 포함된 VNN 범위의 공유를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-122">However applications that use file system APIs have to use the VNN-scoped share, which has a path in the following format:</span></span>  
  
 `\\<VNN>\<filestream_share_name>`  
  
 <span data-ttu-id="6b93c-123">이 VNN 범위의 공유는 다음 이벤트 중 하나가 발생할 때 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-123">This VNN-scoped share is created when one of the following events occurs.</span></span>  
  
-   <span data-ttu-id="6b93c-124">FILESTREAM 데이터가 포함된 데이터베이스를 주 복제본의 AlwaysOn 가용성 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-124">You add a database that contains FILESTREAM data to an AlwaysOn availability group on the primary replica.</span></span> <span data-ttu-id="6b93c-125">이 경우 `\\<computer_name>\<filestream_share_name>` 공유는 이미 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-125">In this case, the share `\\<computer_name>\<filestream_share_name>` already exists.</span></span> <span data-ttu-id="6b93c-126">`\\<VNN>\<filestream_share_name>` 공유가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-126">The share `\\<VNN>\<filestream_share_name>` is created.</span></span>  
  
-   <span data-ttu-id="6b93c-127">가용성 그룹이 포함된 주 복제본에서 파일 입/출력 스트리밍 액세스를 위해 FILESTREAM을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-127">You enable FILESTREAM for file i/o streaming access on a primary replica that has availability groups.</span></span> <span data-ttu-id="6b93c-128">다음 공유가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-128">The following shares are created:</span></span>  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  <span data-ttu-id="6b93c-129">`\\<VNN1>\<filestream_share_name>` - 가용성 그룹 1</span><span class="sxs-lookup"><span data-stu-id="6b93c-129">`\\<VNN1>\<filestream_share_name>` for availability group 1.</span></span>  
  
    3.  <span data-ttu-id="6b93c-130">`\\<VNN2>\<filestream_share_name>` - 가용성 그룹 2</span><span class="sxs-lookup"><span data-stu-id="6b93c-130">`\\<VNN2>\<filestream_share_name>` for availability group 2.</span></span>  
  
 <span data-ttu-id="6b93c-131">이러한 VNN 범위의 공유는 모든 보조 복제본에도 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-131">These VNN-scoped shares are also propagated to all secondary replicas.</span></span>  
  
 <span data-ttu-id="6b93c-132">FILESTREAM 또는 FileTable 데이터가 포함된 데이터베이스가 AlwaysOn 가용성 그룹에 속하는 경우</span><span class="sxs-lookup"><span data-stu-id="6b93c-132">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="6b93c-133">FILESTREAM 및 FileTable 함수가 컴퓨터 이름 대신 VNN(가상 네트워크 이름)을 사용하거나 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-133">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="6b93c-134">이러한 함수에 대한 자세한 내용은 [Filestream 및 FileTable 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b93c-134">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="6b93c-135">파일 시스템 API를 통한 FILESTREAM 또는 FileTable 데이터에 대한 모든 액세스에는 컴퓨터 이름 대신 VNN이 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-135">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span>  
  
 <span data-ttu-id="6b93c-136">데이터베이스가 가용성 그룹에 속할 때 애플리케이션이 `\\<computer_name>\<filestream_share_name>` 형식의 컴퓨터 이름을 사용하여 공유에 액세스하려고 시도하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-136">If your application tries to access the share by using the computer name in the format `\\<computer_name>\<filestream_share_name>` when the database is part of an availability group, then an error is raised.</span></span>  
  
 <span data-ttu-id="6b93c-137">데이터베이스가 가용성 그룹에 속하지 않을 때 애플리케이션이 VNN 범위의 경로를 사용하여 공유에 액세스하려고 시도하면 요청이 성공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-137">If your application tries to access the share by using a VNN-scoped path when the database is not part of an availability group, then the request may succeed.</span></span> <span data-ttu-id="6b93c-138">이 경우 가상 네트워크 이름은 컴퓨터 이름으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-138">In this case, the virtual network name is resolved to the computer name.</span></span> <span data-ttu-id="6b93c-139">하지만 이러한 사용 방식은 가용성 그룹이 삭제될 경우 VNN 범위의 경로가 작동을 중지할 수 있기 때문에 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b93c-139">However this usage is strongly discouraged, since the VNN-scoped path will stop working if the availability group is dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6b93c-140">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6b93c-140">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6b93c-141">Enable and Configure FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="6b93c-141">Enable and Configure FILESTREAM</span></span>](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [<span data-ttu-id="6b93c-142">FileTable의 필수 구성 요소를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="6b93c-142">Enable the Prerequisites for FileTable</span></span>](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="6b93c-143">관련 내용</span><span class="sxs-lookup"><span data-stu-id="6b93c-143">Related Content</span></span>  
 <span data-ttu-id="6b93c-144">없음</span><span class="sxs-lookup"><span data-stu-id="6b93c-144">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b93c-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b93c-145">See Also</span></span>  
 [<span data-ttu-id="6b93c-146">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="6b93c-146">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
