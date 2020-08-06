---
title: 배달 확장 프로그램에 대해 IDeliveryReportServerInformation 인터페이스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52e137d1a866305ec6435a4940fe98448bce5778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661542"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a><span data-ttu-id="cd441-102">배달 확장 프로그램에 대해 IDeliveryReportServerInformation 인터페이스 사용</span><span class="sxs-lookup"><span data-stu-id="cd441-102">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>
  <span data-ttu-id="cd441-103"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 인터페이스는 보고서 서버에 대한 정보를 검색하는 데 사용할 수 있는 여러 가지 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-103">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface exposes several properties that you can use to retrieve information about a report server.</span></span> <span data-ttu-id="cd441-104">이 정보를 사용하여 알림 및 보고서를 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-104">You can use this information to deliver notifications and reports.</span></span> <span data-ttu-id="cd441-105">배달 확장 프로그램 클래스를 구현하는 경우 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 인터페이스에서 필요한 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 속성을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-105">When implementing your delivery extension class, you implement the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property as required by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="cd441-106"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 속성은 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 인터페이스를 구현하는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-106">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property returns an object that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface.</span></span> <span data-ttu-id="cd441-107">이 개체로부터 보고서 서버에서 현재 지원하는 렌더링 확장 프로그램 목록을 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-107">From this object you can get a list of rendering extensions currently supported by the report server.</span></span>  
  
 <span data-ttu-id="cd441-108">다음 `for` 루프를 사용 하 여 보고서 서버에서 현재 사용 가능한 렌더링 확장 프로그램 목록을 **ArrayList** 개체로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd441-108">The following `for` loop could be used to store a list of rendering extensions currently available on the report server in an **ArrayList** object.</span></span>  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 <span data-ttu-id="cd441-109"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 인터페이스에 대한 자세한 내용은 [배달 확장 프로그램에 대해 IDeliveryReportServerInformation 인터페이스 사용](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd441-109">For more information about the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface, see [Using the IDeliveryReportServerInformation Interface for a Delivery Extension](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd441-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd441-110">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="cd441-111">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="cd441-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="cd441-112">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cd441-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
