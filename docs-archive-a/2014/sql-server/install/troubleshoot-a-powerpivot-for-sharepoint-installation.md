---
title: SharePoint용 PowerPivot 설치 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3adc27132d976288c14ac702baae0b842e8aef0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650446"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="b8ca6-102">SharePoint용 PowerPivot 설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b8ca6-102">Troubleshoot a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="b8ca6-103">예상한 페이지 및 기능 대신 오류가 발생할 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-103">If you get errors instead of the pages and features you expect, do the following.</span></span>  
  
-   <span data-ttu-id="b8ca6-104">알려진 설치 문제에 대한 해결 방법은 SharePoint 및 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에 대한 릴리스 정보를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-104">Review release notes for both SharePoint and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to get workarounds for known installation problems.</span></span> <span data-ttu-id="b8ca6-105">릴리스 정보는 소프트웨어를 다운로드한 Microsoft 사이트나 설치 미디어에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-105">Release notes are provided with the installation media or on the Microsoft site from which you downloaded the software.</span></span>  
  
    -   <span data-ttu-id="b8ca6-106">[SQL Server 2014 릴리스 정보](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b8ca6-106">[SQL Server 2014 Release Notes](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).</span></span>  
  
-   <span data-ttu-id="b8ca6-107">Technet wiki 항목인 [PowerPivot 및 기타 추가 기능의 설치 문제 해결](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-107">See the Technet wiki topic, [Troubleshooting Installations of PowerPivot (and other add-ins)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).</span></span>  
  
## <a name="issues"></a><span data-ttu-id="b8ca6-108">문제</span><span class="sxs-lookup"><span data-stu-id="b8ca6-108">Issues</span></span>  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a><span data-ttu-id="b8ca6-109">PowerPivot 갤러리 축소판 이미지가 빨간색 X로 표시됨</span><span class="sxs-lookup"><span data-stu-id="b8ca6-109">PowerPivot Gallery Thumbnail images show as a red X</span></span>  
 <span data-ttu-id="b8ca6-110">한 가지 가능한 원인은 **사이트 모음에 대한 PowerPivot 기능 통합** 이 활성 상태가 아닌 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-110">One Possible cause is the **PowerPivot features Integration for Site Collections** is not active.</span></span> <span data-ttu-id="b8ca6-111">다음을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-111">Complete the following:</span></span>  
  
1.  <span data-ttu-id="b8ca6-112">PowerPivot 갤러리 라이브러리의 기어 아이콘 ![SharePoint 설정](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정") 또는 **홈** 목록에서 **사이트 설정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-112">In the PowerPivot Gallery library, click **Site Settings** from either the gear icon ![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") or the **Home** list.</span></span>  
  
2.  <span data-ttu-id="b8ca6-113">**사이트 모음 관리** 섹션에서 **사이트 모음 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-113">In the **Site Collection Administration** section, click **Site Collection Features**.</span></span>  
  
3.  <span data-ttu-id="b8ca6-114">**사이트 모음 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-114">Click **Site Collection Features**.</span></span>  
  
4.  <span data-ttu-id="b8ca6-115">**사이트 모음에 대한 PowerPivot 기능 통합** 이 **활성**상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ca6-115">Verify **PowerPivot features Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="b8ca6-116">이 문제의 추가 원인은 [PowerPivot 갤러리의 아이콘에 빨간색 X가 표시](https://support.microsoft.com/kb/2361559) 되는 경우를 참조 하세요 https://support.microsoft.com/kb/2361559) .</span><span class="sxs-lookup"><span data-stu-id="b8ca6-116">For additional causes of this issue, see [PowerPivot Gallery shows Red X's for Icons](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).</span></span>  
  
  
