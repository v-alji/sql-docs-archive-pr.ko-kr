---
title: 배달 확장 프로그램에 대해 RenderedOutputFile 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661541"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a><span data-ttu-id="3a4bb-102">배달 확장 프로그램에 대해 RenderedOutputFile 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="3a4bb-102">Using the RenderedOutputFile Class for a Delivery Extension</span></span>
  <span data-ttu-id="3a4bb-103"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 클래스는 데이터 스트림 및 데이터 스트림의 연관 속성에 대한 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-103">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class represents a data stream and information about the data stream's associated properties.</span></span> <span data-ttu-id="3a4bb-104"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 클래스의 **Data** 속성은 렌더링된 보고서 또는 보고서 리소스를 **Stream** 개체로 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-104">The **Data** property of the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class is used to represent a rendered report or report resource as a **Stream** object.</span></span>  
  
 <span data-ttu-id="3a4bb-105">**Report** 개체의 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 메서드는 렌더링된 단일 보고서를 구성하는 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체 배열을 하나 이상 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-105">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the **Report** object returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together constitute a single rendered report.</span></span> <span data-ttu-id="3a4bb-106">첫 번째 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 렌더링된 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-106">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="3a4bb-107">다른 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 보고서 데이터(예: HTML 파일 및 연결된 이미지)와 함께 배달되어야 하는 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-107">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="3a4bb-108">단일 스트림 렌더링 확장 프로그램(IMAGE, PDF, MHTML 및 EXCEL)은 배열에 있는 하나의 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-108">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and EXCEL) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="3a4bb-109"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 클래스 사용 방법에 대한 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4bb-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a4bb-110">See Also</span></span>  
 <span data-ttu-id="3a4bb-111">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3a4bb-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="3a4bb-112">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3a4bb-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
