---
title: 복제 로그 판독기 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 120c7418d8b16fe6d083961affcf0b8a9c9f6c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650917"
---
# <a name="replication-log-reader-agent"></a><span data-ttu-id="4a835-102">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="4a835-102">Replication Log Reader Agent</span></span>
  <span data-ttu-id="4a835-103">복제 로그 판독기 에이전트는 트랜잭션 복제를 위해 구성한 각 데이터베이스의 트랜잭션 로그를 모니터링하고 트랜잭션 로그에서 복제 대상으로 표시된 트랜잭션을 배포 데이터베이스에 복사하는 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-103">The Replication Log Reader Agent is an executable that monitors the transaction log of each database configured for transactional replication and copies the transactions marked for replication from the transaction log into the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a835-104">매개 변수는 지정되는 순서에 제한을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="4a835-105">선택적 매개 변수가 지정되지 않은 경우 기본 에이전트 프로필을 기반으로 하여 미리 정의된 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-105">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a835-106">구문</span><span class="sxs-lookup"><span data-stu-id="4a835-106">Syntax</span></span>  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a835-107">인수</span><span class="sxs-lookup"><span data-stu-id="4a835-107">Arguments</span></span>  
 <span data-ttu-id="4a835-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="4a835-108">**-?**</span></span>  
 <span data-ttu-id="4a835-109">사용 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-109">Displays usage information.</span></span>  
  
 <span data-ttu-id="4a835-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="4a835-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="4a835-111">게시자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-111">Is the name of the Publisher.</span></span> <span data-ttu-id="4a835-112">해당 서버에 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스에 대해 *server_name*을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="4a835-113">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="4a835-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="4a835-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="4a835-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="4a835-115">게시자 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="4a835-116">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="4a835-116">**-Continuous**</span></span>  
 <span data-ttu-id="4a835-117">에이전트에서 복제된 트랜잭션의 폴링을 계속 시도할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-117">Specifies whether the agent tries to poll replicated transactions continually.</span></span> <span data-ttu-id="4a835-118">이 인수가 지정된 경우 에이전트는 보류 중인 트랜잭션이 없는 경우에도 원본의 복제된 트랜잭션을 폴링 간격에 따라 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-118">If specified, the agent polls replicated transactions from the source at polling intervals even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="4a835-119">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="4a835-119">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="4a835-120">에이전트 정의 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-120">Is the path of the agent definition file.</span></span> <span data-ttu-id="4a835-121">에이전트 정의 파일에는 에이전트의 명령줄 인수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-121">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="4a835-122">파일 내용은 실행 파일로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-122">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="4a835-123">임의 문자가 있는 인수 값을 지정하려면 큰따옴표(")를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-123">Use double quotation marks (") to specify argument values that contain arbitrary characters.</span></span>  
  
 <span data-ttu-id="4a835-124">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="4a835-124">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="4a835-125">배포자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-125">Is the Distributor name.</span></span> <span data-ttu-id="4a835-126">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-126">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="4a835-127">해당 서버에 있는 명명된 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대해 server_name을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="4a835-127">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="4a835-128">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="4a835-128">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="4a835-129">배포자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-129">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="4a835-130">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="4a835-130">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="4a835-131">배포자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-131">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="4a835-132">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="4a835-132">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="4a835-133">배포자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-133">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="4a835-134">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 모드(기본값)를 나타내며 값 **1** 은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-134">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="4a835-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="4a835-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="4a835-136">연결을 만들 때 로그 판독기 에이전트에서 사용하는 SSL(Secure Sockets Layer) 암호화의 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-136">Is the level of Secure Sockets Layer (SSL) encryption that is used by the Log Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="4a835-137">EncryptionLevel 값</span><span class="sxs-lookup"><span data-stu-id="4a835-137">EncryptionLevel value</span></span>|<span data-ttu-id="4a835-138">Description</span><span class="sxs-lookup"><span data-stu-id="4a835-138">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4a835-139">**0**</span><span class="sxs-lookup"><span data-stu-id="4a835-139">**0**</span></span>|<span data-ttu-id="4a835-140">SSL이 사용되지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-140">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="4a835-141">**1**</span><span class="sxs-lookup"><span data-stu-id="4a835-141">**1**</span></span>|<span data-ttu-id="4a835-142">SSL이 사용되지만 에이전트에서 SSL 서버 인증서가 트러스트된 발급자에 의해 서명된 것인지 확인하지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-142">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="4a835-143">**2**</span><span class="sxs-lookup"><span data-stu-id="4a835-143">**2**</span></span>|<span data-ttu-id="4a835-144">SSL이 사용되고 인증서가 확인됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-144">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="4a835-145">유효한 SSL 인증서는 SQL Server의 정규화된 도메인 이름으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-145">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="4a835-146">-EncryptionLevel을 2로 설정할 때 에이전트가 성공적으로 연결되도록 하려면 로컬 SQL Server에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-146">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="4a835-147">'별칭 이름' 매개 변수는 서버 이름이어야 하며 '서버' 매개 변수는 SQL Server의 정규화된 이름으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-147">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
 
 <span data-ttu-id="4a835-148">자세한 내용은 [SQL Server 복제 보안](../security/view-and-modify-replication-security-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4a835-148">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="4a835-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="4a835-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="4a835-150">확장 이벤트 XML 구성 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-150">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="4a835-151">확장 이벤트 구성 파일에서는 세션을 구성하고 추적 이벤트를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-151">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="4a835-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="4a835-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="4a835-153">로그 판독기 작업을 수행하는 동안 기록에 추가되는 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-153">Specifies the amount of history logged during a log reader operation.</span></span> <span data-ttu-id="4a835-154">**1**을 선택하여 기록 로깅이 성능에 주는 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-154">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="4a835-155">HistoryVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="4a835-155">HistoryVerboseLevel value</span></span>|<span data-ttu-id="4a835-156">Description</span><span class="sxs-lookup"><span data-stu-id="4a835-156">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="4a835-157">**0**</span><span class="sxs-lookup"><span data-stu-id="4a835-157">**0**</span></span>||  
|<span data-ttu-id="4a835-158">**1**</span><span class="sxs-lookup"><span data-stu-id="4a835-158">**1**</span></span>|<span data-ttu-id="4a835-159">기본값</span><span class="sxs-lookup"><span data-stu-id="4a835-159">Default.</span></span> <span data-ttu-id="4a835-160">시작, 진행, 성공 등과 같이 상태가 동일한 이전 기록 메시지를 항상 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-160">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="4a835-161">상태가 같은 이전 레코드가 없으면 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-161">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="4a835-162">**2**</span><span class="sxs-lookup"><span data-stu-id="4a835-162">**2**</span></span>|<span data-ttu-id="4a835-163">유휴 메시지나 장기 실행 작업 메시지에 대한 레코드가 없으면 새 기록 레코드를 삽입합니다. 이 경우 이전 레코드를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-163">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
  
 <span data-ttu-id="4a835-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="4a835-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="4a835-165">기록 스레드가 기존 연결에서 서버의 응답을 기다리고 있는지 확인할 때까지 걸리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-165">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="4a835-166">이 값을 줄이면 장기 실행 일괄 처리를 실행할 때 점검 에이전트에서 로그 판독기 에이전트를 주의 대상으로 표시하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-166">This value can be decreased to avoid having the checkup agent mark the Log Reader Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="4a835-167">기본값은 300초입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-167">The default is 300 seconds.</span></span>  
  
 <span data-ttu-id="4a835-168">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="4a835-168">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="4a835-169">로그인 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 15초입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-169">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="4a835-170">**-LogScanThreshold** _scan_threshold_</span><span class="sxs-lookup"><span data-stu-id="4a835-170">**-LogScanThreshold** _scan_threshold_</span></span>  
 <span data-ttu-id="4a835-171">내부적으로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-171">Internal use only.</span></span>  
  
 <span data-ttu-id="4a835-172">**-MaxCmdsInTran** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="4a835-172">**-MaxCmdsInTran** _number_of_commands_</span></span>  
 <span data-ttu-id="4a835-173">로그 판독기가 배포 데이터베이스에 명령을 쓸 때 하나의 트랜잭션으로 그룹화되는 문의 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-173">Specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="4a835-174">이 매개 변수를 사용하면 로그 판독기 에이전트와 배포 에이전트가 게시자에서 여러 명령으로 구성된 큰 트랜잭션을 구독자에 적용할 때 여러 개의 작은 트랜잭션으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-174">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applied at the Subscriber.</span></span> <span data-ttu-id="4a835-175">이 매개 변수를 지정하면 배포자에서 경합을 줄일 수 있고 게시자와 구독자 간 대기 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-175">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="4a835-176">원래 트랜잭션이 작은 단위로 적용되므로 구독자는 엄격한 트랜잭션 원자성을 깨고 원래 트랜잭션이 끝나기 전에 큰 논리적 게시자 트랜잭션의 행에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-176">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="4a835-177">기본값은 **0**으로 게시자의 트랜잭션 경계를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-177">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a835-178">이 매개 변수는[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외의 게시에 대해서는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-178">This parameter is ignored for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publications.</span></span> <span data-ttu-id="4a835-179">자세한 내용은 [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)의 "트랜잭션 세트 작업 구성" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a835-179">For more information, see the section "Configuring the Transaction Set Job" in [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
 <span data-ttu-id="4a835-180">**-MessageInterval** _message_interval_</span><span class="sxs-lookup"><span data-stu-id="4a835-180">**-MessageInterval** _message_interval_</span></span>  
 <span data-ttu-id="4a835-181">기록 로깅에 사용되는 시간 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-181">Is the time interval used for history logging.</span></span> <span data-ttu-id="4a835-182">기록 이벤트는 마지막 기록 이벤트가 기록된 후 **MessageInterval** 값에 도달할 때 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-182">A history event is logged when the **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="4a835-183">원본에 사용할 수 있는 복제된 트랜잭션이 없는 경우 에이전트에서는 배포자에 트랜잭션 없음 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-183">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="4a835-184">이 옵션은 다른 트랜잭션 없음 메시지를 보고하기 전에 에이전트에서 기다리는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-184">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="4a835-185">에이전트에서는 이전에 복제된 트랜잭션을 처리한 후 원본에 사용할 수 있는 트랜잭션이 없는지 감지할 때 항상 트랜잭션 없음 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-185">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="4a835-186">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-186">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="4a835-187">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="4a835-187">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="4a835-188">에이전트 출력 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-188">Is the path of the agent output file.</span></span> <span data-ttu-id="4a835-189">파일 이름을 지정하지 않으면 출력이 콘솔로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-189">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="4a835-190">지정된 파일 이름이 존재하면 출력이 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-190">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="4a835-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span><span class="sxs-lookup"><span data-stu-id="4a835-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span></span>  
 <span data-ttu-id="4a835-192">출력이 자세해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-192">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="4a835-193">값</span><span class="sxs-lookup"><span data-stu-id="4a835-193">Value</span></span>|<span data-ttu-id="4a835-194">Description</span><span class="sxs-lookup"><span data-stu-id="4a835-194">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a835-195">**0**</span><span class="sxs-lookup"><span data-stu-id="4a835-195">**0**</span></span>|<span data-ttu-id="4a835-196">오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-196">Only error messages are printed.</span></span>|  
|<span data-ttu-id="4a835-197">**1**</span><span class="sxs-lookup"><span data-stu-id="4a835-197">**1**</span></span>|<span data-ttu-id="4a835-198">모든 에이전트 진행률 보고 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-198">All agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="4a835-199">**2** (기본값)</span><span class="sxs-lookup"><span data-stu-id="4a835-199">**2** (default)</span></span>|<span data-ttu-id="4a835-200">모든 오류 메시지와 에이전트 진행률 보고 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-200">All error messages and agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="4a835-201">**3**</span><span class="sxs-lookup"><span data-stu-id="4a835-201">**3**</span></span>|<span data-ttu-id="4a835-202">복제된 각 명령의 처음 100바이트가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-202">The first 100 bytes of each replicated command are printed.</span></span>|  
|<span data-ttu-id="4a835-203">**4**</span><span class="sxs-lookup"><span data-stu-id="4a835-203">**4**</span></span>|<span data-ttu-id="4a835-204">복제된 모든 명령이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-204">All replicated commands are printed.</span></span>|  
  
 <span data-ttu-id="4a835-205">값 2-4는 디버깅할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-205">Values 2-4 are useful when debugging.</span></span>  
  
 <span data-ttu-id="4a835-206">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="4a835-206">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="4a835-207">패킷 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-207">Is the packet size, in bytes.</span></span> <span data-ttu-id="4a835-208">기본값은 4096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-208">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="4a835-209">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="4a835-209">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="4a835-210">로그에서 복제된 트랜잭션을 쿼리하는 빈도(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-210">Is how often, in seconds, the log is queried for replicated transactions.</span></span> <span data-ttu-id="4a835-211">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-211">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="4a835-212">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="4a835-212">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="4a835-213">에이전트 매개 변수에 사용할 에이전트 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-213">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="4a835-214">**ProfileName** 이 NULL이면 에이전트 프로필이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-214">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="4a835-215">**ProfileName** 이 지정되지 않으면 에이전트 유형에 대한 기본 프로필이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-215">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="4a835-216">자세한 내용은 [복제 에이전트 프로필](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a835-216">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="4a835-217">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="4a835-217">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="4a835-218">게시 데이터베이스와 함께 데이터베이스 미러링 세션에 참여하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 장애 조치 파트너 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-218">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="4a835-219">자세한 내용은 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a835-219">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="4a835-220">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="4a835-220">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="4a835-221">게시자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-221">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="4a835-222">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증(기본값)을 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-222">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="4a835-223">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="4a835-223">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="4a835-224">게시자 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-224">Is the Publisher login name.</span></span>  
  
 <span data-ttu-id="4a835-225">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="4a835-225">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="4a835-226">게시자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-226">Is the Publisher password.</span></span>  
  
 <span data-ttu-id="4a835-227">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="4a835-227">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="4a835-228">쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 1800초입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-228">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="4a835-229">**-ReadBatchSize** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="4a835-229">**-ReadBatchSize** _number_of_transactions_</span></span>  
 <span data-ttu-id="4a835-230">게시 데이터베이스의 트랜잭션 로그에서 읽은 처리 사이클당 최대 트랜잭션 수로서, 기본값은 500입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-230">Is the maximum number of transactions read out of the transaction log of the publishing database per processing cycle, with a default of 500.</span></span> <span data-ttu-id="4a835-231">에이전트에서는 로그의 모든 트랜잭션을 읽을 때까지 일괄 처리로 트랜잭션을 계속 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-231">The agent will continue to read transactions in batches until all transactions are read from the log.</span></span> <span data-ttu-id="4a835-232">이 매개 변수는 Oracle 게시자에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-232">This parameter is not supported for Oracle Publishers.</span></span>  
  
 <span data-ttu-id="4a835-233">**-ReadBatchThreshold** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="4a835-233">**-ReadBatchThreshold** _number_of_commands_</span></span>  
 <span data-ttu-id="4a835-234">배포 에이전트에서 구독자에 대해 실행하기 전에 트랜잭션 로그에서 읽을 복제 명령의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-234">Is the number of replication commands to be read from the transaction log before being issued to the Subscriber by the Distribution Agent.</span></span> <span data-ttu-id="4a835-235">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-235">The default is 0.</span></span> <span data-ttu-id="4a835-236">이 매개 변수가 지정되어 있지 않으면 로그 판독기 에이전트에서는 로그의 끝까지 또는 **-ReadBatchSize** (트랜잭션 수)에 지정된 개수까지 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-236">If this parameter is not specified, the Log Reader Agent will read to the end of the log or to the number specified in **-ReadBatchSize** (number of transactions).</span></span>  
  
 <span data-ttu-id="4a835-237">**-RecoverFromDataErrors**</span><span class="sxs-lookup"><span data-stu-id="4a835-237">**-RecoverFromDataErrors**</span></span>  
 <span data-ttu-id="4a835-238">SQL Server 이외의 게시자에서 게시된 열 데이터에 오류가 발생할 경우에도 로그 판독기 에이전트가 계속 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-238">Specifies that the Log Reader Agent continue to run when it encounters errors in column data published from a non-SQL Server Publisher.</span></span> <span data-ttu-id="4a835-239">기본적으로는 이러한 오류가 발생하면 로그 판독기 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-239">By default, such errors cause the Log Reader Agent to fail.</span></span> <span data-ttu-id="4a835-240">**-RecoverFromDataErrors**를 사용하면 잘못된 열 데이터가 NULL 또는 null이 아닌 적절한 값으로 복제되며 [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) 테이블에 경고 메시지가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-240">When you use **-RecoverFromDataErrors**, erroneous column data is replicated either as NULL or an appropriate nonnull value, and warning messages are logged to the [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) table.</span></span> <span data-ttu-id="4a835-241">이 매개 변수는 Oracle 게시자에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-241">This parameter is only supported for Oracle Publishers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a835-242">설명</span><span class="sxs-lookup"><span data-stu-id="4a835-242">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4a835-243">도메인 사용자 계정(기본값) 대신 로컬 시스템 계정에서 실행되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 설치한 경우 해당 서비스에서는 로컬 컴퓨터에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-243">If you installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account instead of under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="4a835-244">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트에서 실행되는 로그 판독기 에이전트가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로그인할 때 Windows 인증 모드를 사용하도록 구성된 경우 해당 로그 판독기 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-244">If the Log Reader Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Log Reader Agent fails.</span></span> <span data-ttu-id="4a835-245">기본 설정은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-245">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="4a835-246">보안 계정을 변경하는 방법에 대한 자세한 내용은 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a835-246">For information about changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="4a835-247">로그 판독기 에이전트를 시작하려면 명령 프롬프트에서 **logread.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-247">To start the Log Reader Agent, execute **logread.exe** from the command prompt.</span></span> <span data-ttu-id="4a835-248">자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a835-248">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="4a835-249">변경 내역</span><span class="sxs-lookup"><span data-stu-id="4a835-249">Change History</span></span>  
  
|<span data-ttu-id="4a835-250">업데이트된 내용</span><span class="sxs-lookup"><span data-stu-id="4a835-250">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="4a835-251">**-ExtendedEventConfigFile** 매개 변수를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a835-251">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a835-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a835-252">See Also</span></span>  
 [<span data-ttu-id="4a835-253">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="4a835-253">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
