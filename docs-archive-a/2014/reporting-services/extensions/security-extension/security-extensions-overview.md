---
title: 보안 확장 프로그램 개요 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9cd6c2a1518b724a7faafecdb2926505694e9707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651506"
---
# <a name="security-extensions-overview"></a><span data-ttu-id="b3e65-102">보안 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="b3e65-102">Security Extensions Overview</span></span>
  <span data-ttu-id="b3e65-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보안 확장 프로그램은 사용자 또는 그룹에 대한 인증 및 권한 부여를 제공합니다. 즉, 여러 사용자들이 보고서 서버에 로그온한 다음 각자의 ID에 준하여 서로 다른 태스크나 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-103">A [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension enables the authentication and authorization of users or groups; that is, it enables different users to log on to a report server and, based on their identities, perform different tasks or operations.</span></span> <span data-ttu-id="b3e65-104">기본적으로 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 는 Windows 계정 프로토콜을 사용하여 시스템에 계정을 보유하고 있다고 주장하는 사용자의 신원을 확인하는 방식의 Windows 기반 인증 확장 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-104">By default, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a Windows-based authentication extension, which uses Windows account protocols to verify the identities of users who claim to have accounts on the system.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="b3e65-105">는 역할 기반 보안 시스템을 사용하여 사용자에게 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-105">uses a role-based security system to authorize users.</span></span> <span data-ttu-id="b3e65-106">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 역할 기반 보안 모델은 다른 기술의 역할 기반 보안 모델과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-106">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] role-based security model is similar to the role-based security models of other technologies.</span></span>

 <span data-ttu-id="b3e65-107">보안 확장 프로그램은 확장 가능한 개방형 API를 기반으로 하므로 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 새 인증 및 권한 부여 확장 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-107">Because security extensions are based on an open and extensible API, you can create new authentication and authorization extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b3e65-108">다음은 Forms 기반 인증 및 권한 부여를 사용하는 일반적인 보안 확장 구현의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-108">The following is an example of a typical security extension implementation that uses Forms-based authentication and authorization:</span></span>

 <span data-ttu-id="b3e65-109">![Reporting Services 보안 확장 프로그램 프로세스](../../media/rosettasecurityextensionflow.gif "Reporting Services 보안 확장 프로그램 프로세스")</span><span class="sxs-lookup"><span data-stu-id="b3e65-109">![Reporting Services security extension process](../../media/rosettasecurityextensionflow.gif "Reporting Services security extension process")</span></span>

 <span data-ttu-id="b3e65-110">그림에서 볼 수 있듯이 인증 및 권한 부여는 다음과 같이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-110">As shown in the illustration, authentication and authorization occur as follows:</span></span>

1.  <span data-ttu-id="b3e65-111">사용자가 URL을 사용하여 보고서 관리자에 액세스하려고 하자 클라이언트 애플리케이션에 대한 사용자 자격 증명을 수집하는 폼으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-111">A user tries to access Report Manager by using a URL and is redirected to a form that collects user credentials for the client application.</span></span>

2.  <span data-ttu-id="b3e65-112">사용자가 폼에 자격 증명을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-112">The user submits credentials to the form.</span></span>

3.  <span data-ttu-id="b3e65-113">사용자 자격 증명이 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 메서드를 통해 Reporting Services 웹 서비스로 제출됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-113">The user credentials are submitted to the Reporting Services Web service through the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span>

4.  <span data-ttu-id="b3e65-114">웹 서비스에서 고객이 제공한 보안 확장 프로그램을 호출하고 사용자 이름과 암호가 사용자 지정 보안 기관에 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-114">The Web service calls the customer-supplied security extension and verifies that the user name and password exist in the custom security authority.</span></span>

5.  <span data-ttu-id="b3e65-115">인증 후 웹 서비스가 인증 티켓(일명 "쿠키")을 만들고, 티켓을 관리하고, 보고서 관리자의 홈 페이지에 대해 사용자의 역할을 검증합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-115">After authentication, the Web service creates an authentication ticket (known as a "cookie"), manages the ticket, and verifies the user's role for the Home page of Report Manager.</span></span>

6.  <span data-ttu-id="b3e65-116">웹 서비스가 브라우저로 쿠키를 반환하고 보고서 관리자에 적절한 사용자 인터페이스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-116">The Web service returns the cookie to the browser and displays the appropriate user interface in Report Manager.</span></span>

7.  <span data-ttu-id="b3e65-117">사용자가 인증된 후 브라우저에서 HTTP 헤더에 쿠키를 전송하는 동안 보고서 관리자에게 요청을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-117">After the user is authenticated, the browser makes requests to Report Manager while transmitting the cookie in the HTTP header.</span></span> <span data-ttu-id="b3e65-118">이 요청은 보고서 관리자 애플리케이션에서 사용자 동작에 응답하여 이루어진 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-118">These requests are in response to user actions within the Report Manager application.</span></span>

8.  <span data-ttu-id="b3e65-119">요청된 사용자 작업과 함께 웹 서비스로 쿠키가 HTTP 헤더에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-119">The cookie is transmitted in the HTTP header to the Web service along with the requested user operation.</span></span>

9. <span data-ttu-id="b3e65-120">쿠키가 검증되고 유효한 경우, 보고서 서버가 보고서 서버 데이터베이스에서 보안 설명자 및 기타 요청된 작업과 관련한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-120">The cookie is validated, and if it is valid, the report server returns the security descriptor and other information relating to the requested operation from the report server database.</span></span>

10. <span data-ttu-id="b3e65-121">쿠키가 유효한 경우 보고서 서버가 보안 확장 프로그램을 호출하여 사용자에게 특정 작업을 수행할 권한이 부여되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-121">If the cookie is valid, the report server makes a call to the security extension to check if the user is authorized to perform the specific operation.</span></span>

11. <span data-ttu-id="b3e65-122">사용자에게 권한이 부여된 경우 보고서 서버가 요청된 작업을 수행하고 호출자에게 제어를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-122">If the user is authorized, the report server performs the requested operation and returns control to the caller.</span></span>

12. <span data-ttu-id="b3e65-123">사용자가 인증된 후 보고서 서버에 대한 URL 액세스에서 같은 쿠키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-123">After the user is authenticated, URL access to the report server uses the same cookie.</span></span> <span data-ttu-id="b3e65-124">쿠키가 HTTP 헤더에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-124">The cookie is transmitted in the HTTP header.</span></span>

13. <span data-ttu-id="b3e65-125">세션이 종료될 때까지 사용자가 계속해서 보고서 서버에 작업을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-125">The user continues to request operations on the report server until the session has ended.</span></span>

## <a name="when-to-implement-a-security-extension"></a><span data-ttu-id="b3e65-126">보안 확장 프로그램 구현 시기</span><span class="sxs-lookup"><span data-stu-id="b3e65-126">When to Implement a Security Extension</span></span>
 <span data-ttu-id="b3e65-127">가능하면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-127">We recommend that you use Windows Authentication if at all possible.</span></span> <span data-ttu-id="b3e65-128">그러나 다음 두 가지 경우에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 에 사용자 지정 인증 및 권한 부여가 적합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e65-128">However, custom authentication and authorization for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] may be appropriate in the following two cases:</span></span>

-   <span data-ttu-id="b3e65-129">인터넷 또는 엑스트라넷 애플리케이션에서 Windows 계정을 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="b3e65-129">You have an Internet or extranet application that cannot use Windows accounts.</span></span>

-   <span data-ttu-id="b3e65-130">사용자가 정의한 사용자 및 역할이 있고 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 대응하는 권한 부여 체계를 제공해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="b3e65-130">You have custom-defined users and roles and need to provide a matching authorization scheme in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e65-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3e65-131">See Also</span></span>
 <span data-ttu-id="b3e65-132">[보안 확장 프로그램을 구현](../security-extension/implementing-a-security-extension.md) [하 여 사용자 지정 인증 쿠키를 전달 하도록 보고서 관리자 구성](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span><span class="sxs-lookup"><span data-stu-id="b3e65-132">[Implementing a Security Extension](../security-extension/implementing-a-security-extension.md) [Configure Report Manager to Pass Custom Authentication Cookies](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span></span>


