---
title: Reporting Services를 사용한 스크립팅 및 PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652013"
---
# <a name="scripting-and-powershell-with-reporting-services"></a><span data-ttu-id="cbd21-102">Reporting Services를 사용한 스크립팅 및 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbd21-102">Scripting and PowerShell with Reporting Services</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cbd21-103">는 rs.exe 명령줄 유틸리티, SharePoint 모드 보고서 서버용 PowerShell cmdlet을 비롯한 스크립트를 통해 기본 모드 및 SharePoint 모드에서 PowerShell의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 개체 모델을 활용하여 다양한 개발 및 관리 시나리오를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-103">supports a wide range of development and management scenarios through script, including the rs.exe command line utility, PowerShell cmdlets for SharePoint mode report servers, and leveraging the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] object model from PowerShell for both Native and SharePoint mode.</span></span>

-   <span data-ttu-id="cbd21-104">관리자는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 에서 스크립트를 작성하여 보고서 서버 설치를 배포 및 관리하는 방법을 자동화하며</span><span class="sxs-lookup"><span data-stu-id="cbd21-104">Administrators can write script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] to automate how they deploy and manage a report server installation.</span></span> <span data-ttu-id="cbd21-105">보고서 서버 데이터베이스를 생성, 구성 및 업데이트하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 생성하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-105">Administrators can also generate and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that create, configure, and update a report server database.</span></span> <span data-ttu-id="cbd21-106">또한 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 기록 및 재생 스크립트 기능을 사용하여 일상적인 유지 관리 작업을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-106">Administrators can also use the record and playback script features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to automate routine maintenance tasks.</span></span>

-   <span data-ttu-id="cbd21-107">개발자는 스크립트를 포함하는 사용자 지정 애플리케이션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-107">Developers can create custom applications that include script.</span></span> <span data-ttu-id="cbd21-108">보고서 서버 웹 서비스를 호출하는 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-108">You can run script that makes calls to the Report Server Web service.</span></span> <span data-ttu-id="cbd21-109">관리 코드로 작성할 수 있는 거의 모든 작업을 스크립트로도 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-109">Almost any operation that you can write in managed code can also be written in script.</span></span>

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="cbd21-110">는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 스크립트를 보고서 서버에서 실행되는 스크립트 호스트인 RS.exe 유틸리티에서 처리할 수 있는 스크립트 언어로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-110">supports [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET script as the script language that can be processed by the RS.exe utility, a script host that runs on the report server.</span></span>

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a><span data-ttu-id="cbd21-111">Reporting Services SharePoint 모드 PowerShell cmdlet 및 샘플</span><span class="sxs-lookup"><span data-stu-id="cbd21-111">Reporting Services SharePoint mode PowerShell cmdlets and samples</span></span>
 <span data-ttu-id="cbd21-112">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="cbd21-112">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cbd21-113">SharePoint 모드에는 보고서 서버 관리를 위한 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-113">SharePoint mode includes [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlets for report server administration.</span></span>

-   <span data-ttu-id="cbd21-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) 에서는 다음 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Includes the following examples:</span></span>

    -   <span data-ttu-id="cbd21-115">서비스 애플리케이션 및 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="cbd21-115">Create a service application and proxy</span></span>

    -   <span data-ttu-id="cbd21-116">배달 확장 검토 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="cbd21-116">Review and update a delivery extension</span></span>

    -   <span data-ttu-id="cbd21-117">보고 서비스 애플리케이션 데이터베이스의 속성 가져오기 및 설정(예: 데이터베이스 시간 제한)</span><span class="sxs-lookup"><span data-stu-id="cbd21-117">Get and set Properties of the Reporting Service Application Database, for example database timeout</span></span>

    -   <span data-ttu-id="cbd21-118">데이터 확장 나열</span><span class="sxs-lookup"><span data-stu-id="cbd21-118">List Data Extensions</span></span>

## <a name="reporting-services-object-model-and-powershell-samples"></a><span data-ttu-id="cbd21-119">Reporting Services 개체 모델 및 Powershell 샘플</span><span class="sxs-lookup"><span data-stu-id="cbd21-119">Reporting Services Object model and Powershell samples</span></span>
 <span data-ttu-id="cbd21-120">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="cbd21-120">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 <span data-ttu-id="cbd21-121">대부분 SharePoint 및 기본 모드에 유효하며 핵심 개체 모델을 호출하는 PowerShell(예: 마이그레이션 작업, 구독 작업)과 관련 샘플은 SQL15에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-121">PowerShell calling the core object model and for the most part valid for SharePoint and native mode, for example the migration work, subscription work, and more related samples for subscriptions work in SQL15.</span></span>

-   <span data-ttu-id="cbd21-122">[PowerShell을 사용하여 Reporting Services 구독 소유자 변경, 나열 및 구독 실행](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="cbd21-122">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>

-   <span data-ttu-id="cbd21-123">[PowerShell을 사용하여 기본 모드 보고서 서버로 Azure VM 만들기](https://msdn.microsoft.com/library/azure/dn449661.aspx)</span><span class="sxs-lookup"><span data-stu-id="cbd21-123">[Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/azure/dn449661.aspx).</span></span>

-   <span data-ttu-id="cbd21-124">[Reporting Services WMI 공급자 액세스](access-the-reporting-services-wmi-provider.md)에서 "PowerShell을 사용하여 WMI 클래스 액세스" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd21-124">See the section "Access the WMI classes using PowerShell" in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).</span></span>

-   <span data-ttu-id="cbd21-125">[PowerShell을 사용하여 SSRS를 관리하는 방법](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span><span class="sxs-lookup"><span data-stu-id="cbd21-125">[How to Administer SSRS using PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span></span>

## <a name="rsexe-scripting-samples"></a><span data-ttu-id="cbd21-126">RS.exe 스크립팅 샘플</span><span class="sxs-lookup"><span data-stu-id="cbd21-126">RS.exe scripting samples</span></span>

-   <span data-ttu-id="cbd21-127">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-127">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>

-   <span data-ttu-id="cbd21-128">추가 스크립트, 애플리케이션 및 확장 예에 대해서는 [SQL Server Reporting Services 제품 샘플](https://go.microsoft.com/fwlink/?LinkId=177889)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd21-128">For additional script, application, and extension examples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="see-also"></a><span data-ttu-id="cbd21-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbd21-129">See Also</span></span>
 <span data-ttu-id="cbd21-130">RS.exe 유틸리티 [는 rs.exe 유틸리티 및 웹 서비스를 사용 하](script-with-the-rs-exe-utility-and-the-web-service.md) 여 [배포 및 관리 작업](script-deployment-and-administrative-tasks.md) 스크립트를 [&#41;&#40;SSRS](rs-exe-utility-ssrs.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd21-130">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) [Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md)</span></span>


