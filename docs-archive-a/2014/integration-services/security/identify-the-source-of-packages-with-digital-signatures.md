---
title: 디지털 서명을 사용하여 패키지 원본 확인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90c0e2e3db13ba4b228b70ccfffddbc2ff221774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743340"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a><span data-ttu-id="a813d-102">디지털 서명을 사용하여 패키지 원본 확인</span><span class="sxs-lookup"><span data-stu-id="a813d-102">Identify the Source of Packages with Digital Signatures</span></span>
  <span data-ttu-id="a813d-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에 해당 원본을 식별하는 디지털 인증서를 사용하여 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be signed with a digital certificate to identify its source.</span></span> <span data-ttu-id="a813d-104">디지털 인증서를 사용하여 패키지에 서명하면 패키지를 로드하기 전에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 디지털 서명을 확인하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-104">After a package has been signed with a digital certificate, you can have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the digital signature before loading the package.</span></span> <span data-ttu-id="a813d-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 서명을 확인하도록 하려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 **dtexec** 유틸리티(dtexec.exe)에서 옵션을 설정하거나 선택적 레지스트리 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-105">To have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the signature, you set an option in either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in the **dtexec** utility (dtexec.exe), or set an optional registry value.</span></span>  
  
## <a name="signing-a-package-with-a-digital-certificate"></a><span data-ttu-id="a813d-106">디지털 인증서를 사용하여 패키지 서명</span><span class="sxs-lookup"><span data-stu-id="a813d-106">Signing a Package with a Digital Certificate</span></span>  
 <span data-ttu-id="a813d-107">디지털 인증서를 사용하여 패키지에 서명하려면 먼저 인증서를 만들거나 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-107">Before you can sign a package with a digital certificate, you first have to obtain or create the certificate.</span></span> <span data-ttu-id="a813d-108">인증서가 있으면 이 인증서를 사용하여 패키지에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-108">After you have the certificate, you can then use this certificate to sign the package.</span></span> <span data-ttu-id="a813d-109">인증서를 가져오고 해당 인증서를 사용하여 패키지에 서명하는 방법에 대한 자세한 내용은 [디지털 인증서를 사용하여 패키지 서명](../sign-a-package-by-using-a-digital-certificate.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a813d-109">For more information about how to obtain a certificate and sign a package with that certificate, see [Sign a Package by Using a Digital Certificate](../sign-a-package-by-using-a-digital-certificate.md).</span></span>  
  
## <a name="setting-an-option-to-check-the-package-signature"></a><span data-ttu-id="a813d-110">패키지 서명을 확인하는 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="a813d-110">Setting an Option to Check the Package Signature</span></span>  
 <span data-ttu-id="a813d-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 및 **dtexec** 유틸리티 모두에는 서명된 패키지의 디지털 서명을 확인하도록 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 를 구성하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-111">Both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and the **dtexec** utility have an option that configures [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of a signed package.</span></span> <span data-ttu-id="a813d-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 **dtexec** 유틸리티 중 무엇을 사용할지는 다음과 같이 모든 패키지를 확인할지 또는 특정 패키지만 확인할지에 따라 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-112">Whether you use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or the **dtexec** utility depends on whether you want to check all packages or just specific ones:</span></span>  
  
-   <span data-ttu-id="a813d-113">디자인 타임에 패키지를 로드하기 전에 모든 패키지의 디지털 서명을 확인하려면 **에서** 패키지 로드 시 디지털 서명 확인 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-113">To check the digital signature of all packages before loading the packages at design time, set the **Check digital signature when loading a package** option in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a813d-114">이 옵션은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 모든 패키지에 대한 전역 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-114">This option is a global setting for all packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a813d-115">자세한 내용은 [General Page](../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a813d-115">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
-   <span data-ttu-id="a813d-116">개별 패키지의 디지털 서명을 확인 하려면 `/VerifyS[igned]` **dtexec** 유틸리티를 사용 하 여 패키지를 실행할 때 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-116">To check the digital signature of an individual package, specify the `/VerifyS[igned]` option when you use the **dtexec** utility to run the package.</span></span> <span data-ttu-id="a813d-117">자세한 내용은 [dtexec Utility](../packages/dtexec-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a813d-117">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a><span data-ttu-id="a813d-118">패키지 서명을 확인하는 레지스트리 값 설정</span><span class="sxs-lookup"><span data-stu-id="a813d-118">Setting a Registry Value to Check the Package Signature</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a813d-119">에서는 서명되거나 서명되지 않은 패키지에 대한 조직의 정책을 관리하는 데 사용할 수 있는 선택적 레지스트리 값인 **BlockedSignatureStates**도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-119">also supports an optional registry value, **BlockedSignatureStates**, that you can use to manage an organization's policy for loading signed and unsigned packages.</span></span> <span data-ttu-id="a813d-120">이 레지스트리 값을 사용하면 패키지에 서명이 없거나 패키지의 서명이 잘못되거나 신뢰할 수 없는 경우 패키지를 로드하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-120">The registry value can prevent packages from loading if the packages are unsigned, or have invalid or untrusted signatures.</span></span> <span data-ttu-id="a813d-121">이 레지스트리 값을 설정하는 방법에 대한 자세한 내용은 [레지스트리 값을 설정하여 서명 정책 구현](../implement-a-signing-policy-by-setting-a-registry-value.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a813d-121">For more information about how to set this registry value, see [Implement a Signing Policy by Setting a Registry Value](../implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a813d-122">선택적 **BlockedSignatureStates** 레지스트리 값은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 **dtexec** 명령줄에서 설정한 디지털 서명 옵션보다 더 제한적인 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-122">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or at the **dtexec** command line.</span></span> <span data-ttu-id="a813d-123">이 경우 더 제한적인 설정이 다른 설정보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="a813d-123">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a813d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a813d-124">See Also</span></span>  
 <span data-ttu-id="a813d-125">[SSIS&#41; 패키지 Integration Services &#40;](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="a813d-125">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="a813d-126">보안 개요&#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a813d-126">Security Overview &#40;Integration Services&#41;</span></span>](security-overview-integration-services.md)  
  
  
