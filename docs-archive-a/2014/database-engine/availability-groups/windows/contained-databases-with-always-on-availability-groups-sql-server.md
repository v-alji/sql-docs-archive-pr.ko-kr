---
title: Always On 가용성 그룹이 있는 포함된 데이터베이스(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c8a0b41ee7224dad83fb41691a4898c15b7b38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646657"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a><span data-ttu-id="4f0a7-102">Always On 가용성 그룹에 포함된 데이터베이스(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4f0a7-102">Contained Databases with Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="4f0a7-103">이 항목에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 포함된 데이터베이스를 사용하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0a7-103">This topic contains information about the using a contained database with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="4f0a7-104">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="4f0a7-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="4f0a7-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4f0a7-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="4f0a7-106">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4f0a7-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="4f0a7-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="4f0a7-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="4f0a7-108">포함된 데이터베이스를 가용성 그룹에 추가하기 전에 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 `contained database authentication` 서버 옵션이 `1`로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0a7-108">Before adding a contained database to an availability group, ensure that the `contained database authentication` server option is set to `1` on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="4f0a7-109">자세한 내용은 [contained database authentication 서버 구성 옵션](../../configure-windows/contained-database-authentication-server-configuration-option.md) 및 [서버 구성 옵션&#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)에서 포함된 데이터베이스를 사용하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0a7-109">For more information, see [contained database authentication Server Configuration Option](../../configure-windows/contained-database-authentication-server-configuration-option.md) and [Server Configuration Options &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4f0a7-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4f0a7-110">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4f0a7-111">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4f0a7-111">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f0a7-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f0a7-112">See Also</span></span>  
 <span data-ttu-id="4f0a7-113">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f0a7-113">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="4f0a7-114">포함된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="4f0a7-114">Contained Databases</span></span>](../../../relational-databases/databases/contained-databases.md)  
  
  
