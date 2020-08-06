---
title: 유지 관리 계획 마법사 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.ag.maintwiz.planprop.f1
- sql12.ag.maintwiz.task.f1
- sql12.ag.maintwiz.maintcleanup.f1
- sql12.ag.maintwiz.indexdefrag.f1
- sql12.ag.maintwiz.order.f1
- sql12.ag.maintwiz.histcleanup.f1
- sql12.ag.maintwiz.backuplog.f1
- sql12.ag.maintwiz.progress.f1
- sql12.ag.maintwiz.execagentjob.f1
- sql12.ag.maintwiz.integrity.f1
- sql12.ag.maintwiz.welcome.f1
- sql12.ag.maintwiz.backupdiff.f1
- sql12.ag.maintwiz.server.f1
- sql12.ag.maintwiz.summary.f1
- sql12.ag.maintwiz.backupfull.f1
- sql12.ag.maintwiz.report.f1
- sql12.ag.maintwiz.shrinkdb.f1
- sql12.ag.maintwiz.reindex.f1
- sql12.ag.maintwiz.updatestats.f1
helpviewer_keywords:
- Maintenance Plan Wizard
- Database Maintenance Plan Wizard
- Database Maintenance Plan Wizard, starting
ms.assetid: db65c726-9892-480c-873b-3af29afcee44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac134bbd4c65da4700990b69b09134230e98903f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647694"
---
# <a name="use-the-maintenance-plan-wizard"></a><span data-ttu-id="3eef1-102">유지 관리 계획 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="3eef1-102">Use the Maintenance Plan Wizard</span></span>
  <span data-ttu-id="3eef1-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 유지 관리 계획 마법사를 사용하여 단일 서버 또는 다중 서버 유지 관리 계획을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Wizard in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3eef1-104">유지 관리 계획 마법사는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 정기적으로 실행할 수 있는 유지 관리 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-104">The Maintenance Plan Wizard creates a maintenance plan that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can run on a regular basis.</span></span> <span data-ttu-id="3eef1-105">이를 통해 백업, 데이터베이스 무결성 확인 또는 지정된 간격으로 데이터베이스 통계 업데이트와 같은 다양한 데이터베이스 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-105">This allows you to perform various database administration tasks, including backups, database integrity checks, or database statistics updates, at specified intervals.</span></span>  
  
 <span data-ttu-id="3eef1-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3eef1-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3eef1-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3eef1-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3eef1-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3eef1-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3eef1-109">보안</span><span class="sxs-lookup"><span data-stu-id="3eef1-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="3eef1-110">SQL Server Management Studio에서 유지 관리 계획 마법사를 사용하여 유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="3eef1-110">Creating a maintenance plan using the Maintenance Plan Wizard in SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3eef1-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3eef1-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3eef1-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3eef1-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3eef1-113">다중 서버 유지 관리 계획을 만들려면 하나의 마스터 서버 및 하나 이상의 대상 서버가 있는 다중 서버 환경을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-113">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="3eef1-114">다중 서버 유지 관리 계획은 마스터 서버에서 만들고 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-114">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="3eef1-115">이러한 계획을 대상 서버에서 볼 수 있지만 유지 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-115">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="3eef1-116">**db_ssisadmin** 및 **dc_admin** 역할의 멤버는 해당 권한을 **sysadmin**으로 승격할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-116">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="3eef1-117">이러한 권한 승격이 발생할 수 있는 것은 이러한 역할이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 수정할 수 있고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **에이전트의** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 컨텍스트를 사용하여 이러한 패키지를 실행할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-117">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3eef1-118">유지 관리 계획, 데이터 컬렉션 집합 및 기타 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 때 이러한 권한 상승이 발생하지 않도록 하려면 패키지를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 제한된 권한을 갖는 프록시 계정을 사용하도록 구성하거나 **db_ssisadmin** 및 **dc_admin** 역할에 **sysadmin** 멤버만 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-118">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3eef1-119">보안</span><span class="sxs-lookup"><span data-stu-id="3eef1-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3eef1-120">권한</span><span class="sxs-lookup"><span data-stu-id="3eef1-120">Permissions</span></span>  
 <span data-ttu-id="3eef1-121">유지 관리 계획을 만들거나 관리하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-121">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="3eef1-122">개체 탐색기에 **sysadmin** 고정 서버 역할의 멤버인 사용자에 대한 **유지 관리 계획** 노드만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-122">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-wizard"></a><a name="SSMSProcedure"></a><span data-ttu-id="3eef1-123">유지 관리 계획 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="3eef1-123">Using Maintenance Plan Wizard</span></span>  
  
#### <a name="to-start-the-maintenance-plan-wizard"></a><span data-ttu-id="3eef1-124">유지 관리 계획 마법사를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="3eef1-124">To start the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="3eef1-125">유지 관리 계획을 만들 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-125">Expand the server where you want to create your management plan.</span></span>  
  
2.  <span data-ttu-id="3eef1-126">**관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-126">Expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="3eef1-127">**유지 관리 계획** 폴더를 마우스 오른쪽 단추로 클릭하고 **유지 관리 계획 마법사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-127">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="3eef1-128">**SQL Server 유지 관리 계획 마법사** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-128">On the **SQL Server Maintenance Plan Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="3eef1-129">**계획 속성 선택** 페이지에서:</span><span class="sxs-lookup"><span data-stu-id="3eef1-129">On the **Select Plan Properties** page:</span></span>  
  
    1.  <span data-ttu-id="3eef1-130">**이름** 상자에 만들 유지 관리 계획의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-130">In the **Name** box, enter the name of the maintenance plan you are creating.</span></span>  
  
    2.  <span data-ttu-id="3eef1-131">**설명** 상자에 유지 관리 계획에 대한 간략한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-131">In the **Description** box, briefly describe your maintenance plan.</span></span>  
  
    3.  <span data-ttu-id="3eef1-132">**다음 계정으로 실행** 목록에서 Microsoft SQL Server 에이전트가 유지 관리 계획을 실행할 때 사용하는 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-132">In the **Run as** list, specify the credential that Microsoft SQL Server Agent uses when executing the maintenance plan.</span></span>  
  
    4.  <span data-ttu-id="3eef1-133">**각 태스크에 별도의 일정** 또는 **전체 계획에 하나의 일정 또는 일정 없음** 을 선택하여 유지 관리 계획의 되풀이 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-133">Select either **Separate schedules for each task** or **Single schedule for the entire plan or no schedule** to specify the recurring schedule of the maintenance plan.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3eef1-134">**각 태스크에 별도의 일정**을 선택할 경우 **e.** 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-134">If you select **Separate schedules for each task**, you will need to follow the steps in **e.**</span></span> <span data-ttu-id="3eef1-135">단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-135">below for each task in your maintenance plan.</span></span>  
  
    5.  <span data-ttu-id="3eef1-136">**전체 계획에 하나의 일정 또는 일정 없음**을 선택하는 경우에는 **일정**아래에서 **변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-136">If you selected **Single schedule for the entire plan or no schedule**, under **Schedule**, click **Change**.</span></span>  
  
        1.  <span data-ttu-id="3eef1-137">**새 작업 일정** 대화 상자의 **이름** 상자에 작업 일정 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-137">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
        2.  <span data-ttu-id="3eef1-138">**일정 유형** 목록에서 다음과 같은 일정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-138">On the **Schedule type** list, select the type of schedule:</span></span>  
  
            -   <span data-ttu-id="3eef1-139">**SQL Server 에이전트가 시작될 때 자동으로 시작**</span><span class="sxs-lookup"><span data-stu-id="3eef1-139">**Start automatically when SQL Server Agent starts**</span></span>  
  
            -   <span data-ttu-id="3eef1-140">**CPU가 유휴 상태로 될 때마다 시작**</span><span class="sxs-lookup"><span data-stu-id="3eef1-140">**Start whenever the CPUs become idle**</span></span>  
  
            -   <span data-ttu-id="3eef1-141">**되풀이**.</span><span class="sxs-lookup"><span data-stu-id="3eef1-141">**Recurring**.</span></span> <span data-ttu-id="3eef1-142">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-142">This is the default selection.</span></span>  
  
            -   <span data-ttu-id="3eef1-143">**한 번**</span><span class="sxs-lookup"><span data-stu-id="3eef1-143">**One time**</span></span>  
  
        3.  <span data-ttu-id="3eef1-144">일정을 사용하거나 사용하지 않으려면 **사용** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-144">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
        4.  <span data-ttu-id="3eef1-145">**되풀이**를 선택하는 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-145">If you select **Recurring**:</span></span>  
  
            1.  <span data-ttu-id="3eef1-146">**빈도**아래의 **되풀이** 목록에서 다음과 같이 발생 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-146">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
                -   <span data-ttu-id="3eef1-147">**일별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 일 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-147">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
                -   <span data-ttu-id="3eef1-148">**주별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 주 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-148">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="3eef1-149">작업 일정을 실행할 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-149">Select the day or days of the week on which the job schedule is run.</span></span>  
  
                -   <span data-ttu-id="3eef1-150">**월별**을 선택한 경우 **매(Day)** 또는 **매(The)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-150">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                    -   <span data-ttu-id="3eef1-151">**매(Day)** 를 선택한 경우 작업 일정을 실행할 날짜와 작업 일정을 반복할 월 수를 모두 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-151">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="3eef1-152">예를 들어 작업 일정을 격월로 15일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 상자에 "15", 두 번째 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-152">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="3eef1-153">두 번째 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-153">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                    -   <span data-ttu-id="3eef1-154">**매(The)** 를 선택한 경우 작업 일정을 실행할 요일 및 작업 일정을 반복할 월 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-154">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="3eef1-155">예를 들어 작업 일정을 격월로 마지막 평일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 목록에서 **마지막**, 두 번째 목록에서 **평일**을 선택한 다음, 마지막 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-155">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="3eef1-156">**첫 번째**, **두 번째**, **세 번째** 또는 **네 번째** 또는 특정 평일(예: 일요일 또는 수요일)을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-156">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="3eef1-157">마지막 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-157">Please note that the largest number allowed in the last box is "99".</span></span>  
  
            2.  <span data-ttu-id="3eef1-158">**일별 빈도**에서 작업 일정이 실행되는 날에 작업 일정을 반복하는 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-158">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
                -   <span data-ttu-id="3eef1-159">**한 번 수행**을 선택하는 경우 **한 번 수행** 상자에 작업 일정을 실행할 특정 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-159">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="3eef1-160">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-160">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
                -   <span data-ttu-id="3eef1-161">**되풀이 수행**을 선택하는 경우 **빈도**에 선택한 날 동안 작업 일정을 실행할 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-161">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="3eef1-162">예를 들어 작업 일정을 실행하는 날에 2시간마다 작업 일정을 반복하려면 **되풀이 수행**을 선택하고 첫 번째 상자에 "2"를 입력한 다음, 목록에서 **시간**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-162">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="3eef1-163">이 목록에서 **분** 과 **초**도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-163">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="3eef1-164">첫 번째 상자에 허용되는 가장 큰 숫자는 "100"입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-164">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                     <span data-ttu-id="3eef1-165">**시작** 상자에 작업 일정 실행을 시작할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-165">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="3eef1-166">**종료** 상자에 작업 일정 반복을 중지할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-166">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="3eef1-167">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-167">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            3.  <span data-ttu-id="3eef1-168">**기간**아래의 **시작 날짜**에 작업 일정 실행을 시작할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-168">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="3eef1-169">**종료 날짜** 또는 **종료 날짜 없음** 을 선택하여 작업 일정 실행을 중지할 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-169">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="3eef1-170">**종료 날짜**를 선택하는 경우 작업 일정 실행을 중지할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-170">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
        5.  <span data-ttu-id="3eef1-171">**한 번**을 선택하는 경우 **한 번 발생**아래 **날짜** 상자에 작업 일정을 실행할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-171">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="3eef1-172">**시간** 상자에 작업 일정을 실행할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-172">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="3eef1-173">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-173">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        6.  <span data-ttu-id="3eef1-174">**요약**아래 **설명**에서 모든 작업 일정 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-174">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
        7.  <span data-ttu-id="3eef1-175">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-175">Click **OK**.</span></span>  
  
    6.  <span data-ttu-id="3eef1-176">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-176">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3eef1-177">**대상 서버 선택** 페이지에서 유지 관리 계획을 실행할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-177">On the **Select Target Servers** page, select the servers where you want to run the maintenance plan.</span></span> <span data-ttu-id="3eef1-178">이 페이지는 마스터 서버로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-178">This page is only visible on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances that are configured as master servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eef1-179">다중 서버 유지 관리 계획을 만들려면 하나의 마스터 서버와 하나 이상의 대상 서버가 있는 다중 서버 환경을 구성하고 로컬 서버를 마스터 서버로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-179">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured, and the local server should be configured as a master server.</span></span> <span data-ttu-id="3eef1-180">다중 서버 환경에서 이 페이지에는 **(로컬)** 마스터 서버와 해당하는 모든 대상 서버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-180">In multiserver environments, this page displays the **(local)** master server and all corresponding target servers.</span></span>  
  
7.  <span data-ttu-id="3eef1-181">**유지 관리 태스크 선택** 페이지에서 계획에 추가할 유지 관리 태스크를 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-181">On the **Select Maintenance Tasks** page, select one or more maintenance tasks to add to the plan.</span></span> <span data-ttu-id="3eef1-182">필요한 태스크를 모두 선택했으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-182">When you have selected all of the necessary tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eef1-183">여기에서 선택하는 태스크에 따라 아래의 **유지 관리 태스크 순서 선택** 페이지 다음에 완료해야 하는 페이지가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-183">The tasks you select here will determine which pages you will need to complete after the **Select Maintenance Task Order** page below.</span></span>  
  
8.  <span data-ttu-id="3eef1-184">**유지 관리 태스크 순서 선택** 페이지에서 태스크를 선택하고 **위로 이동...** 또는 **아래로 이동...** 을 클릭하여 태스크의 실행 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-184">On the **Select Maintenance Task Order** page, select a task and click either **Move Up...** or **Move Down...** to change its order of execution.</span></span> <span data-ttu-id="3eef1-185">완료했거나 현재 태스크 순서에 만족하면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-185">When finished, or if you are satisfied with the current order of tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eef1-186">위의 **계획 속성 선택** 페이지에서 **각 태스크에 별도의 일정**을 선택한 경우 이 페이지에서 유지 관리 태스크의 순서를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-186">If you selected **Separate schedules for each task** on the **Select Plan Properties** page above, you will not be able to change the order of the maintenance tasks on this page.</span></span>  
  
#### <a name="define-database-check-integrity-checkdb-tasks"></a><span data-ttu-id="3eef1-187">데이터베이스 무결성 검사(CHECKDB) 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-187">Define Database Check Integrity (CHECKDB) Tasks</span></span>  
  
1.  <span data-ttu-id="3eef1-188">**데이터베이스 무결성 검사 태스크 정의** 페이지에서 사용자와 시스템 테이블 및 인덱스의 할당 및 구조적 무결성을 검사할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-188">On the **Define Database Check Integrity Task** page, choose the database or databases where the allocation and structural integrity of user and system tables and indexes will be checked.</span></span> <span data-ttu-id="3eef1-189">이 태스크에서는 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 데이터베이스의 모든 무결성 문제를 보고하므로 시스템 관리자나 데이터베이스 소유자가 나중에 이러한 문제를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-189">By running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement, this task ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span> <span data-ttu-id="3eef1-190">자세한 내용은 [DBCC CHECKDB&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)를 참조하세요. 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-190">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-191">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-191">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-192">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-192">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-193">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-193">Specify the databases affected by this task.</span></span>  
  
    -   <span data-ttu-id="3eef1-194">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="3eef1-194">**All databases**</span></span>  
  
         <span data-ttu-id="3eef1-195">**tempdb**를 제외한 모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 이 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-195">Generate a maintenance plan that runs this task against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
    -   <span data-ttu-id="3eef1-196">**시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="3eef1-196">**System databases**</span></span>  
  
         <span data-ttu-id="3eef1-197">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **및 사용자가 만든 데이터베이스를 제외한** 시스템 데이터베이스에 대해 이 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-197">Generate a maintenance plan that runs this task against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb** and user-created databases.</span></span>  
  
    -   <span data-ttu-id="3eef1-198">**모든 사용자 데이터베이스(master, model, msdb, tempdb 제외)**</span><span class="sxs-lookup"><span data-stu-id="3eef1-198">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
  
         <span data-ttu-id="3eef1-199">사용자가 만든 모든 데이터베이스에 대해 이 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-199">Generate a maintenance plan that runs this task against all user-created databases.</span></span> <span data-ttu-id="3eef1-200">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-200">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
    -   <span data-ttu-id="3eef1-201">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="3eef1-201">**These databases**</span></span>  
  
         <span data-ttu-id="3eef1-202">선택한 데이터베이스에 대해서만 이 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-202">Generate a maintenance plan that runs this task against only those databases that are selected.</span></span> <span data-ttu-id="3eef1-203">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-203">At least one database in the list must be selected if this option is chosen.</span></span>  
  
     <span data-ttu-id="3eef1-204">**인덱스 포함** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-204">**Include indexes** check box</span></span>  
     <span data-ttu-id="3eef1-205">모든 인덱스 페이지와 테이블 데이터 페이지가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-205">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
#### <a name="define-database-shrink-tasks"></a><span data-ttu-id="3eef1-206">데이터베이스 축소 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-206">Define Database Shrink Tasks</span></span>  
  
1.  <span data-ttu-id="3eef1-207">**데이터베이스 축소 태스크 정의** 페이지에서 `DBCC SHRINKDATABASE` 또는 `NOTRUNCATE` 옵션과 함께 `TRUNCATEONLY` 문을 사용하여 선택한 데이터베이스의 크기를 축소하는 태스크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-207">On the **Define Shrink Database Task** page, create a task that attempts to reduce the size of the selected databases by using the `DBCC SHRINKDATABASE` statement, with either the `NOTRUNCATE` or `TRUNCATEONLY` option.</span></span> <span data-ttu-id="3eef1-208">자세한 내용은 [DBCC SHRINKDATABASE&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-208">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span> <span data-ttu-id="3eef1-209">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-209">When complete, click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="3eef1-210">파일 축소를 위해 이동되는 데이터는 파일 내의 모든 사용 가능한 위치로 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-210">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="3eef1-211">이로 인해 인덱스 조각화가 발생하여 인덱스 범위를 검색하는 쿼리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-211">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="3eef1-212">조각화를 방지하려면 축소 후 파일에 대한 인덱스를 다시 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-212">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
     <span data-ttu-id="3eef1-213">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-213">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-214">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-214">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-215">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-215">Specify the databases affected by this task.</span></span> <span data-ttu-id="3eef1-216">이 목록에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 9단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-216">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="3eef1-217">**데이터베이스 크기가 다음을 초과하면 축소** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-217">**Shrink database when it grows beyond** box</span></span>  
     <span data-ttu-id="3eef1-218">데이터베이스 축소 태스크를 시작하는 기준이 되는 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-218">Specify the size in megabytes that causes the task to execute.</span></span>  
  
     <span data-ttu-id="3eef1-219">**축소 후 데이터 공간 유지 비율** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-219">**Amount of free space to remain after shrink** box</span></span>  
     <span data-ttu-id="3eef1-220">데이터베이스 파일의 사용 가능한 공간이 이 크기(백분율)에 도달하면 축소를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-220">Stop shrinking when free space in database files reaches this size (as a percentage).</span></span>  
  
     <span data-ttu-id="3eef1-221">**데이터베이스 파일에 확보된 공간 유지**</span><span class="sxs-lookup"><span data-stu-id="3eef1-221">**Retain freed space in database files**</span></span>  
     <span data-ttu-id="3eef1-222">데이터베이스가 인접 페이지로 압축되지만 해당 페이지의 할당이 취소되지 않으므로 데이터베이스 파일이 축소되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-222">The database is condensed to contiguous pages but the pages are not deallocated, and the database files do not shrink.</span></span> <span data-ttu-id="3eef1-223">공간을 다시 할당하지 않고 데이터베이스를 다시 확장하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-223">Use this option if you expect the database to expand again, and you do not want to reallocate space.</span></span> <span data-ttu-id="3eef1-224">이 옵션을 사용하면 데이터베이스 파일이 가능한 한 축소되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-224">With this option, the database files do not shrink as much as possible.</span></span> <span data-ttu-id="3eef1-225">이 작업에서는 NOTRUNCATE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-225">This uses the NOTRUNCATE option.</span></span>  
  
     <span data-ttu-id="3eef1-226">**해제된 공간을 운영 체제로 반환**</span><span class="sxs-lookup"><span data-stu-id="3eef1-226">**Return freed space to operating system**</span></span>  
     <span data-ttu-id="3eef1-227">데이터베이스가 인접 페이지로 압축되며 다른 프로그램에서 사용할 수 있도록 해당 페이지가 운영 체제로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-227">The database is condensed to contiguous pages and the pages are released back to the operating system for use by other programs.</span></span> <span data-ttu-id="3eef1-228">이 데이터베이스 파일은 가능한 한 큰 폭으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-228">This database files shrink as much as possible.</span></span> <span data-ttu-id="3eef1-229">이 작업에서는 TRUNCATEONLY 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-229">This uses the TRUNCATEONLY option.</span></span> <span data-ttu-id="3eef1-230">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-230">This is the default option.</span></span>  
  
#### <a name="define-the-index-tasks"></a><span data-ttu-id="3eef1-231">인덱스 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-231">Define the Index Tasks</span></span>  
  
1.  <span data-ttu-id="3eef1-232">**인덱스 다시 구성 태스크 정의** 페이지에서 인덱스 페이지를 보다 효율적인 검색 순서로 이동할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-232">On the **Define Reorganize Index Task** page, select the server or servers where you'll be moving index pages into a more efficient search order.</span></span> <span data-ttu-id="3eef1-233">이 태스크에서는 `ALTER INDEX ... REORGANIZE` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-233">This task uses the `ALTER INDEX ... REORGANIZE` statement.</span></span> <span data-ttu-id="3eef1-234">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-234">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span> <span data-ttu-id="3eef1-235">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-235">When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-236">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-236">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-237">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-237">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-238">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-238">Specify the databases affected by this task.</span></span> <span data-ttu-id="3eef1-239">이 목록에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 9단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-239">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="3eef1-240">**개체** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-240">**Object** list</span></span>  
     <span data-ttu-id="3eef1-241">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 목록을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-241">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="3eef1-242">이 목록은 위의 **데이터베이스** 목록에서 단일 데이터베이스를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-242">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="3eef1-243">**선택** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-243">**Selection** list</span></span>  
     <span data-ttu-id="3eef1-244">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-244">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="3eef1-245">개체 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-245">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="3eef1-246">**큰 개체 압축** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-246">**Compact large objects** check box</span></span>  
     <span data-ttu-id="3eef1-247">가능한 경우에 테이블 및 뷰에 대한 공간 할당을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-247">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="3eef1-248">이 옵션에서는 `ALTER INDEX ... LOB_COMPACTION = ON`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-248">This option uses `ALTER INDEX ... LOB_COMPACTION = ON`.</span></span>  
  
2.  <span data-ttu-id="3eef1-249">**인덱스 다시 작성 태스크 정의** 페이지에서 여러 인덱스를 다시 만들 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-249">On the **Define Rebuild Index Task** page, select the database or databases where you'll be re-creating multiple indexes.</span></span> <span data-ttu-id="3eef1-250">이 태스크에서는 `ALTER INDEX ... REBUILD PARTITION` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-250">This task uses the `ALTER INDEX ... REBUILD PARTITION` statement.</span></span> <span data-ttu-id="3eef1-251">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요. 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-251">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).) When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-252">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-252">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-253">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-253">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-254">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-254">Specify the databases affected by this task.</span></span> <span data-ttu-id="3eef1-255">이 목록에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 9단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-255">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="3eef1-256">**개체** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-256">**Object** list</span></span>  
     <span data-ttu-id="3eef1-257">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 목록을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-257">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="3eef1-258">이 목록은 위의 **데이터베이스** 목록에서 단일 데이터베이스를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-258">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="3eef1-259">**선택** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-259">**Selection** list</span></span>  
     <span data-ttu-id="3eef1-260">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-260">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="3eef1-261">개체 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-261">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="3eef1-262">**사용 가능한 공간 옵션** 영역</span><span class="sxs-lookup"><span data-stu-id="3eef1-262">**Free space options** area</span></span>  
     <span data-ttu-id="3eef1-263">인덱스와 테이블에 채우기 비율을 적용하기 위한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-263">Presents options for applying fill factor to indexes and tables.</span></span>  
  
     <span data-ttu-id="3eef1-264">**페이지당 기본 여유 공간**</span><span class="sxs-lookup"><span data-stu-id="3eef1-264">**Default free space per page**</span></span>  
     <span data-ttu-id="3eef1-265">기본 여유 공간 크기로 페이지를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-265">Reorganizes the pages with the default amount of free space.</span></span> <span data-ttu-id="3eef1-266">이렇게 하면 데이터베이스 테이블의 인덱스를 삭제하고 인덱스를 만들 때 지정한 채우기 비율로 인덱스를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-266">This will drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span> <span data-ttu-id="3eef1-267">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-267">This is the default option.</span></span>  
  
     <span data-ttu-id="3eef1-268">**페이지당 빈 공간 비율을 다음으로 변경** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-268">**Change free space per page to** box</span></span>  
     <span data-ttu-id="3eef1-269">데이터베이스 테이블의 인덱스를 삭제하고 자동으로 계산된 새 채우기 비율로 인덱스를 다시 만들기 때문에 인덱스 페이지에 대해 지정된 크기의 사용 가능한 공간이 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-269">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="3eef1-270">이 비율이 커질수록 인덱스 페이지에 대해 더 많은 사용 가능한 공간이 예약되고 인덱스가 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-270">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="3eef1-271">유효한 값은 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-271">Valid values are from 0 through 100.</span></span> <span data-ttu-id="3eef1-272">`FILLFACTOR` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-272">Uses the `FILLFACTOR` option.</span></span>  
  
     <span data-ttu-id="3eef1-273">**고급 옵션** 영역</span><span class="sxs-lookup"><span data-stu-id="3eef1-273">**Advanced options** area</span></span>  
     <span data-ttu-id="3eef1-274">인덱스를 정렬하고 인덱스를 다시 만들기 위한 추가 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-274">Presents additional options for sorting indexes and reindexing.</span></span>  
  
     <span data-ttu-id="3eef1-275">**tempdb에 결과 정렬** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-275">**Sort results in tempdb** check box</span></span>  
     <span data-ttu-id="3eef1-276">인덱스를 만드는 동안 생성된 중간 정렬 결과가 임시로 저장되는 위치를 결정하려면 `SORT_IN_TEMPDB` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-276">Uses the `SORT_IN_TEMPDB` option which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="3eef1-277">정렬 작업이 필요하지 않거나 메모리에서 정렬을 수행할 수 있으면 `SORT_IN_TEMPDB` 옵션이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-277">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB` option is ignored.</span></span>  
  
     <span data-ttu-id="3eef1-278">**인덱스를 다시 만드는 동안 인덱스를 온라인으로 유지** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-278">**Keep index online while reindexing** check box</span></span>  
     <span data-ttu-id="3eef1-279">사용자가 인덱스 작업을 수행하는 동안 기본 테이블이나 클러스터형 인덱스 데이터 및 연관된 모든 비클러스터형 인덱스에 액세스할 수 있는 `ONLINE` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-279">Uses the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span> <span data-ttu-id="3eef1-280">이 옵션을 선택하면 온라인 다시 작성에 허용되지 않는 인덱스를 다시 작성하기 위한 추가 옵션인 **인덱스 다시 작성 안 함** 및 **오프라인 인덱스 다시 작성**이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-280">Selecting this option activates additional options for rebuilding indexes that do not allow for online rebuilds: **Do not rebuild indexes** and **Rebuild indexes offline**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eef1-281">온라인 인덱스 작업은 일부 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-281">Online index operations are not available in every edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3eef1-282">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-282">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
#### <a name="define-the-update-statistics-task"></a><span data-ttu-id="3eef1-283">통계 업데이트 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-283">Define the Update Statistics Task</span></span>  
  
1.  <span data-ttu-id="3eef1-284">**통계 업데이트 태스크 정의** 페이지에서 테이블 및 인덱스 통계가 업데이트될 데이터베이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-284">On the **Define Update Statistics Task** page, define the database or databases on which table and index statistics will be updated.</span></span> <span data-ttu-id="3eef1-285">이 태스크에서는 `UPDATE STATISTICS` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-285">This task uses the `UPDATE STATISTICS` statement.</span></span> <span data-ttu-id="3eef1-286">자세한 내용은 [UPDATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)를 참조하세요. 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-286">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) When finished, click **Next**</span></span>  
  
     <span data-ttu-id="3eef1-287">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-287">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-288">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-288">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-289">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-289">Specify the databases affected by this task.</span></span> <span data-ttu-id="3eef1-290">이 목록에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 9단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-290">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="3eef1-291">**개체** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-291">**Object** list</span></span>  
     <span data-ttu-id="3eef1-292">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 목록을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-292">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="3eef1-293">이 목록은 위의 **데이터베이스** 목록에서 단일 데이터베이스를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-293">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="3eef1-294">**선택** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-294">**Selection** list</span></span>  
     <span data-ttu-id="3eef1-295">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-295">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="3eef1-296">개체 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-296">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="3eef1-297">**모든 기존 통계**</span><span class="sxs-lookup"><span data-stu-id="3eef1-297">**All existing statistics**</span></span>  
     <span data-ttu-id="3eef1-298">열과 인덱스의 통계를 모두 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-298">Update statistics for both columns and indexes.</span></span>  
  
     <span data-ttu-id="3eef1-299">**열 통계만**</span><span class="sxs-lookup"><span data-stu-id="3eef1-299">**Column statistics only**</span></span>  
     <span data-ttu-id="3eef1-300">열 통계만 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-300">Only update column statistics.</span></span> <span data-ttu-id="3eef1-301">`WITH COLUMNS` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-301">Uses the `WITH COLUMNS` option.</span></span>  
  
     <span data-ttu-id="3eef1-302">**인덱스 통계만**</span><span class="sxs-lookup"><span data-stu-id="3eef1-302">**Index statistics only**</span></span>  
     <span data-ttu-id="3eef1-303">인덱스 통계만 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-303">Only update index statistics.</span></span> <span data-ttu-id="3eef1-304">`WITH INDEX` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-304">Uses the `WITH INDEX` option.</span></span>  
  
     <span data-ttu-id="3eef1-305">**검색 유형**</span><span class="sxs-lookup"><span data-stu-id="3eef1-305">**Scan type**</span></span>  
     <span data-ttu-id="3eef1-306">업데이트된 통계를 수집하는 데 사용되는 검색 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-306">Type of scan used to gather updated statistics.</span></span>  
  
     <span data-ttu-id="3eef1-307">**전체 검색**</span><span class="sxs-lookup"><span data-stu-id="3eef1-307">**Full scan**</span></span>  
     <span data-ttu-id="3eef1-308">통계를 수집하기 위해 테이블이나 뷰의 모든 행을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-308">Read all rows in the table or view to gather the statistics.</span></span>  
  
     <span data-ttu-id="3eef1-309">**샘플링 기준**</span><span class="sxs-lookup"><span data-stu-id="3eef1-309">**Sample by**</span></span>  
     <span data-ttu-id="3eef1-310">보다 큰 테이블이나 뷰에 대한 통계를 수집할 때 샘플링할 행의 수 또는 테이블이나 인덱싱된 뷰의 백분율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-310">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
#### <a name="define-the-history-cleanup-task"></a><span data-ttu-id="3eef1-311">기록 정리 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-311">Define the History Cleanup Task</span></span>  
  
1.  <span data-ttu-id="3eef1-312">**기록 정리 태스크 정의** 페이지에서 오래된 태스크 기록을 삭제할 데이터베이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-312">On the **Define History Cleanup Task** page, define the database or databases where you want to discard old task history.</span></span> <span data-ttu-id="3eef1-313">이 태스크는 `EXEC sp_purge_jobhistory`, `EXEC sp_maintplan_delete_log`및 `EXEC sp_delete_backuphistory` 문을 사용하여 **msdb** 테이블에서 기록 정보를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-313">This task uses the `EXEC sp_purge_jobhistory`, `EXEC sp_maintplan_delete_log`, and `EXEC sp_delete_backuphistory` statements to remove history information from the **msdb** tables.</span></span> <span data-ttu-id="3eef1-314">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-314">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-315">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-315">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-316">**삭제할 기록 데이터를 선택하세요.**</span><span class="sxs-lookup"><span data-stu-id="3eef1-316">**Select the historical data to delete**</span></span>  
     <span data-ttu-id="3eef1-317">삭제할 태스크 데이터의 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-317">Chose the type of task data to delete/</span></span>  
  
     <span data-ttu-id="3eef1-318">**백업 및 복원 기록**</span><span class="sxs-lookup"><span data-stu-id="3eef1-318">**Backup and restore history**</span></span>  
     <span data-ttu-id="3eef1-319">최근 백업을 만들었을 당시의 기록을 보존하면 데이터베이스를 복원하려고 할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 복구 계획을 만드는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-319">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="3eef1-320">보존 기간은 적어도 전체 데이터베이스 백업 빈도만큼 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-320">The retention period should be at least the frequency of full database backups.</span></span>  
  
     <span data-ttu-id="3eef1-321">**SQL Server 에이전트 작업 기록**</span><span class="sxs-lookup"><span data-stu-id="3eef1-321">**SQL Server Agent Job history**</span></span>  
     <span data-ttu-id="3eef1-322">이 기록을 사용하면 실패한 작업의 문제를 해결하거나 데이터베이스 동작의 발생 이유를 확인하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-322">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="3eef1-323">**유지 관리 계획 기록**</span><span class="sxs-lookup"><span data-stu-id="3eef1-323">**Maintenance Plan history**</span></span>  
     <span data-ttu-id="3eef1-324">이 기록을 사용하면 실패한 유지 관리 계획 동작의 문제를 해결하거나 데이터베이스 작업의 발생 이유를 확인하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-324">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="3eef1-325">**다음보다 오래된 기록 데이터 제거**</span><span class="sxs-lookup"><span data-stu-id="3eef1-325">**Remove historical data older than**</span></span>  
     <span data-ttu-id="3eef1-326">삭제할 항목의 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-326">Specify age of items that you want to delete.</span></span> <span data-ttu-id="3eef1-327">**시**, **일**, **주** (기본값), **월**또는 **년**을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-327">You can specify **Hour(s)**, **Day(s)**, **Week(s)** (the default), **Month(s)**, or **Year(s)**</span></span>  
  
#### <a name="define-the-execute-agent-job-task"></a><span data-ttu-id="3eef1-328">에이전트 작업 실행 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-328">Define the Execute Agent Job Task</span></span>  
  
1.  <span data-ttu-id="3eef1-329">**에이전트 작업 실행 태스크 정의** 페이지의 **사용 가능한 SQL Server 에이전트 작업**에서 실행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-329">On the **Define Execute Agent Job Task** page, under **Available SQL Server Agent jobs**, choose the job or jobs to run.</span></span> <span data-ttu-id="3eef1-330">SQL 에이전트 작업이 없으면 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-330">This option will not be available if you have no SQL Agent jobs.</span></span> <span data-ttu-id="3eef1-331">이 태스크에서는 `EXEC sp_start_job` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-331">This task uses the `EXEC sp_start_job` statement.</span></span> <span data-ttu-id="3eef1-332">자세한 내용은 [sp_start_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)을 참조하세요. 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-332">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)When finished, click **Next**.</span></span>  
  
#### <a name="define-backup-tasks"></a><span data-ttu-id="3eef1-333">백업 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-333">Define Backup Tasks</span></span>  
  
1.  <span data-ttu-id="3eef1-334">**데이터베이스 백업(전체) 태스크 정의** 페이지에서 전체 백업을 실행할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-334">On the **Define Backup Database (Full) Task** page, select the database or databases on which to run a full backup.</span></span> <span data-ttu-id="3eef1-335">이 태스크에서는 `BACKUP DATABASE` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-335">This task uses the `BACKUP DATABASE` statement.</span></span> <span data-ttu-id="3eef1-336">자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-336">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="3eef1-337">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-337">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-338">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-338">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-339">**백업 유형** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-339">**Backup type** list</span></span>  
     <span data-ttu-id="3eef1-340">수행할 백업 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-340">Displays the type of backup to be performed.</span></span> <span data-ttu-id="3eef1-341">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-341">This is read-only.</span></span>  
  
     <span data-ttu-id="3eef1-342">**데이터베이스** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-342">**Databases** list</span></span>  
     <span data-ttu-id="3eef1-343">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-343">Specify the databases affected by this task.</span></span> <span data-ttu-id="3eef1-344">이 목록에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 9단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-344">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="3eef1-345">**백업 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="3eef1-345">**Backup component**</span></span>  
     <span data-ttu-id="3eef1-346">전체 데이터베이스를 백업하려면 **데이터베이스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-346">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="3eef1-347">데이터베이스 일부만 백업하려면 **파일 및 파일 그룹** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-347">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="3eef1-348">이 옵션을 선택한 경우 파일 또는 파일 그룹 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-348">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="3eef1-349">**데이터베이스** 상자에서 여러 데이터베이스를 선택한 경우에는 **백업 구성 요소** 에 대해 **데이터베이스**만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-349">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="3eef1-350">파일 또는 파일 그룹 백업을 수행하려면 각 데이터베이스에 대해 태스크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-350">To perform file or filegroup backups, create a task for each database.</span></span> <span data-ttu-id="3eef1-351">이러한 옵션은 위의 **데이터베이스** 목록에서 단일 데이터베이스를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-351">These options are only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="3eef1-352">**백업 세트 만료 기한** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-352">**Backup set will expire** check box</span></span>  
     <span data-ttu-id="3eef1-353">이 백업에 대한 백업 세트를 덮어쓸 수 있는 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-353">Specifies when the backup set for this backup can be overwritten.</span></span> <span data-ttu-id="3eef1-354">**다음 이후** 를 선택하고 만료까지의 일 수를 입력하거나 **날짜** 를 선택하고 만료 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-354">Select **After** and enter a number of days to expiration, or select **On** and enter a date of expiration.</span></span> <span data-ttu-id="3eef1-355">**URL** 이 백업 대상으로 선택된 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-355">This option is disabled if **URL** is selected as the backup destination.</span></span>  
  
     <span data-ttu-id="3eef1-356">**백업할 위치**</span><span class="sxs-lookup"><span data-stu-id="3eef1-356">**Back up to**</span></span>  
     <span data-ttu-id="3eef1-357">데이터베이스를 백업할 미디어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-357">Specifies the medium on which to back up the database.</span></span> <span data-ttu-id="3eef1-358">**디스크**, **테이프**또는 **URL**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-358">Select **Disk**, **Tape**, or **URL**.</span></span> <span data-ttu-id="3eef1-359">데이터베이스를 포함하는 컴퓨터에 연결된 테이프 디바이스만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-359">Only tape devices attached to the computer containing the database are available.</span></span>  
  
     <span data-ttu-id="3eef1-360">**하나 이상의 파일에 데이터베이스 백업**</span><span class="sxs-lookup"><span data-stu-id="3eef1-360">**Back up database(s) across one or more files**</span></span>  
     <span data-ttu-id="3eef1-361">**추가** 를 클릭하여 **백업 대상 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-361">Click **Add** to open the **Select Backup Destination** dialog box.</span></span> <span data-ttu-id="3eef1-362">URL을 백업 대상으로 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-362">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="3eef1-363">대화 상자에서 파일을 제거하려면 **제거** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-363">Click **Remove** to remove a file from the box.</span></span>  
  
     <span data-ttu-id="3eef1-364">파일 헤더를 읽고 파일의 현재 백업 내용을 표시하려면 **내용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-364">Click **Contents** to read the file header and display the current backup contents of the file.</span></span>  
  
     <span data-ttu-id="3eef1-365">**백업 대상 선택** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-365">**Select Backup Destination** dialog box</span></span>  
     <span data-ttu-id="3eef1-366">백업 대상으로 파일, 테이프 드라이브 또는 백업 디바이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-366">Select the file, tape drive, or backup device for the backup destination.</span></span> <span data-ttu-id="3eef1-367">URL을 백업 대상으로 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-367">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="3eef1-368">**백업 파일이 있는 경우** 목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-368">**If backup files exist** list</span></span>  
     <span data-ttu-id="3eef1-369">기존 백업 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-369">Specify how to handle existing backups.</span></span> <span data-ttu-id="3eef1-370">파일이나 테이프의 기존 백업 뒤에 새 백업을 추가하려면 **추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-370">Select **Append** to add the new backups after any existing backups in the file or on the tape.</span></span> <span data-ttu-id="3eef1-371">파일이나 테이프의 이전 내용을 제거하고 새 백업으로 바꾸려면 **덮어쓰기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-371">Select **Overwrite** to remove the old content of a file or tape, and replace it with this new backup.</span></span>  
  
     <span data-ttu-id="3eef1-372">**모든 데이터베이스에 대한 백업 파일 만들기**</span><span class="sxs-lookup"><span data-stu-id="3eef1-372">**Create a backup file for every database**</span></span>  
     <span data-ttu-id="3eef1-373">폴더 상자에서 지정한 위치에 백업 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-373">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="3eef1-374">선택한 데이터베이스당 하나의 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-374">One file is created for each database selected.</span></span> <span data-ttu-id="3eef1-375">URL을 백업 대상으로 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-375">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="3eef1-376">**각 데이터베이스에 대한 하위 디렉터리 만들기** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-376">**Create a sub-directory for each database** check box</span></span>  
     <span data-ttu-id="3eef1-377">지정한 디스크 디렉터리 아래에 유지 관리 계획의 일부로 백업 중인 각 데이터베이스에 대한 데이터베이스 백업이 있는 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-377">Create a sub-directory under the specified disk directory that contains the database backup for each database being backed up as part of the maintenance plan.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3eef1-378">하위 디렉터리는 부모 디렉터리에서 사용 권한을 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-378">The sub-directory will inherit permissions from the parent directory.</span></span> <span data-ttu-id="3eef1-379">무단으로 액세스하지 못하도록 하려면 사용 권한을 제한하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-379">Restrict permissions to avoid unauthorized access.</span></span>  
  
     <span data-ttu-id="3eef1-380">**폴더** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-380">**Folder** box</span></span>  
     <span data-ttu-id="3eef1-381">자동으로 생성된 데이터베이스 파일을 포함할 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-381">Specify the folder to contain the automatically created database files.</span></span> <span data-ttu-id="3eef1-382">URL을 백업 대상으로 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-382">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="3eef1-383">**SQL 자격 증명**</span><span class="sxs-lookup"><span data-stu-id="3eef1-383">**SQL Credential**</span></span>  
     <span data-ttu-id="3eef1-384">Azure Storage에 인증하는 데 사용되는 SQL 자격 증명을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-384">Select a SQL Credential used to authenticate to Azure Storage.</span></span> <span data-ttu-id="3eef1-385">사용할 수 있는 기존 SQL 자격 증명이 없는 경우 **만들기** 단추를 클릭하여 새 SQL 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-385">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3eef1-386">**만들기** 를 클릭하면 열리는 대화 상자에서는 관리 인증서나 구독용 게시 프로필이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-386">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="3eef1-387">관리 인증서나 게시 프로필에 액세스할 수 없는 경우 Transact-SQL이나 SQL Server Management Studio를 사용하여 스토리지 계정 이름을 지정하고 키 정보에 액세스하여 SQL 자격 증명을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-387">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="3eef1-388">Transact-sql을 사용 하 여 자격 증명을 만들려면 [이 항목의 샘플 코드를 참조](../security/authentication-access/create-a-credential.md#Credential) 하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-388">See the sample code in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="3eef1-389">또는 SQL Server Management Studio를 사용하여 데이터베이스 엔진 인스턴스에서 **보안**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **자격 증명**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-389">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="3eef1-390">**ID** 에 대한 스토리지 계정 이름을 지정하고 **암호** 필드에 액세스 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-390">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
     <span data-ttu-id="3eef1-391">**Azure Storage 컨테이너**</span><span class="sxs-lookup"><span data-stu-id="3eef1-391">**Azure storage container**</span></span>  
     <span data-ttu-id="3eef1-392">Azure Storage 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-392">Specify the name of the Azure storage container</span></span>  
  
     <span data-ttu-id="3eef1-393">**URL 접두사:**</span><span class="sxs-lookup"><span data-stu-id="3eef1-393">**URL prefix:**</span></span>  
     <span data-ttu-id="3eef1-394">이는 지정된 Azure 스토리지 컨테이너 이름 및 SQL 자격 증명에 저장된 스토리지 계정 정보를 기반으로 자동 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-394">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="3eef1-395">**\<storage account>.blob.core.windows.net** 이외의 형식을 사용하는 도메인을 사용하지 않는 경우 이 필드의 정보를 편집하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-395">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
     <span data-ttu-id="3eef1-396">**백업 파일 확장명** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-396">**Backup file extension** box</span></span>  
     <span data-ttu-id="3eef1-397">백업 파일에 사용할 확장명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-397">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="3eef1-398">기본값은 .bak입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-398">The default is .bak.</span></span>  
  
     <span data-ttu-id="3eef1-399">**백업 무결성 확인** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-399">**Verify backup integrity** check box</span></span>  
     <span data-ttu-id="3eef1-400">백업 세트가 올바른지 확인하고 모든 볼륨을 읽을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-400">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
     <span data-ttu-id="3eef1-401">**백업 암호화**</span><span class="sxs-lookup"><span data-stu-id="3eef1-401">**Backup Encryption**</span></span>  
     <span data-ttu-id="3eef1-402">암호화된 백업을 만들려면 **백업 암호화** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-402">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="3eef1-403">암호화 단계에 사용할 암호화 알고리즘을 선택하고 기존 인증서 또는 비대칭 키 목록의 인증서 또는 비대칭 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-403">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="3eef1-404">사용 가능한 암호화 알고리즘은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-404">The available algorithms for encryption are:</span></span>  
  
    -   <span data-ttu-id="3eef1-405">AES 128</span><span class="sxs-lookup"><span data-stu-id="3eef1-405">AES 128</span></span>  
  
    -   <span data-ttu-id="3eef1-406">AES 192</span><span class="sxs-lookup"><span data-stu-id="3eef1-406">AES 192</span></span>  
  
    -   <span data-ttu-id="3eef1-407">AES 256</span><span class="sxs-lookup"><span data-stu-id="3eef1-407">AES 256</span></span>  
  
    -   <span data-ttu-id="3eef1-408">Triple DES</span><span class="sxs-lookup"><span data-stu-id="3eef1-408">Triple DES</span></span>  
  
     <span data-ttu-id="3eef1-409">기존 백업 세트에 추가하도록 선택한 경우 암호화 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-409">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
  
     <span data-ttu-id="3eef1-410">인증서나 키를 백업하고 암호화한 백업과 다른 위치에 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-410">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
  
     <span data-ttu-id="3eef1-411">EKM(Extensible Key Management)에 있는 키만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-411">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
     <span data-ttu-id="3eef1-412">**백업 압축 설정**  목록</span><span class="sxs-lookup"><span data-stu-id="3eef1-412">**Set backup compression**  list</span></span>  
     <span data-ttu-id="3eef1-413">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (이상 버전)에서 다음 [백업 압축](../backup-restore/backup-compression-sql-server.md) 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-413">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="3eef1-414">**기본 서버 설정 사용**</span><span class="sxs-lookup"><span data-stu-id="3eef1-414">**Use the default server setting**</span></span>|<span data-ttu-id="3eef1-415">서버 수준 기본값을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-415">Click to use the server-level default.</span></span> <span data-ttu-id="3eef1-416">이 기본값은 **백업 압축 기본값** 서버 구성 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-416">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="3eef1-417">이 옵션의 현재 설정을 확인하는 방법에 대한 자세한 내용은 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-417">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
    |<span data-ttu-id="3eef1-418">**백업 압축**</span><span class="sxs-lookup"><span data-stu-id="3eef1-418">**Compress backup**</span></span>|<span data-ttu-id="3eef1-419">서버 수준 기본값에 관계없이 백업을 압축하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-419">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="3eef1-420">**\*\* 중요 \*\*** 압축 시에는 기본적으로 CPU 사용량이 크게 증가하며, 압축 프로세스에서 CPU를 추가로 사용하므로 동시 작업 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-420">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="3eef1-421">따라서 CPU 사용량이 리소스 관리자에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-421">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the Resource Governor.</span></span> <span data-ttu-id="3eef1-422">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-422">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
    |<span data-ttu-id="3eef1-423">**백업 압축 안 함**</span><span class="sxs-lookup"><span data-stu-id="3eef1-423">**Do not compress backup**</span></span>|<span data-ttu-id="3eef1-424">서버 수준 기본값에 관계없이 압축되지 않은 백업을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-424">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
2.  <span data-ttu-id="3eef1-425">**데이터베이스 백업(차등) 태스크 정의** 페이지에서 부분 백업을 실행할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-425">On the **Define Backup Database (Differential) Task** page, select the database or databases on which to run a partial backup.</span></span> <span data-ttu-id="3eef1-426">이 페이지에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 16단계에 있는 정의 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-426">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="3eef1-427">이 태스크에서는 `BACKUP DATABASE ... WITH DIFFERENTIAL` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-427">This task uses the `BACKUP DATABASE ... WITH DIFFERENTIAL` statement.</span></span> <span data-ttu-id="3eef1-428">자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-428">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  <span data-ttu-id="3eef1-429">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-429">When finished, click **Next**.</span></span>  
  
3.  <span data-ttu-id="3eef1-430">**데이터베이스 백업(트랜잭션 로그) 태스크 정의** 페이지에서 트랜잭션 로그에 대한 백업을 실행할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-430">On the **Define Backup Database (Transaction Log) Task** page, select the database or databases on which to run a backup for a transaction log.</span></span> <span data-ttu-id="3eef1-431">이 페이지에서 사용할 수 있는 옵션에 대한 자세한 내용은 위의 16단계에 있는 정의 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-431">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="3eef1-432">이 태스크에서는 `BACKUP LOG` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-432">This task uses the `BACKUP LOG` statement.</span></span> <span data-ttu-id="3eef1-433">자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eef1-433">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="3eef1-434">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-434">When finished, click **Next**.</span></span>  
  
#### <a name="define-maintenance-cleanup-tasks"></a><span data-ttu-id="3eef1-435">유지 관리 정리 태스크 정의</span><span class="sxs-lookup"><span data-stu-id="3eef1-435">Define Maintenance Cleanup Tasks</span></span>  
  
1.  <span data-ttu-id="3eef1-436">**유지 관리 정리 태스크 정의** 페이지에서 유지 관리 계획에서 만든 텍스트 보고서와 데이터베이스 백업 파일을 포함하여 유지 관리 계획의 일부로 삭제할 파일의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-436">On the **Define Maintenance Cleanup Task** page, specify the types of files to delete as part of the maintenance plan, including text reports created by maintenance plans and database backup files.</span></span> <span data-ttu-id="3eef1-437">이 태스크에서는 `EXEC xp_delete_file` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-437">This task uses the `EXEC xp_delete_file` statement.</span></span> <span data-ttu-id="3eef1-438">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-438">When finished, click **Next**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3eef1-439">이 태스크에서는 지정된 디렉터리의 하위 폴더에 있는 파일을 자동으로 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-439">This task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="3eef1-440">이 예방 조치로 인해 유지 관리 정리 태스크를 사용하여 파일을 삭제하는 악의적 공격의 가능성이 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-440">This precaution reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="3eef1-441">첫 번째 수준의 하위 폴더를 삭제하려는 경우 **첫 번째 수준의 하위 폴더 포함**을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-441">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
     <span data-ttu-id="3eef1-442">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-442">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-443">**다음 유형의 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="3eef1-443">**Delete files of the following type**</span></span>  
     <span data-ttu-id="3eef1-444">삭제할 파일의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-444">Specify the type of files to be deleted.</span></span>  
  
     <span data-ttu-id="3eef1-445">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="3eef1-445">**Backup files**</span></span>  
     <span data-ttu-id="3eef1-446">데이터베이스 백업 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-446">Delete database backup files.</span></span>  
  
     <span data-ttu-id="3eef1-447">**유지 관리 계획 텍스트 보고서**</span><span class="sxs-lookup"><span data-stu-id="3eef1-447">**Maintenance Plan text reports**</span></span>  
     <span data-ttu-id="3eef1-448">이전에 실행한 유지 관리 계획의 텍스트 보고서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-448">Delete text reports of previously run maintenance plans.</span></span>  
  
     <span data-ttu-id="3eef1-449">**파일 위치**</span><span class="sxs-lookup"><span data-stu-id="3eef1-449">**File location**</span></span>  
     <span data-ttu-id="3eef1-450">삭제할 파일을 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-450">Specify path to files to be deleted.</span></span>  
  
     <span data-ttu-id="3eef1-451">**특정 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="3eef1-451">**Delete specific file**</span></span>  
     <span data-ttu-id="3eef1-452">**파일 이름** 입력란에 표시되는 특정 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-452">Delete the specific file provided in the **File name** text box.</span></span>  
  
     <span data-ttu-id="3eef1-453">**확장명에 따라 폴더 검색 및 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="3eef1-453">**Search folder and delete files based on an extension**</span></span>  
     <span data-ttu-id="3eef1-454">지정한 확장명을 가진 파일을 지정한 폴더에서 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-454">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="3eef1-455">이 옵션을 사용하여 여러 파일(예: Tuesday 폴더에서 확장명이 .bak인 모든 백업 파일)을 한 번에 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-455">Use this to delete multiple files at once, such as all backup files in the Tuesday folder with the .bak extension.</span></span>  
  
     <span data-ttu-id="3eef1-456">**폴더** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-456">**Folder** box</span></span>  
     <span data-ttu-id="3eef1-457">삭제할 파일이 있는 폴더의 경로와 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-457">Path and name of the folder containing the files to be deleted.</span></span>  
  
     <span data-ttu-id="3eef1-458">**파일 확장명** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-458">**File extension** box</span></span>  
     <span data-ttu-id="3eef1-459">삭제할 파일의 파일 확장명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-459">Provide the file extension of the files to be deleted.</span></span> <span data-ttu-id="3eef1-460">Tuesday 폴더에서 확장명이 .bak인 모든 백업 파일과 같은 여러 파일을 삭제하려면 .bak를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-460">To delete multiple files at one time, like all backup files with the .bak extension in the Tuesday folder, specify .bak.</span></span>  
  
     <span data-ttu-id="3eef1-461">**첫 번째 수준의 하위 폴더 포함** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-461">**Include first-level subfolders** check box</span></span>  
     <span data-ttu-id="3eef1-462">**폴더** 에 지정된 폴더 아래의 첫 번째 하위 폴더에서 **파일 확장명**에 지정된 확장명을 갖는 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-462">Delete files with the extension specified for **File extension** from first-level subfolders under the folder specified in **Folder**.</span></span>  
  
     <span data-ttu-id="3eef1-463">**태스크 런타임에 파일의 보존 기간에 따라 파일 삭제** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-463">**Delete files based on the age of the file at task run time** check box</span></span>  
     <span data-ttu-id="3eef1-464">**다음보다 오래된 파일 삭제** 상자에 숫자와 시간 단위를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-464">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
     <span data-ttu-id="3eef1-465">**다음보다 오래된 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="3eef1-465">**Delete files older than the following**</span></span>  
     <span data-ttu-id="3eef1-466">숫자와 시간 단위(**시**, **일**, **주**, **월**또는 **년**)를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-466">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (**Hour**, **Day**, **Week**, **Month**, or **Year**).</span></span> <span data-ttu-id="3eef1-467">지정한 시간대 이전의 파일은 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-467">Files older than the time frame specified will be deleted.</span></span>  
  
#### <a name="select-report-options"></a><span data-ttu-id="3eef1-468">보고서 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="3eef1-468">Select Report Options</span></span>  
  
1.  <span data-ttu-id="3eef1-469">**보고서 옵션 선택** 페이지에서 유지 관리 계획 동작의 보고서를 저장하거나 배포하기 위한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-469">On the **Select Report Options** page, select options for saving or distributing a report of the maintenance plan actions.</span></span> <span data-ttu-id="3eef1-470">이 태스크에서는 `EXEC sp_notify_operator` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-470">This task uses the `EXEC sp_notify_operator` statement.</span></span> <span data-ttu-id="3eef1-471">자세한 내용은 [sp_notify_operator&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)을 참조하세요. 완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-471">For more information, see [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql).When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="3eef1-472">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-472">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="3eef1-473">**텍스트 파일에 보고서 쓰기** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-473">**Write a report to a text file** check box</span></span>  
     <span data-ttu-id="3eef1-474">보고서를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-474">Save the report in a file.</span></span>  
  
     <span data-ttu-id="3eef1-475">**폴더 위치** 상자</span><span class="sxs-lookup"><span data-stu-id="3eef1-475">**Folder location** box</span></span>  
     <span data-ttu-id="3eef1-476">보고서를 포함할 파일 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-476">Specify the location of the file that will contain the report.</span></span>  
  
     <span data-ttu-id="3eef1-477">**전자 메일 보고서** 확인란</span><span class="sxs-lookup"><span data-stu-id="3eef1-477">**E-mail report** check box</span></span>  
     <span data-ttu-id="3eef1-478">태스크가 실패하면 전자 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-478">Send an e-mail when a task fails.</span></span> <span data-ttu-id="3eef1-479">이 태스크를 사용하려면 MSDB를 메일 호스트 데이터베이스로 사용하여 데이터베이스 메일을 사용하도록 설정하고 올바르게 구성해야 합니다. 또한 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 운영자에게 유효한 전자 메일 주소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-479">To use this task you must have Database Mail enabled and correctly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
     <span data-ttu-id="3eef1-480">**에이전트 운영자**</span><span class="sxs-lookup"><span data-stu-id="3eef1-480">**Agent operator**</span></span>  
     <span data-ttu-id="3eef1-481">전자 메일의 받는 사람을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-481">Specify the recipient of the e-mail.</span></span>  
  
     <span data-ttu-id="3eef1-482">**메일 프로필**</span><span class="sxs-lookup"><span data-stu-id="3eef1-482">**Mail profile**</span></span>  
     <span data-ttu-id="3eef1-483">전자 메일의 보내는 사람을 정의하는 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-483">Specify the profile that defines the sender of the e-mail.</span></span>  
  
#### <a name="complete-the-wizard"></a><span data-ttu-id="3eef1-484">마법사 완료</span><span class="sxs-lookup"><span data-stu-id="3eef1-484">Complete the Wizard</span></span>  
  
1.  <span data-ttu-id="3eef1-485">**마법사 완료** 페이지에서 이전 페이지에서 선택한 내용을 확인하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-485">On the **Complete the Wizard** page, verify the choices made on the previous pages, and click **Finish**.</span></span>  
  
2.  <span data-ttu-id="3eef1-486">**유지 관리 계획 마법사 진행률** 페이지에서 유지 관리 계획 마법사의 동작에 대한 상태 정보를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-486">On the **Maintenance Wizard Progress** page, monitor status information about the actions of the Maintenance Plan Wizard.</span></span> <span data-ttu-id="3eef1-487">마법사에서 선택한 옵션에 따라 진행률 페이지에 하나 이상의 동작이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-487">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="3eef1-488">맨 위에 있는 상자에는 전반적인 마법사 상태와 수신된 상태, 오류 및 경고 메시지의 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-488">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="3eef1-489">다음은 **유지 관리 계획 마법사 진행률** 페이지에서 선택할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-489">The following options are available on the **Maintenance Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="3eef1-490">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="3eef1-490">**Details**</span></span>  
     <span data-ttu-id="3eef1-491">동작, 상태 및 마법사가 수행한 동작의 결과로 반환된 모든 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-491">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="3eef1-492">**동작**</span><span class="sxs-lookup"><span data-stu-id="3eef1-492">**Action**</span></span>  
     <span data-ttu-id="3eef1-493">각 동작의 이름과 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-493">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="3eef1-494">**상태**</span><span class="sxs-lookup"><span data-stu-id="3eef1-494">**Status**</span></span>  
     <span data-ttu-id="3eef1-495">마법사 동작 결과 전체적으로 **성공** 값을 반환했는지 또는 **실패**값을 반환했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-495">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="3eef1-496">**메시지**</span><span class="sxs-lookup"><span data-stu-id="3eef1-496">**Message**</span></span>  
     <span data-ttu-id="3eef1-497">프로세스에서 반환된 모든 오류 또는 경고 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-497">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="3eef1-498">**Report**</span><span class="sxs-lookup"><span data-stu-id="3eef1-498">**Report**</span></span>  
     <span data-ttu-id="3eef1-499">파티션 작성 마법사의 결과가 포함된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-499">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="3eef1-500">**보고서 보기**, **보고서를 파일로 저장**, **클립보드에 보고서 복사**및 **보고서를 전자 메일로 보내기**중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-500">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="3eef1-501">**보고서 보기**</span><span class="sxs-lookup"><span data-stu-id="3eef1-501">**View Report**</span></span>  
     <span data-ttu-id="3eef1-502">파티션 작성 마법사의 진행률에 대한 텍스트 보고서가 포함된 **보고서 보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-502">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="3eef1-503">**보고서를 파일로 저장**</span><span class="sxs-lookup"><span data-stu-id="3eef1-503">**Save Report to File**</span></span>  
     <span data-ttu-id="3eef1-504">**보고서를 다른 이름으로 저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-504">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="3eef1-505">**클립보드에 보고서 복사**</span><span class="sxs-lookup"><span data-stu-id="3eef1-505">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="3eef1-506">마법사의 진행률 보고서 결과를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-506">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="3eef1-507">**보고서를 전자 메일로 보내기**</span><span class="sxs-lookup"><span data-stu-id="3eef1-507">**Send Report as Email**</span></span>  
     <span data-ttu-id="3eef1-508">마법사의 진행률 보고서 결과를 이메일 메시지에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3eef1-508">Copies the results of the wizard's progress report into an email message.</span></span>  
  
  
