---
title: 보고서 서버로 직접 탐색 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ab4d146bba4bd87de56b30ad100b57f79eb68de3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660873"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a><span data-ttu-id="e360a-102">보고서 서버로 직접 이동(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="e360a-102">Direct Browsing to Report Server (Upgrade Advisor)</span></span>
  <span data-ttu-id="e360a-103">업그레이드 관리자가 현재 설치 된에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버 가상 디렉터리로 직접 검색 하 고 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e360a-103">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory.</span></span>  
  
||  
|-|  
|<span data-ttu-id="e360a-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="e360a-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="e360a-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e360a-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e360a-106">설명</span><span class="sxs-lookup"><span data-stu-id="e360a-106">Description</span></span>  
 <span data-ttu-id="e360a-107">업그레이드 관리자가 현재 설치 된에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버 가상 디렉터리 (예: **http:// \<server name> /reportserver**)로 직접 검색 하 고 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e360a-107">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory, for example **http://\<server name>/ReportServer**.</span></span> <span data-ttu-id="e360a-108">이는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 현재 버전에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e360a-108">This is not supported in current versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e360a-109">이 규칙은 경고이며 업그레이드가 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e360a-109">This rule is a warning and upgrade is not blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e360a-110">수정 동작</span><span class="sxs-lookup"><span data-stu-id="e360a-110">Corrective Action</span></span>  
 <span data-ttu-id="e360a-111">문서 라이브러리에 대 한 SharePoint 사용자 인터페이스를 사용 하 여 찾아보거나 **http:// \<server name> /sharepoint site>/_vti_bin/sharepoint**를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e360a-111">Browse using the SharePoint user interface for document libraries or use **http://\<server name>/sharepoint site>/_vti_bin/reportserver**.</span></span>  
  
  
