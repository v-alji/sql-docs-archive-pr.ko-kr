---
title: 보고서 서버 네임스페이스 관리 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b2dc38976406aaa0fa799e7a58ee340e5449d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730144"
---
# <a name="report-server-namespace-management-methods"></a><span data-ttu-id="f00db-102">보고서 서버 네임스페이스 관리 메서드</span><span class="sxs-lookup"><span data-stu-id="f00db-102">Report Server Namespace Management Methods</span></span>
  <span data-ttu-id="f00db-103">보고서 서버 관리 웹 서비스에는 보고서 서버 데이터베이스에서 보고서, 폴더 및 리소스를 관리하는 데 사용할 수 있는 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-103">The Report Server Management Web service contains methods that you can use to manage reports, folders, and resources in the report server database.</span></span>  
  
|<span data-ttu-id="f00db-104">방법</span><span class="sxs-lookup"><span data-stu-id="f00db-104">Method</span></span>|<span data-ttu-id="f00db-105">작업</span><span class="sxs-lookup"><span data-stu-id="f00db-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|<span data-ttu-id="f00db-106">작업 실행을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-106">Cancels execution of a job.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|<span data-ttu-id="f00db-107">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에 폴더를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-107">Adds a folder to the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|<span data-ttu-id="f00db-108">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에 새 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-108">Adds a new item to a report server database or SharePoint library.</span></span> <span data-ttu-id="f00db-109">이 메서드는 `Report`, `Model`, `Dataset`, `Component`, `Resource` 및 `DataSource` 항목 유형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-109">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<span data-ttu-id="f00db-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span><span class="sxs-lookup"><span data-stu-id="f00db-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span></span>|<span data-ttu-id="f00db-111">새 보고서 편집 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-111">Creates a new report edit session.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|<span data-ttu-id="f00db-112">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에서 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-112">Removes an item from the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|<span data-ttu-id="f00db-113">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에서 지정된 검색 조건과 일치하는 항목을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-113">Returns the items in the report server database or SharePoint library that match the specified search criteria.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|<span data-ttu-id="f00db-114">제공된 매개 변수를 기준으로 이벤트를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-114">Triggers an event based on the supplied parameters.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|<span data-ttu-id="f00db-115">지정된 확장 프로그램에 대한 설정 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-115">Returns a list of settings for a given extension.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|<span data-ttu-id="f00db-116">항목이 존재하는 경우 보고서 서버 데이터베이스 또는 SharePoint 라이브러리에서 항목의 유형을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-116">Retrieves the type of an item in the report server database or SharePoint library, if the item exists.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="f00db-117">보고서 서버 데이터베이스 또는 SharePoint 라이브러리의 항목에 대한 하나 이상의 속성 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-117">Returns the values of one or more properties on an item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|<span data-ttu-id="f00db-118">항목의 정의 또는 콘텐츠를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-118">Retrieves the definition or content for an item.</span></span> <span data-ttu-id="f00db-119">이 메서드는 `Report`, `Model`, `Dataset`, `Component`, `Resource` 및 `DataSource` 항목 유형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-119">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|<span data-ttu-id="f00db-120">항목과 연결된 카탈로그 항목 참조 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-120">Returns a list of catalog item references associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|<span data-ttu-id="f00db-121">스케일 아웃 배포에 있는 모든 보고서 서버 인스턴스 또는 연결된 보고서 서버 인스턴스에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-121">Returns information on the connected report server instance or all the report server instances in a scale-out deployment.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="f00db-122">시스템 속성을 하나 이상 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-122">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|<span data-ttu-id="f00db-123">지정된 폴더의 자식 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-123">Gets a list of children of a specified folder.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|<span data-ttu-id="f00db-124">지원되는 자격 증명 검색 옵션 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-124">Returns a list of supported credential retrieval options.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|<span data-ttu-id="f00db-125">보고서 서버 구성 파일에 나타나는 이벤트 확장 프로그램 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-125">Returns a list of event extensions as they appear in the report server configuration file.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|<span data-ttu-id="f00db-126">보고서 서버에서 실행 중인 작업 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-126">Returns a list of jobs running on the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|<span data-ttu-id="f00db-127">지정된 확장 유형에 대해 구성된 확장 프로그램 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-127">Returns a list of extensions that are configured for a given extension type.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|<span data-ttu-id="f00db-128">지원되는 확장 유형 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-128">Returns a list of supported extension types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|<span data-ttu-id="f00db-129">지원되는 카탈로그 항목 유형 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-129">Returns a list of supported catalog item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|<span data-ttu-id="f00db-130">지원되는 작업 동작 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-130">Returns a list of supported job actions.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|<span data-ttu-id="f00db-131">지원되는 작업 상태 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-131">Returns a list of supported job states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|<span data-ttu-id="f00db-132">지원되는 작업 유형 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-132">Returns a list of supported job types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|<span data-ttu-id="f00db-133">지정된 항목의 부모 항목을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-133">Retrieves parent items for the given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|<span data-ttu-id="f00db-134">지원되는 보안 범위 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-134">Returns a list of supported security scopes.</span></span>|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|<span data-ttu-id="f00db-135">웹 서비스 요청을 하는 현재 사용자를 로그아웃시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-135">Logs out the current user making Web service requests.</span></span> <span data-ttu-id="f00db-136">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-136">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|<span data-ttu-id="f00db-137">보고서 서버 웹 서비스에 사용자를 로그온하고 사용자 요청을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-137">Logs on a user and authenticates a user request to the Report Server Web service.</span></span> <span data-ttu-id="f00db-138">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-138">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|<span data-ttu-id="f00db-139">항목과 연결된 카탈로그 항목을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-139">Sets the catalog items associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|<span data-ttu-id="f00db-140">항목을 이동하거나 항목 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-140">Moves and/or renames an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="f00db-141">항목 속성을 하나 이상 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-141">Sets one or more properties of an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|<span data-ttu-id="f00db-142">지정된 항목의 정의 또는 콘텐츠를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-142">Sets the definition or content for a specified item.</span></span> <span data-ttu-id="f00db-143">이 메서드는 `Report`, `Model`, `Dataset`, `Component`, `Resource` 및 `DataSource` 항목 유형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-143">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="f00db-144">보고서 서버 또는 SharePoint 팜에서 시스템 속성을 하나 이상 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-144">Sets one or more system properties in the report server or SharePoint farm.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|<span data-ttu-id="f00db-145">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 확장 프로그램 설정의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f00db-145">Validates [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f00db-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f00db-146">See Also</span></span>  
 <span data-ttu-id="f00db-147">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="f00db-147">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="f00db-148">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="f00db-148">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="f00db-149">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f00db-149">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="f00db-150">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f00db-150">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
