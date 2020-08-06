---
title: SQL Server 속성(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 405073fc-eaa3-43c6-bf82-2cd58cacc1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: adec9ed7c69023218baa96ab8f8edbb6f2b365bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651406"
---
# <a name="sql-server-properties-log-on-tab"></a><span data-ttu-id="f4fbb-102">SQL Server 속성(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="f4fbb-102">SQL Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="f4fbb-103">**SQL Server 속성** 대화 상자의 **로그온** 탭을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에서 사용할 계정을 지정하고 계정의 암호를 변경하며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-103">Use the **Log On** tab of the **SQL Server Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="f4fbb-104">계정의 암호를 변경하면 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-104">Changing the password of an account takes effect immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4fbb-105">클러스터형 인스턴스의 서비스에서 사용하는 계정 이름을 변경하는 경우 새 계정은 변경되는 서비스의 설치 중에 지정한 도메인 그룹의 멤버여야 합니다. 그렇지 않으면 해당 그룹에 멤버를 추가할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="f4fbb-106">그룹 멤버 자격을 수정할 권한이 없을 경우 도메인 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="f4fbb-107">서비스를 실행할 계정을 선택하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "Windows 서비스 계정 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-107">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4fbb-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f4fbb-108">Options</span></span>  
 <span data-ttu-id="f4fbb-109">**기본 제공 계정**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-109">**Built-in account**</span></span>  
 <span data-ttu-id="f4fbb-110">**로컬 시스템**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-110">**Local System**</span></span>  
 -   <span data-ttu-id="f4fbb-111">로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-111">Specify the local system account.</span></span> <span data-ttu-id="f4fbb-112">이 계정에는 암호가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-112">This account does not require a password.</span></span> <span data-ttu-id="f4fbb-113">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="f4fbb-114">**로컬 서비스**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-114">**Local Service**</span></span>  
 -   <span data-ttu-id="f4fbb-115">로컬 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-115">Specify the local service account.</span></span> <span data-ttu-id="f4fbb-116">이 계정에는 암호가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-116">This account does not require a password.</span></span> <span data-ttu-id="f4fbb-117">그러나 로컬 서비스 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-117">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="f4fbb-118">**네트워크 서비스**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-118">**Network Service**</span></span>  
 -   <span data-ttu-id="f4fbb-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 대해 네트워크 서비스 계정을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-119">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="f4fbb-120">이러한 서비스에 대해서는 로컬 사용자 또는 도메인 사용자 계정이 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-120">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="f4fbb-121">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-121">**This account**</span></span>  
 <span data-ttu-id="f4fbb-122">Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-122">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="f4fbb-123">서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-123">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="f4fbb-124">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-124">**Account Name**</span></span>  
 <span data-ttu-id="f4fbb-125">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-125">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="f4fbb-126">**암호**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-126">**Password**</span></span>  
 <span data-ttu-id="f4fbb-127">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-127">Type the password of the account.</span></span>  
  
 <span data-ttu-id="f4fbb-128">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-128">**Confirm password**</span></span>  
 <span data-ttu-id="f4fbb-129">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-129">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="f4fbb-130">**시작**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-130">**Start**</span></span>  
 <span data-ttu-id="f4fbb-131">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-131">Start the service.</span></span>  
  
 <span data-ttu-id="f4fbb-132">**중지**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-132">**Stop**</span></span>  
 <span data-ttu-id="f4fbb-133">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-133">Stop the service.</span></span>  
  
 <span data-ttu-id="f4fbb-134">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-134">**Pause**</span></span>  
 <span data-ttu-id="f4fbb-135">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-135">Pause the service.</span></span>  
  
 <span data-ttu-id="f4fbb-136">**재개**</span><span class="sxs-lookup"><span data-stu-id="f4fbb-136">**Resume**</span></span>  
 <span data-ttu-id="f4fbb-137">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-137">Resume a paused service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f4fbb-138">기본적으로 로컬 Administrators 그룹의 멤버만 서비스를 시작, 중지, 일시 중지, 재개 또는 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-138">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="f4fbb-139">관리자가 아닌 사용자에게 서비스 관리 권한을 부여하려면 [Windows Server 2003에서 사용자에게 서비스 관리 권한을 부여하는 방법](https://support.microsoft.com/kb/325349)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-139">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="f4fbb-140">이 프로세스는 다른 Windows 버전에서도 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-140">(The process is similar on other versions of Windows.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4fbb-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]시작 시 "구현되지 않았습니다[0x80004001]"라는 구가 포함된 WMI 오류가 발생할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 대상 컴퓨터에 설치되어 있지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4fbb-141">When starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a WMI error containing the phrase "not implemented [0x80004001]" may indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not installed on the target computer.</span></span>  
  
  
