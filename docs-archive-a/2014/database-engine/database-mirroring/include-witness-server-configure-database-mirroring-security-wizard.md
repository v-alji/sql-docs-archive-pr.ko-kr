---
title: 미러링 모니터 서버 포함(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 314d2205463436e2182b8d1a4cc0cc972213bd5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647195"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a><span data-ttu-id="c8fef-102">미러링 모니터 서버 포함(데이터베이스 미러링 보안 구성 마법사)</span><span class="sxs-lookup"><span data-stu-id="c8fef-102">Include Witness Server (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="c8fef-103">이 페이지를 사용하여 데이터베이스 미러링에 대한 보안 구성에 미러링 모니터 서버를 포함할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8fef-103">Use this page to specify whether you want to include a witness server in this security configuration for database mirroring.</span></span>  
  
 <span data-ttu-id="c8fef-104">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="c8fef-104">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="c8fef-105">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c8fef-105">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="c8fef-106">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c8fef-106">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="c8fef-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c8fef-107">Options</span></span>  
 <span data-ttu-id="c8fef-108">**예**</span><span class="sxs-lookup"><span data-stu-id="c8fef-108">**Yes**</span></span>  
 <span data-ttu-id="c8fef-109">보안 구성에 미러링 모니터 서버 인스턴스를 포함하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8fef-109">Click to include a witness server instance in the security configuration.</span></span> <span data-ttu-id="c8fef-110">주 서버 인스턴스에서 장애가 발생한 경우에 미러링 서버 인스턴스에 대한 자동 장애 조치(failover)가 있는 보호 우선 모드에서는 미러링 모니터 서버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c8fef-110">The witness is necessary for high-safety mode with automatic failover, which supports automatic failover to the mirror server instance if the principal server instance fails.</span></span>  
  
 <span data-ttu-id="c8fef-111">**아니요**</span><span class="sxs-lookup"><span data-stu-id="c8fef-111">**No**</span></span>  
 <span data-ttu-id="c8fef-112">미러링 모니터 서버를 포함하지 않고 보안을 구성하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8fef-112">Click to configure security without a witness.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fef-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8fef-113">See Also</span></span>  
 <span data-ttu-id="c8fef-114">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="c8fef-114">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="c8fef-115">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c8fef-115">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="c8fef-116">데이터베이스 미러링 모니터 서버</span><span class="sxs-lookup"><span data-stu-id="c8fef-116">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
