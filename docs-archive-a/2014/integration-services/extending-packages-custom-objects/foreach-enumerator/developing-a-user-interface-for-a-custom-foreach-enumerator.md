---
title: 사용자 지정 ForEach 열거자의 사용자 인터페이스 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 500c67f1ee4577190d7a24286bbfeed0347e92fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651201"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a><span data-ttu-id="4ef47-102">사용자 지정 ForEach 열거자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="4ef47-102">Developing a User Interface for a Custom ForEach Enumerator</span></span>
  <span data-ttu-id="4ef47-103">기본 클래스의 속성 및 메서드 구현을 재정의하여 사용자 지정 기능을 제공한 후 Foreach 열거자에 대한 사용자 지정 사용자 인터페이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your Foreach enumerator.</span></span> <span data-ttu-id="4ef47-104">사용자 지정 사용자 인터페이스를 만들지 않을 경우 사용자는 속성 창에서만 새 사용자 지정 Foreach 열거자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-104">If you do not create a custom user interface, users can only configure the new custom Foreach enumerator by using the Properties window.</span></span>  
  
 <span data-ttu-id="4ef47-105">사용자 지정 사용자 인터페이스 프로젝트 또는 어셈블리에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-105">In a custom user interface project or assembly, you create a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>.</span></span> <span data-ttu-id="4ef47-106">이 클래스는 일반적으로 다른 Windows Forms 컨트롤을 호스팅하는 합성 컨트롤을 만드는 데 사용되는 System.Windows.Forms.UserControl에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-106">This class derives from System.Windows.Forms.UserControl, which is typically used to create a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="4ef47-107">만든 컨트롤은 **Foreach 루프 편집기**의 **컬렉션** 탭에 있는 **열거자 구성** 영역에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-107">The control that you create is displayed in the **Enumerator configuration** area of the **Collection** tab of the **Foreach Loop Editor**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4ef47-108">[사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)에 설명된 대로 사용자 지정 사용자 인터페이스를 서명 및 빌드하고 전역 어셈블리 캐시에 설치한 후에는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 속성에서 이 클래스의 정규화된 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-108">After signing and building your custom user interface and installing it in the global assembly cache as described in [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
## <a name="coding-the-user-interface-control-class"></a><span data-ttu-id="4ef47-109">사용자 인터페이스 컨트롤 클래스 코딩</span><span class="sxs-lookup"><span data-stu-id="4ef47-109">Coding the User Interface Control Class</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="4ef47-110">사용자 인터페이스 초기화</span><span class="sxs-lookup"><span data-stu-id="4ef47-110">Initializing the User Interface</span></span>  
 <span data-ttu-id="4ef47-111"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> 메서드를 재정의하여 호스트 개체에 대한 참조와 패키지에 정의된 연결 관리자 및 변수의 컬렉션에 대한 참조를 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-111">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> method to cache references to the host object, and to the collections of connection managers and variables defined in the package.</span></span>  
  
### <a name="setting-properties-on-the-user-interface-control"></a><span data-ttu-id="4ef47-112">사용자 인터페이스 컨트롤의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="4ef47-112">Setting Properties on the User Interface Control</span></span>  
 <span data-ttu-id="4ef47-113">사용자 인터페이스 클래스를 파생시키는 기본 UserControl 클래스는 다른 Windows Forms 컨트롤을 호스팅하는 합성 컨트롤로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-113">The UserControl class, from which the user interface class is derived, is intended for use as a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="4ef47-114">이 클래스는 다른 컨트롤을 호스팅하므로 Windows Forms 애플리케이션에서와 같이 컨트롤을 끌어 놓은 다음 정렬하고 해당 속성을 설정하고 런타임에 해당 이벤트에 응답하여 사용자 지정 인터페이스를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-114">Because this class hosts other controls, you can design your custom user interface by dragging and dropping controls, arranging them, setting their properties, and responding at run time to their events as in any Windows Forms application.</span></span>  
  
### <a name="saving-settings"></a><span data-ttu-id="4ef47-115">설정 저장</span><span class="sxs-lookup"><span data-stu-id="4ef47-115">Saving Settings</span></span>  
 <span data-ttu-id="4ef47-116"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> 메서드를 재정의하여 사용자가 편집기를 닫을 때 컨트롤에서 선택한 값을 열거자의 속성에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef47-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> method to copy the values selected by the user from the controls to the properties of the enumerator when the user closes the editor.</span></span>  
  
<span data-ttu-id="4ef47-117">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4ef47-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4ef47-118">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4ef47-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4ef47-119">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4ef47-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4ef47-120">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4ef47-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef47-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ef47-121">See Also</span></span>  
 <span data-ttu-id="4ef47-122">[사용자 지정 Foreach 열거자 만들기](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="4ef47-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="4ef47-123">사용자 지정 Foreach 열거자 코딩</span><span class="sxs-lookup"><span data-stu-id="4ef47-123">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
  
  
