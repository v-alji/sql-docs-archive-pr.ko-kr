---
title: 전자 메일 설정-Configuration Manager (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732439"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a><span data-ttu-id="5847f-102">전자 메일 설정 - 구성 관리자(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="5847f-102">E-mail Settings - Configuration Manager (SSRS Native Mode)</span></span>
  <span data-ttu-id="5847f-103">이 페이지에서는 보고서 서버에서 보고서 서버 전자 메일 배달을 가능하게 하는 SMTP(Simple Mail Transport Protocol) 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-103">Use this page to specify Simple Mail Transport Protocol (SMTP) settings that enable report server e-mail delivery from the report server.</span></span> <span data-ttu-id="5847f-104">보고서 서버 전자 메일 배달 확장 프로그램을 사용하여 전자 메일 구독을 통해 보고서 또는 보고서 처리 알림을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-104">You can use the Report Server E-Mail delivery extension to distribute reports or report processing notifications through e-mail subscriptions.</span></span> <span data-ttu-id="5847f-105">보고서 서버 전자 메일 배달 확장 프로그램을 사용하려면 SMTP 서버 및 보낸 사람 주소: 필드에 사용할 전자 메일 주소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-105">The Report Server E-Mail delivery extension requires an SMTP server and an e-mail address to use in the From: field.</span></span>  
  
 <span data-ttu-id="5847f-106">메일 서버 호스트 및 렌더링 확장 프로그램 가용성을 제한하는 설정을 포함한 추가 구성 설정을 사용하여 전자 메일 구독을 추가로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-106">Additional configuration settings can be used to further customize e-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability.</span></span> <span data-ttu-id="5847f-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자에서는 이러한 설정을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-107">You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="5847f-108">추가 설정을 구성하려면 RSReportServer.config 파일을 직접 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-108">To configure the additional settings, you must manually edit the RSReportServer.config file.</span></span> <span data-ttu-id="5847f-109">자세한 내용은 온라인 설명서에서 [전자 메일 배달을 위한 보고서 서버 구성 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 및 [Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) 을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5847f-109">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="5847f-110">이 페이지를 열려면 Reporting Services 구성 관리자를 시작한 다음 탐색 창에서 **전자 메일 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-110">To open this page, start the Reporting Services Configuration Manager and click **E-mail Settings** in the navigation pane.</span></span> <span data-ttu-id="5847f-111">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5847f-111">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="5847f-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5847f-113">옵션</span><span class="sxs-lookup"><span data-stu-id="5847f-113">Options</span></span>  
 <span data-ttu-id="5847f-114">**보낸 사람 주소**</span><span class="sxs-lookup"><span data-stu-id="5847f-114">**Sender Address**</span></span>  
 <span data-ttu-id="5847f-115">생성된 전자 메일의 보낸 사람: 필드에 사용할 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-115">Specifies the e-mail address to use in the From: field of a generated e-mail.</span></span> <span data-ttu-id="5847f-116">SMTP 서버에서 메일을 보낼 수 있는 권한이 있는 사용자 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-116">You must specify a user account that has permission to send mail from the SMTP server.</span></span>  
  
 <span data-ttu-id="5847f-117">**현재 SMTP 배달 방법**</span><span class="sxs-lookup"><span data-stu-id="5847f-117">**Current SMTP Delivery Method**</span></span>  
 <span data-ttu-id="5847f-118">보고서 서버 전자 메일이 SMTP 서버를 통해 라우팅되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-118">Specifies that report server e-mail is routed through an SMTP server.</span></span> <span data-ttu-id="5847f-119">Reporting Services 구성 관리자에서는 이 배달 방법만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-119">This is the only delivery method that you can specify in the Reporting Services Configuration Manager.</span></span>  
  
 <span data-ttu-id="5847f-120">다른 배달 방법으로는 로컬 SMTP 서비스 픽업 디렉터리를 사용하는 방법이 있으며</span><span class="sxs-lookup"><span data-stu-id="5847f-120">An alternative delivery method is to use a local SMTP service pickup directory.</span></span> <span data-ttu-id="5847f-121">이는 네트워크 SMTP 서비스를 사용할 수 없는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-121">You can use this delivery method if a network SMTP service is not available.</span></span> <span data-ttu-id="5847f-122">로컬 SMTP 서비스 픽업 디렉터리를 지정하려면 RSReportServer.config 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-122">To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="5847f-123">구성 파일을 편집하여 로컬 SMTP 서비스 픽업 디렉터리를 사용할 경우 Reporting Services 구성 관리자에서는 **현재 배달 방법** 옵션을 *사용자 지정* 으로 설정하여 구성 파일에 배달 방법이 지정되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-123">If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.</span></span>  
  
 <span data-ttu-id="5847f-124">`SendUsing` 구성 설정을 통해 구성 파일에서 배달 방법을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-124">In the configuration file, the delivery method is set through the `SendUsing` configuration setting.</span></span> <span data-ttu-id="5847f-125">설정을 지정 하는 방법에 대 한 자세한 내용은 `SendUsing` [SSRS Configuration Manager&#41;&#40;전자 메일 배달에 대 한 보고서 서버 구성 ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5847f-125">For more information about specifying the `SendUsing` setting, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="5847f-126">**SMTP 서버**</span><span class="sxs-lookup"><span data-stu-id="5847f-126">**SMTP Server**</span></span>  
 <span data-ttu-id="5847f-127">사용할 SMTP 서버 또는 게이트웨이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-127">Specify the SMTP server or gateway to use.</span></span> <span data-ttu-id="5847f-128">네트워크에서 로컬 서버나 SMTP 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5847f-128">You can use a local server or an SMTP server on your network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5847f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5847f-129">See Also</span></span>  
 <span data-ttu-id="5847f-130">[SSRS Configuration Manager &#40;전자 메일 배달에 대 한 보고서 서버 구성&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5847f-130">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="5847f-131">Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="5847f-131">Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
