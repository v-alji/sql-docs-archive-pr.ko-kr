---
title: 사용자 지정 Foreach 열거자 만들기 | Microsoft Docs
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
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d99970d466aa53d25a80f0600f1fce7819e94956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648449"
---
# <a name="creating-a-custom-foreach-enumerator"></a><span data-ttu-id="ef276-102">사용자 지정 Foreach 열거자 만들기</span><span class="sxs-lookup"><span data-stu-id="ef276-102">Creating a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="ef276-103">사용자 지정 foreach 열거자를 만드는 단계는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 다른 사용자 지정 개체를 만드는 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-103">The steps involved in creating a custom foreach enumerator are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="ef276-104">기본 클래스에서 상속되는 새 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="ef276-105">foreach 열거자의 경우 기본 클래스는 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>입니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-105">For a foreach enumerator, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.</span></span>  
  
-   <span data-ttu-id="ef276-106">개체 유형을 식별하는 특성을 클래스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="ef276-107">foreach 열거자의 경우 이 특성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>입니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-107">For a foreach enumerator, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
-   <span data-ttu-id="ef276-108">기본 클래스의 메서드 및 속성 구현을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="ef276-109">foreach 열거자의 경우 가장 중요한 항목은 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-109">For a foreach enumerator, the most important is the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
-   <span data-ttu-id="ef276-110">필요한 경우 사용자 지정 사용자 인터페이스를 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="ef276-111">foreach 열거자의 경우 사용자 지정 사용자 인터페이스를 개발하려면 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> 인터페이스를 구현하는 클래스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-111">For a foreach enumerator, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> interface.</span></span>  
  
 <span data-ttu-id="ef276-112">사용자 지정 열거자는 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 컨테이너에 의해 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-112">A custom enumerator is hosted by the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container.</span></span> <span data-ttu-id="ef276-113">런타임에 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 컨테이너는 사용자 지정 열거자의 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-113">At run time, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="ef276-114">사용자 지정 열거자는 `IEnumerable`와 같이 `ArrayList` 인터페이스를 구현하는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-114">The custom enumerator returns an object that implements the `IEnumerable` interface, such as an `ArrayList`.</span></span> <span data-ttu-id="ef276-115">그런 다음 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>는 컬렉션의 각 요소를 반복하고, 사용자 정의 변수를 통해 현재 요소의 값을 제어 흐름에 제공하고, 컨테이너에서 제어 흐름을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates over each element in the collection, provides the value of the current element to the control flow through a user-defined variable, and executes the control flow in the container.</span></span>  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a><span data-ttu-id="ef276-116">사용자 지정 ForEach 열거자 시작</span><span class="sxs-lookup"><span data-stu-id="ef276-116">Getting Started with a Custom ForEach Enumerator</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="ef276-117">프로젝트 및 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef276-117">Creating Projects and Classes</span></span>  
 <span data-ttu-id="ef276-118">관리되는 foreach 열거자는 모두 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 기본 클래스에서 파생되므로 사용자 지정 foreach 열거자를 만들려면 먼저 관리되는 프로그래밍 언어로 클래스 라이브러리 프로젝트를 만들고 기본 클래스에서 상속되는 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-118">Because all managed foreach enumerators derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, the first step when you create a custom foreach enumerator is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="ef276-119">이 파생 클래스에서 기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-119">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="ef276-120">동일한 솔루션에서 사용자 지정 사용자 인터페이스에 대한 두 번째 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-120">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="ef276-121">배포를 쉽게 하려면 사용자 인터페이스에 대한 별도의 어셈블리를 만드는 것이 좋습니다. 이렇게 하면 foreach 열거자 또는 해당 사용자 인터페이스를 독립적으로 업데이트하거나 다시 배포할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-121">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the foreach enumerator or its user interface independently.</span></span>  
  
 <span data-ttu-id="ef276-122">강력한 이름 키 파일을 사용하여 빌드 시 생성될 어셈블리에 서명하도록 두 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-122">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a><span data-ttu-id="ef276-123">DtsForEachEnumerator 특성 적용</span><span class="sxs-lookup"><span data-stu-id="ef276-123">Applying the DtsForEachEnumerator Attribute</span></span>  
 <span data-ttu-id="ef276-124">앞에서 만든 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 특성을 적용하여 해당 클래스를 foreach 열거자로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-124">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class that you have created to identify it as a foreach enumerator.</span></span> <span data-ttu-id="ef276-125">이 특성은 foreach 열거자의 이름 및 설명 같은 디자인 타임 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-125">This attribute provides design-time information such as the name and description of the foreach enumerator.</span></span> <span data-ttu-id="ef276-126">`Name`속성은 **Foreach 루프 편집기** 대화 상자의 **컬렉션** 탭에서 사용 가능한 열거자의 드롭다운 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-126">The `Name` property appears in the dropdown list of available enumerators on the **Collection** tab of the **Foreach Loop Editor** dialog box.</span></span>  
  
 <span data-ttu-id="ef276-127"><xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 속성을 사용하여 foreach 열거자를 사용자 지정 사용자 인터페이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property to link the foreach enumerator to its custom user interface.</span></span> <span data-ttu-id="ef276-128">이 속성에 필요한 공개 키 토큰을 가져오려면 **sn.exe -t**를 사용하여 사용자 인터페이스 어셈블리 서명에 사용할 키 쌍(.snk) 파일의 공개 키 토큰을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-128">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a><span data-ttu-id="ef276-129">사용자 지정 열거자 빌드, 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="ef276-129">Building, Deploying, and Debugging a Custom Enumerator</span></span>  
 <span data-ttu-id="ef276-130">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 사용자 지정 foreach 열거자의 빌드, 배포 및 디버깅 단계는 다른 형식의 사용자 지정 개체에 대해 필요한 단계와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ef276-130">The steps for building, deploying, and debugging a custom foreach enumerator in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="ef276-131">자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef276-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="ef276-132">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ef276-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ef276-133">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="ef276-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ef276-134">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="ef276-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ef276-135">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="ef276-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef276-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef276-136">See Also</span></span>  
 <span data-ttu-id="ef276-137">[사용자 지정 Foreach 열거자 코딩](coding-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="ef276-137">[Coding a Custom Foreach Enumerator](coding-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="ef276-138">사용자 지정 ForEach 열거자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="ef276-138">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
