---
title: 사용자 지정 데이터 흐름 구성 요소 만들기 | Microsoft Docs
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
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 110d07ff88707ad1a01f299b6f532df99ce58404
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652226"
---
# <a name="creating-a-custom-data-flow-component"></a><span data-ttu-id="6e5fc-102">사용자 지정 데이터 흐름 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="6e5fc-102">Creating a Custom Data Flow Component</span></span>
  <span data-ttu-id="6e5fc-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 데이터 흐름 태스크는 개발자가 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]와 관리형 코드를 사용하여 사용자 지정 데이터 흐름의 원본, 변환 및 대상 구성 요소를 만들 수 있게 해 주는 개체 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the data flow task exposes an object model that lets developers create custom data flow components-sources, transformations, and destinations-by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] and managed code.</span></span>  
  
 <span data-ttu-id="6e5fc-104">데이터 흐름 태스크는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 포함하는 구성 요소와 구성 요소 간의 데이터 이동을 정의하는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체의 컬렉션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-104">A data flow task consists of components that contain an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface and a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects that define the movement of data between components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e5fc-105">사용자 지정 공급자를 만들 경우 ProviderDescriptors.xml 파일을 메타데이터 열 값으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-105">When you create a custom provider, you need to update the ProviderDescriptors.xml file with the metadata column values.</span></span>  
  
## <a name="design-time-and-run-time"></a><span data-ttu-id="6e5fc-106">디자인 타임 및 런타임</span><span class="sxs-lookup"><span data-stu-id="6e5fc-106">Design Time and Run Time</span></span>  
 <span data-ttu-id="6e5fc-107">실행 전 데이터 흐름 태스크에서 증분 변경 작업이 수행될 때 해당 데이터 흐름 태스크는 디자인 타임 상태에 있다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-107">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="6e5fc-108">변경 작업에는 구성 요소의 추가 또는 제거, 구성 요소를 연결하는 경로 개체의 추가 또는 제거, 구성 요소의 메타데이터 변경 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-108">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="6e5fc-109">메타데이터가 변경되면 구성 요소에서는 변경 내용을 모니터링하고 그에 따라 반응할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-109">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="6e5fc-110">예를 들어 변경에 대한 응답으로 구성 요소에서는 특정 변경 작업을 허용하지 않거나 추가 변경 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-110">For example, a component can disallow certain changes or to make additional changes in response to a change.</span></span> <span data-ttu-id="6e5fc-111">디자인 타임에 디자이너는 디자인 타임 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 인터페이스를 통해 구성 요소와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-111">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="6e5fc-112">실행 시 데이터 흐름 태스크에서는 구성 요소의 시퀀스를 검사하고, 실행 계획을 준비하고, 작업 계획을 실행하는 작업자 스레드의 풀을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-112">At execution time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="6e5fc-113">각 작업자 스레드는 데이터 흐름 태스크 내부의 일부 작업을 수행하지만 작업자 스레드의 주요 태스크는 런타임 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 인터페이스를 통해 구성 요소의 메서드를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-113">Although each worker thread performs some work that is internal to the data flow task, the principal task of the worker thread is to call the methods of the component through the run-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interface.</span></span>  
  
## <a name="creating-a-component"></a><span data-ttu-id="6e5fc-114">구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="6e5fc-114">Creating a Component</span></span>  
 <span data-ttu-id="6e5fc-115">데이터 흐름 구성 요소를 만들려면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스에서 클래스를 파생시키고 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 클래스를 적용한 다음 기본 클래스의 적절한 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-115">To create a data flow component, you derive a class from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class, apply the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class, and then override the appropriate methods of the base class.</span></span> <span data-ttu-id="6e5fc-116"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 인터페이스를 구현하고 구성 요소에서 재정의할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interfaces, and exposes their methods for you to override in your component.</span></span>  
  
 <span data-ttu-id="6e5fc-117">프로젝트에는 구성 요소에서 사용되는 개체에 따라 다음 어셈블리 중 일부 또는 모두에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-117">Depending on the objects used by your component, your project will require references to some or all of the following assemblies:</span></span>  
  
|<span data-ttu-id="6e5fc-118">기능</span><span class="sxs-lookup"><span data-stu-id="6e5fc-118">Feature</span></span>|<span data-ttu-id="6e5fc-119">참조할 어셈블리</span><span class="sxs-lookup"><span data-stu-id="6e5fc-119">Assembly to reference</span></span>|<span data-ttu-id="6e5fc-120">가져올 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="6e5fc-120">Namespace to import</span></span>|  
|-------------|---------------------------|-------------------------|  
|<span data-ttu-id="6e5fc-121">디자이너의</span><span class="sxs-lookup"><span data-stu-id="6e5fc-121">Data flow</span></span>|<span data-ttu-id="6e5fc-122">Microsoft.SqlServer.PipelineHost</span><span class="sxs-lookup"><span data-stu-id="6e5fc-122">Microsoft.SqlServer.PipelineHost</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|<span data-ttu-id="6e5fc-123">데이터 흐름 래퍼</span><span class="sxs-lookup"><span data-stu-id="6e5fc-123">Data flow wrapper</span></span>|<span data-ttu-id="6e5fc-124">Microsoft.SqlServer.DTSPipelineWrap</span><span class="sxs-lookup"><span data-stu-id="6e5fc-124">Microsoft.SqlServer.DTSPipelineWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|<span data-ttu-id="6e5fc-125">런타임</span><span class="sxs-lookup"><span data-stu-id="6e5fc-125">Runtime</span></span>|<span data-ttu-id="6e5fc-126">Microsoft.SQLServer.ManagedDTS</span><span class="sxs-lookup"><span data-stu-id="6e5fc-126">Microsoft.SQLServer.ManagedDTS</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|<span data-ttu-id="6e5fc-127">런타임 래퍼</span><span class="sxs-lookup"><span data-stu-id="6e5fc-127">Runtime wrapper</span></span>|<span data-ttu-id="6e5fc-128">Microsoft.SqlServer.DTSRuntimeWrap</span><span class="sxs-lookup"><span data-stu-id="6e5fc-128">Microsoft.SqlServer.DTSRuntimeWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 <span data-ttu-id="6e5fc-129">다음 코드 예에서는 기본 클래스에서 파생되는 간단한 구성 요소를 보여 주고 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-129">The following code example shows a simple component that derives from the base class, and applies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="6e5fc-130">DTSPipelineWrap 어셈블리에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-130">You need to add a reference to the DTSPipelineWrap assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
<span data-ttu-id="6e5fc-131">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6e5fc-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6e5fc-132">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6e5fc-133">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6e5fc-134">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5fc-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5fc-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e5fc-135">See Also</span></span>  
 [<span data-ttu-id="6e5fc-136">데이터 흐름 구성 요소의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="6e5fc-136">Developing a User Interface for a Data Flow Component</span></span>](developing-a-user-interface-for-a-data-flow-component.md)  
  
  
