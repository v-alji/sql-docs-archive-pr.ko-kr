---
title: SQL Server 설치 로그 파일 보기 및 읽기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 70f9bbb9a8ed72503dc6fe90077232748b2c4ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730884"
---
# <a name="view-and-read-sql-server-setup-log-files"></a><span data-ttu-id="e6134-102">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="e6134-102">View and Read SQL Server Setup Log Files</span></span>
  <span data-ttu-id="e6134-103">설치 프로그램의 각 실행 은% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log에 새 타임 스탬프 로그 폴더를 사용 하 여 만들어집니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-103">Each execution of Setup creates log files are created with a new timestamped log folder at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span> <span data-ttu-id="e6134-104">타임스탬프 로그 폴더 이름 형식은 YYYYMMDD_hhmmss입니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-104">The time-stamped log folder name format is YYYYMMDD_hhmmss.</span></span> <span data-ttu-id="e6134-105">설치 프로그램을 무인 모드로 실행하면 % temp%\sqlsetup\*.log에 로그가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-105">When Setup is run in an unattended mode, the logs are created at % temp%\sqlsetup\*.log.</span></span> <span data-ttu-id="e6134-106">로그 폴더의 모든 파일은 각각의 로그 폴더에 Log\*.cab 파일로 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-106">All files in the logs folder are archived into the Log\*.cab file in their respective log folder.</span></span>  
  
 <span data-ttu-id="e6134-107">일반적인 설치 요청은 다음과 같은 세 가지 실행 단계를 거칩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-107">A typical Setup request goes through three execution phases:</span></span>  
  
1.  <span data-ttu-id="e6134-108">전역 규칙 텍스트</span><span class="sxs-lookup"><span data-stu-id="e6134-108">Global rules text</span></span>  
  
2.  <span data-ttu-id="e6134-109">구성 요소 업데이트</span><span class="sxs-lookup"><span data-stu-id="e6134-109">Component update</span></span>  
  
3.  <span data-ttu-id="e6134-110">사용자 요청 동작</span><span class="sxs-lookup"><span data-stu-id="e6134-110">User-requested action</span></span>  
  
 <span data-ttu-id="e6134-111">각 단계에서 설치 프로그램이 자세한 로그 및 요약 로그를 생성하며 필요한 경우 추가 로그가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-111">In each phase, Setup generates detail and summary logs with additional logs created as appropriate.</span></span> <span data-ttu-id="e6134-112">설치 프로그램은 사용자가 요청한 설치 동작마다 세 번 이상 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-112">Setup is called at least three times per user-requested Setup action.</span></span>  
  
 <span data-ttu-id="e6134-113">데이터 저장소 파일에는 설치 프로세스에서 추적하는 모든 구성 개체 상태의 스냅샷이 포함되어 있으며 이는 구성 오류 문제를 해결하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-113">Datastore files contain a snapshot of the state of all configuration objects being tracked by the Setup process, and are useful for troubleshooting configuration errors.</span></span> <span data-ttu-id="e6134-114">각 실행 단계에서는 데이터 저장소 개체에 대한 XML 파일 덤프가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-114">XML file dumps are created for datastore objects for each execution phase.</span></span> <span data-ttu-id="e6134-115">이러한 덤프는 타임스탬프 로그 폴더의 다음과 같은 자체 로그 하위 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-115">They are saved in their own log subfolder under the time-stamped log folder, as follows:</span></span>  
  
-   <span data-ttu-id="e6134-116">Datastore_GlobalRules</span><span class="sxs-lookup"><span data-stu-id="e6134-116">Datastore_GlobalRules</span></span>  
  
-   <span data-ttu-id="e6134-117">Datastore_ComponentUpdated</span><span class="sxs-lookup"><span data-stu-id="e6134-117">Datastore_ComponentUpdated</span></span>  
  
-   <span data-ttu-id="e6134-118">데이터 저장소</span><span class="sxs-lookup"><span data-stu-id="e6134-118">Datastore</span></span>  
  
 <span data-ttu-id="e6134-119">다음 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 로그 파일에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-119">The following sections describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup log files.</span></span>  
  
## <a name="summary-text"></a><span data-ttu-id="e6134-120">요약 텍스트</span><span class="sxs-lookup"><span data-stu-id="e6134-120">Summary Text</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-121">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-121">Overview</span></span>  
 <span data-ttu-id="e6134-122">이 파일은 설치 중에 검색된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소, 운영 체제 환경, 명령줄 매개 변수 값(지정된 경우) 및 각 MSI/MSP의 전반적인 실행 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-122">This file shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that were detected during Setup, the operating system environment, command-line parameter values if they are specified, and the overall status of each MSI/MSP that was executed.</span></span>  
  
 <span data-ttu-id="e6134-123">로그는 다음 섹션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-123">The log is organized into the following sections:</span></span>  
  
-   <span data-ttu-id="e6134-124">전반적인 실행 요약</span><span class="sxs-lookup"><span data-stu-id="e6134-124">An overall summary of the execution</span></span>  
  
-   <span data-ttu-id="e6134-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 실행된 컴퓨터의 속성 및 구성</span><span class="sxs-lookup"><span data-stu-id="e6134-125">Properties and the configuration of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup was run</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e6134-126">제품 기능</span><span class="sxs-lookup"><span data-stu-id="e6134-126">product features previously installed on the computer</span></span>  
  
-   <span data-ttu-id="e6134-127">설치 버전 및 설치 패키지 속성에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="e6134-127">Description of the installation version and installation package properties</span></span>  
  
-   <span data-ttu-id="e6134-128">설치 중에 제공된 런타임 입력 설정</span><span class="sxs-lookup"><span data-stu-id="e6134-128">Runtime input settings that are provided during install</span></span>  
  
-   <span data-ttu-id="e6134-129">구성 파일의 위치</span><span class="sxs-lookup"><span data-stu-id="e6134-129">Location of the configuration file</span></span>  
  
-   <span data-ttu-id="e6134-130">실행 결과의 세부 사항</span><span class="sxs-lookup"><span data-stu-id="e6134-130">Details of the execution results</span></span>  
  
-   <span data-ttu-id="e6134-131">전역 규칙</span><span class="sxs-lookup"><span data-stu-id="e6134-131">Global rules</span></span>  
  
-   <span data-ttu-id="e6134-132">설치 시나리오 관련 규칙</span><span class="sxs-lookup"><span data-stu-id="e6134-132">Rules specific to the installation scenario</span></span>  
  
-   <span data-ttu-id="e6134-133">실패한 규칙</span><span class="sxs-lookup"><span data-stu-id="e6134-133">Failed rules</span></span>  
  
-   <span data-ttu-id="e6134-134">규칙 보고서 파일의 위치</span><span class="sxs-lookup"><span data-stu-id="e6134-134">Location of the rules report file</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-135">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-135">Location</span></span>  
 <span data-ttu-id="e6134-136">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-136">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span>  
  
 <span data-ttu-id="e6134-137">요약 텍스트 파일에서 오류를 찾으려면 "오류" 또는 "실패" 키워드를 사용하여 파일을 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6134-137">To find errors in the summary text file, search the file by using the "error" or "failed" keywords.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmsstxt"></a><span data-ttu-id="e6134-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-139">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-139">Overview</span></span>  
 <span data-ttu-id="e6134-140">summary_engine base 파일은 요약 파일과 비슷하며 주 워크플로 중에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-140">The summary_engine base file is similar to the summary file and is generated during the main workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-141">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-141">Location</span></span>  
 <span data-ttu-id="e6134-142">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-142">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmss_componentupdatetxt"></a><span data-ttu-id="e6134-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-144">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-144">Overview</span></span>  
 <span data-ttu-id="e6134-145">구성 요소 업데이트 요약 로그 파일은 요약 파일과 비슷하며 구성 요소 업데이트 워크플로 중에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-145">The component update summary log file is similar to the summary file and is generated during the component update workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-146">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-146">Location</span></span>  
 <span data-ttu-id="e6134-147">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-147">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_versionnumbermmdd_hhmmss_globalrulestxt"></a><span data-ttu-id="e6134-148">Summary_engine-base_ \<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-148">Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-149">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-149">Overview</span></span>  
 <span data-ttu-id="e6134-150">전역 규칙 요약 로그 파일은 요약 파일과 비슷하며 전역 규칙 워크플로 중에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-150">The global rules summary log file is similar to the summary file generated during the global rules workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-151">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-151">Location</span></span>  
 <span data-ttu-id="e6134-152">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-152">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detailtxt"></a><span data-ttu-id="e6134-153">Detail.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-153">Detail.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-154">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-154">Overview</span></span>  
 <span data-ttu-id="e6134-155">Detail.txt는 설치 또는 업그레이드와 같은 주 워크플로 중에 생성되며 실행 세부 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-155">Detail.txt is generated for the main workflow such as install or upgrade, and provides the details of the execution.</span></span> <span data-ttu-id="e6134-156">파일의 로그는 각 설치 동작이 호출된 시간을 기준으로 생성되며 동작이 실행된 순서와 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-156">The logs in the file are generated based on the time when each action for the installation was invoked, and show the order in which the actions were executed, and their dependencies.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-157">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-157">Location</span></span>  
 <span data-ttu-id="e6134-158">% Programfiles% \120\Setup에 있습니다. \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6134-158">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup</span></span>  
  
 <span data-ttu-id="e6134-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span></span>  
  
 <span data-ttu-id="e6134-160">설치 프로세스 중에 오류가 발생하면 이 파일 끝에 예외나 오류가 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-160">If an error occurs during the Setup process, the exception or error are logged at the end of this file.</span></span> <span data-ttu-id="e6134-161">이 파일에서 오류를 찾으려면 먼저 파일 끝을 검사한 다음 "오류" 또는 "예외" 키워드로 파일을 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6134-161">To find the errors in this file, first examine the end of the file followed by a search of the file for the "error" or "exception" keywords.</span></span>  
  
## <a name="detail_componentupdatetxt"></a><span data-ttu-id="e6134-162">Detail_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-162">Detail_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-163">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-163">Overview</span></span>  
 <span data-ttu-id="e6134-164">Detail_ComponentUpdate.txt 파일은 구성 요소 업데이트 워크플로 중에 생성되며 Detail.txt와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-164">The Detail_ComponentUpdate.txt file is generated for the component update workflow and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-165">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-165">Location</span></span>  
 <span data-ttu-id="e6134-166">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-166">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detail_globalrulestxt"></a><span data-ttu-id="e6134-167">Detail_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="e6134-167">Detail_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-168">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-168">Overview</span></span>  
 <span data-ttu-id="e6134-169">Detail_GlobalRules.txt 파일은 전역 규칙 실행 중 생성되며 Detail.txt와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-169">Detail_GlobalRules.txt is generated for the global rules execution and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-170">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-170">Location</span></span>  
 <span data-ttu-id="e6134-171">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-171">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="msi-log-files"></a><span data-ttu-id="e6134-172">MSI 로그 파일</span><span class="sxs-lookup"><span data-stu-id="e6134-172">MSI log files</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-173">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-173">Overview</span></span>  
 <span data-ttu-id="e6134-174">MSI 로그 파일은 설치 패키지 프로세스의 세부 사항을 제공하며,</span><span class="sxs-lookup"><span data-stu-id="e6134-174">The MSI log files provide details of the installation package process.</span></span> <span data-ttu-id="e6134-175">지정된 패키지를 설치하는 동안 MSIEXEC에 의해 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-175">They are generated by the MSIEXEC during the installation of the specified package.</span></span>  
  
 <span data-ttu-id="e6134-176">MSI 로그 파일의 유형:</span><span class="sxs-lookup"><span data-stu-id="e6134-176">Types of MSI log files:</span></span>  
  
-   <span data-ttu-id="e6134-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="e6134-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="e6134-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="e6134-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="e6134-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span><span class="sxs-lookup"><span data-stu-id="e6134-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-180">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-180">Location</span></span>  
 <span data-ttu-id="e6134-181">MSI 로그 파일 은% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\<이름 \> .log에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-181">The MSI log files are located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\<Name\>.log.</span></span>  
  
 <span data-ttu-id="e6134-182">파일 끝에 성공/실패 상태 및 속성을 포함하는 실행 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-182">At the end of the file is a summary of the execution which includes the success or failure status and properties.</span></span> <span data-ttu-id="e6134-183">MSI 파일에서 오류를 찾으려면 "값 3"을 검색하십시오. 그러면 대개 이 문자열 부근에서 오류를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-183">To find the error in the MSI file, search for "value 3" and usually the errors can be found close to the string.</span></span>  
  
## <a name="configurationfileini"></a><span data-ttu-id="e6134-184">ConfigurationFile.ini</span><span class="sxs-lookup"><span data-stu-id="e6134-184">ConfigurationFile.ini</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-185">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-185">Overview</span></span>  
 <span data-ttu-id="e6134-186">구성 파일은 설치 중에 제공된 입력 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-186">The configuration file contains the input settings that are provided during installation.</span></span> <span data-ttu-id="e6134-187">이 파일을 사용하면 수동으로 설정을 입력하지 않고도 설치를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-187">It can be used to restart the installation without having to enter the settings manually.</span></span> <span data-ttu-id="e6134-188">그러나 계정의 암호, PID 및 일부 매개 변수는 구성 파일에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-188">However, passwords for the accounts, PID, and some parameters are not saved in the configuration file.</span></span> <span data-ttu-id="e6134-189">이러한 설정은 파일에 추가하거나 명령줄 또는 설치 사용자 인터페이스를 사용하여 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-189">The settings can be either added to the file or provided by using the command line or the Setup user interface.</span></span> <span data-ttu-id="e6134-190">자세한 내용은 [구성 파일을 사용 하 여 SQL Server 2014 설치](install-sql-server-using-a-configuration-file.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6134-190">For more information, see [Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md).</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-191">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-191">Location</span></span>  
 <span data-ttu-id="e6134-192">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-192">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="systemconfigurationcheck_reporthtm"></a><span data-ttu-id="e6134-193">SystemConfigurationCheck_Report.htm</span><span class="sxs-lookup"><span data-stu-id="e6134-193">SystemConfigurationCheck_Report.htm</span></span>  
  
### <a name="overview"></a><span data-ttu-id="e6134-194">개요</span><span class="sxs-lookup"><span data-stu-id="e6134-194">Overview</span></span>  
 <span data-ttu-id="e6134-195">시스템 구성 검사 보고서는 각 실행 규칙에 대한 간단한 설명과 실행 상태를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6134-195">The system configuration check report contains a short description for each executed rule, and the execution status.</span></span>  
  
### <a name="location"></a><span data-ttu-id="e6134-196">위치</span><span class="sxs-lookup"><span data-stu-id="e6134-196">Location</span></span>  
 <span data-ttu-id="e6134-197">% Programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="e6134-197">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6134-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6134-198">See Also</span></span>  
 <span data-ttu-id="e6134-199">[설치 방법 도움말 항목](../../sql-server/install/installation-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="e6134-199">[Installation How-to Topics](../../sql-server/install/installation-how-to-topics.md) </span></span>  
 [<span data-ttu-id="e6134-200">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="e6134-200">Install SQL Server 2014</span></span>](install-sql-server.md)  
  
  
