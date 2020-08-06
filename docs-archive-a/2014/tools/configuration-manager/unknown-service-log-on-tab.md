---
title: 알 수 없는 서비스 (로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0bda49cd95475d4f922f41ebe1701a814c3f60fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647414"
---
# <a name="unknown-service-log-on-tab"></a><span data-ttu-id="14b46-102">알 수 없는 서비스(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="14b46-102">Unknown Service (Log On Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="14b46-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자가 이 서비스를 식별할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is unable to identify this service.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14b46-104">구성 관리자는 서비스가 실행되는 컴퓨터의 WMI 공급자로부터 서비스 정보를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-104">Configuration Manager receives service information from the WMI provider on the computer running the service.</span></span> <span data-ttu-id="14b46-105">서비스 속성을 읽는 동안 오류가 발생했거나 서비스 속성이 완전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-105">Either there was an error while reading the service properties, or the service properties are not complete.</span></span> <span data-ttu-id="14b46-106">이 문제를 해결하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 닫은 후 다시 열거나 서비스가 실행되는 컴퓨터의 WMI 공급자를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="14b46-106">To resolve the problem, try closing and reopening [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or check the WMI provider on the computer running the service.</span></span>  
  
 <span data-ttu-id="14b46-107">WMI 공급자는 Windows 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-107">The WMI provider is a Windows component.</span></span> <span data-ttu-id="14b46-108">WMI 공급자에 대한 사용 권한을 확인하는 방법은 SQL Server 온라인 설명서의 "방법: WMI를 구성하여 SQL Server 도구에 서버 상태 표시"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14b46-108">For information on how to check permissions on the WMI provider, see "How to: Configure WMI to Show Server Status in SQL Server Tools" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="14b46-109">올바른 서비스가 표시되는 경우 **알 수 없는 서비스 속성** 대화 상자의 **로그온** 탭을 사용하여 이 서비스에서 사용할 계정을 지정할 수 있으며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-109">If you believe you are viewing the correct service, use the **Log On** tab of the **Unknown Service Properties** dialog box to specify the account used by this service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="14b46-110">옵션</span><span class="sxs-lookup"><span data-stu-id="14b46-110">Options</span></span>  
 <span data-ttu-id="14b46-111">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="14b46-111">**Local System account**</span></span>  
 <span data-ttu-id="14b46-112">암호를 요구하지 않는 로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-112">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="14b46-113">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="14b46-114">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="14b46-114">**This account**</span></span>  
 <span data-ttu-id="14b46-115">Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-115">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="14b46-116">서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-116">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="14b46-117">계정 선택 방법은 SQL Server 온라인 설명서의 "Windows 서비스 계정 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14b46-117">For information about selecting an account, "Setting Up Windows Service Accounts" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="14b46-118">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="14b46-118">**Account Name**</span></span>  
 <span data-ttu-id="14b46-119">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-119">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="14b46-120">**암호**</span><span class="sxs-lookup"><span data-stu-id="14b46-120">**Password**</span></span>  
 <span data-ttu-id="14b46-121">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-121">Type the password of the account.</span></span>  
  
 <span data-ttu-id="14b46-122">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="14b46-122">**Confirm password**</span></span>  
 <span data-ttu-id="14b46-123">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-123">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="14b46-124">**시작**</span><span class="sxs-lookup"><span data-stu-id="14b46-124">**Start**</span></span>  
 <span data-ttu-id="14b46-125">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-125">Start the service.</span></span>  
  
 <span data-ttu-id="14b46-126">**중지**</span><span class="sxs-lookup"><span data-stu-id="14b46-126">**Stop**</span></span>  
 <span data-ttu-id="14b46-127">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-127">Stop the service.</span></span>  
  
 <span data-ttu-id="14b46-128">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="14b46-128">**Pause**</span></span>  
 <span data-ttu-id="14b46-129">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-129">Pause the service.</span></span>  
  
 <span data-ttu-id="14b46-130">**재개**</span><span class="sxs-lookup"><span data-stu-id="14b46-130">**Resume**</span></span>  
 <span data-ttu-id="14b46-131">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="14b46-131">Resume a paused service.</span></span>  
  
  
