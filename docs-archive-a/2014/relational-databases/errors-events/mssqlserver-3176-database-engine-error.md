---
title: MSSQLSERVER_3176 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e1a836995fe8738bb5c2ff0cb4de10d84d1f29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651017"
---
# <a name="mssqlserver_3176"></a><span data-ttu-id="79387-102">MSSQLSERVER_3176</span><span class="sxs-lookup"><span data-stu-id="79387-102">MSSQLSERVER_3176</span></span>
    
## <a name="details"></a><span data-ttu-id="79387-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="79387-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79387-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="79387-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="79387-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="79387-105">Event ID</span></span>|<span data-ttu-id="79387-106">3176</span><span class="sxs-lookup"><span data-stu-id="79387-106">3176</span></span>|  
|<span data-ttu-id="79387-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="79387-107">Event Source</span></span>|<span data-ttu-id="79387-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="79387-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="79387-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="79387-109">Component</span></span>|<span data-ttu-id="79387-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="79387-110">SQLEngine</span></span>|  
|<span data-ttu-id="79387-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="79387-111">Symbolic Name</span></span>|<span data-ttu-id="79387-112">LDDB_FILE_CLAIM</span><span class="sxs-lookup"><span data-stu-id="79387-112">LDDB_FILE_CLAIM</span></span>|  
|<span data-ttu-id="79387-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="79387-113">Message Text</span></span>|<span data-ttu-id="79387-114">'%ls'(%d) 및 '%ls'(%d)에서 파일 '%ls'을(를) 요구했습니다.</span><span class="sxs-lookup"><span data-stu-id="79387-114">File '%ls' is claimed by '%ls'(%d) and '%ls'(%d).</span></span> <span data-ttu-id="79387-115">WITH MOVE 절을 사용하여 하나 이상의 파일 위치를 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79387-115">The WITH MOVE clause can be used to relocate one or more files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="79387-116">설명</span><span class="sxs-lookup"><span data-stu-id="79387-116">Explanation</span></span>  
 <span data-ttu-id="79387-117">파일을 두 가지 이상의 용도로 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="79387-117">Attempting to use a file for more than one purpose.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="79387-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="79387-118">Possible Causes</span></span>  
 <span data-ttu-id="79387-119">다른 데이터베이스에서 이미 파일 이름을 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79387-119">Another database is already using the file name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79387-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="79387-120">User Action</span></span>  
 <span data-ttu-id="79387-121">데이터베이스 파일을 다른 위치로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="79387-121">Restore the database files to a different location.</span></span> <span data-ttu-id="79387-122">RESTORE 문에서 WITH MOVE 절을 사용하여 각 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="79387-122">In a RESTORE statement, use a WITH MOVE clause to move each file.</span></span> <span data-ttu-id="79387-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **데이터베이스 복원 옵션** 대화 상자의 **데이터베이스 파일을 다음으로 복원** 표에서 파일 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="79387-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], change the file locations in the **Restore the database files as** grid of the **Restore Database Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79387-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79387-124">See Also</span></span>  
 <span data-ttu-id="79387-125">[데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79387-125">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="79387-126">[SQL Server&#41;&#40;새 위치로 파일을 복원 합니다.](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="79387-126">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="79387-127">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="79387-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
