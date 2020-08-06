---
title: Reporting Services의 전자 메일 배달 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9780a47b8e11f831f3a390829acdbd8ae935cf2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651462"
---
# <a name="e-mail-delivery-in-reporting-services"></a><span data-ttu-id="bdddb-102">Reporting Services의 전자 메일 배달</span><span class="sxs-lookup"><span data-stu-id="bdddb-102">E-Mail Delivery in Reporting Services</span></span>
  <span data-ttu-id="bdddb-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에는 개별 사용자 또는 그룹에 보고서를 메일로 보낼 수 있는 메일 배달 확장 프로그램이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes an e-mail delivery extension that provides a way to e-mail a report to individual users or groups.</span></span> <span data-ttu-id="bdddb-104">전자 메일 배달 확장 프로그램은 Reporting Services 구성 관리자를 통해 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 파일을 편집하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-104">The e-mail delivery extension is configured through the Reporting Services Configuration Manager and by editing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
 <span data-ttu-id="bdddb-105">보고서를 전자 메일로 배포하거나 받으려면 표준 구독 또는 데이터 기반 구독을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-105">To distribute or receive a report by e-mail, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="bdddb-106">한 번에 보고서 하나만 구독 또는 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-106">You can subscribe to or distribute only one report at a time.</span></span> <span data-ttu-id="bdddb-107">단일 전자 메일 메시지에 여러 보고서를 배달하는 구독을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-107">You cannot create a subscription that delivers multiple reports in a single e-mail message.</span></span> <span data-ttu-id="bdddb-108">구독에 대 한 자세한 내용은 [기본 모드&#41;에서 표준 구독 만들기, 수정 및 삭제 &#40;Reporting Services ](create-and-manage-subscriptions-for-native-mode-report-servers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bdddb-108">For more information about subscriptions, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="bdddb-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 모드 &#124; SharePoint 2010 및 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="bdddb-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013</span></span><br /><br /> <span data-ttu-id="bdddb-110">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드</span><span class="sxs-lookup"><span data-stu-id="bdddb-110">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
## <a name="e-mail-delivery-options"></a><span data-ttu-id="bdddb-111">전자 메일 배달 옵션</span><span class="sxs-lookup"><span data-stu-id="bdddb-111">E-Mail Delivery Options</span></span>  
 <span data-ttu-id="bdddb-112">보고서 서버 전자 메일 배달에서는 다음과 같은 방법으로 보고서를 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-112">Report server e-mail delivery can deliver reports in the following ways:</span></span>  
  
-   <span data-ttu-id="bdddb-113">생성된 보고서에 대한 알림 및 하이퍼링크를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-113">Send a notification and a hyperlink to the generated report.</span></span>  
  
-   <span data-ttu-id="bdddb-114">전자 메일 메시지의 제목: 줄에 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-114">Send a notification in the Subject: line of an e-mail message.</span></span> <span data-ttu-id="bdddb-115">기본적으로 구독 정의의 제목: 줄에는 구독 처리 시 보고서별 정보로 대체되는 다음과 같은 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-115">By default, the Subject: line in the subscription definition includes the following variables that are replaced by report-specific information when the subscription is processed:</span></span>  
  
     <span data-ttu-id="bdddb-116">**@ReportName**보고서의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-116">**@ReportName** specifies the name of the report.</span></span>  
  
     <span data-ttu-id="bdddb-117">**@ExecutionTime**보고서가 실행 된 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-117">**@ExecutionTime** specifies when the report was executed.</span></span>  
  
     <span data-ttu-id="bdddb-118">각 구독의 제목: 줄에서 이러한 변수를 정적 텍스트와 결합하거나 텍스트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-118">You can combine these variables with static text or modify the text in the Subject: line for each subscription.</span></span>  
  
-   <span data-ttu-id="bdddb-119">포함된 보고서 또는 첨부된 보고서를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-119">Send an embedded or attached report.</span></span> <span data-ttu-id="bdddb-120">렌더링 형식과 브라우저에 따라 보고서가 포함될지 또는 첨부될지가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-120">The rendering format and browser determine whether the report is embedded or attached.</span></span>  
  
     <span data-ttu-id="bdddb-121">브라우저에서 HTML 4.0 및 MHTML을 지원하고 웹 보관 파일 렌더링 형식을 선택한 경우 보고서는 메시지의 일부로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-121">If your browser supports HTML 4.0 and MHTML, and you choose the Web archive rendering format, the report is embedded as part of the message.</span></span> <span data-ttu-id="bdddb-122">CSV, PDF를 비롯한 다른 렌더링 형식은 모두 보고서를 첨부 파일로 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-122">All other rendering formats (CSV, PDF, and so on) deliver reports as attachments.</span></span> <span data-ttu-id="bdddb-123">이 기능은 RSReportServer 구성 파일에서 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-123">You can disable this functionality in the RSReportServer configuration file.</span></span>  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="bdddb-124">는 보고서를 보내기 전에 첨부 파일 또는 메시지의 크기를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-124">does not check the size of the attachment or message before sending the report.</span></span> <span data-ttu-id="bdddb-125">첨부 파일 또는 메시지가 메일 서버에서 허용하는 최대 제한을 초과할 경우 보고서가 배달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-125">If the attachment or message exceeds the maximum limit allowed by your mail server, the report is not delivered.</span></span> <span data-ttu-id="bdddb-126">큰 보고서의 경우 URL, 알림 등과 같은 다른 배달 옵션 중 하나를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="bdddb-126">Choose one of the other delivery options (such as URL or notification) if for large reports.</span></span>  
  
 <span data-ttu-id="bdddb-127">구독을 생성할 때 보고서 배달 방식을 결정하는 배달 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-127">You set delivery options that determine how a report is delivered when you create the subscription.</span></span> <span data-ttu-id="bdddb-128">예를 들어 구독에서 **링크 포함** 을 선택하면 메일 메시지에 보고서에 대한 하이퍼링크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-128">For example, if you select **Include Link** in the subscription, the e-mail message includes a hyperlink to the report.</span></span>  
  
## <a name="role-based-e-mail-settings"></a><span data-ttu-id="bdddb-129">역할 기반 전자 메일 설정</span><span class="sxs-lookup"><span data-stu-id="bdddb-129">Role-based E-Mail Settings</span></span>  
 <span data-ttu-id="bdddb-130">보고서를 구독할 때 적용되는 전자 메일 배달 설정은 역할에 "개별 구독 관리" 태스크가 포함되어 있는지 아니면 "모든 구독 관리" 작업이 포함되어 있는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-130">When you subscribe to a report, the e-mail delivery settings you work with vary depending on whether your role includes the "Manage individual subscriptions" task or the "Manage all subscriptions" task.</span></span>  
  
|<span data-ttu-id="bdddb-131">Task</span><span class="sxs-lookup"><span data-stu-id="bdddb-131">Task</span></span>|<span data-ttu-id="bdddb-132">사용 가능한 설정</span><span class="sxs-lookup"><span data-stu-id="bdddb-132">Available settings</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="bdddb-133">개별 구독 관리</span><span class="sxs-lookup"><span data-stu-id="bdddb-133">Manage individual subscriptions</span></span>|<span data-ttu-id="bdddb-134">사용자가 보고서 배달을 자동화하고 자신에게 보고서가 배달되도록 할 수 있는 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-134">Shows fields that enable a user to automate and deliver a report to himself or herself.</span></span> <span data-ttu-id="bdddb-135">이 모드에서는 전자 메일 별칭이 적용되는 필드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-135">In this mode, fields that accept e-mail aliases are not available.</span></span>|  
|<span data-ttu-id="bdddb-136">모든 구독 관리</span><span class="sxs-lookup"><span data-stu-id="bdddb-136">Manage all subscriptions</span></span>|<span data-ttu-id="bdddb-137">받는 사람:, 참조:, 숨은 참조: 및 회신: 필드를 비롯하여 보다 폭넓은 배포를 지원하는 필드를 표시하여 보고서를 더 많은 구독자에게 라우팅하는 추가 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-137">Shows fields that support wider distribution, including To:, Cc:, Bcc:, and Reply-To: fields, providing more ways to route a report to more subscribers.</span></span> <span data-ttu-id="bdddb-138">전자 메일 별칭 필드의 사용 여부는 RSReportServer 구성 파일 설정을 통해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-138">The availability of e-mail alias fields is defined through the RSReportServer configuration file settings.</span></span>|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a><span data-ttu-id="bdddb-139">구독에 전자 메일 주소 지정</span><span class="sxs-lookup"><span data-stu-id="bdddb-139">Specifying E-Mail Addresses in a Subscription</span></span>  
 <span data-ttu-id="bdddb-140">인트라넷 내에서 보고서를 배포하고 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange 서버에 대한 SMTP 게이트웨이를 사용하는 경우 동료에게 전자 메일을 보낼 때처럼 전자 메일 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-140">If you are distributing reports within an intranet and you are using an SMTP gateway to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange server, type the e-mail alias (as if you were sending e-mail to a coworker).</span></span> <span data-ttu-id="bdddb-141">외부 전자 메일 계정에 배달할 경우 전체 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-141">If delivery is to an external e-mail account, type the full e-mail address.</span></span> <span data-ttu-id="bdddb-142">추가 전자 메일 주소를 지정하여 구독에 다른 구독자를 추가하면 이 구독에서 생성된 보고서의 복사본이 해당 구독자에게 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-142">If you specify more e-mail addresses to add others to your subscription, subscribers get an exact copy of the report that is produced from this subscription.</span></span>  
  
 <span data-ttu-id="bdddb-143">보고서 서버는 전자 메일 주소의 유효성을 검사하거나 전자 메일 서버로부터 전자 메일 주소를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-143">The report server does not validate e-mail addresses or obtain e-mail addresses from an e-mail server.</span></span> <span data-ttu-id="bdddb-144">따라서 사용할 전자 메일 주소를 미리 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-144">You must know in advance which e-mail addresses you want to use.</span></span> <span data-ttu-id="bdddb-145">기본적으로 조직의 내부 또는 외부에 있는 유효한 모든 전자 메일 계정에 전자 메일로 보고서를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-145">By default, you can e-mail reports to any valid e-mail account within or outside of your organization.</span></span> <span data-ttu-id="bdddb-146">그러나 구성 설정을 사용하면 이름이 식별된 메일 서버 호스트에만 전자 메일을 배달하도록 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-146">Configuration settings can be used, however, to restrict e-mail delivery to mail server hosts that you identify by name.</span></span> <span data-ttu-id="bdddb-147">조직의 멤버가 아닌 사용자에게 전자 메일을 배달하려면 추가 호스트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-147">You can specify additional hosts if you want to support e-mail delivery to people that are not members of your organization.</span></span>  
  
 <span data-ttu-id="bdddb-148">보고서를 배달하는 데 사용되는 전자 메일 메시지는 전자 메일 서버에 정의된 전자 메일 계정으로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-148">The e-mail message used to deliver the report must be sent from an e-mail account that is defined on the e-mail server.</span></span> <span data-ttu-id="bdddb-149">구성 설정에서 전자 메일 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-149">A configuration setting specifies the e-mail account.</span></span> <span data-ttu-id="bdddb-150">전자 메일 계정은 전자 메일 배달 확장 프로그램에서 배달되는 모든 보고서에 사용되기 때문에 여러 계정을 지정하거나 개별 보고서의 계정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-150">The e-mail account is used for all reports delivered by the e-mail delivery extension; you cannot specify multiple accounts or vary the account for individual reports.</span></span>  
  
## <a name="e-mail-server-configuration"></a><span data-ttu-id="bdddb-151">전자 메일 서버 구성</span><span class="sxs-lookup"><span data-stu-id="bdddb-151">E-Mail Server Configuration</span></span>  
 <span data-ttu-id="bdddb-152">보고서 서버는 표준 연결을 통해 전자 메일 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-152">The report server connects with an e-mail server through a standard connection.</span></span> <span data-ttu-id="bdddb-153">SSL(Secure Sockets Layer)을 통해 암호화된 통신은 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-153">It does not use communication that has been encrypted using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="bdddb-154">전자 메일 서버는 보고서 서버와 동일한 네트워크에 있는 원격 또는 로컬 SMTP(Simple Mail Transport Protocol) 서버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdddb-154">The e-mail server must be a remote or local Simple Mail Transport Protocol (SMTP) server on the same network as the report server.</span></span>  
  
 <span data-ttu-id="bdddb-155">기본 모드 보고서 서버를 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bdddb-155">For information on how to configure a native mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="bdddb-156">SSRS Configuration Manager &#40;전자 메일 배달에 대 한 보고서 서버 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="bdddb-156">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [<span data-ttu-id="bdddb-157">전자 메일 설정-Configuration Manager &#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="bdddb-157">E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;</span></span>](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 <span data-ttu-id="bdddb-158">SharePoint 모드 보고서 서버를 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bdddb-158">For information on how to configure a SharePoint mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="bdddb-159">Reporting Services 서비스 애플리케이션에 대한 메일 구성&#40;SharePoint 2010 및 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="bdddb-159">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="bdddb-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdddb-160">See Also</span></span>  
 <span data-ttu-id="bdddb-161">[태스크 및 권한](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="bdddb-161">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="bdddb-162">[구독 및 배달&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="bdddb-162">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="bdddb-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="bdddb-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="bdddb-164">역할 할당</span><span class="sxs-lookup"><span data-stu-id="bdddb-164">Role Assignments</span></span>](../security/role-assignments.md)  
  
  
