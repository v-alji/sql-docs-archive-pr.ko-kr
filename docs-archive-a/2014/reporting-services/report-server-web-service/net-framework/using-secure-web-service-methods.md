---
title: 보안 웹 서비스 메서드 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e88a164602f9bbe6ad42c3897285a484cac94466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739219"
---
# <a name="using-secure-web-service-methods"></a><span data-ttu-id="2d563-102">보안 웹 서비스 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="2d563-102">Using Secure Web Service Methods</span></span>
  <span data-ttu-id="2d563-103">특정 보고서 서버 웹 서비스 메서드를 호출할 때 보안 연결이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-103">Certain Report Server Web service methods may require a secure connection when you invoke them.</span></span> <span data-ttu-id="2d563-104">보안 연결이 필요한 메서드는 RSReportServer.config 파일의 `SecureConnectionLevel` 설정에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-104">The methods that require a secure connection are determined by the `SecureConnectionLevel` setting in the RSReportServer.config file.</span></span> <span data-ttu-id="2d563-105">이 설정의 값은 0 이상의 유효 범위를 가진 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-105">The value of the setting is an integer value with a valid range of 0 and higher.</span></span> <span data-ttu-id="2d563-106">다음 표에서는 이러한 값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-106">The following table describes these values.</span></span>  
  
|<span data-ttu-id="2d563-107">Level</span><span class="sxs-lookup"><span data-stu-id="2d563-107">Level</span></span>|<span data-ttu-id="2d563-108">Description</span><span class="sxs-lookup"><span data-stu-id="2d563-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d563-109">**0**</span><span class="sxs-lookup"><span data-stu-id="2d563-109">**0**</span></span>|<span data-ttu-id="2d563-110">안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-110">Not secure.</span></span> <span data-ttu-id="2d563-111">Reporting Services SOAP API에 대해 이루어지는 호출에 보안 연결이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-111">Calls made to the Reporting Services SOAP API do not require a secure connection.</span></span>|  
|<span data-ttu-id="2d563-112">**0**보다 큼</span><span class="sxs-lookup"><span data-stu-id="2d563-112">Greater than **0**</span></span>|<span data-ttu-id="2d563-113">보안.</span><span class="sxs-lookup"><span data-stu-id="2d563-113">Secure.</span></span> <span data-ttu-id="2d563-114">Reporting Services SOAP API에 대해 이루어지는 모든 호출에 보안 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-114">All calls made to the Reporting Services SOAP API require a secure connection.</span></span>|  
  
 <span data-ttu-id="2d563-115">웹 서비스의 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 메서드를 사용하여 보고서 서버의 현재 구성에 따라 보안 연결이 필요한 웹 서비스 메서드 목록을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-115">You can use the <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> method of the Web service to return a list of Web service methods that require a secure connection according to the current configuration of the report server.</span></span> <span data-ttu-id="2d563-116">SSL 시나리오에서는 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>를 통해 반환된 메서드 목록을 평가하고 웹 서비스 URI의 스키마 이름을 호출되는 메서드에 따라 "https" 또는 "http"로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d563-116">In an SSL scenario, you should evaluate the list of methods that are returned by <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> and change the scheme name of the Web service URI to "https" or "http" depending on the method being called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d563-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d563-117">See Also</span></span>  
 <span data-ttu-id="2d563-118">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="2d563-118">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="2d563-119">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="2d563-119">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
