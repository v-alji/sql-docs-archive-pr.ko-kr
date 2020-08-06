---
title: 추적 속성 (일반 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30de30c88db35a41f8f118b6545d56a78b2dec79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741216"
---
# <a name="trace-properties-general-tab"></a><span data-ttu-id="acde8-102">추적 속성(일반 탭)</span><span class="sxs-lookup"><span data-stu-id="acde8-102">Trace Properties (General Tab)</span></span>
  <span data-ttu-id="acde8-103">**추적 속성** 대화 상자의 **일반** 탭을 사용하여 추적의 속성을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-103">Use the **General** tab of the **Trace Properties** dialog box to view or specify properties of a trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="acde8-104">옵션</span><span class="sxs-lookup"><span data-stu-id="acde8-104">Options</span></span>  
 <span data-ttu-id="acde8-105">**추적 이름**</span><span class="sxs-lookup"><span data-stu-id="acde8-105">**Trace name**</span></span>  
 <span data-ttu-id="acde8-106">추적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-106">Specify the name of the trace.</span></span>  
  
 <span data-ttu-id="acde8-107">**추적 공급자 이름**</span><span class="sxs-lookup"><span data-stu-id="acde8-107">**Trace provider name**</span></span>  
 <span data-ttu-id="acde8-108">추적되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-108">Shows the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that will be traced.</span></span> <span data-ttu-id="acde8-109">이 필드에는 연결할 때 지정한 서버의 이름이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-109">This field is populated automatically with the name of the server that you specified when you connected.</span></span> <span data-ttu-id="acde8-110">추적 공급자의 이름을 변경하려면 **취소** 를 클릭하여 대화 상자를 닫은 다음 새 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-110">To change the name of the trace provider, click **Cancel** to close the dialog box, and start a new trace.</span></span>  
  
 <span data-ttu-id="acde8-111">**추적 공급자 유형**</span><span class="sxs-lookup"><span data-stu-id="acde8-111">**Trace provider type**</span></span>  
 <span data-ttu-id="acde8-112">추적을 제공하는 서버 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-112">Shows the server type that is providing the trace.</span></span> <span data-ttu-id="acde8-113">**추적 공급자 유형** 필드는 추적 정의 파일에 의해 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-113">The trace definition file populates the **Trace provider type** field automatically.</span></span> <span data-ttu-id="acde8-114">이 필드는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-114">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="acde8-115">**version**</span><span class="sxs-lookup"><span data-stu-id="acde8-115">**version**</span></span>  
 <span data-ttu-id="acde8-116">추적을 제공하는 서버 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-116">Shows the version of the server that is providing the trace.</span></span> <span data-ttu-id="acde8-117">**버전** 필드는 추적 정의 파일에 의해 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-117">The trace definition file populates the **Version** field automatically.</span></span> <span data-ttu-id="acde8-118">이 필드는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-118">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="acde8-119">**템플릿 사용**</span><span class="sxs-lookup"><span data-stu-id="acde8-119">**Use the template**</span></span>  
 <span data-ttu-id="acde8-120">템플릿 디렉터리에서 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-120">Select a template from the template directory.</span></span> <span data-ttu-id="acde8-121">이 디렉터리에는 기본 템플릿 및 현재 추적 공급자 유형을 위해 만들어진 사용자 정의 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-121">The directory is populated with the default templates and any user-defined templates created for the current trace provider type.</span></span>  
  
 <span data-ttu-id="acde8-122">**파일에 저장**</span><span class="sxs-lookup"><span data-stu-id="acde8-122">**Save to file**</span></span>  
 <span data-ttu-id="acde8-123">추적 데이터를 .trc 파일에 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-123">Capture the trace data to a .trc file.</span></span> <span data-ttu-id="acde8-124">추적 데이터를 저장하면 나중에 검토 및 분석 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-124">Saving trace data is useful for later review and analysis.</span></span>  
  
 <span data-ttu-id="acde8-125">**최대 파일 크기 설정(MB)**</span><span class="sxs-lookup"><span data-stu-id="acde8-125">**Set maximum file size (MB)**</span></span>  
 <span data-ttu-id="acde8-126">추적 데이터를 파일에 저장하려면 추적 파일의 최대 크기를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-126">If you choose to save the trace data to a file, you must specify the maximum size of the trace file.</span></span> <span data-ttu-id="acde8-127">기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-127">The default is 5 megabytes (MB).</span></span> <span data-ttu-id="acde8-128">최대 크기는 파일이 저장된 파일 시스템이 NTFS인지 FAT인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-128">The maximum size is limited only by the file system (NTFS, FAT) where the file is saved.</span></span>  
  
 <span data-ttu-id="acde8-129">\<Graphic>**다른 이름으로 저장**</span><span class="sxs-lookup"><span data-stu-id="acde8-129">\<Graphic> **Save As**</span></span>  
 <span data-ttu-id="acde8-130">파일을 저장하려고 선택한 후에는 이 아이콘을 선택하여 파일 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-130">After you have selected to save, you can select this icon to change the file name.</span></span>  
  
 <span data-ttu-id="acde8-131">**파일 롤오버 사용**</span><span class="sxs-lookup"><span data-stu-id="acde8-131">**Enable file rollover**</span></span>  
 <span data-ttu-id="acde8-132">최대 파일 크기에 도달했을 때 추적 데이터를 보관할 추가 파일을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-132">Select to enable the creation of additional files to accept the trace data when the maximum file size is reached.</span></span> <span data-ttu-id="acde8-133">각각의 새 파일 이름에는 원래의 .trc 파일 이름 뒤에 순서대로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-133">Each new file name consists of the original .trc file name, numbered sequentially.</span></span> <span data-ttu-id="acde8-134">예를 들어 최대 파일 크기에 도달하면 **NewTrace.trc** 가 닫히고 **NewTrace_1.trc**, **NewTrace_2.trc**등의 새 파일이 순서대로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-134">For example, once it reaches maximum file size, **NewTrace.trc** closes, and a new file, **NewTrace_1.trc**, opens, followed by **NewTrace_2.trc**, and so on.</span></span> <span data-ttu-id="acde8-135">추적 내용을 파일에 저장하면 파일 롤오버 옵션이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-135">File rollover is enabled by default when you save a trace to a file.</span></span>  
  
 <span data-ttu-id="acde8-136">**서버에서 추적 데이터 처리**</span><span class="sxs-lookup"><span data-stu-id="acde8-136">**Server processes trace data**</span></span>  
 <span data-ttu-id="acde8-137">추적을 실행하는 서버가 추적 데이터를 처리하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-137">Specify that the server running the trace should process the trace data.</span></span> <span data-ttu-id="acde8-138">이 옵션을 사용하면 추적으로 인해 발생하는 성능 오버헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-138">Using this option reduces the performance overhead incurred by tracing.</span></span> <span data-ttu-id="acde8-139">이 확인란을 선택하면 스트레스 상태에서도 모든 이벤트가 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-139">If selected, no events are skipped even under stress conditions.</span></span> <span data-ttu-id="acde8-140">이 확인란의 선택을 취소하면 SQL Server 프로파일러가 처리를 수행하게 되고 스트레스 상태에서 몇몇 이벤트는 추적되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-140">If this check box is cleared, processing is performed by SQL Server Profiler, and there is a possibility that some events are not traced under stress conditions.</span></span>  
  
 <span data-ttu-id="acde8-141">**테이블에 저장**</span><span class="sxs-lookup"><span data-stu-id="acde8-141">**Save to table**</span></span>  
 <span data-ttu-id="acde8-142">추적 데이터를 데이터베이스 테이블에 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-142">Capture the trace data to a database table.</span></span> <span data-ttu-id="acde8-143">추적 데이터를 저장하면 나중에 검토 및 분석 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-143">Saving trace data is useful for later review and analysis.</span></span> <span data-ttu-id="acde8-144">추적 데이터를 테이블에 저장하면 추적이 저장될 서버에 상당한 오버헤드가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-144">However, saving trace data to a table can incur significant overhead on the server where the trace is being saved.</span></span> <span data-ttu-id="acde8-145">가능하면 추적되는 서버에 추적 테이블을 저장하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-145">If possible, do not save the trace table on the same server that is being traced.</span></span>  
  
 <span data-ttu-id="acde8-146">\<Graphic>**대상 테이블**</span><span class="sxs-lookup"><span data-stu-id="acde8-146">\<Graphic> **Destination Table**</span></span>  
 <span data-ttu-id="acde8-147">추적 데이터를 데이터베이스 테이블에 저장하도록 선택한 후에는 이 아이콘을 선택하여 테이블 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-147">After you have selected to save the trace data to a database table, you can select this icon to change the table name.</span></span>  
  
 <span data-ttu-id="acde8-148">**최대 행 수 설정(천 단위)**</span><span class="sxs-lookup"><span data-stu-id="acde8-148">**Set maximum rows (in thousands)**</span></span>  
 <span data-ttu-id="acde8-149">데이터를 저장할 행의 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-149">Specify the largest number of rows in which to save data.</span></span> <span data-ttu-id="acde8-150">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-150">The default is 1000 rows.</span></span>  
  
 <span data-ttu-id="acde8-151">**추적 중지 시간 설정**</span><span class="sxs-lookup"><span data-stu-id="acde8-151">**Enable trace stop time**</span></span>  
 <span data-ttu-id="acde8-152">추적을 끝내고 닫을 날짜와 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="acde8-152">Set the date and time for the trace to end and close itself.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acde8-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acde8-153">See Also</span></span>  
 [<span data-ttu-id="acde8-154">추적 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="acde8-154">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
