---
title: 사용자 지정 로그 공급자 만들기 | Microsoft Docs
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
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1efb736aece2cc8d118c81326989559f0d17a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732740"
---
# <a name="creating-a-custom-log-provider"></a><span data-ttu-id="07ff4-102">사용자 지정 로그 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ff4-102">Creating a Custom Log Provider</span></span>
  <span data-ttu-id="07ff4-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임 환경에는 광범위한 로깅 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time environment has extensive logging capabilities.</span></span> <span data-ttu-id="07ff4-104">로그를 사용하면 패키지를 실행하는 동안 발생하는 이벤트를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-104">A log lets you capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="07ff4-105">에는 XML, 텍스트, 데이터베이스, Windows 이벤트 로그 등의 다양한 형식으로 로그를 만들고 저장하는 데 사용할 수 있는 다양한 로그 공급자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-105">includes a variety of log providers that enable logs to be created and stored in multiple formats, such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="07ff4-106">이러한 공급자 또는 출력 형식이 요구 사항에 맞지 않을 경우에는 사용자 지정 로그 공급자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-106">If one of these providers or output formats does not fit your needs, you can create a custom log provider.</span></span>

 <span data-ttu-id="07ff4-107">사용자 지정 로그 공급자를 만드는 단계는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 다른 사용자 지정 개체를 만드는 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-107">The steps involved in creating a custom log provider are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>

-   <span data-ttu-id="07ff4-108">기본 클래스에서 상속되는 새 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-108">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="07ff4-109">로그 공급자의 경우 기본 클래스는 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>입니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-109">For a log provider, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.</span></span>

-   <span data-ttu-id="07ff4-110">개체 유형을 식별하는 특성을 클래스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-110">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="07ff4-111">로그 공급자의 경우 이 특성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>입니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-111">For a log provider, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.</span></span>

-   <span data-ttu-id="07ff4-112">기본 클래스의 메서드 및 속성 구현을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-112">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="07ff4-113">로그 공급자의 경우 이러한 구현에는 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 속성과 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-113">For a log provider, these include the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods.</span></span>

-   <span data-ttu-id="07ff4-114">사용자 지정 로그 공급자의 사용자 지정 사용자 인터페이스는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 구현되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-114">Custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="getting-started-with-a-custom-log-provider"></a><span data-ttu-id="07ff4-115">사용자 지정 로그 공급자 시작</span><span class="sxs-lookup"><span data-stu-id="07ff4-115">Getting Started with a Custom Log Provider</span></span>

### <a name="creating-projects-and-classes"></a><span data-ttu-id="07ff4-116">프로젝트 및 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="07ff4-116">Creating Projects and Classes</span></span>
 <span data-ttu-id="07ff4-117">관리되는 로그 공급자는 모두 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 기본 클래스에서 파생되므로 사용자 지정 로그 공급자를 만들려면 먼저 관리되는 프로그래밍 언어로 클래스 라이브러리 프로젝트를 만든 다음 기본 클래스에서 상속되는 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-117">Because all managed log providers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, the first step when you create a custom log provider is to create a class library project in your preferred managed programming language, and then create a class that inherits from the base class.</span></span> <span data-ttu-id="07ff4-118">이 파생 클래스에서 기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-118">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>

 <span data-ttu-id="07ff4-119">생성할 어셈블리를 강력한 이름 키 파일을 사용하여 서명하도록 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-119">Configure the project to sign the assembly that will be generated with a strong name key file.</span></span>

> [!NOTE]
>  <span data-ttu-id="07ff4-120">대부분의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 로그 공급자에는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>를 구현하며 **SSIS 로그 구성** 대화 상자의 **구성** 텍스트 상자를 사용 가능한 연결 관리자의 필터링된 드롭다운 목록으로 바꾸는 사용자 지정 사용자 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-120">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="07ff4-121">그러나 사용자 지정 로그 공급자의 사용자 지정 사용자 인터페이스는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 구현되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-121">However custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

### <a name="applying-the-dtslogprovider-attribute"></a><span data-ttu-id="07ff4-122">DtsLogProvider 특성 적용</span><span class="sxs-lookup"><span data-stu-id="07ff4-122">Applying the DtsLogProvider Attribute</span></span>
 <span data-ttu-id="07ff4-123">앞에서 만든 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 특성을 적용하여 해당 클래스를 로그 공급자로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-123">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class that you have created to identify it as a log provider.</span></span> <span data-ttu-id="07ff4-124">이 특성은 로그 공급자의 이름 및 설명 같은 디자인 타임 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-124">This attribute provides design-time information such as the name and description of the log provider.</span></span> <span data-ttu-id="07ff4-125">`DisplayName` `Description` 특성의 및 속성은 **Name** `Description` 에서 패키지에 대 한 로깅을 구성할 때 표시 되는 **SSIS 로그 구성** 편집기에 표시 되는 이름 및 열에 해당 합니다 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="07ff4-125">The `DisplayName` and `Description` properties of the attribute correspond to the **Name** and `Description` columns displayed in the **Configure SSIS Logs** editor, which is displayed when configuring logging for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="07ff4-126">이 특성의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> 속성은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-126">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> property of the attribute is not used.</span></span> <span data-ttu-id="07ff4-127">그러나 이 속성을 설정하지 않으면 사용 가능한 로그 공급자 목록에 해당 사용자 지정 로그 공급자가 표시되지 않으므로 이 속성 값을 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-127">However, you must enter a value for it, or the custom log provider will not appear in the list of available log providers.</span></span>

> [!NOTE]
>  <span data-ttu-id="07ff4-128">사용자 지정 로그 공급자의 사용자 지정 사용자 인터페이스는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 구현되어 있지 않으므로 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 속성에 값을 지정해도 아무 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-128">Since custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], specifying a value for the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> has no effect.</span></span>

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a><span data-ttu-id="07ff4-129">사용자 지정 로그 공급자 빌드, 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="07ff4-129">Building, Deploying, and Debugging a Custom Log Provider</span></span>
 <span data-ttu-id="07ff4-130">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 사용자 지정 로그 공급자의 빌드, 배포 및 디버깅 단계는 다른 형식의 사용자 지정 개체에 대해 필요한 단계와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="07ff4-130">The steps for building, deploying, and debugging a custom log provider in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="07ff4-131">자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07ff4-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>

<span data-ttu-id="07ff4-132">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="07ff4-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="07ff4-133">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="07ff4-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="07ff4-134">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="07ff4-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="07ff4-135">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="07ff4-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="07ff4-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07ff4-136">See Also</span></span>
 <span data-ttu-id="07ff4-137">사용자 지정 [로그 공급자 코딩](coding-a-custom-log-provider.md) 사용자 [지정 로그 공급자의 사용자 인터페이스 개발](developing-a-user-interface-for-a-custom-log-provider.md)</span><span class="sxs-lookup"><span data-stu-id="07ff4-137">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md)</span></span>


