---
title: '방법: 업그레이드 관리자 설치 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3ed5b66522126bfabc94bfa8036ec6c31ac04500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660312"
---
# <a name="how-to-install-upgrade-advisor"></a><span data-ttu-id="d6bcc-102">방법: 업그레이드 관리자 설치</span><span class="sxs-lookup"><span data-stu-id="d6bcc-102">How to: Install Upgrade Advisor</span></span>
  <span data-ttu-id="d6bcc-103">업그레이드 관리자는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 제외하고 지원되는 모든 구성 요소의 원격 분석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-103">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="d6bcc-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 검색하지 않는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있는 모든 컴퓨터에 업그레이드 관리자를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-104">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d6bcc-105">컴퓨터에는 업그레이드 관리자의 필수 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-105">The computer must also meet Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="d6bcc-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 인스턴스를 검색하는 경우에는 보고서 서버에 업그레이드 관리자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="d6bcc-107">자세한 내용은 [업그레이드 관리자 설치](../../../2014/sql-server/install/installing-upgrade-advisor.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-107">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
### <a name="to-install-upgrade-advisor"></a><span data-ttu-id="d6bcc-108">업그레이드 관리자를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="d6bcc-108">To install Upgrade Advisor</span></span>  
  
1.  <span data-ttu-id="d6bcc-109">다음 방법 중 하나를 사용하여 설치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-109">Start the installation using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="d6bcc-110">웹 사이트에서 설치 하는 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] **다운로드** 링크를 클릭 한 다음 **실행** 단추를 클릭 하 여 설치를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-110">If you are installing from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site, click the **Download** link and then click the **Run** button to start the installation.</span></span>  
  
    -   <span data-ttu-id="d6bcc-111">제품 미디어에서 설치 하는 경우 **redist** 폴더를 열고 **업그레이드 관리자** 폴더를 연 다음 **SQLUA.msi**를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-111">If you are installing from the product media, open the **redist** folder, open the **Upgrade Advisor** folder, and then double-click **SQLUA.msi**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6bcc-112">업그레이드 관리자를 사용하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-112">Upgrade Advisor requires the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4.</span></span> <span data-ttu-id="d6bcc-113">설치되어 있지 않거나 시험판 버전이 설치되어 있는 경우 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-113">If it is not installed, or if you have a pre-release version, an error message will appear.</span></span> <span data-ttu-id="d6bcc-114">이전 버전의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 모두 제거한 다음 최신 버전의 .NET Framework 4를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-114">Uninstall any earlier version of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and then install the latest version of .NET Framework 4.</span></span>  
    >   
    >  <span data-ttu-id="d6bcc-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom은 업그레이드 관리자 설치를 위한 필수 구성 요소 이며 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자 설치를 통해 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-115">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="d6bcc-116">설치 프로그램을 실행 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 기능 팩에서 scriptdom을 다운로드 하 여 설치 해야 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6bcc-116">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
2.  <span data-ttu-id="d6bcc-117">\*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자 설치 시작\*\* 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-117">On the **Welcome to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor Setup** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d6bcc-118">**사용권 계약** 페이지에서 사용권 계약을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-118">On the **License Agreement** page, read the license agreement.</span></span> <span data-ttu-id="d6bcc-119">동의 하면 **동의 함을 선택 하** 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-119">If you agree, select **I accept the license agreement** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d6bcc-120">**등록 정보** 페이지에서 사용자 이름과 회사 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-120">On the **Registration Information** page, enter your name and company.</span></span>  
  
5.  <span data-ttu-id="d6bcc-121">**기능 선택** 페이지에서 **설치 경로** 값을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-121">On the **Feature Selection** page, review the **Installation path** value.</span></span> <span data-ttu-id="d6bcc-122">필요한 경우 **찾아보기** 단추를 사용 하 여 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-122">If necessary, use the **Browse** button to change the location.</span></span> <span data-ttu-id="d6bcc-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-123">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d6bcc-124">**프로그램 설치 준비 완료** 페이지에서 **설치** 를 클릭 하 여 업그레이드 관리자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-124">On the **Ready to Install the Program** page, click **Install** to install Upgrade Advisor.</span></span>  
  
7.  <span data-ttu-id="d6bcc-125">마법사를 끝내려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bcc-125">Click **Finish** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bcc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6bcc-126">See Also</span></span>  
 [<span data-ttu-id="d6bcc-127">업그레이드 관리자 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d6bcc-127">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
