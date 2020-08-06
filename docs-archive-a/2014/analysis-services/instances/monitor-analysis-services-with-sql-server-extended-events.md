---
title: SQL Server 확장 이벤트 (Xevent)를 사용 하 여 Analysis Services 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d12d9bc8d6a56702e1b44f8404b25681a1033f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653033"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a><span data-ttu-id="9e62c-102">SQL Server 확장 이벤트(XEvent)를 사용하여 Analysis Services 모니터링</span><span class="sxs-lookup"><span data-stu-id="9e62c-102">Use SQL Server Extended Events (XEvents) to Monitor Analysis Services</span></span>
  <span data-ttu-id="9e62c-103">Analysis Services는 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)를 사용 하 여 추적 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-103">Analysis Services provides tracing capabilities through the usage of [Extended Events](../../relational-databases/extended-events/extended-events.md).</span></span>  
  
 <span data-ttu-id="9e62c-104">확장 이벤트는 서버 시스템에 대해 구성할 수 있는 확장성이 높은 이벤트 인프라입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-104">Extended Events is an event infrastructure that is highly scalable and configurable for server systems.</span></span> <span data-ttu-id="9e62c-105">확장 이벤트는 성능 리소스를 적게 사용하는 간단한 성능 모니터링 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-105">Extended Events is a light weight performance monitoring system that uses very few performance resources.</span></span>  
  
 <span data-ttu-id="9e62c-106">Xevent를 통해 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)에 정의 된 대로 모든 Analysis Services 이벤트를 캡처하고 특정 소비자를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-106">All Analysis Services events can be captured and target to specific consumers, as defined in [Extended Events](../../relational-databases/extended-events/extended-events.md), through XEvents.</span></span>  
  
## <a name="initiating-extended-events-in-analysis-services"></a><span data-ttu-id="9e62c-107">Analysis Services에서 확장 이벤트 시작</span><span class="sxs-lookup"><span data-stu-id="9e62c-107">Initiating Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="9e62c-108">확장 이벤트 추적은 다음과 같은 XMLA 개체 만들기 스크립트 명령을 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-108">Extended Event tracing is enabled using a similar XMLA create object script command as shown below:</span></span>  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="9e62c-109">여기에서 다음 요소는 추적 요구 사항에 따라 사용자가 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-109">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="9e62c-110">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="9e62c-110">*trace_id*</span></span>  
 <span data-ttu-id="9e62c-111">이 추적의 고유 식별자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-111">Defines the unique identifier for this trace.</span></span>  
  
 <span data-ttu-id="9e62c-112">*trace_name*</span><span class="sxs-lookup"><span data-stu-id="9e62c-112">*trace_name*</span></span>  
 <span data-ttu-id="9e62c-113">이 추적에 지정된 이름으로, 대개 사람이 읽을 수 있는 추적에 대한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-113">The name given to this trace; usually a human readable definition of the trace.</span></span> <span data-ttu-id="9e62c-114">*trace_id* 값을 이름으로 사용하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-114">It is a common practice to use the *trace_id* value as the name.</span></span>  
  
 <span data-ttu-id="9e62c-115">*AS_event*</span><span class="sxs-lookup"><span data-stu-id="9e62c-115">*AS_event*</span></span>  
 <span data-ttu-id="9e62c-116">노출할 Analysis Services 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-116">The Analysis Services event to be exposed.</span></span> <span data-ttu-id="9e62c-117">이벤트의 이름은 [Analysis Services 추적 이벤트](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e62c-117">See [Analysis Services Trace Events](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) for names of the events.</span></span>  
  
 <span data-ttu-id="9e62c-118">*data_filename*</span><span class="sxs-lookup"><span data-stu-id="9e62c-118">*data_filename*</span></span>  
 <span data-ttu-id="9e62c-119">이벤트 데이터가 포함된 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-119">The name of the file that contains the events data.</span></span> <span data-ttu-id="9e62c-120">추적을 반복적으로 보내는 경우 데이터를 덮어쓰지 않도록 이름 뒤에 타임스탬프가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-120">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
 <span data-ttu-id="9e62c-121">*metadata_filename*</span><span class="sxs-lookup"><span data-stu-id="9e62c-121">*metadata_filename*</span></span>  
 <span data-ttu-id="9e62c-122">이벤트 메타데이터가 포함된 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-122">The name of the file that contains the events metadata.</span></span> <span data-ttu-id="9e62c-123">추적을 반복적으로 보내는 경우 데이터를 덮어쓰지 않도록 이름 뒤에 타임스탬프가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-123">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
## <a name="stopping-extended-events-in-analysis-services"></a><span data-ttu-id="9e62c-124">Analysis Services에서 확장 이벤트 중지</span><span class="sxs-lookup"><span data-stu-id="9e62c-124">Stopping Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="9e62c-125">확장 이벤트 추적 개체를 중지하려면 다음과 같은 유사한 XMLA 개체 삭제 스크립트 명령을 사용하여 해당 개체를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-125">To stop the Extended Events tracing object you need to delete that object using a similar XMLA delete object script command as shown below:</span></span>  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="9e62c-126">여기에서 다음 요소는 추적 요구 사항에 따라 사용자가 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-126">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="9e62c-127">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="9e62c-127">*trace_id*</span></span>  
 <span data-ttu-id="9e62c-128">삭제할 추적의 고유 식별자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e62c-128">Defines the unique identifier for the trace to be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e62c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e62c-129">See Also</span></span>  
 [<span data-ttu-id="9e62c-130">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="9e62c-130">Extended Events</span></span>](../../relational-databases/extended-events/extended-events.md)  
  
  
