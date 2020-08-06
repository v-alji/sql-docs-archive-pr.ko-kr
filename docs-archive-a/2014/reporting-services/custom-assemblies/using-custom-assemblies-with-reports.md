---
title: 보고서에서 사용자 지정 어셈블리 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730220"
---
# <a name="using-custom-assemblies-with-reports"></a><span data-ttu-id="9e577-102">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="9e577-102">Using Custom Assemblies with Reports</span></span>
  <span data-ttu-id="9e577-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 보고서 항목 값, 스타일 및 서식 지정을 위한 사용자 지정 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can write custom code for report item values, styles, and formatting.</span></span> <span data-ttu-id="9e577-104">예를 들어, 사용자 지정 코드를 사용하여 로캘에 따른 통화 형식을 지정하거나 특정 값을 특수한 서식으로 플래그 지정하거나 회사에서 사용되는 다른 비즈니스 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-104">For example, you can use custom code to format currencies based on locale, flag certain values with special formatting, or apply other business rules that are in practice for your company.</span></span> <span data-ttu-id="9e577-105">보고서에이 코드를 포함 하는 한 가지 방법은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 보고서 정의 파일 내에서 참조할 수 있는를 사용 하 여 사용자 지정 코드 어셈블리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-105">One way to include this code in your reports is to create a custom code assembly using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that you can reference from within your report definition files.</span></span> <span data-ttu-id="9e577-106">보고서가 실행되면 서버는 사용자 어셈블리에서 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-106">The server calls the functions in your custom assemblies when a report is run.</span></span> <span data-ttu-id="9e577-107">사용자 지정 어셈블리는 보고서에서 사용하고자 하는 특수화된 함수를 검색하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-107">Custom assemblies can be used to retrieve specialized functions that you plan to use in your reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e577-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9e577-108">In This Section</span></span>  
 [<span data-ttu-id="9e577-109">RDL 파일에서 어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="9e577-109">Referencing Assemblies in an RDL File</span></span>](referencing-assemblies-in-an-rdl-file.md)  
 <span data-ttu-id="9e577-110">보고서 정의 언어 파일에서 사용자 지정 어셈블리를 참조하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-110">Describes how to reference your custom assemblies in a report definition language file.</span></span>  
  
 [<span data-ttu-id="9e577-111">사용자 지정 어셈블리 배포</span><span class="sxs-lookup"><span data-stu-id="9e577-111">Deploying a Custom Assembly</span></span>](deploying-a-custom-assembly.md)  
 <span data-ttu-id="9e577-112">사용자 지정 어셈블리를 보고서 디자이너 및 보고서 서버에 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-112">Describes how to deploy a custom assembly to Report Designer and the report server.</span></span>  
  
 [<span data-ttu-id="9e577-113">강력한 이름의 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="9e577-113">Using Strong-Named Custom Assemblies</span></span>](using-strong-named-custom-assemblies.md)  
 <span data-ttu-id="9e577-114">강력한 이름을 가진 사용자 지정 어셈블리를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-114">Describes how to use custom assemblies with strong names.</span></span>  
  
 [<span data-ttu-id="9e577-115">사용자 지정 어셈블리에서 권한 어설션</span><span class="sxs-lookup"><span data-stu-id="9e577-115">Asserting Permissions in Custom Assemblies</span></span>](asserting-permissions-in-custom-assemblies.md)  
 <span data-ttu-id="9e577-116">제한된 권한 및 특정 권한으로 사용자 지정 어셈블리를 배포하는 방법과 이러한 권한을 코드에서 어설션하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-116">Describes how to deploy custom assemblies with limited and specific permissions and how to assert those permissions in code.</span></span>  
  
 [<span data-ttu-id="9e577-117">식을 통해 사용자 지정 어셈블리 액세스</span><span class="sxs-lookup"><span data-stu-id="9e577-117">Accessing Custom Assemblies Through Expressions</span></span>](accessing-custom-assemblies-through-expressions.md)  
 <span data-ttu-id="9e577-118">사용자 지정 어셈블리 메서드를 보고서 정의에서 보고서 식의 형태로 호출하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-118">Describes how to call custom assembly methods as report expressions in your report definitions.</span></span>  
  
 [<span data-ttu-id="9e577-119">사용자 지정 어셈블리 개체 초기화</span><span class="sxs-lookup"><span data-stu-id="9e577-119">Initializing Custom Assembly Objects</span></span>](initializing-custom-assembly-objects.md)  
 <span data-ttu-id="9e577-120">보고서에서 호출된 사용자 지정 어셈블리 개체에 대한 값을 초기화하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-120">Describes how to initialize values for custom assembly objects called from a report.</span></span>  
  
 [<span data-ttu-id="9e577-121">방법: 사용자 지정 어셈블리 디버깅</span><span class="sxs-lookup"><span data-stu-id="9e577-121">How to: Debug Custom Assemblies</span></span>](how-to-debug-custom-assemblies.md)  
 <span data-ttu-id="9e577-122">사용자 지정 어셈블리 코드를 디버깅하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e577-122">Describes how to debug your custom assembly code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e577-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e577-123">See Also</span></span>  
 [<span data-ttu-id="9e577-124">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9e577-124">Report Definition Language &#40;SSRS&#41;</span></span>](../reports/report-definition-language-ssrs.md)  
  
  
