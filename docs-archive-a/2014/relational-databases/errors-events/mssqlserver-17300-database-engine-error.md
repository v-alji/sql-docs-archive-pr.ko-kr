---
title: MSSQLSERVER_17300 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f77e39c71901166085d011d6d00f9a4a379bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729544"
---
# <a name="mssqlserver_17300"></a><span data-ttu-id="9b0bb-102">MSSQLSERVER_17300</span><span class="sxs-lookup"><span data-stu-id="9b0bb-102">MSSQLSERVER_17300</span></span>
    
## <a name="details"></a><span data-ttu-id="9b0bb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9b0bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b0bb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9b0bb-104">Product Name</span></span>|<span data-ttu-id="9b0bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b0bb-105">SQL Server</span></span>|  
|<span data-ttu-id="9b0bb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9b0bb-106">Event ID</span></span>|<span data-ttu-id="9b0bb-107">17300</span><span class="sxs-lookup"><span data-stu-id="9b0bb-107">17300</span></span>|  
|<span data-ttu-id="9b0bb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9b0bb-108">Event Source</span></span>|<span data-ttu-id="9b0bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9b0bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9b0bb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9b0bb-110">Component</span></span>|<span data-ttu-id="9b0bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9b0bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="9b0bb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9b0bb-112">Symbolic Name</span></span>|<span data-ttu-id="9b0bb-113">PROC_OUT_OF_SYSTASK_SESSIONS</span><span class="sxs-lookup"><span data-stu-id="9b0bb-113">PROC_OUT_OF_SYSTASK_SESSIONS</span></span>|  
|<span data-ttu-id="9b0bb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9b0bb-114">Message Text</span></span>|<span data-ttu-id="9b0bb-115">SQL Server에서 메모리가 부족하거나 구성된 세션의 수가 서버에서 허용되는 최대 수를 초과하므로 새 시스템 태스크를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-115">SQL Server was unable to run a new system task, either because there is insufficient memory or the number of configured sessions exceeds the maximum allowed in the server.</span></span> <span data-ttu-id="9b0bb-116">서버에 적당한 메모리가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-116">Verify that the server has adequate memory.</span></span> <span data-ttu-id="9b0bb-117">허용되는 최대 세션 수를 확인하려면 'user connections' 옵션과 함께 sp_configure를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-117">Use sp_configure with option 'user connections' to check the maximum number of user connections allowed.</span></span> <span data-ttu-id="9b0bb-118">사용자 프로세스를 비롯하여 현재 세션 수를 확인하려면 sys.dm_exec_sessions를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-118">Use sys.dm_exec_sessions to check the current number of sessions, including user processes.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9b0bb-119">설명</span><span class="sxs-lookup"><span data-stu-id="9b0bb-119">Explanation</span></span>  
 <span data-ttu-id="9b0bb-120">메모리가 부족하거나 서버에 구성된 세션 수가 초과되어 새 시스템 태스크를 실행하려는 시도가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-120">An attempt to run a new system task failed because of insufficient memory or because the number of configured sessions in the server was exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9b0bb-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9b0bb-121">User Action</span></span>  
 <span data-ttu-id="9b0bb-122">서버에 충분한 메모리가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-122">Verify that the server has enough memory.</span></span> <span data-ttu-id="9b0bb-123">sys.dm_exec_sessions를 사용하여 현재 시스템 태스크 수를 확인하고 sp_configure를 사용하여 구성된 최대 사용자 연결 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-123">Verify the current number of system tasks by using sys.dm_exec_sessions, and verify the configured value of maximum user connections by using sp_configure.</span></span>  
  
 <span data-ttu-id="9b0bb-124">다음 태스크를 적절하게 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="9b0bb-125">서버에 메모리를 더 많이 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-125">Add more memory to the server.</span></span>  
  
-   <span data-ttu-id="9b0bb-126">하나 이상의 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-126">Terminate one or more sessions.</span></span>  
  
-   <span data-ttu-id="9b0bb-127">서버에 허용되는 최대 사용자 연결 수를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="9b0bb-127">Increase the maximum number of user connections allowed on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0bb-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b0bb-128">See Also</span></span>  
 <span data-ttu-id="9b0bb-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9b0bb-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="9b0bb-130">[서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b0bb-130">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="9b0bb-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9b0bb-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span></span>  
 <span data-ttu-id="9b0bb-132">[User connections 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="9b0bb-132">[Configure the user connections Server Configuration Option](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="9b0bb-133">KILL&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9b0bb-133">KILL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
