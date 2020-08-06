---
title: 구성할 서버 선택(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18e36f5c8ec020b3859dc847d1bbfc019817bcd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648578"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a><span data-ttu-id="75649-102">구성할 서버 선택(데이터베이스 미러링 보안 구성 마법사)</span><span class="sxs-lookup"><span data-stu-id="75649-102">Choose Servers to Configure (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="75649-103">이 페이지를 사용하여 지금 구성할 서버 인스턴스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75649-103">Use this page to specify which server instances you want to configure now.</span></span> <span data-ttu-id="75649-104">마법사를 계속하려면 서버 인스턴스를 적어도 하나 이상 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75649-104">You must select at least one server instance before continuing the wizard.</span></span>  
  
 <span data-ttu-id="75649-105">서버 인스턴스에 대한 확인란을 선택 취소하면 해당 인스턴스가 변경되지 않지만</span><span class="sxs-lookup"><span data-stu-id="75649-105">If you clear the check box for a server instance, the wizard will not make any changes to it.</span></span> <span data-ttu-id="75649-106">해당 인스턴스에 대한 정보를 입력하라는 메시지가 나타나고 이 정보가 다른 서버 인스턴스 구성의 일부로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="75649-106">The wizard, however, will ask you to enter information about that instance and save this information as part of the configuration of the other server instances.</span></span> <span data-ttu-id="75649-107">예를 들어 미러링 모니터 서버 인스턴스에 대한 확인란을 선택 취소하면 주 서버 인스턴스와 미러 서버 인스턴스에 저장된 보안 구성의 일부로 해당 계정에 대한 로그인을 만들어야 하기 때문에 미러링 모니터 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 입력하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="75649-107">For example, if you clear the check box for the witness server instance, the wizard will ask you to enter the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the witness because a login for that account must be created as part of the security configuration saved at the principal and mirror server instances.</span></span>  
  
 <span data-ttu-id="75649-108">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="75649-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="75649-109">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="75649-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="75649-110">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="75649-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="75649-111">옵션</span><span class="sxs-lookup"><span data-stu-id="75649-111">Options</span></span>  
 <span data-ttu-id="75649-112">**주 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="75649-112">**Principal server instance**</span></span>  
 <span data-ttu-id="75649-113">주 서버에 대한 보안을 구성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75649-113">Select to configure security for the principal server.</span></span>  
  
 <span data-ttu-id="75649-114">**미러 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="75649-114">**Mirror server instance**</span></span>  
 <span data-ttu-id="75649-115">미러 서버에 대한 보안을 구성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75649-115">Select to configure security for the mirror server.</span></span>  
  
 <span data-ttu-id="75649-116">**미러링 모니터 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="75649-116">**Witness server instance**</span></span>  
 <span data-ttu-id="75649-117">미러링 모니터 서버(있는 경우)에 대한 보안을 구성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75649-117">Select to configure security for the witness server (if present).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75649-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75649-118">See Also</span></span>  
 <span data-ttu-id="75649-119">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="75649-119">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="75649-120">데이터베이스 미러링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="75649-120">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
