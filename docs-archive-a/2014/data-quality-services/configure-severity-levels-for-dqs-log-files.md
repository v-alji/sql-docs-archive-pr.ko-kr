---
title: DQS 로그 파일에 대한 심각도 수준 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 46fb9de1fbe1e3e59b20bb2ac7afeebe19ba2da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728731"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a><span data-ttu-id="7d66d-102">DQS 로그 파일에 대한 심각도 수준 구성</span><span class="sxs-lookup"><span data-stu-id="7d66d-102">Configure Severity Levels for DQS Log Files</span></span>
  <span data-ttu-id="7d66d-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]를 사용하여 다양한 작업 및 모듈의 심각도를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-103">This topic describes how to configure severity levels for various activities and modules in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="7d66d-104">심각도는 DQS에서 발생하는 이벤트의 강도를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-104">Severity levels define the intensity of events that occur in DQS.</span></span> <span data-ttu-id="7d66d-105">DQS 이벤트의 심각도는 다음과 같습니다(심각도 내림차순 정렬).</span><span class="sxs-lookup"><span data-stu-id="7d66d-105">DQS events have the following severity levels, in the decreasing order of severity:</span></span>  
  
-   <span data-ttu-id="7d66d-106">**치명적**: 심각한/예기치 않은 결과를 일으킬 수 있는 치명적인 런타임 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-106">**Fatal**: Critical runtime errors that might cause severe/unexpected results.</span></span>  
  
-   <span data-ttu-id="7d66d-107">**오류**: 그 외 런타임 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-107">**Error**: Other runtime errors.</span></span>  
  
-   <span data-ttu-id="7d66d-108">**경고**: 오류를 일으킬 수 있는 이벤트에 대한 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-108">**Warn**: Warning about events that might result in an error.</span></span>  
  
-   <span data-ttu-id="7d66d-109">**정보**: 오류나 경고가 아닌 일반 이벤트에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-109">**Info**: Information about general events that is not an error or a warning.</span></span> <span data-ttu-id="7d66d-110">예를 들어 'DQS 프로세스가 시작되었습니다'가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-110">For example, a DQS process has started.</span></span>  
  
-   <span data-ttu-id="7d66d-111">**디버그**: 이벤트에 대한 자세한(세부) 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-111">**Debug**: Detailed (verbose) information about the event.</span></span>  
  
 <span data-ttu-id="7d66d-112">다양한 DQS 작업 및 모듈의 심각도를 구성하면 해당 DQS 작업 또는 모듈에 대한 DQS 로그 파일에 로깅하고 기록할 정보가 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-112">By configuring severity levels for various DQS activities and modules, you are filtering the information that you want to be logged, and written to the DQS log file for the respective DQS activity or module.</span></span> <span data-ttu-id="7d66d-113">예를 들어 DQS 작업의 심각도를 **경고**로 설정하면 해당 DQS 작업과 관련된 경고 이상의 심각도 메시지만 로깅됩니다(오류 및 치명적).</span><span class="sxs-lookup"><span data-stu-id="7d66d-113">For example, if you set the severity level of a DQS activity to **Warn**, only warning and higher severity messages (Error and Fatal) associated with the DQS activity will be logged.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7d66d-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7d66d-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7d66d-115">보안</span><span class="sxs-lookup"><span data-stu-id="7d66d-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7d66d-116">권한</span><span class="sxs-lookup"><span data-stu-id="7d66d-116">Permissions</span></span>  
 <span data-ttu-id="7d66d-117">로그 심각도 설정을 구성하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-117">You must have the dqs_administrator role on the DQS_MAIN database to configure log severity settings.</span></span>  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a><span data-ttu-id="7d66d-118">활동 수준에서 심각도 수준 구성</span><span class="sxs-lookup"><span data-stu-id="7d66d-118">Configure Severity Levels at Activity Level</span></span>  
 <span data-ttu-id="7d66d-119">DQS에서 도메인 관리, 기술 자료 검색, 일치 정책, 데이터 정리, 데이터 일치 및 참조 데이터 서비스와 같은 작업에 대한 로그 심각도 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-119">You can configure log severity settings for the following activities in DQS: domain management, knowledge discovery, matching policy, data cleansing, data matching, and reference data services.</span></span> <span data-ttu-id="7d66d-120">이렇게 하려면</span><span class="sxs-lookup"><span data-stu-id="7d66d-120">To do so:</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7d66d-121">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7d66d-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="7d66d-123">그런 다음 **로그 설정** 탭을 클릭 합니다. 심각도 수준을 선택할 수 있는 DQS 작업 **도메인 관리**, **기술 자료 검색**, **정리 프로젝트 (예: rds)**, **일치 정책 및 일치 프로젝트**및 **RDS**가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-123">Next, click the **Log Settings** tab. The following DQS activities are listed for which you can select a severity level: **Domain Management**, **Knowledge Discovery**, **Cleansing Project (Ex. RDS)**, **Matching Policy and Matching Project**, and **RDS**.</span></span>  
  
4.  <span data-ttu-id="7d66d-124">특정 DQS 작업에 대해 로깅할 심각도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-124">For a DQS activity, select the severity level that you want to be logged.</span></span> <span data-ttu-id="7d66d-125">심각도 **치명적**, **오류**, **경고**, **정보**및 **디버그**중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-125">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span> <span data-ttu-id="7d66d-126">예를 들어 기술 자료 검색 작업에서 치명적 메시지만 DQS 로그 파일에 기록하려면 **기술 자료 검색** 작업에 대한 드롭다운 목록에서 **치명적** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-126">For example, if you want only fatal messages to be written to the DQS log files for the knowledge discovery activity, select **Fatal** in the drop-down list against the **Knowledge Discovery** activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d66d-127">기본적으로 각 작업에 대해 **오류** 가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-127">By default, **Error** is selected for each of the activities.</span></span> <span data-ttu-id="7d66d-128">이는 각 작업에 대한 DQS 로그 파일에 기본적으로 오류 및 치명적 메시지가 기록됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-128">This implies that error and fatal messages will be written to the DQS log files for each activity, by default.</span></span>  
  
5.  <span data-ttu-id="7d66d-129">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-129">Click **Close**.</span></span>  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a><span data-ttu-id="7d66d-130">모듈 수준에서 심각도 구성 (고급)</span><span class="sxs-lookup"><span data-stu-id="7d66d-130">Configure Severity Levels at Module Level (Advanced)</span></span>  
 <span data-ttu-id="7d66d-131">**로그 설정** 탭의 **고급** 섹션을 사용하여 모듈 수준에서 로그 심각도 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-131">The **Advanced** section in the **Log Settings** tab enables you to configure log severity settings at a module level.</span></span> <span data-ttu-id="7d66d-132">모듈은 DQS의 기능 내에 다양한 기능을 구현하는 DQS 시스템 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-132">Modules are DQS system assemblies that implement various functionalities within a feature in DQS.</span></span> <span data-ttu-id="7d66d-133">예를 들어 도메인 관리 작업에는 도메인 규칙 정의, 규칙 조건 정의, 복합 도메인의 도메인 간 규칙 정의 등과 같은 다양한 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-133">For example, the domain management activity contains various functionalities such as defining domain rules, defining rule conditions, defining cross-domain rules for composite domains, and so on.</span></span>  
  
 <span data-ttu-id="7d66d-134">때때로 작업 수준의 세분성 수준으로 충분하지 않은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-134">At times, the granularity level at the activity level is not sufficient.</span></span> <span data-ttu-id="7d66d-135">한 작업 내 특정 모듈에서 발생한 문제를 조사해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-135">You might want to investigate an issue that is occurring in a particular module within an activity.</span></span> <span data-ttu-id="7d66d-136">그러면 모듈 수준에서 로그 심각도를 구성하여 문제를 더 정확하게 격리하고 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-136">It helps to have an option to configure log severities at the module level to isolate and track the issue more precisely.</span></span>  
  
 <span data-ttu-id="7d66d-137">작업 수준에서 지정된 로그 심각도 설정은 작업을 구성하는 모든 모듈의 로그 심각도 설정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-137">The log severity setting specified at the activity level determines the log severity setting of all the modules that constitute the activity.</span></span> <span data-ttu-id="7d66d-138">그러나 작업 수준과 모듈 수준의 로그 심각도 설정에 충돌이 발생한 경우 모듈 수준의 심각도 설정이 고려됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-138">However, if there is any conflict between the log severity settings at the activity and module levels, the severity settings at the module level are considered.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="7d66d-139">기본적으로 **고급** 섹션에 심각도가 **정보** 로 설정된 **Microsoft.Ssdqs.Core.Startup**모듈이 미리 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-139">By default, the **Microsoft.Ssdqs.Core.Startup** module is preconfigured in the **Advanced** section with the severity level set as **Info**.</span></span> <span data-ttu-id="7d66d-140">이는 DQS 서비스의 시작 및 중지와 관련된 정보 이상의 심각도(경고, 오류 및 치명적) 이벤트에 대한 로깅을 설정하기 위함입니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-140">This is done to enable logging of events of severity Info and higher (Warn, Error, and Fatal) that are related to starting and stopping of DQS services.</span></span>  
> -   <span data-ttu-id="7d66d-141">DQS 시스템 어셈블리에 대해 잘 알고 있는 고급 DQS 사용자인 경우에만 모듈 수준에서 로그 심각도를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-141">You should configure log severity levels at the module level only if you are an advanced DQS user who is familiar with the DQS system assemblies.</span></span>  
  
 <span data-ttu-id="7d66d-142">모듈 수준에서 로그 심각도를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="7d66d-142">To configure log severity levels at the module level:</span></span>  
  
1.  <span data-ttu-id="7d66d-143">**로그 설정** 탭에서 **고급** 에 대해 아래쪽 화살표를 클릭하여 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-143">In the **Log Settings** tab, click the down arrow against **Advanced** to display the area.</span></span>  
  
2.  <span data-ttu-id="7d66d-144">표시된 표에서 **모듈** 열에 있는 드롭다운 목록의 모듈 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-144">In the grid that appears, select a module name from the drop-down list in the **Module** column.</span></span>  
  
3.  <span data-ttu-id="7d66d-145">다음으로, **심각도** 열의 드롭다운 목록에서 모듈의 심각도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-145">Next, select a severity level for the module from the drop-down list in the **Severity** column.</span></span> <span data-ttu-id="7d66d-146">심각도 **치명적**, **오류**, **경고**, **정보**및 **디버그**중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-146">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span>  
  
     <span data-ttu-id="7d66d-147">예를 들어 도메인 관리 작업 내에서 **Microsoft.Ssdqs.DomainRules.Define** 모듈을 선택하고 다른 로그 심각도를 선택하여 도메인 규칙 정의 기능의 세분성 수준을 도메인 관리 작업과 다르게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-147">For example, within the domain management activity, you can set a different granularity level for the domain rule definition functionality than the domain management activity by selecting the **Microsoft.Ssdqs.DomainRules.Define** module, and selecting a different log severity level.</span></span> <span data-ttu-id="7d66d-148">마찬가지로 **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** 모듈을 선택하고 다른 로그 심각도를 선택하여 도메인 간 규칙 기능의 세분성 수준을 다르게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-148">Similarly, you can set a different granularity level for the cross-domain rule functionality by selecting the **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** module, and selecting a different log severity level.</span></span>  
  
4.  <span data-ttu-id="7d66d-149">필요한 경우 다른 모듈에 대해 2단계와 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-149">Repeat steps 2 and 3 for other modules, if required.</span></span> <span data-ttu-id="7d66d-150">또한 **모듈 추가** 및 **모듈 제거** 아이콘을 클릭하여 표에서 행을 추가하거나 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-150">You can also add or delete rows to the grid by clicking the **Add Module** and **Remove Module** icons.</span></span>  
  
5.  <span data-ttu-id="7d66d-151">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d66d-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d66d-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d66d-152">See Also</span></span>  
 [<span data-ttu-id="7d66d-153">Configure Advanced Settings for DQS Log Files</span><span class="sxs-lookup"><span data-stu-id="7d66d-153">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
