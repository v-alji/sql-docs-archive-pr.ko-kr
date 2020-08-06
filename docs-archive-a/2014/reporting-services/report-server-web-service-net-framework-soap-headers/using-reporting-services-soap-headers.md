---
title: Reporting Services SOAP 헤더 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f48be183398d4d441b5781c9f9467178c3011e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733556"
---
# <a name="using-reporting-services-soap-headers"></a><span data-ttu-id="106db-102">Reporting Services SOAP 헤더 사용</span><span class="sxs-lookup"><span data-stu-id="106db-102">Using Reporting Services SOAP Headers</span></span>
  <span data-ttu-id="106db-103">SOAP를 사용한 웹 서비스 메서드와의 통신은 표준 형식을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="106db-103">Communication with a Web service method using SOAP follows a standard format.</span></span> <span data-ttu-id="106db-104">이 형식의 일부는 XML 문서로 인코딩되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="106db-104">Part of this format is the data that is encoded in an XML document.</span></span> <span data-ttu-id="106db-105">XML 문서는 루트 **Envelope** 요소로 구성되고, 이것은 다시 필수 **Body** 요소와 선택적 **Header** 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="106db-105">The XML document consists of a root **Envelope** element, which in turn consists of a required **Body** element and an optional **Header** element.</span></span> <span data-ttu-id="106db-106">**Body** 요소는 메시지 관련 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-106">The **Body** element contains the data specific to the message.</span></span> <span data-ttu-id="106db-107">선택적 **Header** 요소는 특정 메시지와 직접 관련되지 않은 추가 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="106db-107">The optional **Header** element can contain additional information not directly related to the particular message.</span></span> <span data-ttu-id="106db-108">**Header** 요소의 각 자식 요소를 SOAP 헤더라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-108">Each child element of the **Header** element is called a SOAP header.</span></span>  
  
 <span data-ttu-id="106db-109">SOAP 헤더가 메시지와 관련된 데이터를 포함할 수는 있지만 일반적으로 웹 서버 인프라에서 처리되는 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-109">Although the SOAP headers can contain data related to the message, they typically contain information processed by the Web server infrastructure.</span></span>  
  
 <span data-ttu-id="106db-110">보고서 서버 웹 서비스는 SOAP 헤더에서 사용할 여러 클래스를 정의합니다. <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> 및 <xref:ReportExecution2005.ExecutionHeader></span><span class="sxs-lookup"><span data-stu-id="106db-110">The Report Server Web services define several classes for use in the SOAP header: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader>, and <xref:ReportExecution2005.ExecutionHeader>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="106db-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="106db-111">In This Section</span></span>  
  
|<span data-ttu-id="106db-112">항목</span><span class="sxs-lookup"><span data-stu-id="106db-112">Topic</span></span>|<span data-ttu-id="106db-113">설명</span><span class="sxs-lookup"><span data-stu-id="106db-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="106db-114">일괄 처리 메서드</span><span class="sxs-lookup"><span data-stu-id="106db-114">Batching Methods</span></span>](batching-methods.md)|<span data-ttu-id="106db-115"><xref:ReportService2005.BatchHeader>를 사용하여 여러 작업을 단일 트랜잭션으로 일괄 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-115">Describes how to batch multiple operations into a single transaction using <xref:ReportService2005.BatchHeader>.</span></span>|  
|[<span data-ttu-id="106db-116">실행 상태 식별</span><span class="sxs-lookup"><span data-stu-id="106db-116">Identifying Execution State</span></span>](identifying-execution-state.md)|<span data-ttu-id="106db-117">**SessionHeader**를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 세션 상태를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-117">Describes how to manage session state in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] using **SessionHeader**.</span></span>|  
|[<span data-ttu-id="106db-118">GetProperties 메서드에 대한 항목 네임스페이스 설정</span><span class="sxs-lookup"><span data-stu-id="106db-118">Setting the Item Namespace for the GetProperties Method</span></span>](setting-the-item-namespace-for-the-getproperties-method.md)|<span data-ttu-id="106db-119"><xref:ReportService2010.ReportingService2010.GetProperties%2A> 메서드 및 <xref:ReportService2010.ItemNamespaceHeader> SOAP 헤더를 사용하여 항목의 경로나 ID를 기반으로 속성을 검색하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="106db-119">Describes how to retrieve properties based on either the path or the ID of an item by using the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method and the <xref:ReportService2010.ItemNamespaceHeader> SOAP header.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="106db-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="106db-120">See Also</span></span>  
 <span data-ttu-id="106db-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="106db-121">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="106db-122">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="106db-122">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
