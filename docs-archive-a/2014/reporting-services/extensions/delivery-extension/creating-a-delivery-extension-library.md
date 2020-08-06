---
title: 배달 확장 프로그램 라이브러리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9891c2b0c1bb9c7d495b3ab1f8f2267ce04b79f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741571"
---
# <a name="creating-a-delivery-extension-library"></a><span data-ttu-id="f3374-102">배달 확장 프로그램 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="f3374-102">Creating a Delivery Extension Library</span></span>
  <span data-ttu-id="f3374-103">만드는 각 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 고유한 네임스페이스에 할당하고 라이브러리 또는 어셈블리 파일로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="f3374-104">네임스페이스의 정확한 이름은 중요하지 않지만 고유한 이름이어야 하며 다른 확장 프로그램과 공유하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> <span data-ttu-id="f3374-105">회사의 배달 확장 프로그램에 대해 고유한 네임스페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-105">You should create your own unique namespaces for your company's delivery extensions.</span></span>  
  
 <span data-ttu-id="f3374-106">다음 예에서는 배달 인터페이스 및 유틸리티 클래스가 포함된 네임스페이스를 사용하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 시작하기 위한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-106">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, which uses the namespaces that contain the delivery interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="f3374-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 컴파일할 때 배달 확장 프로그램 인터페이스 및 클래스가 포함된 Microsoft.ReportingServices.Interfaces.dll에 대한 참조를 컴파일러에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-107">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the delivery extension interfaces and classes are contained there.</span></span> <span data-ttu-id="f3374-108"><xref:Microsoft.ReportingServices.Interfaces> 네임스페이스는 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스, <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 인터페이스 등을 구현하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-108">The <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface, the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, and more.</span></span> <span data-ttu-id="f3374-109">예를 들어 C#으로 작성된 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 구현할 코드가 포함된 모든 파일이 확장명 .cs로 단일 디렉터리에 있는 경우 해당 디렉터리에서 다음 명령을 실행하여 CompanyName.ExtensionName.dll에 저장된 파일을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-109">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="f3374-110">다음 코드 예제에서는 확장명 .vb인 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 파일에 대해 사용되는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-110">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f3374-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]를 사용하여 배달 확장 프로그램을 디자인, 개발 및 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3374-111">You can also design, develop, and build your delivery extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="f3374-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 어셈블리를 개발하는 방법은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3374-112">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3374-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3374-113">See Also</span></span>  
 <span data-ttu-id="f3374-114">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="f3374-114">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="f3374-115">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="f3374-115">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="f3374-116">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f3374-116">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
