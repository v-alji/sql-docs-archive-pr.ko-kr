---
title: MSSQLSERVER_1418 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1418 (Database Engine error)
ms.assetid: 6e9c7241-0201-44e0-9f8b-b3c4e293f0f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1fcac03f044aacce5e907824862eb589c97a07d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734112"
---
# <a name="mssqlserver_1418"></a><span data-ttu-id="d9732-102">MSSQLSERVER_1418</span><span class="sxs-lookup"><span data-stu-id="d9732-102">MSSQLSERVER_1418</span></span>
    
## <a name="details"></a><span data-ttu-id="d9732-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d9732-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9732-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d9732-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d9732-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d9732-105">Event ID</span></span>|<span data-ttu-id="d9732-106">1418</span><span class="sxs-lookup"><span data-stu-id="d9732-106">1418</span></span>|  
|<span data-ttu-id="d9732-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d9732-107">Event Source</span></span>|<span data-ttu-id="d9732-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d9732-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d9732-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d9732-109">Component</span></span>|<span data-ttu-id="d9732-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d9732-110">SQLEngine</span></span>|  
|<span data-ttu-id="d9732-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d9732-111">Symbolic Name</span></span>|<span data-ttu-id="d9732-112">DBM_PARTNERNOTFOUND</span><span class="sxs-lookup"><span data-stu-id="d9732-112">DBM_PARTNERNOTFOUND</span></span>|  
|<span data-ttu-id="d9732-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d9732-113">Message Text</span></span>|<span data-ttu-id="d9732-114">서버 네트워크 주소 "%.\*ls"에 연결할 수 없거나 주소가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-114">The server network address "%.\*ls" can not be reached or does not exist.</span></span> <span data-ttu-id="d9732-115">네트워크 주소 이름을 확인하고 로컬과 원격 엔드포인트에 대한 포트가 작동하는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d9732-115">Check the network address name and that the ports for the local and remote endpoints are operational.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9732-116">설명</span><span class="sxs-lookup"><span data-stu-id="d9732-116">Explanation</span></span>  
 <span data-ttu-id="d9732-117">지정된 서버 네트워크 주소에 연결할 수 없거나 주소가 존재하지 않으므로 서버 네트워크 엔드포인트가 응답하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-117">The server network endpoint did not respond because the specified server network address cannot be reached or does not exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9732-118">기본적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 운영 체제에서는 모든 포트를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-118">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] operating system blocks all ports.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9732-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d9732-119">User Action</span></span>  
 <span data-ttu-id="d9732-120">네트워크 주소 이름을 확인하고 명령을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9732-120">Verify the network address name and reissue the command.</span></span>  
  
 <span data-ttu-id="d9732-121">두 파트너에서 모두 수정 동작이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-121">Corrective action might be required on both partners.</span></span> <span data-ttu-id="d9732-122">예를 들어 주 서버 인스턴스에서 SET PARTNER를 실행할 때 이 메시지가 발생하면 미러 서버 인스턴스에서만 수정 동작을 하면 되는 것으로 메시지가 표시되지만</span><span class="sxs-lookup"><span data-stu-id="d9732-122">For example, if this message is raised when you are trying to run SET PARTNER on the principal server instance, the message might imply that you only have to take corrective action on the mirror server instance.</span></span> <span data-ttu-id="d9732-123">실제로 두 파트너에서 모두 수정 동작이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-123">However, corrective actions might be required on both partners.</span></span>  
  
### <a name="additional-corrective-actions"></a><span data-ttu-id="d9732-124">추가 수정 동작</span><span class="sxs-lookup"><span data-stu-id="d9732-124">Additional Corrective Actions</span></span>  
  
-   <span data-ttu-id="d9732-125">미러 데이터베이스의 미러링 준비가 완료되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-125">Make sure that the mirror database is ready for mirroring.</span></span>  
  
-   <span data-ttu-id="d9732-126">미러 서버 인스턴스의 이름과 포트가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-126">Make sure that the name and port of the mirror server instance are correct.</span></span>  
  
-   <span data-ttu-id="d9732-127">대상 미러 서버 인스턴스에 방화벽이 설정되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-127">Make sure that the destination mirror server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="d9732-128">주 서버 인스턴스에 방화벽이 설정되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-128">Make sure that the principal server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="d9732-129">**sys.database_mirroring_endpoints** 카탈로그 뷰의 **state** 또는 **state_desc** 열을 사용하여 파트너에서 엔드포인트가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-129">Verify that the endpoints are started on the partners by using the **state** or **state_desc** column the of the **sys.database_mirroring_endpoints** catalog view.</span></span> <span data-ttu-id="d9732-130">엔드포인트가 시작되지 않았으면 ALTER ENDPOINT 문을 실행하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-130">If either endpoint is not started, execute an ALTER ENDPOINT statement to start it.</span></span>  
  
-   <span data-ttu-id="d9732-131">주 서버 인스턴스가 해당 데이터베이스 미러링 엔드포인트에 할당된 포트에서 수신하고 있는지, 미러 서버 인스턴스가 해당 포트에서 수신하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-131">Make sure that the principal server instance is listening on the port assigned to its database mirroring endpoint and that and the mirror server instance is listening on its port.</span></span> <span data-ttu-id="d9732-132">자세한 내용은 이 항목의 뒤에 나오는 "포트 가용성 확인"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9732-132">For more information, see "Verifying Port Availability," later in this topic.</span></span> <span data-ttu-id="d9732-133">파트너가 할당된 포트에서 수신하고 있지 않으면 다른 포트에서 수신하도록 데이터베이스 미러링 엔드포인트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-133">If a partner is not listening on its assigned port, modify the database mirroring endpoint to listen on a different port.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d9732-134">보안이 잘못 구성된 경우 일반적인 설치 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-134">Improperly configured security can cause a general setup error message.</span></span> <span data-ttu-id="d9732-135">일반적으로 서버 인스턴스는 잘못된 연결 요청에 응답하지 않고 이를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-135">Typically, the server instance drops the bad connection request without responding.</span></span> <span data-ttu-id="d9732-136">호출자에게는 미러 데이터베이스가 없거나 상태가 잘못되었거나, 사용 권한이 올바르지 않는 등의 여러 가지 이유로 보안 구성 오류가 발생한 것처럼 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-136">To the caller, a security-configuration error could appear to have occurred for a variety of other reasons, such as the mirror database in a bad state or does not exist, incorrect permissions, and so on.</span></span>  
  
### <a name="using-the-error-log-file-for-diagnosis"></a><span data-ttu-id="d9732-137">진단을 위해 오류 로그 파일 사용</span><span class="sxs-lookup"><span data-stu-id="d9732-137">Using the Error Log File for Diagnosis</span></span>  
 <span data-ttu-id="d9732-138">오류 로그 파일만 검사할 수 있는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-138">In some cases, only error log files are available for investigation.</span></span> <span data-ttu-id="d9732-139">이 경우 데이터베이스 미러링 엔드포인트의 TCP 포트에 대한 오류 메시지 26023이 오류 로그에 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-139">In these cases, determine whether the error log contains error message 26023 for the TCP port of the database mirroring endpoint.</span></span> <span data-ttu-id="d9732-140">심각도 16인 이 오류는 데이터베이스 미러링 엔드포인트가 시작되지 않았음을 나타낼 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-140">This error, which is severity 16, might indicate that the database mirroring endpoint is not started.</span></span> <span data-ttu-id="d9732-141">**sys.database_mirroring_endpoints**에서 엔드포인트 상태를 시작됨으로 표시하는 경우에도 이 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-141">This message can occur even if **sys.database_mirroring_endpoints** shows the endpoint state as started.</span></span>  
  
 <span data-ttu-id="d9732-142">발생한 문제를 해결한 후 주 서버에서 ALTER DATABASE *database_name* SET PARTNER 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-142">After resolving any issues that you encounter, rerun the ALTER DATABASE *database_name* SET PARTNER statement on the principal server.</span></span>  
  
### <a name="verifying-port-availability"></a><span data-ttu-id="d9732-143">포트 가용성 확인</span><span class="sxs-lookup"><span data-stu-id="d9732-143">Verifying Port Availability</span></span>  
 <span data-ttu-id="d9732-144">네트워크에서 데이터베이스 미러링 세션을 구성할 때는 각 서버 인스턴스의 데이터베이스 미러링 엔드포인트가 데이터베이스 미러링 프로세스에만 사용되도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9732-144">When you are configuring the network for a database mirroring session, make sure the database mirroring endpoint of each server instance is used by only the database mirroring process.</span></span> <span data-ttu-id="d9732-145">데이터베이스 미러링 엔드포인트에 할당된 포트에서 다른 프로세스가 수신할 경우 다른 서버 인스턴스의 데이터베이스 미러링 프로세스에서 해당 엔드포인트에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-145">If another process is listening on the port assigned to a database mirroring endpoint, the database mirroring processes of the other server instances cannot connect to the endpoint.</span></span>  
  
 <span data-ttu-id="d9732-146">Windows 기반 서버가 수신하고 있는 모든 포트를 표시하려면 **netstat** 명령 프롬프트 유틸리티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-146">To display all the ports on which a Windows-based server is listening, use the **netstat** command-prompt utility.</span></span> <span data-ttu-id="d9732-147">**netstat** 구문은 Windows 운영 체제의 버전에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-147">The syntax for **netstat** depends on the version of the Windows operating system.</span></span> <span data-ttu-id="d9732-148">자세한 내용은 해당 운영 체제 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9732-148">For more information, see the operating system documentation.</span></span>  
  
#### <a name="windows-server-2003-service-pack-1-sp1"></a><span data-ttu-id="d9732-149">Windows Server 2003 서비스 팩 1(SP1)</span><span class="sxs-lookup"><span data-stu-id="d9732-149">Windows Server 2003 Service Pack 1 (SP1)</span></span>  
 <span data-ttu-id="d9732-150">수신 포트와 해당 포트가 열려 있는 프로세스를 나열하려면 Windows 명령 프롬프트에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-150">To list listening ports and the processes that have those ports opened, enter the following command at the Windows command prompt:</span></span>  
  
 <span data-ttu-id="d9732-151">**netstat -abn**</span><span class="sxs-lookup"><span data-stu-id="d9732-151">**netstat -abn**</span></span>  
  
#### <a name="windows-server-2003-pre-sp1"></a><span data-ttu-id="d9732-152">Windows Server 2003(SP1 이전)</span><span class="sxs-lookup"><span data-stu-id="d9732-152">Windows Server 2003 (pre-SP1)</span></span>  
 <span data-ttu-id="d9732-153">수신 포트와 해당 포트가 열려 있는 프로세스를 식별하려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="d9732-153">To identify the listening ports and the processes that have those ports opened, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d9732-154">프로세스 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-154">Obtain the process ID.</span></span>  
  
     <span data-ttu-id="d9732-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 프로세스 ID를 확인하려면 해당 인스턴스에 연결한 후 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-155">To learn the process ID of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connect to that instance and use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT SERVERPROPERTY('ProcessID')   
    ```  
  
     <span data-ttu-id="d9732-156">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "SERVERPROPERTY(Transact-SQL)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9732-156">For more information, see "SERVERPROPERTY (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d9732-157">다음 **netstat** 명령의 출력과 프로세스 ID를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d9732-157">Match the process ID with the output of the following **netstat** command:</span></span>  
  
     <span data-ttu-id="d9732-158">**netstat -ano**</span><span class="sxs-lookup"><span data-stu-id="d9732-158">**netstat -ano**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9732-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9732-159">See Also</span></span>  
 <span data-ttu-id="d9732-160">[ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9732-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="d9732-161">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d9732-161">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="d9732-162">[미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d9732-162">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="d9732-163">[SERVERPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9732-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="d9732-164">[서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="d9732-164">[Specify a Server Network Address &#40;Database Mirroring&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="d9732-165">[sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9732-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="d9732-166">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d9732-166">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
