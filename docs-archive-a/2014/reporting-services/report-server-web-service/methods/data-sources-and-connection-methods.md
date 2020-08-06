---
title: 데이터 원본 및 연결 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29dd8dd1c002ab3b7d4594a4e25ec44bdb2cc8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736040"
---
# <a name="data-sources-and-connection-methods"></a><span data-ttu-id="6475a-102">데이터 원본 및 연결 메서드</span><span class="sxs-lookup"><span data-stu-id="6475a-102">Data Sources and Connection Methods</span></span>
  <span data-ttu-id="6475a-103">이러한 메서드를 사용하여 데이터 원본 연결 및 자격 증명을 설정하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-103">You can use these methods to set and manage data source connections and credentials.</span></span>  
  
|<span data-ttu-id="6475a-104">방법</span><span class="sxs-lookup"><span data-stu-id="6475a-104">Method</span></span>|<span data-ttu-id="6475a-105">작업</span><span class="sxs-lookup"><span data-stu-id="6475a-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|<span data-ttu-id="6475a-106">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에서 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-106">Creates a new data source in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|<span data-ttu-id="6475a-107">사용하도록 설정된 데이터 원본을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-107">Disables a data source that is enabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|<span data-ttu-id="6475a-108">사용하지 않도록 설정된 데이터 원본을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-108">Enables a data source that is disabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|<span data-ttu-id="6475a-109">데이터 원본의 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-109">Returns the contents of a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|<span data-ttu-id="6475a-110">지정된 항목의 데이터 원본 프롬프트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-110">Gets the data source prompts for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|<span data-ttu-id="6475a-111">카탈로그에 있는 항목의 데이터 원본을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-111">Returns the data sources for an item in the catalog.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|<span data-ttu-id="6475a-112">지정된 카탈로그 항목을 참조하는 카탈로그 항목 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-112">Returns a list of catalog items that reference a specified catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|<span data-ttu-id="6475a-113">지정된 데이터 원본과 연결된 구독 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-113">Returns a list of subscriptions that are associated with a given data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|<span data-ttu-id="6475a-114">데이터 원본과 연결된 연결 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-114">Sets the connection properties that are associated with a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|<span data-ttu-id="6475a-115">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에 있는 항목의 데이터 원본을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-115">Sets the data sources for an item in a report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|<span data-ttu-id="6475a-116">데이터 원본에 대한 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-116">Tests the connection for a data source.</span></span> <span data-ttu-id="6475a-117">이 메서드는 데이터 원본의 직접 테스트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-117">This method supports the direct testing of the data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|<span data-ttu-id="6475a-118">데이터 원본에 대한 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-118">Tests the connection for a data source.</span></span> <span data-ttu-id="6475a-119">이 메서드는 보고서나 모델 및 공유 데이터 원본에서 사용하는 게시된 데이터 원본의 테스트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6475a-119">This method supports the testing of published data sources that are used by reports or models and shared data sources.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6475a-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6475a-120">See Also</span></span>  
 <span data-ttu-id="6475a-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="6475a-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="6475a-122">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="6475a-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="6475a-123">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="6475a-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="6475a-124">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6475a-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
