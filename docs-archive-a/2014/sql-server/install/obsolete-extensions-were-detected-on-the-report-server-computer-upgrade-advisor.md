---
title: 보고서 서버 컴퓨터에서 사용 되지 않는 확장 프로그램이 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9da9c47285bf809fdf6c89d67e847304d7d29a81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660285"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a><span data-ttu-id="cd460-102">보고서 서버 컴퓨터에서 사용되지 않는 확장 프로그램이 검색됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="cd460-102">Obsolete extensions were detected on the report server computer (Upgrade Advisor)</span></span>
  <span data-ttu-id="cd460-103">업그레이드 관리자가 현재 릴리스에서 더 이상 사용되지 않는 렌더링 확장 프로그램을 하나 이상 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-103">Upgrade Advisor detected one or more rendering extensions that are no longer available in the current release.</span></span>  
  
||  
|-|  
|<span data-ttu-id="cd460-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="cd460-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="cd460-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cd460-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="cd460-106">Description</span><span class="sxs-lookup"><span data-stu-id="cd460-106">Description</span></span>  
 <span data-ttu-id="cd460-107">보고서 서버가 이 릴리스에서 사용이 중단된 하나 이상의 확장 프로그램을 사용하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-107">The report server is configured to use one or more extensions that have been discontinued in this release.</span></span> <span data-ttu-id="cd460-108">다음 확장 프로그램은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-108">Discontinued extensions include:</span></span>  
  
-   <span data-ttu-id="cd460-109">HTML OWC 렌더링 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="cd460-109">HTML OWC rendering extension</span></span>  
  
-   <span data-ttu-id="cd460-110">HTML 3.2 렌더링 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="cd460-110">HTML 3.2 rendering extension</span></span>  
  
 <span data-ttu-id="cd460-111">업그레이드를 계속 진행할 수는 있지만 지원되지 않는 기능은 업그레이드된 보고서 서버에서 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-111">Upgrade can continue, but the unsupported functionality will no longer be available on the upgraded report server.</span></span>  
  
 <span data-ttu-id="cd460-112">이러한 확장 프로그램이 필요한 경우 해당 요구 사항에 대한 대체 솔루션을 찾을 때까지 업그레이드하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="cd460-112">If you require these extensions, do not upgrade until you find an alternate solution to these requirements.</span></span> <span data-ttu-id="cd460-113">사용자는 동일하거나 유사한 기능을 제공하는 사용자 지정 렌더링 확장 프로그램을 구하거나 작성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-113">You might need to obtain or build a custom rendering extension that provides the same or similar functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="cd460-114">수정 동작</span><span class="sxs-lookup"><span data-stu-id="cd460-114">Corrective Action</span></span>  
 <span data-ttu-id="cd460-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 현재 포함되어 있는 기능 집합을 평가하여 지원 기능이 요구 사항을 충족시키는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cd460-115">Evaluate the current set of features that are included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to determine whether supported functionality meets your requirements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd460-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd460-116">See Also</span></span>  
 [<span data-ttu-id="cd460-117">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cd460-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
