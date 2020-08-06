---
title: VSTA로 스크립트 마이그레이션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: afbc19c35f99a5abc5a6ebd92024e42baa6a9237
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740700"
---
# <a name="migrate-scripts-to-vsta"></a><span data-ttu-id="72cbd-102">VSTA로 스크립트 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="72cbd-102">Migrate Scripts to VSTA</span></span>
  <span data-ttu-id="72cbd-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]패키지를로 업그레이드 하 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 경우는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 스크립트 태스크 또는 스크립트 구성 요소의 스크립트를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA (Tools for Applications)로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-103">When you upgrade [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] packages to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migrates the scripts in any Script tasks or Script components to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="72cbd-104">VSTA는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 사용하는 스크립팅 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-104">VSTA is the scripting environment that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> <span data-ttu-id="72cbd-105">에서의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 스크립트 환경은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSA (for Applications)입니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the scripting environment for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).</span></span>  
  
 <span data-ttu-id="72cbd-106">스크립트 태스크나 스크립트 구성 요소의 스크립트에서 인터페이스를 참조하는 경우에는 패키지를 업그레이드하기 전에 해당 참조를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-106">If the scripts in either the Script tasks or Script components reference interfaces, you might have to modify those references before you upgrade the package.</span></span> <span data-ttu-id="72cbd-107">그렇지 않으면 사용하는 업그레이드 방법에 따라 패키지 업그레이드가 실패하거나 스크립트의 유효성 검사가 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-107">Otherwise, the package will not be upgraded or the scripts will not be validated, depending on the upgrade method that you use.</span></span> <span data-ttu-id="72cbd-108">이러한 참조를 수정 하려면 IDTS*xxx*90 인터페이스에 대 한 참조를 해당 idts*xxx*100 인터페이스에 대 한 참조로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-108">To modify these references, replace references to IDTS*xxx*90 interfaces with references to the corresponding IDTS*xxx*100 interfaces.</span></span>  
  
 <span data-ttu-id="72cbd-109">스크립트를 마이그레이션하고 패키지를 업그레이드 하는 방법에 대 한 자세한 내용은 [Integration Services 패키지 업그레이드](../../integration-services/install-windows/upgrade-integration-services-packages.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72cbd-109">For more information about how to migrate scripts and upgrade packages, see [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).</span></span>  
  
## <a name="understanding-migration-failures"></a><span data-ttu-id="72cbd-110">마이그레이션 오류 이해</span><span class="sxs-lookup"><span data-stu-id="72cbd-110">Understanding Migration Failures</span></span>  
 <span data-ttu-id="72cbd-111">스크립트를 마이그레이션할 때 다음과 같은 이유로 마이그레이션이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-111">When you migrate the scripts, the migration can fail because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="72cbd-112">VSA 스크립트의 진입점 이름이 바뀐 경우</span><span class="sxs-lookup"><span data-stu-id="72cbd-112">The entry point for the VSA script was renamed.</span></span>  
  
     <span data-ttu-id="72cbd-113">진입점은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임이 VSTA 프로젝트의 `ScriptMain` 클래스에서 스크립트 태스크 코드에 대한 진입점으로 호출하는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-113">The entry point specifies the method in the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="72cbd-114">`ScriptMain` 클래스는 스크립트 템플릿이 생성하는 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-114">The `ScriptMain` class is the default class that the script templates generate.</span></span>  
  
-   <span data-ttu-id="72cbd-115">VSA 스크립트에 진입점이 없거나 여러 개 있는 경우</span><span class="sxs-lookup"><span data-stu-id="72cbd-115">There is no entry point or there are multiple entry points in the VSA script.</span></span>  
  
-   <span data-ttu-id="72cbd-116">어셈블리 참조를 추가할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="72cbd-116">Assembly references could not be added.</span></span>  
  
-   <span data-ttu-id="72cbd-117">`ScriptMain` 클래스는 `ScriptObjectModelSSIS` 클래스뿐만 아니라 다른 클래스에서도 상속되도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-117">The `ScriptMain` class was modified to inherit from other classes in addition to the `ScriptObjectModelSSIS` class.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="72cbd-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]는 다중 상속을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72cbd-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] does not support multiple inheritance.</span></span>  
  
 <span data-ttu-id="72cbd-119">에서 사용 하는 VSA 스크립트를에서 사용 하는 VSTA 스크립트로 변환할 수 없습니다 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72cbd-119">You cannot convert a VSA script that uses [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] to a VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="72cbd-120">그러나를 사용 하는 새 VSTA 스크립트를 만들 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72cbd-120">However, you can create a new VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="72cbd-121">자세한 내용은은 [스크립트 태스크 코딩 및 디버깅](../../integration-services/control-flow/script-task.md) 및 [스크립트 구성 요소 코딩 및 디버깅](../../integration-services/data-flow/transformations/script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="72cbd-121">For more information, see [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) and [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cbd-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72cbd-122">See Also</span></span>  
 [<span data-ttu-id="72cbd-123">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="72cbd-123">Extending Packages with Scripting</span></span>](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
