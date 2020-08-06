---
title: IIS 이전 버전과의 호환성 구성 요소가 검색 되지 않음 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a5aad54a01b3840e121c6a63de0ea26f35921fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660293"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a><span data-ttu-id="64ea0-102">IIS 이전 버전과의 호환성 구성 요소가 검색되지 않음(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="64ea0-102">IIS backward compatibility components were not detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="64ea0-103">업그레이드 관리자가 설치 프로그램이 새 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL을 만들기 위해 사용하는 정보를 제공하는 IIS 구성 요소 및 설정을 검색하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-103">Upgrade Advisor did not detect IIS components and settings that provide information used by Setup to create new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLS.</span></span>  
  
||  
|-|  
|<span data-ttu-id="64ea0-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="64ea0-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="64ea0-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="64ea0-106">Description</span><span class="sxs-lookup"><span data-stu-id="64ea0-106">Description</span></span>  
 <span data-ttu-id="64ea0-107">IIS에 보고서 서버 및 보고서 관리자 가상 디렉터리에 대한 정보를 제공하는 구성 요소가 포함되어 있지만 이러한 구성 요소가 보고서 서버 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-107">IIS includes components that provide information about the report server and Report Manager virtual directories, and those components are not installed on the report server computer.</span></span> <span data-ttu-id="64ea0-108">업그레이드를 계속 진행할 수는 있지만 업그레이드하는 동안 보고서 서버 또는 보고서 관리자의 URL이 다시 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-108">Upgrade can continue, but URLs for the report server or Report Manager will not be recreated by upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="64ea0-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="64ea0-109">Corrective Action</span></span>  
 <span data-ttu-id="64ea0-110">업그레이드 완료 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 보고서 서버 또는 보고서 관리자의 URL을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-110">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set the URLs for report server or Report Manager.</span></span> <span data-ttu-id="64ea0-111">IIS 관리자를 사용하여 더 이상 필요하지 않은 가상 디렉터리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="64ea0-111">Use IIS Manager to remove the virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="64ea0-112">자세한 내용은 온라인 설명서의 [URL &#40;SSRS Configuration Manager&#41;구성](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) 을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="64ea0-112">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ea0-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64ea0-113">See Also</span></span>  
 [<span data-ttu-id="64ea0-114">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="64ea0-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
