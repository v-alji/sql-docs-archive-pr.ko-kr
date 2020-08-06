---
title: 다중 인스턴스 보고서 서버 배포를 위한 URL 예약 (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2e51813ca2c85d089864dc5d2516e21ed975de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639396"
---
# <a name="url-reservations-for-multi-instance-report-server-deployments--ssrs-configuration-manager"></a><span data-ttu-id="b597e-102">다중 인스턴스 보고서 서버 배포를 위한 URL 예약(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="b597e-102">URL Reservations for Multi-Instance Report Server Deployments  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="b597e-103">같은 컴퓨터에 여러 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 설치하는 경우 각 인스턴스의 URL 예약을 어떻게 정의할지 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-103">If you install multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer, you must consider how you will define the URL reservations for each instance.</span></span> <span data-ttu-id="b597e-104">각 인스턴스 내에서 보고서 서버 웹 서비스와 보고서 관리자에는 각각 한 개 이상의 URL 예약이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-104">Within each instance, the Report Server Web service and Report Manager must have at least one URL reservation each.</span></span> <span data-ttu-id="b597e-105">전체 예약 집합은 HTTP.SYS에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-105">The entire set of reservations must be unique in HTTP.SYS.</span></span>  
  
 <span data-ttu-id="b597e-106">중복된 URL은 서비스가 시작할 때 URL을 등록하는 동안 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-106">Duplicate URLs are detected during URL registration, which occurs when the service starts.</span></span> <span data-ttu-id="b597e-107">고유하지 않은 URL 예약을 만든 경우 서비스를 시작하기 전까지는 이름 충돌이 검색되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-107">If you create URL reservations that are not unique, the name conflict might not be detected until you start the service.</span></span> <span data-ttu-id="b597e-108">따라서 명명 규칙에 따라 모든 값을 고유하게 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-108">For this reason, make sure that you follow naming conventions or rules to ensure all values are unique.</span></span>  
  
## <a name="default-naming-conventions"></a><span data-ttu-id="b597e-109">기본 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="b597e-109">Default Naming Conventions</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="b597e-110">명명된 인스턴스 내에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-110">can be installed within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named instance.</span></span> <span data-ttu-id="b597e-111">명명된 인스턴스 내에 보고서 서버를 설치하거나 구성하면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 제공하는 기본 URL 예약의 가상 디렉터리에 인스턴스 이름이 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-111">When you install or configure a report server within a named instance, the instance name is automatically included in the virtual directory in the default URL reservation that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides.</span></span> <span data-ttu-id="b597e-112">다음 표에서는 기본 인스턴스 및 명명된 인스턴스에 대한 URL 예약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-112">The following table shows the URL reservations for a default instance and a named instance.</span></span>  
  
|<span data-ttu-id="b597e-113">SQL Server 인스턴스</span><span class="sxs-lookup"><span data-stu-id="b597e-113">SQL Server Instance</span></span>|<span data-ttu-id="b597e-114">기본 URL 예약</span><span class="sxs-lookup"><span data-stu-id="b597e-114">Default URL Reservation</span></span>|  
|-------------------------|-----------------------------|  
|<span data-ttu-id="b597e-115">기본 인스턴스(MSSQLServer)</span><span class="sxs-lookup"><span data-stu-id="b597e-115">Default (MSSQLServer)</span></span>|http://+:80/reportserver|  
|<span data-ttu-id="b597e-116">명명된 인스턴스(MynamedInstance)</span><span class="sxs-lookup"><span data-stu-id="b597e-116">Named (MynamedInstance)</span></span>|http://+:80/reportserver_MyNamedInstance|  
  
 <span data-ttu-id="b597e-117">명명된 인스턴스의 경우 가상 디렉터리에 해당 인스턴스 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-117">For the named instance, the virtual directory includes the instance name.</span></span> <span data-ttu-id="b597e-118">기본 인스턴스 및 명명된 인스턴스는 모두 같은 포트에서 수신하지만 고유한 가상 디렉터리 이름에 따라 요청을 수신할 보고서 서버가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-118">Both the default instance and the named instance listen on the same port, but the unique virtual directory names determine which report server gets the request.</span></span>  
  
 <span data-ttu-id="b597e-119">보고서 서버 인스턴스를 구별할 수 있는 가상 디렉터리 이름을 사용하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-119">Best practice recommendations are to use the virtual directory name to distinguish among the report server instance.</span></span> <span data-ttu-id="b597e-120">이렇게 하면 URL과 대상 인스턴스 간의 관계가 명확해지고 애플리케이션 이름이 전체 시스템에서 고유하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-120">It provides a clear correspondence between a URL and the target instance, and ensures that the application names are unique across the whole system.</span></span>  
  
## <a name="custom-naming-conventions"></a><span data-ttu-id="b597e-121">사용자 지정 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="b597e-121">Custom Naming Conventions</span></span>  
 <span data-ttu-id="b597e-122">인스턴스 이름을 사용하는 것이 좋지만 URL 구문 및 사용자 지정 명명 규칙을 사용하여 URL 예약의 고유한 이름 제약 조건을 충족할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-122">Although using the instance name is recommended, you can use the URL syntax and your own naming conventions to meet the unique name constraints for URL reservations.</span></span> <span data-ttu-id="b597e-123">다음 예에서는 각 인스턴스의 고유한 URL을 만드는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-123">The following examples illustrate different approaches for creating unique URLs for each instance.</span></span>  
  
|<span data-ttu-id="b597e-124">보고서 서버 기본 인스턴스(MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="b597e-124">Report Server default instance (MSSQLSERVER)</span></span>|<span data-ttu-id="b597e-125">ReportServer_MyNamedInstance</span><span class="sxs-lookup"><span data-stu-id="b597e-125">ReportServer_MyNamedInstance</span></span>|<span data-ttu-id="b597e-126">고유성</span><span class="sxs-lookup"><span data-stu-id="b597e-126">Uniqueness</span></span>|  
|----------------------------------------------------|-----------------------------------|----------------|  
|http://+:80/reportserver|http://+:8888/reportserver|<span data-ttu-id="b597e-127">각 인스턴스가 다른 포트에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-127">Each instance listens on a different port.</span></span>|  
|`http://www.contoso.com/reportserver`|`http://SRVR-46/reportserver`|<span data-ttu-id="b597e-128">각 인스턴스가 다른 서버 이름(정규화된 도메인 이름 및 컴퓨터 이름)에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-128">Each instance responds to different server names (fully qualified domain name, and machine name).</span></span>|  
  
## <a name="uniqueness-requirements"></a><span data-ttu-id="b597e-129">고유성 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b597e-129">Uniqueness Requirements</span></span>  
 <span data-ttu-id="b597e-130">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서 사용되는 기본 기술에는 고유 이름 관련 요구 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-130">The underlying technologies used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] impose requirements around unique names.</span></span> <span data-ttu-id="b597e-131">HTTP.SYS의 리포지토리 내에서 모든 URL이 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-131">HTTP.SYS requires that all URLs within its repository be unique.</span></span> <span data-ttu-id="b597e-132">포트, 호스트 이름 또는 가상 디렉터리 이름을 변경하여 고유한 URL을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-132">You can vary the port, host name, or virtual directory name to create a unique URL.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="b597e-133">을 사용하려면 애플리케이션 ID가 동일한 프로세스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-133">requires that application identities be unique within the same process.</span></span> <span data-ttu-id="b597e-134">이러한 요구 사항은 가상 디렉터리 이름에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-134">This requirement affects the virtual directory names.</span></span> <span data-ttu-id="b597e-135">따라서 동일한 보고서 서버 인스턴스 내에서 중복되는 가상 디렉터리 이름을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b597e-135">It specifies that you cannot duplicate a virtual directory name within the same report server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b597e-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b597e-136">See Also</span></span>  
 <span data-ttu-id="b597e-137">[보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b597e-137">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="b597e-138">URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="b597e-138">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](configure-a-url-ssrs-configuration-manager.md)  
  
  
