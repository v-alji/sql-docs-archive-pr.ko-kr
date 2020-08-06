---
title: SQL 전체 텍스트 필터 데몬 시작 관리자(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb3f23907e96214929617bf2923e46148c0ab1f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660230"
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a><span data-ttu-id="c4a50-102">SQL 전체 텍스트 필터 데몬 시작 관리자(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="c4a50-102">SQL Full-text Filter Daemon Launcher (Log On Tab)</span></span>
  <span data-ttu-id="c4a50-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 검색에서 SQL 전체 텍스트 필터 데몬 시작 관리자(FDHOST Launcher) 서비스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search.</span></span> <span data-ttu-id="c4a50-104">전체 텍스트 검색을 사용할 경우 이 서비스를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="c4a50-105">필터 데몬 호스트 프로세스에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "전체 텍스트 검색 아키텍처"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4a50-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="c4a50-106">**SQL 전체 텍스트 필터 데몬 시작 관리자 속성** 대화 상자의 **로그온** 탭을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 서비스에서 사용할 계정을 지정하고 계정의 암호를 변경하며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-106">Use the **Log On** tab of the **SQL Full-text Filter Daemon Launcher  Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="c4a50-107">계정의 암호를 변경하는 경우 서비스를 다시 시작해야 변경된 암호가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-107">Changing the password of an account takes affect after restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4a50-108">클러스터형 인스턴스의 서비스에서 사용하는 계정 이름을 변경하는 경우 새 계정은 서비스의 설치 중에 지정한 도메인 그룹의 멤버여야 합니다. 그렇지 않으면 해당 그룹에 멤버를 추가할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-108">When changing the account name used by a service on a clustered instance, either the new account must be a member of the domain group specified during setup for the service, or you must have permission to add members to that group.</span></span> <span data-ttu-id="c4a50-109">그룹 멤버 자격을 수정할 권한이 없을 경우 도메인 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4a50-109">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="c4a50-110">서비스를 실행할 계정을 선택하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "Windows 서비스 계정 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4a50-110">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c4a50-111">옵션</span><span class="sxs-lookup"><span data-stu-id="c4a50-111">Options</span></span>  
 <span data-ttu-id="c4a50-112">**기본 제공 계정**</span><span class="sxs-lookup"><span data-stu-id="c4a50-112">**Built-in account**</span></span>  
 <span data-ttu-id="c4a50-113">**로컬 시스템**</span><span class="sxs-lookup"><span data-stu-id="c4a50-113">**Local System**</span></span>  
 <span data-ttu-id="c4a50-114">로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-114">Specify the local system account.</span></span> <span data-ttu-id="c4a50-115">이 계정에는 암호가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-115">This account does not require a password.</span></span> <span data-ttu-id="c4a50-116">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-116">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="c4a50-117">**로컬 서비스**</span><span class="sxs-lookup"><span data-stu-id="c4a50-117">**Local Service**</span></span>  
 <span data-ttu-id="c4a50-118">로컬 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-118">Specify the local service account.</span></span> <span data-ttu-id="c4a50-119">이 계정에는 암호가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-119">This account does not require a password.</span></span> <span data-ttu-id="c4a50-120">그러나 로컬 서비스 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-120">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="c4a50-121">**네트워크 서비스**</span><span class="sxs-lookup"><span data-stu-id="c4a50-121">**Network Service**</span></span>  
 <span data-ttu-id="c4a50-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 대해서는 네트워크 서비스 계정을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-122">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="c4a50-123">이러한 서비스에 대해서는 로컬 사용자 또는 도메인 사용자 계정이 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-123">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="c4a50-124">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="c4a50-124">**This account**</span></span>  
 <span data-ttu-id="c4a50-125">Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-125">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="c4a50-126">서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-126">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="c4a50-127">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="c4a50-127">**Account Name**</span></span>  
 <span data-ttu-id="c4a50-128">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-128">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="c4a50-129">**암호**</span><span class="sxs-lookup"><span data-stu-id="c4a50-129">**Password**</span></span>  
 <span data-ttu-id="c4a50-130">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-130">Type the password of the account.</span></span>  
  
 <span data-ttu-id="c4a50-131">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="c4a50-131">**Confirm password**</span></span>  
 <span data-ttu-id="c4a50-132">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-132">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="c4a50-133">**시작**</span><span class="sxs-lookup"><span data-stu-id="c4a50-133">**Start**</span></span>  
 <span data-ttu-id="c4a50-134">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-134">Start the service.</span></span>  
  
 <span data-ttu-id="c4a50-135">**중지**</span><span class="sxs-lookup"><span data-stu-id="c4a50-135">**Stop**</span></span>  
 <span data-ttu-id="c4a50-136">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-136">Stop the service.</span></span>  
  
 <span data-ttu-id="c4a50-137">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="c4a50-137">**Pause**</span></span>  
 <span data-ttu-id="c4a50-138">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-138">Pause the service.</span></span> <span data-ttu-id="c4a50-139">이 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-139">Not available for this service.</span></span>  
  
 <span data-ttu-id="c4a50-140">**재개**</span><span class="sxs-lookup"><span data-stu-id="c4a50-140">**Resume**</span></span>  
 <span data-ttu-id="c4a50-141">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a50-141">Resume a paused service.</span></span>  
  
  
