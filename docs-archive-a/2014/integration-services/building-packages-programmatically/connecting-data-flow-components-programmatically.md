---
title: 프로그래밍 방식으로 데이터 흐름 구성 요소 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39494fee5314f309b79abfd30303fdd607fd3c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649641"
---
# <a name="connecting-data-flow-components-programmatically"></a><span data-ttu-id="303c4-102">프로그래밍 방식으로 데이터 흐름 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="303c4-102">Connecting Data Flow Components Programmatically</span></span>
  <span data-ttu-id="303c4-103">데이터 흐름 태스크에 구성 요소를 추가한 후 해당 구성 요소를 연결하여 원본에서 변환을 거쳐 대상으로 이동하는 데이터 흐름을 나타내는 실행 트리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-103">After you have added components to the data flow task, you connect them to create an execution tree that represents the flow of data from sources through transformations to destinations.</span></span> <span data-ttu-id="303c4-104">데이터 흐름의 구성 요소를 연결하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-104">You use <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects to connect the components in the data flow.</span></span>  
  
## <a name="creating-a-path"></a><span data-ttu-id="303c4-105">경로 만들기</span><span class="sxs-lookup"><span data-stu-id="303c4-105">Creating a Path</span></span>  
 <span data-ttu-id="303c4-106"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> 인터페이스에 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> 속성의 새 메서드를 호출하여 새 경로를 만들고 이 경로를 데이터 흐름 태스크의 경로 컬렉션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-106">Call the New method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> interface to create a new path and add it to the collection of paths in the data flow task.</span></span> <span data-ttu-id="303c4-107">이 메서드는 연결이 끊어진 새 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체를 반환합니다. 그러면 이 개체를 사용하여 두 구성 요소를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-107">This method returns a new, disconnected <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, which you then use to connect two components.</span></span>  
  
 <span data-ttu-id="303c4-108">경로를 연결하고 연결된 경로에 참여하는 구성 요소에 해당 구성 요소가 연결되었음을 알리려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> method to connect the path and to notify the components participating in the path that they have been connected.</span></span> <span data-ttu-id="303c4-109">이 메서드는 업스트림 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>과 다운스트림 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>을 매개 변수로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-109">This method accepts an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the upstream component and an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> of the downstream component as parameters.</span></span> <span data-ttu-id="303c4-110">기본적으로 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 메서드를 호출하면 입력이 있는 구성 요소에 대한 단일 입력과 출력이 있는 구성 요소에 대한 단일 출력이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-110">By default, the call to the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method creates a single input for components that have inputs, and a single output for components that have outputs.</span></span> <span data-ttu-id="303c4-111">다음 예에서는 원본의 이 기본 출력과 대상의 입력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-111">The following example uses this default output of the source and input of the destination.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="303c4-112">다음 단계</span><span class="sxs-lookup"><span data-stu-id="303c4-112">Next Step</span></span>  
 <span data-ttu-id="303c4-113">두 구성 요소 간의 경로를 설정한 다음에는 다운스트림 구성 요소의 입력 열을 매핑해야 합니다. 이 단계에 대한 자세한 내용은 다음에 나오는 [프로그래밍 방식으로 입력 열 선택](../building-packages-programmatically/selecting-input-columns-programmatically.md) 항목에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-113">After you establish a path between two components, the next step is to map input columns in the downstream component, which is discussed in the next topic, [Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="303c4-114">샘플</span><span class="sxs-lookup"><span data-stu-id="303c4-114">Sample</span></span>  
 <span data-ttu-id="303c4-115">다음 코드 예제에서는 두 구성 요소 간의 경로를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="303c4-115">The following code sample shows how to establish a path between two components.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 <span data-ttu-id="303c4-116">}</span><span class="sxs-lookup"><span data-stu-id="303c4-116">}</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="303c4-117">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="303c4-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="303c4-118">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="303c4-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="303c4-119">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="303c4-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="303c4-120">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="303c4-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303c4-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="303c4-121">See Also</span></span>  
 [<span data-ttu-id="303c4-122">프로그래밍 방식으로 입력 열 선택</span><span class="sxs-lookup"><span data-stu-id="303c4-122">Selecting Input Columns Programmatically</span></span>](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  
