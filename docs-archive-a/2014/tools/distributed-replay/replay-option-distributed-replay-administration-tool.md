---
title: 재생 옵션(Distributed Replay Administration Tool) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740618"
---
# <a name="replay-option-distributed-replay-administration-tool"></a><span data-ttu-id="ddb1a-102">재생 옵션(Distributed Replay Administration Tool)</span><span class="sxs-lookup"><span data-stu-id="ddb1a-102">Replay Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="ddb1a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인는 `DReplay.exe` Distributed Replay controller와 통신 하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="ddb1a-104">이 항목에서는 **replay** 명령줄 옵션과 해당 구문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-104">This topic describes the **replay** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="ddb1a-105">**replay** 옵션은 이벤트 재생 단계를 시작합니다. 이 단계에서 컨트롤러는 재생 데이터를 지정된 클라이언트로 발송하고 분산 재생을 시작하며 클라이언트를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-105">The **replay** option initiates the event replay stage, in which the controller dispatches replay data to the specified clients, launches the distributed replay and synchronizes the clients.</span></span> <span data-ttu-id="ddb1a-106">필요에 따라 재생에 참여하는 각 클라이언트는 재생 작업을 기록하고 결과 추적 파일을 로컬에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-106">Optionally, each client participating in the replay can record the replay activity and save a result trace file locally.</span></span>

 <span data-ttu-id="ddb1a-107">![항목 링크 아이콘](../../database-engine/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="ddb1a-108">구문</span><span class="sxs-lookup"><span data-stu-id="ddb1a-108">Syntax</span></span>

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="ddb1a-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ddb1a-109">Parameters</span></span>
 <span data-ttu-id="ddb1a-110">**-m** *컨트롤러* 컨트롤러의 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="ddb1a-111">"`localhost`" 또는 "`.`"을 사용하여 로컬 컴퓨터를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="ddb1a-112">**-m** 매개 변수를 지정하지 않으면 로컬 컴퓨터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="ddb1a-113">**-d** *controller_working_dir* 중간 파일이 저장 되는 컨트롤러의 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-113">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="ddb1a-114">**-d** 매개 변수는 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-114">The **-d** parameter is required.</span></span>

 <span data-ttu-id="ddb1a-115">적용되는 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-115">The following requirements apply:</span></span>

-   <span data-ttu-id="ddb1a-116">디렉터리가 컨트롤러에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-116">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="ddb1a-117">드라이브 문자로 시작하는 전체 경로(예: `c:\WorkingDir`)를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-117">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="ddb1a-118">경로가 백슬래시("`\`")로 끝나지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-118">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="ddb1a-119">UNC 경로는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-119">UNC paths are not supported.</span></span>

 <span data-ttu-id="ddb1a-120">**-o** 클라이언트의 재생 작업을 캡처하여 `<ResultDirectory>` 클라이언트 구성 파일의 요소에 지정 된 경로에 있는 결과 추적 파일에 저장 `DReplayClient.xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-120">**-o** Captures the clients' replay activity and saves it to a result trace file in the path specified by the `<ResultDirectory>` element in the client configuration file, `DReplayClient.xml`.</span></span>

 <span data-ttu-id="ddb1a-121">**–o** 매개 변수를 지정하지 않으면 결과 추적 파일이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-121">When the **-o** parameter is not specified, the result trace file is not generated.</span></span> <span data-ttu-id="ddb1a-122">콘솔 출력은 재생이 끝날 때 요약 정보를 반환하지만 그 외 다른 재생 통계는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-122">The console output returns summary information at the end of replay, but no other replay statistics are available.</span></span>

 <span data-ttu-id="ddb1a-123">**-s** *target_server* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 분산 작업을 재생 해야 하는 대상 인스턴스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-123">**-s** *target_server* Specifies the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that the distributed workload should be replayed against.</span></span> <span data-ttu-id="ddb1a-124">이 매개 변수는 **server_name[\인스턴스 이름]** 형식으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-124">You must specify this parameter in the format **server_name[\instance name]**.</span></span>

 <span data-ttu-id="ddb1a-125">"`localhost`" 또는 "`.`"을 대상 서버로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-125">You cannot use "`localhost`" or "`.`" as the target server.</span></span>

 <span data-ttu-id="ddb1a-126">재생 구성 파일 **의** 섹션에 `<Server>` 요소가 지정되어 있으면 `<ReplayOptions>` -s `DReplay.exe.replay.config`매개 변수를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-126">The **-s** parameter is not required if the `<Server>` element is specified in the `<ReplayOptions>` section of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="ddb1a-127">**-s** 매개 변수를 사용하는 경우 재생 구성 파일의 `<Server>` 섹션에 있는 `<ReplayOptions>` 요소가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-127">If the **-s** parameter is used, the `<Server>` element in the `<ReplayOptions>` section of the replay configuration file will be ignored.</span></span>

 <span data-ttu-id="ddb1a-128">**-w** *클라이언트* 이 필수 매개 변수는 분산 재생에 참여할 클라이언트의 컴퓨터 이름을 지정 하는 쉼표로 구분 된 목록 (공백 없음)입니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-128">**-w** *clients* This required parameter is a comma-separated list (without spaces) that specifies the computer names of clients that should participate in the distributed replay.</span></span> <span data-ttu-id="ddb1a-129">IP 주소는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-129">IP addresses are not allowed.</span></span> <span data-ttu-id="ddb1a-130">클라이언트가 컨트롤러에 이미 등록되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-130">Be aware that the clients must already be registered with the controller.</span></span>

> [!NOTE]
>  <span data-ttu-id="ddb1a-131">각 클라이언트는 클라이언트 서비스가 시작될 때 클라이언트 구성 파일에 지정된 컨트롤러에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-131">Each client registers with the controller that is specified in the client configuration file when the client service starts.</span></span>

 <span data-ttu-id="ddb1a-132">**-c** *config_file* 재생 구성 파일의 전체 경로입니다. 다른 위치에 저장 되는 위치를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-132">**-c** *config_file* Is the full path of the replay configuration file; used to specify the location when it is stored in a different location.</span></span>

 <span data-ttu-id="ddb1a-133">재생 구성 파일 **의 기본값을 사용하려는 경우** -c `DReplay.exe.replay.config`매개 변수를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-133">The **-c** parameter is not required if you want to use the default values of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="ddb1a-134">**-f** *status_interval* 상태를 표시할 빈도 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-134">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="ddb1a-135">**-f** 를 지정하지 않을 경우 기본 간격은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-135">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="ddb1a-136">예</span><span class="sxs-lookup"><span data-stu-id="ddb1a-136">Examples</span></span>
 <span data-ttu-id="ddb1a-137">이 예에서는 분산 재생 동작의 대부분이 수정된 재생 구성 파일인 `DReplay.exe.replay.config`에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-137">In this example, the distributed replay derives much of its behavior from a modified replay configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="ddb1a-138">**-m** 매개 변수는 `controller1` 이라는 컴퓨터가 컨트롤러로 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-138">The **-m** parameter specifies that a computer named `controller1` acts as the controller.</span></span> <span data-ttu-id="ddb1a-139">컨트롤러 서비스가 다른 컴퓨터에서 실행 중일 때는 컴퓨터 이름을 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-139">The computer name must be specified when the controller service is running on a different computer.</span></span>

-   <span data-ttu-id="ddb1a-140">**-d** 매개 변수는 컨트롤러에서 중간 파일의 위치( `c:\WorkingDir`)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-140">The **-d** parameter specifies the location of the intermediate file on the controller, `c:\WorkingDir`.</span></span>

-   <span data-ttu-id="ddb1a-141">**-o** 매개 변수는 지정된 각 클라이언트가 재생 작업을 캡처하여 결과 추적 파일에 저장하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-141">The **-o** parameter specifies that each specified client capture the replay activity and save it to a result trace file.</span></span> <span data-ttu-id="ddb1a-142">참고: 구성 파일의 `<ResultTrace>` 요소를 사용하면 행 개수 및 결과 집합을 기록할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-142">Note: The `<ResultTrace>` element in the configuration file can be used to specify if row count and result set be recorded.</span></span>

-   <span data-ttu-id="ddb1a-143">**-w** 매개 변수는 `client1` 부터 `client4` 까지의 컴퓨터가 분산 재생에 클라이언트로 참여하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-143">The **-w** parameter specifies that computers `client1` through `client4` participate as clients in the distributed replay.</span></span>

-   <span data-ttu-id="ddb1a-144">**-c** 매개 변수는 수정된 구성 파일인 `DReplay.exe.replay.config`를 가리키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-144">The **-c** parameter is used to point to the modified configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="ddb1a-145">재생 구성 파일 **의** 요소에 `<Server>` 요소가 지정되어 있으므로 `<ReplayOptions>` -s `DReplay.exe.replay.config`매개 변수를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-145">The **-s** parameter is not required because the `<Server>` element is specified in the `<ReplayOptions>` element of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="ddb1a-146">다음 구문을 사용하여 이벤트 재생 단계가 시작되며 이때 관리 도구는 컨트롤러와는 다른 컴퓨터에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-146">The event replay stage is initiated with the following syntax, when the administration tool is run from a different computer than the controller:</span></span>

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 <span data-ttu-id="ddb1a-147">동기 시퀀스 모드를 지정하기 위해 `<SequencingMode>` 파일의 `DReplay.exe.replay.config` 요소가 `synchronization`값으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-147">To specify a synchronous sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `synchronization`.</span></span> <span data-ttu-id="ddb1a-148">행 개수를 기록하도록 지정하기 위해 재생 구성 파일의 `<ResultTrace>` 섹션이 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-148">The `<ResultTrace>` section of the replay configuration file is modified to specify that row count be recorded.</span></span> <span data-ttu-id="ddb1a-149">다음 XML 예에서는 이러한 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-149">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 <span data-ttu-id="ddb1a-150">스트레스 시퀀스 모드를 지정하기 위해 `<SequencingMode>` 파일의 `DReplay.exe.replay.config` 요소가 `stress`값으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-150">To specify a stress sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `stress`.</span></span> <span data-ttu-id="ddb1a-151">`<ConnectTimeScale>` 과 `<ThinkTimeScale>` 요소는 50%를 지정하기 위해 `50` 으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-151">The `<ConnectTimeScale>` and `<ThinkTimeScale>` elements are set to the value `50` (to specify 50 percent).</span></span> <span data-ttu-id="ddb1a-152">연결 시간 및 대기 시간에 대한 자세한 내용은 [Configure Distributed Replay](configure-distributed-replay.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-152">For more information about connect time and think time, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span> <span data-ttu-id="ddb1a-153">다음 XML 예에서는 이러한 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-153">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="ddb1a-154">사용 권한</span><span class="sxs-lookup"><span data-stu-id="ddb1a-154">Permissions</span></span>
 <span data-ttu-id="ddb1a-155">관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-155">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="ddb1a-156">로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-156">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="ddb1a-157">자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddb1a-157">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddb1a-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddb1a-158">See Also</span></span>
 <span data-ttu-id="ddb1a-159">[추적 데이터 재생](replay-trace-data.md) [Distributed Replay SQL Server](sql-server-distributed-replay.md) [재생 결과를 검토 하 고](review-the-replay-results.md) Distributed Replay [를 사용 하 여 Distributed Replay 테스트 SQL Server을 사용 하 여](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) Distributed Replay 테스트를 [SQL Server](https://social.technet.microsoft.com/Forums/sl/sqldru/) [Distributed Replay 구성](configure-distributed-replay.md) 합니다. SQL Server를 사용 하 여 [테스트를 부하 테스트 1 부](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span><span class="sxs-lookup"><span data-stu-id="ddb1a-159">[Replay Trace Data](replay-trace-data.md) [Review the Replay Results](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay Forum](https://social.technet.microsoft.com/Forums/sl/sqldru/) [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span></span>


