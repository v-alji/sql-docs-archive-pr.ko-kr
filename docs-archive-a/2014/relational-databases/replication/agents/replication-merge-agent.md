---
title: 복제 병합 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Merge Agent, executables
- Merge Agent, parameter reference
- agents [SQL Server replication], Merge Agent
- command prompt [SQL Server replication]
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b3d74dcc6be62ae8a01d911a8404c7bc32fd651
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646952"
---
# <a name="replication-merge-agent"></a><span data-ttu-id="93544-102">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="93544-102">Replication Merge Agent</span></span>
  <span data-ttu-id="93544-103">복제 병합 에이전트는 데이터베이스 테이블에 저장된 초기 스냅샷 파일을 구독자에 적용하는 유틸리티 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-103">The Replication Merge Agent is a utility executable that applies the initial snapshot held in the database tables to the Subscribers.</span></span> <span data-ttu-id="93544-104">또한 이 에이전트는 초기 스냅샷이 만들어진 후 게시자에서 발생한 증분 데이터 변경 내용을 병합하고, 사용자가 구성한 규칙에 따라 또는 사용자가 만든 사용자 지정 해결 프로그램을 사용하여 충돌을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-104">It also merges incremental data changes that occurred at the Publisher after the initial snapshot was created, and reconciles conflicts either according to the rules you configure or using a custom resolver you create.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93544-105">매개 변수는 지정되는 순서에 제한을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="93544-106">선택적 매개 변수가 지정되지 않은 경우 로컬 컴퓨터의 미리 정의된 레지스트리 설정 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-106">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93544-107">구문</span><span class="sxs-lookup"><span data-stu-id="93544-107">Syntax</span></span>  
  
```  
  
      replmerg [-?]   
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Publicationpublication-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database  
[-AltSnapshotFolderalt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-DestThreadsnumber_of_destination_threads]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatchdownload_generations_per_batch]  
[-DownloadReadChangesPerBatchdownload_read_changes_per_batch]  
[-DownloadWriteChangesPerBatchdownload_write_changes_per_batch]  
[-DynamicSnapshotLocationdynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]  
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogininternet_login]  
[-InternetPasswordinternet_password]  
[-InternetProxyLogininternet_proxy_login]  
[-InternetProxyPasswordinternet_proxy_password]  
[-InternetProxyServerinternet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeoutinternet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MakeGenerationIntervalmake_generation_interval_seconds]  
[-MaxBcpThreadsnumber_of_threads]  
[-MaxDownloadChangesnumber_of_download_changes]  
[-MaxUploadChangesnumber_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSizepacket_size]   
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOutquery_time_out_seconds]  
[-SrcThreadsnumber_of_source_threads]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatchupload_generations_per_batch]  
[-UploadReadChangesPerBatchupload_read_changes_per_batch]  
[-UploadWriteChangesPerBatchupload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateIntervalvalidate_interval]  
```  
  
## <a name="arguments"></a><span data-ttu-id="93544-108">인수</span><span class="sxs-lookup"><span data-stu-id="93544-108">Arguments</span></span>  
 <span data-ttu-id="93544-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="93544-109">**-?**</span></span>  
 <span data-ttu-id="93544-110">사용 가능한 모든 매개 변수를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-110">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="93544-111">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="93544-111">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="93544-112">게시자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-112">Is the name of the Publisher.</span></span> <span data-ttu-id="93544-113">해당 서버에 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스에 대해 *server_name*을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-113">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="93544-114">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="93544-114">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="93544-115">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="93544-115">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="93544-116">게시자 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-116">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="93544-117">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="93544-117">**-Publication** _publication_</span></span>  
 <span data-ttu-id="93544-118">게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-118">Is the name of the publication.</span></span> <span data-ttu-id="93544-119">이 매개 변수는 게시가 새 구독이나 다시 초기화된 구독에 대해 항상 스냅샷을 사용할 수 있도록 설정된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-119">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="93544-120">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="93544-120">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="93544-121">구독자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-121">Is the name of the Subscriber.</span></span> <span data-ttu-id="93544-122">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-122">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="93544-123">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="93544-123">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="93544-124">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="93544-124">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="93544-125">구독자 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-125">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="93544-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="93544-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="93544-127">구독에 대한 초기 스냅샷이 들어 있는 폴더의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-127">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="93544-128">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="93544-128">**-Continuous**</span></span>  
 <span data-ttu-id="93544-129">에이전트에서 복제된 트랜잭션의 폴링을 계속 시도할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-129">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="93544-130">이 인수가 지정된 경우 에이전트는 보류 중인 트랜잭션이 없는 경우에도 원본의 복제된 트랜잭션을 폴링 간격에 따라 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-130">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="93544-131">**-DestThreads** _number_of_destination_threads_</span><span class="sxs-lookup"><span data-stu-id="93544-131">**-DestThreads** _number_of_destination_threads_</span></span>  
 <span data-ttu-id="93544-132">병합 에이전트에서 대상에 변경 내용을 적용하는 데 사용하는 대상 스레드의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-132">Specifies the number of destination threads that the Merge Agent uses to apply changes at the destination.</span></span> <span data-ttu-id="93544-133">업로드 중에는 게시자가 대상이 되고 다운로드 중에는 구독자가 대상이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-133">The destination is the Publisher during upload and the Subscriber during download.</span></span> <span data-ttu-id="93544-134">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-134">The default is 4.</span></span>  
  
 <span data-ttu-id="93544-135">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="93544-135">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="93544-136">에이전트 정의 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-136">Is the path of the agent definition file.</span></span> <span data-ttu-id="93544-137">에이전트 정의 파일에는 에이전트의 명령 프롬프트 인수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-137">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="93544-138">파일 내용은 실행 파일로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-138">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="93544-139">임의 문자가 있는 인수 값을 지정하려면 큰따옴표(")를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-139">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="93544-140">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="93544-140">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="93544-141">배포자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-141">Is the Distributor name.</span></span> <span data-ttu-id="93544-142">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-142">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="93544-143">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="93544-143">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="93544-144">배포자(밀어넣기) 배포의 경우에는 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름이 기본 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-144">For Distributor (push) distribution, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="93544-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="93544-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="93544-146">배포자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="93544-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="93544-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="93544-148">배포자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="93544-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="93544-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="93544-150">배포자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="93544-151">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 모드(기본값)를 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-151">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="93544-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span></span>  
 <span data-ttu-id="93544-153">게시자의 변경 내용을 구독자로 다운로드하는 동안 한 번의 일괄 처리에서 처리할 세대 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-153">Is the number of generations to be processed in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="93544-154">세대는 아티클 단위의 논리적 변경 내용 그룹으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-154">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="93544-155">안정적인 통신 연결의 기본값은 100이고,</span><span class="sxs-lookup"><span data-stu-id="93544-155">The default for a reliable communication link is 100.</span></span> <span data-ttu-id="93544-156">안정적이지 않은 통신 연결의 기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-156">The default for an unreliable communication link is 10.</span></span>  
  
 <span data-ttu-id="93544-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span></span>  
 <span data-ttu-id="93544-158">게시자의 변경 내용을 구독자로 다운로드하는 동안 한 번의 일괄 처리에서 읽을 변경 내용 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-158">Is the number of changes to be read in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="93544-159">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-159">The default is 100.</span></span>  
  
 <span data-ttu-id="93544-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span></span>  
 <span data-ttu-id="93544-161">게시자의 변경 내용을 구독자로 다운로드하는 동안 한 번의 일괄 처리에서 적용할 변경 내용 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-161">Is the number of changes to be applied in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="93544-162">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-162">The default is 100.</span></span>  
  
 <span data-ttu-id="93544-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="93544-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="93544-164">게시에서 매개 변수가 있는 행 필터를 사용할 경우 필터링된 데이터 스냅샷 파일의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-164">Is the location of the filtered data snapshot files when the publication uses parameterized row filters.</span></span>  
  
 <span data-ttu-id="93544-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="93544-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="93544-166">연결을 만들 때 병합 에이전트에서 사용하는 SSL(Secure Sockets Layer) 암호화의 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-166">Is the level of Secure Sockets Layer (SSL) encryption used by the Merge Agent when making connections.</span></span>  
  
|<span data-ttu-id="93544-167">EncryptionLevel 값</span><span class="sxs-lookup"><span data-stu-id="93544-167">EncryptionLevel value</span></span>|<span data-ttu-id="93544-168">Description</span><span class="sxs-lookup"><span data-stu-id="93544-168">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="93544-169">**0**</span><span class="sxs-lookup"><span data-stu-id="93544-169">**0**</span></span>|<span data-ttu-id="93544-170">SSL이 사용되지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-170">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="93544-171">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-171">**1**</span></span>|<span data-ttu-id="93544-172">SSL이 사용되지만 에이전트에서 SSL 서버 인증서가 트러스트된 발급자에 의해 서명된 것인지 확인하지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-172">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="93544-173">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-173">**2**</span></span>|<span data-ttu-id="93544-174">SSL이 사용되고 인증서가 확인됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-174">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="93544-175">유효한 SSL 인증서는 SQL Server의 정규화된 도메인 이름으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-175">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="93544-176">-EncryptionLevel을 2로 설정할 때 에이전트가 성공적으로 연결되도록 하려면 로컬 SQL Server에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93544-176">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="93544-177">'별칭 이름' 매개 변수는 서버 이름이어야 하며 '서버' 매개 변수는 SQL Server의 정규화된 이름으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-177">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="93544-178">자세한 내용은 [SQL Server 복제 보안](../security/view-and-modify-replication-security-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93544-178">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="93544-179">**-ExchangeType** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="93544-179">**-ExchangeType** [ **1**| **2**| **3**]</span></span>  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="93544-180">업로드를 제한하려면 `@subscriber_upload_options`의 `sp_addmergearticle`를 대신 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="93544-180">To restrict uploading, use the `@subscriber_upload_options` of `sp_addmergearticle` instead.</span></span>  
  
 <span data-ttu-id="93544-181">동기화를 수행할 때의 데이터 교환 유형을 지정하며 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-181">Specifies the type of data exchange during synchronization, which can be one of the following:</span></span>  
  
|<span data-ttu-id="93544-182">ExchangeType 값</span><span class="sxs-lookup"><span data-stu-id="93544-182">ExchangeType value</span></span>|<span data-ttu-id="93544-183">Description</span><span class="sxs-lookup"><span data-stu-id="93544-183">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="93544-184">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-184">**1**</span></span>|<span data-ttu-id="93544-185">에이전트에서 구독자의 데이터 변경 내용을 게시자로 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-185">Agent should upload data changes from the Subscriber to the Publisher.</span></span>|  
|<span data-ttu-id="93544-186">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-186">**2**</span></span>|<span data-ttu-id="93544-187">에이전트에서 게시자의 데이터 변경 내용을 구독자로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-187">Agent should download data changes from the Publisher to the Subscriber.</span></span>|  
|<span data-ttu-id="93544-188">**3** (기본값)</span><span class="sxs-lookup"><span data-stu-id="93544-188">**3** (default)</span></span>|<span data-ttu-id="93544-189">에이전트에서는 먼저 구독자의 데이터 변경 내용을 게시자로 업로드한 다음 게시자의 데이터 변경 내용을 구독자로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-189">Agent should first upload data changes from the Subscriber to the Publisher and then download data changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="93544-190">웹 동기화의 경우 이 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-190">You must use this option with Web synchronization.</span></span>|  
  
 <span data-ttu-id="93544-191">다운로드 전용 아티클을 사용하면 게시에 있는 개별 아티클의 동기화 동작을 제어할 수 있으며 성능도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-191">Download-only articles enable you to control the synchronization behavior of individual articles in a publication, and they can provide a performance benefit.</span></span> <span data-ttu-id="93544-192">자세한 내용은 [다운로드 전용 아티클로 병합 복제 성능 최적화](../merge/optimize-merge-replication-performance-with-download-only-articles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93544-192">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="93544-193">`ExchangeType`을 사용하여 병합 복제의 업로드 및 다운로드 단계를 별도의 세션으로 분리하는 경우 `ExchangeType`을 먼저 1로 설정한 상태로 병합 에이전트를 실행한 후 값을 2로 설정하여 병합 에이전트를 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-193">If using `ExchangeType` to separate the upload and download phase of merge replication into separate sessions, you must run the merge agent with `ExchangeType` set to 1 first and then run the merge agent again with the value 2.</span></span> <span data-ttu-id="93544-194">두 매개 변수를 사용하여 병합 에이전트를 실행하는 데 실패하면 메타데이터가 삭제되고 구독을 다시 초기화해야 합니다(업로드 제외).</span><span class="sxs-lookup"><span data-stu-id="93544-194">Failure to run the merge agent with both parameters will cause metadata to be deleted and require you to reinitialize the subscription (without upload).</span></span>  
  
 <span data-ttu-id="93544-195">**-FastRowCount** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-195">**-FastRowCount** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-196">행 개수 유효성 검사에 사용할 행 개수 계산 방법의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-196">Specifies what type of rowcount calculation method should be used for rowcount validation.</span></span> <span data-ttu-id="93544-197">값 **1** (기본값)은 빠른 행 개수 계산 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-197">A value of **1** (default) indicates the fast method.</span></span> <span data-ttu-id="93544-198">값 **0** 은 전체 행 개수 계산 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-198">A value of **0** indicates the full rowcount method.</span></span>  
  
 <span data-ttu-id="93544-199">**-FileTransferType** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-199">**-FileTransferType** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-200">파일 전송 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-200">Specifies the file transfer type.</span></span> <span data-ttu-id="93544-201">값 **0** 은 UNC(Universal Naming Convention)를 나타내고, 값 **1** 은 FTP(File Transfer Protocol)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-201">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="93544-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span><span class="sxs-lookup"><span data-stu-id="93544-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span></span>  
 <span data-ttu-id="93544-203">병합 에이전트에서 사용할 일치성 수준을 지정하며 값은 다음 중 하나가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-203">Specifies the level of convergence the Merge Agent should use, and can be one of the following:</span></span>  
  
|<span data-ttu-id="93544-204">ForceConvergenceLevel 값</span><span class="sxs-lookup"><span data-stu-id="93544-204">ForceConvergenceLevel value</span></span>|<span data-ttu-id="93544-205">Description</span><span class="sxs-lookup"><span data-stu-id="93544-205">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="93544-206">**0** (기본값)</span><span class="sxs-lookup"><span data-stu-id="93544-206">**0** (default)</span></span>|<span data-ttu-id="93544-207">기본값</span><span class="sxs-lookup"><span data-stu-id="93544-207">Default.</span></span> <span data-ttu-id="93544-208">추가 일치 작업 없이 표준 병합을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-208">Perform a standard merge without additional convergence.</span></span>|  
|<span data-ttu-id="93544-209">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-209">**1**</span></span>|<span data-ttu-id="93544-210">모든 세대에 대해 일치 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-210">Force convergence for all generations.</span></span>|  
|<span data-ttu-id="93544-211">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-211">**2**</span></span>|<span data-ttu-id="93544-212">모든 세대에 대해 일치 작업을 수행하고 손상된 계보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-212">Force convergence for all generations and correct corrupt lineages.</span></span> <span data-ttu-id="93544-213">이 값을 지정할 경우 계보를 수정할 위치를 게시자, 구독자 또는 게시자와 구독자 모두로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-213">When specifying this value, specify where lineages should be corrected: the Publisher, the Subscriber, or both the Publisher and the Subscriber.</span></span>|  
  
 <span data-ttu-id="93544-214">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="93544-214">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="93544-215">배포자용 FTP 서비스의 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-215">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="93544-216">지정되지 않은 경우, **Distributor** 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-216">When not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="93544-217">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="93544-217">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="93544-218">FTP 서비스에 연결할 때 사용되는 사용자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-218">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="93544-219">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="93544-219">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="93544-220">배포자용 FTP 서비스의 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-220">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="93544-221">지정되지 않은 경우, FTP 서비스용 기본 포트 번호(21)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-221">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="93544-222">**-FtpUserName** _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="93544-222">**-FtpUserName** _ftp_user_name_</span></span>  
 <span data-ttu-id="93544-223">FTP 서비스에 연결할 때 사용할 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-223">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="93544-224">지정되지 않은 경우, anonymous가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-224">When not specified, anonymous is used.</span></span>  
  
 <span data-ttu-id="93544-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="93544-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="93544-226">병합 작업을 수행하는 동안 기록에 추가되는 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-226">Specifies the amount of history logged during a merge operation.</span></span> <span data-ttu-id="93544-227">**1**을 선택하여 성능에서 기록 로깅의 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-227">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="93544-228">HistoryVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="93544-228">HistoryVerboseLevel value</span></span>|<span data-ttu-id="93544-229">Description</span><span class="sxs-lookup"><span data-stu-id="93544-229">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="93544-230">**0**</span><span class="sxs-lookup"><span data-stu-id="93544-230">**0**</span></span>|<span data-ttu-id="93544-231">최종 에이전트 상태 메시지, 최종 세션 정보 및 기타 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-231">Log the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="93544-232">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-232">**1**</span></span>|<span data-ttu-id="93544-233">각 세션 상태의 증분 세션 정보를 기록합니다. 여기에는 최종 에이전트 상태 메시지, 최종 세션 정보 및 오류뿐 아니라 완료율도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-233">Log incremental session details at each session status, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="93544-234">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-234">**2**</span></span>|<span data-ttu-id="93544-235">기본값</span><span class="sxs-lookup"><span data-stu-id="93544-235">Default.</span></span> <span data-ttu-id="93544-236">각 세션 상태의 증분 세션 정보와 아티클 수준 세션 정보를 기록합니다. 여기에는 최종 에이전트 상태 메시지, 최종 세션 정보 및 오류뿐 아니라 완료율도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-236">Log both incremental session details at each session status and article level session details, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span> <span data-ttu-id="93544-237">에이전트 상태 메시지도 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-237">Agent status messages are also logged.</span></span>|  
|<span data-ttu-id="93544-238">**3**</span><span class="sxs-lookup"><span data-stu-id="93544-238">**3**</span></span>|<span data-ttu-id="93544-239">기록되는 에이전트 진행 메시지가 더 많다는 점만 제외하고 **-HistoryVerboseLevel** = **2**와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-239">The same as **-HistoryVerboseLevel** = **2**, except that more agent progress messages are logged.</span></span>|  
  
 <span data-ttu-id="93544-240">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="93544-240">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="93544-241">로컬 컴퓨터의 네트워크 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-241">Is the network name of the local computer.</span></span> <span data-ttu-id="93544-242">기본값은 로컬 컴퓨터 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-242">The default is the local computer name.</span></span>  
  
 <span data-ttu-id="93544-243">**-InteractiveResolution** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-243">**-InteractiveResolution** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-244">동기화를 수행하는 동안 충돌이 발생할 경우 대화형 충돌 해결을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-244">Specifies whether interactive conflict resolution is used when a conflict occurs during synchronization.</span></span> <span data-ttu-id="93544-245">기본값은 **0**으로, 대화형 충돌 해결을 사용하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-245">The default is **0**, indicating that interactive conflict resolution is not used.</span></span>  
  
 <span data-ttu-id="93544-246">**-InternetLogin** _internet_login_</span><span class="sxs-lookup"><span data-stu-id="93544-246">**-InternetLogin** _internet_login_</span></span>  
 <span data-ttu-id="93544-247">인증이 필요한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 수신기 ISAPI DLL에 연결할 때 사용되는 로그인 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-247">Specifies the login name used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="93544-248">**-InternetPassword** _internet_password_</span><span class="sxs-lookup"><span data-stu-id="93544-248">**-InternetPassword** _internet_password_</span></span>  
 <span data-ttu-id="93544-249">인증이 필요한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 수신기 ISAPI DLL에 연결할 때 사용되는 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-249">Specifies the password used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="93544-250">**-InternetProxyLogin**  *internet_proxy_login*</span><span class="sxs-lookup"><span data-stu-id="93544-250">**-InternetProxyLogin**  *internet_proxy_login*</span></span>  
 <span data-ttu-id="93544-251">인증이 필요한 프록시 서버( *internet_proxy_server*에 정의됨)에 연결할 때 사용되는 로그인 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-251">Specifies the login name used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="93544-252">**-InternetProxyPassword**  *internet_proxy_password*</span><span class="sxs-lookup"><span data-stu-id="93544-252">**-InternetProxyPassword**  *internet_proxy_password*</span></span>  
 <span data-ttu-id="93544-253">인증이 필요한 프록시 서버( *internet_proxy_server*에 정의됨)에 연결할 때 사용되는 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-253">Specifies the password used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="93544-254">**-InternetProxyServer**  *internet_proxy_server*</span><span class="sxs-lookup"><span data-stu-id="93544-254">**-InternetProxyServer**  *internet_proxy_server*</span></span>  
 <span data-ttu-id="93544-255">*internet_url*에 지정된 HTTP 리소스에 액세스할 때 사용할 프록시 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-255">Specifies the proxy server to use when accessing the HTTP resource specified in *internet_url*.</span></span>  
  
 <span data-ttu-id="93544-256">**-InternetSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-256">**-InternetSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-257">웹 동기화를 수행하는 동안 웹 서버에 연결할 때 사용할 IIS 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-257">Specifies the IIS security mode used when connecting to the Web server during Web synchronization.</span></span> <span data-ttu-id="93544-258">값 **0** 은 기본 인증을 나타내고, 값 **1** 은 Windows 통합 인증(기본값)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-258">A value of **0** indicates Basic Authentication, and a value of **1** indicates Windows Integrated Authentication (default).</span></span>  
  
 <span data-ttu-id="93544-259">**-InternetTimeout** _internet_timeout_</span><span class="sxs-lookup"><span data-stu-id="93544-259">**-InternetTimeout** _internet_timeout_</span></span>  
 <span data-ttu-id="93544-260">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 수신기 ISAPI DLL에 대한 연결 제한 시간이 초과되기까지의 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-260">Is the number of seconds before a connection to the to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL times out.</span></span>  
  
 <span data-ttu-id="93544-261">**-InternetURL** _internet_url_</span><span class="sxs-lookup"><span data-stu-id="93544-261">**-InternetURL** _internet_url_</span></span>  
 <span data-ttu-id="93544-262">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 수신기 ISAPI DLL에 연결하는 데 사용되는 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-262">Specifies the URL used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL.</span></span> <span data-ttu-id="93544-263">이 속성은 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-263">This property must be specified.</span></span>  
  
 <span data-ttu-id="93544-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="93544-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="93544-265">기록 스레드가 기존 연결에서 서버의 응답을 기다리고 있는지 확인할 때까지 걸리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-265">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="93544-266">이 값을 줄이면 장기 실행 일괄 처리를 실행할 때 점검 에이전트에서 병합 에이전트를 주의 대상으로 표시하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-266">This value can be decreased to avoid having the checkup agent mark the Merge Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="93544-267">기본값은 **300** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-267">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="93544-268">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="93544-268">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="93544-269">로그인 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 **15** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-269">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="93544-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="93544-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span></span>  
 <span data-ttu-id="93544-271">생성 만들기 또는 클라이언트에 다운로드할 변경 내용의 일괄 처리 간에 대기하는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-271">Is the number of seconds to wait between creating generations, or batches of changes, to download to the client.</span></span> <span data-ttu-id="93544-272">기본값은 **1** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-272">The default is **1** second.</span></span>  
  
 <span data-ttu-id="93544-273">makegeneration은 게시자 변경 내용을 구독자로 다운로드하기 위해 준비하는 프로세스로, 다운로드하는 동안 성능 병목 상태를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-273">Makegeneration is the process that prepares Publisher changes to be downloaded to Subscribers, and it can be a performance bottleneck during downloads.</span></span> <span data-ttu-id="93544-274">makegeneration 프로세스는 **-MakeGenerationInterval**에 지정된 간격 내에서 이미 실행된 경우 현재 동기화 세션에서 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-274">If the makegeneration process already ran within the interval specified by **-MakeGenerationInterval**, the process is skipped for the current synchronization session.</span></span> <span data-ttu-id="93544-275">이는 동기화 동시성에 도움이 되며, 구독자가 변경 내용을 다운로드하지 않으려는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-275">This can benefit synchronization concurrency and is especially helpful if Subscribers do not expect to download changes.</span></span>  
  
 <span data-ttu-id="93544-276">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="93544-276">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="93544-277">병렬로 수행할 수 있는 대량 복사 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-277">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="93544-278">동시에 존재하는 스레드 및 ODBC 연결의 최대 개수는 **MaxBcpThreads** 와 게시 데이터베이스의 시스템 테이블 **sysmergeschemachange** 에 나타나는 대량 복사 요청 수 중 더 작은 값입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-278">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the system table **sysmergeschemachange** in the publication database.</span></span> <span data-ttu-id="93544-279">**MaxBcpThreads** 값은 0보다 크고 하드 코딩된 상한값이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-279">**MaxBcpThreads** must have a value greater than 0 and has no hard-coded upper limit.</span></span> <span data-ttu-id="93544-280">기본값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-280">The default is **1**.</span></span>  
  
 <span data-ttu-id="93544-281">**-MaxDownloadChanges** _number_of_download_changes_</span><span class="sxs-lookup"><span data-stu-id="93544-281">**-MaxDownloadChanges** _number_of_download_changes_</span></span>  
 <span data-ttu-id="93544-282">게시자에서 구독자로 다운로드할 변경된 행의 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-282">Specifies the maximum number of changed rows that should be downloaded from the Publisher to the Subscriber.</span></span> <span data-ttu-id="93544-283">다운로드되는 행 수가 지정된 최대값보다 클 수도 있습니다. 전체 세대가 처리되는 경우나, 병렬 대상 스레드가 실행될 수 있고 각 스레드가 첫 번째 전달에서 100개 이상의 변경 내용을 처리하는 경우가 이러한 경우에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-283">The number of rows downloaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="93544-284">기본적으로 다운로드할 수 있는 모든 변경 내용이 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="93544-284">By default all changes that are ready to be downloaded are sent.</span></span>  
  
 <span data-ttu-id="93544-285">**-MaxUploadChanges** _number_of_upload_changes_</span><span class="sxs-lookup"><span data-stu-id="93544-285">**-MaxUploadChanges** _number_of_upload_changes_</span></span>  
 <span data-ttu-id="93544-286">구독자에서 게시자로 업로드할 변경된 행의 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-286">Specifies the maximum number of changed rows that should be uploaded from the Subscriber to the Publisher.</span></span> <span data-ttu-id="93544-287">업로드되는 행 수가 지정된 최대값보다 클 수도 있습니다. 전체 세대가 처리되는 경우나, 병렬 대상 스레드가 실행될 수 있고 각 스레드가 첫 번째 전달에서 100개 이상의 변경 내용을 처리하는 경우가 이러한 경우에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-287">The number of rows uploaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="93544-288">기본적으로 업로드할 수 있는 모든 변경 내용이 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="93544-288">By default all changes that are ready to be uploaded are sent.</span></span>  
  
 <span data-ttu-id="93544-289">**-MetadataRetentionCleanup** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-289">**-MetadataRetentionCleanup** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-290">게시 보존 기간에 따라 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)및 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 에서 메타데이터를 제거할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-290">Specifies if metadata is removed from [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) based on the publication retention period.</span></span> <span data-ttu-id="93544-291">기본값은 **1**로서, 정리를 수행함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-291">The default is **1**, indicating that cleanup should occur.</span></span> <span data-ttu-id="93544-292">값 **0** 은 정리를 자동으로 수행하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-292">A value of **0** indicates that cleanup should not occur automatically.</span></span>  
  
 <span data-ttu-id="93544-293">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="93544-293">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="93544-294">에이전트 출력 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-294">Is the path of the agent output file.</span></span> <span data-ttu-id="93544-295">파일 이름을 지정하지 않으면 출력이 콘솔로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-295">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="93544-296">지정된 파일 이름이 존재하면 출력이 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-296">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="93544-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span><span class="sxs-lookup"><span data-stu-id="93544-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span></span>  
 <span data-ttu-id="93544-298">출력이 자세해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-298">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="93544-299">정보 표시 수준이 **0**이면 오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-299">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="93544-300">정보 표시 수준이 **1**이면 모든 진행률 보고 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-300">If the verbose level is **1**, all of the progress report messages are printed.</span></span> <span data-ttu-id="93544-301">정보 표시 수준이 **2** (기본값)이면 디버깅에 유용한 오류 메시지와 진행률 보고 메시지가 모두 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-301">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="93544-302">**-ParallelUploadDownload** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-302">**-ParallelUploadDownload** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-303">병합 에이전트에서 게시자에 업로드되는 변경 내용과 구독자에 다운로드되는 변경 내용을 병렬로 처리할지 여부를 지정합니다. 병렬 처리는 네트워크 대역폭이 높은 대규모 환경에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-303">Specifies whether the Merge Agent should process in parallel the changes uploaded to the Publisher and those downloaded to the Subscriber, which is useful in high volume environments with high network bandwidth.</span></span> <span data-ttu-id="93544-304">**ParallelUploadDownload** 가 **1**이면 병렬 처리가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-304">If **ParallelUploadDownload** is **1**, then parallel processing is enabled.</span></span>  
  
 <span data-ttu-id="93544-305">**-PacketSize**</span><span class="sxs-lookup"><span data-stu-id="93544-305">**-PacketSize**</span></span>  
 <span data-ttu-id="93544-306">패킷 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-306">Is the packet size, in bytes.</span></span> <span data-ttu-id="93544-307">기본값은 4096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-307">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="93544-308">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="93544-308">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="93544-309">게시자 또는 구독자에서 데이터 변경 내용을 쿼리하는 빈도(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-309">Is how often, in seconds, the Publisher or Subscriber is queried for data changes.</span></span> <span data-ttu-id="93544-310">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-310">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="93544-311">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="93544-311">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="93544-312">에이전트 매개 변수에 사용할 에이전트 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-312">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="93544-313">**ProfileName** 이 NULL이면 에이전트 프로필이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-313">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="93544-314">**ProfileName** 이 지정되지 않으면 에이전트 유형에 대한 기본 프로필이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-314">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="93544-315">자세한 내용은 [복제 에이전트 프로필](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93544-315">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="93544-316">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="93544-316">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="93544-317">게시 데이터베이스와 함께 데이터베이스 미러링 세션에 참여하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 장애 조치 파트너 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-317">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="93544-318">자세한 내용은 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93544-318">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="93544-319">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="93544-319">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="93544-320">게시자 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-320">Is the Publisher login name.</span></span> <span data-ttu-id="93544-321">**PublisherSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-321">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="93544-322">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="93544-322">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="93544-323">게시자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-323">Is the Publisher password.</span></span> <span data-ttu-id="93544-324">**PublisherSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-324">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="93544-325">**-PublisherSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="93544-325">**-PublisherSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="93544-326">게시자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-326">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="93544-327">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증(기본값)을 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-327">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="93544-328">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="93544-328">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="93544-329">쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 300초입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-329">Is the number of seconds before the query times out. The default is 300 seconds.</span></span> <span data-ttu-id="93544-330">`QueryTimeout` 값이 1800보다 클 경우 병합 에이전트에서는 이 값을 사용하여 분할된 스냅샷이 생성되기를 기다릴 시간을 결정하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-330">The Merge Agent also uses the value of `QueryTimeout` to determine how long to wait for generation of a partitioned snapshot when this value is greater than 1800.</span></span>  
  
 <span data-ttu-id="93544-331">**-SrcThreads** _number_of_source_threads_</span><span class="sxs-lookup"><span data-stu-id="93544-331">**-SrcThreads** _number_of_source_threads_</span></span>  
 <span data-ttu-id="93544-332">병합 에이전트에서 원본의 변경 내용을 열거하는 데 사용하는 원본 스레드의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-332">Specifies the number of source threads that the Merge Agent uses to enumerate changes from the source.</span></span> <span data-ttu-id="93544-333">업로드 중에는 구독자가 원본이 되고 다운로드 중에는 게시자가 원본이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-333">The source is the Subscriber during upload and the Publisher during download.</span></span> <span data-ttu-id="93544-334">기본값은 **3**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-334">The default is **3**.</span></span>  
  
 <span data-ttu-id="93544-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="93544-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="93544-336">실행 중인 동시 병합 프로세스의 수가 **@max_concurrent_merge** **sp_addmergepublication**의 속성으로 설정 된 제한에 도달 하는 경우 병합 에이전트 대기 하는 최대 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-336">Is the maximum number of seconds that the Merge Agent waits when the number of concurrent merge processes running is at the limit set by the **@max_concurrent_merge** property of **sp_addmergepublication**.</span></span> <span data-ttu-id="93544-337">최대 시간(초)에 도달한 경우 병합 에이전트가 계속 대기 중이면 해당 병합 에이전트가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-337">If the maximum number of seconds is reached and the Merge Agent is still waiting, it will exit.</span></span> <span data-ttu-id="93544-338">값 0은 에이전트가 취소될 경우에도 무기한 대기함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-338">A value of 0 means that the agent waits indefinitely, although it can be cancelled.</span></span>  
  
 <span data-ttu-id="93544-339">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="93544-339">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="93544-340">**SubscriberType** 이 **2** 로서, ODBC DSN(데이터 원본 이름)이 없는 Jet 데이터베이스에 대한 연결이 허용되는 경우 Jet 데이터베이스(.mdb 파일)의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-340">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="93544-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="93544-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="93544-342">기존 구독자 데이터베이스가 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-342">Specifies whether there is an existing Subscriber database.</span></span>  
  
|<span data-ttu-id="93544-343">SubscriberDBAddOption 값</span><span class="sxs-lookup"><span data-stu-id="93544-343">SubscriberDBAddOption value</span></span>|<span data-ttu-id="93544-344">Description</span><span class="sxs-lookup"><span data-stu-id="93544-344">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="93544-345">**0**</span><span class="sxs-lookup"><span data-stu-id="93544-345">**0**</span></span>|<span data-ttu-id="93544-346">기존 데이터베이스를 사용합니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="93544-346">Use the existing database (default).</span></span>|  
|<span data-ttu-id="93544-347">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-347">**1**</span></span>|<span data-ttu-id="93544-348">비어 있는 새 구독자 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93544-348">Create a new, empty Subscriber database.</span></span>|  
|<span data-ttu-id="93544-349">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-349">**2**</span></span>|<span data-ttu-id="93544-350">새 데이터베이스를 만들어 지정된 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-350">Create a new database and attach it to the specified file.</span></span>|  
|<span data-ttu-id="93544-351">**3**</span><span class="sxs-lookup"><span data-stu-id="93544-351">**3**</span></span>|<span data-ttu-id="93544-352">새 데이터베이스를 만들어 연결하고 해당 파일에 있을 수 있는 모든 구독을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-352">Create a new database, attach the database, and enable all subscriptions that might exist at the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="93544-353">값 **2** 와 **3**을 사용할 경우에는 **SubscriberDatabasePath** 옵션에서 구독자의 데이터베이스 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-353">When you use values **2** and **3**, the database path for the Subscriber must be specified in the **SubscriberDatabasePath** option.</span></span>  
  
 <span data-ttu-id="93544-354">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="93544-354">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="93544-355">구독자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-355">Is the Subscriber login name.</span></span> <span data-ttu-id="93544-356">**SubscriberSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-356">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="93544-357">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="93544-357">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="93544-358">구독자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-358">Is the Subscriber password.</span></span> <span data-ttu-id="93544-359">**SubscriberSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-359">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="93544-360">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="93544-360">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="93544-361">구독자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-361">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="93544-362">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증(기본값)을 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-362">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="93544-363">**-SubscriberConflictClean** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="93544-363">**-SubscriberConflictClean** [ **0**| **1**]</span></span>  
 <span data-ttu-id="93544-364">동기화 프로세스를 수행하는 동안 구독자에서 충돌 테이블을 정리할지 여부를 나타냅니다. 값 **1** 은 구독자의 충돌 테이블이 정리됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-364">Is if conflict tables are cleaned-up at the Subscriber during the synchronization process, where a value of **1** indicates that conflict tables at the Subscriber are cleaned-up.</span></span> <span data-ttu-id="93544-365">이 매개 변수는 분산 충돌 로깅을 사용하는 게시자에 대한 구독에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-365">This parameter is used only for subscriptions to publications with decentralized conflict logging.</span></span>  
  
 <span data-ttu-id="93544-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span><span class="sxs-lookup"><span data-stu-id="93544-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span></span>  
 <span data-ttu-id="93544-367">병합 에이전트에서 사용하는 구독자 연결 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-367">Specifies the type of Subscriber connection used by the Merge Agent.</span></span> <span data-ttu-id="93544-368">이 매개 변수에는 기본값 **0** 만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-368">Only the default value of **0** is supported for this parameter.</span></span>  
  
 <span data-ttu-id="93544-369">**-SubscriptionType**[ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="93544-369">**-SubscriptionType**[ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="93544-370">배포의 구독 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-370">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="93544-371">값 **0** 은 밀어넣기 구독(기본값)을, 값 **1** 은 끌어오기 구독을, 값 **2** 는 익명 구독을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-371">A value of **0** indicates a push subscription (default), a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="93544-372">**-SyncToAlternate** [ **0|1**]</span><span class="sxs-lookup"><span data-stu-id="93544-372">**-SyncToAlternate** [ **0|1**]</span></span>  
 <span data-ttu-id="93544-373">병합 에이전트에서 구독자와 대체 게시자 간의 동기화를 수행하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-373">Specifies whether the Merge Agent is synchronizing between a Subscriber and an alternate Publisher.</span></span> <span data-ttu-id="93544-374">값 **1** 은 동기화 대상이 대체 게시자임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93544-374">A value of **1** indicates that it is an alternate Publisher.</span></span> <span data-ttu-id="93544-375">기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-375">The default is **0**.</span></span>  
  
 <span data-ttu-id="93544-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span></span>  
 <span data-ttu-id="93544-377">구독자의 변경 내용을 게시자로 업로드하는 동안 한 번의 일괄 처리에서 처리할 세대 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-377">Is the number of generations to be processed in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="93544-378">세대는 아티클 단위의 논리적 변경 내용 그룹으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="93544-378">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="93544-379">안정적인 통신 연결의 기본값은 **100**이고,</span><span class="sxs-lookup"><span data-stu-id="93544-379">The default for a reliable communication link is **100**.</span></span> <span data-ttu-id="93544-380">안정적이지 않은 통신 연결의 기본값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-380">The default for an unreliable communication link is **1**.</span></span>  
  
 <span data-ttu-id="93544-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span></span>  
 <span data-ttu-id="93544-382">구독자의 변경 내용을 게시자로 업로드하는 동안 한 번의 일괄 처리에서 읽을 변경 내용 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-382">Is the number of changes to be read in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="93544-383">기본값은 **100**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-383">The default is **100**.</span></span>  
  
 <span data-ttu-id="93544-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="93544-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span></span>  
 <span data-ttu-id="93544-385">구독자의 변경 내용을 게시자로 업로드하는 동안 한 번의 일괄 처리에서 적용할 변경 내용 수입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-385">Is the number of changes to be applied in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="93544-386">기본값은 **100**입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-386">The default is **100**.</span></span>  
  
 <span data-ttu-id="93544-387">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="93544-387">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="93544-388">병합 에이전트에서 구독자에 스냅샷 파일을 적용할 때 BULK INSERT 명령을 사용하도록 지정하여 초기 스냅샷의 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="93544-388">Improves the performance of the initial snapshot by causing the Merge Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="93544-389">이 매개 변수는 XML 데이터 형식과 호환되지 않으므로 이후에는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-389">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="93544-390">XML 데이터를 복제하지 않을 계획이라면 이 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-390">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="93544-391">이 매개 변수는 문자 모드 스냅샷과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-391">This parameter cannot be used with character mode snapshots.</span></span> <span data-ttu-id="93544-392">이 매개 변수를 사용하려면 구독자의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정에 스냅샷 .bcp 데이터 파일이 있는 디렉터리에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-392">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="93544-393">이 매개 변수를 사용하지 않으면 에이전트에서 로드한 ODBC 드라이버가 파일 내용을 읽으므로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정의 보안 컨텍스트가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-393">When this parameter is not used, the ODBC driver loaded by the agent reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="93544-394">**-Validate** [**0**|**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="93544-394">**-Validate** [**0**|**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="93544-395">병합 세션이 종료될 때 유효성 검사를 수행할지 여부와 수행할 유효성 검사 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-395">Specifies whether validation should be done at the end of the merge session, and, if so, what type of validation.</span></span> <span data-ttu-id="93544-396">값 **3** 이 권장 값입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-396">The value of **3** is the recommended value.</span></span>  
  
|<span data-ttu-id="93544-397">값 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="93544-397">Validate value</span></span>|<span data-ttu-id="93544-398">Description</span><span class="sxs-lookup"><span data-stu-id="93544-398">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="93544-399">**0** (기본값)</span><span class="sxs-lookup"><span data-stu-id="93544-399">**0** (default)</span></span>|<span data-ttu-id="93544-400">유효성 검사를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-400">No validation.</span></span>|  
|<span data-ttu-id="93544-401">**1**</span><span class="sxs-lookup"><span data-stu-id="93544-401">**1**</span></span>|<span data-ttu-id="93544-402">행 개수의 유효성만 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-402">Rowcount-only validation.</span></span>|  
|<span data-ttu-id="93544-403">**2**</span><span class="sxs-lookup"><span data-stu-id="93544-403">**2**</span></span>|<span data-ttu-id="93544-404">행 개수 및 체크섬의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-404">Rowcount and checksum validation.</span></span>|  
|<span data-ttu-id="93544-405">**3**</span><span class="sxs-lookup"><span data-stu-id="93544-405">**3**</span></span>|<span data-ttu-id="93544-406">행 개수 및 이진 체크섬의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-406">Rowcount and binary checksum validation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="93544-407">구독자에서의 데이터 형식과 게시자에서의 데이터 형식이 다른 경우 이진 체크섬 또는 체크섬 유효성 검사가 올바르지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-407">Validation by using binary checksum or checksum can incorrectly report a failure if data types are different at the Subscriber than they are at the Publisher.</span></span> <span data-ttu-id="93544-408">자세한 내용은 [복제된 데이터의 유효성 검사](../validate-data-at-the-subscriber.md)의 "데이터 유효성 검사에 대한 고려 사항" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93544-408">For more information, see the section "Considerations for Data Validation" in [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="93544-409">**-ValidateInterval** _validate_interval_</span><span class="sxs-lookup"><span data-stu-id="93544-409">**-ValidateInterval** _validate_interval_</span></span>  
 <span data-ttu-id="93544-410">연속 모드에서 구독 유효성 검사가 수행되는 빈도(분)입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-410">Is how often, in minutes, the subscription is validated in continuous mode.</span></span> <span data-ttu-id="93544-411">기본값은 **60** 분입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-411">The default is **60** minutes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93544-412">설명</span><span class="sxs-lookup"><span data-stu-id="93544-412">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93544-413">도메인 사용자 계정(기본값)이 아닌 로컬 시스템 계정에서 실행되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 설치한 경우 해당 서비스에서는 로컬 컴퓨터에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-413">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="93544-414">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트에서 실행되는 병합 에이전트가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로그인할 때 Windows 인증 모드를 사용하도록 구성된 경우 해당 병합 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-414">If the Merge Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Merge Agent fails.</span></span> <span data-ttu-id="93544-415">기본 설정은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="93544-415">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="93544-416">병합 에이전트를 시작하려면 명령 프롬프트에서 **replmerg.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="93544-416">To start the Merge Agent, execute **replmerg.exe** from the command prompt.</span></span> <span data-ttu-id="93544-417">자세한 내용은 [복제 에이전트 실행 파일](../concepts/replication-agent-executables-concepts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="93544-417">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
 <span data-ttu-id="93544-418">연속 모드에서 실행하는 동안 현재 세션에 대한 병합 에이전트 기록은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-418">The merge agent history for the current session is not removed while running in continuous mode.</span></span> <span data-ttu-id="93544-419">장기 실행 에이전트로 인해 성능에 영향을 미칠 수 있는 병합 기록 테이블에 다수의 항목이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93544-419">A long running agent can result in a large number of entries in the merge history tables which could impact performance.</span></span> <span data-ttu-id="93544-420">이 문제를 해결하려면 예약 모드로 전환하거나, 계속해서 연속 모드를 사용하지만 정기적으로 병합 에이전트를 다시 시작하는 전용 작업을 만들거나, 기록 수준의 자세한 정도를 줄여 행 수를 줄임으로써 성능에 미치는 영향을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="93544-420">To resolve this problem switch to scheduled mode, or continue to use continuous mode but create a dedicated job to periodically restart the merge agent, or reduce the verbosity of the history level to reduce the number of rows and therefor reduce the performance impact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93544-421">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93544-421">See Also</span></span>  
 [<span data-ttu-id="93544-422">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="93544-422">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
