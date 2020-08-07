---
title: 기본 Reporting Services 배달 확장 프로그램 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734920"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a><span data-ttu-id="5c09c-102">기본 Reporting Services 배달 확장 프로그램 변경</span><span class="sxs-lookup"><span data-stu-id="5c09c-102">Change the Default Reporting Services Delivery Extension</span></span>
  <span data-ttu-id="5c09c-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 설정을 수정하여 구독 정의 페이지의 **배달 방법** 목록에 표시될 배달 확장 프로그램을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-103">You can modify [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration settings to change the default delivery extension that appears in the **Delivered by** list of a subscription definition page.</span></span> <span data-ttu-id="5c09c-104">예를 들어, 구성을 수정하여 사용자가 새 구독을 만들었을 때 전자 메일 배달 대신 기본적으로 파일 공유 전달을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-104">For example you can modify the configuration so that when users create a new subscription, file share delivery is selected by default instead of e-mail delivery.</span></span> <span data-ttu-id="5c09c-105">또한 배달 확장 프로그램이 사용자 인터페이스에 나열되는 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-105">You can also change the order the delivery extensions are listed in the user interface.</span></span>

 <span data-ttu-id="5c09c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="5c09c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5c09c-107">는 메일 및 Windows 파일 공유 배달을 포함하는 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-107">includes E-mail and Windows File Share delivery are extensions.</span></span> <span data-ttu-id="5c09c-108">사용자 지정 배달을 지원하기 위해 사용자 지정 확장 프로그램이나 타사 확장 프로그램을 배포한 경우에는 보고서 서버에 배달 확장 프로그램이 더 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-108">Your report server might have additional delivery extensions if you have deployed custom or third-party extensions to support custom delivery.</span></span> <span data-ttu-id="5c09c-109">배달 확장 프로그램의 가용성은 보고서 서버에 배포되었는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-109">The availability of a delivery extension depends on whether it is deployed on a report server.</span></span>

## <a name="default-native-mode-report-server-configuration"></a><span data-ttu-id="5c09c-110">기본 모드 보고서 서버 기본 구성</span><span class="sxs-lookup"><span data-stu-id="5c09c-110">Default Native mode report server configuration</span></span>
 <span data-ttu-id="5c09c-111">보고서 관리자의 **배달 방법** 목록에 표시되는 배달 확장 프로그램의 순서는 **RSReportServer.config** 파일에 배달 확장 프로그램 항목이 표시된 순서를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-111">The order of a delivery extension appears in Report Manager in the **Delivered by** list is based on the order of the delivery extension entries in the **RSReportServer.config** file.</span></span> <span data-ttu-id="5c09c-112">예를 들어, 다음 이미지에서는 목록에 전자 메일이 가장 먼저 표시되도록 기본 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-112">For example the following image shows e-mail first in the list and it is selected by default.</span></span>

 <span data-ttu-id="5c09c-113">![배달 확장 프로그램의 기본 목록](../media/ssrs-default-delivery.png "배달 확장 프로그램의 기본 목록")</span><span class="sxs-lookup"><span data-stu-id="5c09c-113">![default list of delivery extensions](../media/ssrs-default-delivery.png "default list of delivery extensions")</span></span>

 <span data-ttu-id="5c09c-114">다음은 기본 전달 확장 프로그램과 보고서 관리자에서의 표시 순서를 제어하는 **RSReportServer.config** 의 기본 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-114">The following is the default section of **RSReportServer.config** that controls the default delivery extension and the order they are displayed in Report Manager.</span></span> <span data-ttu-id="5c09c-115">전자 메일이 파일에 첫 번째로 표시되며 이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-115">Note that email appears first in the file and it is set as the default.</span></span>

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a><span data-ttu-id="5c09c-116">보고서 관리자에서 파일 공유 배달을 기본 배달 확장 프로그램으로 구성</span><span class="sxs-lookup"><span data-stu-id="5c09c-116">Configure File Share Delivery as the default delivery extension in Report Manager</span></span>

1.  <span data-ttu-id="5c09c-117">이 절차의 단계는 UI에서 파일 공유 배달이 첫 번째 옵션으로 표시되고 기본 선택 항목으로 나타나도록 구성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-117">The steps in this procedure modify the configuration so that file share delivery is listed as the first option in the UI and it is the default selection.</span></span>

     <span data-ttu-id="5c09c-118">텍스트 편집기에서 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-118">Open the RSReportServer.config file in a text editor.</span></span> <span data-ttu-id="5c09c-119">구성 파일에 대한 자세한 내용은 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c09c-119">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span> <span data-ttu-id="5c09c-120">구성 변경 후에는 UI가 다음 이미지와 유사해 보입니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-120">After the configuration changes, the UI will look like the following image:</span></span>

     <span data-ttu-id="5c09c-121">![배달 확장 프로그램의 수정된 목록](../media/ssrs-modified-delivery.png "배달 확장 프로그램의 수정된 목록")</span><span class="sxs-lookup"><span data-stu-id="5c09c-121">![modified list of delivery extensions](../media/ssrs-modified-delivery.png "modified list of delivery extensions")</span></span>

2.  <span data-ttu-id="5c09c-122">DeliveryUI 섹션이 다음 예시와 유사하게 보이도록 수정하고 주요 변경 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-122">Modify the DeliveryUI section to look like the following sample and note the key changes of:</span></span>

    1.  <span data-ttu-id="5c09c-123">FileShare 확장 프로그램이 이메일 확장 프로그램 앞에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-123">The FileShare extension is before the email extension.</span></span> <span data-ttu-id="5c09c-124">이렇게 하면 보고서 관리자에 확장 프로그램이 나열되는 순서가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-124">This will change the order the extensions are listed in Report Manager.</span></span>

    2.  <span data-ttu-id="5c09c-125">파일 공유 확장 프로그램에는 DefaultExtension 태그( `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` )가 포함되며 해당 확장 프로그램 종료 태그( `</Extension>`)가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-125">The File share extension contains DefaultExtension tag `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` and the extension end tag was added `</Extension>`.</span></span>

    3.  <span data-ttu-id="5c09c-126">전자 메일 확장 프로그램은 이제 기본값으로 구성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-126">The email extension is no longer configured as the default.</span></span> `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  <span data-ttu-id="5c09c-127">구성 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-127">Save the configuration file.</span></span>

4.  <span data-ttu-id="5c09c-128">몇 분 안에 보고서 서버가 구성 파일을 다시 로드하고 새 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-128">Within a few minutes the report server will reload the configuration file and the new settings will take effect.</span></span> <span data-ttu-id="5c09c-129">보고서 서버 서비스를 다시 시작하여 구성 파일을 강제로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-129">You can restart the report server service to force the loading of the configuration file.</span></span>

     <span data-ttu-id="5c09c-130">구성을 읽을 때 다음과 같은 이벤트가 Windows 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-130">The following event is written to the windows event log when the configuration is read.</span></span>

     <span data-ttu-id="5c09c-131">**이벤트 ID:** 109</span><span class="sxs-lookup"><span data-stu-id="5c09c-131">**Event ID:** 109</span></span>

     <span data-ttu-id="5c09c-132">**원본:** 보고서 서버 Windows 서비스(인스턴스 이름)</span><span class="sxs-lookup"><span data-stu-id="5c09c-132">**Source:** Report Server Windows Service (instance name)</span></span>

     <span data-ttu-id="5c09c-133">RSReportServer.config 파일 수정</span><span class="sxs-lookup"><span data-stu-id="5c09c-133">The RSReportServer.config file has been modified</span></span>

## <a name="sharepoint-mode-report-servers"></a><span data-ttu-id="5c09c-134">SharePoint 모드 보고서 서버</span><span class="sxs-lookup"><span data-stu-id="5c09c-134">SharePoint mode report servers</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5c09c-135">SharePoint 모드는 RsrReportServer.config 파일이 아니라 SharePoint 서비스 애플리케이션 데이터베이스에 확장 프로그램 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-135">SharePoint mode stores extensions information in the SharePoint service application databases and not in the RsrReportServer.config file.</span></span> <span data-ttu-id="5c09c-136">SharePoint 모드에서 PowerShell을 사용하 여 배달 확장 프로그램 구성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-136">In SharePoint mode, delivery extension configuration is modified using PowerShell.</span></span>

#### <a name="configure-the-default-delivery-extension"></a><span data-ttu-id="5c09c-137">기본 배달 확장 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="5c09c-137">Configure the default delivery extension</span></span>

1.  <span data-ttu-id="5c09c-138">**SharePoint 관리 셸**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-138">Open the **SharePoint Management Shell**.</span></span>

2.  <span data-ttu-id="5c09c-139">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 알고 있는 경우에 이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-139">You can skip this step if you already know the name of your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="5c09c-140">SharePoint 팜에 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 나열하려면 다음 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-140">Use the following PowerShell to list the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service applications in your SharePoint farm.</span></span>

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  <span data-ttu-id="5c09c-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 “ssrsapp”의 현재 기본 배달 확장 프로그램을 확인하려면 다음 PowerShell을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5c09c-141">Run the following PowerShell to verify the current default delivery extension for the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application "ssrsapp".</span></span>

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a><span data-ttu-id="5c09c-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c09c-142">See Also</span></span>
 <span data-ttu-id="5c09c-143">[Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md) [Rsreportserver.config 구성](../report-server/rsreportserver-config-configuration-file.md) 파일 [공유 배달 Reporting Services](file-share-delivery-in-reporting-services.md) [전자](e-mail-delivery-in-reporting-services.md) 메일 배달에 [대 한 보고서 서버 구성 Reporting Services &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="5c09c-143">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span></span>
