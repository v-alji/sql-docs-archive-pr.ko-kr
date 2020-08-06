---
title: 다른 유형의 데이터베이스 복제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8988a425bc9519d43b8100e4cd34418114edae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736180"
---
# <a name="heterogeneous-database-replication"></a><span data-ttu-id="3912d-102">다른 유형의 데이터베이스 복제</span><span class="sxs-lookup"><span data-stu-id="3912d-102">Heterogeneous Database Replication</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="3912d-103">에서는 트랜잭션 및 스냅샷 복제에 대해 다음과 같이 다른 유형의 시나리오를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-103">supports the following heterogeneous scenarios for transactional and snapshot replication:</span></span>  
  
-   <span data-ttu-id="3912d-104">Oracle에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="3912d-104">Publishing data from Oracle to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3912d-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자로 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="3912d-105">Publishing data from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="3912d-106">SQL Server 이외의 구독자에 대한 다른 유형의 복제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="3912d-107">Oracle 게시는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="3912d-108">데이터를 이동하려면 변경 데이터 캡처 및 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]를 사용하여 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a><span data-ttu-id="3912d-109">Oracle에서 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="3912d-109">Publishing Data from Oracle</span></span>  
 <span data-ttu-id="3912d-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용하여 Oracle에서 데이터를 게시할 수 있습니다. 이때 대부분의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 스냅샷 및 트랜잭션 복제 기능을 동일한 방식으로 간단하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-110">You can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to publish data from Oracle with most of the same features and ease-of-use as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot and transactional replication.</span></span> <span data-ttu-id="3912d-111">다음 시나리오에 대해서는 Oracle에서 데이터를 게시하는 것이 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-111">Publishing data from Oracle is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="3912d-112">시나리오</span><span class="sxs-lookup"><span data-stu-id="3912d-112">Scenario</span></span>|<span data-ttu-id="3912d-113">설명</span><span class="sxs-lookup"><span data-stu-id="3912d-113">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="3912d-114">.NET Framework 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="3912d-114">.NET Framework application deployments</span></span>|<span data-ttu-id="3912d-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 이외 데이터베이스에서 복제한 데이터 작업 시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio 및[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용하여 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-115">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="3912d-116">데이터 웨어하우징 준비 서버(staging server)</span><span class="sxs-lookup"><span data-stu-id="3912d-116">Data warehousing staging servers</span></span>|<span data-ttu-id="3912d-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 준비 데이터베이스와[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스의 동기화를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-117">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="3912d-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3912d-118">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="3912d-119">원본 시스템의 변경 내용을 복제하면서 실시간으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 대한 애플리케이션을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-119">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="3912d-120">마이그레이션에 만족하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-120">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
 <span data-ttu-id="3912d-121">자세한 내용은 [Oracle 게시 개요](oracle-publishing-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3912d-121">For more information, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a><span data-ttu-id="3912d-122">SQL Server 이외 구독자에 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="3912d-122">Publishing Data to Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="3912d-123">다음[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스는 스냅샷 및 트랜잭션 게시의 구독자로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3912d-123">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases are supported as Subscribers to snapshot and transactional publications:</span></span>  
  
-   <span data-ttu-id="3912d-124">Oracle에서 지원하는 모든 플랫폼용 Oracle 제품</span><span class="sxs-lookup"><span data-stu-id="3912d-124">Oracle for all platforms that Oracle supports.</span></span>  
  
-   <span data-ttu-id="3912d-125">AS400, MVS, Unix, Linux 및 Windows용 IBM DB2</span><span class="sxs-lookup"><span data-stu-id="3912d-125">IBM DB2 for AS400, MVS, Unix, Linux, and Windows.</span></span>  
  
 <span data-ttu-id="3912d-126">자세한 내용은 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3912d-126">For more information, see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span>  
  
  
