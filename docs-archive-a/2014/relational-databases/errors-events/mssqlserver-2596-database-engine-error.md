---
title: MSSQLSERVER_2596 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27b2ceed40274df4ba57c4d61a83fbc60b6a7f80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651040"
---
# <a name="mssqlserver_2596"></a><span data-ttu-id="753e8-102">MSSQLSERVER_2596</span><span class="sxs-lookup"><span data-stu-id="753e8-102">MSSQLSERVER_2596</span></span>
    
## <a name="details"></a><span data-ttu-id="753e8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="753e8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="753e8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="753e8-104">Product Name</span></span>|<span data-ttu-id="753e8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="753e8-105">SQL Server</span></span>|  
|<span data-ttu-id="753e8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="753e8-106">Event ID</span></span>|<span data-ttu-id="753e8-107">2596</span><span class="sxs-lookup"><span data-stu-id="753e8-107">2596</span></span>|  
|<span data-ttu-id="753e8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="753e8-108">Event Source</span></span>|<span data-ttu-id="753e8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="753e8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="753e8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="753e8-110">Component</span></span>|<span data-ttu-id="753e8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="753e8-111">SQLEngine</span></span>|  
|<span data-ttu-id="753e8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="753e8-112">Symbolic Name</span></span>|<span data-ttu-id="753e8-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span><span class="sxs-lookup"><span data-stu-id="753e8-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span></span>|  
|<span data-ttu-id="753e8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="753e8-114">Message Text</span></span>|<span data-ttu-id="753e8-115">복구 문이 처리되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="753e8-115">The repair statement was not processed.</span></span> <span data-ttu-id="753e8-116">데이터베이스는 읽기 전용 모드일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="753e8-116">The database cannot be in read-only mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="753e8-117">설명</span><span class="sxs-lookup"><span data-stu-id="753e8-117">Explanation</span></span>  
 <span data-ttu-id="753e8-118">이 메시지는 데이터베이스가 읽기 전용 모드임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="753e8-118">This message indicates that the database is in read-only mode.</span></span> <span data-ttu-id="753e8-119">데이터베이스가 읽기 전용 모드인 경우 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="753e8-119">Repairs are not possible when a database is in read-only mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="753e8-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="753e8-120">User Action</span></span>  
 <span data-ttu-id="753e8-121">ALTER DATABASE를 사용하여 데이터베이스를 읽기/쓰기 권한으로 설정한 다음 DBCC 명령을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="753e8-121">Set the database to read-write by using ALTER DATABASE, and then re-run the DBCC command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753e8-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="753e8-122">See Also</span></span>  
 [<span data-ttu-id="753e8-123">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="753e8-123">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
