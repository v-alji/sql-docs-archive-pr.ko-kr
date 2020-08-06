---
title: 복제 배포 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, executables
- agents [SQL Server replication], Distribution Agent
- Distribution Agent, parameter reference
- command prompt [SQL Server replication]
ms.assetid: 7b4fd480-9eaf-40dd-9a07-77301e44e2ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5bd0b61626f4af268f93043114d5945d00a37b5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650919"
---
# <a name="replication-distribution-agent"></a><span data-ttu-id="56563-102">복제 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="56563-102">Replication Distribution Agent</span></span>
  <span data-ttu-id="56563-103">복제 배포 에이전트는 스냅샷(스냅샷 복제 및 트랜잭션 복제의 경우) 및 배포 데이터베이스 테이블에 저장된 트랜잭션(트랜잭션 배포의 경우)을 구독자의 대상 테이블로 이동하는 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-103">The Replication Distribution Agent is an executable that moves the snapshot (for snapshot replication and transactional replication) and the transactions held in the distribution database tables (for transactional replication) to the destination tables at the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56563-104">매개 변수는 지정되는 순서에 제한을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="56563-105">선택적 매개 변수가 지정되지 않은 경우 로컬 컴퓨터의 미리 정의된 레지스트리 설정 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-105">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56563-106">구문</span><span class="sxs-lookup"><span data-stu-id="56563-106">Syntax</span></span>  
  
```  
  
      distrib [-?]  
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database   
[-AltSnapshotFolderalt_snapshot_folder_path]   
[-BcpBatchSizebcp_batch_size]  
[-CommitBatchSizecommit_batch_size]  
[-CommitBatchThresholdcommit_batch_threshold]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributordistributor]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ErrorFileerror_path_and_file_name]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-FileTransferType [0|1]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]   
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreads]  
[-MaxDeliveredTransactionsnumber_of_transactions]  
[-MessageIntervalmessage_interval]  
[-OledbStreamThresholdoledb_stream_threshold]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-Publicationpublication]  
[-QueryTimeOutquery_time_out_seconds]  
[-QuotedIdentifierquoted_identifier]  
[-SkipErrorsnative_error_id [:...n]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password]  
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|3]]  
[-SubscriptionStreams [1|2|...64]]  
[-SubscriptionTableNamesubscription_table]  
[-SubscriptionType [0|1|2]]  
[-TransactionsPerHistory [0|1|...10000]]  
[-UseDTS]  
[-UseInprocLoader]  
[-UseOledbStreaming]  
```  
  
## <a name="arguments"></a><span data-ttu-id="56563-107">인수</span><span class="sxs-lookup"><span data-stu-id="56563-107">Arguments</span></span>  
 <span data-ttu-id="56563-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="56563-108">**-?**</span></span>  
 <span data-ttu-id="56563-109">사용 가능한 모든 매개 변수를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-109">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="56563-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="56563-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="56563-111">게시자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-111">Is the name of the Publisher.</span></span> <span data-ttu-id="56563-112">해당 서버에 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스에 대해 *server_name*을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="56563-113">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="56563-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="56563-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="56563-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="56563-115">게시자 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="56563-116">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="56563-116">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="56563-117">구독자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-117">Is the name of the Subscriber.</span></span> <span data-ttu-id="56563-118">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-118">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="56563-119">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="56563-119">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="56563-120">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="56563-120">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="56563-121">구독자 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-121">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="56563-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="56563-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="56563-123">구독에 대한 초기 스냅샷이 들어 있는 폴더의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-123">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="56563-124">**-BcpBatchSize** _bcp_batch_size_</span><span class="sxs-lookup"><span data-stu-id="56563-124">**-BcpBatchSize** _bcp_batch_size_</span></span>  
 <span data-ttu-id="56563-125">대량 복사 작업에서 보낼 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-125">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="56563-126">**bcp in** 작업을 수행하는 경우 일괄 처리 크기는 한 번의 트랜잭션으로 서버에 보낼 행 수이며 배포 에이전트가 **bcp** 진행 메시지를 기록하기 전에 보내야 하는 행 수이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-126">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="56563-127">**bcp out** 작업을 수행하는 경우 고정 일괄 처리 크기로 **1000** 이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-127">When performing a **bcp out** operation, a fixed batch size of **1000** is used.</span></span>  
  
 <span data-ttu-id="56563-128">**-CommitBatchSize** _commit_batch_size_</span><span class="sxs-lookup"><span data-stu-id="56563-128">**-CommitBatchSize** _commit_batch_size_</span></span>  
 <span data-ttu-id="56563-129">COMMIT 문을 실행하기 전에 구독자에 대해 실행할 트랜잭션의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-129">Is the number of transactions to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="56563-130">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-130">The default is 100.</span></span>  
  
 <span data-ttu-id="56563-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span><span class="sxs-lookup"><span data-stu-id="56563-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span></span>  
 <span data-ttu-id="56563-132">COMMIT 문을 실행하기 전에 구독자에 대해 실행할 복제 명령의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-132">Is the number of replication commands to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="56563-133">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-133">The default is 1000.</span></span>  
  
 <span data-ttu-id="56563-134">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="56563-134">**-Continuous**</span></span>  
 <span data-ttu-id="56563-135">에이전트에서 복제된 트랜잭션의 폴링을 계속 시도할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-135">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="56563-136">이 인수가 지정된 경우 에이전트는 보류 중인 트랜잭션이 없는 경우에도 원본의 복제된 트랜잭션을 폴링 간격에 따라 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-136">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="56563-137">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="56563-137">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="56563-138">에이전트 정의 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-138">Is the path of the agent definition file.</span></span> <span data-ttu-id="56563-139">에이전트 정의 파일에는 에이전트의 명령 프롬프트 인수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-139">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="56563-140">파일 내용은 실행 파일로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-140">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="56563-141">임의 문자가 있는 인수 값을 지정하려면 큰따옴표(")를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-141">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="56563-142">**-Distributor** _distributor_</span><span class="sxs-lookup"><span data-stu-id="56563-142">**-Distributor** _distributor_</span></span>  
 <span data-ttu-id="56563-143">배포자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-143">Is the Distributor name.</span></span> <span data-ttu-id="56563-144">배포자(밀어넣기) 배포의 경우에는 로컬 배포자의 이름이 기본 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-144">For Distributor (push) distribution, the name defaults to the name of the local Distributor.</span></span>  
  
 <span data-ttu-id="56563-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="56563-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="56563-146">배포자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="56563-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="56563-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="56563-148">배포자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="56563-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="56563-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="56563-150">배포자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="56563-151">값 0은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 모드를 나타내고 값 1은 Windows 인증 모드(기본값)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-151">A value of 0 indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode, and a value of 1 indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="56563-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="56563-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="56563-153">연결을 만들 때 배포 에이전트에서 사용하는 SSL(Secure Sockets Layer) 암호화의 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-153">Is the level of Secure Sockets Layer (SSL) encryption used by the Distribution Agent when making connections.</span></span>  
  
|<span data-ttu-id="56563-154">EncryptionLevel 값</span><span class="sxs-lookup"><span data-stu-id="56563-154">EncryptionLevel value</span></span>|<span data-ttu-id="56563-155">Description</span><span class="sxs-lookup"><span data-stu-id="56563-155">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="56563-156">**0**</span><span class="sxs-lookup"><span data-stu-id="56563-156">**0**</span></span>|<span data-ttu-id="56563-157">SSL이 사용되지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-157">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="56563-158">**1**</span><span class="sxs-lookup"><span data-stu-id="56563-158">**1**</span></span>|<span data-ttu-id="56563-159">SSL이 사용되지만 에이전트에서 SSL 서버 인증서가 트러스트된 발급자에 의해 서명된 것인지 확인하지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-159">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="56563-160">**2**</span><span class="sxs-lookup"><span data-stu-id="56563-160">**2**</span></span>|<span data-ttu-id="56563-161">SSL이 사용되고 인증서가 확인됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-161">Specifies that SSL is used, and that the certificate is verified.</span></span>|  
 
 > [!NOTE]  
 >  <span data-ttu-id="56563-162">유효한 SSL 인증서는 SQL Server의 정규화된 도메인 이름으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-162">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="56563-163">-EncryptionLevel을 2로 설정할 때 에이전트가 성공적으로 연결되도록 하려면 로컬 SQL Server에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="56563-163">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="56563-164">'별칭 이름' 매개 변수는 서버 이름이어야 하며 '서버' 매개 변수는 SQL Server의 정규화된 이름으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-164">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>

 <span data-ttu-id="56563-165">자세한 내용은 [SQL Server 복제 보안](../security/view-and-modify-replication-security-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56563-165">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="56563-166">**-ErrorFile** _error_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="56563-166">**-ErrorFile** _error_path_and_file_name_</span></span>  
 <span data-ttu-id="56563-167">배포 에이전트에서 생성한 오류 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-167">Is the path and file name of the error file generated by the Distribution Agent.</span></span> <span data-ttu-id="56563-168">이 파일은 구독자에서 복제 트랜잭션을 적용하는 동안 오류가 발생할 때마다 생성되며 게시자나 배포자에서 발생한 오류는 이 파일에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-168">This file is generated at any point where failure occurred while applying replication transactions at the Subscriber; errors that occur at the Publisher or Distributor are not logged in this file.</span></span> <span data-ttu-id="56563-169">이 파일에는 실패한 복제 트랜잭션 및 관련 오류 메시지가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-169">This file contains the failed replication transactions and associated error messages.</span></span> <span data-ttu-id="56563-170">지정하지 않으면 오류 파일이 배포 에이전트의 현재 디렉터리에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-170">When not specified, the error file is generated in the current directory of the Distribution Agent.</span></span> <span data-ttu-id="56563-171">오류 파일 이름은 배포 에이전트의 이름에 .err 확장명을 붙인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-171">The error file name is the name of the Distribution Agent with an .err extension.</span></span> <span data-ttu-id="56563-172">지정된 파일 이름이 존재하면 오류 메시지가 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-172">If the specified file name exists, error messages are appended to the file.</span></span> <span data-ttu-id="56563-173">이 매개 변수는 최대 256개의 유니코드 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-173">This parameter can be a maximum of 256 Unicode characters.</span></span>  
  
 <span data-ttu-id="56563-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="56563-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="56563-175">확장 이벤트 XML 구성 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-175">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="56563-176">확장 이벤트 구성 파일에서는 세션을 구성하고 추적 이벤트를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-176">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="56563-177">**-FileTransferType** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="56563-177">**-FileTransferType** [ **0**| **1**]</span></span>  
 <span data-ttu-id="56563-178">파일 전송 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-178">Specifies the file transfer type.</span></span> <span data-ttu-id="56563-179">값 **0** 은 UNC(Universal Naming Convention)를 나타내고, 값 **1** 은 FTP(File Transfer Protocol)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-179">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="56563-180">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="56563-180">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="56563-181">배포자용 FTP 서비스의 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-181">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="56563-182">지정되지 않은 경우, **DistributorAddress** 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-182">When not specified, **DistributorAddress** is used.</span></span> <span data-ttu-id="56563-183">**DistributorAddress** 가 지정되지 않은 경우 **Distributor** 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-183">If **DistributorAddress** is not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="56563-184">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="56563-184">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="56563-185">FTP 서비스에 연결할 때 사용되는 사용자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-185">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="56563-186">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="56563-186">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="56563-187">배포자용 FTP 서비스의 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-187">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="56563-188">지정되지 않은 경우, FTP 서비스용 기본 포트 번호(21)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-188">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="56563-189">**-FtpUserName**  _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="56563-189">**-FtpUserName**  _ftp_user_name_</span></span>  
 <span data-ttu-id="56563-190">FTP 서비스에 연결할 때 사용할 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-190">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="56563-191">지정되지 않은 경우, **anonymous** 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-191">When not specified, **anonymous** is used.</span></span>  
  
 <span data-ttu-id="56563-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span><span class="sxs-lookup"><span data-stu-id="56563-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span></span>  
 <span data-ttu-id="56563-193">배포 작업을 수행하는 동안 기록에 추가되는 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-193">Specifies the amount of history logged during a distribution operation.</span></span> <span data-ttu-id="56563-194">**1**을 선택하여 기록 로깅이 성능에 주는 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-194">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="56563-195">HistoryVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="56563-195">HistoryVerboseLevel value</span></span>|<span data-ttu-id="56563-196">Description</span><span class="sxs-lookup"><span data-stu-id="56563-196">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="56563-197">**0**</span><span class="sxs-lookup"><span data-stu-id="56563-197">**0**</span></span>|<span data-ttu-id="56563-198">진행 메시지를 콘솔이나 출력 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="56563-198">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="56563-199">기록 레코드는 배포 데이터베이스에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-199">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="56563-200">**1**</span><span class="sxs-lookup"><span data-stu-id="56563-200">**1**</span></span>|<span data-ttu-id="56563-201">기본값</span><span class="sxs-lookup"><span data-stu-id="56563-201">Default.</span></span> <span data-ttu-id="56563-202">시작, 진행, 성공 등과 같이 상태가 동일한 이전 기록 메시지를 항상 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-202">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="56563-203">상태가 같은 이전 레코드가 없으면 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-203">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="56563-204">**2**</span><span class="sxs-lookup"><span data-stu-id="56563-204">**2**</span></span>|<span data-ttu-id="56563-205">유휴 메시지나 장기 실행 작업 메시지에 대한 레코드가 없으면 새 기록 레코드를 삽입합니다. 이 경우 이전 레코드를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-205">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="56563-206">**3**</span><span class="sxs-lookup"><span data-stu-id="56563-206">**3**</span></span>|<span data-ttu-id="56563-207">유휴 메시지에 대한 레코드가 없으면 항상 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-207">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="56563-208">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="56563-208">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="56563-209">게시자에 연결할 때 사용하는 호스트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-209">Is the host name used when connecting to the Publisher.</span></span> <span data-ttu-id="56563-210">이 매개 변수는 최대 128개의 유니코드 문자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-210">This parameter can be a maximum of 128 Unicode characters.</span></span>  
  
 <span data-ttu-id="56563-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="56563-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="56563-212">기록 스레드가 기존 연결에서 서버의 응답을 기다리고 있는지 확인할 때까지 걸리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-212">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="56563-213">이 값을 줄이면 장기 실행 일괄 처리를 실행할 때 점검 에이전트에서 배포 에이전트를 주의 대상으로 표시하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-213">This value can be decreased to avoid having the checkup agent mark the Distribution Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="56563-214">기본값은 **300** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-214">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="56563-215">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="56563-215">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="56563-216">로그인 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 **15** 초입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-216">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="56563-217">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="56563-217">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="56563-218">병렬로 수행할 수 있는 대량 복사 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-218">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="56563-219">동시에 존재하는 스레드 및 ODBC 연결의 최대 개수는 **MaxBcpThreads** 와 배포 데이터베이스의 동기화 트랜잭션에 나타나는 대량 복사 요청 수 중 더 작은 값입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-219">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="56563-220">**MaxBcpThreads** 값은 **0** 보다 크고 하드 코딩된 상한값이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-220">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="56563-221">기본값은 최대값이 **8** 인 프로세서 수의 **2**배입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-221">The default is **2** times the number of processors, up to a maximum value of **8**.</span></span> <span data-ttu-id="56563-222">게시자에서 동시 스냅샷 옵션을 사용하여 생성된 스냅샷을 적용할 경우 **MaxBcpThreads**에 지정한 숫자에 관계없이 하나의 스레드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-222">When applying a snapshot that was generated at the Publisher using the concurrent snapshot option, one thread is used, regardless of the number you specify for **MaxBcpThreads**.</span></span>  
  
 <span data-ttu-id="56563-223">**-MaxDeliveredTransactions** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="56563-223">**-MaxDeliveredTransactions** _number_of_transactions_</span></span>  
 <span data-ttu-id="56563-224">한 번의 동기화에서 구독자에 적용되는 밀어넣기 또는 끌어오기 트랜잭션의 최대 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-224">Is the maximum number of push or pull transactions applied to Subscribers in one synchronization.</span></span> <span data-ttu-id="56563-225">값 **0** 은 최대값이 무한개의 트랜잭션임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-225">A value of **0** indicates that the maximum is an infinite number of transactions.</span></span> <span data-ttu-id="56563-226">다른 값은 구독자가 게시자에서 끌어오는 동기화의 기간을 줄이는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-226">Other values can be used by Subscribers to shorten the duration of a synchronization being pulled from a Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56563-227">-MaxDeliveredTransactions와 -Continuous를 둘 다 지정한 경우 배포 에이전트는 -Continuous가 지정되었음에도 불구하고 지정된 개수의 트랜잭션을 제공한 다음 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-227">If -MaxDeliveredTransactions and -Continuous are both specified, the Distribution Agent delivers the specified number of transactions and then stops (even though -Continuous is specified).</span></span> <span data-ttu-id="56563-228">작업이 완료되면 배포 에이전트를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-228">You must restart the Distribution Agent after the job completes.</span></span>  
  
 <span data-ttu-id="56563-229">**-MessageInterval**  _message_interval_</span><span class="sxs-lookup"><span data-stu-id="56563-229">**-MessageInterval**  _message_interval_</span></span>  
 <span data-ttu-id="56563-230">기록 로깅에 사용되는 시간 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-230">Is the time interval used for history logging.</span></span> <span data-ttu-id="56563-231">기록 이벤트는 다음과 같은 경우에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-231">A history event is logged when one of these parameters is reached:</span></span>  
  
-   <span data-ttu-id="56563-232">마지막 기록 이벤트가 기록된 후 **TransactionsPerHistory** 값에 도달한 경우</span><span class="sxs-lookup"><span data-stu-id="56563-232">The **TransactionsPerHistory** value is reached after the last history event is logged.</span></span>  
  
-   <span data-ttu-id="56563-233">마지막 기록 이벤트가 기록된 후 **MessageInterval** 값에 도달한 경우</span><span class="sxs-lookup"><span data-stu-id="56563-233">The **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="56563-234">원본에 사용할 수 있는 복제된 트랜잭션이 없는 경우 에이전트에서는 배포자에 트랜잭션 없음 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-234">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="56563-235">이 옵션은 다른 트랜잭션 없음 메시지를 보고하기 전에 에이전트에서 기다리는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-235">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="56563-236">에이전트에서는 이전에 복제된 트랜잭션을 처리한 후 원본에 사용할 수 있는 트랜잭션이 없는지 감지할 때 항상 트랜잭션 없음 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-236">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="56563-237">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-237">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="56563-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span><span class="sxs-lookup"><span data-stu-id="56563-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span></span>  
 <span data-ttu-id="56563-239">BLOB(Binary Large Object)의 최소 크기(바이트)를 지정합니다. 이 크기를 넘으면 데이터가 스트림으로 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-239">Specifies the minimum size, in bytes, for binary large object data above which the data will be bound as a stream.</span></span> <span data-ttu-id="56563-240">이 매개 변수를 사용하려면 **–UseOledbStreaming**을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-240">You must specify **-UseOledbStreaming** to use this parameter.</span></span> <span data-ttu-id="56563-241">값은 400바이트에서 1048576바이트 사이일 수 있으며 기본값은 16384바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-241">Values can range from 400 to 1048576 bytes, with a default of 16384 bytes.</span></span>  
  
 <span data-ttu-id="56563-242">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="56563-242">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="56563-243">에이전트 출력 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-243">Is the path of the agent output file.</span></span> <span data-ttu-id="56563-244">파일 이름을 지정하지 않으면 출력이 콘솔로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-244">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="56563-245">지정된 파일 이름이 존재하면 출력이 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-245">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="56563-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="56563-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="56563-247">출력이 자세해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-247">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="56563-248">정보 표시 수준이 **0**이면 오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-248">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="56563-249">정보 표시 수준이 **1**이면 모든 진행률 보고 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-249">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="56563-250">정보 표시 수준이 **2** (기본값)이면 디버깅에 유용한 오류 메시지와 진행률 보고 메시지가 모두 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-250">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="56563-251">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="56563-251">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="56563-252">패킷 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-252">Is the packet size, in bytes.</span></span> <span data-ttu-id="56563-253">기본값은 4096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-253">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="56563-254">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="56563-254">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="56563-255">배포 데이터베이스에서 복제된 트랜잭션을 쿼리하는 빈도(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-255">Is how often, in seconds, the distribution database is queried for replicated transactions.</span></span> <span data-ttu-id="56563-256">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-256">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="56563-257">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="56563-257">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="56563-258">에이전트 매개 변수에 사용할 에이전트 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-258">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="56563-259">**ProfileName** 이 NULL이면 에이전트 프로필이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-259">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="56563-260">**ProfileName** 이 지정되지 않으면 에이전트 유형에 대한 기본 프로필이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-260">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="56563-261">자세한 내용은 [복제 에이전트 프로필](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56563-261">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="56563-262">**-Publication**  _publication_</span><span class="sxs-lookup"><span data-stu-id="56563-262">**-Publication**  _publication_</span></span>  
 <span data-ttu-id="56563-263">게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-263">Is the name of the publication.</span></span> <span data-ttu-id="56563-264">이 매개 변수는 게시가 새 구독이나 다시 초기화된 구독에 대해 항상 스냅샷을 사용할 수 있도록 설정된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-264">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="56563-265">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="56563-265">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="56563-266">쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 1800초입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-266">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="56563-267">**-QuotedIdentifier** _quoted_identifier_</span><span class="sxs-lookup"><span data-stu-id="56563-267">**-QuotedIdentifier** _quoted_identifier_</span></span>  
 <span data-ttu-id="56563-268">사용할 따옴표 붙은 식별자 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-268">Specifies the quoted identifier character to use.</span></span> <span data-ttu-id="56563-269">값의 첫 번째 문자는 배포 에이전트에서 사용하는 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-269">The first character of the value indicates the value the Distribution Agent uses.</span></span> <span data-ttu-id="56563-270">값을 지정하지 않고 **QuotedIdentifier** 를 사용하면 배포 에이전트에서는 공백을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-270">If **QuotedIdentifier** is used with no value, the Distribution Agent uses a space.</span></span> <span data-ttu-id="56563-271">**QuotedIdentifier** 를 사용하지 않는 경우 배포 에이전트에서는 구독자가 지원하는 따옴표 붙은 식별자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-271">If **QuotedIdentifier** is not used, the Distribution Agent uses whatever quoted identifier the Subscriber supports.</span></span>  
  
 <span data-ttu-id="56563-272">**-SkipErrors** _native_error_id_ [ **:** _...n_]</span><span class="sxs-lookup"><span data-stu-id="56563-272">**-SkipErrors** _native_error_id_ [**:**_...n_]</span></span>  
 <span data-ttu-id="56563-273">이 에이전트에서 건너뛸 오류 번호를 지정하는 콜론으로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-273">Is a colon-separated list that specifies the error numbers to be skipped by this agent.</span></span>  
  
 <span data-ttu-id="56563-274">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="56563-274">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="56563-275">**SubscriberType** 이 **2** 로서, ODBC DSN(데이터 원본 이름)이 없는 Jet 데이터베이스에 대한 연결이 허용되는 경우 Jet 데이터베이스(.mdb 파일)의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-275">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="56563-276">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="56563-276">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="56563-277">구독자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-277">Is the Subscriber login name.</span></span> <span data-ttu-id="56563-278">**SubscriberSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-278">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="56563-279">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="56563-279">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="56563-280">구독자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-280">Is the Subscriber password.</span></span> <span data-ttu-id="56563-281">**SubscriberSecurityMode** 가 **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증의 경우)이면 이 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-281">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="56563-282">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="56563-282">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="56563-283">구독자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-283">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="56563-284">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 나타내고 값 **1** 은 Windows 인증 모드(기본값)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-284">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, and a value of **1** indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="56563-285">**-SubscriberType** [ **0**| **1**| **3**]</span><span class="sxs-lookup"><span data-stu-id="56563-285">**-SubscriberType** [ **0**| **1**| **3**]</span></span>  
 <span data-ttu-id="56563-286">배포 에이전트에서 사용하는 구독자 연결 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-286">Specifies the type of Subscriber connection used by the Distribution Agent.</span></span>  
  
|<span data-ttu-id="56563-287">SubscriberType 값</span><span class="sxs-lookup"><span data-stu-id="56563-287">SubscriberType value</span></span>|<span data-ttu-id="56563-288">Description</span><span class="sxs-lookup"><span data-stu-id="56563-288">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="56563-289">**0**</span><span class="sxs-lookup"><span data-stu-id="56563-289">**0**</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="56563-290">**1**</span><span class="sxs-lookup"><span data-stu-id="56563-290">**1**</span></span>|<span data-ttu-id="56563-291">ODBC 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="56563-291">ODBC data source</span></span>|  
|<span data-ttu-id="56563-292">**3**</span><span class="sxs-lookup"><span data-stu-id="56563-292">**3**</span></span>|<span data-ttu-id="56563-293">OLE DB 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="56563-293">OLE DB data source</span></span>|  
  
 <span data-ttu-id="56563-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span><span class="sxs-lookup"><span data-stu-id="56563-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span></span>  
 <span data-ttu-id="56563-295">단일 스레드를 사용할 때 나타나는 여러 가지 트랜잭션 특징을 유지하면서 변경 내용의 일괄 처리를 구독자에 대해 병렬로 적용하기 위해 배포 에이전트당 허용된 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-295">Is the number of connections allowed per Distribution Agent to apply batches of changes in parallel to a Subscriber, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="56563-296">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 게시자의 경우 1에서 64 사이의 값 범위가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-296">For a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, a range of values from 1 to 64 is supported.</span></span> <span data-ttu-id="56563-297">이 매개 변수는 게시자 및 배포자가 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상 버전에서 실행 중인 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-297">This parameter is only supported when the Publisher and Distributor are running on [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later versions.</span></span> <span data-ttu-id="56563-298">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자 또는 피어 투 피어 구독의 경우 이 매개 변수가 지원되지 않거나 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-298">This parameter is not supported or must be 0 for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers or peer-to-peer subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56563-299">여러 연결 중 하나가 실행 또는 커밋되지 않으면 모든 연결에서 현재 일괄 처리를 중지하고 에이전트가 단일 스트림을 사용하여 실패한 일괄 처리를 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-299">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="56563-300">이러한 재시도 단계가 완료되기 전에는 구독자에 임시 트랜잭션 불일치가 발생할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="56563-300">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="56563-301">실패한 일괄 처리가 성공적으로 커밋되면 구독자의 트랜잭션 일관성이 다시 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-301">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="56563-302">**-SubscriptionStreams**의 값으로 2 이상을 지정할 경우 구독자에서 트랜잭션을 받는 순서가 게시자에서 트랜잭션을 만든 순서와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-302">When you specify a value of 2 or greater for **-SubscriptionStreams**, the order in which transactions are received at the Subscriber may differ from the order in which they were made at the Publisher.</span></span> <span data-ttu-id="56563-303">이 동작으로 인해 동기화 중 제약 조건 위반이 발생할 경우에는 동기화할 때 NOT FOR REPLICATION 옵션을 사용하여 제약 조건이 적용되지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-303">If this behavior causes constraint violations during synchronization, you should use the NOT FOR REPLICATION option to disable the enforcement of constraints during synchronization.</span></span> <span data-ttu-id="56563-304">자세한 내용은 [동기화하는 동안 트리거 및 제약 조건 동작 제어&#40;복제 Transact-SQL 프로그래밍&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56563-304">For more information, see [Control the Behavior of Triggers and Constraints During Synchronization &#40;Replication Transact-SQL Programming&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56563-305">Subscriptionstreams는 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 제공하도록 구성된 아티클에 대해서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-305">Subscriptionstreams do not work for articles configured to deliver [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="56563-306">subscriptionstreams를 사용하려면 대신 저장 프로시저 호출을 제공하도록 아티클을 구성하십시오.</span><span class="sxs-lookup"><span data-stu-id="56563-306">To use subscriptionstreams, configure articles to deliver stored procedure calls instead.</span></span>  
  
 <span data-ttu-id="56563-307">**-SubscriptionTableName** _subscription_table_</span><span class="sxs-lookup"><span data-stu-id="56563-307">**-SubscriptionTableName** _subscription_table_</span></span>  
 <span data-ttu-id="56563-308">지정된 구독자에서 생성되거나 사용된 구독 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-308">Is the name of the subscription table generated or used at the given Subscriber.</span></span> <span data-ttu-id="56563-309">지정되지 않은 경우 [MSreplication_subscriptions&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) 테이블이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-309">When not specified, the [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) table is used.</span></span> <span data-ttu-id="56563-310">긴 파일 이름을 지원하지 않는 DBMS(데이터베이스 관리 시스템)의 경우에 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-310">Use this option for database management systems (DBMS) that do not support long file names.</span></span>  
  
 <span data-ttu-id="56563-311">**-SubscriptionType** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="56563-311">**-SubscriptionType** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="56563-312">배포의 구독 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-312">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="56563-313">값 **0** 은 밀어넣기 구독을, 값 **1** 은 끌어오기 구독을, 값 **2** 는 익명 구독을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56563-313">A value of **0** indicates a push subscription, a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="56563-314">**-TransactionsPerHistory** [ **0**| **1**|... **10000**]</span><span class="sxs-lookup"><span data-stu-id="56563-314">**-TransactionsPerHistory** [ **0**| **1**|... **10000**]</span></span>  
 <span data-ttu-id="56563-315">기록 로깅의 트랜잭션 간격을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-315">Specifies the transaction interval for history logging.</span></span> <span data-ttu-id="56563-316">기록 로깅의 마지막 인스턴스 후 커밋된 트랜잭션의 수가 이 옵션보다 클 경우 기록 메시지가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="56563-316">If the number of committed transactions after the last instance of history logging is greater than this option, a history message is logged.</span></span> <span data-ttu-id="56563-317">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-317">The default is 100.</span></span> <span data-ttu-id="56563-318">값이 **0** 이면 **TransactionsPerHistory**에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-318">A value of **0** indicates infinite **TransactionsPerHistory**.</span></span> <span data-ttu-id="56563-319">이전 **-messageinterval**매개 변수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56563-319">See the preceding **-MessageInterval**parameter.</span></span>  
  
 <span data-ttu-id="56563-320">**-UseDTS**</span><span class="sxs-lookup"><span data-stu-id="56563-320">**-UseDTS**</span></span>  
 <span data-ttu-id="56563-321">데이터 변환을 허용하는 게시의 매개 변수로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-321">Must be specified as a parameter for a publication that allows data transformation.</span></span>  
  
 <span data-ttu-id="56563-322">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="56563-322">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="56563-323">배포 에이전트에서 구독자에 스냅샷 파일을 적용할 때 BULK INSERT 명령을 사용하도록 지정하여 초기 스냅샷의 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="56563-323">Improves the performance of the initial snapshot by causing the Distribution Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="56563-324">이 매개 변수는 XML 데이터 형식과 호환되지 않으므로 이후에는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-324">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="56563-325">XML 데이터를 복제하지 않을 계획이라면 이 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-325">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="56563-326">이 매개 변수는 문자 모드 스냅샷 또는[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-326">This parameter cannot be used with character mode snapshots or non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span> <span data-ttu-id="56563-327">이 매개 변수를 사용하려면 구독자의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정에 스냅샷 .bcp 데이터 파일이 있는 디렉터리에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-327">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="56563-328">이 매개 변수를 사용하지 않으면 에이전트([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자의 경우) 또는 에이전트에서 로드한 ODBC 드라이버( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구독자의 경우)가 파일 내용을 읽으므로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정의 보안 컨텍스트가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-328">When this parameter is not used, the agent (for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) or the ODBC driver loaded by the agent (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="56563-329">**-UseOledbStreaming**</span><span class="sxs-lookup"><span data-stu-id="56563-329">**-UseOledbStreaming**</span></span>  
 <span data-ttu-id="56563-330">이 인수를 지정하면 BLOB(Binary Large Object) 데이터를 스트림으로 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-330">When specified, enables the binding of binary large object data as a stream.</span></span> <span data-ttu-id="56563-331">크기(바이트)가 얼마 이상일 때 스트림을 사용할지를 지정하려면 **-OledbStreamThreshold** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-331">Use **-OledbStreamThreshold** to specify the size, in bytes, above which a stream will be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56563-332">설명</span><span class="sxs-lookup"><span data-stu-id="56563-332">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="56563-333">도메인 사용자 계정(기본값)이 아닌 로컬 시스템 계정에서 실행되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 설치한 경우 해당 서비스에서는 로컬 컴퓨터에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-333">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can only access the local computer.</span></span> <span data-ttu-id="56563-334">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트에서 실행되는 배포 에이전트가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 인스턴스에 로그인할 때 Windows 인증 모드를 사용하도록 구성된 경우 해당 배포 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-334">If the Distribution Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Distribution Agent fails.</span></span> <span data-ttu-id="56563-335">기본 설정은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="56563-335">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="56563-336">보안 계정을 변경하는 방법에 대한 자세한 내용은 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="56563-336">For information on changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="56563-337">배포 에이전트를 시작하려면 명령 프롬프트에서 **distrib.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56563-337">To start the Distribution Agent, execute **distrib.exe** from the command prompt.</span></span> <span data-ttu-id="56563-338">자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56563-338">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="56563-339">변경 내역</span><span class="sxs-lookup"><span data-stu-id="56563-339">Change History</span></span>  
  
|<span data-ttu-id="56563-340">업데이트된 내용</span><span class="sxs-lookup"><span data-stu-id="56563-340">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="56563-341">**-ExtendedEventConfigFile** 매개 변수를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="56563-341">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56563-342">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56563-342">See Also</span></span>  
 [<span data-ttu-id="56563-343">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="56563-343">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
