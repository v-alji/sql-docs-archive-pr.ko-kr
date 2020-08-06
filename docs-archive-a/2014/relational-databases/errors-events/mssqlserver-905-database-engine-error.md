---
title: MSSQLSERVER_905 | Microsoft 문서
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7dd3c8c5a287e2d123e2a9d1430ecd49b27f29f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650038"
---
# <a name="mssqlserver_905"></a><span data-ttu-id="074d0-102">MSSQLSERVER_905</span><span class="sxs-lookup"><span data-stu-id="074d0-102">MSSQLSERVER_905</span></span>
    
## <a name="details"></a><span data-ttu-id="074d0-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="074d0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="074d0-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="074d0-104">Product Name</span></span>|<span data-ttu-id="074d0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="074d0-105">SQL Server</span></span>|  
|<span data-ttu-id="074d0-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="074d0-106">Event ID</span></span>|<span data-ttu-id="074d0-107">905</span><span class="sxs-lookup"><span data-stu-id="074d0-107">905</span></span>|  
|<span data-ttu-id="074d0-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="074d0-108">Event Source</span></span>|<span data-ttu-id="074d0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="074d0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="074d0-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="074d0-110">Component</span></span>|<span data-ttu-id="074d0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="074d0-111">SQLEngine</span></span>|  
|<span data-ttu-id="074d0-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="074d0-112">Symbolic Name</span></span>|<span data-ttu-id="074d0-113">DBSTARTUP_EE_PARTITIONING</span><span class="sxs-lookup"><span data-stu-id="074d0-113">DBSTARTUP_EE_PARTITIONING</span></span>|  
|<span data-ttu-id="074d0-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="074d0-114">Message Text</span></span>|<span data-ttu-id="074d0-115">파티션 함수 '%.\*ls'이(가) 포함되어 있기 때문에 이 SQL Server Edition에서는 데이터베이스 '%.\*ls'을(를) 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-115">Database '%.\*ls' cannot be started in this edition of SQL Server because it contains a partition function '%.\*ls'.</span></span> <span data-ttu-id="074d0-116">SQL Server Enterprise Edition에서만 분할을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-116">Only Enterprise edition of SQL Server supports partitioning.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="074d0-117">설명</span><span class="sxs-lookup"><span data-stu-id="074d0-117">Explanation</span></span>  
 <span data-ttu-id="074d0-118">데이터베이스에는 하나 이상의 분할된 테이블 또는 인덱스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-118">The database contains one or more partitioned tables or indexes.</span></span> <span data-ttu-id="074d0-119">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Edition에서는 분할을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-119">This edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot use partitioning.</span></span> <span data-ttu-id="074d0-120">따라서 데이터베이스를 올바로 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-120">Therefore, the database cannot be started correctly.</span></span> <span data-ttu-id="074d0-121">분할된 테이블 및 인덱스는 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-121">Partitioned tables and indexes are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="074d0-122">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="074d0-122">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="074d0-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="074d0-123">User Action</span></span>  
 <span data-ttu-id="074d0-124">sp_detach_db 저장 프로시저를 사용하여 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-124">Detach the database by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="074d0-125">필요한 경우 파일을 이동한 다음 CREATE DATABASE와 함께 FOR ATTACH 또는 FOR ATTACH_REBUILD_LOG 옵션을 사용하여 지원되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전의 인스턴스에 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-125">Move the files if it is needed, and then attach the database to an instance of a supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition by using the CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="074d0-126">모든 테이블에서 분할을 사용할 수 없게 설정하고 파티션 함수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-126">Disable partitioning on all tables and remove the partitioning functions.</span></span> <span data-ttu-id="074d0-127">데이터베이스를 다시 분리한 다음 현재 서버에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="074d0-127">Detach the database again, and reattach the database to the current server.</span></span>  
  
  
