---
title: 배달 확장 프로그램에 대해 Notification 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661547"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a><span data-ttu-id="14117-102">배달 확장 프로그램에 대해 Notification 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="14117-102">Using a Notification Class for a Delivery Extension</span></span>
  <span data-ttu-id="14117-103"><xref:Microsoft.ReportingServices.Interfaces.Notification> 클래스는 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스에 있으며 배달 확장 프로그램에서 보고서 배달을 위해 사용하는 구독 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14117-103">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents subscription information that delivery extensions use for delivering reports.</span></span> <span data-ttu-id="14117-104"><xref:Microsoft.ReportingServices.Interfaces.Notification> 클래스는 배달용 보고서 렌더링, 알림 상태 결정 및 사용자 데이터 설정 작업을 수행하는 데 사용할 수 있는 다수의 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="14117-104">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class provides a number of properties that can be used to render the reports for delivery, determine the status of the notification, and set user data.</span></span>

 <span data-ttu-id="14117-105">![보고서 알림 프로세스](../../media/bk-ext-03.gif "보고서 알림 프로세스") 알림은 배달의 중앙 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="14117-105">![Report notification process](../../media/bk-ext-03.gif "Report notification process") The notification is the central object of any delivery</span></span>

 <span data-ttu-id="14117-106">사용자 지정 배달 확장 프로그램을 사용하는 구독과 연결된 이벤트가 발생할 경우 <xref:Microsoft.ReportingServices.Interfaces.Report> 개체가 포함된 알림이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="14117-106">When an event fires that is associated with a subscription that uses your custom delivery extension, a notification is created that contains a <xref:Microsoft.ReportingServices.Interfaces.Report> object.</span></span> <span data-ttu-id="14117-107"><xref:Microsoft.ReportingServices.Interfaces.Report> 개체는 주어진 보고서를 지원되는 렌더링 형식으로 렌더링하는 데 필요한 기능을 캡슐화하며 서버에 있는 보고서 URL 및 보고서 이름과 같이 보고서 특정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="14117-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object encapsulates the functionality needed to render a given report to a supported rendering format and contains report-specific properties, such as the URL to the report on the server and the name of the report.</span></span> <span data-ttu-id="14117-108"><xref:Microsoft.ReportingServices.Interfaces.Report> 클래스에 대한 자세한 내용은 [배달 확장 프로그램에 대해 보고서 클래스 사용](../delivery-extension/using-the-report-class-for-a-delivery-extension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14117-108">For more information about the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [Using the Report Class for a Delivery Extension](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).</span></span>

 <span data-ttu-id="14117-109"><xref:Microsoft.ReportingServices.Interfaces.Notification> 개체를 배달 확장 프로그램의 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 메서드에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="14117-109">You pass the <xref:Microsoft.ReportingServices.Interfaces.Notification> object to the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of your delivery extension.</span></span> <span data-ttu-id="14117-110"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 메서드에는 알림을 처리하고 보고서를 배달하기 위한 특정 코드가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14117-110">Your <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method should contain specific code to process the notification and to deliver the report.</span></span>

 <span data-ttu-id="14117-111"><xref:Microsoft.ReportingServices.Interfaces.Notification> 클래스 사용 방법에 대한 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14117-111">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Notification> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="retry-functionality"></a><span data-ttu-id="14117-112">다시 시도 기능</span><span class="sxs-lookup"><span data-stu-id="14117-112">Retry Functionality</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="14117-113">에서는 즉시 배달할 수 없는 알림에 대해 재시도 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14117-113">allows you to create a retry queue for notifications that cannot immediately be delivered.</span></span> <span data-ttu-id="14117-114">보고서 서버에서 배달 확장 프로그램의 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 메서드를 호출하고 나면 배달 확장 프로그램은 보고서 서버에서 나중에 배달을 다시 시도하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14117-114">After the report server invokes the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of a delivery extension, the delivery extension can request that the report server retry the delivery at a later point in time.</span></span> <span data-ttu-id="14117-115">이 경우 보고서 서버에서 알림을 내부 큐에 두고 일정 시간이 경과한 후 배달을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="14117-115">If this occurs, the report server places the notification in an internal queue and retries the delivery after a specific period of time has elapsed.</span></span> <span data-ttu-id="14117-116">관리자는 **MaxNumberOfRetries** XML 요소 및 **PeriodBetweenRetries** XML 요소를 사용하여 RSReportServer.config 파일의 배달 확장 프로그램 섹션에서 보고서 서버가 수행하는 최대 재시도 횟수 및 간격을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14117-116">Administrators can configure the maximum number of retry attempts that the report server performs and the period between retries in the delivery extension section of the RSReportServer.config file using the **MaxNumberOfRetries** XML element and the **PeriodBetweenRetries** XML element.</span></span> <span data-ttu-id="14117-117">나중에 배달에 성공하거나 다시 시도 최대 횟수에 도달하면 알림이 재시도 큐에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="14117-117">Notifications are removed from the retry queue if delivery later succeeds or if the maximum number of retry attempts is reached.</span></span> <span data-ttu-id="14117-118">최대 재시도 횟수에 도달한 후 배달에 실패하면 알림이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="14117-118">If delivery fails after the maximum number of retries, the notification is discarded.</span></span>

## <a name="see-also"></a><span data-ttu-id="14117-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14117-119">See Also</span></span>
 <span data-ttu-id="14117-120">[확장 라이브러리 Reporting Services](../reporting-services-extension-library.md) [배달 확장 프로그램 구현](../delivery-extension/implementing-a-delivery-extension.md)</span><span class="sxs-lookup"><span data-stu-id="14117-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


