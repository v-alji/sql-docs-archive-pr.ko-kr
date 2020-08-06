---
title: 보고서 서버 사이트에서 ISAPI 필터가 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bff1834ddf1b8f90787a47a8fd58a240d2b715d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740716"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a><span data-ttu-id="1111b-102">ISAPI 필터가 보고서 서버 사이트에서 검색됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="1111b-102">ISAPI filters detected on the report server site (Upgrade Advisor)</span></span>
  <span data-ttu-id="1111b-103">업그레이드 관리자가 보고서 서버와 보고서 관리자 가상 디렉터리를 호스팅하는 웹 사이트에서 하나 이상의 ISAPI 필터를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-103">Upgrade Advisor detected one or more ISAPI filters on the Web site that hosts the report server and Report Manager virtual directories.</span></span> <span data-ttu-id="1111b-104">ISAPI 필터는에서 지원 되지 않습니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1111b-104">ISAPI filters are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="1111b-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]전용.</span><span class="sxs-lookup"><span data-stu-id="1111b-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native .</span></span>|  
  
## <a name="component"></a><span data-ttu-id="1111b-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1111b-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="1111b-107">Description</span><span class="sxs-lookup"><span data-stu-id="1111b-107">Description</span></span>  
 <span data-ttu-id="1111b-108">업그레이드하기 전에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 애플리케이션이 웹 사이트에 대한 ISAPI 필터를 사용하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-108">Before upgrading, verify whether the ISAPI filters on the Web site are used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications.</span></span> <span data-ttu-id="1111b-109">ISAPI 필터가 필요하지 않으면 보고서 서버를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-109">If you do not require the ISAPI filter, you can upgrade the report server.</span></span> <span data-ttu-id="1111b-110">설치 프로그램은 IIS에서 실행되는 ISAPI 필터에 대한 지원 없이 기본 URL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-110">Setup will create the default URLs, without support for the ISAPI filter that runs in IIS.</span></span> <span data-ttu-id="1111b-111">ISAPI 필터가 필요하면 ISAPI 필터를 호스팅하는 다른 방법(예: ISA Server를 사용하거나 IIS에서 ISAPI 필터를 계속 호스팅하는 방법)을 찾을 때까지 업그레이드하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1111b-111">If you require the ISAPI filter, do not upgrade until you find an alternative way of hosting the ISAPI filter (for example, using ISA Server or continuing to host the ISAPI filter in IIS).</span></span> <span data-ttu-id="1111b-112">보고서 서버는 특정 시나리오에서 ISAPI 필터의 대체로 ASP.NET HTTPModules를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-112">The report server supports ASP.NET HTTPModules as a replacement for ISAPI filters in certain scenarios.</span></span> <span data-ttu-id="1111b-113">자세한 내용은 MSDN에서 ASP.NET 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1111b-113">For more information, see the ASP.NET documentation on MSDN.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="1111b-114">수정 동작</span><span class="sxs-lookup"><span data-stu-id="1111b-114">Corrective Action</span></span>  
 <span data-ttu-id="1111b-115">배포에 필요한 ISAPI 필터를 호스팅하는 별도의 솔루션을 평가하고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1111b-115">Evaluate and use a separate solution for hosting ISAPI filters required by your deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1111b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1111b-116">See Also</span></span>  
 [<span data-ttu-id="1111b-117">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1111b-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
