---
title: 전처리 옵션(Distributed Replay Utility Administration Tool) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7f168d45b03473d958e202bd75116f4519d2fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648727"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a><span data-ttu-id="44bfa-102">전처리 옵션(Distributed Replay Utility Administration Tool)</span><span class="sxs-lookup"><span data-stu-id="44bfa-102">Preprocess Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="44bfa-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인는 `DReplay.exe` Distributed Replay controller와 통신 하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="44bfa-104">이 항목에서는 **preprocess** 명령줄 옵션과 해당 구문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-104">This topic describes the **preprocess** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="44bfa-105">**프로세스** 옵션은 전처리 단계를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-105">The **preprocess** option initiates the preprocess stage.</span></span> <span data-ttu-id="44bfa-106">이 단계 동안 컨트롤러는 대상 서버에 대해 재생할 입력 추적 데이터를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-106">During this stage, the controller prepares the input trace data for replay against the target server.</span></span>

 <span data-ttu-id="44bfa-107">![항목 링크 아이콘](../../database-engine/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44bfa-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="44bfa-108">구문</span><span class="sxs-lookup"><span data-stu-id="44bfa-108">Syntax</span></span>

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="44bfa-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="44bfa-109">Parameters</span></span>
 <span data-ttu-id="44bfa-110">**-m** *컨트롤러* 컨트롤러의 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="44bfa-111">"`localhost`" 또는 "`.`"을 사용하여 로컬 컴퓨터를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="44bfa-112">**-m** 매개 변수를 지정하지 않으면 로컬 컴퓨터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="44bfa-113">**-i** *input_trace_file* 컨트롤러에서 입력 추적 파일의 전체 경로를 지정 합니다 (예:) `D:\Mytrace.trc` .</span><span class="sxs-lookup"><span data-stu-id="44bfa-113">**-i** *input_trace_file* Specifies the full path of the input trace file on the controller, such as `D:\Mytrace.trc`.</span></span> <span data-ttu-id="44bfa-114">**-i** 매개 변수는 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-114">The **-i** parameter is required.</span></span>

 <span data-ttu-id="44bfa-115">같은 디렉터리에 롤오버 파일이 있으면 자동으로 로드되어 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-115">If there are rollover files in the same directory, they will be loaded and used automatically.</span></span> <span data-ttu-id="44bfa-116">파일은 파일 롤오버 명명 규칙을 따라야 합니다(예: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, `Mytrace_n.trc`).</span><span class="sxs-lookup"><span data-stu-id="44bfa-116">The files must follow the file rollover naming convention, for example: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.</span></span>

> [!NOTE]
>  <span data-ttu-id="44bfa-117">컨트롤러와는 다른 컴퓨터에서 관리 도구를 사용하는 경우 이 매개 변수에 로컬 경로를 사용할 수 있도록 입력 추적 파일을 컨트롤러로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-117">If you are using the administration tool on a different computer than the controller, you will need to copy the input trace files to the controller so that a local path can be used for this parameter.</span></span>

 <span data-ttu-id="44bfa-118">**-d** *controller_working_dir* 중간 파일이 저장 되는 컨트롤러의 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-118">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="44bfa-119">**-d** 매개 변수는 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-119">The **-d** parameter is required.</span></span>

 <span data-ttu-id="44bfa-120">적용되는 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-120">The following requirements apply:</span></span>

-   <span data-ttu-id="44bfa-121">디렉터리가 컨트롤러에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-121">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="44bfa-122">드라이브 문자로 시작하는 전체 경로(예: `c:\WorkingDir`)를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-122">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="44bfa-123">경로가 백슬래시("`\`")로 끝나지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-123">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="44bfa-124">UNC 경로는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-124">UNC paths are not supported.</span></span>

 <span data-ttu-id="44bfa-125">**-c** *config_file* 은 전처리 구성 파일의 전체 경로입니다. 다른 위치에 저장 된 경우 전처리 구성 파일의 위치를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-125">**-c** *config_file* Is the full path of the preprocess configuration file; used to specify the location of the preprocess configuration file when stored in a different location.</span></span> <span data-ttu-id="44bfa-126">이 매개 변수는 UNC 경로이거나 관리 도구를 실행하는 컴퓨터에 로컬로 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-126">This parameter can be a UNC path, or can reside locally on the computer where you run the administration tool.</span></span>

 <span data-ttu-id="44bfa-127">필터링이 필요 없거나 최대 유휴 시간을 수정하지 않으려는 경우에는 **-c** 매개 변수를 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-127">The **-c** parameter is not required if no filtering is needed, or if you do not want to modify the maximum idle time.</span></span>

 <span data-ttu-id="44bfa-128">**-c** 매개 변수를 지정하지 않을 경우 기본 전처리 구성 파일 `DReplay.exe.preprocess.config`가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-128">Without the **-c** parameter, the default preprocess configuration file, `DReplay.exe.preprocess.config`, is used.</span></span>

 <span data-ttu-id="44bfa-129">**-f** *status_interval* 상태 메시지를 표시할 빈도 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-129">**-f** *status_interval* Specifies the frequency (in seconds) at which to display status messages.</span></span>

 <span data-ttu-id="44bfa-130">**-f** 를 지정하지 않을 경우 기본 간격은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-130">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="44bfa-131">예</span><span class="sxs-lookup"><span data-stu-id="44bfa-131">Examples</span></span>
 <span data-ttu-id="44bfa-132">이 예에서는 모든 기본 설정을 사용하여 전처리 단계가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-132">In this example, the preprocess stage is initiated with all of the default settings.</span></span> <span data-ttu-id="44bfa-133">`localhost` 값은 컨트롤러 서비스가 관리 도구와 동일한 컴퓨터에서 실행 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-133">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span> <span data-ttu-id="44bfa-134">*input_trace_file* 매개 변수는 입력 추적 데이터 `c:\mytrace.trc`의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-134">The *input_trace_file* parameter specifies the location of the input trace data, `c:\mytrace.trc`.</span></span> <span data-ttu-id="44bfa-135">추적 파일 필터링은 사용되지 않으므로 **-c** 매개 변수는 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-135">Because there is no trace file filtering involved, the **-c** parameter does have to be specified.</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 <span data-ttu-id="44bfa-136">이 예에서는 전처리 단계가 시작되고 수정한 전처리 구성 파일이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-136">In this example, the preprocess stage is initiated and a modified preprocess configuration file is specified.</span></span> <span data-ttu-id="44bfa-137">위의 예와는 달리 수정한 구성 파일을 다른 위치에 저장한 경우 **-c** 매개 변수를 사용하여 해당 위치를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-137">Unlike the previous example, the **-c** parameter is used to point to the modified configuration file, if you have stored it in a different location.</span></span> <span data-ttu-id="44bfa-138">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-138">For example:</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 <span data-ttu-id="44bfa-139">수정한 전처리 구성 파일에는 분산 재생 중 시스템 세션을 필터링하는 필터 조건이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-139">In the modified preprocess configuration file, a filter condition is added that filters out system sessions during distributed replay.</span></span> <span data-ttu-id="44bfa-140">이 필터는 전처리 구성 파일 `<PreprocessModifiers>` 에서 `DReplay.exe.preprocess.config`요소를 수정하여 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-140">The filter is added by modifying the `<PreprocessModifiers>` element in the preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span>

 <span data-ttu-id="44bfa-141">다음은 수정된 구성 파일의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-141">The following shows an example of the modified configuration file:</span></span>

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="44bfa-142">사용 권한</span><span class="sxs-lookup"><span data-stu-id="44bfa-142">Permissions</span></span>
 <span data-ttu-id="44bfa-143">관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-143">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="44bfa-144">로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44bfa-144">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="44bfa-145">자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44bfa-145">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44bfa-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44bfa-146">See Also</span></span>
 <span data-ttu-id="44bfa-147">[Distributed Replay](sql-server-distributed-replay.md) [구성](configure-distributed-replay.md) SQL Server [입력 추적 데이터를 준비](prepare-the-input-trace-data.md) Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="44bfa-147">[Prepare the Input Trace Data](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md)</span></span>


