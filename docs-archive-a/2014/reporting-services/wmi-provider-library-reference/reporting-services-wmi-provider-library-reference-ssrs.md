---
title: Reporting Services WMI 공급자 라이브러리 참조(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a98ca22f9d34627e484a698dcf540b31808d07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649887"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a><span data-ttu-id="9ac55-102">Reporting Services WMI 공급자 라이브러리 참조(SSRS)</span><span class="sxs-lookup"><span data-stu-id="9ac55-102">Reporting Services WMI Provider Library Reference (SSRS)</span></span>
  <span data-ttu-id="9ac55-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI(Windows Management Instrumentation) 공급자는 보고서 서버 및 보고서 관리자의 설정을 수정하는 스크립트 및 코드를 쓸 수 있도록 WMI 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.</span></span>  
  
 <span data-ttu-id="9ac55-104">예를 들어, 보고서 서버에서 보고서 서버 데이터베이스에 연결할 때 통합 보안 사용 여부를 변경하려면 MSReportServer_ConfigurationSetting 클래스의 인스턴스를 만들고 보고서 서버 인스턴스의 DatabaseIntegratedSecurity 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-104">For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the MSReportServer_ConfigurationSetting class and use the DatabaseIntegratedSecurity property of the of the report server instance.</span></span> <span data-ttu-id="9ac55-105">다음 표에 표시된 클래스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-105">The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="9ac55-106">클래스는 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 또는 [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 네임스페이스에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-106">The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] namespaces.</span></span> <span data-ttu-id="9ac55-107">각 클래스는 읽기 및 쓰기 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-107">Each of the classes support read and write operations.</span></span> <span data-ttu-id="9ac55-108">만들기 작업은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-108">Create operations are not supported.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="9ac55-109">클래스</span><span class="sxs-lookup"><span data-stu-id="9ac55-109">Classes</span></span>  
 [<span data-ttu-id="9ac55-110">MSReportServer_Instance 클래스</span><span class="sxs-lookup"><span data-stu-id="9ac55-110">MSReportServer_Instance Class</span></span>](msreportserver-instance-class.md)  
 <span data-ttu-id="9ac55-111">클라이언트에서 설치된 보고서 서버에 연결하는 데 필요한 기본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-111">Provides basic information required for a client to connect to an installed report server.</span></span>  
  
 [<span data-ttu-id="9ac55-112">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="9ac55-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
 <span data-ttu-id="9ac55-113">보고서 서버 인스턴스의 설치 및 런타임 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-113">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="9ac55-114">이러한 매개 변수는 보고서 서버의 구성 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac55-114">These parameters are stored in the configuration file for the report server.</span></span>  
  
 <span data-ttu-id="9ac55-115">WMI 작업에 대 한 자세한 내용은 sdk에 포함 된 WMI SDK 설명서를 참조 하십시오 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9ac55-115">For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac55-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ac55-116">See Also</span></span>  
 <span data-ttu-id="9ac55-117">[Reporting Services WMI 공급자에 액세스](../tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="9ac55-117">[Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="9ac55-118">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ac55-118">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
