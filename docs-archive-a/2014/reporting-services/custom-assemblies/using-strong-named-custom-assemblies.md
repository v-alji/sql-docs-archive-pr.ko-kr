---
title: 강력한 이름의 사용자 지정 어셈블리 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e685ecda39e0487eb4b469920820fa6e4a10daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639420"
---
# <a name="using-strong-named-custom-assemblies"></a><span data-ttu-id="5d223-102">강력한 이름의 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="5d223-102">Using Strong-Named Custom Assemblies</span></span>
  <span data-ttu-id="5d223-103">강력한 이름은 어셈블리를 식별하며 어셈블리의 텍스트 이름, 네 부분으로 구성된 버전 번호, 문화권 정보(제공된 경우), 공개 키, 어셈블리의 매니페스트에 저장된 디지털 서명 등을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-103">A strong name identifies an assembly and includes the assembly's text name, four-part version number, culture information (if provided), a public key, and a digital signature stored in the assembly's manifest.</span></span> <span data-ttu-id="5d223-104">강력한 이름은 CLR(공용 언어 런타임)에 대해 어셈블리를 고유하게 식별하고 이진 무결성을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-104">A strong name uniquely identifies an assembly to the common language runtime (CLR) and ensures binary integrity.</span></span>  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a><span data-ttu-id="5d223-105">AllowPartiallyTrustedCallersAttribute 사용</span><span class="sxs-lookup"><span data-stu-id="5d223-105">Using AllowPartiallyTrustedCallersAttribute</span></span>  
 <span data-ttu-id="5d223-106">보고서에서 강력한 이름의 어셈블리를 사용하려면 어셈블리의 **AllowPartiallyTrustedCallers** 특성을 사용하여 부분적으로 신뢰할 수 있는 코드를 통해 강력한 이름의 어셈블리가 호출되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-106">To use strong-named assemblies with reports, you must allow your strong-named assembly to be called by partially trusted code using the assembly's **AllowPartiallyTrustedCallers** attribute.</span></span> <span data-ttu-id="5d223-107">**AllowPartiallyTrustedCallersAttribute**를 사용하여 강력한 이름의 어셈블리가 보고서 식에서 보고서 디자이너 또는 보고서 서버에 의해 호출되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-107">You can use **AllowPartiallyTrustedCallersAttribute** to allow strong-named assemblies to be called by Report Designer or the report server in report expressions.</span></span> <span data-ttu-id="5d223-108">부분적으로 신뢰할 수 있는 코드로 강력한 이름의 어셈블리를 호출할 수 있도록 하려면 다음 어셈블리 수준 특성을 어셈블리 특성 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-108">To allow partially trusted code to call strong-named assemblies, add the following assembly-level attribute to your assembly attribute file.</span></span>  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 <span data-ttu-id="5d223-109">**AllowPartiallyTrustedCallersAttribute**는 어셈블리 수준에서 강력한 이름의 어셈블리에 의해 적용될 때만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-109">**AllowPartiallyTrustedCallersAttribute** is effective only when applied by a strong-named assembly at the assembly level.</span></span> <span data-ttu-id="5d223-110">어셈블리 수준에서 특성을 적용 하는 방법에 대 한 자세한 내용은 SDK 설명서의 "특성 적용"을 참조 하십시오 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5d223-110">For more information about applying attributes at the assembly level, see "Applying Attributes" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="5d223-111">**AllowPartiallyTrustedCallersAttribute**가 있는 경우에는 기본 **FullTrustLinkDemand** 보안 검사가 수행되지 않아 부분적으로 신뢰할 수 있는 다른 어셈블리에서 어셈블리를 호출할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-111">When **AllowPartiallyTrustedCallersAttribute** is present, the default **FullTrustLinkDemand** security checks are prevented, making the assembly callable from any other partially trusted assembly.</span></span> <span data-ttu-id="5d223-112">클래스 수준 또는 메서드 수준의 선언적 보안 특성을 포함한 모든 보안 검사는 명시적으로 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d223-112">All security checks, including class-level or method-level declarative security attributes, must be explicitly stated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d223-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d223-113">See Also</span></span>  
 [<span data-ttu-id="5d223-114">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="5d223-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
