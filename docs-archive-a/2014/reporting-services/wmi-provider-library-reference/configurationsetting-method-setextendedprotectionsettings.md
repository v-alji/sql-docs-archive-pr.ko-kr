---
title: SetExtendedProtectionSettings 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee937747b74bcf8d53012721b4be5bfca04185df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737726"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="b8a97-102">SetExtendedProtectionSettings 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="b8a97-102">SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="b8a97-103">SetExtendedProtectionSettings 메서드는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 파일인 RSReportServer.config에서 RSWindowsExtendedProtectionLevel 및 RSWindowsExtendedProtectionScenario 속성을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-103">The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration file RSReportServer.config.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a97-104">구문</span><span class="sxs-lookup"><span data-stu-id="b8a97-104">Syntax</span></span>  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8a97-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b8a97-105">Parameters</span></span>  
 <span data-ttu-id="b8a97-106">*ExtendedProtectionLevel*</span><span class="sxs-lookup"><span data-stu-id="b8a97-106">*ExtendedProtectionLevel*</span></span>  
 <span data-ttu-id="b8a97-107">RSRreportserver.config 파일에서 RSWindowsExtendedProtectionLevel을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-107">Sets the RSWindowsExtendedProtectionLevel in the RSRreportserver.config file.</span></span> <span data-ttu-id="b8a97-108">이 필수 값은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-108">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="b8a97-109">다음 목록에서는 유효한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-109">The following list shows valid values:</span></span>  
  
 `"Off | Allow | Require"`  
  
 <span data-ttu-id="b8a97-110">*ExtendedProtectionScenario*</span><span class="sxs-lookup"><span data-stu-id="b8a97-110">*ExtendedProtectionScenario*</span></span>  
 <span data-ttu-id="b8a97-111">RSReportserver.config 파일에서 RSWindowsExtendedProtectionScenario를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-111">Sets the RSWindowsExtendedProtectionScenario in the RSReportserver.config file.</span></span> <span data-ttu-id="b8a97-112">이 필수 값은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-112">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="b8a97-113">다음 목록에서는 유효한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-113">The following list shows valid values:</span></span>  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a><span data-ttu-id="b8a97-114">설명</span><span class="sxs-lookup"><span data-stu-id="b8a97-114">Remarks</span></span>  
 <span data-ttu-id="b8a97-115">RSWindowsExtendedProtectionLevel 및 RSWindowsExtendedProtectionScenario 속성은 RSReportServer.config 파일의 AuthenticationTypes에 RSWindowNTLM, RSWindowsNegotiate, 또는 RSWindowsKerberos가 포함된 경우 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-115">The RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties apply when the AuthenticationTypes in the RSReportServer.config file include RSWindowNTLM, RSWindowsNegotiate, or RSWindowsKerberos.</span></span> <span data-ttu-id="b8a97-116">이러한 속성을 설정하면 사용자와 클라이언트 소프트웨어가 보고서 서버에 인증하는 방식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-116">Setting these properties affects how users and client software authenticate with a report server.</span></span> <span data-ttu-id="b8a97-117">먼저 확장된 보호와 관련된 설명서를 읽은 후 ExtendedProtectionLevel을 `Allow` 또는 `Require`로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-117">It is recommended that you read the documentation for extended protection before setting ExtendedProtectionLevel to either `Allow` or `Require`.</span></span>  
  
 <span data-ttu-id="b8a97-118">ExtendedProtectionLevel을 설정하려면 사용자가 보고서 서버의 BUILTIN\Administrators 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a97-118">To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\Administrators group on the report server.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a97-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b8a97-119">Requirements</span></span>  
 <span data-ttu-id="b8a97-120">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a97-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a97-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8a97-121">See Also</span></span>  
 <span data-ttu-id="b8a97-122">[RSWindowsExtendedProtectionScenario 속성&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="b8a97-122">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="b8a97-123">[RSWindowsExtendedProtectionLevel 속성&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="b8a97-123">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="b8a97-124">[Reporting Services 인증에 대한 확장된 보호](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b8a97-124">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="b8a97-125">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="b8a97-125">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
