---
title: 복제 큐 판독기 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 854c425db3fbaa346dab5eb2c41bd58cf03f65c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646951"
---
# <a name="replication-queue-reader-agent"></a><span data-ttu-id="9425d-102">복제 큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="9425d-102">Replication Queue Reader Agent</span></span>
  <span data-ttu-id="9425d-103">복제 큐 판독기 에이전트는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 큐 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 메시지 큐에 저장된 메시지를 읽고 해당 메시지를 게시자에 적용하는 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-103">The Replication Queue Reader Agent is an executable that reads messages stored in a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue or a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue and then applies those messages to the Publisher.</span></span> <span data-ttu-id="9425d-104">큐 판독기 에이전트는 지연 업데이트를 허용하는 스냅샷 및 트랜잭션 게시와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-104">Queue Reader Agent is used with snapshot and transactional publications that allow queued updating.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9425d-105">매개 변수는 지정되는 순서에 제한을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="9425d-106">선택적 매개 변수가 지정되지 않은 경우 기본 에이전트 프로필을 기반으로 하여 미리 정의된 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-106">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9425d-107">구문</span><span class="sxs-lookup"><span data-stu-id="9425d-107">Syntax</span></span>  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9425d-108">인수</span><span class="sxs-lookup"><span data-stu-id="9425d-108">Arguments</span></span>  
 <span data-ttu-id="9425d-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="9425d-109">**-?**</span></span>  
 <span data-ttu-id="9425d-110">사용 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-110">Displays usage information.</span></span>  
  
 <span data-ttu-id="9425d-111">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="9425d-111">**-Continuous**</span></span>  
 <span data-ttu-id="9425d-112">에이전트에서 지연된 트랜잭션의 처리를 계속 시도할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-112">Specifies whether the agent attempts to process queued transactions continuously.</span></span> <span data-ttu-id="9425d-113">이 인수가 지정된 경우 에이전트는 구독자에서 보류 중인 지연 트랜잭션이 없는 경우에도 실행을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-113">If specified, the agent continues execution even if there are no queued transactions pending from any of the subscribers.</span></span>  
  
 <span data-ttu-id="9425d-114">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="9425d-114">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="9425d-115">에이전트 정의 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-115">Is the path of the agent definition file.</span></span> <span data-ttu-id="9425d-116">에이전트 정의 파일에는 에이전트의 명령줄 인수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-116">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="9425d-117">파일 내용은 실행 파일로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-117">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="9425d-118">임의 문자가 있는 인수 값을 지정하려면 큰따옴표(")를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-118">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="9425d-119">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9425d-119">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9425d-120">배포자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-120">Is the Distributor name.</span></span> <span data-ttu-id="9425d-121">해당 서버에 있는 기본 *server_name* 인스턴스에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-121">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="9425d-122">해당 서버에 있는 기본 *server_name*\\*instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="9425d-122">Specify *server_name*\\*instance_name* for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="9425d-123">이 인수가 지정되지 않은 경우 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름이 기본 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-123">If not specified, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="9425d-124">**-DistributionDB** _distribution_database_</span><span class="sxs-lookup"><span data-stu-id="9425d-124">**-DistributionDB** _distribution_database_</span></span>  
 <span data-ttu-id="9425d-125">배포 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-125">Is the distribution database.</span></span>  
  
 <span data-ttu-id="9425d-126">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="9425d-126">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="9425d-127">배포자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-127">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="9425d-128">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="9425d-128">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="9425d-129">배포자 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-129">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="9425d-130">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="9425d-130">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="9425d-131">배포자의 보안 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-131">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="9425d-132">값 **0** 은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증 모드(기본값)를 나타내며 값 **1** 은 Windows 인증 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-132">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="9425d-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="9425d-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="9425d-134">연결을 만들 때 큐 판독기 에이전트에서 사용하는 SSL(Secure Sockets Layer) 암호화의 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-134">Is the level of Secure Sockets Layer (SSL) encryption used by the Queue Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="9425d-135">EncryptionLevel 값</span><span class="sxs-lookup"><span data-stu-id="9425d-135">EncryptionLevel value</span></span>|<span data-ttu-id="9425d-136">Description</span><span class="sxs-lookup"><span data-stu-id="9425d-136">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9425d-137">**0**</span><span class="sxs-lookup"><span data-stu-id="9425d-137">**0**</span></span>|<span data-ttu-id="9425d-138">SSL이 사용되지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-138">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="9425d-139">**1**</span><span class="sxs-lookup"><span data-stu-id="9425d-139">**1**</span></span>|<span data-ttu-id="9425d-140">SSL이 사용되지만 에이전트에서 SSL 서버 인증서가 트러스트된 발급자에 의해 서명된 것인지 확인하지 않음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-140">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="9425d-141">**2**</span><span class="sxs-lookup"><span data-stu-id="9425d-141">**2**</span></span>|<span data-ttu-id="9425d-142">SSL이 사용되고 인증서가 확인됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-142">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="9425d-143">유효한 SSL 인증서는 SQL Server의 정규화된 도메인 이름으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-143">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="9425d-144">-EncryptionLevel을 2로 설정할 때 에이전트가 성공적으로 연결되도록 하려면 로컬 SQL Server에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-144">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="9425d-145">'별칭 이름' 매개 변수는 서버 이름이어야 하며 '서버' 매개 변수는 SQL Server의 정규화된 이름으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-145">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="9425d-146">자세한 내용은 [SQL Server 복제 보안](../security/view-and-modify-replication-security-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9425d-146">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="9425d-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="9425d-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="9425d-148">큐 판독기 작업을 수행하는 동안 기록에 추가되는 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-148">Specifies the amount of history logged during a queue reader operation.</span></span> <span data-ttu-id="9425d-149">**1**을 선택하여 성능에서 기록 로깅의 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-149">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="9425d-150">HistoryVerboseLevel 값</span><span class="sxs-lookup"><span data-stu-id="9425d-150">HistoryVerboseLevel value</span></span>|<span data-ttu-id="9425d-151">Description</span><span class="sxs-lookup"><span data-stu-id="9425d-151">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="9425d-152">**0**</span><span class="sxs-lookup"><span data-stu-id="9425d-152">**0**</span></span>|<span data-ttu-id="9425d-153">기록 로깅을 사용하지 않습니다(권장되지 않음).</span><span class="sxs-lookup"><span data-stu-id="9425d-153">No history logging (not recommended).</span></span>|  
|<span data-ttu-id="9425d-154">**1**</span><span class="sxs-lookup"><span data-stu-id="9425d-154">**1**</span></span>|<span data-ttu-id="9425d-155">기본값</span><span class="sxs-lookup"><span data-stu-id="9425d-155">Default.</span></span> <span data-ttu-id="9425d-156">시작, 진행, 성공 등과 같이 상태가 동일한 이전 기록 메시지를 항상 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-156">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="9425d-157">상태가 같은 이전 레코드가 없으면 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-157">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="9425d-158">**2**</span><span class="sxs-lookup"><span data-stu-id="9425d-158">**2**</span></span>|<span data-ttu-id="9425d-159">유휴 메시지 또는 장기 실행 작업 메시지를 포함하여 새 기록 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-159">Insert new history records, including idle messages or long-running job messages.</span></span>|  
|<span data-ttu-id="9425d-160">**3**</span><span class="sxs-lookup"><span data-stu-id="9425d-160">**3**</span></span>|<span data-ttu-id="9425d-161">문제 해결에 유용한 추가 정보를 포함하는 새 기록 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-161">Insert new history records that include additional details that may be useful for troubleshooting.</span></span>|  
  
 <span data-ttu-id="9425d-162">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="9425d-162">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="9425d-163">로그인 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 15초입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-163">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="9425d-164">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="9425d-164">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="9425d-165">에이전트 출력 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-165">Is the path of the agent output file.</span></span> <span data-ttu-id="9425d-166">파일 이름을 지정하지 않으면 출력이 콘솔로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-166">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="9425d-167">지정된 파일 이름이 존재하면 출력이 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-167">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="9425d-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="9425d-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="9425d-169">출력이 자세해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-169">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="9425d-170">정보 표시 수준이 **0**이면 오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-170">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="9425d-171">정보 표시 수준이 **1**이면 모든 진행률 보고 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-171">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="9425d-172">정보 표시 수준이 **2** (기본값)이면 디버깅에 유용한 오류 메시지와 진행률 보고 메시지가 모두 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-172">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="9425d-173">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="9425d-173">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="9425d-174">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기반 큐를 사용하는 구독 업데이트에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-174">Is relevant only for updating subscriptions that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] based queues.</span></span> <span data-ttu-id="9425d-175">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 큐가 보류 중인 지연 트랜잭션에 대해 폴링되는 빈도(초)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-175">Specifies how often, in seconds, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue is polled for pending queued transactions.</span></span> <span data-ttu-id="9425d-176">이 값은 0초에서 240초 사이일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-176">The value can be between 0 and 240 seconds.</span></span> <span data-ttu-id="9425d-177">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-177">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="9425d-178">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9425d-178">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9425d-179">게시 데이터베이스와 함께 데이터베이스 미러링 세션에 참여하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 장애 조치 파트너 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-179">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="9425d-180">자세한 내용은 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9425d-180">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="9425d-181">**-ProfileName** _agent_profile_name_</span><span class="sxs-lookup"><span data-stu-id="9425d-181">**-ProfileName** _agent_profile_name_</span></span>  
 <span data-ttu-id="9425d-182">에이전트에 대한 기본값 집합을 제공하는 데 사용되는 에이전트 프로필의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-182">Is the name of an agent profile used to supply a set of default values to the agent.</span></span> <span data-ttu-id="9425d-183">자세한 내용은 [복제 에이전트 프로필](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9425d-183">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="9425d-184">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="9425d-184">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="9425d-185">쿼리 시간이 초과될 때까지 걸리는 시간(초)입니다. 기본값은 1800초입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-185">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="9425d-186">**-ResolverState** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="9425d-186">**-ResolverState** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="9425d-187">지연 업데이트 충돌의 해결 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-187">Specifies how queued updating conflicts are resolved.</span></span> <span data-ttu-id="9425d-188">값 **1** 은 충돌 시 게시자의 내용이 적용되고, 현재 충돌하는 지연 트랜잭션이 게시자 및 원래 업데이트 구독자에서 다시 롤백되며, 이후 지연 트랜잭션의 처리가 계속됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-188">A value of **1** indicates the Publisher wins the conflict, and the current conflicting queued transaction will be rolled back on the Publisher and the originating updating Subscriber; the processing of subsequent queued transactions will continue.</span></span> <span data-ttu-id="9425d-189">값 **2** 는 충돌 시 구독자의 내용이 적용되고 지연 트랜잭션이 게시자의 값을 재정의함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-189">A value of **2** indicates the Subscriber wins the conflict, and the queued transaction will override the values on the Publisher.</span></span> <span data-ttu-id="9425d-190">값 **3** 은 충돌이 발생할 경우 구독자가 다시 초기화되고, 게시자의 내용이 적용되고, 이후 지연 트랜잭션의 처리가 종료되며, 구독이 다시 초기화됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-190">A value of **3** indicates that any conflict will result in Subscriber re-initialization; the Publisher wins the conflict, processing of subsequent queued transactions will be terminated, and the subscription will be reinitialized.</span></span> <span data-ttu-id="9425d-191">기본 설정은 트랜잭션 게시의 경우 **1** 이고 스냅샷 게시의 경우 **3** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-191">The default setting is **1** for transactional publications and **3** for snapshot publications.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9425d-192">설명</span><span class="sxs-lookup"><span data-stu-id="9425d-192">Remarks</span></span>  
 <span data-ttu-id="9425d-193">큐 판독기 에이전트를 시작하려면 명령 프롬프트에서 **qrdrsvc.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9425d-193">To start the Queue Reader Agent, execute **qrdrsvc.exe** from the command prompt.</span></span> <span data-ttu-id="9425d-194">자세한 내용은 [복제 에이전트 실행 파일](../concepts/replication-agent-executables-concepts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9425d-194">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9425d-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9425d-195">See Also</span></span>  
 [<span data-ttu-id="9425d-196">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="9425d-196">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
