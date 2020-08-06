---
title: RDL 파일에서 어셈블리 참조 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14593717d2319d7d702fd0c414e0c24428006f51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729143"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a><span data-ttu-id="50e5e-102">RDL 파일에서 어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="50e5e-102">Referencing Assemblies in an RDL File</span></span>
  <span data-ttu-id="50e5e-103">보고서 정의 파일에서 사용자 지정 코드 어셈블리를 사용할 수 있도록 지원하기 위해 두 가지 RDL(Report Definition Language) 요소인 **CodeModules** 요소와 **Classes** 요소가 RDL 사양에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-103">To support the use of custom code assemblies in report definition files, two Report Definition Language (RDL) elements are included in the RDL specification: the **CodeModules** element and the **Classes** element.</span></span>  
  
 <span data-ttu-id="50e5e-104">**CodeModules** 요소를 통해 보고서 식에서 관리 코드 어셈블리를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-104">The **CodeModules** element enables you to refer to managed code assemblies in report expressions.</span></span> <span data-ttu-id="50e5e-105">**CodeModules**는 보고서 정의 파일에서 특수화된 함수를 호출하는 데 사용하는 어셈블리에 대한 참조가 포함된 최상위 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-105">**CodeModules** is a top-level element that contains the reference to the assembly that you use in your report definition files to call specialized functions.</span></span> <span data-ttu-id="50e5e-106">사용자 지정 어셈블리 사용을 지원하는 보고서 정의 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-106">An entry in a report definition that supports the use of a custom assembly might look like the following:</span></span>  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 <span data-ttu-id="50e5e-107">사용자 지정 코드에서 <xref:System.Reflection.Assembly.Load%2A>를 호출하는 대신 **CodeModule** 요소를 RDL 파일에 수동으로 추가하거나 **보고서 속성** 대화 상자의 **참조** 탭을 사용하여 사용자 지정 어셈블리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-107">Instead of calling <xref:System.Reflection.Assembly.Load%2A> from your custom code, register your custom assemblies by either manually adding **CodeModule** elements to your RDL file or by using the **References** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="50e5e-108">자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-108">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="50e5e-109">**Classes** 요소는 보고서 정의에서 인스턴스 멤버 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-109">The **Classes** element supports the use of instance members in a report definition.</span></span> <span data-ttu-id="50e5e-110">**Classes**는 클래스 이름 및 인스턴스 이름에 대한 참조를 포함하는 최상위 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-110">**Classes** is a top-level element that contains a reference to the class name and an instance name.</span></span> <span data-ttu-id="50e5e-111">인스턴스 멤버 사용을 지원하는 보고서 정의 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50e5e-111">An entry in a report definition that supports the use of instance members might look like the following:</span></span>  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 <span data-ttu-id="50e5e-112">자세한 내용은 [식을 통해 사용자 지정 어셈블리 액세스](accessing-custom-assemblies-through-expressions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50e5e-112">For more information, see [Accessing Custom Assemblies Through Expressions](accessing-custom-assemblies-through-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e5e-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50e5e-113">See Also</span></span>  
 [<span data-ttu-id="50e5e-114">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="50e5e-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
