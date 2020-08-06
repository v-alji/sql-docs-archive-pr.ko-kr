---
title: RSWindowsExtendedProtectionLevel 속성 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02ff3bad42ae25adf6cfa563944d89bac2c600e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649890"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="0a8a9-102">RSWindowsExtendedProtectionLevel 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="0a8a9-102">RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="0a8a9-103">보고서 서버에서 지원하도록 구성된 보호 수준을 나타내는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8a9-103">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="0a8a9-104">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0a8a9-104">This property is read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a8a9-105">구문</span><span class="sxs-lookup"><span data-stu-id="0a8a9-105">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a><span data-ttu-id="0a8a9-106">설명</span><span class="sxs-lookup"><span data-stu-id="0a8a9-106">Remarks</span></span>  
 <span data-ttu-id="0a8a9-107">보고서 서버에서 지원하도록 구성된 보호 수준을 나타내는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8a9-107">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="0a8a9-108">WMI 공급자가 연결되어 있는 보고서 서버에서 확장된 보호를 지원하지 않으면 ""(빈 문자열)이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a8a9-108">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span> <span data-ttu-id="0a8a9-109">다음 목록에서는 유효한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a8a9-109">The following list shows valid values:</span></span>  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a><span data-ttu-id="0a8a9-110">코드 예</span><span class="sxs-lookup"><span data-stu-id="0a8a9-110">Example Code</span></span>  
 [<span data-ttu-id="0a8a9-111">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="0a8a9-111">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a8a9-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a8a9-112">See Also</span></span>  
 <span data-ttu-id="0a8a9-113">[RSWindowsExtendedProtectionScenario 속성&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="0a8a9-113">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="0a8a9-114">[SetExtendedProtectionSettings 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="0a8a9-114">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="0a8a9-115">[Reporting Services 인증에 대한 확장된 보호](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="0a8a9-115">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="0a8a9-116">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="0a8a9-116">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
