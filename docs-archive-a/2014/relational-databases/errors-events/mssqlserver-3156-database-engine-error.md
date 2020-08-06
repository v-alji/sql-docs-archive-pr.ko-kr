---
title: MSSQLSERVER_3156 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 25b5a037012a6d6b47b91e763a49cfb67b89f43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651021"
---
# <a name="mssqlserver_3156"></a><span data-ttu-id="1460c-102">MSSQLSERVER_3156</span><span class="sxs-lookup"><span data-stu-id="1460c-102">MSSQLSERVER_3156</span></span>
    
## <a name="details"></a><span data-ttu-id="1460c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1460c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1460c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1460c-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1460c-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1460c-105">Event ID</span></span>|<span data-ttu-id="1460c-106">3156</span><span class="sxs-lookup"><span data-stu-id="1460c-106">3156</span></span>|  
|<span data-ttu-id="1460c-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1460c-107">Event Source</span></span>|<span data-ttu-id="1460c-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1460c-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1460c-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1460c-109">Component</span></span>|<span data-ttu-id="1460c-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1460c-110">SQLEngine</span></span>|  
|<span data-ttu-id="1460c-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1460c-111">Symbolic Name</span></span>|<span data-ttu-id="1460c-112">LDDB_CANT_WRITE</span><span class="sxs-lookup"><span data-stu-id="1460c-112">LDDB_CANT_WRITE</span></span>|  
|<span data-ttu-id="1460c-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1460c-113">Message Text</span></span>|<span data-ttu-id="1460c-114">파일 '%ls'을(를) '%ls'(으)로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-114">File '%ls' cannot be restored to '%ls'.</span></span> <span data-ttu-id="1460c-115">WITH MOVE를 사용하여 올바른 파일 위치를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1460c-115">Use WITH MOVE to identify a valid location for the file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1460c-116">설명</span><span class="sxs-lookup"><span data-stu-id="1460c-116">Explanation</span></span>  
 <span data-ttu-id="1460c-117">이 일반적인 메시지는 지정된 위치와 관련된 문제로 인해 복원할 수 없는 논리적 또는 물리적 파일 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-117">This general message identifies the logical or physical file names of files that could not be restored because of a problem with the specified location.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="1460c-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="1460c-118">Possible Causes</span></span>  
 <span data-ttu-id="1460c-119">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-119">The possible causes include the following:</span></span>  
  
-   <span data-ttu-id="1460c-120">지정된 Windows 디렉터리에 대한 액세스 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-120">You might need access to the specified Windows directory.</span></span>  
  
-   <span data-ttu-id="1460c-121">경로를 잘못 입력했거나 존재하지 않는 경로를 지정했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-121">You might have mistyped the path or specified a path that does not exist.</span></span>  
  
-   <span data-ttu-id="1460c-122">해당 파일 이름이 덮어쓸 수 없는 파일에 사용되고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-122">The file name might be being used by a file that cannot be overwritten.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1460c-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1460c-123">User Action</span></span>  
 <span data-ttu-id="1460c-124">자세한 내용은 오류 로그에서 다른 메시지를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1460c-124">Look at the error logs for other messages that provide more details.</span></span>  
  
 <span data-ttu-id="1460c-125">액세스 권한을 부여하거나 RESTORE 문에 WITH MOVE 옵션을 사용하는 방법으로 파일의 위치를 다시 지정하여 지정된 위치와 관련된 문제를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1460c-125">Correct the problem with the specified location, for example, by granting access, or use the WITH MOVE option in your RESTORE statement to relocate the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1460c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1460c-126">See Also</span></span>  
 <span data-ttu-id="1460c-127">[데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1460c-127">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="1460c-128">[SQL Server&#41;&#40;새 위치로 파일을 복원 합니다.](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1460c-128">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="1460c-129">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1460c-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
