---
title: 사용자 지정 인증 쿠키를 전달 하도록 보고서 관리자 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90e8798fb91152ec64e7f290dc1522fc8eaa451c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648259"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a><span data-ttu-id="4db29-102">보고서 관리자에서 사용자 지정 인증 쿠키를 전달하도록 구성</span><span class="sxs-lookup"><span data-stu-id="4db29-102">Configure Report Manager to Pass Custom Authentication Cookies</span></span>
  <span data-ttu-id="4db29-103">사용자 지정 인증 확장 프로그램을 사용하는 경우 보고서 관리자에서 사용자 지정 인증 쿠키를 전송하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-103">If you are using a custom authentication extension, you should configure Report Manager to transmit custom authentication cookies.</span></span> <span data-ttu-id="4db29-104">그렇게 하지 않으면 보고서 관리자에서 HTTP 요청을 통해 보고서 서버 관련 쿠키만 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-104">Otherwise, Report Manager will only transmit cookies through HTTP requests specific to the report server.</span></span> <span data-ttu-id="4db29-105">추가 쿠키를 전송하려면 RSReportServer.Config 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-105">If you want to transmit additional cookies, you must modify the RSReportServer.Config file.</span></span>  
  
## <a name="modifying-the-rsreportserverconfig-file"></a><span data-ttu-id="4db29-106">RSReportServer.Config 파일 수정</span><span class="sxs-lookup"><span data-stu-id="4db29-106">Modifying the RSReportServer.Config File</span></span>  
 <span data-ttu-id="4db29-107"><`PassThroughCookies`> 요소를 RSReportServer.config 파일의 보고서 관리자 구성 설정에 추가 하 여 추가 쿠키를 보고서 서버에 전송 하도록 보고서 관리자 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-107">You can enable Report Manager to transmit additional cookies through to the report server by adding a <`PassThroughCookies`> element to the Report Manager configuration settings in the RSReportServer.config file.</span></span> <span data-ttu-id="4db29-108">추가 쿠키 전송은 보고서 서버 인증 쿠키뿐만 아니라 타사 인증 시스템의 쿠키도 필요한 Single Sign-On 인증 솔루션에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-108">Transmitting additional cookies is helpful in a single sign-on authentication solution that requires not only the report server authentication cookies, but also cookies from a third-party authentication system.</span></span>  
  
 <span data-ttu-id="4db29-109">보고서 관리자 사용 시 HTTP 요청을 통해 추가 쿠키를 전송하려면 RSReportServer.config 파일에서 다음 요소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4db29-109">To enable additional cookies to be transmitted through HTTP requests when using Report Manager, set the following elements in the RSReportServer.config file:</span></span>  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4db29-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4db29-110">See Also</span></span>  
 <span data-ttu-id="4db29-111">[보고서 서버 인증](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="4db29-111">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="4db29-112">[Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="4db29-112">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="4db29-113">[보안 확장 프로그램 개요](../extensions/security-extension/security-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4db29-113">[Security Extensions Overview](../extensions/security-extension/security-extensions-overview.md) </span></span>  
 [<span data-ttu-id="4db29-114">보고서 서버 구성 및 관리&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="4db29-114">Configure and Administer a Report Server &#40;SSRS Native Mode&#41;</span></span>](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
