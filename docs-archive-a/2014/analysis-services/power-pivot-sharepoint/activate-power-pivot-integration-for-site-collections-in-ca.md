---
title: 중앙 관리에서 사이트 모음에 대 한 PowerPivot 기능 통합 활성화 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b565434cba197d04327e833d4ac6eab3caf96646
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730927"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a><span data-ttu-id="e5b9a-102">중앙 관리에서 사이트 모음에 대해 PowerPivot 기능 통합 활성화</span><span class="sxs-lookup"><span data-stu-id="e5b9a-102">Activate PowerPivot Feature Integration for Site Collections in Central Administration</span></span>
  <span data-ttu-id="e5b9a-103">기존 팜 설치 옵션을 사용하여 SQL Server SharePoint용 PowerPivot을 설치한 경우 특정 사이트 모음에 대해 PowerPivot 기능 통합을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-103">Activating PowerPivot feature integration for specific site collections is required if you used the Existing Farm installation option to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="e5b9a-104">새 서버 옵션을 사용해 SharePoint용 PowerPivot을 설치한 경우에는 SQL Server 설치 프로그램에서 배포를 구성할 때 루트 사이트 모음에 대해 PowerPivot 기능 통합을 이미 활성화했기 때문에 이 태스크를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-104">If you installed PowerPivot for SharePoint using the New Server option, you can skip this task because SQL Server Setup already activated PowerPivot feature integration for the root site collection when it configured your deployment.</span></span>  
  
 <span data-ttu-id="e5b9a-105">사이트 모음 수준에서 기능을 활성화하면 사이트에서 애플리케이션 페이지 및 템플릿을 사용할 수 있습니다. 여기에는 예약된 데이터 새로 고침을 구성하는 애플리케이션 페이지와 PowerPivot 갤러리 및 데이터 피드 라이브러리를 구성하는 애플리케이션 페이지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-105">Feature activation at the site collection level is necessary to make application pages and templates available to your sites, including configuration pages for scheduled data refresh and application pages for PowerPivot Gallery and Data Feed libraries.</span></span>  
  
 <span data-ttu-id="e5b9a-106">PowerPivot 쿼리 처리를 지원하는 각 사이트 모음에 대해 PowerPivot 통합을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-106">You must activate PowerPivot integration for each site collection that supports PowerPivot query processing.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e5b9a-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e5b9a-107">Prerequisites</span></span>  
 <span data-ttu-id="e5b9a-108">사이트 모음 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-108">You must be a site collection administrator.</span></span>  
  
## <a name="activate-powerpivot-features"></a><span data-ttu-id="e5b9a-109">PowerPivot 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="e5b9a-109">Activate PowerPivot Features</span></span>  
  
1.  <span data-ttu-id="e5b9a-110">SharePoint  사이트에서 **사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-110">On a SharePoint site, click **Site Actions**.</span></span>  
  
     <span data-ttu-id="e5b9a-111">기본적으로 SharePoint 웹 애플리케이션은 포트 80을 통해 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-111">By default, SharePoint web applications are accessed through port 80.</span></span> <span data-ttu-id="e5b9a-112">즉, http://\<computer name>을 입력하여 루트 사이트 모음을 열어서 SharePoint 사이트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-112">This means that you can often access a SharePoint site by entering http://\<computer name> to open the root site collection.</span></span>  
  
2.  <span data-ttu-id="e5b9a-113">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-113">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="e5b9a-114">사이트 컬렉션 관리에서 **사이트 컬렉션 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-114">In Site Collection Administration, click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="e5b9a-115">페이지를 아래로 스크롤하여 **PowerPivot 통합 사이트 컬렉션 기능**을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-115">Scroll down the page until you find **PowerPivot Integration Site Collection Feature**.</span></span>  
  
5.  <span data-ttu-id="e5b9a-116">**활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-116">Click **Activate**.</span></span>  
  
6.  <span data-ttu-id="e5b9a-117">각 사이트를 열고 **사이트 작업**을 클릭하여 추가 사이트 모음에 대해 위 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b9a-117">Repeat for additional site collections by opening each site and clicking **Site Actions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b9a-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5b9a-118">See Also</span></span>  
 <span data-ttu-id="e5b9a-119">[중앙 관리에서 PowerPivot 서버 관리 및 구성](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="e5b9a-119">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 <span data-ttu-id="e5b9a-120">[초기 구성 &#40;SharePoint용 PowerPivot&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="e5b9a-120">[Initial Configuration &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="e5b9a-121">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="e5b9a-121">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
