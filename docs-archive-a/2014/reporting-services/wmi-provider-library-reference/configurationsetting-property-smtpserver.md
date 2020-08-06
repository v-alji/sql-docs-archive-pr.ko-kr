---
title: SMTPServer 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SMTPServer
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SMTPServer property
ms.assetid: 8bcceeba-e1a0-44ef-bda1-600c6925e1db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b706834c80fa0ff126d35beffbfdc84ef92cefe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737612"
---
# <a name="smtpserver-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="20710-102">SMTPServer 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="20710-102">SMTPServer Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="20710-103">보고서 서버 구성 파일에서 SMTP 서버 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20710-103">Gets the SMTP server property from the report server configuration file.</span></span> <span data-ttu-id="20710-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="20710-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20710-105">구문</span><span class="sxs-lookup"><span data-stu-id="20710-105">Syntax</span></span>  
  
```vb  
Public Dim SMTPServer As String  
```  
  
```csharp  
public string SMTPServer;  
```  
  
## <a name="property-values"></a><span data-ttu-id="20710-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="20710-106">Property Values</span></span>  
 <span data-ttu-id="20710-107">RSReportServer.config 파일의 `String` 속성 값이 들어 있는 읽기 전용 `SMTPServer` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="20710-107">A read-only `String` object containing the value of the `SMTPServer` property from the RSReportServer.config file.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="20710-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="20710-108">Example Code</span></span>  
 [<span data-ttu-id="20710-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="20710-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="20710-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="20710-110">Requirements</span></span>  
 <span data-ttu-id="20710-111">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20710-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20710-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20710-112">See Also</span></span>  
 [<span data-ttu-id="20710-113">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="20710-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
