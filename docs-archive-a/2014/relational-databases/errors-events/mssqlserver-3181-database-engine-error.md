---
title: MSSQLSERVER_3181 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f18509d9a18ba8be1f4e40c93bff5abfcae3d69c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651016"
---
# <a name="mssqlserver_3181"></a><span data-ttu-id="707bb-102">MSSQLSERVER_3181</span><span class="sxs-lookup"><span data-stu-id="707bb-102">MSSQLSERVER_3181</span></span>
    
## <a name="details"></a><span data-ttu-id="707bb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="707bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="707bb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="707bb-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="707bb-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="707bb-105">Event ID</span></span>|<span data-ttu-id="707bb-106">3181</span><span class="sxs-lookup"><span data-stu-id="707bb-106">3181</span></span>|  
|<span data-ttu-id="707bb-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="707bb-107">Event Source</span></span>|<span data-ttu-id="707bb-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="707bb-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="707bb-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="707bb-109">Component</span></span>|<span data-ttu-id="707bb-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="707bb-110">SQLEngine</span></span>|  
|<span data-ttu-id="707bb-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="707bb-111">Symbolic Name</span></span>|<span data-ttu-id="707bb-112">LDDB_STORAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="707bb-112">LDDB_STORAGE_VERIFY</span></span>|  
|<span data-ttu-id="707bb-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="707bb-113">Message Text</span></span>|<span data-ttu-id="707bb-114">이 백업을 복원하려고 하면 스토리지 공간 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="707bb-114">Attempting to restore this backup may encounter storage space problems.</span></span> <span data-ttu-id="707bb-115">이어서 나타나는 메시지에서 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="707bb-115">Subsequent messages will provide details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="707bb-116">설명</span><span class="sxs-lookup"><span data-stu-id="707bb-116">Explanation</span></span>  
 <span data-ttu-id="707bb-117">RESTORE VERIFYONLY 문은 데이터베이스가 복원될 디스크의 사용 가능한 스토리지 공간을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="707bb-117">The RESTORE VERIFYONLY statement checks the available storage space on the disk to which the database is to be restored.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="707bb-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="707bb-118">Possible Causes</span></span>  
 <span data-ttu-id="707bb-119">사용 가능한 디스크 공간이 확인하려는 백업을 복원하기에 부족할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="707bb-119">The available disk space may be insufficient to restore the backup being verified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="707bb-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="707bb-120">User Action</span></span>  
 <span data-ttu-id="707bb-121">충분한 디스크 공간이 있는 위치로 백업을 복원하거나 디스크에 더 많은 공간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="707bb-121">Restore the backup to a location with sufficient disk space, or provide more space on the disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707bb-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="707bb-122">See Also</span></span>  
 <span data-ttu-id="707bb-123">[데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="707bb-123">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="707bb-124">[SQL Server&#41;&#40;새 위치로 파일을 복원 합니다.](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="707bb-124">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="707bb-125">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="707bb-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="707bb-126">RESTORE VERIFYONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="707bb-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
