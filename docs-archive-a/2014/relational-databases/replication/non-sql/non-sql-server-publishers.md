---
title: SQL Server 이외 게시자 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f15f07dbf294d697afd385318f3dbf1447c8e2d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646349"
---
# <a name="non-sql-server-publishers"></a><span data-ttu-id="ff072-102">SQL Server 이외 게시자</span><span class="sxs-lookup"><span data-stu-id="ff072-102">Non-SQL Server Publishers</span></span>
  <span data-ttu-id="ff072-103">이외의 원본에서 데이터를 게시 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 데이터를 통합할 수 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ff072-103">Publishing data from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sources allows you to consolidate data in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ff072-104">는 Oracle 데이터베이스에서 게시된 스냅샷 또는 트랜잭션 데이터를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-104">can subscribe to snapshot or transactional data published from an Oracle database.</span></span> <span data-ttu-id="ff072-105">Oracle에서 게시에 대한 자세한 내용은 [Oracle 게시 개요](oracle-publishing-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff072-105">For more information about publishing from Oracle, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="ff072-106">SQL Server 이외의 구독자에 대한 다른 유형의 복제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="ff072-107">Oracle 게시는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="ff072-108">데이터를 이동하려면 변경 데이터 캡처 및 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]를 사용하여 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="ff072-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스에서 게시 작업은 다음과 같은 시나리오에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-109">Publishing from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="ff072-110">시나리오</span><span class="sxs-lookup"><span data-stu-id="ff072-110">Scenario</span></span>|<span data-ttu-id="ff072-111">설명</span><span class="sxs-lookup"><span data-stu-id="ff072-111">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="ff072-112">.NET Framework 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="ff072-112">.NET Framework application deployments</span></span>|<span data-ttu-id="ff072-113">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 이외 데이터베이스에서 복제한 데이터 작업 시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio 및[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용하여 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-113">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="ff072-114">데이터 웨어하우징 준비 서버(staging server)</span><span class="sxs-lookup"><span data-stu-id="ff072-114">Data warehousing staging servers</span></span>|<span data-ttu-id="ff072-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 준비 데이터베이스와[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스의 동기화를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-115">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="ff072-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff072-116">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="ff072-117">원본 시스템의 변경 내용을 복제하면서 실시간으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 대한 애플리케이션을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-117">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="ff072-118">마이그레이션에 만족하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ff072-118">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff072-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff072-119">See Also</span></span>  
 [<span data-ttu-id="ff072-120">다른 유형의 데이터베이스 복제</span><span class="sxs-lookup"><span data-stu-id="ff072-120">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
