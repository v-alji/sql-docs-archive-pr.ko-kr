---
title: 업그레이드 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660856"
---
# <a name="resolving-upgrade-issues"></a><span data-ttu-id="1353f-102">업그레이드 문제 해결</span><span class="sxs-lookup"><span data-stu-id="1353f-102">Resolving Upgrade Issues</span></span>
  <span data-ttu-id="1353f-103">이 섹션의 항목에서는 검색 가능 여부에 관계없이 업그레이드 또는 업그레이드 이후 환경에 영향을 줄 수 있는 업그레이드 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-103">The topics in this section describe upgrade issues that can be detected as well as those that cannot be detected, but that might affect the upgrade or post-upgrade experience.</span></span> <span data-ttu-id="1353f-104">문제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소별로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-104">The issues are organized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1353f-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1353f-105">In This Section</span></span>  
  
-   [<span data-ttu-id="1353f-106">최신 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-106">Late-Breaking Upgrade Issues</span></span>](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [<span data-ttu-id="1353f-107">데이터베이스 엔진 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-107">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [<span data-ttu-id="1353f-108">전체 텍스트 Search 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-108">Full-Text Search Upgrade Issues</span></span>](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [<span data-ttu-id="1353f-109">복제 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-109">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [<span data-ttu-id="1353f-110">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1353f-110">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [<span data-ttu-id="1353f-111">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a><span data-ttu-id="1353f-112">업그레이드를 방해하는 문제</span><span class="sxs-lookup"><span data-stu-id="1353f-112">Issues That Prevent Upgrading</span></span>  
 <span data-ttu-id="1353f-113">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 일부 구성 또는 설정이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하는 것을 방해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-113">A few configurations or settings in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1353f-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 설치할 때 이러한 문제가 검색되면 설치 프로그램에서는 업그레이드 프로세스가 중지되고 업그레이드 관리자를 실행하고 차단 문제를 모두 해결하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-114">If Setup detects these issues when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Setup stops the upgrade process and requests that you run Upgrade Advisor and fix any blocking issues.</span></span>  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 <span data-ttu-id="1353f-115">다음 태스크가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 업그레이드 보고서에 나열되면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 필요한 동작을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-115">If the following tasks are listed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] upgrade report, you must perform the required actions before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
-   [<span data-ttu-id="1353f-116">데이터베이스 ID 32767 분리</span><span class="sxs-lookup"><span data-stu-id="1353f-116">Detach database ID 32767</span></span>](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [<span data-ttu-id="1353f-117">고정 서버 역할 이름과 일치하는 로그인 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-117">Rename logins matching fixed server role names</span></span>](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [<span data-ttu-id="1353f-118">sys 사용자 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-118">Rename user sys</span></span>](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [<span data-ttu-id="1353f-119">sp_rename을 사용하여 중복 인덱스 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1353f-119">Use sp_rename to rename duplicate index name</span></span>](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a><span data-ttu-id="1353f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1353f-120">See Also</span></span>  
 [<span data-ttu-id="1353f-121">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="1353f-121">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
