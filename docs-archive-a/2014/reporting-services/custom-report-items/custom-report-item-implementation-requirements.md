---
title: 사용자 지정 보고서 항목 구현 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69fdf58eb385e819b524b9c5b5178997257c797c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741643"
---
# <a name="custom-report-item-implementation-requirements"></a><span data-ttu-id="bab0f-102">사용자 지정 보고서 항목 구현 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bab0f-102">Custom Report Item Implementation Requirements</span></span>
  <span data-ttu-id="bab0f-103">이 항목에서는 사용자 지정 보고서 항목을 개발하고 배포하기 위한 선행 조건에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-103">This topic will discuss the prerequisites for developing and deploying custom report items.</span></span>  
  
## <a name="development-and-deployment-requirements"></a><span data-ttu-id="bab0f-104">개발 및 배포 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bab0f-104">Development and Deployment Requirements</span></span>  
 <span data-ttu-id="bab0f-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대한 사용자 지정 보고서 항목을 개발하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-105">Developing a custom report item for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requires the following:</span></span>  
  
-   <span data-ttu-id="bab0f-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및를 사용 하 여를 실행 하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 대 한 관리 액세스</span><span class="sxs-lookup"><span data-stu-id="bab0f-106">Administrative access to a server running [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]<span data-ttu-id="bab0f-107">또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK (소프트웨어 개발 키트)가 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-107">or above with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] software development kit (SDK) installed.</span></span>  
  
-   <span data-ttu-id="bab0f-108">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서에 대한 액세스</span><span class="sxs-lookup"><span data-stu-id="bab0f-108">Access to the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
-   <span data-ttu-id="bab0f-109">구성 요소 제작 및 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 구성 요소 모델 네임스페이스에 대한 지식.</span><span class="sxs-lookup"><span data-stu-id="bab0f-109">Familiarity with component authoring and the component model namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="bab0f-110">자세한 내용은 msdn.microsoft.com에서 "구성 요소 제작" 및 "Visual Studio의 구성 요소 모델 네임스페이스"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bab0f-110">For more information, see "Component Authoring" and "Component Model Namespaces in Visual Studio" on msdn.microsoft.com.</span></span>  
  
## <a name="language-and-namespace-requirements"></a><span data-ttu-id="bab0f-111">언어 및 네임스페이스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bab0f-111">Language and Namespace Requirements</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bab0f-112">사용자 지정 보고서 항목은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-112">custom report items fully support the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="bab0f-113">원하는 .NET 호환 언어를 사용하여 사용자 지정 보고서 항목을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-113">You can develop custom report items using your choice of .NET-compliant languages.</span></span>  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]<span data-ttu-id="bab0f-114">에서는 코딩, 디버깅, 테스트 등의 반복되는 주기를 단순화 및 가속화하고 쉽게 배포할 수 있도록 다양한 도구와 기능을 개발자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-114">offers the developer many tools and features to simplify and accelerate the iterative cycles of coding, debugging, and testing and to make deployment easier.</span></span> <span data-ttu-id="bab0f-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK에는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 과 C# 컴파일러 및 관련 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-115">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK includes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and C# compilers and related tools.</span></span>  
  
-   <span data-ttu-id="bab0f-116">사용자 지정 보고서 항목에서는 `Microsoft.ReportDesigner` 및 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스가 사용되며,</span><span class="sxs-lookup"><span data-stu-id="bab0f-116">Custom report items use the `Microsoft.ReportDesigner` and <xref:Microsoft.ReportingServices.Interfaces> namespaces.</span></span> <span data-ttu-id="bab0f-117">이 네임스페이스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 일부로 설치되는 Microsoft.ReportingServices.Designer.DLL 및 Microsoft.ReportingServices.Interfaces.DLL 어셈블리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-117">These are stored in the Microsoft.ReportingServices.Designer.DLL and Microsoft.ReportingServices.Interfaces.DLL assemblies, which are installed as part of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bab0f-118">사용자 지정 보고서 항목 디자인 타임 구성 요소는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 <xref:System.ComponentModel> 네임스페이스에서 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-118">Custom report item design-time components need to implement interfaces from the <xref:System.ComponentModel> namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="bab0f-119"><xref:System.ComponentModel>은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bab0f-119">The <xref:System.ComponentModel> is documented in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bab0f-120">기본적으로 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 설치되지만 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK는 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-120">By default, the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK is not.</span></span> <span data-ttu-id="bab0f-121">컴퓨터에 SDK가 설치되지 않아 SDK 설명서가 온라인 설명서 컬렉션에 포함되어 있지 않을 경우 이 섹션의 SDK 내용에 대한 링크가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-121">Unless the SDK is installed on the computer and the SDK documentation is included in the Books Online collection, links to SDK content in this section will not work.</span></span> <span data-ttu-id="bab0f-122">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK를 설치한 후 [SQL Server 제품 설명서 추가 또는 제거](../../index.yml)의 지침에 따라 온라인 설명서 컬렉션과 목차에 SDK 설명서를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab0f-122">After you have installed the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, you can add the SDK documentation to the Books Online collection and table of contents by following the instructions in [Add or Remove Product Documentation for SQL Server](../../index.yml).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab0f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bab0f-123">See Also</span></span>  
 <span data-ttu-id="bab0f-124">[사용자 지정 보고서 항목 런타임 구성 요소 만들기](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="bab0f-124">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="bab0f-125">[사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="bab0f-125">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="bab0f-126">[방법: 사용자 지정 보고서 항목 배포](how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="bab0f-126">[How to: Deploy a Custom Report Item](how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="bab0f-127">사용자 지정 보고서 항목 클래스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bab0f-127">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
