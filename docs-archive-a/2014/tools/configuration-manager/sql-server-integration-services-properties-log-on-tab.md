---
title: SQL Server Integration Services 속성(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfef02a82872ea1df25e7ccb8526e488aaa5f406
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737306"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a><span data-ttu-id="a3ed8-102">SQL Server Integration Services 속성(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="a3ed8-102">SQL Server Integration Services Properties (Log On Tab)</span></span>
  <span data-ttu-id="a3ed8-103">**속성** 대화 상자의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **로그온** 탭을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스에서 사용할 계정을 지정할 수 있으며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-103">Use the **Log On** tab of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to specify the account used by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a3ed8-104">옵션</span><span class="sxs-lookup"><span data-stu-id="a3ed8-104">Options</span></span>  
 <span data-ttu-id="a3ed8-105">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-105">**Local System account**</span></span>  
 <span data-ttu-id="a3ed8-106">암호를 요구하지 않는 로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="a3ed8-107">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 다른 서버와 상호 작용하지 못하도록 서비스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="a3ed8-108">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-108">**This account**</span></span>  
 <span data-ttu-id="a3ed8-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a3ed8-110">에서는 서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="a3ed8-111">계정 선택 방법은 온라인 설명서에서 "Windows 서비스 계정 설정" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-111">For information about selecting an account, search Books Online for the topic, "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="a3ed8-112">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-112">**Account Name**</span></span>  
 <span data-ttu-id="a3ed8-113">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="a3ed8-114">**암호**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-114">**Password**</span></span>  
 <span data-ttu-id="a3ed8-115">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="a3ed8-116">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-116">**Confirm password**</span></span>  
 <span data-ttu-id="a3ed8-117">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="a3ed8-118">**시작**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-118">**Start**</span></span>  
 <span data-ttu-id="a3ed8-119">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-119">Start the service.</span></span>  
  
 <span data-ttu-id="a3ed8-120">**중지**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-120">**Stop**</span></span>  
 <span data-ttu-id="a3ed8-121">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-121">Stop the service.</span></span>  
  
 <span data-ttu-id="a3ed8-122">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-122">**Pause**</span></span>  
 <span data-ttu-id="a3ed8-123">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-123">Pause the service.</span></span>  
  
 <span data-ttu-id="a3ed8-124">**재개**</span><span class="sxs-lookup"><span data-stu-id="a3ed8-124">**Resume**</span></span>  
 <span data-ttu-id="a3ed8-125">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ed8-125">Resume a paused service.</span></span>  
  
  
