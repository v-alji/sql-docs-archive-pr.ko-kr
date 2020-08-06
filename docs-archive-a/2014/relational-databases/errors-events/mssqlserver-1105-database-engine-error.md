---
title: MSSQLSERVER_1105 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dea326fab7edd6a5c155c8f0182bffc044505eb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646538"
---
# <a name="mssqlserver_1105"></a><span data-ttu-id="3f491-102">MSSQLSERVER_1105</span><span class="sxs-lookup"><span data-stu-id="3f491-102">MSSQLSERVER_1105</span></span>
    
## <a name="details"></a><span data-ttu-id="3f491-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3f491-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f491-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3f491-104">Product Name</span></span>|<span data-ttu-id="3f491-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3f491-105">SQL Server</span></span>|  
|<span data-ttu-id="3f491-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3f491-106">Event ID</span></span>|<span data-ttu-id="3f491-107">1105</span><span class="sxs-lookup"><span data-stu-id="3f491-107">1105</span></span>|  
|<span data-ttu-id="3f491-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3f491-108">Event Source</span></span>|<span data-ttu-id="3f491-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3f491-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3f491-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3f491-110">Component</span></span>|<span data-ttu-id="3f491-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3f491-111">SQLEngine</span></span>|  
|<span data-ttu-id="3f491-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3f491-112">Symbolic Name</span></span>|<span data-ttu-id="3f491-113">NO_MORE_SPACE_IN_FG</span><span class="sxs-lookup"><span data-stu-id="3f491-113">NO_MORE_SPACE_IN_FG</span></span>|  
|<span data-ttu-id="3f491-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3f491-114">Message Text</span></span>|<span data-ttu-id="3f491-115">'%.\*ls' 파일 그룹이 꽉 찼으므로 데이터베이스 '%.\*ls'의 개체 %.\*ls'%.\*ls에 공간을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-115">Could not allocate space for object '%.\*ls'%.\*ls in database '%.\*ls' because the '%.\*ls' filegroup is full.</span></span> <span data-ttu-id="3f491-116">필요 없는 파일을 삭제하거나, 파일 그룹의 개체를 삭제하거나, 파일 그룹에 파일을 추가하거나, 파일 그룹의 기존 파일에 대해 자동 증가를 설정하여 디스크 공간을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="3f491-116">Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f491-117">설명</span><span class="sxs-lookup"><span data-stu-id="3f491-117">Explanation</span></span>  
 <span data-ttu-id="3f491-118">파일 그룹에 사용 가능한 디스크 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-118">No disk space is available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f491-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3f491-119">User Action</span></span>  
 <span data-ttu-id="3f491-120">다음 동작으로 파일 그룹에 사용 가능한 공간을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-120">The following actions may make space available in the filegroup:</span></span>  
  
-   <span data-ttu-id="3f491-121">자동 증가를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-121">Turn on autogrow.</span></span>  
  
-   <span data-ttu-id="3f491-122">파일에 파일 추가</span><span class="sxs-lookup"><span data-stu-id="3f491-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="3f491-123">더 이상 필요하지 않은 인덱스나 테이블을 삭제하여 디스크 공간을 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-123">Free disk space by dropping index or tables that are no longer needed.</span></span>  
  
-   <span data-ttu-id="3f491-124">자세한 내용은 SQL Server 온라인 도움말의 "데이터 디스크 공간 부족 문제 해결"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f491-124">For more information, see "Troubleshooting Insufficient Data Disk Space" in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f491-125">인덱스가 여러 파일에 있을 때, 파일 중 하나가 가득 차면 `ALTER INDEX REORGANIZE`가 1105 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-125">When an index is located on several files, `ALTER INDEX REORGANIZE` can return error 1105 when one of the files is full.</span></span> <span data-ttu-id="3f491-126">프로세스에서 가득 찬 파일로 행을 이동하려 하면 재구성 프로세스는 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-126">The reorganization process is blocked when the process tries to move rows to the full file.</span></span> <span data-ttu-id="3f491-127">이 제한을 해결하려면 `ALTER INDEX REBUILD` 대신 `ALTER INDEX REORGANIZE`를 수행하거나 가득 찬 파일의 파일 증가 제한을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="3f491-127">To work around this limitation perform an `ALTER INDEX REBUILD` instead of `ALTER INDEX REORGANIZE` or increase the file growth limit of any files that are full.</span></span>  
  
  
