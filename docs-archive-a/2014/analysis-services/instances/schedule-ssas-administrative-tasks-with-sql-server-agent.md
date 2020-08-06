---
title: SQL Server 에이전트를 사용 하 여 SSAS 관리 작업 예약 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d1484b3-51d9-48a0-93d2-0c3e4ed22b87
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c78fa5fcebc0589ba863163b93ad2d10731b75a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733248"
---
# <a name="schedule-ssas-administrative-tasks-with-sql-server-agent"></a><span data-ttu-id="38abb-102">SQL Server 에이전트를 사용하여 SSAS 관리 태스크 예약</span><span class="sxs-lookup"><span data-stu-id="38abb-102">Schedule SSAS Administrative Tasks with SQL Server Agent</span></span>
  <span data-ttu-id="38abb-103">SQL Server 에이전트 서비스를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리 작업을 예약하여 필요한 순서 및 시간에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-103">Using the SQL Server Agent service, you can schedule [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative tasks to run in the order and times that you need.</span></span> <span data-ttu-id="38abb-104">예약된 태스크를 사용하면 정기적으로 또는 예측 가능한 주기에 따라 프로세스가 자동으로 실행되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-104">Scheduled tasks help you automate processes that run on regular or predictable cycles.</span></span> <span data-ttu-id="38abb-105">비즈니스 활동을 수행하지 않는 시간 동안 큐브 처리 등의 관리 태스크가 실행되도록 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-105">You can schedule administrative tasks, such as cube processing, to run during times of slow business activity.</span></span> <span data-ttu-id="38abb-106">또한 SQL Server 에이전트 작업 내에 작업 단계를 만들어 태스크 실행 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-106">You can also determine the order in which tasks run by creating job steps within a SQL Server Agent job.</span></span> <span data-ttu-id="38abb-107">예를 들어 큐브를 처리한 다음 큐브 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-107">For example, you can process a cube and then perform a backup of the cube.</span></span>  
  
 <span data-ttu-id="38abb-108">작업 단계를 사용하면 실행 흐름을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-108">Job steps give you control over flow of execution.</span></span> <span data-ttu-id="38abb-109">한 작업이 실패한 경우 남아 있는 태스크를 계속 실행하거나 실행을 중지하도록 SQL Server 에이전트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-109">If one job fails, you can configure SQL Server Agent to continue to run the remaining tasks or to stop execution.</span></span> <span data-ttu-id="38abb-110">또한 작업 실행의 성공 또는 실패에 대한 알림을 보내도록 SQL Server 에이전트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-110">You can also configure SQL Server Agent to send notifications about the success or failure of job execution.</span></span>  
  
 <span data-ttu-id="38abb-111">이 항목은 SQL Server 에이전트를 사용하여 XMLA 스크립트를 실행하는 두 가지 방법을 보여 주는 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-111">This topic is a walkthrough that shows two ways of using SQL Server Agent to run XMLA script.</span></span> <span data-ttu-id="38abb-112">첫 번째 예에서는 1차원 처리를 예약하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-112">The first example demonstrates how to schedule processing of a single dimension.</span></span> <span data-ttu-id="38abb-113">예 2에서는 처리 태스크를 일정대로 실행되는 단일 스크립트에 결합하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-113">Example two shows how to combine processing tasks into a single script that runs on a schedule.</span></span> <span data-ttu-id="38abb-114">이 연습을 완료하려면 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-114">To complete this walkthrough, you will need to meet the following prerequisites.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="38abb-115">전제 조건</span><span class="sxs-lookup"><span data-stu-id="38abb-115">Prerequisites</span></span>  
 <span data-ttu-id="38abb-116">SQL Server 에이전트 서비스가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-116">SQL Server Agent service must be installed.</span></span>  
  
 <span data-ttu-id="38abb-117">기본적으로 서비스 계정으로 작업이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-117">By default, jobs run under the service account.</span></span> <span data-ttu-id="38abb-118">에서 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQL Server 에이전트의 기본 계정은 NT Service\SQLAgent $입니다 \<instancename> .</span><span class="sxs-lookup"><span data-stu-id="38abb-118">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the default account for SQL Server Agent is NT Service\SQLAgent$\<instancename>.</span></span> <span data-ttu-id="38abb-119">백업 또는 처리 태스크를 수행하려면 이 계정이 Analysis Services 인스턴스의 시스템 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-119">To perform a backup or processing task, this account must be a system administrator on the Analysis Services instance.</span></span> <span data-ttu-id="38abb-120">자세한 내용은 [Analysis Services&#41;&#40;서버 관리자 권한 부여 ](grant-server-admin-rights-to-an-analysis-services-instance.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38abb-120">For more information, see [Grant Server Administrator Permissions &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="38abb-121">또한 작업에 사용할 테스트 데이터베이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-121">You should also have a test database to work with.</span></span> <span data-ttu-id="38abb-122">AdventureWorks 다차원 예제 데이터베이스나 Analysis Services 다차원 자습서에 있는 프로젝트를 배포하여 이 연습에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-122">You can deploy the AdventureWorks multidimensional sample database or a project from the Analysis Services multidimensional tutorial to use in this walkthrough.</span></span> <span data-ttu-id="38abb-123">자세한 내용은 [Analysis Services 다차원 모델링 자습서에 대 한 샘플 데이터 및 프로젝트 설치](../install-sample-data-and-projects.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38abb-123">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md).</span></span>  
  
## <a name="example-1-processing-a-dimension-in-a-scheduled-task"></a><span data-ttu-id="38abb-124">예제 1: 예약된 태스크에서 차원 처리</span><span class="sxs-lookup"><span data-stu-id="38abb-124">Example 1: Processing a dimension in a scheduled task</span></span>  
 <span data-ttu-id="38abb-125">이 예에서는 차원을 처리하는 작업을 만들고 예약하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-125">This example demonstrates how to create and schedule a job that processes a dimension.</span></span>  
  
 <span data-ttu-id="38abb-126">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 예약된 태스크는 SQL Server 에이전트 작업에 포함되는 XMLA 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-126">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] scheduled task is an XMLA script that is embedded into a SQL Server Agent job.</span></span> <span data-ttu-id="38abb-127">이 작업은 원하는 시간 또는 빈도로 실행하도록 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-127">This job is scheduled to run at desired times and frequency.</span></span> <span data-ttu-id="38abb-128">SQL Server 에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 일부이므로 데이터베이스 엔진 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 관리 태스크를 만들고 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-128">Because the SQL Server Agent is part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you work with both the Database Engine and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create and schedule an administrative task.</span></span>  
  
###  <a name="create-a-script-for-processing-a-dimension-in-a-sql-server-agent-job"></a><a name="bkmk_CreateScript"></a> <span data-ttu-id="38abb-129">SQL Server 에이전트 작업에서 차원 처리를 위한 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="38abb-129">Create a script for processing a dimension in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="38abb-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="38abb-131">데이터베이스 폴더를 열고 차원을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-131">Open a database folder and find a dimension.</span></span> <span data-ttu-id="38abb-132">차원을 마우스 오른쪽 단추로 클릭하고 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-132">Right-click the dimension and select **Process**.</span></span>  
  
2.  <span data-ttu-id="38abb-133">**차원 처리** 대화 상자에 있는 **개체 목록** 의 **처리 옵션**열에서 이 열에 대한 옵션이 **전체 처리**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-133">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="38abb-134">그렇지 않을 경우 **처리 옵션**에서 해당 옵션을 클릭하고 드롭다운 목록에서 **전체 처리** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-134">If it is not, under **Process Options**, click the option, and then select **Process Full** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="38abb-135">**스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-135">Click **Script**.</span></span>  
  
     <span data-ttu-id="38abb-136">이 단계에서 차원을 처리하는 XMLA 스크립트가 포함된 **XML 쿼리** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-136">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="38abb-137">**차원 처리** 대화 상자에서 **취소** 를 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-137">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="38abb-138">**XMLA 쿼리** 창에서 XMLA 스크립트를 강조 표시하고 강조된 스크립트를 마우스 오른쪽 단추로 클릭한 후 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-138">In the **XMLA Query** window, highlight the XMLA script, right-click the highlighted script, and select **Copy**.</span></span>  
  
     <span data-ttu-id="38abb-139">이 단계에서 XMLA 스크립트를 Windows 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-139">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="38abb-140">XMLA 스크립트를 클립보드에 남겨 두거나 메모장 또는 다른 텍스트 편집기에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-140">You can leave the XMLA script in the Clipboard or paste it into Notepad or another text editor.</span></span> <span data-ttu-id="38abb-141">다음은 XMLA 스크립트의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-141">The following is an example of the XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Account</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
###  <a name="create-and-schedule-the-dimension-processing-job"></a><a name="bkmk_ProcessJob"></a> <span data-ttu-id="38abb-142">차원 처리 작업 만들기 및 예약</span><span class="sxs-lookup"><span data-stu-id="38abb-142">Create and schedule the dimension processing job</span></span>  
  
1.  <span data-ttu-id="38abb-143">데이터베이스 엔진 인스턴스에 연결한 후 개체 탐색기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-143">Connect to an instance of the Database Engine and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="38abb-144">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-144">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="38abb-145">**작업** 을 마우스 오른쪽 단추로 클릭하고 **새 작업**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-145">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="38abb-146">**새 작업** 대화 상자에서 **이름**에 작업 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-146">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="38abb-147">**페이지 선택**에서 **단계**를 선택하고 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-147">Under **Select a page**, select **Steps**, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="38abb-148">**새 작업 단계** 대화 상자에서 **단계 이름**에 단계 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-148">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="38abb-149">**서버**에의 기본 인스턴스에 대해 **localhost** 를 입력 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 하 고 명명 된 인스턴스의 경우 \*\* \\ localhost\*\* 를 입력 \<*instance name*> 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-149">In **Server**, type **localhost** for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and **localhost\\**\<*instance name*> for a named instance.</span></span>  
  
     <span data-ttu-id="38abb-150">원격 컴퓨터에서 작업을 실행하려는 경우 작업을 실행할 서버 이름과 인스턴스 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-150">If you will be running the job from a remote computer, use the server name and instance name where the job will run.</span></span> <span data-ttu-id="38abb-151">\<*server name*>명명 된 인스턴스에 대 한 기본 인스턴스 및 \<*server name*> \\ < *인스턴스 이름*> 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-151">Use the format \<*server name*> for a default instance, and \<*server name*>\\<*instance name*> for a named instance.</span></span>  
  
8.  <span data-ttu-id="38abb-152">**유형**에서 **SQL Server Analysis Services 명령**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-152">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
9. <span data-ttu-id="38abb-153">**명령**에서 마우스 오른쪽 단추를 클릭하고 **붙여넣기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-153">In **Command**, right-click and select **Paste**.</span></span> <span data-ttu-id="38abb-154">이전 단계에서 생성한 XMLA 스크립트가 명령 창에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-154">The XMLA script that you generated in the previous step should appear in the command window.</span></span>  
  
10. <span data-ttu-id="38abb-155">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-155">Click **OK**.</span></span>  
  
11. <span data-ttu-id="38abb-156">**페이지 선택**에서 **일정**을 클릭한 후 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-156">Under **Select a page**, click **Schedules**, and then click **New**.</span></span>  
  
12. <span data-ttu-id="38abb-157">**새 작업 일정** 대화 상자에서 **이름**에 일정 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-157">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="38abb-158">이 단계에서 일요일 오전 12시 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-158">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="38abb-159">다음 단계에서는 수동으로 작업을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-159">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="38abb-160">모니터링할 때 작업을 실행하는 일정을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-160">You can also specify a schedule that executes the job when you are monitoring it.</span></span>  
  
13. <span data-ttu-id="38abb-161">**새 작업** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-161">In the **New Job** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="38abb-162">**개체 탐색기**에서 **작업**을 확장하고 만들어진 작업을 마우스 오른쪽 단추로 클릭한 후 **작업 시작 단계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-162">In **Object Explorer**, expand **Jobs**, right-click the job you created, and then select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="38abb-163">작업에 단계가 하나뿐이므로 작업이 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-163">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="38abb-164">작업에 둘 이상의 단계가 있으면 작업을 시작할 단계를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-164">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
15. <span data-ttu-id="38abb-165">작업이 끝나면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-165">When the job finishes, click **Close**.</span></span>  
  
## <a name="example-2-batch-processing-a-dimension-and-a-partition-in-a-scheduled-task"></a><span data-ttu-id="38abb-166">예제 2: 예약된 태스크에서 차원 및 파티션 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="38abb-166">Example 2: Batch processing a dimension and a partition in a scheduled task</span></span>  
 <span data-ttu-id="38abb-167">이 예의 절차는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 차원을 일괄 처리하는 작업을 만들고 예약하는 동시에 집계를 위해 차원에 종속되는 큐브 파티션을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-167">The procedures in this example demonstrate how to create and schedule a job that batch processes an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database dimension, and at the same time to process a  cube partition that depends on the dimension for aggregation.</span></span> <span data-ttu-id="38abb-168">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체 일괄 처리에 대한 자세한 내용은 [일괄 처리&#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38abb-168">For more information about batch processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Batch Processing &#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md).</span></span>  
  
###  <a name="create-a-script-for-batch-processing-a-dimension-and-partition-in-a-sql-server-agent-job"></a><a name="bkmk_BatchProcess"></a><span data-ttu-id="38abb-169">SQL Server 에이전트 작업에서 차원 및 파티션 일괄 처리를 위한 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="38abb-169">Create a script for batch processing a dimension and partition in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="38abb-170">같은 데이터베이스를 사용하여 **차원**을 확장하고 **고객** 차원을 마우스 오른쪽 단추로 클릭한 다음 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-170">Using the same database, expand **Dimensions**, right-click the **Customer** dimension, and select **Process**.</span></span>  
  
2.  <span data-ttu-id="38abb-171">**차원 처리** 대화 상자에 있는 **개체 목록** 의 **처리 옵션**열에서 이 열에 대한 옵션이 **전체 처리**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-171">In the **Process Dimension** dialog box, in **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
3.  <span data-ttu-id="38abb-172">**스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-172">Click **Script**.</span></span>  
  
     <span data-ttu-id="38abb-173">이 단계에서 차원을 처리하는 XMLA 스크립트가 포함된 **XML 쿼리** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-173">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="38abb-174">**차원 처리** 대화 상자에서 **취소** 를 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-174">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="38abb-175">**큐브**, **Adventure Works**, **측정값 그룹**, **인터넷 판매**, **파티션**을 차례로 확장하고 목록의 마지막 파티션을 마우스 오른쪽 단추로 클릭한 다음 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-175">Expand **Cubes**, expand **Adventure Works**, expand **Measure Groups**, expand **Internet Sales**, expand **Partitions**, right-click the last partition in the list, and then select **Process**.</span></span>  
  
6.  <span data-ttu-id="38abb-176">**파티션 처리** 대화 상자에 있는 **개체 목록** 의 **처리 옵션**열에서 이 열에 대한 옵션이 **전체 처리**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-176">In the **Process Partition** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
7.  <span data-ttu-id="38abb-177">**스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-177">Click **Script**.</span></span>  
  
     <span data-ttu-id="38abb-178">이 단계에서 파티션을 처리하는 XMLA 스크립트가 포함된 두 번째 **XML 쿼리** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-178">This step opens a second **XML Query** window that contains the XMLA script that processes the partition.</span></span>  
  
8.  <span data-ttu-id="38abb-179">**파티션 처리** 대화 상자에서 **취소** 를 클릭하여 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-179">In the **Process Partition** dialog box, click **Cancel** to close the editor.</span></span>  
  
     <span data-ttu-id="38abb-180">이때 두 스크립트를 병합하고 차원이 먼저 처리되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-180">At this point you must merge the two scripts, and ensure that the dimension is processed first.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="38abb-181">파티션이 먼저 처리되고 이후에 차원이 처리되면 파티션이 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-181">If the partition is processed first, the subsequent dimension processing causes the partition to become unprocessed.</span></span> <span data-ttu-id="38abb-182">파티션을 두 번째로 처리해야 처리됨 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-182">The partition would then require a second processing to reach a processed state.</span></span>  
  
9. <span data-ttu-id="38abb-183">파티션을 처리하는 XMLA 스크립트가 포함된 **XMLA 쿼리** 창에서 `Batch` 및 `Parallel` 태그 안의 코드를 강조 표시하고 강조된 스크립트를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-183">In the **XMLA Query** window that contains the XMLA script that processes the partition, highlight the code inside the `Batch` and `Parallel` tags, right-click the highlighted script, and select **Copy**.</span></span>  
  
    ```  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID> Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
    ```  
  
10. <span data-ttu-id="38abb-184">차원을 처리하는 XMLA 스크립트가 포함된 **XMLA 쿼리** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-184">Open the **XMLA Query** window that contains the XMLA script that processes the dimension.</span></span> <span data-ttu-id="38abb-185">`</Process>` 태그 왼쪽의 스크립트 내부를 마우스 오른쪽 단추로 클릭하고 **붙여넣기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-185">Right-click within the script to the left of the `</Process>` tag and select **Paste**.</span></span>  
  
     <span data-ttu-id="38abb-186">다음 예에서는 수정된 XMLA 스크립트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-186">The following example shows the revised XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Customer</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID>Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
11. <span data-ttu-id="38abb-187">수정된 XMLA 스크립트를 강조 표시하고 강조된 스크립트를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-187">Highlight the revised XMLA script, right-click the highlighted script, and select **Copy.**</span></span>  
  
12. <span data-ttu-id="38abb-188">이 단계에서 XMLA 스크립트를 Windows 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-188">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="38abb-189">XMLA 스크립트를 클립보드에 남겨 두거나 파일에 저장하거나 메모장 또는 다른 텍스트 편집기에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-189">You can leave the XMLA script in the Clipboard, save it to a file, or paste it into Notepad or another text editor.</span></span>  
  
###  <a name="create-and-schedule-the-batch-processing-job"></a><a name="bkmk_Scheduling"></a> <span data-ttu-id="38abb-190">일괄 처리 작업 만들기 및 예약</span><span class="sxs-lookup"><span data-stu-id="38abb-190">Create and schedule the batch processing job</span></span>  
  
1.  <span data-ttu-id="38abb-191">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 후 개체 탐색기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-191">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="38abb-192">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-192">Expand **SQL Server Agent**.</span></span> <span data-ttu-id="38abb-193">서비스가 실행되지 않았으면 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-193">Start the service if is not running.</span></span>  
  
3.  <span data-ttu-id="38abb-194">**작업** 을 마우스 오른쪽 단추로 클릭하고 **새 작업**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-194">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="38abb-195">**새 작업** 대화 상자에서 **이름**에 작업 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-195">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="38abb-196">**단계**에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-196">In **Steps**, click **New**.</span></span>  
  
6.  <span data-ttu-id="38abb-197">**새 작업 단계** 대화 상자에서 **단계 이름**에 단계 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-197">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="38abb-198">**유형**에서 **SQL Server Analysis Services 명령**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-198">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
8.  <span data-ttu-id="38abb-199">**다음 계정으로 실행**에서 **SQL Server 에이전트 서비스 계정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-199">In **Run as**, select the **SQL Server Agent Service Account**.</span></span> <span data-ttu-id="38abb-200">사전 요구 사항 섹션에서 설명한 대로 이 계정에는 Analysis Services에 대한 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-200">Recall from the Prerequisites section that this account must have administrative permissions on Analysis Services.</span></span>  
  
9. <span data-ttu-id="38abb-201">**서버**에서 Analysis Services 인스턴스의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-201">In **Server**, specify the server name of the Analysis Services instance.</span></span>  
  
10. <span data-ttu-id="38abb-202">**명령**에서 마우스 오른쪽 단추를 클릭하고 **붙여넣기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-202">In **Command**, right-click and select **Paste**.</span></span>  
  
11. <span data-ttu-id="38abb-203">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-203">Click **OK**.</span></span>  
  
12. <span data-ttu-id="38abb-204">**일정** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-204">In the **Schedules** page, click **New**.</span></span>  
  
13. <span data-ttu-id="38abb-205">**새 작업 일정** 대화 상자에서 **이름**에 일정 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-205">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="38abb-206">이 단계에서 일요일 오전 12시 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-206">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="38abb-207">다음 단계에서는 수동으로 작업을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-207">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="38abb-208">모니터링할 때 작업을 실행할 일정을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-208">You can also select a schedule which will execute the job when you are monitoring it.</span></span>  
  
14. <span data-ttu-id="38abb-209">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-209">Click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="38abb-210">**개체 탐색기**에서 **작업**을 확장하고 만들어진 작업을 마우스 오른쪽 단추로 클릭한 후 **작업 시작 단계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-210">In **Object Explorer**, expand **Jobs**, right-click the job you created, and select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="38abb-211">작업에 단계가 하나뿐이므로 작업이 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-211">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="38abb-212">작업에 둘 이상의 단계가 있으면 작업을 시작할 단계를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-212">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
16. <span data-ttu-id="38abb-213">작업이 끝나면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38abb-213">When the job finishes, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38abb-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38abb-214">See Also</span></span>  
 <span data-ttu-id="38abb-215">[처리 옵션 및 설정 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="38abb-215">[Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span></span>  
 [<span data-ttu-id="38abb-216">Analysis Services의 스크립트 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="38abb-216">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  
