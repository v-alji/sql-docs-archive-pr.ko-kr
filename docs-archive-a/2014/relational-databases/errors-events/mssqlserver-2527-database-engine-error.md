---
title: MSSQLSERVER_2527 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900707634a016ecfd29f9f676e68b4d2f557ccea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649082"
---
# <a name="mssqlserver_2527"></a><span data-ttu-id="57e5a-102">MSSQLSERVER_2527</span><span class="sxs-lookup"><span data-stu-id="57e5a-102">MSSQLSERVER_2527</span></span>
    
## <a name="details"></a><span data-ttu-id="57e5a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="57e5a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57e5a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="57e5a-104">Product Name</span></span>|<span data-ttu-id="57e5a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="57e5a-105">SQL Server</span></span>|  
|<span data-ttu-id="57e5a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="57e5a-106">Event ID</span></span>|<span data-ttu-id="57e5a-107">2527</span><span class="sxs-lookup"><span data-stu-id="57e5a-107">2527</span></span>|  
|<span data-ttu-id="57e5a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="57e5a-108">Event Source</span></span>|<span data-ttu-id="57e5a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="57e5a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="57e5a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="57e5a-110">Component</span></span>|<span data-ttu-id="57e5a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="57e5a-111">SQLEngine</span></span>|  
|<span data-ttu-id="57e5a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="57e5a-112">Symbolic Name</span></span>|<span data-ttu-id="57e5a-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="57e5a-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span></span>|  
|<span data-ttu-id="57e5a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="57e5a-114">Message Text</span></span>|<span data-ttu-id="57e5a-115">파일 그룹 F_NAME이(가) 오프라인 상태이므로 테이블 O_NAME의 인덱스 I_NAME을(를) 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57e5a-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is offline.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="57e5a-116">설명</span><span class="sxs-lookup"><span data-stu-id="57e5a-116">Explanation</span></span>  
 <span data-ttu-id="57e5a-117">이 정보 메시지는 인덱스에 대한 데이터를 저장하는 파일 그룹 중 하나가 오프라인 상태이므로 인덱스를 검사할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57e5a-117">This informational message indicates that the index cannot be checked because one of the filegroups that stores data for the index is offline.</span></span> <span data-ttu-id="57e5a-118">파일 그룹의 파일 상태에 따라 전체 파일 그룹의 사용 가능 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="57e5a-118">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="57e5a-119">파일 그룹을 사용하려면 파일 그룹 내의 모든 파일이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57e5a-119">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="57e5a-120">다른 문제가 없으면 같은 개체에 대한 다른 인덱스를 모두 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="57e5a-120">If there are no other problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57e5a-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="57e5a-121">User Action</span></span>  
 <span data-ttu-id="57e5a-122">지정된 파일 그룹의 파일 상태를 보려면 **sys.database_files** 또는 **sys.master_files** 카탈로그 뷰 중 하나를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="57e5a-122">To view the state of the files for the specified filegroup, query either the **sys.database_files** or **sys.master_files** catalog view.</span></span>  
  
 <span data-ttu-id="57e5a-123">백업에서 오프라인 파일을 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="57e5a-123">Restore the offline file from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e5a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57e5a-124">See Also</span></span>  
 <span data-ttu-id="57e5a-125">[sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57e5a-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="57e5a-126">[master_files &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57e5a-126">[sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span></span>  
 [<span data-ttu-id="57e5a-127">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57e5a-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
