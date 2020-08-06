---
title: 보고서 서버에서 사용자 지정 또는 폼 인증 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1447e1e695f0e59dbc07b7e19f4df335a1220a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648262"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a><span data-ttu-id="46173-102">보고서 서버에서 사용자 지정 또는 폼 인증 구성</span><span class="sxs-lookup"><span data-stu-id="46173-102">Configure Custom or Forms Authentication on the Report Server</span></span>
  <span data-ttu-id="46173-103">Reporting Services에서는 사용자 지정 또는 폼 기반 인증 모듈을 추가할 수 있는 확장 가능한 아키텍처를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-103">Reporting Services provides an extensible architecture that allows you to plug in custom or forms-based authentication modules.</span></span> <span data-ttu-id="46173-104">배포 요구 사항에 Windows 통합 보안이나 기본 인증이 포함되지 않은 경우 사용자 지정 인증 확장 프로그램을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-104">You might consider implementing a custom authentication extension if deployment requirements do not include Windows integrated security or Basic authentication.</span></span> <span data-ttu-id="46173-105">사용자 지정 인증을 사용하는 가장 일반적인 시나리오는 웹 애플리케이션에 대한 인터넷 또는 엑스트라넷 액세스를 지원하려는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="46173-105">The most common scenario for using custom authentication is to support Internet or extranet access to a Web application.</span></span> <span data-ttu-id="46173-106">기본 Windows 인증 확장 프로그램을 사용자 지정 인증 확장 프로그램으로 바꾸면 외부 사용자에게 보고서 서버에 대한 액세스 권한을 부여하는 방법을 보다 자세히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-106">Replacing the default Windows Authentication extension with a custom authentication extension gives you more control over how external users are granted access to the report server.</span></span>  
  
 <span data-ttu-id="46173-107">실제로 사용자 지정 인증 확장 프로그램을 배포하려면 어셈블리 및 애플리케이션 파일 복사, 구성 파일 수정 및 테스트 등의 여러 단계를 거쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-107">In practice, deploying a custom authentication extension requires multiple steps that include copying assemblies and application files, modifying configuration files, and testing.</span></span> <span data-ttu-id="46173-108">이 항목에서는 구성 파일에 지정하는 인증 설정에만 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="46173-108">This topic focuses on just the authentication settings that you specify in the configuration files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46173-109">사용자 지정 인증 확장 프로그램을 만들려면 사용자 지정 코드와 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 보안 관련 지식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-109">Creating a custom authentication extension requires custom code and expertise in [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] security.</span></span> <span data-ttu-id="46173-110">사용자 지정 인증 확장 프로그램을 만들지 않으려는 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory 그룹 및 계정을 사용할 수 있지만, 이렇게 하려면 보고서 서버 배포 범위를 대폭 줄여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-110">If you do not want to create a custom authentication extension, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory groups and accounts, but you should greatly reduce the scope of a report server deployment.</span></span> <span data-ttu-id="46173-111">사용자 지정 인증에 대한 자세한 내용은 [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="46173-111">For more information about custom authentication, see [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
 <span data-ttu-id="46173-112">또한 SharePoint 제품과 통합된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 환경에서 폼 인증이나 사용자 지정 인증 확장 프로그램을 사용하려는 경우에는 SharePoint 사이트에서 해당 인증 방법을 사용하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-112">Additionally, if you want to use Forms authentication or a custom authentication extension in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environment that is integrated with a SharePoint product, you must configure the SharePoint site to use the authentication method that you choose.</span></span> <span data-ttu-id="46173-113">SharePoint에서 인증을 구성하는 방법은 MSDN( [Developer Network)에서](https://go.microsoft.com/fwlink/?LinkId=115575) 인증 예제 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46173-113">For more information about configuring authentication in SharePoint, see [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a><span data-ttu-id="46173-114">사용자 지정 인증을 사용하도록 보고서 서버를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="46173-114">To configure a report server to use Custom authentication</span></span>  
  
1.  <span data-ttu-id="46173-115">텍스트 편집기에서 RSReportServer.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46173-115">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="46173-116"><`Authentication`>를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-116">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="46173-117">다음 XML 구조를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-117">Copy the following XML structure:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  <span data-ttu-id="46173-118"><>의 기존 항목 위에 붙여넣습니다 `Authentication` .</span><span class="sxs-lookup"><span data-stu-id="46173-118">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="46173-119">`Custom`은 다른 인증 유형과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-119">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="46173-120">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-120">Save the file.</span></span>  
  
6.  <span data-ttu-id="46173-121">보고서 서버의 Web.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46173-121">Open the Web.config file for the report server.</span></span> <span data-ttu-id="46173-122">기본적으로 이 파일은 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-122">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.</span></span>  
  
7.  <span data-ttu-id="46173-123">`authentication mode`를 찾아 `Forms`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-123">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  <span data-ttu-id="46173-124">`identity impersonate`를 찾아 `False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-124">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. <span data-ttu-id="46173-125">보고서 관리자의 Web.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46173-125">Open the Web.config file for Report Manager.</span></span> <span data-ttu-id="46173-126">기본적으로 이 파일은 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46173-126">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.</span></span>  
  
10. <span data-ttu-id="46173-127">`authentication mode`를 찾아 `Forms`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-127">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. <span data-ttu-id="46173-128">`identity impersonate`를 찾아 `False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-128">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. <span data-ttu-id="46173-129">구성 파일에 `PassThroughCookies` 요소 구조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-129">Add the `PassThroughCookies` element structure to the configuration file.</span></span> <span data-ttu-id="46173-130">자세한 내용은 [보고서 관리자에서 사용자 지정 인증 쿠키를 전달하도록 구성](configure-the-web-portal-to-pass-custom-authentication-cookies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46173-130">For more information, see [Configure Report Manager to Pass Custom Authentication Cookies](configure-the-web-portal-to-pass-custom-authentication-cookies.md).</span></span>  
  
13. <span data-ttu-id="46173-131">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-131">Save the file.</span></span>  
  
14. <span data-ttu-id="46173-132">스케일 아웃 배포를 구성한 경우 배포의 다른 보고서 서버에서 위의 모든 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="46173-132">If you configured a scale-out deployment, repeat all of the previous steps for other report servers in the deployment.</span></span>  
  
15. <span data-ttu-id="46173-133">보고서 서버를 다시 시작하여 현재 열려 있는 모든 세션을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="46173-133">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46173-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46173-134">See Also</span></span>  
 <span data-ttu-id="46173-135">[보안 확장 프로그램 구현](../extensions/security-extension/implementing-a-security-extension.md) </span><span class="sxs-lookup"><span data-stu-id="46173-135">[Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md) </span></span>  
 <span data-ttu-id="46173-136">[보고서 서버 인증](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="46173-136">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="46173-137">[Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="46173-137">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="46173-138">[보고서 서버에서 기본 인증 구성](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="46173-138">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="46173-139">보고서 서버의 Windows 인증 구성</span><span class="sxs-lookup"><span data-stu-id="46173-139">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)  
  
  
