---
title: MSSQLSERVER_9002 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40fe70db8849d09f9296a06cbeed65a9c71e5a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652846"
---
# <a name="mssqlserver_9002"></a><span data-ttu-id="5013f-102">MSSQLSERVER_9002</span><span class="sxs-lookup"><span data-stu-id="5013f-102">MSSQLSERVER_9002</span></span>
    
## <a name="details"></a><span data-ttu-id="5013f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5013f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5013f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5013f-104">Product Name</span></span>|<span data-ttu-id="5013f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5013f-105">SQL Server</span></span>|  
|<span data-ttu-id="5013f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5013f-106">Event ID</span></span>|<span data-ttu-id="5013f-107">9002</span><span class="sxs-lookup"><span data-stu-id="5013f-107">9002</span></span>|  
|<span data-ttu-id="5013f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5013f-108">Event Source</span></span>|<span data-ttu-id="5013f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5013f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5013f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5013f-110">Component</span></span>|<span data-ttu-id="5013f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5013f-111">SQLEngine</span></span>|  
|<span data-ttu-id="5013f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5013f-112">Symbolic Name</span></span>|<span data-ttu-id="5013f-113">LOG_IS_FULL</span><span class="sxs-lookup"><span data-stu-id="5013f-113">LOG_IS_FULL</span></span>|  
|<span data-ttu-id="5013f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5013f-114">Message Text</span></span>|<span data-ttu-id="5013f-115">데이터베이스 '%.\*ls'의 트랜잭션 로그가 꽉 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="5013f-115">The transaction log for database '%.\*ls' is full.</span></span> <span data-ttu-id="5013f-116">로그의 공간을 다시 사용할 수 없는 이유를 확인하려면 sys.databases의 log_reuse_wait_desc 열을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5013f-116">To find out why space in the log cannot be reused, see the log_reuse_wait_desc column in sys.databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5013f-117">설명</span><span class="sxs-lookup"><span data-stu-id="5013f-117">Explanation</span></span>  
 <span data-ttu-id="5013f-118">데이터베이스 로그에 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="5013f-118">The database log is out of space.</span></span> <span data-ttu-id="5013f-119">**sys.databases**의 **log_reuse_wait_desc** 열을 확인하여 로그의 공간을 다시 사용할 수 없는 이유를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5013f-119">The **log_reuse_wait_desc** column in **sys.databases** describes why space in the log cannot be reused.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5013f-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5013f-120">User Action</span></span>  
 <span data-ttu-id="5013f-121">**sys.databases**를 사용하여 로그가 꽉 찬 이유를 확인하고 문제를 해결하세요.</span><span class="sxs-lookup"><span data-stu-id="5013f-121">Use **sys.databases** to determine why the log is full and then correct the condition.</span></span> <span data-ttu-id="5013f-122">자세한 내용은 SQL Server 온라인 설명서의 "꽉 찬 트랜잭션 로그 문제 해결(오류 9002)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5013f-122">For more information, see "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5013f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5013f-123">See Also</span></span>  
 <span data-ttu-id="5013f-124">[꽉 찬 트랜잭션 로그 문제 해결&#40;SQL Server 오류 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span><span class="sxs-lookup"><span data-stu-id="5013f-124">[Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span></span>  
 [<span data-ttu-id="5013f-125">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5013f-125">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
