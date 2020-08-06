---
title: Microsoft SQL Server Reporting Services SharePoint 공유 서비스가 함께 설치 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8a26fedd892dfb26dea4616efd46d3b3748b508
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653114"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a><span data-ttu-id="49a89-102">Microsoft SQL Server Reporting Services SharePoint 공유 서비스가 병렬로 설치됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="49a89-102">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side (Upgrade Advisor)</span></span>
  <span data-ttu-id="49a89-103">업그레이드 관리자 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 SharePoint 공유 서비스가 이전 버전의와 나란히 설치 되었음을 발견 했습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="49a89-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared service is installed side by side with a previous version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="49a89-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="49a89-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="49a89-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="49a89-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="49a89-106">Description</span><span class="sxs-lookup"><span data-stu-id="49a89-106">Description</span></span>  
 <span data-ttu-id="49a89-107">업그레이드 관리자가 sharepoint 공유 서비스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 아키텍처를 기반으로 하지 않는 이전 버전의와 나란히 설치 되어 있음을 발견 했습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="49a89-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Shared service is installed side by side with a previous version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is not based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="49a89-108">컴퓨터에 이전 및 최신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 관련 기술이 함께 설치되어 있기 때문에 업그레이드가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="49a89-108">Because the computer has both older and newer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint related technologies installed side by side, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="49a89-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="49a89-109">Corrective Action</span></span>  
 <span data-ttu-id="49a89-110">업그레이드를 계속하려면 기존 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 중 하나를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49a89-110">To continue with upgrade, you must uninstall one of the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installations.</span></span> <span data-ttu-id="49a89-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 중 하나를 제거한 후 업그레이드 관리자를 다시 실행하여 다른 업그레이드 문제가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="49a89-111">After removing one of the installations of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
  
