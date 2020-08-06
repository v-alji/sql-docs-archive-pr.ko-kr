---
title: 업그레이드 관리자 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], when to use
- SQL Server Upgrade Advisor, when to use
- when to use Upgrade Advisor
ms.assetid: 5f26a7b9-1ac2-442c-8316-87b078db3baf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 75a16e57734493cdd7ac00e7bad3124eb7a99d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650371"
---
# <a name="working-with-upgrade-advisor"></a><span data-ttu-id="b49cf-102">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="b49cf-102">Working with Upgrade Advisor</span></span>
  <span data-ttu-id="b49cf-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로의 성공적인 업그레이드를 위해 업그레이드 관리자는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 설치에서 해결해야 하는 문제를 식별하는 중앙 콘솔을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-103">To help ensure that your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is successful, Upgrade Advisor provides a central console to identify issues to address in your installations before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="b49cf-104">업그레이드 관리자를 사용하여 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-104">You can use Upgrade Advisor to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b49cf-105">로컬 또는 원격 서버에서 이전 버전의 구성 요소 분석</span><span class="sxs-lookup"><span data-stu-id="b49cf-105">Analyze previous version's components on local or remote servers.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b49cf-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 원격 인스턴스는 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-106">You cannot analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b49cf-107">분석 결과 보기</span><span class="sxs-lookup"><span data-stu-id="b49cf-107">View the results of the analysis.</span></span>  
  
 <span data-ttu-id="b49cf-108">업그레이드 관리자에는 분석기와 뷰어가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-108">Upgrade Advisor includes an analyzer and a viewer.</span></span> <span data-ttu-id="b49cf-109">업그레이드 관리자 분석 마법사가 선택된 구성 요소를 분석하면</span><span class="sxs-lookup"><span data-stu-id="b49cf-109">The Upgrade Advisor Analysis Wizard analyzes the components you select.</span></span> <span data-ttu-id="b49cf-110">분석기는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 처리해야 하는 문제에 대한 사용자 지정 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-110">The analyzer then generates custom reports about issues that you must handle before you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b49cf-111">사용자 지정 보고서는 업그레이드 관리자 보고서 뷰어를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-111">You use the Upgrade Advisor Report Viewer to view the custom reports.</span></span> <span data-ttu-id="b49cf-112">업그레이드 관리자 분석에서 검색 하는 내용에 대 한 자세한 내용은 [업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b49cf-112">For more information about what Upgrade Advisor analysis detects, see [Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="b49cf-113">이 섹션의 항목에서는 업그레이드 관리자 기능에 대한 개요를 제공하고 업그레이드 관리자 및 업그레이드 관리자 보고서를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-113">The topics in this section provide an overview of Upgrade Advisor functionality and information about how to use Upgrade Advisor and Upgrade Advisor reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b49cf-114">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b49cf-114">In This Section</span></span>  
  
|<span data-ttu-id="b49cf-115">항목</span><span class="sxs-lookup"><span data-stu-id="b49cf-115">Topic</span></span>|<span data-ttu-id="b49cf-116">Description</span><span class="sxs-lookup"><span data-stu-id="b49cf-116">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b49cf-117">업그레이드 관리자 개요</span><span class="sxs-lookup"><span data-stu-id="b49cf-117">Overview of Upgrade Advisor</span></span>](../../../2014/sql-server/install/overview-of-upgrade-advisor.md)|<span data-ttu-id="b49cf-118">업그레이드 프로세스, 업그레이드 관리자 분석 마법사 및 업그레이드 관리자 보고서 뷰어에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-118">Provides an overview of the upgrade process, the Upgrade Advisor Analysis Wizard, and the Upgrade Advisor Report Viewer.</span></span>|  
|[<span data-ttu-id="b49cf-119">업그레이드 관리자 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="b49cf-119">Upgrade Advisor How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)|<span data-ttu-id="b49cf-120">일반적인 업그레이드 관리자 절차를 수행하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-120">Provides instructions to perform common Upgrade Advisor procedures.</span></span>|  
|[<span data-ttu-id="b49cf-121">업그레이드 관리자 사용자 인터페이스 참조</span><span class="sxs-lookup"><span data-stu-id="b49cf-121">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)|<span data-ttu-id="b49cf-122">업그레이드 관리자 분석 마법사 페이지에서 F1 키를 누르거나 **도움말** 을 클릭 하면 표시 되는 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49cf-122">Contains topics that appear if you press the F1 key or click **Help** on the Upgrade Advisor Analysis Wizard pages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b49cf-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b49cf-123">See Also</span></span>  
 <span data-ttu-id="b49cf-124">[업그레이드 관리자 설치](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="b49cf-124">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="b49cf-125">업그레이드 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b49cf-125">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
