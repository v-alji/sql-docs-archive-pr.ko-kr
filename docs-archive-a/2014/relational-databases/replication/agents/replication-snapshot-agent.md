---
title: 복제 스냅샷 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a26aca7b33a7355500350572ea5e8ed21bddeacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646947"
---
# <a name="replication-snapshot-agent"></a><span data-ttu-id="5eb23-102">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="5eb23-102">Replication Snapshot Agent</span></span>
  <span data-ttu-id="5eb23-103">복제 스냅샷 에이전트는 게시된 테이블과 데이터베이스 개체의 스키마 및 데이터를 포함하는 스냅샷 파일을 준비하여 스냅샷 폴더에 저장하고 배포 데이터베이스에 동기화 작업을 기록하는 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-103">The Replication Snapshot Agent is an executable file that prepares snapshot files containing schema and data of published tables and database objects, stores the files in the snapshot folder, and records synchronization jobs in the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eb23-104">매개 변수는 지정되는 순서에 제한을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-104">Parameters can be specified in any order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb23-105">구문</span><span class="sxs-lookup"><span data-stu-id="5eb23-105">Syntax</span></span>  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5eb23-106">인수</span><span class="sxs-lookup"><span data-stu-id="5eb23-106">Arguments</span></span>  
 <span data-ttu-id="5eb23-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="5eb23-107">**-?**</span></span>  
 <span data-ttu-id="5eb23-108">사용 가능한 모든 매개 변수를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-108">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="5eb23-109">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="5eb23-109">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="5eb23-110">게시자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-110">Is the name of the Publisher.</span></span> <span data-ttu-id="5eb23-111">해당 서버에 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스에 대해 server_name을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-111">Specify server_name for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="5eb23-112">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="5eb23-112">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="5eb23-113">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="5eb23-113">**-Publication** _publication_</span></span>  
 <span data-ttu-id="5eb23-114">게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-114">Is the name of the publication.</span></span> <span data-ttu-id="5eb23-115">이 매개 변수는 게시가 새 구독이나 다시 초기화된 구독에 대해 항상 스냅샷을 사용할 수 있도록 설정된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-115">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="5eb23-116">**-70Subscribers**</span><span class="sxs-lookup"><span data-stu-id="5eb23-116">**-70Subscribers**</span></span>  
 <span data-ttu-id="5eb23-117">구독자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전 7.0을 실행하는 경우에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-117">Must be used if any Subscribers are running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version 7.0.</span></span>  
  
 <span data-ttu-id="5eb23-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span><span class="sxs-lookup"><span data-stu-id="5eb23-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span></span>  
 <span data-ttu-id="5eb23-119">대량 복사 작업에서 보낼 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-119">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="5eb23-120">**bcp in** 작업을 수행하는 경우 일괄 처리 크기는 한 번의 트랜잭션으로 서버에 보낼 행 수이며 배포 에이전트가 **bcp** 진행 메시지를 기록하기 전에 보내야 하는 행 수이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-120">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="5eb23-121">**bcp out** 작업을 수행하는 경우 고정 일괄 처리 크기로 1000이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-121">When performing a **bcp out** operation, a fixed batch size of 1000 is used.</span></span> <span data-ttu-id="5eb23-122">값 0은 메시지 로깅을 사용하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-122">A value of 0 indicates no message logging.</span></span>  
  
 <span data-ttu-id="5eb23-123">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5eb23-123">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="5eb23-124">에이전트 정의 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-124">Is the path of the agent definition file.</span></span> <span data-ttu-id="5eb23-125">에이전트 정의 파일에는 에이전트의 명령줄 인수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-125">An agent definition file contains command line arguments for the agent.</span></span> <span data-ttu-id="5eb23-126">파일 내용은 실행 파일로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-126">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="5eb23-127">임의 문자가 있는 인수 값을 지정하려면 큰따옴표(")를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-127">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="5eb23-128">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="5eb23-128">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="5eb23-129">배포자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-129">Is the Distributor name.</span></span> <span data-ttu-id="5eb23-130">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-130">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="5eb23-131">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="5eb23-131">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="5eb23-132">**-DistributorDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-132">**-DistributorDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="5eb23-133">교착 상태가 발생할 경우 배포자에 대한 스냅샷 에이전트 연결의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-133">Is the priority of the Snapshot Agent connection to the Distributor when a deadlock occurs.</span></span> <span data-ttu-id="5eb23-134">이 매개 변수는 스냅샷을 생성하는 동안 스냅샷 에이전트와 사용자 애플리케이션 사이에서 발생할 수 있는 교착 상태를 해결하기 위해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-134">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="5eb23-135">DistributorDeadlockPriority 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-135">DistributorDeadlockPriority value</span></span>|<span data-ttu-id="5eb23-136">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-136">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="5eb23-137">**-1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-137">**-1**</span></span>|<span data-ttu-id="5eb23-138">배포자에서 교착 상태가 발생할 경우 스냅샷 에이전트 이외의 애플리케이션이 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-138">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Distributor.</span></span>|  
|<span data-ttu-id="5eb23-139">**0** (기본값)</span><span class="sxs-lookup"><span data-stu-id="5eb23-139">**0** (Default)</span></span>|<span data-ttu-id="5eb23-140">우선 순위가 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-140">Priority is not assigned.</span></span>|  
|<span data-ttu-id="5eb23-141">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-141">**1**</span></span>|<span data-ttu-id="5eb23-142">배포자에서 교착 상태가 발생할 경우 스냅샷 에이전트가 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-142">Snapshot Agent has priority when a deadlock occurs at the Distributor.</span></span>|  
  
 <span data-ttu-id="5eb23-143">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="5eb23-143">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="5eb23-144">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 배포자에 연결할 때 사용되는 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-144">Is the login used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5eb23-145">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="5eb23-145">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="5eb23-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 배포자에 연결할 때 사용되는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-146">Is the password used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="5eb23-147">.</span><span class="sxs-lookup"><span data-stu-id="5eb23-147">.</span></span>  
  
 <span data-ttu-id="5eb23-148">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-148">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5eb23-149">배포자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-149">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="5eb23-150">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 모드(기본값)를 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-150">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="5eb23-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span><span class="sxs-lookup"><span data-stu-id="5eb23-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span></span>  
 <span data-ttu-id="5eb23-152">동적 스냅샷을 만들 때 필터링에서 [HOST_NAME&#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) 값을 설정하는데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-152">Is used to set a value for [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="5eb23-153">예를 들어 아티클에 대해 하위 집합 필터 절 `rep_id = HOST_NAME()` 이 지정된 경우 병합 에이전트를 호출하기 전에 **DynamicFilterHostName** 속성을 "FBJones"로 설정하면 **rep_id** 열에 "FBJones"가 있는 행만 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-153">For example, if the subset filter clause `rep_id = HOST_NAME()` is specified for an article, and you set the **DynamicFilterHostName** property to "FBJones" before calling the Merge Agent, only rows having "FBJones" in the **rep_id** column will be replicated.</span></span>  
  
 <span data-ttu-id="5eb23-154">**-DynamicFilterLogin** _dynamic_filter_login_</span><span class="sxs-lookup"><span data-stu-id="5eb23-154">**-DynamicFilterLogin** _dynamic_filter_login_</span></span>  
 <span data-ttu-id="5eb23-155">동적 스냅샷을 만들 때 필터링에서 [SUSER_SNAME&#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 값을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-155">Is used to set a value for [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql)in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="5eb23-156">예를 들어 아티클에 대해 하위 집합 필터 절 `user_id = SUSER_SNAME()` 이 지정된 경우 **SQLSnapshot** 개체의 **Run** 메서드를 호출하기 전에 **DynamicFilterLogin** 속성을 "rsmith"로 설정하면 **user_id** 열에 "rsmith"가 있는 행만 스냅샷에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-156">For example, if the subset filter clause `user_id = SUSER_SNAME()` is specified for an article, and you set the **DynamicFilterLogin** property to "rsmith" before calling the **Run** method of the **SQLSnapshot** object, only rows having "rsmith" in the **user_id** column will be included in the snapshot.</span></span>  
  
 <span data-ttu-id="5eb23-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="5eb23-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="5eb23-158">동적 스냅샷을 생성할 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-158">Is the location where the dynamic snapshot should be generated.</span></span>  
  
 <span data-ttu-id="5eb23-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="5eb23-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="5eb23-160">연결을 만들 때 스냅샷 에이전트에서 사용하는 SSL(Secure Sockets Layer) 암호화의 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-160">Is the level of Secure Sockets Layer (SSL) encryption used by the Snapshot Agent when making connections.</span></span>  
  
|<span data-ttu-id="5eb23-161">EncryptionLevel 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-161">EncryptionLevel value</span></span>|<span data-ttu-id="5eb23-162">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-162">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="5eb23-163">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb23-163">**0**</span></span>|<span data-ttu-id="5eb23-164">SSL이 사용되지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-164">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="5eb23-165">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-165">**1**</span></span>|<span data-ttu-id="5eb23-166">SSL이 사용되지만 에이전트에서 SSL 서버 인증서가 트러스트된 발급자에 의해 서명된 것인지 확인하지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-166">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="5eb23-167">**2**</span><span class="sxs-lookup"><span data-stu-id="5eb23-167">**2**</span></span>|<span data-ttu-id="5eb23-168">SSL이 사용되고 인증서가 확인됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-168">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="5eb23-169">유효한 SSL 인증서는 SQL Server의 정규화된 도메인 이름으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-169">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="5eb23-170">-EncryptionLevel을 2로 설정할 때 에이전트가 성공적으로 연결되도록 하려면 로컬 SQL Server에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-170">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="5eb23-171">'별칭 이름' 매개 변수는 서버 이름이어야 하며 '서버' 매개 변수는 SQL Server의 정규화된 이름으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-171">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="5eb23-172">자세한 내용은 [SQL Server 복제 보안](../security/view-and-modify-replication-security-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5eb23-172">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="5eb23-173">**-FieldDelimiter** _field_delimiter_</span><span class="sxs-lookup"><span data-stu-id="5eb23-173">**-FieldDelimiter** _field_delimiter_</span></span>  
 <span data-ttu-id="5eb23-174">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 대량 복사 데이터 파일에서 필드 끝을 표시하는 문자 또는 문자 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-174">Is the character or character sequence that marks the end of a field in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="5eb23-175">기본값은 \n\<x$3>\n입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-175">The default is \n\<x$3>\n.</span></span>  
  
 <span data-ttu-id="5eb23-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="5eb23-177">스냅샷 작업을 수행하는 동안 기록에 추가되는 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-177">Specifies the amount of history logged during a snapshot operation.</span></span> <span data-ttu-id="5eb23-178">**1**을 선택하여 성능에서 기록 로깅의 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-178">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="5eb23-179">HistoryVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-179">HistoryVerboseLevel value</span></span>|<span data-ttu-id="5eb23-180">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-180">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="5eb23-181">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb23-181">**0**</span></span>|<span data-ttu-id="5eb23-182">진행 메시지를 콘솔이나 출력 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-182">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="5eb23-183">기록 레코드는 배포 데이터베이스에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-183">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="5eb23-184">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-184">**1**</span></span>|<span data-ttu-id="5eb23-185">시작, 진행, 성공 등과 같이 상태가 동일한 이전 기록 메시지를 항상 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-185">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="5eb23-186">상태가 같은 이전 레코드가 없으면 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-186">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="5eb23-187">**2** (기본값)</span><span class="sxs-lookup"><span data-stu-id="5eb23-187">**2** (default)</span></span>|<span data-ttu-id="5eb23-188">유휴 메시지나 장기 실행 작업 메시지에 대한 레코드가 없으면 새 기록 레코드를 삽입합니다. 이 경우 이전 레코드를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-188">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="5eb23-189">**3**</span><span class="sxs-lookup"><span data-stu-id="5eb23-189">**3**</span></span>|<span data-ttu-id="5eb23-190">유휴 메시지에 대한 레코드가 없으면 항상 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-190">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="5eb23-191">**-HRBcpBlocks** _number_of_blocks_</span><span class="sxs-lookup"><span data-stu-id="5eb23-191">**-HRBcpBlocks** _number_of_blocks_</span></span>  
 <span data-ttu-id="5eb23-192">기록기 스레드와 판독기 스레드 사이에서 대기하는 **bcp** 데이터 블록 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-192">Is the number of **bcp** data blocks that are queued between the writer and reader threads.</span></span> <span data-ttu-id="5eb23-193">기본값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-193">The default value is 50.</span></span> <span data-ttu-id="5eb23-194">**HRBcpBlocks** 는 Oracle 게시에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-194">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eb23-195">이 매개 변수는 Oracle 게시자에서 **bcp** 성능의 성능 튜닝에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-195">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="5eb23-196">-**Hrbcpblocksize**_block_size_</span><span class="sxs-lookup"><span data-stu-id="5eb23-196">-**HRBcpBlockSize**_block_size_</span></span>  
 <span data-ttu-id="5eb23-197">각 **bcp** 데이터 블록의 크기(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-197">Is the size, in kilobytes (KB), of each **bcp** data block.</span></span> <span data-ttu-id="5eb23-198">기본값은 64KB입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-198">The default value is 64 KB.</span></span> <span data-ttu-id="5eb23-199">**HRBcpBlocks** 는 Oracle 게시에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-199">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eb23-200">이 매개 변수는 Oracle 게시자에서 **bcp** 성능의 성능 튜닝에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-200">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="5eb23-201">**-HRBcpDynamicBlocks**</span><span class="sxs-lookup"><span data-stu-id="5eb23-201">**-HRBcpDynamicBlocks**</span></span>  
 <span data-ttu-id="5eb23-202">각 **bcp** 데이터 블록의 크기를 동적으로 늘릴 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-202">Is whether or not the size of each **bcp** data block can grow dynamically.</span></span> <span data-ttu-id="5eb23-203">**HRBcpBlocks** 는 Oracle 게시에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-203">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eb23-204">이 매개 변수는 Oracle 게시자에서 **bcp** 성능의 성능 튜닝에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-204">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="5eb23-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span><span class="sxs-lookup"><span data-stu-id="5eb23-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span></span>  
 <span data-ttu-id="5eb23-206">[MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) 테이블에 "waiting for backend message"를 기록하기 전까지 스냅샷 에이전트에서 대기하는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-206">Is the amount of time, in seconds, that the Snapshot Agent waits before logging "waiting for backend message" to the [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) table.</span></span> <span data-ttu-id="5eb23-207">기본값은 300초입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-207">The default value is 300 seconds.</span></span>  
  
 <span data-ttu-id="5eb23-208">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="5eb23-208">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="5eb23-209">로그인 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 **15** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-209">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="5eb23-210">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="5eb23-210">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="5eb23-211">병렬로 수행할 수 있는 대량 복사 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-211">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="5eb23-212">동시에 존재하는 스레드 및 ODBC 연결의 최대 개수는 **MaxBcpThreads** 와 배포 데이터베이스의 동기화 트랜잭션에 나타나는 대량 복사 요청 수 중 더 작은 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-212">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="5eb23-213">**MaxBcpThreads** 값은 **0** 보다 크고 하드 코딩된 상한값이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-213">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="5eb23-214">기본값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-214">The default is **1**.</span></span>  
  
 <span data-ttu-id="5eb23-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5eb23-216">관련이 없는 삭제 작업을 구독자에 보낼지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-216">Is if irrelevant deletes are sent to the Subscriber.</span></span> <span data-ttu-id="5eb23-217">관련이 없는 삭제 작업은 구독자의 파티션에 속하지 않는 행에 대해 구독자에게 보내지는 DELETE 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-217">Irrelevant deletes are DELETE commands that are sent to Subscribers for rows that do not belong to the Subscriber's partition.</span></span> <span data-ttu-id="5eb23-218">관련이 없는 삭제 작업은 데이터 무결성 또는 일치성에 영향을 주지 않지만 불필요한 네트워크 트래픽을 초래할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-218">Irrelevant deletes do not affect data integrity or convergence, but they can result in unnecessary network traffic.</span></span> <span data-ttu-id="5eb23-219">**MaxNetworkOptimization** 의 기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-219">The default value of **MaxNetworkOptimization** is **0**.</span></span> <span data-ttu-id="5eb23-220">**MaxNetworkOptimization** 을 **1** 로 설정하면 관련이 없는 삭제 작업이 최소화되므로 네트워크 트래픽이 줄어들고 네트워크 성능은 최대화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-220">Setting **MaxNetworkOptimization** to **1** minimizing the chances of irrelevant deletes thereby reducing network traffic and maximizing network optimization.</span></span> <span data-ttu-id="5eb23-221">이 매개 변수를 **1** 로 설정하면 메타데이터 스토리지 공간이 늘어나며 여러 수준의 조인 필터와 복잡한 하위 집합 필터가 있는 경우 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-221">Setting this parameter to **1** can also increase the storage of metadata and cause performance to degrade at the Publisher if multiple levels of join filters and complex subset filters are present.</span></span> <span data-ttu-id="5eb23-222">복제 토폴로지를 신중하게 평가한 후 관련이 없는 삭제 작업으로 인해 네트워크 트래픽이 허용 불가능한 수준으로 높아지는 경우에만 **MaxNetworkOptimization** 을 **1** 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-222">You should carefully assess your replication topology and set **MaxNetworkOptimization** to **1** only if network traffic from irrelevant deletes is unacceptably high.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5eb23-223">이 매개 변수를 **1** 로 설정 하는 것은 병합 게시의 동기화 최적화 옵션이 **true** 로 설정 된 경우에만 유용 합니다 ( **@keep_partition_changes** [transact-sql&#41;&#40;sp_addmergepublication ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)의 매개 변수).</span><span class="sxs-lookup"><span data-stu-id="5eb23-223">Setting this parameter to **1** is useful only when the synchronization optimization option of the merge publication is set to **true** (the **@keep_partition_changes** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span>  
  
 <span data-ttu-id="5eb23-224">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5eb23-224">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="5eb23-225">에이전트 출력 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-225">Is the path of the agent output file.</span></span> <span data-ttu-id="5eb23-226">파일 이름을 지정하지 않으면 출력이 콘솔로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-226">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="5eb23-227">지정된 파일 이름이 존재하면 출력이 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-227">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="5eb23-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="5eb23-229">출력이 자세해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-229">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="5eb23-230">OutputVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-230">OutputVerboseLevel value</span></span>|<span data-ttu-id="5eb23-231">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-231">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5eb23-232">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb23-232">**0**</span></span>|<span data-ttu-id="5eb23-233">오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-233">Only error messages are printed.</span></span>|  
|<span data-ttu-id="5eb23-234">**1** (기본값)</span><span class="sxs-lookup"><span data-stu-id="5eb23-234">**1** (default)</span></span>|<span data-ttu-id="5eb23-235">모든 진행률 보고 메시지가 출력됩니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="5eb23-235">All the progress report messages are printed (default).</span></span>|  
|<span data-ttu-id="5eb23-236">**2**</span><span class="sxs-lookup"><span data-stu-id="5eb23-236">**2**</span></span>|<span data-ttu-id="5eb23-237">모든 오류 메시지 및 진행률 보고 메시지가 출력되며, 디버깅에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-237">All error messages and progress report messages are printed, which is useful for debugging.</span></span>|  

 <span data-ttu-id="5eb23-238">**-PrefetchTables** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-238">**-PrefetchTables** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5eb23-239">테이블 개체가 프리페치되고 캐시되는지를 지정하는 선택적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-239">Optional parameter that specifies if the table objects will be prefetched and cached.</span></span>  <span data-ttu-id="5eb23-240">기본 동작은 내부 계산을 기반으로 하는 SMO 구성 요소를 사용하여 특정 테이블 속성을 프리페치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-240">The default behavior is to prefetch certain table properties using SMO component based on an internal calculation.</span></span>  <span data-ttu-id="5eb23-241">이 매개 변수는 SMO 프리페치 작업이 실행하는 데 상당히 오래 걸리는 시나리오에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-241">This parameter can be helpful in scenarios where SMO prefetch operation takes considerable longer to run.</span></span> <span data-ttu-id="5eb23-242">이 매개 변수를 사용하지 않으면 게시에 아티클로 추가되는 테이블의 비율을 기준으로 런타임 시 동작이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-242">If this parameter is not used, this decision is made at runtime based on the percentage of tables that are added as articles to the publication.</span></span>  
  
|<span data-ttu-id="5eb23-243">OutputVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-243">OutputVerboseLevel value</span></span>|<span data-ttu-id="5eb23-244">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-244">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5eb23-245">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb23-245">**0**</span></span>|<span data-ttu-id="5eb23-246">SMO 구성 요소의 프리페치 메서드 호출을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-246">Call to Prefetch method of SMO component is disabled.</span></span>|  
|<span data-ttu-id="5eb23-247">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-247">**1**</span></span>|<span data-ttu-id="5eb23-248">스냅샷 에이전트가 프리페치 메서드를 호출하여 SMO를 사용하는 일부 테이블 속성을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-248">Snapshot Agent will call Prefetch method to cache some table properties using SMO</span></span>|  
  
 <span data-ttu-id="5eb23-249">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="5eb23-249">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="5eb23-250">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 때 스냅샷 에이전트에서 사용하는 패킷 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-250">Is the packet size (in bytes) used by the Snapshot Agent when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5eb23-251">기본값은 8192바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-251">The default value is 8192 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eb23-252">성능이 향상될 것이라는 확신이 없으면 패킷 크기를 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5eb23-252">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="5eb23-253">대부분의 애플리케이션에는 기본 패킷 크기가 제일 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-253">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="5eb23-254">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="5eb23-254">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="5eb23-255">에이전트 매개 변수에 사용할 에이전트 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-255">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="5eb23-256">**ProfileName** 이 NULL이면 에이전트 프로필이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-256">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="5eb23-257">**ProfileName** 이 지정되지 않으면 에이전트 유형에 대한 기본 프로필이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-257">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="5eb23-258">자세한 내용은 [복제 에이전트 프로필](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eb23-258">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="5eb23-259">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="5eb23-259">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="5eb23-260">게시 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-260">Is the name of the publication database.</span></span> <span data-ttu-id="5eb23-261">이 매개 변수는 Oracle 게시자에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-261">*This parameter is not supported for Oracle Publishers*.</span></span>  
  
 <span data-ttu-id="5eb23-262">**-PublisherDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-262">**-PublisherDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="5eb23-263">교착 상태가 발생할 경우 게시자에 대한 스냅샷 에이전트 연결의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-263">Is the priority of the Snapshot Agent connection to the Publisher when a deadlock occurs.</span></span> <span data-ttu-id="5eb23-264">이 매개 변수는 스냅샷을 생성하는 동안 스냅샷 에이전트와 사용자 애플리케이션 사이에서 발생할 수 있는 교착 상태를 해결하기 위해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-264">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="5eb23-265">PublisherDeadlockPriority 값</span><span class="sxs-lookup"><span data-stu-id="5eb23-265">PublisherDeadlockPriority value</span></span>|<span data-ttu-id="5eb23-266">Description</span><span class="sxs-lookup"><span data-stu-id="5eb23-266">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="5eb23-267">**-1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-267">**-1**</span></span>|<span data-ttu-id="5eb23-268">게시자에서 교착 상태가 발생할 경우 스냅샷 에이전트 이외의 애플리케이션이 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-268">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Publisher.</span></span>|  
|<span data-ttu-id="5eb23-269">**0** (기본값)</span><span class="sxs-lookup"><span data-stu-id="5eb23-269">**0** (Default)</span></span>|<span data-ttu-id="5eb23-270">우선 순위가 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-270">Priority is not assigned.</span></span>|  
|<span data-ttu-id="5eb23-271">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb23-271">**1**</span></span>|<span data-ttu-id="5eb23-272">게시자에서 교착 상태가 발생할 경우 스냅샷 에이전트가 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-272">Snapshot Agent has priority when a deadlock occurs at the Publisher.</span></span>|  
  
 <span data-ttu-id="5eb23-273">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="5eb23-273">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="5eb23-274">게시 데이터베이스와 함께 데이터베이스 미러링 세션에 참여하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 장애 조치 파트너 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-274">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="5eb23-275">자세한 내용은 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eb23-275">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="5eb23-276">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="5eb23-276">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="5eb23-277">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 게시자에 연결할 때 사용되는 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-277">Is the login used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5eb23-278">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="5eb23-278">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="5eb23-279">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 게시자에 연결할 때 사용되는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-279">Is the password used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="5eb23-280">.</span><span class="sxs-lookup"><span data-stu-id="5eb23-280">.</span></span>  
  
 <span data-ttu-id="5eb23-281">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-281">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5eb23-282">게시자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-282">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="5eb23-283">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증(기본값)을 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-283">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="5eb23-284">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="5eb23-284">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="5eb23-285">쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 1800초입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-285">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="5eb23-286">**-ReplicationType** [ **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="5eb23-286">**-ReplicationType** [ **1**| **2**]</span></span>  
 <span data-ttu-id="5eb23-287">복제 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-287">Specifies the type of replication.</span></span> <span data-ttu-id="5eb23-288">값 **1** 은 트랜잭션 복제를 나타내며 값 **2** 는 병합 복제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-288">A value of **1** indicates transactional replication, and a value of **2** indicates merge replication.</span></span>  
  
 <span data-ttu-id="5eb23-289">**-RowDelimiter** _row_delimiter_</span><span class="sxs-lookup"><span data-stu-id="5eb23-289">**-RowDelimiter** _row_delimiter_</span></span>  
 <span data-ttu-id="5eb23-290">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 대량 복사 데이터 파일에서 행 끝을 표시하는 문자 또는 문자 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-290">Is the character or character sequence that marks the end of a row in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="5eb23-291">기본값은 \n\<,@g>\n입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-291">The default is \n\<,@g>\n.</span></span>  
  
 <span data-ttu-id="5eb23-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="5eb23-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="5eb23-293">스냅숏 에이전트 동시에 실행 중인 동적 스냅숏 프로세스의 수가 **@max_concurrent_dynamic_snapshots** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)의 속성으로 설정 된 제한에 도달한 경우 대기 하는 최대 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-293">Is the maximum number of seconds that the Snapshot Agent waits when the number of concurrent dynamic snapshot processes running is at the limit set by the **@max_concurrent_dynamic_snapshots** property of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="5eb23-294">최대 시간(초)에 도달한 경우 스냅샷 에이전트가 계속 대기 중이면 해당 스냅샷 에이전트가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-294">If the maximum number of seconds is reached and the Snapshot Agent is still waiting, it will exit.</span></span> <span data-ttu-id="5eb23-295">값 0은 에이전트가 취소될 경우에도 무기한 대기함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-295">A value of 0 means that the agent waits indefinitely, although it can be canceled.</span></span>  
  
 <span data-ttu-id="5eb23-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span><span class="sxs-lookup"><span data-stu-id="5eb23-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span></span>  
 <span data-ttu-id="5eb23-297">이 매개 변수는 더 이상 사용되지 않으며 이전 버전과의 호환성을 위해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-297">This parameter has been deprecated and is supported for backward-compatibility only.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eb23-298">설명</span><span class="sxs-lookup"><span data-stu-id="5eb23-298">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5eb23-299">도메인 사용자 계정(기본값)이 아닌 로컬 시스템 계정에서 실행되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 설치한 경우 해당 서비스에서는 로컬 컴퓨터에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-299">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a Local System account rather than under a Domain User account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="5eb23-300">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트에서 실행되는 스냅샷 에이전트가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로그인할 때 Windows 인증 모드를 사용하도록 구성된 경우 해당 스냅샷 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-300">If the Snapshot Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Snapshot Agent fails.</span></span> <span data-ttu-id="5eb23-301">기본 설정은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-301">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5eb23-302">스냅샷 에이전트를 시작하려면 명령 프롬프트에서 **snapshot.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5eb23-302">To start the Snapshot Agent, execute **snapshot.exe** from the command prompt.</span></span> <span data-ttu-id="5eb23-303">자세한 내용은 [복제 에이전트 실행 파일](../concepts/replication-agent-executables-concepts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5eb23-303">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb23-304">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5eb23-304">See Also</span></span>  
 [<span data-ttu-id="5eb23-305">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="5eb23-305">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
