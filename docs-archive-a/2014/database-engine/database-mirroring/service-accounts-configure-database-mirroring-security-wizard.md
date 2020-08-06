---
title: 서비스 계정(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58e49467a28e816c6592b1ded212b5aea0e6bc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733055"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a><span data-ttu-id="fb845-102">서비스 계정(데이터베이스 미러링 보안 구성 마법사)</span><span class="sxs-lookup"><span data-stu-id="fb845-102">Service Accounts (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="fb845-103">Windows 인증을 사용할 때 서버 인스턴스가 다른 계정을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대해 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-103">When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb845-104">이러한 서비스 계정은 모두 같은 도메인 또는 트러스트된 도메인에 있는 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-104">These service accounts must all be domain accounts (in the same or trusted domains).</span></span>  
  
 <span data-ttu-id="fb845-105">모든 서버 인스턴스가 동일한 도메인 계정을 사용하거나 인증서 기반 인증을 사용하는 경우 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-105">If all the server instances use the same domain account or use certificate-based authentication, leave the fields blank.</span></span> <span data-ttu-id="fb845-106">**마침**을 클릭하기만 하면 마법사가 자동으로 현재 마법사 계정을 기반으로 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-106">Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb845-107">서버 인스턴스의 데이터베이스 미러링 엔드포인트에서 인증서를 사용하도록 구성되어 있는 경우에는 서비스 계정 필드를 비워 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-107">If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.</span></span>  
  
 <span data-ttu-id="fb845-108">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="fb845-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="fb845-109">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fb845-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="fb845-110">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fb845-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="fb845-111">옵션</span><span class="sxs-lookup"><span data-stu-id="fb845-111">Options</span></span>  
 <span data-ttu-id="fb845-112">**주 서버**</span><span class="sxs-lookup"><span data-stu-id="fb845-112">**Principal**</span></span>  
 <span data-ttu-id="fb845-113">주 서버 인스턴스의 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-113">Specify the service account of the principal server instance.</span></span> <span data-ttu-id="fb845-114">도메인 이름을 대문자로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-114">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="fb845-115">*DOMAINNAME* \\ *사용자 이름*</span><span class="sxs-lookup"><span data-stu-id="fb845-115">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="fb845-116">**미러**</span><span class="sxs-lookup"><span data-stu-id="fb845-116">**Mirror**</span></span>  
 <span data-ttu-id="fb845-117">미러 서버 인스턴스의 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-117">Specify the service account of the mirror server instance.</span></span> <span data-ttu-id="fb845-118">도메인 이름을 대문자로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-118">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="fb845-119">*DOMAINNAME* \\ *사용자 이름*</span><span class="sxs-lookup"><span data-stu-id="fb845-119">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="fb845-120">**감시**</span><span class="sxs-lookup"><span data-stu-id="fb845-120">**Witness**</span></span>  
 <span data-ttu-id="fb845-121">미러링 모니터 서버 인스턴스의 서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-121">Specify the service account of the witness server instance.</span></span> <span data-ttu-id="fb845-122">도메인 이름을 대문자로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb845-122">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="fb845-123">*DOMAINNAME* \\ *사용자 이름*</span><span class="sxs-lookup"><span data-stu-id="fb845-123">*DOMAINNAME*\\*username*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb845-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb845-124">See Also</span></span>  
 <span data-ttu-id="fb845-125">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb845-125">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="fb845-126">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="fb845-126">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="fb845-127">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb845-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="fb845-128">데이터베이스 미러링을 위한 로그인 계정을 설정 하거나 &#40;SQL Server를 AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="fb845-128">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
