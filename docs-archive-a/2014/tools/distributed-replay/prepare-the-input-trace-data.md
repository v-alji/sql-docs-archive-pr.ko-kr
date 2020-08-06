---
title: 입력 추적 데이터 준비 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c14fd3d2-5770-47c2-a851-cc13ddbc9bf5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c13dddcf29f93940fa4eae6b2849dcfb278ae3b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734812"
---
# <a name="prepare-the-input-trace-data"></a><span data-ttu-id="a1ad2-102">입력 추적 데이터 준비</span><span class="sxs-lookup"><span data-stu-id="a1ad2-102">Prepare the Input Trace Data</span></span>
  <span data-ttu-id="a1ad2-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 기능을 사용하여 분산 재생을 시작하려면 Distributed Replay Administration Tool에서 전처리 단계를 시작하여 입력 추적 데이터를 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-103">Before you can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature, you must prepare the input trace data by initiating the preprocess stage from the distributed replay administration tool.</span></span> <span data-ttu-id="a1ad2-104">전처리 단계에서는 Distributed Replay Controller가 추적 데이터를 전처리하고 중간 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-104">In the preprocess stage, the distributed replay controller processes the trace data and generates an intermediate file:</span></span>  
  
 <span data-ttu-id="a1ad2-105">![Distributed Replay 전처리 단계](../../database-engine/media/preprocess.gif "Distributed Replay 전처리 단계")</span><span class="sxs-lookup"><span data-stu-id="a1ad2-105">![Distributed replay preprocess stage](../../database-engine/media/preprocess.gif "Distributed replay preprocess stage")</span></span>  
  
 <span data-ttu-id="a1ad2-106">전처리 단계에 대한 자세한 내용은 [SQL Server Distributed Replay](sql-server-distributed-replay.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-106">For more information about the preprocess stage, see [SQL Server Distributed Replay](sql-server-distributed-replay.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1ad2-107">Distributed Replay와 호환되는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전에서 입력 추적 데이터를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-107">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="a1ad2-108">또한 입력 추적 데이터가 추적 데이터를 재생할 대상 서버와 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-108">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="a1ad2-109">버전 요구 사항에 대한 자세한 내용은 [Distributed Replay Requirements](distributed-replay-requirements.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-109">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-prepare-the-input-trace-data"></a><span data-ttu-id="a1ad2-110">입력 추적 데이터를 준비하려면</span><span class="sxs-lookup"><span data-stu-id="a1ad2-110">To prepare the input trace data</span></span>  
  
1.  <span data-ttu-id="a1ad2-111">**(선택 사항) 전처리 구성 설정 수정**: 시스템 세션 필터링 여부 또는 최대 유휴 시간 구성 여부 등의 전처리 구성 설정을 수정하려면 XML 기반 전처리 구성 파일인 `DReplay.exe.preprocess.config`의 `<PreprocessModifiers>` 요소를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-111">**(Optional) Modify preprocess configuration settings**: If you want to modify the preprocess configuration settings, such as whether to filter system sessions or to configure the maximum idle time, you must modify the `<PreprocessModifiers>` element of the XML-based preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span> <span data-ttu-id="a1ad2-112">전처리 구성 파일을 수정하는 경우 원래 파일 대신 복사본을 수정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-112">If you modify the preprocess configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="a1ad2-113">설정을 수정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-113">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="a1ad2-114">기본 전처리 구성 파일인 `DReplay.exe.preprocess.config`를 복사한 후 복사한 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-114">Make a copy of the default preprocess configuration file, `DReplay.exe.preprocess.config`, and rename the new file.</span></span> <span data-ttu-id="a1ad2-115">기본 전처리 구성 파일은 관리 도구 설치 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-115">The default preprocess configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="a1ad2-116">새 구성 파일에서 전처리 구성 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-116">Modify the preprocess configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="a1ad2-117">전처리 단계(다음 단계)를 시작할 때 *preprocess* 옵션의 **config_file** 매개 변수를 사용하여 수정된 구성 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-117">When initiating the preprocess stage (the next step), use the *config_file* parameter of the **preprocess** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="a1ad2-118">전처리 구성 파일에 대한 자세한 내용은 [Distributed Replay 구성](configure-distributed-replay.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-118">For more information about the preprocess configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="a1ad2-119">**전처리 단계 시작**: 입력 추적 데이터를 준비하려면 **preprocess** 옵션을 사용하여 관리 도구를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-119">**Initiate the preprocess stage**: To prepare the input trace data, you must run the administration tool with the **preprocess** option.</span></span> <span data-ttu-id="a1ad2-120">자세한 내용은 [전처리 옵션&#40;Distributed Replay Administration Tool&#41;](preprocess-option-distributed-replay-administration-tool.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-120">For more information, see [Preprocess Option &#40;Distributed Replay Administration Tool&#41;](preprocess-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="a1ad2-121">Windows 명령 프롬프트 유틸리티(`CMD.exe`)를 열고 Distributed Replay Administration Tool의 설치 위치(`DReplay.exe`)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-121">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="a1ad2-122">(선택 사항) 컨트롤러 서비스가 관리 도구와 다른 컴퓨터에서 실행 중인 경우 *controller* 매개 변수 **-m**을 사용하여 컨트롤러를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-122">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="a1ad2-123">*input_trace_file* 매개 변수 **-i**를 사용하여 입력 추적 파일의 위치와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-123">Use the *input_trace_file* parameter, **-i**, to specify the location and name of the input trace files.</span></span>  
  
    4.  <span data-ttu-id="a1ad2-124">*controller_working_directory* 매개 변수 **-d**를 사용하여 컨트롤러에서 중간 파일을 저장할 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-124">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file should be saved on the controller.</span></span>  
  
    5.  <span data-ttu-id="a1ad2-125">(선택 사항) *config_file* 매개 변수 **-c**를 사용하여 전처리 구성 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-125">(Optional) Use the *config_file* parameter, **-c**, to specify location of the preprocess configuration file.</span></span> <span data-ttu-id="a1ad2-126">기본 전처리 구성 파일을 복사하고 복사본을 수정한 경우 이 매개 변수를 사용하여 새 구성 파일을 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-126">Use this parameter to point to the new configuration file if you have modified a copy of the default preprocess configuration file.</span></span>  
  
    6.  <span data-ttu-id="a1ad2-127">(선택 사항) *status_interval* 매개 변수 **-f**를 사용하여 관리 도구가 30초가 아닌 다른 빈도로 상태 메시지를 표시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-127">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency different than 30 seconds.</span></span>  
  
     <span data-ttu-id="a1ad2-128">예를 들어 컨트롤러 서비스와 동일한 컴퓨터에서 `c:\trace1.trc`에 있는 추적 파일 및 `c:\WorkingDir` 에 있는 컨트롤러 작업 디렉터리에 대해 전처리 단계를 시작하고 기본값인 30초 간격으로 상태 메시지가 표시되도록 하려면 `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span><span class="sxs-lookup"><span data-stu-id="a1ad2-128">For example, initiating the preprocess stage on the same computer as the controller service, for a trace file located at `c:\trace1.trc`, a controller working directory located at `c:\WorkingDir` , and a status message displayed at the default value of 30 seconds, requires the syntax: `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span></span>  
  
3.  <span data-ttu-id="a1ad2-129">전처리 단계가 완료되면 중간 파일이 컨트롤러 작업 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-129">After the preprocess stage is complete, the intermediate file is stored in the controller working directory.</span></span> <span data-ttu-id="a1ad2-130">이벤트 재생 단계를 시작하려면 **replay** 옵션을 사용하여 관리 도구를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-130">To initiate the event replay stage, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="a1ad2-131">자세한 내용은 [추적 데이터 재생](replay-trace-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ad2-131">For more information, see [Replay Trace Data](replay-trace-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ad2-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1ad2-132">See Also</span></span>  
 <span data-ttu-id="a1ad2-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="a1ad2-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="a1ad2-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="a1ad2-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="a1ad2-135">[관리 도구 명령줄 옵션&#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a1ad2-135">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="a1ad2-136">Distributed Replay 구성</span><span class="sxs-lookup"><span data-stu-id="a1ad2-136">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
