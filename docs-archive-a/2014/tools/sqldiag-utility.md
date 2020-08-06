---
title: SQLdiag 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], SQLdiag
- stopping diagnostic collection
- storing diagnostic information
- performance [SQL Server], diagnostic collection
- diagnostic records [SQL Server]
- scripts [SQL Server], diagnostic collection
- logs [SQL Server], diagnostic collection
- starting diagnostic collection
- clustered instance of SQL Server
- monitoring performance [SQL Server], diagnostic collection
- security [SQL Server], diagnostic collection
- SQLDIAG service
- space [SQL Server], diagnostic collection
- SQLdiag utility
- disk space [SQL Server], diagnostic collection
- configuration files [SQL Server]
- automatic diagnostic collection
- clusters [SQL Server], diagnostic collection
ms.assetid: 45ba1307-33d1-431e-872c-a6e4556f5ff2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0559e0b2261ed5ba1c9c384608d04194d685f695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727560"
---
# <a name="sqldiag-utility"></a><span data-ttu-id="ebc49-102">SQLdiag Utility</span><span class="sxs-lookup"><span data-stu-id="ebc49-102">SQLdiag Utility</span></span>
  <span data-ttu-id="ebc49-103">**SQLdiag** 유틸리티는 콘솔 애플리케이션 또는 서비스로 실행할 수 있는 범용 진단 정보 수집 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-103">The **SQLdiag** utility is a general purpose diagnostics collection utility that can be run as a console application or as a service.</span></span> <span data-ttu-id="ebc49-104">**SQLdiag** 를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 및 기타 서버 유형에서 로그 및 데이터 파일을 수집할 수 있으며 이러한 파일을 사용하여 지속적으로 서버를 모니터링하거나 특정 서버 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-104">You can use **SQLdiag** to collect logs and data files from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="ebc49-105">**SQLdiag** 는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 고객 지원 서비스에서 진단 정보를 빠르고 간편하게 수집할 수 있도록 지원하는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-105">**SQLdiag** is intended to expedite and simplify diagnostic information gathering for [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-106">이 유틸리티는 변경될 수 있으며 해당 명령줄 인수나 동작을 사용하는 애플리케이션 또는 스크립트의 경우 후속 릴리스에서 제대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-106">This utility may be changed, and applications or scripts that rely on its command line arguments or behavior may not work correctly in future releases.</span></span>  
  
 <span data-ttu-id="ebc49-107">**SQLdiag** 에서는 다음과 같은 진단 정보를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-107">**SQLdiag** can collect the following types of diagnostic information:</span></span>  
  
-   <span data-ttu-id="ebc49-108">Windows 성능 로그</span><span class="sxs-lookup"><span data-stu-id="ebc49-108">Windows performance logs</span></span>  
  
-   <span data-ttu-id="ebc49-109">Windows 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="ebc49-109">Windows event logs</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="ebc49-110">추적 정보</span><span class="sxs-lookup"><span data-stu-id="ebc49-110">traces</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ebc49-111">차단 정보</span><span class="sxs-lookup"><span data-stu-id="ebc49-111">blocking information</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ebc49-112">구성 정보</span><span class="sxs-lookup"><span data-stu-id="ebc49-112">configuration information</span></span>  
  
 <span data-ttu-id="ebc49-113">SQLDiag.xml 구성 파일을 편집하여 **SQLdiag** 에서 수집할 정보 유형을 지정할 수 있습니다. 이에 대해서는 다음 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-113">You can specify what types of information you want **SQLdiag** to collect by editing the configuration file SQLDiag.xml, which is described in a following section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc49-114">구문</span><span class="sxs-lookup"><span data-stu-id="ebc49-114">Syntax</span></span>  
  
```  
  
      sqldiag   
     { [/?] }  
     |  
     { [/I configuration_file]  
       [/O output_folder_path]  
       [/Psupport_folder_path]  
       [/Noutput_folder_management_option]  
       [/Mmachine1 [ machine2machineN]| @machinelistfile]  
       [/Cfile_compression_type]  
       [/B [+]start_time]  
       [/E [+]stop_time]  
       [/ASQLdiag_application_name]  
       [/T { tcp [ ,port ] | np | lpc } ]  
       [/Q] [/G] [/R] [/U] [/L] [/X] }  
     |  
     { [START | STOP | STOP_ABORT] }  
     |  
     { [START | STOP | STOP_ABORT] /ASQLdiag_application_name }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ebc49-115">인수</span><span class="sxs-lookup"><span data-stu-id="ebc49-115">Arguments</span></span>  
 <span data-ttu-id="ebc49-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="ebc49-116">**/?**</span></span>  
 <span data-ttu-id="ebc49-117">사용 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-117">Displays usage information.</span></span>  
  
 <span data-ttu-id="ebc49-118">**/I** _configuration_file_</span><span class="sxs-lookup"><span data-stu-id="ebc49-118">**/I** _configuration_file_</span></span>  
 <span data-ttu-id="ebc49-119">**SQLdiag** 에서 사용할 구성 파일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-119">Sets the configuration file for **SQLdiag** to use.</span></span> <span data-ttu-id="ebc49-120">기본적으로 **/I** 는 SQLDiag.Xml로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-120">By default, **/I** is set to SQLDiag.Xml.</span></span>  
  
 <span data-ttu-id="ebc49-121">**/O** _output_folder_path_</span><span class="sxs-lookup"><span data-stu-id="ebc49-121">**/O** _output_folder_path_</span></span>  
 <span data-ttu-id="ebc49-122">**SQLdiag** 출력을 지정된 폴더로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-122">Redirects **SQLdiag** output to the specified folder.</span></span> <span data-ttu-id="ebc49-123">**/O** 옵션을 지정하지 않으면 **SQLdiag** 출력이 **SQLdiag** 시작 폴더의 SQLDIAG라는 하위 폴더에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-123">If the **/O** option is not specified, **SQLdiag** output is written to a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="ebc49-124">SQLDIAG 폴더가 없으면 **SQLdiag** 에서 이 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-124">If the SQLDIAG folder does not exist, **SQLdiag** attempts to create it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-125">출력 폴더 위치는 **/P**로 지정할 수 있는 지원 폴더 위치에 대해 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-125">The output folder location is relative to the support folder location that can be specified with **/P**.</span></span> <span data-ttu-id="ebc49-126">완전히 다른 출력 폴더 위치를 설정하려면 **/O**에 대해 전체 디렉터리 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-126">To set an entirely different location for the output folder, specify the full directory path for **/O**.</span></span>  
  
 <span data-ttu-id="ebc49-127">**/P** _support_folder_path_</span><span class="sxs-lookup"><span data-stu-id="ebc49-127">**/P** _support_folder_path_</span></span>  
 <span data-ttu-id="ebc49-128">지원 폴더 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-128">Sets the support folder path.</span></span> <span data-ttu-id="ebc49-129">기본적으로 **/P** 는 **SQLdiag** 실행 파일이 있는 폴더로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-129">By default, **/P** is set to the folder where the **SQLdiag** executable resides.</span></span> <span data-ttu-id="ebc49-130">지원 폴더에는 XML 구성 파일, Transact-SQL 스크립트 및 진단 정보를 수집하는 동안 유틸리티에서 사용하는 기타 파일을 비롯한 **SQLdiag** 지원 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-130">The support folder contains **SQLdiag** support files, such as the XML configuration file, Transact-SQL scripts, and other files that the utility uses during diagnostics collection.</span></span> <span data-ttu-id="ebc49-131">이 옵션을 사용하여 대체 지원 파일 경로를 지정하면 **SQLdiag** 는 지정한 폴더에 없는 경우 필요한 지원 파일을 자동으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-131">If you use this option to specify an alternate support files path, **SQLdiag** will automatically copy the support files it requires to the specified folder if they do not already exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-132">현재 폴더를 지원 경로로 설정하려면 다음과 같이 명령줄에서 **%cd%** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-132">To set your current folder as the support path, specify **%cd%** on the command line as follows:</span></span>  
>   
>  <span data-ttu-id="ebc49-133">**SQLDIAG /P %cd%**</span><span class="sxs-lookup"><span data-stu-id="ebc49-133">**SQLDIAG /P %cd%**</span></span>  
  
 <span data-ttu-id="ebc49-134">**/N** _output_folder_management_option_</span><span class="sxs-lookup"><span data-stu-id="ebc49-134">**/N** _output_folder_management_option_</span></span>  
 <span data-ttu-id="ebc49-135">**SQLdiag** 가 시작될 때 출력 폴더를 덮어쓸 것인지 또는 이름을 바꿀 것인지 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-135">Sets whether **SQLdiag** overwrites or renames the output folder when it starts up.</span></span> <span data-ttu-id="ebc49-136">사용 가능한 옵션은</span><span class="sxs-lookup"><span data-stu-id="ebc49-136">Available options:</span></span>  
  
 <span data-ttu-id="ebc49-137">1 = 출력 폴더를 덮어씁니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="ebc49-137">1 = Overwrites the output folder (default)</span></span>  
  
 <span data-ttu-id="ebc49-138">2 = **SQLdiag** 가 시작될 때 출력 폴더의 이름을 SQLDIAG_00001, SQLDIAG_00002 등으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-138">2 = When **SQLdiag** starts up, it renames the output folder to SQLDIAG_00001, SQLDIAG_00002, and so on.</span></span> <span data-ttu-id="ebc49-139">현재 출력 폴더의 이름을 바꾼 다음 **SQLdiag** 는 기본 출력 폴더 SQLDIAG에 출력을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-139">After renaming the current output folder, **SQLdiag** writes output to the default output folder SQLDIAG.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-140">**SQLdiag** 는 시작할 때 현재 출력 폴더에 출력을 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-140">**SQLdiag** does not append output to the current output folder when it starts up.</span></span> <span data-ttu-id="ebc49-141">대신 기본 출력 폴더를 덮어쓰거나(옵션 1) 폴더의 이름을 바꾼 다음(옵션 2) SQLDIAG라는 새 기본 출력 폴더에 출력을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-141">It can only overwrite the default output folder (option 1) or rename the folder (option 2), and then it writes output to the new default output folder named SQLDIAG.</span></span>  
  
 <span data-ttu-id="ebc49-142">**/M** _machine1_ [ *machine2 \* \* machineN*] |*@machinelistfile*</span><span class="sxs-lookup"><span data-stu-id="ebc49-142">**/M** _machine1_ [ *machine2\*\*machineN*] | *@machinelistfile*</span></span>  
 <span data-ttu-id="ebc49-143">구성 파일에 지정된 컴퓨터를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-143">Overrides the machines specified in the configuration file.</span></span> <span data-ttu-id="ebc49-144">기본적으로 구성 파일은 SQLDiag.Xml이거나 **/I** 매개 변수를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-144">By default the configuration file is SQLDiag.Xml, or is set with the **/I** parameter.</span></span> <span data-ttu-id="ebc49-145">둘 이상의 컴퓨터를 지정할 경우 각 컴퓨터 이름을 공백으로 구분하십시오.</span><span class="sxs-lookup"><span data-stu-id="ebc49-145">When specifying more than one machine, separate each machine name with a space.</span></span>  
  
 <span data-ttu-id="ebc49-146">을 사용 하 여 *@machinelistfile* 구성 파일에 저장할 컴퓨터 목록 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-146">Using *@machinelistfile* specifies a machine list filename to be stored in the configuration file.</span></span>  
  
 <span data-ttu-id="ebc49-147">**/C** _file_compression_type_</span><span class="sxs-lookup"><span data-stu-id="ebc49-147">**/C** _file_compression_type_</span></span>  
 <span data-ttu-id="ebc49-148">**SQLdiag** 출력 폴더 파일에서 사용되는 파일 압축 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-148">Sets the type of file compression used on the **SQLdiag** output folder files.</span></span> <span data-ttu-id="ebc49-149">사용 가능한 옵션은</span><span class="sxs-lookup"><span data-stu-id="ebc49-149">Available options:</span></span>  
  
 <span data-ttu-id="ebc49-150">0 = 없음(기본값)</span><span class="sxs-lookup"><span data-stu-id="ebc49-150">0 = none (default)</span></span>  
  
 <span data-ttu-id="ebc49-151">1 = NTFS 압축을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-151">1 = uses NTFS compression</span></span>  
  
 <span data-ttu-id="ebc49-152">**/B** [ **+** ]*start_time*</span><span class="sxs-lookup"><span data-stu-id="ebc49-152">**/B** [**+**]*start_time*</span></span>  
 <span data-ttu-id="ebc49-153">진단 데이터 수집 시작 날짜와 시간을 다음 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-153">Specifies the date and time to start collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="ebc49-154">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="ebc49-154">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="ebc49-155">시간은 24시간제 표시법으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-155">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="ebc49-156">예를 들어 오후 2시는</span><span class="sxs-lookup"><span data-stu-id="ebc49-156">For example, 2:00 P.M.</span></span> <span data-ttu-id="ebc49-157">**14:00:00**으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-157">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="ebc49-158">날짜 없이 HH:MM:SS에 **+** 를 사용하여 현재 날짜와 시간에 대한 상대 시간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-158">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="ebc49-159">예를 들어 **/B +02:00:00**으로 지정하면 **SQLdiag** 에서는 2시간 후부터 정보 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-159">For example, if you specify **/B +02:00:00**, **SQLdiag** will wait 2 hours before it starts collecting information.</span></span>  
  
 <span data-ttu-id="ebc49-160">**+** 와 지정한 *start_time*사이에 공백을 넣지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ebc49-160">Do not insert a space between **+** and the specified *start_time*.</span></span>  
  
 <span data-ttu-id="ebc49-161">지정한 시작 시간이 과거일 경우 **SQLdiag** 에서 강제로 시작 날짜를 변경하여 시작 날짜와 시간을 미래 시간으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-161">If you specify a start time that is in the past, **SQLdiag** forcibly changes the start date so the start date and time are in the future.</span></span> <span data-ttu-id="ebc49-162">예를 들어 현재 시간이 08:00:00인데 **/B 01:00:00** 으로 지정하면 **SQLdiag** 에서 강제로 시작 날짜를 다음 날로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-162">For example, if you specify **/B 01:00:00** and the current time is 08:00:00, **SQLdiag** forcibly changes the start date so that the start date is the next day.</span></span>  
  
 <span data-ttu-id="ebc49-163">**SQLdiag** 는 유틸리티를 실행하는 컴퓨터의 현지 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-163">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="ebc49-164">**/E** [ **+** ]*stop_time*</span><span class="sxs-lookup"><span data-stu-id="ebc49-164">**/E** [**+**]*stop_time*</span></span>  
 <span data-ttu-id="ebc49-165">진단 데이터 수집 종료 날짜와 시간을 다음 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-165">Specifies the date and time to stop collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="ebc49-166">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="ebc49-166">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="ebc49-167">시간은 24시간제 표시법으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-167">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="ebc49-168">예를 들어 오후 2시는</span><span class="sxs-lookup"><span data-stu-id="ebc49-168">For example, 2:00 P.M.</span></span> <span data-ttu-id="ebc49-169">**14:00:00**으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-169">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="ebc49-170">날짜 없이 HH:MM:SS에 **+** 를 사용하여 현재 날짜와 시간에 대한 상대 시간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-170">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="ebc49-171">예를 들어 시작 시간과 종료 시간을 **/B +02:00:00 /E +03:00:00**으로 지정하면 **SQLdiag** 에서는 2시간 후부터 정보 수집을 시작하고 3시간 동안 정보를 수집한 다음 중지하고 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-171">For example, if you specify a start time and end time by using **/B +02:00:00 /E +03:00:00**, **SQLdiag** waits 2 hours before it starts collecting information, then collects information for 3 hours before it stops and exits.</span></span> <span data-ttu-id="ebc49-172">**/B** 를 지정하지 않으면 **SQLdiag** 에서 즉시 진단 정보 수집을 시작하고 **/E**로 지정된 날짜와 시간에 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-172">If **/B** is not specified, **SQLdiag** starts collecting diagnostics immediately and ends at the date and time specified by **/E**.</span></span>  
  
 <span data-ttu-id="ebc49-173">**+** 와 지정한 *start_time* 또는 *end_time*사이에 공백을 넣지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ebc49-173">Do not insert a space between **+** and the specified *start_time* or *end_time*.</span></span>  
  
 <span data-ttu-id="ebc49-174">**SQLdiag** 는 유틸리티를 실행하는 컴퓨터의 현지 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-174">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="ebc49-175">**/A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="ebc49-175">**/A** _SQLdiag_application_name_</span></span>  
 <span data-ttu-id="ebc49-176">동일한 **인스턴스에 대해 여러** SQLdiag [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 인스턴스를 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-176">Enables running multiple instances of the **SQLdiag** utility against the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="ebc49-177">각 *SQLdiag_application_name* 은 서로 다른 **SQLdiag**인스턴스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-177">Each *SQLdiag_application_name* identifies a different instance of **SQLdiag**.</span></span> <span data-ttu-id="ebc49-178">*SQLdiag_application_name* 인스턴스와 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 이름은 전혀 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-178">No relationship exists between a *SQLdiag_application_name* instance and a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="ebc49-179">*SQLdiag_application_name* 은 특정 **SQLdiag** 서비스 인스턴스를 시작하거나 중지하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-179">*SQLdiag_application_name* can be used to start or stop a specific instance of the **SQLdiag** service.</span></span>  
  
 <span data-ttu-id="ebc49-180">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-180">For example:</span></span>  
  
 <span data-ttu-id="ebc49-181">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="ebc49-181">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
 <span data-ttu-id="ebc49-182">또한 **/R** 옵션과 함께 사용하여 특정 **SQLdiag** 인스턴스를 서비스로 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-182">It can also be used with the **/R** option to register a specific instance of **SQLdiag** as a service.</span></span> <span data-ttu-id="ebc49-183">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-183">For example:</span></span>  
  
 <span data-ttu-id="ebc49-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="ebc49-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-185">**SQLdiag** 는 *SQLdiag_application_name*에 대해 지정한 인스턴스 이름 앞에 DIAG$를 자동으로 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-185">**SQLdiag** automatically prefixes DIAG$ to the instance name specified for *SQLdiag_application_name*.</span></span> <span data-ttu-id="ebc49-186">**SQLdiag** 를 서비스로 등록하는 경우 이를 통해 구분이 가능한 서비스 이름이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-186">This provides a sensible service name if you register **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="ebc49-187">/T { tcp [ ,*port* ] | np | lpc }</span><span class="sxs-lookup"><span data-stu-id="ebc49-187">/T { tcp [ ,*port* ] | np | lpc }</span></span>  
 <span data-ttu-id="ebc49-188">지정된 프로토콜을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-188">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the specified protocol.</span></span>  
  
 <span data-ttu-id="ebc49-189">tcp [,*port*]</span><span class="sxs-lookup"><span data-stu-id="ebc49-189">tcp [,*port*]</span></span>  
 <span data-ttu-id="ebc49-190">TCP/IP(Transmission Control Protocol/Internet Protocol)입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-190">Transmission Control Protocol/Internet Protocol (TCP/IP).</span></span> <span data-ttu-id="ebc49-191">필요에 따라 연결을 위한 포트 번호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-191">You can optionally specify a port number for the connection.</span></span>  
  
 <span data-ttu-id="ebc49-192">np</span><span class="sxs-lookup"><span data-stu-id="ebc49-192">np</span></span>  
 <span data-ttu-id="ebc49-193">명명된 파이프입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-193">Named pipes.</span></span> <span data-ttu-id="ebc49-194">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기본 인스턴스는 명명된 인스턴스에 대한 명명된 파이프 `\\.\pipe\sql\query` 및 `\\.\pipe\MSSQL$<instancename>\sql\query` 에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-194">By default, the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listens on named pipe `\\.\pipe\sql\query` and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="ebc49-195">대체 파이프 이름을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-195">You cannot connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using an alternate pipe name.</span></span>  
  
 <span data-ttu-id="ebc49-196">lpc</span><span class="sxs-lookup"><span data-stu-id="ebc49-196">lpc</span></span>  
 <span data-ttu-id="ebc49-197">로컬 프로시저 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-197">Local procedure call.</span></span> <span data-ttu-id="ebc49-198">이 공유 메모리 프로토콜은 클라이언트가 같은 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-198">This shared memory protocol is available if the client is connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same computer.</span></span>  
  
 <span data-ttu-id="ebc49-199">**/Q**</span><span class="sxs-lookup"><span data-stu-id="ebc49-199">**/Q**</span></span>  
 <span data-ttu-id="ebc49-200">자동 모드에서 **SQLdiag** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-200">Runs **SQLdiag** in quiet mode.</span></span> <span data-ttu-id="ebc49-201">**/Q** 는 암호 프롬프트와 같은 모든 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-201">**/Q** suppresses all prompts, such as password prompts.</span></span>  
  
 <span data-ttu-id="ebc49-202">**/G**</span><span class="sxs-lookup"><span data-stu-id="ebc49-202">**/G**</span></span>  
 <span data-ttu-id="ebc49-203">제네릭 모드에서 **SQLdiag** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-203">Runs **SQLdiag** in generic mode.</span></span> <span data-ttu-id="ebc49-204">**/G** 를 지정하면 시작 시 **SQLdiag** 에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 연결을 확인하거나 사용자가 **sysadmin** 고정 서버 역할의 멤버인지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-204">When **/G** is specified, on startup **SQLdiag** does not enforce [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connectivity checks or verify that the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="ebc49-205">대신 **SQLdiag** 는 사용자에게 각각의 요청된 진단 정보를 수집할 수 있는 권한이 있는지 여부를 Windows를 통해 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-205">Instead, **SQLdiag** defers to Windows to determine whether a user has the appropriate rights to gather each requested diagnostic.</span></span>  
  
 <span data-ttu-id="ebc49-206">**/G** 를 지정하지 않으면 **SQLdiag** 에서 사용자가 Windows **Administrators** 그룹의 멤버인지 확인하고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Administrators **그룹 멤버가 아닐 경우** 진단 정보를 수집하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-206">If **/G** is not specified, **SQLdiag** checks to determine whether the user is a member of the Windows **Administrators** group, and will not collect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] diagnostics if the user is not an **Administrators** group member.</span></span>  
  
 <span data-ttu-id="ebc49-207">**/R**</span><span class="sxs-lookup"><span data-stu-id="ebc49-207">**/R**</span></span>  
 <span data-ttu-id="ebc49-208">**SQLdiag** 를 서비스로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-208">Registers **SQLdiag** as a service.</span></span> <span data-ttu-id="ebc49-209">**SQLdiag** 를 서비스로 등록할 때 지정하는 모든 명령줄 인수는 나중에 서비스를 실행할 때 사용할 수 있도록 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-209">Any command line arguments that are specified when you register **SQLdiag** as a service are preserved for future runs of the service.</span></span>  
  
 <span data-ttu-id="ebc49-210">**SQLdiag** 를 서비스로 등록할 경우 기본 서비스 이름은 SQLDIAG입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-210">When **SQLdiag** is registered as a service, the default service name is SQLDIAG.</span></span> <span data-ttu-id="ebc49-211">**/A** 인수를 사용하여 서비스 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-211">You can change the service name by using the **/A** argument.</span></span>  
  
 <span data-ttu-id="ebc49-212">다음과 같이 **START** 명령줄 인수를 사용하여 서비스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-212">Use the **START** command line argument to start the service:</span></span>  
  
 <span data-ttu-id="ebc49-213">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="ebc49-213">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="ebc49-214">다음과 같이 **net start** 명령을 사용하여 서비스를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-214">You can also use the **net start** command to start the service:</span></span>  
  
 <span data-ttu-id="ebc49-215">**net start SQLDIAG**</span><span class="sxs-lookup"><span data-stu-id="ebc49-215">**net start SQLDIAG**</span></span>  
  
 <span data-ttu-id="ebc49-216">**/U**</span><span class="sxs-lookup"><span data-stu-id="ebc49-216">**/U**</span></span>  
 <span data-ttu-id="ebc49-217">서비스로 등록된 **SQLdiag** 의 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-217">Unregisters **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="ebc49-218">명명된 **SQLdiag** 인스턴스의 등록을 취소하는 경우에는 **/A** 인수도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-218">Use the **/A** argument also if unregistering a named **SQLdiag** instance.</span></span>  
  
 <span data-ttu-id="ebc49-219">**/L**</span><span class="sxs-lookup"><span data-stu-id="ebc49-219">**/L**</span></span>  
 <span data-ttu-id="ebc49-220">각각 **/B** 또는 **/E** 인수를 사용하여 시작 시간이나 종료 시간도 지정한 경우 **SQLdiag** 가 연속 모드로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-220">Runs **SQLdiag** in continuous mode when a start time or end time is also specified with the **/B** or **/E** arguments, respectively.</span></span> <span data-ttu-id="ebc49-221">예약된 종료로 인해 진단 정보 수집이 중지되면**SQLdiag** 가 자동으로 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-221">**SQLdiag** automatically restarts after diagnostics collection stops due to a scheduled shutdown.</span></span> <span data-ttu-id="ebc49-222">예를 들어 **/E** 또는 **/X** 인수를 사용하면 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-222">For example, by using the **/E** or the **/X** arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-223">**/B** 및 **/E** 명령줄 인수를 사용하여 시작 시간이나 종료 시간을 지정하지 않는 경우 **SQLdiag** 는 **/L** 인수를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-223">**SQLdiag** ignores the **/L** argument if a start time or end time is not specified by using the **/B** and **/E** command line arguments.</span></span>  
  
 <span data-ttu-id="ebc49-224">**/L** 은 서비스 모드를 나타내는 인수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-224">Using **/L** does not imply the service mode.</span></span> <span data-ttu-id="ebc49-225">**SQLdiag** 를 서비스로 실행할 때 **/L** 을 사용하려면 해당 서비스를 등록할 때 명령줄에서 /L을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-225">To use **/L** when running **SQLdiag** as a service, specify it on the command line when you register the service.</span></span>  
  
 <span data-ttu-id="ebc49-226">**/X**</span><span class="sxs-lookup"><span data-stu-id="ebc49-226">**/X**</span></span>  
 <span data-ttu-id="ebc49-227">스냅샷 모드에서 **SQLdiag** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-227">Runs **SQLdiag** in snapshot mode.</span></span> <span data-ttu-id="ebc49-228">**SQLdiag** 는 구성된 모든 진단 정보에 대해 스냅샷을 만들고 자동으로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-228">**SQLdiag** takes a snapshot of all configured diagnostics and then shuts down automatically.</span></span>  
  
 <span data-ttu-id="ebc49-229">**START** | **STOP** | **STOP_ABORT**</span><span class="sxs-lookup"><span data-stu-id="ebc49-229">**START** | **STOP** | **STOP_ABORT**</span></span>  
 <span data-ttu-id="ebc49-230">**SQLdiag** 서비스를 시작하거나 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-230">Starts or stops the **SQLdiag** service.</span></span> <span data-ttu-id="ebc49-231">**STOP_ABORT** 는 현재 수행하고 있는 진단 정보 수집을 완료하지 않고 가능한 빨리 서비스를 강제 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-231">**STOP_ABORT** forces the service to shut down as quickly as possible without finishing collection of diagnostics it is currently collecting.</span></span>  
  
 <span data-ttu-id="ebc49-232">이러한 서비스 제어 인수를 사용할 때는 명령줄에서 첫 번째 인수로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-232">When these service control arguments are used, they must be the first argument used on the command line.</span></span> <span data-ttu-id="ebc49-233">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-233">For example:</span></span>  
  
 <span data-ttu-id="ebc49-234">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="ebc49-234">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="ebc49-235">명명된 **SQLdiag** 인스턴스를 지정하는 **/A**인수만 **START**, **STOP**또는 **STOP_ABORT** 와 함께 사용하여 특정 **SQLdiag** 서비스 인스턴스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-235">Only the **/A** argument, which specifies a named instance of **SQLdiag**, can be used with **START**, **STOP**, or **STOP_ABORT** to control a specific instance of the **SQLdiag** service.</span></span> <span data-ttu-id="ebc49-236">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-236">For example:</span></span>  
  
 <span data-ttu-id="ebc49-237">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="ebc49-237">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
## <a name="security-requirements"></a><span data-ttu-id="ebc49-238">보안 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ebc49-238">Security Requirements</span></span>  
 <span data-ttu-id="ebc49-239">**/G** 명령줄 인수를 지정하여 일반 모드에서 **SQLdiag**를 실행하지 않을 경우 **SQLdiag**를 실행하는 사용자는 Windows **Administrators** 그룹의 멤버이면서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** 고정 서버 역할의 멤버이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-239">Unless **SQLdiag** is run in generic mode (by specifying the **/G** command line argument), the user who runs **SQLdiag** must be a member of the Windows **Administrators** group and a member of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** fixed server role.</span></span> <span data-ttu-id="ebc49-240">기본적으로 **SQLdiag** 에서는 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 연결하지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-240">By default, **SQLdiag** connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Windows Authentication, but it also supports [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="ebc49-241">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ebc49-241">Performance Considerations</span></span>  
 <span data-ttu-id="ebc49-242">**SQLdiag** 를 실행할 때 성능에 주는 영향은 수집하도록 구성한 진단 데이터의 종류에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-242">The performance effects of running **SQLdiag** depend on the type of diagnostic data you have configured it to collect.</span></span> <span data-ttu-id="ebc49-243">예를 들어 **추적 정보를 수집하도록** SQLdiag [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 구성한 경우 추적할 이벤트 클래스를 많이 선택할수록 서버 성능에 더 많은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-243">For example, if you have configured **SQLdiag** to collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tracing information, the more event classes you choose to trace, the more your server performance is affected.</span></span>  
  
 <span data-ttu-id="ebc49-244">**SQLdiag** 를 실행할 때 성능에 주는 영향은 구성한 진단 정보를 개별적으로 수집할 때 드는 노력을 모두 합한 것과 거의 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-244">The performance impact of running **SQLdiag** is approximately equivalent to the sum of the costs of collecting the configured diagnostics separately.</span></span> <span data-ttu-id="ebc49-245">예를 들어 **SQLdiag** 로 추적 정보를 수집할 경우 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]를 사용하여 해당 정보를 수집할 때와 성능에 주는 영향이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-245">For example, collecting a trace with **SQLdiag** incurs the same performance cost as collecting it with [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="ebc49-246">**SQLdiag** 사용으로 인해 성능에 주는 영향은 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-246">The performance impact of using **SQLdiag** is negligible.</span></span>  
  
## <a name="required-disk-space"></a><span data-ttu-id="ebc49-247">필요한 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="ebc49-247">Required Disk Space</span></span>  
 <span data-ttu-id="ebc49-248">**SQLdiag** 에서는 여러 가지 진단 정보를 수집할 수 있으므로 **SQLdiag** 를 실행하는 데 필요한 디스크 여유 공간은 그에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-248">Because **SQLdiag** can collect different types of diagnostic information, the free disk space that is required to run **SQLdiag** varies.</span></span> <span data-ttu-id="ebc49-249">수집하는 진단 정보의 양은 서버에서 처리하는 작업의 성격과 양에 따라 다르며 몇 MB부터 몇 GB에 이르기까지 매우 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-249">The amount of diagnostic information collected depends on the nature and volume of the workload that the server is processing and may range from a few megabytes to several gigabytes.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ebc49-250">구성 파일</span><span class="sxs-lookup"><span data-stu-id="ebc49-250">Configuration Files</span></span>  
 <span data-ttu-id="ebc49-251">시작 시 **SQLdiag** 에서는 지정된 구성 파일 및 명령줄 인수를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-251">On startup, **SQLdiag** reads the configuration file and the command line arguments that have been specified.</span></span> <span data-ttu-id="ebc49-252">사용자는 구성 파일에 **SQLdiag** 가 구성 파일에 수집할 진단 정보 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-252">You specify the types of diagnostic information that **SQLdiag** collects in the configuration file.</span></span> <span data-ttu-id="ebc49-253">기본적으로 **SQLdiag** 에서는 SQLDiag.Xml 구성 파일을 사용합니다. 이 구성 파일은 해당 도구가 실행될 때마다 추출되며 **SQLdiag** 유틸리티 시작 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-253">By default, **SQLdiag** uses the SQLDiag.Xml configuration file, which is extracted each time the tool runs and is located in the **SQLdiag** utility startup folder.</span></span> <span data-ttu-id="ebc49-254">이 구성 파일은 XML 스키마인 SQLDiag_schema.xsd를 사용하며 이 스키마 또한 **SQLdiag** 를 실행할 때마다 실행 파일에서 유틸리티 시작 디렉터리로 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-254">The configuration file uses the XML schema, SQLDiag_schema.xsd, which is also extracted into the utility startup directory from the executable file each time **SQLdiag** runs.</span></span>  
  
### <a name="editing-the-configuration-files"></a><span data-ttu-id="ebc49-255">구성 파일 편집</span><span class="sxs-lookup"><span data-stu-id="ebc49-255">Editing the Configuration Files</span></span>  
 <span data-ttu-id="ebc49-256">SQLDiag.Xml을 복사 및 편집하여 **SQLdiag** 에서 수집하는 진단 데이터의 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-256">You can copy and edit SQLDiag.Xml to change the types of diagnostic data that **SQLdiag** collects.</span></span> <span data-ttu-id="ebc49-257">구성 파일을 편집할 때는 항상 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]와 같은 XML 스키마에 대해 구성 파일의 유효성을 검사할 수 있는 XML 편집기를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ebc49-257">When editing the configuration file always use an XML editor that can validate the configuration file against its XML schema, such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="ebc49-258">직접 SQLDiag.Xml을 편집해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-258">You should not edit SQLDiag.Xml directly.</span></span> <span data-ttu-id="ebc49-259">대신 SQLDiag.Xml을 복사하고 새 파일 이름으로 바꿔 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-259">Instead, make a copy of SQLDiag.Xml and rename it to a new file name in the same folder.</span></span> <span data-ttu-id="ebc49-260">그런 다음 새 파일을 편집하고 **/I** 인수를 사용하여 **SQLdiag**에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-260">Then edit the new file, and use the **/I** argument to pass it to **SQLdiag**.</span></span>  
  
#### <a name="editing-the-configuration-file-when-sqldiag-runs-as-a-service"></a><span data-ttu-id="ebc49-261">SQLdiag를 서비스로 실행할 때 구성 파일 편집</span><span class="sxs-lookup"><span data-stu-id="ebc49-261">Editing the Configuration File When SQLdiag Runs as a Service</span></span>  
 <span data-ttu-id="ebc49-262">이미 **SQLdiag** 를 서비스로 실행한 경우 구성 파일을 편집하려면 **/U** 명령줄 인수를 지정하여 SQLDIAG 서비스의 등록을 취소한 다음 **/R** 명령줄 인수를 사용하여 이 서비스를 다시 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-262">If you have already run **SQLdiag** as a service and need to edit the configuration file, unregister the SQLDIAG service by specifying the **/U** command line argument and then re-register the service by using the **/R** command line argument.</span></span> <span data-ttu-id="ebc49-263">서비스의 등록을 취소하고 다시 등록하면 Windows 레지스트리에 캐시된 이전 구성 정보가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-263">Unregistering and re-registering the service removes old configuration information that was cached in the Windows registry.</span></span>  
  
## <a name="output-folder"></a><span data-ttu-id="ebc49-264">출력 폴더</span><span class="sxs-lookup"><span data-stu-id="ebc49-264">Output Folder</span></span>  
 <span data-ttu-id="ebc49-265">**/O** 인수를 사용하여 출력 폴더를 지정하지 않으면 **SQLdiag** 가 **SQLdiag** 시작 폴더에 SQLDIAG라는 하위 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-265">If you do not specify an output folder with the **/O** argument, **SQLdiag** creates a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="ebc49-266">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 와 같이 추적 정보의 양이 많은 진단 정보를 수집하는 경우 로컬 드라이브의 출력 폴더에 요청된 진단 정보 출력을 저장할 수 있는 충분한 공간이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-266">For diagnostic information collection that involves high volume tracing, such as [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] , make sure that the output folder is on a local drive with enough space to store the requested diagnostic output.</span></span>  
  
 <span data-ttu-id="ebc49-267">**SQLdiag** 를 다시 시작하면 출력 폴더의 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-267">When **SQLdiag** is restarted, it overwrites the contents of the output folder.</span></span> <span data-ttu-id="ebc49-268">이 문제를 방지하려면 명령줄에서 **/N 2** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-268">To avoid this, specify **/N 2** on the command line.</span></span>  
  
## <a name="data-collection-process"></a><span data-ttu-id="ebc49-269">데이터 수집 프로세스</span><span class="sxs-lookup"><span data-stu-id="ebc49-269">Data Collection Process</span></span>  
 <span data-ttu-id="ebc49-270">**SQLdiag** 가 시작되면 SQLDiag.Xml에 지정된 진단 데이터를 수집하는 데 필요한 초기화 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-270">When **SQLdiag** starts, it performs the initialization checks necessary to collect the diagnostic data that have been specified in SQLDiag.Xml.</span></span> <span data-ttu-id="ebc49-271">이 프로세스는 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-271">This process may take several seconds.</span></span> <span data-ttu-id="ebc49-272">**SQLdiag** 를 콘솔 애플리케이션으로 실행하는 경우 진단 데이터 수집을 시작하면 **SQLdiag** 에서 수집을 시작했으며 Ctrl+C를 눌러 중지할 수 있음을 알리는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-272">After **SQLdiag** has started collecting diagnostic data when it is run as a console application, a message displays informing you that **SQLdiag** collection has started and that you can press CTRL+C to stop it.</span></span> <span data-ttu-id="ebc49-273">**SQLdiag** 를 서비스로 실행하는 경우 이와 비슷한 메시지가 Windows 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-273">When **SQLdiag** is run as a service, a similar message is written to the Windows event log.</span></span>  
  
 <span data-ttu-id="ebc49-274">**SQLdiag** 를 사용하여 재현할 수 있는 문제를 진단하는 경우 이 메시지가 표시된 다음에 서버에서 해당 문제를 재현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-274">If you are using **SQLdiag** to diagnose a problem that you can reproduce, wait until you receive this message before you reproduce the problem on your server.</span></span>  
  
 <span data-ttu-id="ebc49-275">**SQLdiag** 에서는 대부분의 진단 데이터를 병렬로 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-275">**SQLdiag** collects most diagnostic data in parallel.</span></span> <span data-ttu-id="ebc49-276">Windows 성능 로그 및 이벤트 로그에서 정보를 수집하는 경우를 제외하고 모든 진단 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** 유틸리티 또는 Windows 명령 프로세서와 같은 도구에 연결하여 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-276">All diagnostic information is collected by connecting to tools, such as the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** utility or the Windows command processor, except when information is collected from Windows performance logs and event logs.</span></span> <span data-ttu-id="ebc49-277">**SQLdiag** 에서는 컴퓨터당 작업자 스레드를 하나씩 사용하여 이러한 도구의 진단 데이터 수집을 모니터링하므로 동시에 여러 도구가 완료되기까지 기다려야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-277">**SQLdiag** uses one worker thread per computer to monitor the diagnostic data collection of these other tools, often simultaneously waiting for several tools to complete.</span></span> <span data-ttu-id="ebc49-278">수집이 진행되는 동안 **SQLdiag** 는 각 진단의 출력을 출력 폴더로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-278">During the collection process, **SQLdiag** routes the output from each diagnostic to the output folder.</span></span>  
  
## <a name="stopping-data-collection"></a><span data-ttu-id="ebc49-279">데이터 수집 중지</span><span class="sxs-lookup"><span data-stu-id="ebc49-279">Stopping Data Collection</span></span>  
 <span data-ttu-id="ebc49-280">**SQLdiag** 에서 진단 데이터를 수집하기 시작하면 사용자가 직접 중지하거나 지정한 시간에 중지되도록 구성한 경우를 제외하고 계속해서 데이터를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-280">After **SQLdiag** starts collecting diagnostic data, it continues to do so unless you stop it or it is configured to stop at a specified time.</span></span> <span data-ttu-id="ebc49-281">**/E** 인수를 사용하여 중지 시간을 지정하거나 **/X** 인수를 사용하여 **SQLdiag** 를 스냅샷 모드로 실행하면 지정한 시간에 중지되도록 **SQLdiag** 를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-281">You can configure **SQLdiag** to stop at a specified time by using the **/E** argument, which allows you to specify a stop time, or by using the **/X** argument, which causes **SQLdiag** to run in snapshot mode.</span></span>  
  
 <span data-ttu-id="ebc49-282">**SQLdiag** 가 중지되면 시작했던 모든 진단이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-282">When **SQLdiag** stops, it stops all diagnostics it has started.</span></span> <span data-ttu-id="ebc49-283">예를 들어 수집 중인 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 추적이 중지되고 실행 중인 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트 실행이 중지되며 데이터를 수집하는 동안 발생한 모든 하위 프로세스가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-283">For example, it stops [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] traces it was collecting, it stops executing [!INCLUDE[tsql](../includes/tsql-md.md)] scripts it was running, and it stops any sub processes it has spawned during data collection.</span></span> <span data-ttu-id="ebc49-284">진단 데이터 수집이 완료되면 **SQLdiag** 가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-284">After diagnostic data collection has completed, **SQLdiag** exits.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-285">**SQLdiag** 서비스를 일시 중지하는 작업은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-285">Pausing the **SQLdiag** service is not supported.</span></span> <span data-ttu-id="ebc49-286">**SQLdiag** 서비스를 일시 중지하면 일시 중지했을 때 수집하던 진단 정보의 수집을 완료한 다음 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-286">If you attempt to pause the **SQLdiag** service, it stops after it finishes collecting the diagnostics that it was collecting when you paused it.</span></span> <span data-ttu-id="ebc49-287">**SQLdiag** 를 중지한 다음 다시 시작하면 애플리케이션이 다시 시작되며 출력 폴더가 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-287">If you restart **SQLdiag** after stopping it, the application restarts and overwrites the output folder.</span></span> <span data-ttu-id="ebc49-288">출력 폴더를 덮어쓰지 않으려면 명령줄에서 **/N 2** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-288">To avoid overwriting the output folder, specify **/N 2** on the command line.</span></span>  
  
 <span data-ttu-id="ebc49-289">**콘솔 애플리케이션으로 실행하는 SQLdiag를 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="ebc49-289">**To stop SQLdiag when running as a console application**</span></span>  
  
 <span data-ttu-id="ebc49-290">**SQLdiag** 를 콘솔 애플리케이션으로 실행하는 경우 **SQLdiag** 가 실행 중인 콘솔 창에서 Ctrl+C를 눌러 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-290">If you are running **SQLdiag** as a console application, press CTRL+C in the console window where **SQLdiag** is running to stop it.</span></span> <span data-ttu-id="ebc49-291">Ctrl+C를 누르면 **SQLdiag** 데이터 수집이 종료되며 프로세스가 종료될 때까지 몇 분 정도 기다려야 한다는 메시지가 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-291">After you press CTRL+C, a message displays in the console window informing you that **SQLDiag** data collection is ending, and that you should wait until the process shuts down, which may take several minutes.</span></span>  
  
 <span data-ttu-id="ebc49-292">Ctrl+C를 두 번 눌러 모든 자식 진단 프로세스를 종료하고 즉시 애플리케이션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-292">Press Ctrl+C twice to terminate all child diagnostic processes and immediately terminate the application.</span></span>  
  
 <span data-ttu-id="ebc49-293">**서비스로 실행하는 SQLdiag를 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="ebc49-293">**To stop SQLdiag when running as a service**</span></span>  
  
 <span data-ttu-id="ebc49-294">**SQLdiag** 를 서비스로 실행하는 경우 **SQLdiag** 시작 폴더에서 **SQLDiag STOP** 을 실행하여 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-294">If you are running **SQLdiag** as a service, run **SQLDiag STOP** in the **SQLdiag** startup folder to stop it.</span></span>  
  
 <span data-ttu-id="ebc49-295">동일한 컴퓨터에서 여러 **SQLdiag** 인스턴스를 실행하는 경우 서비스를 중지할 때 명령줄에서 **SQLdiag** 인스턴스 이름을 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-295">If you are running multiple instances of **SQLdiag** on the same computer, you can also pass the **SQLdiag** instance name to on the command line when you stop the service.</span></span> <span data-ttu-id="ebc49-296">예를 들어 Instance1이라는 **SQLdiag** 인스턴스를 중지하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-296">For example, to stop a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG STOP /A Instance1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-297">**/A** 는 **START**, **STOP**또는 **STOP_ABORT**와 함께 사용할 수 있는 유일한 명령줄 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-297">**/A** is the only command-line argument that can be used with **START**, **STOP**, or **STOP_ABORT**.</span></span> <span data-ttu-id="ebc49-298">서비스 제어 동사 중 하나로 명명된 **SQLdiag** 인스턴스를 지정해야 하는 경우 이전 구문 예에서와 같이 명령줄에서 제어 동사 뒤에 **/A** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-298">If you need to specify a named instance of **SQLdiag** with one of the service control verbs, specify **/A** after the control verb on the command line as shown in the previous syntax example.</span></span> <span data-ttu-id="ebc49-299">제어 동사를 사용할 때는 명령줄에서 첫 번째 인수로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-299">When control verbs are used, they must be the first argument on the command line.</span></span>  
  
 <span data-ttu-id="ebc49-300">최대한 빨리 서비스를 중지하려면 유틸리티 시작 폴더에서 **SQLDIAG STOP_ABORT** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-300">To stop the service as quickly as possible, run **SQLDIAG STOP_ABORT** in the utility startup folder.</span></span> <span data-ttu-id="ebc49-301">이 명령을 사용하면 현재 수행 중인 진단 정보 수집이 완료되기를 기다리지 않고 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-301">This command aborts any diagnostics collecting currently being performed without waiting for them to finish.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-302">**SQLDiag STOP** 또는 **SQLDIAG STOP_ABORT** 를 사용하여 **SQLdiag** 서비스를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-302">Use **SQLDiag STOP** or **SQLDIAG STOP_ABORT** to stop the **SQLdiag** service.</span></span> <span data-ttu-id="ebc49-303">**SQLdiag** 또는 기타 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 서비스를 중지할 때는 Windows 서비스 콘솔을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ebc49-303">Do not use the Windows Services Console to stop **SQLdiag** or other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="automatically-starting-and-stopping-sqldiag"></a><span data-ttu-id="ebc49-304">SQLdiag 자동 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="ebc49-304">Automatically Starting and Stopping SQLdiag</span></span>  
 <span data-ttu-id="ebc49-305">지정 된 시간에 진단 데이터 수집을 자동으로 시작 하 고 중지 하려면 24 시간 표기법을 사용 하 여 **/b**_start_time_ 및 **/e**_stop_time_ 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-305">To automatically start and stop diagnostic data collection at a specified time, use the **/B**_start_time_ and **/E**_stop_time_ arguments, using 24-hour notation.</span></span> <span data-ttu-id="ebc49-306">예를 들어 계속해서 02:00:00 경에 나타나는 문제를 해결하려면 01:00:00에 자동으로 진단 데이터 수집을 시작하여 03:00:00에 자동으로 중지하도록 **SQLdiag** 를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-306">For example, if you are troubleshooting a problem that consistently appears at approximately 02:00:00, you can configure **SQLdiag** to automatically start collecting diagnostic data at 01:00 and automatically stop at 03:00:00.</span></span> <span data-ttu-id="ebc49-307">시작 시간과 중지 시간은 각각 **/B** 및 **/E** 인수를 사용하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-307">Use the **/B** and **/E** arguments to specify the start and stop time.</span></span> <span data-ttu-id="ebc49-308">24시간제 표시법을 사용하여 정확한 시작 및 중지 날짜와 시간을 YYYYMMDD_HH:MM:SS 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-308">Use 24-hour notation to specify an exact start and stop date and time with the format YYYYMMDD_HH:MM:SS.</span></span> <span data-ttu-id="ebc49-309">현재를 기준으로 상대적인 시작 시간이나 중지 시간을 지정하려면 다음 예에서와 같이 시작 및 중지 시간 앞에 **+** 를 붙이고 날짜 부분(YYYYMMDD_)을 생략합니다. 그러면 **SQLdiag** 는 1시간 후부터 정보 수집을 시작하여 3시간 동안 정보를 수집한 다음 중지하고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-309">To specify a relative start or stop time, prefix the start and stop time with **+** and omit the date portion (YYYYMMDD_) as shown in the following example, which causes **SQLdiag** to wait 1 hour before it starts collecting information, then it collects information for 3 hours before it stops and exits:</span></span>  
  
```  
sqldiag /B +01:00:00 /E +03:00:00  
```  
  
 <span data-ttu-id="ebc49-310">상대적인 *start_time* 을 지정하면 현재 날짜와 시간에 대한 상대 시간에 **SQLdiag** 가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-310">When a relative *start_time* is specified, **SQLdiag** starts at a time that is relative to the current date and time.</span></span> <span data-ttu-id="ebc49-311">상대적인 *end_time* 을 지정하면 지정한 **start_time** 에 대한 상대 시간에 *SQLdiag*가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-311">When a relative *end_time* is specified, **SQLdiag** ends at a time that is relative to the specified *start_time*.</span></span> <span data-ttu-id="ebc49-312">지정한 시작 및 종료 날짜와 시간이 과거인 경우 **SQLdiag** 에서 시작 날짜와 시간이 미래가 되도록 시작 날짜를 강제로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-312">If the start or end date and time that you have specified is in the past, **SQLdiag** forcibly changes the start date so that the start date and time are in the future.</span></span>  
  
 <span data-ttu-id="ebc49-313">이는 선택하는 시작 및 종료 날짜에 중요한 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-313">This has important implications on the start and end dates you choose.</span></span> <span data-ttu-id="ebc49-314">다음과 같은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc49-314">Consider the following example:</span></span>  
  
```  
sqldiag /B +01:00:00 /E 08:30:00  
```  
  
 <span data-ttu-id="ebc49-315">현재 시간이 08:00일 경우 실제로 진단 정보 수집을 시작하기 전에 종료 시간이 지났습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-315">If the current time is 08:00, the end time passes before diagnostic collection actually begins.</span></span> <span data-ttu-id="ebc49-316">이러한 경우 **SQLdiag** 에서 자동으로 시작 및 종료 날짜를 다음 날로 조정하기 때문에 이 예에서 진단 정보 수집은 오늘 09:00에 시작되어( **+** 를 사용하여 상대 시작 시간 지정) 다음날 아침 08:30까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-316">Because **SQLDiag** automatically adjusts start and end dates to the next day when they occur in the past, in this example diagnostic collection starts at 09:00 today (a relative start time has been specified with **+**) and continues collecting until 08:30 the following morning.</span></span>  
  
### <a name="stopping-and-restarting-sqldiag-to-collect-daily-diagnostics"></a><span data-ttu-id="ebc49-317">일일 진단 정보를 수집하는 SQLdiag 중지 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="ebc49-317">Stopping and Restarting SQLdiag to Collect Daily Diagnostics</span></span>  
 <span data-ttu-id="ebc49-318">수동으로 **SQLdiag**를 시작하고 중지할 필요 없이 지정한 진단 정보를 매일 수집하려면 **/L** 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-318">To collect a specified set of diagnostics on a daily basis without having to manually start and stop **SQLdiag**, use the **/L** argument.</span></span> <span data-ttu-id="ebc49-319">**/L** 인수를 사용하면 예약된 종료 후에 자동으로 다시 시작하여 **SQLdiag** 가 계속해서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-319">The **/L** argument causes **SQLdiag** to run continuously by automatically restarting itself after a scheduled shutdown.</span></span> <span data-ttu-id="ebc49-320">**/L** 을 지정한 경우 **SQLdiag** 가 **/E** 인수로 지정한 종료 시간에 도달해서 중지되거나 **/X** 인수를 사용하여 스냅샷 모드에서 실행되고 있기 때문에 중지되면 **SQLdiag** 가 종료되는 대신 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-320">When **/L** is specified, and **SQLdiag** stops because it has reached the end time specified with the **/E** argument, or it stops because it is being run in snapshot mode by using the **/X** argument, **SQLdiag** restarts instead of exiting.</span></span>  
  
 <span data-ttu-id="ebc49-321">다음 예에서는 연속 모드에서 **SQLdiag** 를 실행하여 03:00:00부터 05:00:00까지 진단 데이터를 수집한 후 자동으로 다시 시작하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-321">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after diagnostic data collecting occurs between 03:00:00 and 05:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /E 05:00:00 /L  
```  
  
 <span data-ttu-id="ebc49-322">다음 예에서는 연속 모드에서 **SQLdiag** 를 실행하여 03:00:00에 진단 데이터 스냅샷을 만든 후 자동으로 다시 시작하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-322">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after taking a diagnostic data snapshot at 03:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /X /L  
```  
  
## <a name="running-sqldiag-as-a-service"></a><span data-ttu-id="ebc49-323">SQLdiag를 서비스로 실행</span><span class="sxs-lookup"><span data-stu-id="ebc49-323">Running SQLdiag as a Service</span></span>  
 <span data-ttu-id="ebc49-324">**SQLdiag** 를 사용하여 장시간 진단 데이터를 수집하면서 **SQLdiag** 를 실행 중인 컴퓨터에서 로그아웃해야 할 수도 있는 경우 이를 서비스로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-324">When you want to use **SQLdiag** to collect diagnostic data for long periods of time during which you might need to log out of the computer on which **SQLdiag** is running, you can run it as a service.</span></span>  
  
 <span data-ttu-id="ebc49-325">**SQLDiag를 등록하여 서비스로 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="ebc49-325">**To register SQLDiag to run as a service**</span></span>  
  
 <span data-ttu-id="ebc49-326">명령줄에서 **/R** 인수를 지정하여 **SQLdiag** 를 등록하고 서비스로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-326">You can register **SQLdiag** to run as a service by specifying the **/R** argument at the command line.</span></span> <span data-ttu-id="ebc49-327">그러면 **SQLDiag** 가 서비스로 실행되도록 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-327">This registers **SQLdiag** to run as a service.</span></span> <span data-ttu-id="ebc49-328">**SQLdiag** 서비스 이름은 SQLDIAG입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-328">The **SQLdiag** service name is SQLDIAG.</span></span> <span data-ttu-id="ebc49-329">**SQLdiag** 를 서비스로 등록할 때 명령줄에서 지정한 다른 모든 인수는 보관되어 서비스를 시작할 때 다시 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-329">Any other arguments you specify on the command line when you register **SQLDiag** as a service are preserved and reused when the service is started.</span></span>  
  
 <span data-ttu-id="ebc49-330">기본 SQLDIAG 서비스 이름을 변경하려면 **/A** 명령줄 인수를 사용하여 다른 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-330">To change the default SQLDIAG service name, use the **/A** command-line argument to specify another name.</span></span> <span data-ttu-id="ebc49-331">**SQLdiag** 는 **/A** 를 사용하여 지정한 모든 **SQLdiag** 인스턴스 이름 앞에 DIAG$를 자동으로 붙여 구분이 가능한 서비스 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-331">**SQLdiag** automatically prefixes DIAG$ to any **SQLdiag** instance name specified with **/A** to create sensible service names.</span></span>  
  
 <span data-ttu-id="ebc49-332">**SQLDIAG 서비스의 등록을 취소하려면**</span><span class="sxs-lookup"><span data-stu-id="ebc49-332">**To unregister the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="ebc49-333">서비스의 등록을 취소하려면 **/U** 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-333">To unregister the service, specify the **/U** argument.</span></span> <span data-ttu-id="ebc49-334">서비스로 등록된 **SQLdiag** 의 등록을 취소하면 서비스의 Windows 레지스트리 키도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-334">Unregistering **SQLdiag** as a service also deletes the Windows registry keys of the service.</span></span>  
  
 <span data-ttu-id="ebc49-335">**SQLDIAG 서비스를 시작하거나 다시 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="ebc49-335">**To start or restart the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="ebc49-336">SQLDIAG 서비스를 시작하거나 다시 시작하려면 명령줄에서 **SQLDiag START** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-336">To start or restart the SQLDIAG service, run **SQLDiag START** from the command line.</span></span>  
  
 <span data-ttu-id="ebc49-337">**/A** 인수를 사용하여 여러 **SQLdiag** 인스턴스를 실행하는 경우 서비스를 시작할 때 명령줄에서 **SQLdiag** 인스턴스 이름을 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-337">If you are running multiple instances of **SQLdiag** by using the **/A** argument, you can also pass the **SQLdiag** instance name on the command line when you start the service.</span></span> <span data-ttu-id="ebc49-338">예를 들어 Instance1이라는 **SQLdiag** 인스턴스를 시작하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-338">For example, to start a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG START /A Instance1  
```  
  
 <span data-ttu-id="ebc49-339">**net start** 명령을 사용하여 SQLDIAG 서비스를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-339">You can also use the **net start** command to start the SQLDIAG service.</span></span>  
  
 <span data-ttu-id="ebc49-340">**SQLdiag**를 다시 시작하면 현재 출력 폴더의 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-340">When you restart **SQLdiag**, it overwrites the contents in the current output folder.</span></span> <span data-ttu-id="ebc49-341">이러한 문제를 방지하려면 명령줄에서 **/N 2** 를 지정하여 유틸리티가 시작될 때 출력 폴더의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-341">To avoid this, specify **/N 2** on the command line to rename the output folder when the utility starts.</span></span>  
  
 <span data-ttu-id="ebc49-342">**SQLdiag** 서비스를 일시 중지하는 작업은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-342">Pausing the **SQLdiag** service is not supported.</span></span>  
  
## <a name="running-multiple-instances-of-sqldiag"></a><span data-ttu-id="ebc49-343">여러 SQLdiag 인스턴스 실행</span><span class="sxs-lookup"><span data-stu-id="ebc49-343">Running Multiple Instances of SQLdiag</span></span>  
 <span data-ttu-id="ebc49-344">명령줄에서 **/a**_SQLdiag_application_name_ 를 지정 하 여 동일한 컴퓨터에서 여러 **SQLdiag** 인스턴스를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-344">Run multiple instances of **SQLdiag** on the same computer by specifying **/A**_SQLdiag_application_name_ on the command line.</span></span> <span data-ttu-id="ebc49-345">이는 동일한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 동시에 다른 진단 정보 집합을 수집하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-345">This is useful for collecting different sets of diagnostics simultaneously from the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="ebc49-346">예를 들어 지속적으로 간단한 데이터 수집을 수행하도록 명명된 **SQLdiag** 인스턴스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-346">For example, you can configure a named instance of **SQLdiag** to continuously perform lightweight data collection.</span></span> <span data-ttu-id="ebc49-347">그런 다음 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 특정 문제가 발생하는 경우 기본 **SQLdiag** 인스턴스를 실행하여 해당 문제에 대한 진단 정보를 수집하거나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 고객 지원 서비스에서 수집을 요청한 진단 정보 집합을 수집하여 문제를 진단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-347">Then, if a specific problem occurs on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can run the default **SQLdiag** instance to collect diagnostics for that problem, or to gather a set of diagnostics that [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services has asked you to gather to diagnose a problem.</span></span>  
  
## <a name="collecting-diagnostic-data-from-clustered-sql-server-instances"></a><span data-ttu-id="ebc49-348">클러스터형 SQL Server 인스턴스에서 진단 데이터 수집</span><span class="sxs-lookup"><span data-stu-id="ebc49-348">Collecting Diagnostic Data from Clustered SQL Server Instances</span></span>  
 <span data-ttu-id="ebc49-349">**SQLdiag** 에서는 클러스터형 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 진단 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-349">**SQLdiag** supports collecting diagnostic data from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="ebc49-350">클러스터형 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 진단 정보를 수집하려면 SQLDiag.Xml 구성 파일에서 **\<Machine>** 요소의 **name** 특성에 대해 **"."** 을 지정해야 하며 명령줄에 **/G** 인수를 지정하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-350">To gather diagnostics from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, make sure that **"."** is specified for the **name** attribute of the **\<Machine>** element in the configuration file SQLDiag.Xml and do not specify the **/G** argument on the command line.</span></span> <span data-ttu-id="ebc49-351">기본적으로 구성 파일에서 **name** 특성에는 **"."** 가 지정되고 **/G** 인수는 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-351">By default, **"."** is specified for the **name** attribute in the configuration file and the **/G** argument is turned off.</span></span> <span data-ttu-id="ebc49-352">일반적으로 클러스터형 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 정보를 수집할 때는 구성 파일을 편집하거나 명령줄 인수를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-352">Typically, you do not need to edit the configuration file or change the command line arguments when collecting from a clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="ebc49-353">**"."** 를 컴퓨터 이름으로 지정하면 **SQLdiag** 에서는 컴퓨터가 클러스터에서 실행 중임을 감지하고 해당 클러스터에 설치된 모든 가상 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 동시에 진단 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-353">When **"."** is specified as the machine name, **SQLdiag** detects that it is running on a cluster, and simultaneously retrieves diagnostic information from all virtual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are installed on the cluster.</span></span> <span data-ttu-id="ebc49-354">컴퓨터에서 실행 중인 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가상 인스턴스 중 하나에서만 진단 정보를 수집하려면 SQLDiag.Xml에서 **\<Machine>** 요소의 **name** 특성에 해당 가상 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-354">If you want to collect diagnostic information from only one virtual instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is running on a computer, specify that virtual [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] for the **name** attribute of the **\<Machine>** element in SQLDiag.Xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc49-355">클러스터형 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 인스턴스에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 추적 정보를 수집하려면 클러스터에서 관리 공유(ADMIN$)를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc49-355">To collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, administrative shares (ADMIN$) must be enabled on the cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc49-356">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ebc49-356">See Also</span></span>  
 [<span data-ttu-id="ebc49-357">명령 프롬프트 유틸리티 참조&#40;데이터베이스 엔진#41;</span><span class="sxs-lookup"><span data-stu-id="ebc49-357">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
