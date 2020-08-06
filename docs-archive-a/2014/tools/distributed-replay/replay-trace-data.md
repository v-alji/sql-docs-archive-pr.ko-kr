---
title: 추적 데이터 재생 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 19ff5285-fb9d-4fd1-97c4-ec72c311c384
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6c929d7c617ba4dc496eedabaccbbe50da32d08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646789"
---
# <a name="replay-trace-data"></a><span data-ttu-id="ce18d-102">추적 데이터 재생</span><span class="sxs-lookup"><span data-stu-id="ce18d-102">Replay Trace Data</span></span>
  <span data-ttu-id="ce18d-103">입력 추적 데이터를 준비한 후 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 기능을 사용하여 분산 재생을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-103">You can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature after you have prepared the input trace data.</span></span> <span data-ttu-id="ce18d-104">자세한 내용은 [입력 추적 데이터 준비](prepare-the-input-trace-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce18d-104">For more information, see [Prepare the Input Trace Data](prepare-the-input-trace-data.md).</span></span>  
  
 <span data-ttu-id="ce18d-105">관리 도구 **replay** 옵션을 사용하여 Distributed Replay의 이벤트 재생 단계를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-105">Use the administration tool **replay** option to initiate the event replay stage of the distributed replay.</span></span> <span data-ttu-id="ce18d-106">이 단계는 추적 데이터 디스패치와 분산 재생 시작 및 동기화의 두 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-106">This stage consists of two parts: the trace data dispatch and the starting and synchronizing of the distributed replay.</span></span>  
  
 <span data-ttu-id="ce18d-107">![Distributed 이벤트 재생](../../database-engine/media/eventreplay.gif "Distributed 이벤트 재생")</span><span class="sxs-lookup"><span data-stu-id="ce18d-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span></span>  
  
 <span data-ttu-id="ce18d-108">추적 데이터는 두 가지 시퀀스 모드(스트레스 모드 또는 동기화 모드) 중 하나로 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-108">You can replay trace data in one of two sequencing modes: stress mode or synchronization mode.</span></span> <span data-ttu-id="ce18d-109">기본 동작은 스트레스 모드로 추적 데이터를 재생하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-109">The default behavior is to replay trace data in stress mode.</span></span> <span data-ttu-id="ce18d-110">이벤트 재생 단계 및 시퀀스 모드에 대한 자세한 내용은 [SQL Server Distributed Replay](sql-server-distributed-replay.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce18d-110">For more information about the event replay stage and sequencing modes, see [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce18d-111">Distributed Replay와 호환되는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전에서 입력 추적 데이터를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-111">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="ce18d-112">또한 입력 추적 데이터가 추적 데이터를 재생할 대상 서버와 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-112">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="ce18d-113">버전 요구 사항에 대한 자세한 내용은 [Distributed Replay Requirements](distributed-replay-requirements.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce18d-113">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-replay-the-trace"></a><span data-ttu-id="ce18d-114">추적을 재생하려면</span><span class="sxs-lookup"><span data-stu-id="ce18d-114">To replay the trace</span></span>  
  
1.  <span data-ttu-id="ce18d-115">**(선택 사항) 재생 구성 설정 수정:** : 시퀀스 모드 및 다양한 비율 값 등 재생 구성 설정을 수정하려면 XML 기반 재생 구성 파일인 `DReplay.exe.replay.config`의 `<ReplayOptions>` 요소를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-115">**(Optional) Modify replay configuration settings**: If you want to modify the replay configuration settings, such as the sequencing mode and various scaling values, you must modify the `<ReplayOptions>` element of the XML-based replay configuration file `DReplay.exe.replay.config`.</span></span> <span data-ttu-id="ce18d-116">`<OutputOptions>` 요소를 수정하여 행 수를 기록할지 여부 등의 출력 설정을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-116">You can also modify the `<OutputOptions>` element to specify output settings, such as whether to record the row count.</span></span> <span data-ttu-id="ce18d-117">재생 구성 파일을 수정하는 경우 원래 파일 대신 복사본을 수정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-117">If you modify the replay configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="ce18d-118">설정을 수정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-118">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ce18d-119">기본 재생 구성 파일인 `DReplay.exe.replay.config`를 복사한 후 복사한 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-119">Make a copy of the default replay configuration file, `DReplay.exe.replay.config`, and rename the new file.</span></span> <span data-ttu-id="ce18d-120">기본 재생 구성 파일은 관리 도구 설치 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-120">The default replay configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="ce18d-121">새 구성 파일에서 재생 구성 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-121">Modify the replay configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="ce18d-122">이벤트 재생 단계(다음 단계)를 시작할 때 *replay* 옵션의 **config_file** 매개 변수를 사용하여 수정한 구성 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-122">When initiating the event replay stage (the next step), use the *config_file* parameter of the **replay** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="ce18d-123">재생 구성 파일에 대한 자세한 내용은 [Distributed Replay 구성](configure-distributed-replay.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce18d-123">For more information about the replay configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="ce18d-124">**이벤트 재생 단계 시작**: 분산 재생을 시작하려면 **replay** 옵션을 사용하여 관리 도구를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-124">**Initiate the event replay stage**: To start the distributed replay, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="ce18d-125">자세한 내용은 [재생 옵션&#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce18d-125">For more information, see [Replay Option &#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="ce18d-126">Windows 명령 프롬프트 유틸리티(`CMD.exe`)를 열고 Distributed Replay Administration Tool의 설치 위치(`DReplay.exe`)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-126">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="ce18d-127">(선택 사항) 컨트롤러 서비스가 관리 도구와 다른 컴퓨터에서 실행 중인 경우 *controller* 매개 변수 **-m**을 사용하여 컨트롤러를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-127">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="ce18d-128">*controller_working_directory* 매개 변수 **-d**를 사용하여 전처리 단계 동안 컨트롤러에서 중간 파일이 저장되는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-128">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file was saved on the controller during the preprocess stage.</span></span>  
  
    4.  <span data-ttu-id="ce18d-129">(선택 사항) **-o** 매개 변수를 사용하여 각 클라이언트에서 결과 추적 파일의 재생 활동을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-129">(Optional) Use the **-o** parameter to capture the replay activity in a result trace file on each client.</span></span>  
  
    5.  <span data-ttu-id="ce18d-130">(선택 사항) *target_server* 매개 변수 **-s**를 사용하여 Distributed Replay 클라이언트가 추적 작업을 재생할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-130">(Optional) Use the *target_server* parameter, **-s**, to specify the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where the distributed replay clients should replay the trace workload.</span></span> <span data-ttu-id="ce18d-131">재생 구성 파일의 `<Server>` 요소에서 `<ReplayOptions>` 요소를 사용하여 대상 서버를 지정한 경우에는 이 매개 변수가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-131">This parameter is not required if you used the `<Server>` element to specify the target server in the `<ReplayOptions>` element of the replay configuration file.</span></span>  
  
    6.  <span data-ttu-id="ce18d-132">재생에 참가할 Distributed Replay 클라이언트를 지정하려면 *clients* 매개 변수 **-w**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-132">Use the *clients* parameter, **-w**, to specify the distributed replay clients that should participate in the replay.</span></span> <span data-ttu-id="ce18d-133">클라이언트 컴퓨터 이름은 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-133">List the client computer names, separated by commas.</span></span> <span data-ttu-id="ce18d-134">참고: IP 주소는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-134">Note: IP addresses are not allowed.</span></span>  
  
    7.  <span data-ttu-id="ce18d-135">(선택 사항) *config_file* 매개 변수 **-c**를 사용하여 재생 구성 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-135">(Optional) Use the *config_file* parameter, **-c**, to specify location of the replay configuration file.</span></span> <span data-ttu-id="ce18d-136">기본 재생 구성 파일의 복사본을 수정한 경우 이 매개 변수를 사용하여 새 구성 파일을 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-136">Use this parameter to point to the new configuration file if you have modified a copy of the default replay configuration file.</span></span>  
  
    8.  <span data-ttu-id="ce18d-137">(선택 사항) *status_interval* 매개 변수 **-f**를 사용하여 관리 도구가 30초가 아닌 다른 빈도로 상태 메시지를 표시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-137">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency other than 30 seconds.</span></span>  
  
     <span data-ttu-id="ce18d-138">예를 들어 다음 구문은 컨트롤러 서비스와 같은 컴퓨터에서 재생 단계를 시작하고, `c:\WorkingDir`에 있는 컨트롤러 작업 디렉터리를 사용하고, 참가하는 각 클라이언트의 재생 활동을 캡처하고, 클라이언트 `client1` 및 `client2` 를 사용하여 재생을 수행하고, `c:\modifiedreplay.config`에 있는 수정된 재생 구성 파일에서 나머지 재생 구성 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-138">For example, the following syntax initiates the replay stage on the same computer as the controller service, uses a controller working directory located at `c:\WorkingDir`, captures the replay activity on each participating client, uses clients `client1` and `client2` to perform the replay, and obtains the remaining replay configuration settings from a modified replay configuration file located at `c:\modifiedreplay.config`:</span></span>  
  
     `dreplay replay -d c:\WorkingDir -o -w client1,client2 -c c:\modifiedreplay.config`  
  
3.  <span data-ttu-id="ce18d-139">분산 재생이 완료되면 관리 도구에서 요약 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-139">When the distributed replay has finished, the administration tool returns summary information.</span></span> <span data-ttu-id="ce18d-140">**-o** 옵션을 지정한 경우 재생 활동이 각 클라이언트의 결과 추적 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce18d-140">If you specified the **-o** option, the replay activity has been saved in result trace files on each client.</span></span> <span data-ttu-id="ce18d-141">결과 추적 파일에 대한 자세한 내용은 [재생 결과 검토](review-the-replay-results.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce18d-141">For more information about the result trace files, see [Review the Replay Results](review-the-replay-results.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce18d-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce18d-142">See Also</span></span>  
 <span data-ttu-id="ce18d-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="ce18d-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="ce18d-144">[관리 도구 명령줄 옵션&#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ce18d-144">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="ce18d-145">Distributed Replay 구성</span><span class="sxs-lookup"><span data-stu-id="ce18d-145">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
