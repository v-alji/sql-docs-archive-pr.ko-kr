---
title: MSSQL_ENG014117 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4694aacc7d1f5ee31f4ff54d8cdd4256b48f713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638688"
---
# <a name="mssql_eng014117"></a><span data-ttu-id="dd0bd-102">MSSQL_ENG014117</span><span class="sxs-lookup"><span data-stu-id="dd0bd-102">MSSQL_ENG014117</span></span>
    
## <a name="message-details"></a><span data-ttu-id="dd0bd-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="dd0bd-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd0bd-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="dd0bd-104">Product Name</span></span>|<span data-ttu-id="dd0bd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd0bd-105">SQL Server</span></span>|  
|<span data-ttu-id="dd0bd-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="dd0bd-106">Event ID</span></span>|<span data-ttu-id="dd0bd-107">14117</span><span class="sxs-lookup"><span data-stu-id="dd0bd-107">14117</span></span>|  
|<span data-ttu-id="dd0bd-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="dd0bd-108">Event Source</span></span>|<span data-ttu-id="dd0bd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dd0bd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dd0bd-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="dd0bd-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="dd0bd-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="dd0bd-111">Symbolic Name</span></span>||  
|<span data-ttu-id="dd0bd-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="dd0bd-112">Message Text</span></span>|<span data-ttu-id="dd0bd-113">'%s'이(가) 배포 데이터베이스로 구성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-113">'%s' is not configured as a distribution database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd0bd-114">설명</span><span class="sxs-lookup"><span data-stu-id="dd0bd-114">Explanation</span></span>  
 <span data-ttu-id="dd0bd-115">이 오류는 다음 상황 중 하나 또는 둘 다에 해당되는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-115">This error can occur if one or both of the following are true:</span></span>  
  
-   <span data-ttu-id="dd0bd-116">지정된 배포 데이터베이스에 대한 항목이 **msdb..MSdistributiondbs**에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-116">The entry for the specified distribution database is missing from **msdb..MSdistributiondbs**.</span></span>  
  
-   <span data-ttu-id="dd0bd-117">**master** 데이터베이스에 로컬 서버에 대한 항목이 없거나 올바르지 않은 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-117">There is not an entry for the local server in the **master** database, or the entry that is there is incorrect.</span></span>  
  
     <span data-ttu-id="dd0bd-118">복제 시 컴퓨터 이름과 인스턴스 이름(옵션)을 사용하여 토폴로지의 모든 서버를 등록해야 하며 클러스터형 인스턴스의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가상 서버 이름과 인스턴스 이름(옵션)이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-118">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="dd0bd-119">복제가 제대로 수행되려면 토폴로지의 각 서버에 대해 `SELECT @@SERVERNAME` 이 반환한 값이 컴퓨터 이름이나 가상 서버 이름 및 인스턴스 이름(옵션)과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-119">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
     <span data-ttu-id="dd0bd-120">IP 주소나 FQDN(정규화된 도메인 이름)으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 등록한 경우에는 복제가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-120">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="dd0bd-121">복제 구성 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 IP 주소 또는 FQDN으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스를 등록한 경우 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-121">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd0bd-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="dd0bd-122">User Action</span></span>  
 <span data-ttu-id="dd0bd-123">배포자 인스턴스가 제대로 등록되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-123">Verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="dd0bd-124">컴퓨터의 네트워크 이름과 SQL Server 인스턴스의 이름이 다른 경우 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-124">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="dd0bd-125">SQL Server 인스턴스 이름을 유효한 네트워크 이름으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-125">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="dd0bd-126">대체 네트워크 이름을 설정하는 한 가지 방법은 해당 이름을 로컬 호스트 파일에 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-126">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="dd0bd-127">로컬 호스트 파일은 기본적으로 WINDOWS\system32\drivers\etc 또는 WINNT\system32\drivers\etc에 있습니다. 자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-127">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="dd0bd-128">예를 들어 컴퓨터 이름이 comp1이고 컴퓨터의 IP 주소가 10.193.17.129이고 인스턴스 이름이 inst1/instname이면 호스트 파일에 다음 항목을 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-128">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="dd0bd-129">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="dd0bd-129">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="dd0bd-130">배포를 해제하고 인스턴스를 등록한 후 배포를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-130">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="dd0bd-131">비클러스터형 인스턴스에 대해 @@SERVERNAME 값이 올바르지 않으면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-131">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="dd0bd-132">[sp_addserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 저장 프로시저를 실행한 후에 @@SERVERNAME 변경 내용을 적용하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-132">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="dd0bd-133">클러스터형 인스턴스에 대해 @@SERVERNAME 값이 올바르지 않으면 클러스터 관리자를 사용하여 해당 이름을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-133">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="dd0bd-134">자세한 내용은 [Always On 장애 조치(failover) 클러스터 인스턴스(SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-134">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 <span data-ttu-id="dd0bd-135">배포자 인스턴스가 제대로 등록되었는지 확인한 후 배포 데이터베이스가 **msdb..MSdistributiondbs**에 나열되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-135">After verifying that the Distributor instance is registered properly, verify that the distribution database is listed in **msdb..MSdistributiondbs**.</span></span> <span data-ttu-id="dd0bd-136">배포 데이터베이스가 목록에 없는 경우 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-136">If it is not listed:</span></span>  
  
1.  <span data-ttu-id="dd0bd-137">배포 구성을 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-137">Script out the distribution configuration.</span></span> <span data-ttu-id="dd0bd-138">자세한 내용은 [Scripting Replication](scripting-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-138">For more information, see [Scripting Replication](scripting-replication.md).</span></span>  
  
2.  <span data-ttu-id="dd0bd-139">배포를 해제한 다음 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-139">Disable distribution and then re-enable it.</span></span> <span data-ttu-id="dd0bd-140">자세한 내용은 [Configure Distribution](configure-distribution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0bd-140">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0bd-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd0bd-141">See Also</span></span>  
 [<span data-ttu-id="dd0bd-142">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="dd0bd-142">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
