---
title: 프로그래밍 방식으로 데이터 흐름 태스크 추가 | Microsoft Docs
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
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f7e699cc8e88bafb2a4508fdac8560fa73befe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649645"
---
# <a name="adding-the-data-flow-task-programmatically"></a><span data-ttu-id="b77b2-102">프로그래밍 방식으로 데이터 흐름 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="b77b2-102">Adding the Data Flow Task Programmatically</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="b77b2-103">에는 개체 모델에서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> 네임스페이스로 표현되는 데이터 흐름 태스크라는 태스크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-103">includes a task called the Data Flow task, which is represented by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> namespace in the object model.</span></span> <span data-ttu-id="b77b2-104">데이터 흐름 태스크는 패키지 실행 도중 데이터를 변환하고 이동하는 데만 사용되는 특수한 고성능 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-104">The Data Flow task is a specialized, high-performance task, dedicated to transforming and moving data during package execution.</span></span> <span data-ttu-id="b77b2-105">다른 태스크와 마찬가지로 데이터 흐름 태스크도 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 개체에 의해 래핑되며, 런타임 엔진의 측면에서 이 태스크는 단지 패키지의 또 다른 태스크일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-105">Like other tasks, the Data Flow task is wrapped by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object, and from the perspective of the run-time engine, this task is just another task in the package.</span></span> <span data-ttu-id="b77b2-106">그러나 데이터 흐름에는 데이터 흐름 구성 요소라는 추가 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-106">However, the data flow contains additional objects called data flow components.</span></span> <span data-ttu-id="b77b2-107">이러한 구성 요소는 데이터를 원본에서 대상으로 이동하게 하고 때로는 변환을 통해 이동하게 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-107">These components are the components that make data move from a source to a destination, sometimes through a transformation.</span></span> <span data-ttu-id="b77b2-108">이 구성 요소는 이동 방향과 데이터 변환 방식을 모두 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-108">The components define both the direction of movement and how data is transformed.</span></span> <span data-ttu-id="b77b2-109">데이터 흐름 태스크를 구성하려면 태스크에 구성 요소를 추가한 다음 이들 구성 요소를 연결하여 데이터의 흐름을 구성하고 의도한 변환을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-109">Configuring the Data Flow task involves adding components to the task, and then connecting them to establish the flow of data and achieve the intended transformation.</span></span>  
  
 <span data-ttu-id="b77b2-110">데이터 흐름 태스크 내에는 3가지 유형의 구성 요소가 있습니다. **데이터 흐름 원본**, **데이터 흐름 변환** 및 **데이터 흐름 대상**이 이에 해당하며 이러한 구성 요소는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너 도구 상자에 이 순서대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-110">There are three types of components within a Data Flow task: **Data Flow Sources**, **Data Flow Transformations**, and **Data Flow Destinations**, shown in that order within the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer toolbox.</span></span> <span data-ttu-id="b77b2-111">이러한 유형을 보다 간단히 원본, 변환 또는 대상이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-111">These types are also referred to more simply as sources, transformations, or destinations.</span></span> <span data-ttu-id="b77b2-112">이름이 나타내듯이 데이터는 원본에서 변환을 거쳐 대상으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-112">As implied by the names, data flows from a source to a transformation, and then to a destination.</span></span> <span data-ttu-id="b77b2-113">이는 개념을 보여 주기 위해 데이터 흐름을 극단적으로 단순화한 것이지만 데이터 흐름 태스크는 여러 원본을 처리하고 출력을 여러 대상으로 보내는 많은 변환을 서로 연결할 만큼 융통성 있고 강력합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-113">This is a simplistic description of the data flow to illustrate the concept, but the Data Flow task is flexible and powerful enough to handle multiple sources, and to connect together many transformations that send output to multiple destinations.</span></span>  
  
 <span data-ttu-id="b77b2-114">데이터 흐름 태스크는 다른 태스크가 추가되는 방식과 동일한 방식으로 패키지에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-114">The Data Flow task is added to a package the same way other tasks are added.</span></span> <span data-ttu-id="b77b2-115">태스크를 추가한 후에는 데이터 흐름 태스크에 구성 요소를 추가하고 태스크의 구성 요소를 구성 및 연결하여 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-115">After the task has been added, it is configured by adding components to the data flow task, and configuring and connecting components in the task.</span></span>  
  
## <a name="sample"></a><span data-ttu-id="b77b2-116">샘플</span><span class="sxs-lookup"><span data-stu-id="b77b2-116">Sample</span></span>  
 <span data-ttu-id="b77b2-117">다음 코드 예제에서는 패키지에 데이터 흐름 태스크를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-117">The following code sample shows how to add a Data Flow task to a package.</span></span> <span data-ttu-id="b77b2-118">이 예에는 Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap 및 Microsoft.SqlServer.ManagedDTS 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b77b2-118">This example requires a reference to the assemblies Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap, and Microsoft.SqlServer.ManagedDTS.</span></span>  
  
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
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="b77b2-119">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="b77b2-119">External Resources</span></span>  
 <span data-ttu-id="b77b2-120">blogs.msdn.com의 블로그 항목 - [EzAPI – SQL Server 2012용으로 업데이트됨](https://go.microsoft.com/fwlink/?LinkId=243223)</span><span class="sxs-lookup"><span data-stu-id="b77b2-120">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="b77b2-121">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b77b2-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b77b2-122">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b77b2-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b77b2-123">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b77b2-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b77b2-124">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="b77b2-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77b2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b77b2-125">See Also</span></span>  
 [<span data-ttu-id="b77b2-126">프로그래밍 방식으로 데이터 흐름 구성 요소 검색</span><span class="sxs-lookup"><span data-stu-id="b77b2-126">Discovering Data Flow Components Programmatically</span></span>](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
