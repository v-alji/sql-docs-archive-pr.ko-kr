---
title: 가상 디렉터리가 지정 되지 않음 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e20c48d0bf58d28cb2894baa26c2e11db26fab96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650405"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a><span data-ttu-id="f6ff1-102">가상 디렉터리가 지정되지 않음(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="f6ff1-102">Virtual directories are unspecified (Upgrade Advisor)</span></span>
  <span data-ttu-id="f6ff1-103">업그레이드 관리자가 보고서 서버 웹 서비스 또는 보고서 관리자에 대한 가상 디렉터리 설정을 검색하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-103">Upgrade Advisor did not detect virtual directory settings for the Report Server Web service or Report Manager.</span></span> <span data-ttu-id="f6ff1-104">업그레이드가 완료된 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 보고서 서버에 대한 URL 예약을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-104">After upgrade completes, you must configure URL reservations for the report server by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="f6ff1-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="f6ff1-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f6ff1-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="f6ff1-107">Description</span><span class="sxs-lookup"><span data-stu-id="f6ff1-107">Description</span></span>  
 <span data-ttu-id="f6ff1-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 업그레이드하는 동안에는 보고서 서버 웹 서비스 및 보고서 관리자의 새 URL이 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-108">Upgrading a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation includes reserving new URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="f6ff1-109">업그레이드 관리자가 업그레이드할 인스턴스에 대한 보고서 서버 또는 보고서 관리자의 가상 디렉터리를 검색하지 못했기 때문에 업그레이드 프로세스에 업그레이드된 보고서 서버용 URL 예약을 만드는 데 필요한 정보가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-109">Upgrade Advisor did not detect virtual directories for the report server or Report Manager for the instance to be upgraded, and therefore the upgrade process has insufficient information to create URL reservations for the upgraded report server.</span></span> <span data-ttu-id="f6ff1-110">업그레이드를 계속 진행할 수는 있지만 업그레이드된 설치 후에 보고서 서버 또는 보고서 관리자 가상 디렉터리는 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-110">Upgrade can continue, but the report server or Report Manager virtual directory will be undefined after the upgraded installation.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f6ff1-111">수정 동작</span><span class="sxs-lookup"><span data-stu-id="f6ff1-111">Corrective Action</span></span>  
 <span data-ttu-id="f6ff1-112">업그레이드 완료 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 보고서 서버 및 보고서 관리자의 URL을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-112">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to set the URLs for report server and Report Manager.</span></span> <span data-ttu-id="f6ff1-113">IIS 관리자를 사용하여 더 이상 필요하지 않은 모든 가상 디렉터리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ff1-113">Use IIS Manager to remove any virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="f6ff1-114">자세한 내용은 온라인 설명서의 [URL &#40;SSRS Configuration Manager&#41;구성](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) 을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f6ff1-114">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ff1-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6ff1-115">See Also</span></span>  
 [<span data-ttu-id="f6ff1-116">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ff1-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
