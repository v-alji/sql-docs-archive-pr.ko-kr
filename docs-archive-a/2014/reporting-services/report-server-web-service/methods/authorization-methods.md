---
title: 권한 부여 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b04a21b5075e939a4732e2f8ec219e169f4ba440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736043"
---
# <a name="authorization-methods"></a><span data-ttu-id="8e62a-102">권한 부여 메서드</span><span class="sxs-lookup"><span data-stu-id="8e62a-102">Authorization Methods</span></span>
  <span data-ttu-id="8e62a-103">다음 메서드를 사용하여 보고서 서버에서 태스크, 역할 및 정책을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-103">You can use these methods to manage tasks, roles, and policies on the report server.</span></span>  
  
|<span data-ttu-id="8e62a-104">방법</span><span class="sxs-lookup"><span data-stu-id="8e62a-104">Method</span></span>|<span data-ttu-id="8e62a-105">작업</span><span class="sxs-lookup"><span data-stu-id="8e62a-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|<span data-ttu-id="8e62a-106">보고서 서버 데이터베이스에 새 역할을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-106">Adds a new role to the report server database.</span></span> <span data-ttu-id="8e62a-107">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-107">This method =applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|<span data-ttu-id="8e62a-108">보고서 서버 데이터베이스에서 역할을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-108">Deletes a role from the report server database.</span></span> <span data-ttu-id="8e62a-109">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-109">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|<span data-ttu-id="8e62a-110">보고서 서버 데이터베이스 또는 SharePoint 라이브러리의 특정 항목과 연결된 사용자 권한을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-110">Returns the user permissions that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<span data-ttu-id="8e62a-111">보고서 서버 데이터베이스 또는 또는 SharePoint 라이브러리의 특정 항목과 연결된 정책을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-111">Returns the policies that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<span data-ttu-id="8e62a-112">역할 메타데이터 속성 및 관련 태스크 모음을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-112">Returns role metadata properties and a collection of associated tasks.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|<span data-ttu-id="8e62a-113">사용자의 시스템 사용 권한을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-113">Returns the user's system permissions.</span></span> <span data-ttu-id="8e62a-114">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-114">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<span data-ttu-id="8e62a-115">연결된 그룹 및 역할을 포함한 시스템 정책을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-115">Returns the system policies, including groups and roles with which they are associated.</span></span> <span data-ttu-id="8e62a-116">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-116">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|<span data-ttu-id="8e62a-117">보고서 서버 데이터베이스의 특정 항목과 연결된 정책을 삭제하고 항목에 대한 보안 정책을 부모의 보안 정책으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-117">Deletes the policies that are associated with a particular item in the report server database and sets the security policies for the item to those of its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<span data-ttu-id="8e62a-118"><xref:ReportService2010> 끝점을 사용하는 데 SSL(Secure Sockets Layer) 프로토콜이 필요한지 여부를 나타내는 부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-118">Returns a Boolean value that indicates whether the Secure Socket Layer (SSL) protocol is required to use the <xref:ReportService2010> end point.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|<span data-ttu-id="8e62a-119">보고서 서버에서 관리되는 역할의 이름과 설명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-119">Returns the names and descriptions of roles that are managed by the report server.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|<span data-ttu-id="8e62a-120"><xref:ReportExecution2005> 엔드포인트에서 호출될 때 보안 연결이 필요한 SOAP(Simple Object Access Protocol) 메서드 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-120">Returns a list of Simple Object Access Protocol (SOAP) methods in the <xref:ReportExecution2005> endpoint that require a secure connection when invoked.</span></span> <span data-ttu-id="8e62a-121">반환되는 메서드를 결정하는 데는 보고서 서버의 `SecureConnectionLevel` 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-121">The `SecureConnectionLevel` setting of the report server is used to determine which methods are returned.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|<span data-ttu-id="8e62a-122">보고서 서버에서 관리되는 태스크를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-122">Returns the tasks that are managed by the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|<span data-ttu-id="8e62a-123">지정된 항목과 연결된 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-123">Sets the policies that are associated with a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|<span data-ttu-id="8e62a-124">역할 메타데이터 속성을 설정하고 태스크 집합과 역할을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-124">Sets role metadata properties and associates a set of tasks with a role.</span></span> <span data-ttu-id="8e62a-125">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-125">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|<span data-ttu-id="8e62a-126">그룹 및 그룹과 연관된 역할을 정의하는 시스템 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-126">Sets the system policy that defines groups and their associated roles.</span></span> <span data-ttu-id="8e62a-127">이 메서드는 기본 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e62a-127">This method applies to native mode only.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e62a-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e62a-128">See Also</span></span>  
 <span data-ttu-id="8e62a-129">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="8e62a-129">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="8e62a-130">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="8e62a-130">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="8e62a-131">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="8e62a-131">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="8e62a-132">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8e62a-132">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
