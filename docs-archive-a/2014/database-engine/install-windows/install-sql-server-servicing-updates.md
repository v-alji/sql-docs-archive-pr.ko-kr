---
title: SQL Server 2014 서비스 업데이트 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace0fd187386d9a9d96e82f61d1efaa254f08c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729755"
---
# <a name="install-sql-server-2014-servicing-updates"></a><span data-ttu-id="b234b-102">SQL Server 2014 서비스 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="b234b-102">Install SQL Server 2014 Servicing Updates</span></span>
  <span data-ttu-id="b234b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]용 업데이트 설치에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-103">This topic provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b234b-104">이 섹션에서는 다음과 같은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-104">This section provides information about the following:</span></span>  
  
-   <span data-ttu-id="b234b-105">새로 설치하는 동안 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 용 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="b234b-105">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] during a new installation</span></span>  
  
-   <span data-ttu-id="b234b-106">설치 후 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 용 업데이트 설치.</span><span class="sxs-lookup"><span data-stu-id="b234b-106">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed.</span></span>  
  
 <span data-ttu-id="b234b-107">시스템이 최신 보안 업데이트로 업데이트되도록 고객이 적절한 시기에 최신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 업데이트를 확인하고 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-107">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span>  
  
## <a name="installing-updates-for-sscurrent-during-a-new-installation"></a><span data-ttu-id="b234b-108">새로 설치하는 동안 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 용 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="b234b-108">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] During a New Installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b234b-109">설치 프로그램에서 최신 제품 업데이트를 주 제품 설치와 통합하여 주 제품과 해당 업데이트가 동시에 설치되게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-109">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span> <span data-ttu-id="b234b-110">제품 업데이트는 다음 위치에서 적용 가능한 업데이트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-110">Product Update can search for the applicable updates from:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b234b-111">Update</span><span class="sxs-lookup"><span data-stu-id="b234b-111">Update</span></span>  
  
-   <span data-ttu-id="b234b-112">WSUS(Windows Server Update Services)</span><span class="sxs-lookup"><span data-stu-id="b234b-112">Windows Server Update Services (WSUS)</span></span>  
  
-   <span data-ttu-id="b234b-113">로컬 폴더</span><span class="sxs-lookup"><span data-stu-id="b234b-113">A local folder</span></span>  
  
-   <span data-ttu-id="b234b-114">네트워크 공유</span><span class="sxs-lookup"><span data-stu-id="b234b-114">A network share</span></span>  
  
 <span data-ttu-id="b234b-115">설치 프로그램에서 최신 버전의 적용 가능한 업데이트를 찾으면 이를 다운로드하고 현재의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로세스와 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-115">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="b234b-116">제품 업데이트에는 누적 업데이트, 서비스 팩 또는 서비스 팩과 누적 업데이트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-116">Product Update can include a cumulative update, service pack, or service pack plus cumulative update.</span></span> <span data-ttu-id="b234b-117">제품 업데이트 기능은 PCU1에서 제공 되는 [통합 설치 기능](https://go.microsoft.com/fwlink/?LinkId=219945) 을 확장 한 것입니다 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b234b-117">Product Update functionality is an extension of the [Slipstream Functionality](https://go.microsoft.com/fwlink/?LinkId=219945) that was available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.</span></span>  
  
## <a name="installing-updates-for-sscurrent-after-it-has-already-been-installed"></a><span data-ttu-id="b234b-118">설치 후 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 용 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="b234b-118">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed</span></span>  
 <span data-ttu-id="b234b-119">설치 된 인스턴스에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 사용 가능한 업데이트 (일반 배포 릴리스), SP (서비스 팩), SP (서비스 팩) 및 최신 CU (누적 업데이트)를 모두 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-119">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply all available updates: General Distribution Releases (GDR - security/critical updates), Service Packs (SP), as well as the latest available Cumulative Update (CU).</span></span>  
  
 <span data-ttu-id="b234b-120">서비스 릴리스 유형에 따라 SQL Server 업데이트는 MU (Microsoft 업데이트), Microsoft 다운로드 센터 및/또는 고객 지원 서비스 핫픽스 서버를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-120">Depending on the type of servicing release, SQL Server updates are available via Microsoft Update (MU), the Microsoft Download Center, and/or the Customer Support Services hotfix Server.</span></span> <span data-ttu-id="b234b-121">SQL Server에 대 한 보안 및 중요 업데이트는 Microsoft 업데이트에서 자동으로 제공 됩니다. 이러한 업데이트를 보려면 제어판의 Windows 업데이트를 통해 MU로 옵트인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-121">Security and Critical updates for SQL Server are automatically provided by Microsoft Update (to be able to see these updates you need to opt-in to MU through Windows Update in Control panel).</span></span> <span data-ttu-id="b234b-122">서비스 팩은 다운로드 센터 뿐만 아니라 선택적/중요 다운로드로 MU에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-122">Service Packs are available on MU as Optional/Important downloads as well as the Download Center.</span></span> <span data-ttu-id="b234b-123">누적 업데이트는 CU 기술 자료 문서에 제공 된 Microsoft 핫픽스 다운로드 서버에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b234b-123">Cumulative updates are available on the Microsoft hotfix download server provided in CU Knowledge Base articles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b234b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b234b-124">See Also</span></span>  
 <span data-ttu-id="b234b-125">[설치 마법사 &#40;설치 프로그램에서 SQL Server 2014을 설치&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="b234b-125">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="b234b-126">[명령 프롬프트에서 업데이트 설치](installing-updates-from-the-command-prompt.md) [SQL Server 2014 &#40;설치 프로그램의 인스턴스에 기능을 추가&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span><span class="sxs-lookup"><span data-stu-id="b234b-126">[Installing updates from the command prompt](installing-updates-from-the-command-prompt.md) [Add Features to an Instance of SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span></span>  
 [<span data-ttu-id="b234b-127">SQL Server 2014 설치 삭제</span><span class="sxs-lookup"><span data-stu-id="b234b-127">Drop a SQL Server 2014 Installation</span></span>](repair-a-failed-sql-server-installation.md)  
  
  
