---
title: 배달 확장 프로그램에 대한 IDeliveryExtension 인터페이스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f9ab0767a09016d4f4bc1158988965bfc13b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661554"
---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a><span data-ttu-id="96c67-102">배달 확장 프로그램에 대한 IDeliveryExtension 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="96c67-102">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>
  <span data-ttu-id="96c67-103">배달 확장 프로그램 클래스는 알림 내용을 기준으로 사용자에게 보고서 알림을 배달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-103">Your delivery extension class is used to deliver report notifications to users based on the contents of the notifications.</span></span> <span data-ttu-id="96c67-104">배달 확장 프로그램 클래스는 배달 확장 프로그램에 전달되는 사용자 설정을 검사하기 위한 인프라도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-104">The delivery extension class also provides infrastructure for validating user settings that are passed to the delivery extension.</span></span> <span data-ttu-id="96c67-105">또한 배달 확장 프로그램 클래스에는 클라이언트가 확장 프로그램의 이름, 확장 프로그램에서 지원하는 설정, 배달 확장 프로그램에서 사용 가능한 렌더링 형식 등에 대한 정보를 얻는 데 사용할 수 있는 특정 속성이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-105">In addition, your delivery extension class should contain specific properties that clients can use to gain information about the name of the extension, the settings that the extension supports, and the rendering formats that are available to the delivery extension.</span></span>  
  
 <span data-ttu-id="96c67-106">![IDeliveryExtension 인터페이스 프로세스](../../media/bk-ext-02.gif "IDeliveryExtension 인터페이스 프로세스")</span><span class="sxs-lookup"><span data-stu-id="96c67-106">![IDeliveryExtension interface process](../../media/bk-ext-02.gif "IDeliveryExtension interface process")</span></span>  
<span data-ttu-id="96c67-107">IDeliveryExtension 인터페이스를 통해 사용자 데이터의 검사가 가능하며 클라이언트에서는 필수 배달 설정에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-107">The IDeliveryExtension interface allows validation of user data as well as for clients to learn about the required delivery settings</span></span>  
  
 <span data-ttu-id="96c67-108">배달 확장 프로그램 클래스를 만들려면 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 및 <xref:Microsoft.ReportingServices.Interfaces.IExtension>을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-108">To create a delivery extension class, implement <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> and <xref:Microsoft.ReportingServices.Interfaces.IExtension>.</span></span> <span data-ttu-id="96c67-109">**IDeliveryExtension** 인터페이스를 통해 배달 확장 프로그램에서 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 메서드를 사용하여 보고서 알림을 배달하고 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> 메서드를 사용하여 수신되는 확장 프로그램 설정을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-109">The **IDeliveryExtension** interface enables your delivery extension to deliver report notifications using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method and to validate incoming extension settings using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> method.</span></span> <span data-ttu-id="96c67-110">**IExtension** 인터페이스를 통해서는 배달 확장 프로그램에서 지역화된 확장 프로그램 이름을 구현하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성 파일에 저장된 확장 프로그램별 구성 정보를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-110">The **IExtension** interface enables your delivery extension to implement a localized extension name and to process extension-specific configuration information stored in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration file.</span></span> <span data-ttu-id="96c67-111">**IExtension**을 구현하면 배달 확장 프로그램에 <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-111">By implementing **IExtension**, your delivery extension contains the <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> property.</span></span> <span data-ttu-id="96c67-112">[!INCLUDE[ssRS](../../../includes/ssrs.md)] 배달 확장 프로그램이 **LocalizedName** 속성을 지원하는 것이 좋으며, 그럴 경우 사용자 인터페이스에서 확장 프로그램에 대해 보고서 관리자와 같은 친숙한 이름이 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-112">It is strongly recommended that [!INCLUDE[ssRS](../../../includes/ssrs.md)] delivery extensions support the **LocalizedName** property, so that users encounter a familiar name for the extension in a user interface, such as Report Manager.</span></span>  
  
 <span data-ttu-id="96c67-113">배달 확장 프로그램에서는 **IDeliveryExtension** 인터페이스의 **ExtensionSettings** 속성도 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-113">Your delivery extension must also implement the **ExtensionSettings** property of the **IDeliveryExtension** interface.</span></span> <span data-ttu-id="96c67-114">보고서 서버에서는 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 속성에 의해 반환된 값을 사용하여 배달 확장 프로그램에 필요한 설정을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-114">The report server uses the value returned by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property to evaluate the settings that a delivery extension requires.</span></span> <span data-ttu-id="96c67-115">배달 확장 프로그램과 상호 작용하는 클라이언트에서는 보고서 서버 웹 서비스의 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 메서드를 사용하여 배달 확장 프로그램에 대한 설정 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-115">Clients that interact with delivery extensions use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method of the Report Server Web service to return a list of settings for the delivery extension.</span></span>  
  
 <span data-ttu-id="96c67-116">또한 배달 확장 프로그램 클래스를 사용하여 RSReportServer.config 파일에 저장된 사용자 지정 구성 데이터를 검색하고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c67-116">You can also use your delivery extension class to retrieve and process custom configuration data stored in the RSReportServer.config file.</span></span> <span data-ttu-id="96c67-117">사용자 지정 구성 데이터를 처리하는 방법은 <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> 메서드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="96c67-117">For more information about processing custom configuration data, see the <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="96c67-118">예제 **IDeliveryExtension** 클래스 구현은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96c67-118">For a sample **IDeliveryExtension** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c67-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96c67-119">See Also</span></span>  
 <span data-ttu-id="96c67-120">[배달 확장 프로그램 구현](../delivery-extension/implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="96c67-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="96c67-121">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="96c67-121">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
