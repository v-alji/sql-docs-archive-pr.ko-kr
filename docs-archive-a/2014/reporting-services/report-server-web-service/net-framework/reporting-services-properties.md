---
title: Reporting Services 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61f1f50ea7a49acc616a36a4eaf1d3d5fcdf269a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730104"
---
# <a name="reporting-services-properties"></a><span data-ttu-id="de660-102">Reporting Services 속성</span><span class="sxs-lookup"><span data-stu-id="de660-102">Reporting Services Properties</span></span>
  <span data-ttu-id="de660-103">보고서 서버에서는 보고서 서버의 전역 시스템 속성 집합 및 보고서 서버 데이터베이스에 저장된 개별 항목과 연결된 항목 속성 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-103">The report server defines a set of system properties that are global to the report server and a set of item properties that are associated with an individual item stored in the report server database.</span></span> <span data-ttu-id="de660-104">보고서 서버에서 정의된 속성은 삭제할 수 없으며 읽기 전용인 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de660-104">Properties defined by the report server cannot be deleted, and in some cases they are read-only.</span></span> <span data-ttu-id="de660-105">애플리케이션에서 추가 사용자 정의 속성을 시스템 및 항목 속성에 추가하여 시스템 속성 및 항목 속성을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de660-105">An application can extend system properties and item properties by adding additional user-defined properties to the system and item properties.</span></span>  
  
 <span data-ttu-id="de660-106">다음 웹 서비스 메서드는 속성을 검색 하 고 설정 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-106">The following Web service methods retrieve and set [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] properties.</span></span>  
  
|<span data-ttu-id="de660-107">방법</span><span class="sxs-lookup"><span data-stu-id="de660-107">Method</span></span>|<span data-ttu-id="de660-108">작업</span><span class="sxs-lookup"><span data-stu-id="de660-108">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="de660-109">보고서 서버 데이터베이스의 항목에 대한 속성 값을 하나 이상 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-109">Returns the values of one or more properties on an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="de660-110">시스템 속성을 하나 이상 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-110">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="de660-111">보고서 서버 데이터베이스의 항목에 대한 속성을 하나 이상 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-111">Sets one or more properties of an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="de660-112">시스템 속성을 하나 이상 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-112">Sets one or more system properties.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="de660-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="de660-113">In This Section</span></span>  
  
|<span data-ttu-id="de660-114">항목</span><span class="sxs-lookup"><span data-stu-id="de660-114">Topic</span></span>|<span data-ttu-id="de660-115">Description</span><span class="sxs-lookup"><span data-stu-id="de660-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="de660-116">보고서 서버 항목 속성</span><span class="sxs-lookup"><span data-stu-id="de660-116">Report Server Item Properties</span></span>](reporting-services-properties-report-server-item-properties.md)|<span data-ttu-id="de660-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 항목별 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-117">Describes the item-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="de660-118">보고서 서버 시스템 속성</span><span class="sxs-lookup"><span data-stu-id="de660-118">Report Server System Properties</span></span>](reporting-services-properties-report-server-system-properties.md)|<span data-ttu-id="de660-119">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 시스템별 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de660-119">Describes the system-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de660-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de660-120">See Also</span></span>  
 <span data-ttu-id="de660-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="de660-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="de660-122">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="de660-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="de660-123">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="de660-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
