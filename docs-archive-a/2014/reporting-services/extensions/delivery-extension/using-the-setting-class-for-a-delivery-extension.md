---
title: 배달 확장 프로그램에 대해 Setting 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 594cf28391ae4523e1a95ad79ee5b1280ff72218
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729127"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a><span data-ttu-id="5bb4f-102">배달 확장 프로그램에 대해 Setting 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="5bb4f-102">Using the Setting Class for a Delivery Extension</span></span>
  <span data-ttu-id="5bb4f-103"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스는 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스에 있으며 배달 확장 프로그램에 대한 확장 프로그램 설정 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-103">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents information about extension settings for a delivery extension.</span></span> <span data-ttu-id="5bb4f-104"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스는 배달 확장 프로그램이 제대로 작동하는 데 필요한 설정 정보를 저장하기 위한 인프라를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-104">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class provides infrastructure for storing information about the settings that are required in order for a delivery extension to function properly.</span></span> <span data-ttu-id="5bb4f-105">예를 들어 보고서 서버 전자 메일 배달에서 사용자는 받는 사람 주소, 보내는 사람 주소, 전자 메일 제목 줄 등과 같이 전자 메일 배달을 위한 특정 설정을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-105">For example, in Report Server E-Mail delivery, a user is required to supply settings specific to e-mail delivery, such as the recipient's address, the sender's address, the subject line of the e-mail, and more.</span></span> <span data-ttu-id="5bb4f-106">사용자 지정 배달 공급자의 경우에도 사용자가 배달 확장 프로그램에서 알림 및 보고서를 전달할 수 있도록 특정 설정을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-106">Undoubtedly, your custom delivery providers will require the user to supply specific settings in order for the delivery extension to deliver notifications and reports.</span></span>  
  
 <span data-ttu-id="5bb4f-107"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스는 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 인터페이스의 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 속성을 구현할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-107">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is used when implementing the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property of the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="5bb4f-108"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스는 구독 또는 알림이 만들어질 때 사용자가 제공하는 확장 프로그램 설정을 처리하는 데도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-108">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is also used for processing the extension setting data that is supplied by a user when a subscription or notification is created.</span></span>  
  
 <span data-ttu-id="5bb4f-109"><xref:Microsoft.ReportingServices.Interfaces.Setting> 클래스 사용 방법에 대한 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bb4f-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Setting> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb4f-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bb4f-110">See Also</span></span>  
 <span data-ttu-id="5bb4f-111">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="5bb4f-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="5bb4f-112">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="5bb4f-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
