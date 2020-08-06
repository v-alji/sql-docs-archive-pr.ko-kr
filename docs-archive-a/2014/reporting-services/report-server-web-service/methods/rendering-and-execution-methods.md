---
title: 렌더링 및 실행 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0bc793e9a18e993989563fd3526ff12272f775c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736027"
---
# <a name="rendering-and-execution-methods"></a><span data-ttu-id="56101-102">렌더링 및 실행 메서드</span><span class="sxs-lookup"><span data-stu-id="56101-102">Rendering and Execution Methods</span></span>
  <span data-ttu-id="56101-103">다음 메서드를 사용하여 항목 실행 및 캐싱과 보고서 렌더링을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56101-103">You can use these methods to manage item execution and caching, and report rendering.</span></span>  
  
|<span data-ttu-id="56101-104">방법</span><span class="sxs-lookup"><span data-stu-id="56101-104">Method</span></span>|<span data-ttu-id="56101-105">작업</span><span class="sxs-lookup"><span data-stu-id="56101-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|<span data-ttu-id="56101-106">항목 캐시를 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-106">Invalidates the cache for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<span data-ttu-id="56101-107">항목에 대한 캐시 구성 및 캐시된 항목 복사본의 만료 시점을 설명하는 설정을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-107">Returns the cache configuration for an item and the settings that describe when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<span data-ttu-id="56101-108">개별 항목에 대한 실행 옵션 및 연관된 설정을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-108">Returns the execution option and associated settings for an individual item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|<span data-ttu-id="56101-109">지원되는 실행 설정 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-109">Returns a list of supported execution settings.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|<span data-ttu-id="56101-110">지정된 보고서를 처리하고 지정된 형식으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-110">Processes the specified report and renders it in a specified format.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|<span data-ttu-id="56101-111">캐시할 항목을 구성하고 캐시된 항목 복사본의 만료 시점을 지정하는 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-111">Configures an item to be cached and provides settings that specify when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|<span data-ttu-id="56101-112">지정된 항목에 대한 실행 옵션 및 연관된 실행 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-112">Sets execution options and associated execution properties for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|<span data-ttu-id="56101-113">지정된 항목에 대한 항목 실행 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="56101-113">Generates an item execution snapshot for a specified item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56101-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56101-114">See Also</span></span>  
 <span data-ttu-id="56101-115">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="56101-115">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="56101-116">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="56101-116">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="56101-117">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="56101-117">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="56101-118">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="56101-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
