---
title: 배달 확장 프로그램 구현 준비 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bbf98286e6ed35542d8117b4b87b5ff3425def69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661550"
---
# <a name="preparing-to-implement-a-delivery-extension"></a><span data-ttu-id="32b7d-102">배달 확장 프로그램 구현 준비</span><span class="sxs-lookup"><span data-stu-id="32b7d-102">Preparing to Implement a Delivery Extension</span></span>
  <span data-ttu-id="32b7d-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 구현하기 전에 먼저 구현할 인터페이스를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-103">Before you implement your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="32b7d-104">우선 배달 확장 프로그램을 사용할 방식, 배달 확장 프로그램에 필요한 설정, 보고서 알림을 배달하기 위해 구현할 특정 기능 등을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-104">You first need to decide how your delivery extension will be used, what settings your delivery extension will require, and the specific functionality you will need to implement in order to deliver report notifications.</span></span>  
  
 <span data-ttu-id="32b7d-105">각 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램은 다음 기능을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-105">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="32b7d-106">확장 프로그램 및 지역화된 확장 프로그램 이름을 나타내는 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="32b7d-106">An <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface implementation that represents the extension and a localized extension name.</span></span>  
  
-   <span data-ttu-id="32b7d-107">보고서 알림을 최종 사용자에게 배달하는 데 사용할 수 있는 배달 확장 프로그램을 만드는 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 구현</span><span class="sxs-lookup"><span data-stu-id="32b7d-107">An <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> implementation that creates a delivery extension that can be used to deliver report notifications to end users.</span></span>  
  
-   <span data-ttu-id="32b7d-108">구독에 대한 특정 사용자 데이터를 처리할 수 있는 기능</span><span class="sxs-lookup"><span data-stu-id="32b7d-108">The ability to process specific user data for a subscription.</span></span>  
  
 <span data-ttu-id="32b7d-109">각 배달 확장 프로그램은 다음 기능을 포함하도록 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-109">Each delivery extension can be enhanced to include the following functionality:</span></span>  
  
-   <span data-ttu-id="32b7d-110">최종 사용자가 보고서 관리자를 사용하여 배달 확장 프로그램을 사용하는 보고서 구독을 만들 수 있는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 사용자 컨트롤 구현</span><span class="sxs-lookup"><span data-stu-id="32b7d-110">An [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] user control implementation that enables end users to use Report Manager to create report subscriptions that use the delivery extension.</span></span>  
  
 <span data-ttu-id="32b7d-111">다음 표에서는 배달 확장 프로그램에 대해 사용할 수 있는 인터페이스 및 클래스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-111">The following table describes the available interfaces and classes for delivery extensions.</span></span>  
  
|<span data-ttu-id="32b7d-112">인터페이스 또는 클래스</span><span class="sxs-lookup"><span data-stu-id="32b7d-112">Interface or class</span></span>|<span data-ttu-id="32b7d-113">Description</span><span class="sxs-lookup"><span data-stu-id="32b7d-113">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="32b7d-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스</span><span class="sxs-lookup"><span data-stu-id="32b7d-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> Interface</span></span>|<span data-ttu-id="32b7d-115">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 확장 프로그램을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-115">Represents an extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="32b7d-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 인터페이스</span><span class="sxs-lookup"><span data-stu-id="32b7d-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interface</span></span>|<span data-ttu-id="32b7d-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 배달 확장 프로그램을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-117">Represents a delivery extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="32b7d-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 인터페이스</span><span class="sxs-lookup"><span data-stu-id="32b7d-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interface</span></span>|<span data-ttu-id="32b7d-119">배달 확장 프로그램에 필요한 보고서 서버에 대한 정보를 포함합니다(예: 사용 가능한 렌더링 확장 프로그램 목록).</span><span class="sxs-lookup"><span data-stu-id="32b7d-119">Contains information about the report server that is required by delivery extensions (for example, a list of the available rendering extensions).</span></span>|  
|<span data-ttu-id="32b7d-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스</span><span class="sxs-lookup"><span data-stu-id="32b7d-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> Class</span></span>|<span data-ttu-id="32b7d-121">확장 프로그램에 대한 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-121">Represents a setting for an extension.</span></span>|  
|<span data-ttu-id="32b7d-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> 클래스</span><span class="sxs-lookup"><span data-stu-id="32b7d-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> Class</span></span>|<span data-ttu-id="32b7d-123">배달 확장 프로그램에서 보고서를 배달하는 데 사용하는 구독 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-123">Contains subscription information that delivery extensions use to deliver reports.</span></span>|  
|<span data-ttu-id="32b7d-124"><xref:Microsoft.ReportingServices.Interfaces.Report> 클래스</span><span class="sxs-lookup"><span data-stu-id="32b7d-124"><xref:Microsoft.ReportingServices.Interfaces.Report> Class</span></span>|<span data-ttu-id="32b7d-125">배달 확장 프로그램에서 사용자에게 보고서를 배달할 수 있도록 하는 보고서 특정 정보 및 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-125">Represents report-specific information and methods that enable delivery extensions to deliver reports to users.</span></span>|  
|<span data-ttu-id="32b7d-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 클래스</span><span class="sxs-lookup"><span data-stu-id="32b7d-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> Class</span></span>|<span data-ttu-id="32b7d-127">렌더링 확장 프로그램의 출력을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-127">Represents the output from a rendering extension.</span></span> <span data-ttu-id="32b7d-128"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체에는 렌더링 확장 프로그램에서 반환된 스트림을 처리하기 위해 배달 확장 프로그램에서 요구되는 연관 파일 이름 및 형식 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-128">A <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object contains the associated file name and type information that is required by the delivery extension in order to process the stream returned by the rendering extension.</span></span>|  
|<span data-ttu-id="32b7d-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 인터페이스</span><span class="sxs-lookup"><span data-stu-id="32b7d-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interface</span></span>|<span data-ttu-id="32b7d-130">보고서 관리자에서 사용자로부터 전자 메일 주소나 파일 공유 경로 등과 같은 배달 확장 프로그램별 구독 정보를 검색할 수 있는 방법을 나타내는 사용자 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="32b7d-130">A user control that represents the means to retrieve delivery extension-specific subscription information from the user in Report Manager (for example, an e-mail address or the path to a file share).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32b7d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32b7d-131">See Also</span></span>  
 <span data-ttu-id="32b7d-132">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="32b7d-132">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="32b7d-133">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="32b7d-133">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="32b7d-134">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="32b7d-134">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
