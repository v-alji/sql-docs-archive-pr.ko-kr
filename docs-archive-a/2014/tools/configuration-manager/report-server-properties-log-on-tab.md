---
title: 보고서 서버 속성(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: f54be594-f290-4db2-bf18-fd2521728a4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2fca58ee9b419613bc8f1dbd325481efc9069c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652467"
---
# <a name="report-server-properties-log-on-tab"></a><span data-ttu-id="3097f-102">보고서 서버 속성(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="3097f-102">Report Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="3097f-103">**보고서 서버 속성** 대화 상자의 **로그온** 탭을 사용하여 보고서 서버 서비스에서 사용할 계정을 지정할 수 있으며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-103">Use the **Log On** tab of the **Report Server Properties** dialog box to specify the account used by the Report Server service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3097f-104">옵션</span><span class="sxs-lookup"><span data-stu-id="3097f-104">Options</span></span>  
 <span data-ttu-id="3097f-105">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="3097f-105">**Local System account**</span></span>  
 <span data-ttu-id="3097f-106">암호를 요구하지 않는 로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="3097f-107">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 다른 서버와 상호 작용하지 못하도록 서비스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="3097f-108">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="3097f-108">**This account**</span></span>  
 <span data-ttu-id="3097f-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3097f-110">에서는 서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="3097f-111">계정 선택 방법은 온라인 설명서에서 "Windows 서비스 계정 설정" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3097f-111">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="3097f-112">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="3097f-112">**Account Name**</span></span>  
 <span data-ttu-id="3097f-113">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="3097f-114">**암호**</span><span class="sxs-lookup"><span data-stu-id="3097f-114">**Password**</span></span>  
 <span data-ttu-id="3097f-115">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="3097f-116">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="3097f-116">**Confirm password**</span></span>  
 <span data-ttu-id="3097f-117">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="3097f-118">**시작**</span><span class="sxs-lookup"><span data-stu-id="3097f-118">**Start**</span></span>  
 <span data-ttu-id="3097f-119">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-119">Start the service.</span></span>  
  
 <span data-ttu-id="3097f-120">**중지**</span><span class="sxs-lookup"><span data-stu-id="3097f-120">**Stop**</span></span>  
 <span data-ttu-id="3097f-121">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-121">Stop the service.</span></span>  
  
 <span data-ttu-id="3097f-122">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="3097f-122">**Pause**</span></span>  
 <span data-ttu-id="3097f-123">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-123">Pause the service.</span></span>  
  
 <span data-ttu-id="3097f-124">**재개**</span><span class="sxs-lookup"><span data-stu-id="3097f-124">**Resume**</span></span>  
 <span data-ttu-id="3097f-125">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3097f-125">Resume a paused service.</span></span>  
  
  
