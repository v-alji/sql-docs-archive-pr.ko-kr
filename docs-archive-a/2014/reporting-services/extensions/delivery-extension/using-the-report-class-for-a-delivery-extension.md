---
title: 배달 확장 프로그램에 대해 Report 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661538"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a><span data-ttu-id="1d87c-102">배달 확장 프로그램에 대해 Report 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="1d87c-102">Using the Report Class for a Delivery Extension</span></span>
  <span data-ttu-id="1d87c-103"><xref:Microsoft.ReportingServices.Interfaces.Report> 클래스는 보고서 서버 데이터베이스의 보고서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-103">The <xref:Microsoft.ReportingServices.Interfaces.Report> class represents a report in the report server database.</span></span> <span data-ttu-id="1d87c-104">구독은 특정 보고서와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-104">Any subscription is associated with a specific report.</span></span> <span data-ttu-id="1d87c-105">보고서는 알림에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-105">The report is contained in the notification.</span></span> <span data-ttu-id="1d87c-106">배달 확장 프로그램에서는 알림의 일부인 <xref:Microsoft.ReportingServices.Interfaces.Report> 개체를 사용하여 보고서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-106">Your delivery extension can use the <xref:Microsoft.ReportingServices.Interfaces.Report> object that is part of the notification to render the report.</span></span> <span data-ttu-id="1d87c-107"><xref:Microsoft.ReportingServices.Interfaces.Report> 개체에는 보고서 이름 및 보고서 서버의 보고서 URL과 같은 보고서별 속성도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object also contains report-specific properties, such as the URL to the report on the report server and the name of the report.</span></span> <span data-ttu-id="1d87c-108">이러한 속성은 모두 배달 공급자의 일부로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-108">These properties can all be used as part of your delivery provider.</span></span>  
  
 <span data-ttu-id="1d87c-109"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 클래스의 <xref:Microsoft.ReportingServices.Interfaces.Report> 메서드는 보고서를 렌더링하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-109">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the <xref:Microsoft.ReportingServices.Interfaces.Report> class can be used to render a report.</span></span> <span data-ttu-id="1d87c-110"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 메서드는 렌더링된 단일 보고서를 구성하는 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체 배열을 하나 이상 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-110">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together comprise a single rendered report.</span></span> <span data-ttu-id="1d87c-111">첫 번째 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 렌더링된 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-111">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="1d87c-112">다른 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 보고서 데이터(예: HTML 파일 및 연결된 이미지)와 함께 배달되어야 하는 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-112">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="1d87c-113">단일 스트림 렌더링 확장 프로그램(IMAGE, PDF, MHTML 및 Excel)은 배열의 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체 중 하나만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-113">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and Excel) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="1d87c-114"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 보고서 스트림을 포함하며 배달의 일부가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d87c-114">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object, which contains the report stream, can be included as part of a delivery.</span></span>  
  
 <span data-ttu-id="1d87c-115"><xref:Microsoft.ReportingServices.Interfaces.Report> 클래스 사용 방법에 대한 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d87c-115">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d87c-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d87c-116">See Also</span></span>  
 <span data-ttu-id="1d87c-117">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="1d87c-117">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="1d87c-118">[Reporting Services 확장 라이브러리](../reporting-services-extension-library.md) </span><span class="sxs-lookup"><span data-stu-id="1d87c-118">[Reporting Services Extension Library](../reporting-services-extension-library.md) </span></span>  
 [<span data-ttu-id="1d87c-119">배달 확장 프로그램에 대해 RenderedOutputFile 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="1d87c-119">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
