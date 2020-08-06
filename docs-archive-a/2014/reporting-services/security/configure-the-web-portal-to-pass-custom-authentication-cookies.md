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
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>보고서 관리자에서 사용자 지정 인증 쿠키를 전달하도록 구성
  사용자 지정 인증 확장 프로그램을 사용하는 경우 보고서 관리자에서 사용자 지정 인증 쿠키를 전송하도록 구성해야 합니다. 그렇게 하지 않으면 보고서 관리자에서 HTTP 요청을 통해 보고서 서버 관련 쿠키만 전송합니다. 추가 쿠키를 전송하려면 RSReportServer.Config 파일을 수정해야 합니다.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config 파일 수정  
 <`PassThroughCookies`> 요소를 RSReportServer.config 파일의 보고서 관리자 구성 설정에 추가 하 여 추가 쿠키를 보고서 서버에 전송 하도록 보고서 관리자 수 있습니다. 추가 쿠키 전송은 보고서 서버 인증 쿠키뿐만 아니라 타사 인증 시스템의 쿠키도 필요한 Single Sign-On 인증 솔루션에 유용합니다.  
  
 보고서 관리자 사용 시 HTTP 요청을 통해 추가 쿠키를 전송하려면 RSReportServer.config 파일에서 다음 요소를 설정합니다.  
  
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
  
## <a name="see-also"></a>참고 항목  
 [보고서 서버 인증](authentication-with-the-report-server.md)   
 [Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md)   
 [보안 확장 프로그램 개요](../extensions/security-extension/security-extensions-overview.md)   
 [보고서 서버 구성 및 관리&#40;SSRS 기본 모드&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
