---
title: 프로그래밍 방식으로 로깅 설정 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff7f81aca330960e4e94b0343080a37ded8c1273
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731976"
---
# <a name="enabling-logging-programmatically"></a><span data-ttu-id="9474c-102">프로그래밍 방식으로 로깅 설정</span><span class="sxs-lookup"><span data-stu-id="9474c-102">Enabling Logging Programmatically</span></span>
  <span data-ttu-id="9474c-103">런타임 엔진에서는 패키지의 유효성 검사 및 실행 중에 이벤트 관련 정보를 캡처하는 데 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 개체의 컬렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-103">The run-time engine provides a collection of <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects that enable event-specific information to be captured during package validation and execution.</span></span> <span data-ttu-id="9474c-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 개체는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer>, <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop> 개체를 비롯하여 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 개체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects are available to <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> objects, including the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package>, <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>, and <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> objects.</span></span> <span data-ttu-id="9474c-105">개별 컨테이너나 패키지 전체에 대해 로깅 기능을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-105">Logging is enabled on individual containers, or on the whole package.</span></span>

 <span data-ttu-id="9474c-106">컨테이너에서 사용할 수 있는 로그 공급자에는 여러 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-106">There are several types of log providers that are available for a container to use.</span></span> <span data-ttu-id="9474c-107">따라서 여러 형식으로 로그 정보를 만들고 저장할 수 있는 유연성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-107">This provides the flexibility to create and store log information in many formats.</span></span> <span data-ttu-id="9474c-108">컨테이너 개체를 로깅에 참여시키는 과정은 먼저 로깅을 활성화한 후 로그 공급자를 선택하는 두 단계로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-108">Enlisting a container object in logging is a two-step process: first logging is enabled, and then a log provider is selected.</span></span> <span data-ttu-id="9474c-109">컨테이너의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 속성은 로깅되는 이벤트를 지정하고 로그 공급자를 선택하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-109">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> properties of the container are used to specify the logged events and to select the log provider.</span></span>

## <a name="enabling-logging"></a><span data-ttu-id="9474c-110">로깅 설정</span><span class="sxs-lookup"><span data-stu-id="9474c-110">Enabling Logging</span></span>
 <span data-ttu-id="9474c-111">로깅을 수행할 수 있는 각 컨테이너에 있는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 속성은 컨테이너의 이벤트 정보를 이벤트 로그에 기록할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-111">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property, found in each container that can perform logging, determines whether the container's event information is recorded to the event log.</span></span> <span data-ttu-id="9474c-112">이 속성은 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 구조의 값을 할당받으며 기본적으로 컨테이너의 부모에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-112">This property is assigned a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> structure, and is inherited from the container's parent by default.</span></span> <span data-ttu-id="9474c-113">컨테이너가 패키지라서 부모가 없는 경우 이 속성은 기본값이 `Disabled`인 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-113">If the container is a package, and therefore has no parent, the property uses the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>, which defaults to `Disabled`.</span></span>

### <a name="selecting-a-log-provider"></a><span data-ttu-id="9474c-114">로그 공급자 선택</span><span class="sxs-lookup"><span data-stu-id="9474c-114">Selecting a Log Provider</span></span>
 <span data-ttu-id="9474c-115"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 속성이 `Enabled`로 설정되면 컨테이너의 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 컬렉션에 로그 공급자가 추가되면서 프로세스가 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-115">After the <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property is set to `Enabled`, a log provider is added to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection of the container to complete the process.</span></span> <span data-ttu-id="9474c-116"><xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 컬렉션은 <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> 개체에서 사용할 수 있으며 컨테이너에 대해 선택된 로그 공급자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-116">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection is available on the <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> object, and contains the log providers selected for the container.</span></span> <span data-ttu-id="9474c-117"><xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> 메서드는 공급자를 만들어 컬렉션에 추가하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-117">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> method is called to create a provider and add it to the collection.</span></span> <span data-ttu-id="9474c-118">그런 다음 이 메서드는 컬렉션에 추가된 로그 공급자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-118">The method then returns the log provider that was added to the collection.</span></span> <span data-ttu-id="9474c-119">각 공급자에는 해당 공급자에 고유한 구성 설정이 있으며 이러한 속성은 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 속성을 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-119">Each provider has configuration settings that are unique to that provider, and these properties are set using the <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> property.</span></span>

 <span data-ttu-id="9474c-120">다음 표에는 사용할 수 있는 로그 공급자, 해당 설명 및 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 정보가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-120">The following table lists the available log providers, their description, and their <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> information.</span></span>

|<span data-ttu-id="9474c-121">공급자</span><span class="sxs-lookup"><span data-stu-id="9474c-121">Provider</span></span>|<span data-ttu-id="9474c-122">Description</span><span class="sxs-lookup"><span data-stu-id="9474c-122">Description</span></span>|<span data-ttu-id="9474c-123">ConfigString 속성</span><span class="sxs-lookup"><span data-stu-id="9474c-123">ConfigString property</span></span>|
|--------------|-----------------|---------------------------|
|<span data-ttu-id="9474c-124">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="9474c-124">SQL Server Profiler</span></span>|<span data-ttu-id="9474c-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로파일러에서 캡처하고 볼 수 있는 SQL 추적을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-125">Generates SQL traces that may be captured and viewed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span> <span data-ttu-id="9474c-126">이 공급자의 기본 파일 이름 확장명은 .trc입니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-126">The default file name extension for this provider is .trc.</span></span>|<span data-ttu-id="9474c-127">구성이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-127">No configuration is required.</span></span>|
|<span data-ttu-id="9474c-128">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9474c-128">SQL Server</span></span>|<span data-ttu-id="9474c-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 **sysssislog** 테이블에 이벤트 로그 항목을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-129">Writes event log entries to the **sysssislog** table in any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9474c-130">공급자를 사용하려면 데이터베이스에 대한 연결과 대상 데이터베이스 이름이 지정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-130">provider requires that the connection to the database be specified, and also the target database name.</span></span>|
|<span data-ttu-id="9474c-131">텍스트 파일</span><span class="sxs-lookup"><span data-stu-id="9474c-131">Text File</span></span>|<span data-ttu-id="9474c-132">이벤트 로그 항목을 CSV(쉼표로 구분된 값) 형식으로 ASCII 텍스트 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-132">Writes event log entries to ASCII text files in a comma-separated value (CSV) format.</span></span> <span data-ttu-id="9474c-133">이 공급자의 기본 파일 이름 확장명은 .log입니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-133">The default file name extension for this provider is .log.</span></span>|<span data-ttu-id="9474c-134">파일 연결 관리자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-134">The name of a file connection manager.</span></span>|
|<span data-ttu-id="9474c-135">Windows 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="9474c-135">Windows Event Log</span></span>|<span data-ttu-id="9474c-136">로컬 컴퓨터의 애플리케이션 로그에 있는 표준 Windows 이벤트 로그에 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-136">Logs to standard Windows Event Log on the local computer in the Application log.</span></span>|<span data-ttu-id="9474c-137">구성이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-137">No configuration is required.</span></span>|
|<span data-ttu-id="9474c-138">XML 파일</span><span class="sxs-lookup"><span data-stu-id="9474c-138">XML File</span></span>|<span data-ttu-id="9474c-139">이벤트 로그 항목을 XML 형식의 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-139">Writes event log entries to XML formatted file.</span></span> <span data-ttu-id="9474c-140">이 공급자의 기본 파일 이름 확장명은 .xml입니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-140">The default file name extension for this provider is .xml</span></span>|<span data-ttu-id="9474c-141">파일 연결 관리자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-141">The name of a file connection manager.</span></span>|

 <span data-ttu-id="9474c-142">컨테이너의 `EventFilterKind` 및 `EventFilter` 속성을 설정하여 이벤트를 이벤트 로그에 포함하거나 이벤트 로그에서 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-142">Events are included in or excluded from the event log by setting the `EventFilterKind` and the `EventFilter` properties of the container.</span></span> <span data-ttu-id="9474c-143">`EventFilterKind` 구조에는 `ExclusionFilter`에 추가된 이벤트가 이벤트 로그에 포함되는지 여부를 나타내는 `InclusionFilter` 및 `EventFilter` 값이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-143">The `EventFilterKind` structure contains two values, `ExclusionFilter` and `InclusionFilter`, that indicate whether the events that are added to the `EventFilter` are included in the event log.</span></span> <span data-ttu-id="9474c-144">`EventFilter` 속성에는 필터링 제목에 해당하는 이벤트 이름이 들어 있는 문자열 배열이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-144">The `EventFilter` property is then assigned a string array that contains the names of the events that are the subject of the filtering.</span></span>

 <span data-ttu-id="9474c-145">다음 코드에서는 패키지에 로깅 기능을 사용하도록 설정하고, <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 컬렉션에 텍스트 파일에 대한 로그 공급자를 추가하고, 로깅 출력에 포함할 이벤트 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9474c-145">The following code enables logging on a package, adds the log provider for Text files to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection, and specifies a list of events to include in the logging output.</span></span>

## <a name="sample"></a><span data-ttu-id="9474c-146">샘플</span><span class="sxs-lookup"><span data-stu-id="9474c-146">Sample</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package p = new Package();

      ConnectionManager loggingConnection = p.Connections.Add("FILE");
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";

      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");
      provider.ConfigString = loggingConnection.Name;
      p.LoggingOptions.SelectedLogProviders.Add(provider);
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute", 
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };
      p.LoggingMode = DTSLoggingMode.Enabled;

      // Add tasks and other objects to the package.

    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim p As Package = New Package()

    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"

    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")
    provider.ConfigString = loggingConnection.Name
    p.LoggingOptions.SelectedLogProviders.Add(provider)
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}
    p.LoggingMode = DTSLoggingMode.Enabled

    ' Add tasks and other objects to the package.

  End Sub

End Module
```

<span data-ttu-id="9474c-147">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9474c-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9474c-148">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9474c-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9474c-149">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9474c-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9474c-150">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="9474c-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9474c-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9474c-151">See Also</span></span>
 [<span data-ttu-id="9474c-152">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="9474c-152">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)


