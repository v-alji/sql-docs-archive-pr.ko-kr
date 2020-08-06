---
title: 원격 처리 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e0d6ade25f5a321e49c748692a961abc369efad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652403"
---
# <a name="remote-processing-analysis-services"></a><span data-ttu-id="c30af-102">원격 처리(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c30af-102">Remote Processing (Analysis Services)</span></span>
  <span data-ttu-id="c30af-103">원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대해 예약된 처리 또는 무인 모드 처리를 실행할 수 있습니다. 여기서 처리 요청은 한 컴퓨터에서 시작되지만 동일한 네트워크상의 다른 컴퓨터에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-103">You can run scheduled or unattended processing on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, where the processing request originates from one computer but executes on another computer on the same network.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c30af-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c30af-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="c30af-105">각 컴퓨터에서 서로 다른 버전의 SQL Server를 실행하는 경우 클라이언트 라이브러리는 모델을 처리하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 버전과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-105">If you are running different versions of SQL Server on each computer, the client libraries must match the version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is processing the model.</span></span> <span data-ttu-id="c30af-106">예를 들어 처리가 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 인스턴스에서 수행되는 경우 요청이 시작되는 컴퓨터에는 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]에 해당하는 클라이언트 라이브러리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-106">For example, if processing is on a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] instance, then the computer from which the request originates must have the client library corresponding to [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span> <span data-ttu-id="c30af-107">[Analysis Services 연결에 사용되는 데이터 공급자](../instances/data-providers-used-for-analysis-services-connections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-107">See [Data providers used for Analysis Services connections](../instances/data-providers-used-for-analysis-services-connections.md).</span></span>  
  
-   <span data-ttu-id="c30af-108">원격 서버에서 **이 컴퓨터에 대한 원격 연결 허용** 을 사용해야 하고 처리 요청을 실행하는 계정이 허용된 사용자로 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-108">On the remote server, **Allow remote connections to this computer** must be enabled, and the account issuing the processing request must be listed as an allowed user.</span></span>  
  
-   <span data-ttu-id="c30af-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대한 인바운드 연결을 허용하도록 Windows 방화벽 규칙을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-109">Windows firewall rules must be configured to allow inbound connections to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c30af-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 원격 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]인스턴스에 연결할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-110">Verify you can connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c30af-111">[Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-111">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="c30af-112">원격 처리를 시도하기 전에 모든 기존 로컬 처리 오류를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-112">Resolve any existing local processing errors before attempting remote processing.</span></span> <span data-ttu-id="c30af-113">처리 요청이 로컬인 경우 외부 관계형 데이터 원본에서 데이터를 검색할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-113">Verify that when the processing request is local, data can be successfully retrieved from the external relational data source.</span></span> <span data-ttu-id="c30af-114">데이터 검색에 사용되는 자격 증명 지정에 대한 지침은 [가장 옵션 설정&#40;SSAS - 다차원&#41;](set-impersonation-options-ssas-multidimensional.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-114">See [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md) for instructions on specifying credentials used to retrieve data.</span></span>  
  
## <a name="on-demand-remote-processing"></a><span data-ttu-id="c30af-115">요청 시 원격 처리</span><span class="sxs-lookup"><span data-stu-id="c30af-115">On-demand remote processing</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c30af-116">는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자 권한이 있는 사용자 또는 애플리케이션 계정의 처리 요청을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-116">accepts processing requests from user or application accounts that have [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator permissions.</span></span> <span data-ttu-id="c30af-117">관리자인 경우 원격 인스턴스에 연결하고 원격 연결을 통해 데이터베이스를 수동으로 처리할 수 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-117">If you are an administrator, verify that you can connect to the remote instance and process the database manually over the remote connection.</span></span>  
  
1.  <span data-ttu-id="c30af-118">처리를 예약하는 데 사용할 컴퓨터에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 시작하고 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-118">On the computer that will be used to schedule processing, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="c30af-119">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **처리**를 선택한 후 **스크립트** 를 가리키고 **새 쿼리 창 동작 스크립팅**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-119">Right-click the database, select **Process**, point to **Script** and choose **Script Action to New Query Window**.</span></span> <span data-ttu-id="c30af-120">처리를 호출하는 데 사용되는 명령이 쿼리 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-120">Commands used to invoke processing will appear in the query window.</span></span>  
  
3.  <span data-ttu-id="c30af-121">**확인** 을 클릭하여 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-121">Click **OK** to begin processing.</span></span>  
  
     <span data-ttu-id="c30af-122">이 작업이 완료되면 예약된 작업에 포함할 수 있는 XMLA 쿼리가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-122">Successful completion of this task provides an XMLA query that you can embed in a scheduled job.</span></span> <span data-ttu-id="c30af-123">또한 연결 문제가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-123">It also confirms there are no connection problems.</span></span>  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a><span data-ttu-id="c30af-124">SQL Server 에이전트 서비스를 사용하여 원격 처리 예약</span><span class="sxs-lookup"><span data-stu-id="c30af-124">Schedule remote processing using SQL Server Agent Service</span></span>  
 <span data-ttu-id="c30af-125">기본적으로 SQL Server 에이전트 서비스는 컴퓨터 계정을 사용하여 설정된 네트워크 연결을 통해 가상 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-125">By default, SQL Server Agent service runs under a virtual account, with network connections made using the machine account.</span></span> <span data-ttu-id="c30af-126">컴퓨터 계정에 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 관리 권한을 부여하지 않으려면 SQL Server 에이전트 서비스 계정을 최소 권한 도메인 사용자 계정으로 실행되도록 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-126">To avoid having to give a machine account administrative rights on the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you should change the SQL Server Agent service account to run as a least-privilege domain user account.</span></span>  
  
 <span data-ttu-id="c30af-127">**sysadmin** 계정에 서비스를 제공하는 데이터베이스 엔진 인스턴스에 대한 권한을 부여하는 것을 비롯하여 필요한 모든 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-127">Be sure to grant all of the necessary permissions, including giving the account **sysadmin** rights on the Database Engine instance providing the service.</span></span>  
  
 <span data-ttu-id="c30af-128">다음 링크를 사용하여 권한을 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-128">Use the following links to set permissions:</span></span>  
  
-   [<span data-ttu-id="c30af-129">SQL Server 에이전트 구성</span><span class="sxs-lookup"><span data-stu-id="c30af-129">Configure SQL Server Agent</span></span>](../../ssms/agent/configure-sql-server-agent.md)  
  
-   <span data-ttu-id="c30af-130">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) 는 **sysadmin** 권한을 부여하는 것이 불가능한 경우 대체 고정 서버 역할을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-130">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) suggests alternative fixed server roles if granting **sysadmin** permissions is not possible.</span></span>  
  
 <span data-ttu-id="c30af-131">계정 권한을 구성한 후 다음 단계를 계속하세요.</span><span class="sxs-lookup"><span data-stu-id="c30af-131">After account permissions are configured, continue with these steps.</span></span>  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a><span data-ttu-id="c30af-132">SSAS에 대한 SQL Server 에이전트 계정 관리자 권한 부여</span><span class="sxs-lookup"><span data-stu-id="c30af-132">Grant the SQL Server Agent account administrator permission on SSAS</span></span>  
  
1.  <span data-ttu-id="c30af-133">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-133">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="c30af-134">서버 이름을 마우스 오른쪽 단추로 클릭하고**속성**을 클릭한 후 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-134">Right-click the server name, click P**roperties**, and then click **Security**.</span></span>  
  
3.  <span data-ttu-id="c30af-135">**추가** 를 클릭하여 SQL Server 에이전트 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-135">Click **Add** to add the SQL Server Agent account.</span></span>  
  
#### <a name="create-the-job"></a><span data-ttu-id="c30af-136">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="c30af-136">Create the Job</span></span>  
  
1.  <span data-ttu-id="c30af-137">Management Studio에서 로컬 데이터베이스 엔진 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-137">In Management Studio, connect to the local Database Engine instance.</span></span> <span data-ttu-id="c30af-138">SQL Server 에이전트는 개체 탐색기의 마지막 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-138">SQL Server Agent is the last item in Object Explorer.</span></span> <span data-ttu-id="c30af-139">필요한 경우 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-139">If necessary, start the service.</span></span>  
  
2.  <span data-ttu-id="c30af-140">**작업**을 마우스 오른쪽 단추로 클릭하고 **새 작업** 을 클릭한 후 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-140">Right-click **Job**s, click **New Job** and then enter a name.</span></span>  
  
3.  <span data-ttu-id="c30af-141">단계에서 **새로 만들기** 를 클릭한 후 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-141">In Steps, click **New** and then enter a name.</span></span>  
  
4.  <span data-ttu-id="c30af-142">유형에서 **SQL Server Analysis Services 명령**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-142">In Type, choose **SQL Server Analysis Services Command**.</span></span>  
  
5.  <span data-ttu-id="c30af-143">서버에 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-143">In Server, enter the name of the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
6.  <span data-ttu-id="c30af-144">명령에 데이터베이스를 처리하기 위한 XMLA 명령을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-144">In Command, paste the XMLA command for processing the database.</span></span> <span data-ttu-id="c30af-145">이 명령은 요청 시 원격 처리에 대한 확인 단계에서 생성한 XMLA 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-145">This is the XMLA script that you generated in the verification step for on-demand remote processing.</span></span> <span data-ttu-id="c30af-146">**확인** 을 클릭하여 작업을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-146">Click **OK** to save the job.</span></span>  
  
#### <a name="start-sql-server-profiler"></a><span data-ttu-id="c30af-147">SQL Server Profiler 시작</span><span class="sxs-lookup"><span data-stu-id="c30af-147">Start SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="c30af-148">원격 컴퓨터에서 SQL Server Profiler를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-148">On the remote computer, start SQL Server Profiler.</span></span> <span data-ttu-id="c30af-149">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결하고 **실행** 을 클릭하여 기본 이벤트를 사용한 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-149">Connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and click **Run** to start the trace using the default events.</span></span>  
  
     <span data-ttu-id="c30af-150">SQL Server Profiler를 사용하여 처리 이벤트를 발생하는 대로 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-150">You will use SQL Server Profiler to monitor the processing events as they occur.</span></span>  
  
2.  <span data-ttu-id="c30af-151">선택적으로 파일 또는 데이터베이스의 테이블로 추적을 보내도록 추적 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-151">Optionally, you can set trace properties to send the trace to a file or table in a database.</span></span>  
  
#### <a name="run-the-job"></a><span data-ttu-id="c30af-152">작업 실행</span><span class="sxs-lookup"><span data-stu-id="c30af-152">Run the job</span></span>  
  
1.  <span data-ttu-id="c30af-153">작업을 실행하는 데 사용되는 컴퓨터에서 작업이 기본 작업을 수행할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-153">On the computer used to run the job, verify that the job can perform the basic operation.</span></span> <span data-ttu-id="c30af-154">개체 탐색기의 SQL Server 에이전트에서 **작업**을 확장하고 방금 만든 작업을 마우스 오른쪽 단추로 클릭한 후 **작업 시작 단계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-154">In Object Explorer, under SQL Server Agent, expand **Jobs**, right-click the job you just created, and click **Start Job at Step**.</span></span> <span data-ttu-id="c30af-155">작업이 즉시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-155">The job starts immediately.</span></span> <span data-ttu-id="c30af-156">SQL Server Profiler에서 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-156">You can monitor progress in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="c30af-157">마지막 단계로, 정의하는 일정으로 실행되도록 작업을 수정하고 작업을 관리하는 데 필요한 경고 또는 알림을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-157">As a final step, modify the job to run on a schedule that you define, adding any alerts or notifications necessary to administer the job.</span></span> <span data-ttu-id="c30af-158">또한 처리 스크립트를 구체화하거나 개체를 독립적으로 처리하기 위해 작업에 여러 단계를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c30af-158">You might also want to refine the processing script, or create multiple steps in the job to process objects independently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30af-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c30af-159">See Also</span></span>  
 <span data-ttu-id="c30af-160">[SQL Server 에이전트 구성 요소](../../ssms/agent/sql-server-agent.md#Components) </span><span class="sxs-lookup"><span data-stu-id="c30af-160">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) </span></span>  
 <span data-ttu-id="c30af-161">[SQL Server 에이전트를 사용 하 여 SSAS 관리 태스크 예약](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="c30af-161">[Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span></span>  
 <span data-ttu-id="c30af-162">[일괄 처리 &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c30af-162">[Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="c30af-163">[다차원 모델 개체 처리](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c30af-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="c30af-164">개체 처리&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="c30af-164">Processing Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
