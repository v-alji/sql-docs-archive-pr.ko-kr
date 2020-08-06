---
title: SQL Server Browser 속성(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727699"
---
# <a name="sql-server-browser-properties-log-on-tab"></a><span data-ttu-id="e2059-102">SQL Server Browser 속성(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="e2059-102">SQL Server Browser Properties (Log On Tab)</span></span>
  <span data-ttu-id="e2059-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 프로그램은 서버에서 서비스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e2059-104">Browser는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에 대해 들어오는 요청을 수신 대기하고 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e2059-105">Browser는 UDP 포트에서 수신하고 SSRP( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol)를 사용하여 인증되지 않은 요청을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-105">Browser listens on a UDP port and accepts unauthenticated requests using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP).</span></span>  
  
 <span data-ttu-id="e2059-106">계정의 암호를 변경하면 서비스를 다시 시작하지 않고 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-106">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2059-107">옵션</span><span class="sxs-lookup"><span data-stu-id="e2059-107">Options</span></span>  
 <span data-ttu-id="e2059-108">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="e2059-108">**Local System account**</span></span>  
 <span data-ttu-id="e2059-109">로컬 시스템 계정의 보안 컨텍스트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-109">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service in the security context of the Local System account.</span></span> <span data-ttu-id="e2059-110">가능하면 이보다 낮은 권한의 계정을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2059-110">When possible, use a low-permission account instead.</span></span>  
  
 <span data-ttu-id="e2059-111">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="e2059-111">**This account**</span></span>  
 <span data-ttu-id="e2059-112">Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-112">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="e2059-113">서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-113">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="e2059-114">계정 선택 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "Windows 서비스 계정 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2059-114">For information about selecting an account, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="e2059-115">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="e2059-115">**Browse**</span></span>  
 <span data-ttu-id="e2059-116">사용자 또는 기본 제공 보안 주체를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-116">Browse for a user or built-in security principal.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e2059-117">낮은 권한의 계정을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2059-117">Use a low-permission account.</span></span> <span data-ttu-id="e2059-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스에 필요한 권한에 대한 자세한 내용은 [SQL Server Browser 서비스](../../../2014/tools/configuration-manager/sql-server-browser-service.md)의 보안 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2059-118">For information about the permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service, see the Security section of [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="e2059-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="e2059-119">**Password**</span></span>  
 <span data-ttu-id="e2059-120">보안 주체의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-120">Enter the password of the security principal.</span></span>  
  
 <span data-ttu-id="e2059-121">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="e2059-121">**Confirm password**</span></span>  
 <span data-ttu-id="e2059-122">보안 주체의 암호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-122">Confirm the password of the security principal.</span></span>  
  
 <span data-ttu-id="e2059-123">**서비스 상태**</span><span class="sxs-lookup"><span data-stu-id="e2059-123">**Service status**</span></span>  
 <span data-ttu-id="e2059-124">이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-124">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="e2059-125">“ **...** ”는 상태 변경이 보류 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-125">"**...**" indicates a state change is pending.</span></span>  
  
 <span data-ttu-id="e2059-126">**시작**</span><span class="sxs-lookup"><span data-stu-id="e2059-126">**Start**</span></span>  
 <span data-ttu-id="e2059-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-127">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="e2059-128">**중지**</span><span class="sxs-lookup"><span data-stu-id="e2059-128">**Stop**</span></span>  
 <span data-ttu-id="e2059-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-129">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="e2059-130">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="e2059-130">**Pause**</span></span>  
 <span data-ttu-id="e2059-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-131">Pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="e2059-132">**재개**</span><span class="sxs-lookup"><span data-stu-id="e2059-132">**Resume**</span></span>  
 <span data-ttu-id="e2059-133">일시 중지한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="e2059-133">Resume a paused [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2059-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2059-134">See Also</span></span>  
 [<span data-ttu-id="e2059-135">SQL Server Browser 서비스</span><span class="sxs-lookup"><span data-stu-id="e2059-135">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
