---
title: RSWindowsExtendedProtectionScenario 속성 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84e14d056cc0352b0d1d85bc12c9c873a1b89ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734915"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7af3e-102">RSWindowsExtendedProtectionScenario 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7af3e-102">RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7af3e-103">보고서 서버에서 허용하도록 구성된 확장된 보호 시나리오를 나타내는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7af3e-103">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af3e-104">구문</span><span class="sxs-lookup"><span data-stu-id="7af3e-104">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a><span data-ttu-id="7af3e-105">설명</span><span class="sxs-lookup"><span data-stu-id="7af3e-105">Remarks</span></span>  
 <span data-ttu-id="7af3e-106">보고서 서버에서 허용하도록 구성된 확장된 보호 시나리오를 나타내는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7af3e-106">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span> <span data-ttu-id="7af3e-107">WMI 공급자가 연결되어 있는 보고서 서버에서 확장된 보호를 지원하지 않으면 ""(빈 문자열)이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af3e-107">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span>  
  
 <span data-ttu-id="7af3e-108">다음 목록에서는 유효한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7af3e-108">The following list shows valid values:</span></span>  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a><span data-ttu-id="7af3e-109">코드 예</span><span class="sxs-lookup"><span data-stu-id="7af3e-109">Example Code</span></span>  
 [<span data-ttu-id="7af3e-110">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="7af3e-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="7af3e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7af3e-111">See Also</span></span>  
 <span data-ttu-id="7af3e-112">[RSWindowsExtendedProtectionLevel 속성&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="7af3e-112">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="7af3e-113">[SetExtendedProtectionSettings 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="7af3e-113">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="7af3e-114">[Reporting Services 인증에 대한 확장된 보호](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="7af3e-114">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="7af3e-115">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="7af3e-115">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
