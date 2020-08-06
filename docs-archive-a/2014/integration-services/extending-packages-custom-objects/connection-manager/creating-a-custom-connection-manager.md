---
title: 사용자 지정 연결 관리자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857efebbe311e5510e15cae9e78a2b424559ded7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742415"
---
# <a name="creating-a-custom-connection-manager"></a><span data-ttu-id="6b700-102">사용자 지정 연결 관리자 만들기</span><span class="sxs-lookup"><span data-stu-id="6b700-102">Creating a Custom Connection Manager</span></span>
  <span data-ttu-id="6b700-103">사용자 지정 연결 관리자를 만들 때 수행해야 하는 단계는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 다른 사용자 지정 개체를 만들 때의 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-103">The steps that you must follow to create a custom connection manager are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="6b700-104">기본 클래스에서 상속되는 새 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="6b700-105">연결 관리자의 경우 기본 클래스는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>입니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-105">For a connection manager, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.</span></span>  
  
-   <span data-ttu-id="6b700-106">개체 유형을 식별하는 특성을 클래스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="6b700-107">연결 관리자의 경우 이 특성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>입니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-107">For a connection manager, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
-   <span data-ttu-id="6b700-108">기본 클래스의 메서드 및 속성 구현을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-108">Override the implementation of the methods and properties of the base class.</span></span> <span data-ttu-id="6b700-109">연결 관리자의 경우 이러한 구현에는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 속성과 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-109">For a connection manager, these include the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods.</span></span>  
  
-   <span data-ttu-id="6b700-110">필요한 경우 사용자 지정 사용자 인터페이스를 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="6b700-111">연결 관리자의 경우 사용자 지정 사용자 인터페이스를 개발하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 인터페이스를 구현하는 클래스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-111">For a connection manager, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b700-112">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 기본 제공된 대부분의 태스크, 원본 및 대상은 특정 유형의 기본 제공 연결 관리자와만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-112">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="6b700-113">따라서 이러한 예제를 기본 제공 태스크 및 구성 요소와 함께 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-113">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="getting-started-with-a-custom-connection-manager"></a><span data-ttu-id="6b700-114">사용자 지정 연결 관리자 시작</span><span class="sxs-lookup"><span data-stu-id="6b700-114">Getting Started with a Custom Connection Manager</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="6b700-115">프로젝트 및 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="6b700-115">Creating Projects and Classes</span></span>  
 <span data-ttu-id="6b700-116">관리되는 연결 관리자는 모두 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 기본 클래스에서 파생되므로 사용자 지정 연결 관리자를 만들려면 먼저 관리되는 프로그래밍 언어로 클래스 라이브러리 프로젝트를 만들고 기본 클래스에서 상속되는 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-116">Because all managed connection managers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, the first step when you create a custom connection manager is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="6b700-117">이 파생 클래스에서 기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-117">In this derived class, you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="6b700-118">동일한 솔루션에서 사용자 지정 사용자 인터페이스에 대한 두 번째 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-118">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="6b700-119">배포를 쉽게 하려면 사용자 인터페이스에 대한 별도의 어셈블리를 만드는 것이 좋습니다. 이렇게 하면 연결 관리자 또는 해당 사용자 인터페이스를 독립적으로 업데이트하거나 다시 배포할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-119">A separate assembly for the user interface is recommended for ease of deployment because it lets you update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="6b700-120">강력한 이름 키 파일을 사용하여 빌드 시 생성될 어셈블리에 서명하도록 두 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-120">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsconnection-attribute"></a><span data-ttu-id="6b700-121">DtsConnection 특성 적용</span><span class="sxs-lookup"><span data-stu-id="6b700-121">Applying the DtsConnection Attribute</span></span>  
 <span data-ttu-id="6b700-122">앞에서 만든 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 특성을 적용하여 해당 클래스를 연결 관리자로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-122">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class that you have created to identify it as a connection manager.</span></span> <span data-ttu-id="6b700-123">이 특성은 연결 관리자의 이름, 설명 및 연결 유형 같은 디자인 타임 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-123">This attribute provides design-time information such as the name, description, and connection type of the connection manager.</span></span> <span data-ttu-id="6b700-124"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>및 `Description` 속성은에서 패키지에 **Type** `Description` 대 한 연결을 구성할 때 표시 되는 **SSIS 연결 관리자 추가** 대화 상자에 표시 되는 유형 및 열에 해당 합니다 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6b700-124">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> and `Description` properties correspond to the **Type** and `Description` columns displayed in the **Add SSIS Connection Manager** dialog box, which is displayed when configuring connections for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6b700-125"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> 속성을 사용하여 연결 관리자를 사용자 지정 사용자 인터페이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-125">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property to link the connection manager to its custom user interface.</span></span> <span data-ttu-id="6b700-126">이 속성에 필요한 공개 키 토큰을 가져오려면 **sn.exe -t**를 사용하여 사용자 인터페이스 어셈블리 서명에 사용할 키 쌍(.snk) 파일의 공개 키 토큰을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-126">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a><span data-ttu-id="6b700-127">사용자 지정 연결 관리자 빌드, 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="6b700-127">Building, Deploying, and Debugging a Custom Connection Manager</span></span>  
 <span data-ttu-id="6b700-128">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 사용자 지정 연결 관리자의 빌드, 배포 및 디버깅 단계는 다른 형식의 사용자 지정 개체에 대한 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6b700-128">The steps for building, deploying, and debugging a custom connection manager in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps for other types of custom objects.</span></span> <span data-ttu-id="6b700-129">자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b700-129">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="6b700-130">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6b700-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6b700-131">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6b700-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6b700-132">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6b700-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6b700-133">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6b700-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b700-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b700-134">See Also</span></span>  
 <span data-ttu-id="6b700-135">[사용자 지정 연결 관리자 코딩](coding-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6b700-135">[Coding a Custom Connection Manager](coding-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="6b700-136">사용자 지정 연결 관리자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="6b700-136">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
