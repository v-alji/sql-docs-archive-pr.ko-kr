---
title: 확장 프로그램에 대한 보안 고려 사항 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- extensions [Reporting Services], security
- permissions [Reporting Services], extensions
ms.assetid: 58cbdfeb-1105-4a7d-a3b8-b897ff95f367
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e7819f4d6de2003c9982d33ab00cfa0d4030aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660902"
---
# <a name="security-considerations-for-extensions"></a><span data-ttu-id="46810-102">확장 프로그램에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="46810-102">Security Considerations for Extensions</span></span>
  <span data-ttu-id="46810-103">CLR(공용 언어 런타임) 기능이 있는 모든 애플리케이션은 CLR 보안 시스템과 상호 작용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-103">Every application that targets the common language runtime (CLR) must interact with the CLR security system.</span></span> <span data-ttu-id="46810-104">이러한 애플리케이션은 실행되면 CLR에 의해 자동으로 평가되어 권한 집합이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="46810-104">When such an application runs, it is automatically evaluated and given a set of permissions by the CLR.</span></span> <span data-ttu-id="46810-105">부여받은 권한에 따라 애플리케이션이 계속 실행될 수도 있고 보안 예외가 생성될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46810-105">Depending on the permissions that the application receives, it either continues running or generates a security exception.</span></span> <span data-ttu-id="46810-106">특정 보고서 서버에 대한 보안 정책 구성 파일의 로컬 보안 설정 및 정책은 어셈블리에서 수신하는 코드 권한을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-106">The local security settings and policies in the security policy configuration files for a particular report server define the code permissions that an assembly receives.</span></span>  
  
 <span data-ttu-id="46810-107">권한을 요청하기 전에 확장 프로그램 코드에서 사용할 리소스 및 보호된 작업에 대해 알고 있어야 하며 이러한 리소스 및 작업을 보호하고 있는 권한도 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-107">Before requesting permissions, you need to be aware of the resources and protected operations your extension code is planning to use, and you also need to know which permissions protect those resources and operations.</span></span> <span data-ttu-id="46810-108">또한 확장 프로그램 구성 요소가 호출하는 클래스 라이브러리 메서드에서 액세스하는 리소스도 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-108">In addition, you need to keep track of any resources accessed by any class library methods that are called by the extension components.</span></span> <span data-ttu-id="46810-109">자세한 내용은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 개발자 가이드의 "Requesting Permissions(권한 요청)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="46810-109">For more information, see "Requesting Permissions" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
 <span data-ttu-id="46810-110">보고서 서버에 배포된 확장 프로그램은 완전히 신뢰할 수 있는 상태로 실행되어야 합니다. 즉, 확장 프로그램은 **FullTrust** 권한 집합이 부여된 코드 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-110">Extensions deployed to a report server must run as fully trusted, meaning that your extension needs to be part of a code group that is granted the **FullTrust** permission set.</span></span> <span data-ttu-id="46810-111">또한 특정 보고서에 대해 인증되는 사용자에 따라 확장 프로그램이 CLR을 통해 사용할 수 있는 특정 서버 리소스 및 작업에 대한 액세스 권한을 가질 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-111">This also means that your extension may have access to certain server resources and operations available through the CLR depending on the user that is being authenticated for a particular report.</span></span> <span data-ttu-id="46810-112">코드 그룹 및 확장에 관한 자세한 내용은 [Reporting Services의 코드 액세스 보안](secure-development/code-access-security-in-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46810-112">For more information about code groups and extensions, see [Code Access Security in Reporting Services](secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="46810-113">에서는 모든 확장 프로그램에 대해 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 보안을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-113">enforces [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security for all of its extensions.</span></span>  
  
 <span data-ttu-id="46810-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 데이터 처리, 배달, 렌더링 및 보안 확장 프로그램의 배포에 다음 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46810-114">The following conditions apply to the deployment of data processing, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="46810-115">로컬 관리자만 확장 프로그램을 배포할 수 있는 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="46810-115">Only the local administrator has permission to deploy an extension.</span></span>  
  
-   <span data-ttu-id="46810-116">적절한 읽기/쓰기 권한을 가진 사용자만 확장할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소에 대한 구성 파일을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46810-116">Only users with the appropriate read/write permissions can change the configuration files for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component that is being extended.</span></span>  
  
-   <span data-ttu-id="46810-117">권한이 있는 사용자만 보안 정책 파일을 편집하고 확장 프로그램에 대한 코드 액세스 보안을 사용할 수 있는 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="46810-117">Only privileged users have permission to edit the security policy files and enable code access security for an extension.</span></span>  
  
 <span data-ttu-id="46810-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 코드 액세스 보안에 대한 자세한 내용은 [보안 개발 & #40; Reporting Services& #41;](secure-development/secure-development-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46810-118">For more information about code access security in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md).</span></span>  
  
 <span data-ttu-id="46810-119">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 보안에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 개발자 가이드의 ".NET Framework Security(.NET Framework 보안)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="46810-119">For more information about [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security, see ".NET Framework Security" in your [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
## <a name="initialization-of-extension-assemblies"></a><span data-ttu-id="46810-120">확장 프로그램 어셈블리 초기화</span><span class="sxs-lookup"><span data-stu-id="46810-120">Initialization of Extension Assemblies</span></span>  
 <span data-ttu-id="46810-121">일부 확장 프로그램 어셈블리에서 시스템 리소스 액세스, 구성 파일 읽기 및 다른 종속 어셈블리 로드 작업을 수행하려면 특정 권한이 필요하므로 보고서 서버에서 확장 프로그램이 메모리로 처음 로드될 때 서비스 계정 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46810-121">When extensions are first loaded into memory by the report server, they use the service account credentials, because some extension assemblies require specific permissions to access system resources, to read configuration files, and to load other, dependent assemblies.</span></span> <span data-ttu-id="46810-122">하지만 어셈블리가 로드되고 초기화된 후 확장 프로그램 어셈블리에 대한 이후의 모든 호출에서는 현재 로그온한 사용자 계정의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46810-122">After an assembly has been loaded and initialized, however, all subsequent calls to extension assemblies use the credentials of the user account that is currently logged on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46810-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46810-123">See Also</span></span>  
 <span data-ttu-id="46810-124">[Reporting Services 확장 프로그램](reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="46810-124">[Reporting Services Extensions](reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="46810-125">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="46810-125">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
  
  
