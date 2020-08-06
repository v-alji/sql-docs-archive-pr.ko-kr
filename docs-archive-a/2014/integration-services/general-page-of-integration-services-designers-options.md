---
title: 일반 페이지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59073ac29f95f1e64bd0a9382366e9539ce1408a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647131"
---
# <a name="general-page"></a><span data-ttu-id="6ca1c-102">일반 페이지</span><span class="sxs-lookup"><span data-stu-id="6ca1c-102">General Page</span></span>
  <span data-ttu-id="6ca1c-103">**옵션** 대화 상자에 있는 **Integration Services 디자이너** 페이지의 **일반** 페이지를 사용하여 패키지 로드, 표시 및 업그레이드 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-103">Use the **General** page of the **Integration Services Designers** page in the **Options** dialog box to specify the options for loading, displaying, and upgrading packages.</span></span>  
  
 <span data-ttu-id="6ca1c-104">**에서** 일반 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]페이지를 열려면 **도구** 메뉴에서 **옵션**을 클릭한 다음 **Business Intelligence 디자이너**를 확장하여 **Integration Services 디자이너**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-104">To open the **General** page, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Tools** menu, click **Options**, expand **Business Intelligence Designers**, and select **Integration Services Designers**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ca1c-105">옵션</span><span class="sxs-lookup"><span data-stu-id="6ca1c-105">Options</span></span>  
 <span data-ttu-id="6ca1c-106">**패키지 로드 시 디지털 서명 확인**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-106">**Check digital signature when loading a package**</span></span>  
 <span data-ttu-id="6ca1c-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 패키지 로드 시 디지털 서명을 확인하도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-107">Select to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] check the digital signature when loading a package.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6ca1c-108">에서는 디지털 서명이 있는지, 유효한지 신뢰할 수 있는 원본에서 가져온 것인지 여부만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-108">will only check whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6ca1c-109">에서는 패키지가 서명된 이후 변경되었는지 여부는 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-109">will not check whether the package has been changed since the package was signed.</span></span>  
  
 <span data-ttu-id="6ca1c-110">**BlockedSignatureStates** 레지스트리 값을 설정하면 이 레지스트리 값으로 인해 **패키지 로드 시 디지털 서명 확인** 옵션이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-110">If you set the **BlockedSignatureStates** registry value, this registry value overrides the **Check digital signature when loading a package** option.</span></span> <span data-ttu-id="6ca1c-111">자세한 내용은 [레지스트리 값을 설정하여 서명 정책 구현](implement-a-signing-policy-by-setting-a-registry-value.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-111">For more information, see [Implement a Signing Policy by Setting a Registry Value](implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
 <span data-ttu-id="6ca1c-112">디지털 인증서 및 패키지에 대한 자세한 내용은 [디지털 서명을 사용하여 패키지 원본 확인](security/identify-the-source-of-packages-with-digital-signatures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-112">For more information about digital certificates and packages, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
 <span data-ttu-id="6ca1c-113">**패키지가 서명되어 있지 않으면 경고 표시**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-113">**Show warning if package is unsigned**</span></span>  
 <span data-ttu-id="6ca1c-114">서명되어 있지 않은 패키지를 로드할 때 경고를 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-114">Select to display a warning when loading a package that is not signed.</span></span>  
  
 <span data-ttu-id="6ca1c-115">**선행 제약 조건 레이블 표시**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-115">**Show precedence constraint labels**</span></span>  
 <span data-ttu-id="6ca1c-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 확인할 때 선행 제약 조건에 표시할 레이블을 성공, 실패, 완료 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-116">Select which label-Success, Failure, or Completion-to display on precedence constraints when viewing packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6ca1c-117">**스크립트 언어**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-117">**Scripting language**</span></span>  
 <span data-ttu-id="6ca1c-118">새 스크립트 태스크 및 스크립트 구성 요소에 대한 기본 스크립트 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-118">Select the default scripting language for new Script tasks and Script components.</span></span>  
  
 <span data-ttu-id="6ca1c-119">**새 공급자 이름을 사용하도록 연결 문자열 업데이트**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-119">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="6ca1c-120">[!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] 패키지를 열거나 업그레이드할 때 현재 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전에 대해 다음 공급자의 이름을 사용하도록 연결 문자열을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-120">When opening or upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, update connection strings to use the names for the following providers, for the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="6ca1c-121">OLE DB 공급자</span><span class="sxs-lookup"><span data-stu-id="6ca1c-121">OLE DB provider</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6ca1c-122">Native Client</span><span class="sxs-lookup"><span data-stu-id="6ca1c-122">Native Client</span></span>  
  
 <span data-ttu-id="6ca1c-123">[!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 업그레이드 마법사는 연결 관리자에 저장된 연결 문자열만 업데이트하며</span><span class="sxs-lookup"><span data-stu-id="6ca1c-123">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="6ca1c-124">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 식 언어 또는 스크립트 태스크의 코드를 사용하여 동적으로 생성된 연결 문자열은 업데이트하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-124">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="6ca1c-125">**새 패키지 ID 만들기**</span><span class="sxs-lookup"><span data-stu-id="6ca1c-125">**Create new package ID**</span></span>  
 <span data-ttu-id="6ca1c-126">[!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] 패키지를 업그레이드할 때 업그레이드된 버전의 패키지에 대해 새 패키지 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6ca1c-126">When upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, create new package IDs for the upgraded versions of the packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca1c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ca1c-127">See Also</span></span>  
 <span data-ttu-id="6ca1c-128">[보안 개요&#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="6ca1c-128">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="6ca1c-129">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="6ca1c-129">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
