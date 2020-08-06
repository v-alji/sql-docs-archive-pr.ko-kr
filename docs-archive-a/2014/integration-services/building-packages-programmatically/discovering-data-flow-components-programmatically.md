---
title: 프로그래밍 방식으로 데이터 흐름 구성 요소 검색 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a18102f38f1ad06e918efe2ca529185d40deef9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731972"
---
# <a name="discovering-data-flow-components-programmatically"></a><span data-ttu-id="c7d78-102">프로그래밍 방식으로 데이터 흐름 구성 요소 검색</span><span class="sxs-lookup"><span data-stu-id="c7d78-102">Discovering Data Flow Components Programmatically</span></span>
  <span data-ttu-id="c7d78-103">패키지에 데이터 흐름 태스크를 추가한 후 사용할 수 있는 데이터 흐름 구성 요소를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-103">After you have added a data flow task to a package, your next step may be to determine what data flow components are available for your use.</span></span> <span data-ttu-id="c7d78-104">로컬 컴퓨터에 설치되어 있고 사용 가능한 데이터 흐름 원본, 변환 및 대상을 프로그래밍 방식으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-104">You can programmatically discover the data flow sources, transformations, and destinations that are installed and available on the local computer.</span></span> <span data-ttu-id="c7d78-105">패키지에 데이터 흐름 태스크 추가에 대한 자세한 내용은 [프로그래밍 방식으로 데이터 흐름 태스크 추가](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d78-105">For information about adding a data flow task to the package, see [Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).</span></span>  
  
## <a name="discovering-components"></a><span data-ttu-id="c7d78-106">구성 요소 검색</span><span class="sxs-lookup"><span data-stu-id="c7d78-106">Discovering Components</span></span>  
 <span data-ttu-id="c7d78-107"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스에서는 로컬 컴퓨터에 올바르게 설치된 각 구성 요소에 대한 <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> 개체가 들어 있는 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 컬렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-107">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class provides the <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> collection, which contains a <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> object for each component correctly installed on the local computer.</span></span> <span data-ttu-id="c7d78-108">각 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo>에는 구성 요소 이름, 설명 및 생성 이름과 같이 구성 요소에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-108">Each <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contains information about a component such as its name, description, and creation name.</span></span> <span data-ttu-id="c7d78-109">패키지에 구성 요소를 추가할 때 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 속성에서 반환된 값을 사용하여 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-109">You can use the value returned in the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property to set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> when you add a component to a package.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="c7d78-110">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c7d78-110">Next Step</span></span>  
 <span data-ttu-id="c7d78-111">사용 가능한 구성 요소를 검색한 후에는 다음의 [프로그래밍 방식으로 데이터 흐름 구성 요소 추가](../building-packages-programmatically/adding-data-flow-components-programmatically.md) 항목에 설명된 대로 구성 요소를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-111">After discovering available components, the next step is to add and configure the components, which is discussed in the next topic, [Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="c7d78-112">샘플</span><span class="sxs-lookup"><span data-stu-id="c7d78-112">Sample</span></span>  
 <span data-ttu-id="c7d78-113">다음 코드 예제에서는 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 컬렉션을 열거하여 로컬 컴퓨터에서 사용할 수 있는 데이터 흐름 구성 요소를 프로그래밍 방식으로 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-113">The following code sample shows how to enumerate the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object to programmatically discover the data flow components available on the local computer.</span></span> <span data-ttu-id="c7d78-114">이 샘플에는 Microsoft.SqlServer.ManagedDTS 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d78-114">This sample requires a reference to the Microsoft.SqlServer.ManagedDTS assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="c7d78-115">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c7d78-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c7d78-116">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d78-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c7d78-117">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d78-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c7d78-118">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d78-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d78-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7d78-119">See Also</span></span>  
 [<span data-ttu-id="c7d78-120">프로그래밍 방식으로 데이터 흐름 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="c7d78-120">Adding Data Flow Components Programmatically</span></span>](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
