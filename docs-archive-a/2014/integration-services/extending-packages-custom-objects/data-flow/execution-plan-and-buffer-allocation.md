---
title: 실행 계획 및 버퍼 할당 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], buffer allocations
- custom data flow components [Integration Services], execution plans
- buffer allocations [Integration Services]
- data flow components [Integration Services], buffer allocations
- data flow components [Integration Services], execution plans
- execution plans [Integration Services]
ms.assetid: 679d9ff0-641e-47c3-abb8-d1a7dcb279dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03b8bb22988ccf77f8920252ac2d600478c92f3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729667"
---
# <a name="execution-plan-and-buffer-allocation"></a><span data-ttu-id="27bf2-102">실행 계획 및 버퍼 할당</span><span class="sxs-lookup"><span data-stu-id="27bf2-102">Execution Plan and Buffer Allocation</span></span>
  <span data-ttu-id="27bf2-103">실행 전에 데이터 흐름 태스크에서는 구성 요소를 검사하고 각 구성 요소 시퀀스에 대한 실행 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-103">Before execution, the data flow task examines its components and generates an execution plan for each sequence of components.</span></span> <span data-ttu-id="27bf2-104">이 섹션에서는 실행 계획, 실행 계획을 보는 방법 및 실행 계획에 따라 입력 및 출력 버퍼가 할당되는 방식에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-104">This section provides details about the execution plan, how to view the plan, and how input and output buffers are allocated based on the execution plan.</span></span>  
  
## <a name="understanding-the-execution-plan"></a><span data-ttu-id="27bf2-105">실행 계획 이해</span><span class="sxs-lookup"><span data-stu-id="27bf2-105">Understanding the Execution Plan</span></span>  
 <span data-ttu-id="27bf2-106">실행 계획에는 원본 스레드와 작업 스레드가 포함되며 각 스레드에는 원본 스레드에 대한 출력 작업 목록이나 작업 스레드에 대한 입력 및 출력 작업 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-106">An execution plan contains source threads and work threads, and each thread contains work lists that specify output work lists for source threads or input and output work lists for work threads.</span></span> <span data-ttu-id="27bf2-107">실행 계획의 원본 스레드는 데이터 흐름의 원본 구성 요소를 나타내며 실행 계획에서 *SourceThread\*\*n*으로 식별됩니다. 여기서 *n*은 0부터 시작하는 원본 스레드 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-107">The source threads in an execution plan represent the source components in the data flow and are identified in the execution plan by *SourceThread\*\*n*, where *n* is the zero-based number of the source thread.</span></span>  
  
 <span data-ttu-id="27bf2-108">각 원본 스레드에서는 버퍼를 만들고, 수신기를 설정하고, 원본 구성 요소에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-108">Each source thread creates a buffer, sets a listener, and calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method on the source component.</span></span> <span data-ttu-id="27bf2-109">이 지점에서 원본 구성 요소는 데이터 흐름 태스크에서 해당 구성 요소에 제공한 출력 버퍼에 행을 추가하기 시작하므로 이 지점이 실행이 시작되고 데이터가 시작되는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-109">This is where execution starts and data originates, as the source component starts adding rows to the output buffers that are provided to it by the data flow task.</span></span> <span data-ttu-id="27bf2-110">원본 스레드가 실행된 후 잔여 작업은 여러 작업 스레드 간에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-110">After the source threads are running, the balance of work is distributed among work threads.</span></span>  
  
 <span data-ttu-id="27bf2-111">작업 스레드는 입력 및 출력 작업 목록을 모두 포함할 수 있으며 실행 계획에서 *WorkThread\*\*n*으로 식별됩니다. 여기서 *n*은 0부터 시작하는 작업 스레드 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-111">A work thread may contain both input and output work lists and is identified in the execution plan as *WorkThread\*\*n*, where *n* is the zero-based number of the work thread.</span></span> <span data-ttu-id="27bf2-112">그래프에 비동기 출력을 사용하는 구성 요소가 포함된 경우 이러한 스레드에는 출력 작업 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-112">These threads contain output work lists when the graph contains a component with asynchronous outputs.</span></span>  
  
 <span data-ttu-id="27bf2-113">다음 예제 실행 계획이 나타내는 데이터 흐름에서는 원본 구성 요소가 비동기 출력을 사용하는 변환에 연결되어 있고 이 변환은 대상 구성 요소에 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-113">The following sample execution plan represents a data flow that contains a source component connected to a transformation with an asynchronous output connected to a destination component.</span></span> <span data-ttu-id="27bf2-114">이 예에서 변환 구성 요소에는 비동기 출력이 있으므로 WorkThread0에는 출력 작업 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-114">In this example, WorkThread0 contains an output work list because the transformation component has an asynchronous output.</span></span>  
  
```  
SourceThread0   
    Influences: 72 158   
    Output Work List   
        CreatePrimeBuffer of type 1 for output id 10   
        SetBufferListener: "WorkThread0" for input ID 73   
        CallPrimeOutput on component "OLE DB Source" (1)   
    End Output Work List   
    This thread drives 0 distributors   
End SourceThread0   
WorkThread0   
    Influences: 72 158   
    Input Work list, input ID 73   
        CallProcessInput on input ID 73 on component "Sort" (72) for view type 2   
    End Input Work list for input 73   
    Output Work List   
        CreatePrimeBuffer of type 3 for output id 74   
        SetBufferListener: "WorkThread1" for input ID 171with internal handoff   
        CallPrimeOutput on component "Sort" (72)   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread0   
WorkThread1   
    Influences: 158   
    Input Work list, input ID 171  
        CallProcessInput on input ID 171 on component "OLE DB Destination" (158) for view type 4  
    End Input Work list for input 171   
    Output Work List   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="27bf2-115">실행 계획은 패키지가 실행될 때마다 생성되며, 패키지에 로그 공급자를 추가하고 로깅을 사용하도록 설정한 다음 **PipelineExecutionPlan** 이벤트를 선택하면 실행 계획을 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-115">The execution plan is generated every time a package is executed, and can be captured by adding a log provider to the package, enabling logging, and selecting the **PipelineExecutionPlan** event.</span></span>  
  
## <a name="understanding-buffer-allocation"></a><span data-ttu-id="27bf2-116">버퍼 할당 이해</span><span class="sxs-lookup"><span data-stu-id="27bf2-116">Understanding Buffer Allocation</span></span>  
 <span data-ttu-id="27bf2-117">실행 계획에 따라 데이터 흐름 태스크에서는 데이터 흐름 구성 요소의 출력에 정의된 열을 포함하는 버퍼를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-117">Based on the execution plan, the data flow task creates buffers that contain the columns defined in the outputs of the data flow components.</span></span> <span data-ttu-id="27bf2-118">이 버퍼는 비동기 출력을 사용하는 구성 요소가 나타날 때까지 구성 요소의 시퀀스를 통해 데이터 흐름으로 재사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-118">The buffer is reused as the data flows through the sequence of components, until a component with asynchronous outputs is encountered.</span></span> <span data-ttu-id="27bf2-119">그런 다음 비동기 출력의 출력 열과 다운 스트림 구성 요소의 출력 열을 포함하는 새 버퍼가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-119">Then, a new buffer is created, which contains the output columns of the asynchronous output and the output columns of downstream components.</span></span>  
  
 <span data-ttu-id="27bf2-120">실행 중 구성 요소에서는 현재 원본 또는 작업 스레드의 버퍼에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-120">During execution, components have access to the buffer in the current source or work thread.</span></span> <span data-ttu-id="27bf2-121">이 버퍼는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드에 의해 제공된 입력 버퍼이거나 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드에 의해 제공된 출력 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-121">The buffer is either an input buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, or an output buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="27bf2-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 속성도 각 버퍼를 입력 또는 출력 버퍼로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> also identifies each buffer as an input or output buffer.</span></span>  
  
 <span data-ttu-id="27bf2-123">비동기 출력을 사용하는 변환은 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드에서 기존 입력 버퍼를 받고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드에서 새 출력 버퍼를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-123">Transformation components with asynchronous outputs receive the existing input buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, and receive the new output buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="27bf2-124">비동기 출력을 사용하는 구성 요소는 데이터 흐름에서 입력 버퍼와 출력 버퍼를 모두 받는 유일한 유형의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-124">A transformation component with asynchronous outputs is the only type of data flow component that receives both an input and an output buffer.</span></span>  
  
 <span data-ttu-id="27bf2-125">구성 요소에 제공된 버퍼에는 구성 요소의 입력 또는 출력 열 컬렉션에 있는 것보다 많은 열이 포함될 수 있으므로 구성 요소 개발자는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 메서드를 호출하고 `LineageID`를 지정하여 버퍼에서 열을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27bf2-125">Because the buffer provided to a component is likely to contain more columns than the component has in its input or output column collections, component developers can call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method to locate a column in the buffer by specifying its `LineageID`.</span></span>  
  
<span data-ttu-id="27bf2-126">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="27bf2-126">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="27bf2-127">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="27bf2-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="27bf2-128">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="27bf2-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="27bf2-129">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="27bf2-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
