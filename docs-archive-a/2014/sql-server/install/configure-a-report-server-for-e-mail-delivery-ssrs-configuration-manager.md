---
title: 전자 메일 배달을 위한 보고서 서버 구성 (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652560"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a><span data-ttu-id="bb944-102">전자 메일 배달을 위한 보고서 서버 구성(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="bb944-102">Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)</span></span>


  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="bb944-103">에는 전자 메일을 통해 보고서를 배포할 수 있는 전자 메일 배달 확장 프로그램이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-103">includes an e-mail delivery extension so that you can distribute reports through e-mail.</span></span> <span data-ttu-id="bb944-104">전자 메일 구독을 정의하는 방법에 따라 배달은 알림, 링크, 첨부 파일 또는 포함된 보고서로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-104">Depending on how you define the e-mail subscription, a delivery might consist of a notification, link, attachment, or embedded report.</span></span> <span data-ttu-id="bb944-105">전자 메일 배달 확장 프로그램은 기존 메일 서버 기술을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-105">The e-mail delivery extension works with your existing mail server technology.</span></span> <span data-ttu-id="bb944-106">메일 서버는 SMTP 서버 또는 전달자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-106">The mail server must be an SMTP server or forwarder.</span></span> <span data-ttu-id="bb944-107">보고서 서버는 운영 체제에서 제공하는 CDO(Collaboration Data Objects) 라이브러리(cdosys.dll)를 통해 SMTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-107">The report server connects to an SMTP server through Collaboration Data Objects (CDO) libraries (cdosys.dll) that are provided by the operating system.</span></span>  
  
 <span data-ttu-id="bb944-108">보고서 서버 전자 메일 배달 확장 프로그램은 기본적으로 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-108">The report server e-mail delivery extension is not configured by default.</span></span> <span data-ttu-id="bb944-109">따라서 Reporting Services 구성 관리자를 사용하여 확장 프로그램을 최소한으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-109">You must use the Reporting Services Configuration Manager to minimally configure the extension.</span></span> <span data-ttu-id="bb944-110">고급 속성을 설정하려면 `RSReportServer.config` 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-110">To set advanced properties, you must edit the `RSReportServer.config` file.</span></span> <span data-ttu-id="bb944-111">이 확장 프로그램을 사용할 수 있도록 보고서 서버를 구성할 수 없는 경우에는 보고서를 공유 폴더로 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-111">If you cannot configure the report server to use this extension, you can deliver reports to a shared folder instead.</span></span> <span data-ttu-id="bb944-112">자세한 내용은 [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb944-112">For more information, see [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="bb944-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드</span><span class="sxs-lookup"><span data-stu-id="bb944-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a><span data-ttu-id="bb944-114">구성 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bb944-114">Configuration Requirements</span></span>  
  
-   <span data-ttu-id="bb944-115">보고서 서버 전자 메일 배달은 CDO(Collaboration Data Object)에 구현되며 로컬 또는 원격 SMTP(Simple Mail Transfer Protocol) 서버나 SMTP 전달자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-115">Report server e-mail delivery is implemented on Collaboration Data Objects (CDO) and requires a local or remote Simple Mail Transfer Protocol (SMTP) server or SMTP forwarder.</span></span> <span data-ttu-id="bb944-116">SMTP를 지원하지 않는 운영 체제도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-116">SMTP is not supported on all Windows operating systems.</span></span> <span data-ttu-id="bb944-117">Windows Server 2008의 Itanium 기반 버전을 사용하는 경우 SMTP가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-117">If you are using the Itanium-based edition of Windows Server 2008, SMTP is not supported.</span></span> <span data-ttu-id="bb944-118">CDO를 통해 제공되는 구성 옵션에 대한 자세한 내용은 MSDN에서 [CoClass 구성(Configuration CoClass)](https://go.microsoft.com/fwlink/?LinkId=98237) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bb944-118">For more information about configuration options provided through CDO, see [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) on MSDN.</span></span>  
  
-   <span data-ttu-id="bb944-119">메일을 보내려면 보고서 서버 서비스 계정이 SMTP 서버에 대한 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-119">The Report Server service account must have permission on the SMTP server to send mail.</span></span>  
  
-   <span data-ttu-id="bb944-120">전자 메일 배달 확장 프로그램은 전자 메일 첨부 파일에 UTF-8 인코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-120">The e-mail delivery extension uses UTF-8 encoding in e-mail attachments.</span></span> <span data-ttu-id="bb944-121">HTML 렌더링 확장 프로그램에서 UTF-8만 지원하기 때문에 인코딩은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-121">You cannot modify the encoding; the HTML rendering extension only supports UTF-8.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb944-122">기본 전자 메일 배달 확장 프로그램은 디지털 서명 또는 보내는 메일 메시지 암호화를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-122">The default e-mail delivery extension does not provide support for digitally signing or encrypting outgoing mail messages.</span></span>  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a><span data-ttu-id="bb944-123">로컬 또는 원격 SMTP 서비스를 위한 보고서 서버 구성</span><span class="sxs-lookup"><span data-stu-id="bb944-123">Configuring a Report Server for Local or Remote SMTP Service</span></span>  
 <span data-ttu-id="bb944-124">로컬 SMTP 서비스나 원격 SMTP 서버 또는 전달자를 사용하여 전자 메일 배달을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-124">You can use a local SMTP service or a remote SMTP server or forwarder to support e-mail delivery.</span></span> <span data-ttu-id="bb944-125">기존 원격 SMTP 서버에 대한 액세스 권한이 있을 경우 이 서버를 사용할 것을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-125">If you have access to an existing remote SMTP server, you should consider using it.</span></span> <span data-ttu-id="bb944-126">사용할 수 있는 SMTP 서버가 없거나 이후에 컴퓨터 연결 실패의 원인이 될 수 있는 보고서 배달 오류가 발생할 경우 로컬 SMTP 서비스를 사용하도록 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-126">If there is no SMTP server available or if you subsequently encounter report delivery errors that can be attributed to computer connection failures, you should switch to using a local SMTP service.</span></span> <span data-ttu-id="bb944-127">로컬 또는 원격 서비스를 위해 보고서 서버를 구성하는 방법에 대해서는 이 항목의 뒷부분에서 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-127">Details about how to configure a report server for local or remote service are provided further on in this topic.</span></span>  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a><span data-ttu-id="bb944-128">전자 메일 배달을 위한 구성 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bb944-128">Setting Configuration Options for E-Mail Delivery</span></span>  
 <span data-ttu-id="bb944-129">보고서 서버 전자 메일 배달을 사용하려면 먼저 사용할 SMTP 서버에 대한 정보를 제공하는 구성 값을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-129">Before you can use Report Server e-mail delivery, you must set configuration values that provide information about which SMTP server to use.</span></span>  
  
 <span data-ttu-id="bb944-130">전자 메일 배달을 위한 보고서 서버를 구성하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-130">To configure a report server for e-mail delivery, do the following:</span></span>  
  
-   <span data-ttu-id="bb944-131">SMTP 서버와 전자 메일을 보낼 수 있는 권한이 있는 사용자 계정만 지정하는 경우 Reporting Services 구성 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-131">Use the Reporting Services Configuration Manager if you are specifying just an SMTP server and a user account that has permission to send e-mail.</span></span> <span data-ttu-id="bb944-132">이는 보고서 서버 전자 메일 배달 확장 프로그램을 구성하는 데 필요한 최소 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-132">These are the minimum settings that are required for configuring the Report Server e-mail delivery extension.</span></span> <span data-ttu-id="bb944-133">자세한 내용은 [전자 메일 설정-Configuration Manager &#40;SSRS 기본 모드&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) 및 [전자 메일 배달 Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb944-133">For more information, see [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) and [E-Mail Delivery in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="bb944-134">텍스트 편집기를 사용하여 RSreportserver.config 파일에 추가 설정을 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="bb944-134">(Optionally) Use a text editor to specify additional settings in the RSreportserver.config file.</span></span> <span data-ttu-id="bb944-135">이 파일에는 보고서 서버 전자 메일 배달을 위한 모든 구성 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-135">This file contains all of the configuration settings for Report Server e-mail delivery.</span></span> <span data-ttu-id="bb944-136">로컬 SMTP 서버를 사용하거나 전자 메일 배달을 특정 호스트로 제한하는 경우 이러한 파일에 추가 설정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-136">Specifying additional settings in these files is required if you are using a local SMTP server or if you are restricting e-mail delivery to specific hosts.</span></span> <span data-ttu-id="bb944-137">구성 파일을 찾아서 수정 하는 방법에 대 한 자세한 내용은 SQL Server 온라인 설명서의 [RSreportserver.config&#41;&#40;Reporting Services 구성 파일 수정](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb944-137">For more information about finding and modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb944-138">보고서 서버 전자 메일 설정은 CDO를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-138">Report server e-mail settings are based on CDO.</span></span> <span data-ttu-id="bb944-139">특정 설정에 대한 세부 정보를 보려면 CDO 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bb944-139">If you want more detail about specific settings, you can refer to the CDO production documentation.</span></span>  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a><span data-ttu-id="bb944-140">보고서 서버 전자 메일 구성 예제</span><span class="sxs-lookup"><span data-stu-id="bb944-140">Example Report Server E-Mail Configuration</span></span>  
 <span data-ttu-id="bb944-141">다음 예에서는 원격 SMTP 서버에 대한 RSreportserver.config 파일 설정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-141">The following example illustrates the settings in the RSreportserver.config file for a remote SMTP server.</span></span> <span data-ttu-id="bb944-142">설정에 대한 설명 및 유효한 값에 대한 자세한 내용은 [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 온라인 설명서의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl온라인 설명서의e or the CDO product documentation.</span><span class="sxs-lookup"><span data-stu-id="bb944-142">To read about the setting descriptions and valid values, see [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or the CDO product documentation.</span></span>  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a><span data-ttu-id="bb944-143">메시지의 To: Field를 설정 하기 위한 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="bb944-143">Configuration Options for Setting the To: Field in a Message</span></span>  
 <span data-ttu-id="bb944-144">**개별 구독 관리** 태스크에 의해 부여 된 권한에 따라 만들어진 사용자 정의 구독에는 도메인 사용자 계정을 기반으로 하는 미리 설정 된 사용자 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-144">User-defined subscriptions that are created according to the permissions granted by the **Manage individual subscriptions** task contain a pre-set user name that is based on the domain user account.</span></span> <span data-ttu-id="bb944-145">사용자가 구독을 생성할 때 구독을 생성하는 사람의 도메인 사용자 계정이 **받는 사람:** 필드의 수신자 이름으로 자동으로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-145">When the user creates the subscription, the recipient name in the **To:** field is self-addressed using the domain user account of the person creating the subscription.</span></span>  
  
 <span data-ttu-id="bb944-146">도메인 사용자 계정과는 다른 전자 메일 계정을 사용하는 SMTP 서버 또는 전달자를 사용하는 경우 SMTP 서버가 보고서를 해당 사용자에게 배달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-146">If you are using an SMTP server or forwarder that uses e-mail accounts that are different from the domain user account, the report delivery will fail when the SMTP server tries to deliver the report to that user.</span></span>  
  
 <span data-ttu-id="bb944-147">이 문제를 해결하려면 사용자가 **받는 사람:** 필드에 이름을 입력할 수 있도록 구성 설정을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-147">To workaround this issue, you can modify configuration settings that allow users to enter a name in the **To:** field:</span></span>  
  
1.  <span data-ttu-id="bb944-148">텍스트 편집기에서 RSReportServer.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-148">Open RSReportServer.config with a text editor.</span></span>  
  
2.  <span data-ttu-id="bb944-149">`SendEmailToUserAlias`를 `False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-149">Set `SendEmailToUserAlias` to `False`.</span></span>  
  
3.  <span data-ttu-id="bb944-150">`DefaultHostName` 을 DNS(Domain Name System) 이름이나 SMTP 서버 또는 전달자의 IP 주소로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-150">Set `DefaultHostName` to the Domain Name System (DNS) name or IP address of the SMTP server or forwarder.</span></span>  
  
4.  <span data-ttu-id="bb944-151">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-151">Save the file.</span></span>  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a><span data-ttu-id="bb944-152">원격 SMTP 서비스에 대 한 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="bb944-152">Configuration Options for Remote SMTP Service</span></span>  
 <span data-ttu-id="bb944-153">보고서 서버와 SMTP 서버 또는 전달자 간의 연결은 다음과 같은 구성 설정에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-153">The connection between the report server and an SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="bb944-154">`SendUsing` 은 메시지를 보내는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-154">`SendUsing` specifies a method for sending messages.</span></span> <span data-ttu-id="bb944-155">네트워크 SMTP 서비스나 로컬 SMTP 서비스 선택 디렉터리 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-155">You can choose between a network SMTP service or a local SMTP service pickup directory.</span></span> <span data-ttu-id="bb944-156">원격 SMTP 서비스를 사용하려면 RSReportServer.config 파일에서 이 값을 **2** 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-156">To use a remote SMTP service, this value must be set to **2** in the RSReportServer.config file.</span></span>  
  
-   <span data-ttu-id="bb944-157">`SMTPServer` 는 원격 SMTP 서버 또는 전달자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-157">`SMTPServer` specifies the remote SMTP server or forwarder.</span></span> <span data-ttu-id="bb944-158">이 값은 원격 SMTP 서버 또는 전달자를 사용할 때 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-158">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
-   <span data-ttu-id="bb944-159">`From`전자 메일 메시지의 **보낸 사람:** 줄에 표시 되는 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-159">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="bb944-160">이 값은 원격 SMTP 서버 또는 전달자를 사용할 때 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-160">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
 <span data-ttu-id="bb944-161">원격 SMTP 서비스에 사용되는 기타 값은 다음과 같습니다. 기본값을 재설정하지 않으려면 이 값을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-161">Other values that are used for remote SMTP service include the following (note that you do not need to specify these values unless you want to override the default values).</span></span>  
  
-   <span data-ttu-id="bb944-162">**SMTPServerPort** 는 포트 25에 대해 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-162">**SMTPServerPort** is configured for port 25.</span></span>  
  
-   <span data-ttu-id="bb944-163">**SMTPAuthenticate** 는 보고서 서버에서 원격 SMTP 서버에 연결하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-163">**SMTPAuthenticate** specifies how the report server connects to the remote SMTP server.</span></span> <span data-ttu-id="bb944-164">기본값은 0(인증 없음)입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-164">The default value is 0 (or no authentication).</span></span> <span data-ttu-id="bb944-165">이 경우 익명 액세스를 통해 연결이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-165">In this case, the connection is made through Anonymous access.</span></span> <span data-ttu-id="bb944-166">도메인 구성에 따라 보고서 서버와 SMTP 서버가 동일한 도메인의 멤버여야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-166">Depending on your domain configuration, the report server and the SMTP server may need to be members of the same domain.</span></span>  
  
     <span data-ttu-id="bb944-167">제한된 메일 그룹(예: 인증된 계정에서 보낸 메시지만 허용하는 메일 그룹)에 전자 메일을 보내려면 **SMTPAuthenticate** 를 **2**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-167">To send e-mail to restricted distribution lists (for example, distribution lists that accept incoming messages only from authenticated accounts), set **SMTPAuthenticate** to **2**.</span></span>  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a><span data-ttu-id="bb944-168">로컬 SMTP 서비스에 대 한 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="bb944-168">Configuration Options for Local SMTP Service</span></span>  
 <span data-ttu-id="bb944-169">보고서 서버 전자 메일 배달을 테스트하거나 문제를 해결하려면 로컬 SMTP 서비스를 구성하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-169">Configuring a local SMTP service is useful if you are testing or troubleshooting report server e-mail delivery.</span></span> <span data-ttu-id="bb944-170">로컬 SMTP 서비스는 기본적으로 활성화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-170">The local SMTP service is not enabled by default.</span></span> <span data-ttu-id="bb944-171">이 기능을 사용 하도록 설정 하는 방법에 대 한 지침은 [메일 배달을 위한 보고서 서버 구성 (ssrs Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 및 [전자 메일 설정-Configuration Manager &#40;SSRS 기본 모드&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb944-171">For instructions on how to enable it, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="bb944-172">보고서 서버와 로컬 SMTP 서버 또는 전달자 간의 연결은 다음과 같은 구성 설정에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-172">The connection between the report server and a local SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="bb944-173">`SendUsing`가 **1**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-173">`SendUsing` is set to **1**.</span></span>  
  
-   <span data-ttu-id="bb944-174">**SMTPServerPickupDirectory** 를 로컬 드라이브의 폴더로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-174">**SMTPServerPickupDirectory** is set to a folder on the local drive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb944-175">`SMTPServer`로컬 SMTP 서버를 사용 하는 경우를 설정 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-175">Be sure that you do not set `SMTPServer` if you are using a local SMTP server.</span></span>  
  
-   <span data-ttu-id="bb944-176">`From`전자 메일 메시지의 **보낸 사람:** 줄에 표시 되는 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-176">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="bb944-177">이 값은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-177">This value is required.</span></span>  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a><span data-ttu-id="bb944-178">Reporting Services 구성 관리자를 사용 하 여 보고서 서버 전자 메일을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="bb944-178">To configure report server e-mail using the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="bb944-179"> 보고서 서버 Windows 서비스에 SMTP 서버에 대한 `Send As` 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-179">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="bb944-180">Reporting Services 구성 관리자를 시작한 후 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-180">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span>  
  
3.  <span data-ttu-id="bb944-181">전자 메일 설정 페이지에서 SMTP 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-181">On the Email Settings page, enter the name of the SMTP server.</span></span> <span data-ttu-id="bb944-182">이 값은 IP 주소, 회사 인트라넷에 있는 컴퓨터의 UNC 이름 또는 정규화된 도메인 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-182">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
4.  <span data-ttu-id="bb944-183">**보낸 사람 주소**에 SMTP 서버에서 전자 메일을 보낼 수 있는 권한이 있는 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-183">In **Sender Address**, enter the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
5.  <span data-ttu-id="bb944-184">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-184">Click **Apply**.</span></span>  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a><span data-ttu-id="bb944-185">보고서 서버에 대해 원격 SMTP 서비스를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="bb944-185">To configure a remote SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="bb944-186"> 보고서 서버 Windows 서비스에 SMTP 서버에 대한 `Send As` 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-186">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="bb944-187">텍스트 편집기에서 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-187">Open the RSReportServer.config file in a text editor.</span></span>  
  
3.  <span data-ttu-id="bb944-188"><`UrlRoot`>이 보고서 서버 URL 주소로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-188">Verify that <`UrlRoot`> is set to the report server URL address.</span></span> <span data-ttu-id="bb944-189">이 값은 보고서 서버를 구성할 때 설정되므로 이미 채워져 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-189">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="bb944-190">그렇지 않으면 보고서 서버 URL 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-190">If it is not set, type the report server URL address.</span></span>  
  
4.  <span data-ttu-id="bb944-191">배달 섹션에서 <>를 찾습니다 `ReportServerEmail` .</span><span class="sxs-lookup"><span data-stu-id="bb944-191">In the Delivery section, find <`ReportServerEmail`>.</span></span>  
  
5.  <span data-ttu-id="bb944-192"><`SMTPServer`>에서 SMTP 서버의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-192">In <`SMTPServer`>, type the name of the SMTP server.</span></span> <span data-ttu-id="bb944-193">이 값은 IP 주소, 회사 인트라넷에 있는 컴퓨터의 UNC 이름 또는 정규화된 도메인 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-193">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
6.  <span data-ttu-id="bb944-194"><`SendUsing`>이 2로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-194">Verify that <`SendUsing`> is set to 2.</span></span> <span data-ttu-id="bb944-195">다른 값으로 설정되어 있으면 보고서 서버에서 원격 SMTP 서비스를 사용하도록 구성되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-195">If it is set another value, the report server is not configured to use a remote SMTP service.</span></span>  
  
7.  <span data-ttu-id="bb944-196"><`From`>에서 SMTP 서버에서 전자 메일을 보낼 수 있는 권한이 있는 계정의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-196">In <`From`>, type the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
8.  <span data-ttu-id="bb944-197">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-197">Save the file.</span></span>  
  
     <span data-ttu-id="bb944-198">보고서 서버가 자동으로 새 설정을 사용하므로 서비스를 다시 시작할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-198">The report server will use the new settings automatically; you do not need to restart the service.</span></span> <span data-ttu-id="bb944-199">추가 SMTP 설정을 지정하여 보고서 서버 전자 메일 배달에 SMTP 서버가 사용되는 방법을 추가로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-199">You can specify additional SMTP settings to further configure how the SMTP server is used for report server e-mail delivery.</span></span> <span data-ttu-id="bb944-200">자세한 내용은 [Configur온라인 설명서의g a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 및 [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 온라인 설명서의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl온라인 설명서의e.</span><span class="sxs-lookup"><span data-stu-id="bb944-200">For more information, see [Configuring a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a><span data-ttu-id="bb944-201">보고서 서버에 대해 로컬 SMTP 서비스를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="bb944-201">To configure a local SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="bb944-202">제어판에서 **프로그램 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-202">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="bb944-203">**Windows 구성 요소 추가/제거** 를 클릭하여 Windows 구성 요소 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-203">Click **Add/Remove Windows Components** to start the Windows Component Wizard.</span></span>  
  
3.  <span data-ttu-id="bb944-204">**애플리케이션 서버** 를 선택하고 **자세히**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-204">Select **Application Server** and click **Details**.</span></span>  
  
4.  <span data-ttu-id="bb944-205">**인터넷 정보 서비스(IIS)** 를 선택하고 **자세히**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-205">Select **Internet Information Services (IIS)** and click **Details**.</span></span>  
  
5.  <span data-ttu-id="bb944-206">**SMTP 서비스** 확인란을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-206">Select the **SMTP Service** checkbox and click **OK**.</span></span>  
  
6.  <span data-ttu-id="bb944-207">Windows 구성 요소 마법사에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-207">On the Windows Component Wizard, click **Next**.</span></span> <span data-ttu-id="bb944-208">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-208">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="bb944-209">서비스가 **서비스** 콘솔에서 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-209">Verify that the service is running in the **Services** console.</span></span>  
  
8.  <span data-ttu-id="bb944-210">텍스트 편집기에서 **RSReportServer.config** 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-210">Open the **RSReportServer.config** file in a text editor.</span></span>  
  
9. <span data-ttu-id="bb944-211">`<UrlRoot>` 가 보고서 서버 URL 주소로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-211">Verify that `<UrlRoot>` is set to the report server URL address.</span></span> <span data-ttu-id="bb944-212">이 값은 보고서 서버를 구성할 때 설정되므로 이미 채워져 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-212">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="bb944-213">그렇지 않으면 보고서 서버 URL 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-213">If it is not set, type the report server URL address.</span></span>  
  
10. <span data-ttu-id="bb944-214"> 배달 섹션에서 `<ReportServerEmail>.`을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-214">In the Delivery section, find `<ReportServerEmail>.`</span></span>  
  
11. <span data-ttu-id="bb944-215">`<SMTPServer>`에서 이 설정의 모든 값을 지웁니다. 이때 태그는 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-215">In `<SMTPServer>`, clear any values for this setting, but do not delete the tags.</span></span>  
  
12. <span data-ttu-id="bb944-216">`<SendUsing>` 을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-216">Set `<SendUsing>` to 1.</span></span> <span data-ttu-id="bb944-217">다른 값으로 설정되어 있으면 보고서 서버에서 로컬 SMTP 서비스를 사용하도록 구성되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-217">If it is set another value, the report server is not configured to use a local SMTP service.</span></span>  
  
13. <span data-ttu-id="bb944-218">`<SMTPServerPickupDirectory>` 를 로컬 드라이브의 폴더로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-218">Set `<SMTPServerPickupDirectory>` to a folder on the local drive.</span></span>  
  
14. <span data-ttu-id="bb944-219">`<From>` 을 SMTP 서버에서 전자 메일을 보낼 수 있는 권한이 있는 계정으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-219">Set `<From>` to an account that has permission to send e-mail from the SMTP server.</span></span>  
  
15. <span data-ttu-id="bb944-220">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb944-220">Save the file.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="bb944-221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb944-221">See Also</span></span>  
 [<span data-ttu-id="bb944-222">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="bb944-222">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
