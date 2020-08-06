---
title: IP 주소 제한 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732295"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a><span data-ttu-id="68010-102">IP 주소 제한이 검색됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="68010-102">IP address restriction detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="68010-103">업그레이드 관리자가 보고서 서버 또는 보고서 관리자 가상 디렉터리를 호스팅하는 IIS 웹 사이트에서 하나 이상의 IP 주소 제한을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="68010-103">Upgrade Advisor detected one or more IP address restrictions on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="68010-104">는 IP 주소 제한에 대한 기본 지원을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68010-104">does not provide native support for IP address restrictions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="68010-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]전용.</span><span class="sxs-lookup"><span data-stu-id="68010-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="68010-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="68010-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="68010-107">Description</span><span class="sxs-lookup"><span data-stu-id="68010-107">Description</span></span>  
 <span data-ttu-id="68010-108">설치 프로그램이 업그레이드된 보고서 서버용으로 생성된 URL에 대한 IP 주소 제한을 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68010-108">Setup cannot define IP address restrictions on URLs created for an upgraded report server.</span></span> <span data-ttu-id="68010-109">업그레이드를 계속 진행할 수는 있지만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL에 대한 IP 주소 제한은 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68010-109">Upgrade can continue, but IP address restrictions will not be defined on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="68010-110">수정 동작</span><span class="sxs-lookup"><span data-stu-id="68010-110">Corrective Action</span></span>  
 <span data-ttu-id="68010-111">업그레이드 후 ISA Server, 방화벽 소프트웨어 또는 다른 솔루션을 사용하여 특정 IP 주소에서 보고서 서버로의 요청을 허용하거나 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68010-111">After upgrade, use ISA Server, your firewall software, or another solution to allow or exclude requests from specific IP addresses to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68010-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68010-112">See Also</span></span>  
 [<span data-ttu-id="68010-113">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="68010-113">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
