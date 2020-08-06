---
title: 데이터 흐름 구성 요소에서 로그 항목 로깅 및 정의 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14dfec71679bbe455ae8be5face98b776a80b9e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729640"
---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a><span data-ttu-id="6a13e-102">데이터 흐름 구성 요소에서 로그 항목 로깅 및 정의</span><span class="sxs-lookup"><span data-stu-id="6a13e-102">Logging and Defining Log Entries in a Data Flow Component</span></span>
  <span data-ttu-id="6a13e-103">사용자 지정 데이터 흐름 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> 인터페이스의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 메서드를 사용하여 기존 로그 항목에 메시지를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-103">Custom data flow components can post messages to an existing log entry by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="6a13e-104">또한 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> 메서드나 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스의 유사한 메서드를 사용하여 사용자에게 정보를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-104">They can also present information to the user by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> method or similar methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="6a13e-105">그러나 이 방법을 사용할 경우 추가 이벤트를 발생시키고 처리하는 오버헤드가 발생하며 사용자가 직접 관심 있는 메시지에 대한 자세한 정보 메시지를 조사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-105">However, this approach incurs the overhead of raising and handling additional events, and forces the user to sift through verbose informational messages for the messages that may be of interest to them.</span></span> <span data-ttu-id="6a13e-106">아래에서 설명하는 대로 사용자 지정 로그 항목을 사용하면 구성 요소 사용자에게 고유한 레이블이 지정된 사용자 지정 로그 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-106">You can use a custom log entry as described below to provide distinctly labeled custom log information to users of your component.</span></span>  
  
## <a name="registering-and-using-a-custom-log-entry"></a><span data-ttu-id="6a13e-107">사용자 지정 로그 항목 등록 및 사용</span><span class="sxs-lookup"><span data-stu-id="6a13e-107">Registering and Using a Custom Log Entry</span></span>  
  
### <a name="registering-a-custom-log-entry"></a><span data-ttu-id="6a13e-108">사용자 지정 로그 항목 등록</span><span class="sxs-lookup"><span data-stu-id="6a13e-108">Registering a Custom Log Entry</span></span>  
 <span data-ttu-id="6a13e-109">구성 요소에서 사용할 사용자 지정 로그 항목을 등록하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-109">To register a custom log entry for use by your component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="6a13e-110">다음 예에서는 사용자 지정 로그 항목을 등록하고 이름과 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-110">The following example registers a custom log entry and provides a name and description.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 <span data-ttu-id="6a13e-111"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> 열거형은 이벤트가 기록되는 빈도에 대한 힌트를 런타임에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> enumeration provides a hint to the runtime about how frequently the event will be logged:</span></span>  
  
-   <span data-ttu-id="6a13e-112"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: 이벤트가 실행 시마다 로깅되는 것이 아니라 가끔씩만 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-112"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: Event is logged only sometimes, not during every execution.</span></span>  
  
-   <span data-ttu-id="6a13e-113"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: 이벤트가 실행 시마다 일정 횟수만큼 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-113"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: Event is logged a constant number of times during every execution.</span></span>  
  
-   <span data-ttu-id="6a13e-114"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: 이벤트가 완료된 작업 양에 비례하여 여러 번 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-114"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: Event is logged a number of times proportional to the amount of work completed.</span></span>  
  
 <span data-ttu-id="6a13e-115">위의 예에서는 구성 요소가 실행 시마다 한 번씩 로그 항목을 로깅해야 하므로 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-115">The example above uses <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> because the component expects to log an entry once per execution.</span></span>  
  
 <span data-ttu-id="6a13e-116">사용자 지정 로그 항목을 등록하고 데이터 흐름 디자이너 화면에 사용자 지정 구성 요소의 인스턴스를 추가한 후에는 디자이너의 **로깅** 대화 상자에 있는 사용 가능한 로그 항목 목록에 "My Custom Component Log Entry"라는 이름의 새 로그 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-116">After registering the custom log entry and adding an instance of your custom component to the data flow designer surface, the **Logging** dialog box in the designer displays a new log entry with the name "My Custom Component Log Entry" in the list of available log entries.</span></span>  
  
### <a name="logging-to-a-custom-log-entry"></a><span data-ttu-id="6a13e-117">사용자 지정 로그 항목에 로깅</span><span class="sxs-lookup"><span data-stu-id="6a13e-117">Logging to a Custom Log Entry</span></span>  
 <span data-ttu-id="6a13e-118">사용자 지정 로그 항목을 등록한 후에는 구성 요소에서 사용자 지정 메시지를 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-118">After registering the custom log entry, the component can now log custom messages.</span></span> <span data-ttu-id="6a13e-119">다음 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 메서드 실행 중에 구성 요소에서 사용되는 SQL 문의 텍스트를 포함하는 사용자 지정 로그 항목을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-119">The example below writes a custom log entry during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method that contains the text of a SQL statement used by the component.</span></span>  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 <span data-ttu-id="6a13e-120">이제 사용자가 패키지를 실행하고 **로깅** 대화 상자에서 "My Custom Component Log Entry"를 선택하면 "User::My Custom Component Log Entry"라는 레이블이 지정된 항목이 로그에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-120">Now when the user executes the package, after selecting the "My Custom Component Log Entry" in the **Logging** dialog box, the log will contain an entry clearly labeled as "User::My Custom Component Log Entry."</span></span> <span data-ttu-id="6a13e-121">이 새 로그 항목에는 SQL 문, 타임스탬프 및 개발자가 로깅한 추가 데이터의 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a13e-121">This new log entry contains the text of the SQL statement, the timestamp, and any additional data logged by the developer.</span></span>  
  
<span data-ttu-id="6a13e-122">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6a13e-122">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6a13e-123">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6a13e-123">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6a13e-124">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6a13e-124">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6a13e-125">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6a13e-125">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a13e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a13e-126">See Also</span></span>  
 [<span data-ttu-id="6a13e-127">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="6a13e-127">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
