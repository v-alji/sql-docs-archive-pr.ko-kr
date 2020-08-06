---
title: 데이터 처리 확장 프로그램 라이브러리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c14ed699e94c7d8ed0f6f3d727e9ba6e355b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743031"
---
# <a name="creating-a-data-processing-extension-library"></a><span data-ttu-id="90dcf-102">데이터 처리 확장 프로그램 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="90dcf-102">Creating a Data Processing Extension Library</span></span>
  <span data-ttu-id="90dcf-103">만드는 각 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램은 고유한 네임스페이스에 할당하고 라이브러리 또는 어셈블리 파일로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="90dcf-104">네임스페이스의 정확한 이름은 중요하지 않지만 고유한 이름이어야 하며 다른 확장 프로그램과 공유하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="90dcf-105">에서는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 포함되어 있는 데이터 처리 확장 프로그램에 대해 <xref:Microsoft.ReportingServices.DataProcessing> 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-105">uses the namespace <xref:Microsoft.ReportingServices.DataProcessing> for the data processing extensions that ship with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="90dcf-106">회사의 데이터 처리 확장 프로그램에 대해 고유한 네임스페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-106">You should create your own unique namespaces for your company's data processing extensions.</span></span>  
  
 <span data-ttu-id="90dcf-107">다음 예는 데이터 처리 인터페이스 및 유틸리티 클래스가 포함된 네임스페이스를 사용하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 시작하기 위한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-107">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, which uses the namespaces that contain the data processing interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="90dcf-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 컴파일할 때 데이터 처리 확장 프로그램 인터페이스가 포함된 Microsoft.ReportingServices.Interfaces.dll에 대한 참조를 컴파일러에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-108">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the data processing extension interfaces are contained there.</span></span> <span data-ttu-id="90dcf-109"><xref:Microsoft.ReportingServices.DataProcessing> 네임스페이스는 데이터 처리 확장 프로그램 인터페이스를 구현하는 데 필요하고, <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스는 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스를 구현하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-109">The <xref:Microsoft.ReportingServices.DataProcessing> namespace is needed to implement the data processing extension interfaces, and the <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface.</span></span> <span data-ttu-id="90dcf-110">예를 들어 C#으로 작성된 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 구현할 코드가 포함된 모든 파일이 확장명 .cs로 단일 디렉터리에 있는 경우 해당 디렉터리에서 다음 명령을 실행하여 CompanyName.ExtensionName.dll에 저장된 파일을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-110">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="90dcf-111">다음 코드 예제에서는 확장명 .vb인 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 파일에 대해 사용되는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-111">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="90dcf-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]를 사용하여 데이터 처리 확장 프로그램을 디자인, 개발 및 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90dcf-112">You can also design, develop, and build your data processing extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="90dcf-113">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 어셈블리를 개발하는 방법은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="90dcf-113">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90dcf-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90dcf-114">See Also</span></span>  
 <span data-ttu-id="90dcf-115">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="90dcf-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="90dcf-116">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="90dcf-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="90dcf-117">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="90dcf-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
