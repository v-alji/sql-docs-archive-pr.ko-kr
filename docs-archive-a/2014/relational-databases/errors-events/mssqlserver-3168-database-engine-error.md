---
title: MSSQLSERVER_3168 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 764f456653365c085e9f756a749910bbd03b4259
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651020"
---
# <a name="mssqlserver_3168"></a><span data-ttu-id="371c2-102">MSSQLSERVER_3168</span><span class="sxs-lookup"><span data-stu-id="371c2-102">MSSQLSERVER_3168</span></span>
    
## <a name="details"></a><span data-ttu-id="371c2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="371c2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="371c2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="371c2-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="371c2-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="371c2-105">Event ID</span></span>|<span data-ttu-id="371c2-106">3168</span><span class="sxs-lookup"><span data-stu-id="371c2-106">3168</span></span>|  
|<span data-ttu-id="371c2-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="371c2-107">Event Source</span></span>|<span data-ttu-id="371c2-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="371c2-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="371c2-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="371c2-109">Component</span></span>|<span data-ttu-id="371c2-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="371c2-110">SQLEngine</span></span>|  
|<span data-ttu-id="371c2-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="371c2-111">Symbolic Name</span></span>|<span data-ttu-id="371c2-112">LDDB_SYSTEMWRONGVER</span><span class="sxs-lookup"><span data-stu-id="371c2-112">LDDB_SYSTEMWRONGVER</span></span>|  
|<span data-ttu-id="371c2-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="371c2-113">Message Text</span></span>|<span data-ttu-id="371c2-114">디바이스 %ls에 있는 시스템 데이터베이스의 백업은 이 서버(%ls)와 다른 버전의 서버(%ls)에서 생성되었으므로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-114">The backup of the system database on the device %ls cannot be restored because it was created by a different version of the server (%ls) than this server (%ls).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="371c2-115">설명</span><span class="sxs-lookup"><span data-stu-id="371c2-115">Explanation</span></span>  
 <span data-ttu-id="371c2-116">백업을 원래 수행한 빌드가 아닌 다른 서버 빌드에서는 시스템 데이터베이스(**master**, **model** 또는 **msdb**)의 백업을 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-116">You cannot restore a backup of a system database (**master**, **model**, or **msdb**) on a server build that differs from the build on which the backup was originally performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="371c2-117">서비스 팩 또는 핫픽스 빌드를 설치하면 서버 빌드 번호가 변경되며 서버 빌드는 항상 증분식입니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-117">Installing a service pack or a hotfix build changes the server build number, and server builds are always incremental.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="371c2-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="371c2-118">Possible Causes</span></span>  
 <span data-ttu-id="371c2-119">시스템 데이터베이스에 대한 데이터베이스 스키마가 서버 빌드 간에 변경되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-119">The database schema for system databases may be changed across server builds.</span></span> <span data-ttu-id="371c2-120">스키마 변경으로 인해 불일치 문제가 발생하지 않도록 RESTORE 문은 백업 파일의 서버 빌드 번호를 백업을 복원하려는 서버의 빌드 번호와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-120">To make sure that a schema change does not cause inconsistencies, the RESTORE statement compares the server build number on the backup file to the build number of the server on which you are trying to restore the backup.</span></span> <span data-ttu-id="371c2-121">그 결과 빌드가 다르면 해당 문에서 3168 오류 메시지를 표시하고 복원 작업이 비정상적으로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-121">If the builds are different, the statement issues the 3168 error message, and the restore operation terminates abnormally.</span></span>  
  
 <span data-ttu-id="371c2-122">이 문제가 발생할 수 있는 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-122">Some scenarios in which this problem may occur include the following:</span></span>  
  
-   <span data-ttu-id="371c2-123">사용자가 서버 B에서 수행한 백업에서 서버 A의 시스템 데이터베이스를 복원하려고 합니다. 서버 A와 서버 B는 서로 다른 서버 빌드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-123">A user tries to restore a system database on Server A from a backup taken on Server B. Servers A and B are on different server builds.</span></span> <span data-ttu-id="371c2-124">예를 들어 서버 A는 원래 릴리스 버전 빌드에 있고 서버 B는 SP1(서비스 팩 1) 빌드에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-124">For example, Server A might be on the original release version build and Server B might be on a service pack 1 (SP1) build.</span></span>  
  
-   <span data-ttu-id="371c2-125">사용자가 동일한 서버에서 수행한 백업에서 시스템 데이터베이스를 복원하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-125">A user tries to restore a system database from a backup taken on the same server.</span></span> <span data-ttu-id="371c2-126">그러나 백업을 수행할 당시에는 서버가 다른 빌드를 실행하고 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-126">However, the server was running a different build when the backup occurred.</span></span> <span data-ttu-id="371c2-127">즉, 백업을 수행한 이후에 서버가 업그레이드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-127">That is, the server was upgraded since the backup was performed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="371c2-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="371c2-128">User Action</span></span>  
 <span data-ttu-id="371c2-129">이 시나리오에는 복원 프로세스가 마지막 수단으로 이미 시도되었습니다.</span><span class="sxs-lookup"><span data-stu-id="371c2-129">The restore process in this situation is fairly involved, and used only as a last resort.</span></span> <span data-ttu-id="371c2-130">자세한 내용은 "[You cannot restore system database backups to a different build of SQL Server](https://support.microsoft.com/kb/264474)(시스템 데이터베이스 백업을 SQL Server의 다른 빌드로 복원할 수 없습니다.)"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="371c2-130">For more information, see"[You cannot restore system database backups to a different build of SQL Server](https://support.microsoft.com/kb/264474)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="371c2-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="371c2-131">See Also</span></span>  
 [<span data-ttu-id="371c2-132">시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="371c2-132">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
  
