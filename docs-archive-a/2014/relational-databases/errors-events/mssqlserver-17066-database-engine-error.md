---
title: MSSQLSERVER_17066 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c2bc421fb969e4f24e49871ff97047be9040ae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653938"
---
# <a name="mssqlserver_17066"></a><span data-ttu-id="cc63c-102">MSSQLSERVER_17066</span><span class="sxs-lookup"><span data-stu-id="cc63c-102">MSSQLSERVER_17066</span></span>
    
## <a name="details"></a><span data-ttu-id="cc63c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="cc63c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc63c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="cc63c-104">Product Name</span></span>|<span data-ttu-id="cc63c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cc63c-105">SQL Server</span></span>|  
|<span data-ttu-id="cc63c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="cc63c-106">Event ID</span></span>|<span data-ttu-id="cc63c-107">17066</span><span class="sxs-lookup"><span data-stu-id="cc63c-107">17066</span></span>|  
|<span data-ttu-id="cc63c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="cc63c-108">Event Source</span></span>|<span data-ttu-id="cc63c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cc63c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cc63c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cc63c-110">Component</span></span>|<span data-ttu-id="cc63c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cc63c-111">SQLEngine</span></span>|  
|<span data-ttu-id="cc63c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="cc63c-112">Symbolic Name</span></span>|<span data-ttu-id="cc63c-113">SQLASSERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="cc63c-113">SQLASSERT_ONLY</span></span>|  
|<span data-ttu-id="cc63c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="cc63c-114">Message Text</span></span>|<span data-ttu-id="cc63c-115">SQL Server 어설션: 파일: \<%s>, 줄=%d 어설션 오류 = '%s'.</span><span class="sxs-lookup"><span data-stu-id="cc63c-115">SQL Server Assertion: File: \<%s>, line=%d Failed Assertion = '%s'.</span></span> <span data-ttu-id="cc63c-116">이 오류는 타이밍과 관련된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-116">This error may be timing-related.</span></span> <span data-ttu-id="cc63c-117">문을 다시 실행한 후에도 이 오류가 지속되면 DBCC CHECKDB를 사용하여 데이터베이스의 구조적 무결성을 확인하거나 서버를 다시 시작하여 메모리 내부 데이터 구조가 손상되지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc63c-117">If the error persists after rerunning the statement, use DBCC CHECKDB to check the database for structural integrity, or restart the server to ensure in-memory data structures are not corrupted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc63c-118">설명</span><span class="sxs-lookup"><span data-stu-id="cc63c-118">Explanation</span></span>  
 <span data-ttu-id="cc63c-119">이 오류는 일시적인 타이밍 관련 오류나 메모리 내부에 있거나 디스크에 있는 데이터의 손상으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-119">This error can be caused by transient, timing-related errors, or by in-memory or on-disk data corruption.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc63c-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="cc63c-120">User Action</span></span>  
 <span data-ttu-id="cc63c-121">예외를 발생시킨 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-121">Rerun the statement that caused the exception to fire.</span></span> <span data-ttu-id="cc63c-122">타이밍 관련 이벤트로 인해 발생한 오류는 되풀이되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-122">If the error was caused by a timing-related event, the error may not recur.</span></span> <span data-ttu-id="cc63c-123">문제가 지속되면 DBCC CHECKDB를 실행하여 디스크가 손상되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-123">If the problem persists, run DBCC CHECKDB to  check for on-disk corruption.</span></span> <span data-ttu-id="cc63c-124">메모리 내부 데이터 구조가 손상되지 않았는지 확인하려면 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cc63c-124">Restart the server to ensure that the in-memory data structures are not corrupted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc63c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc63c-125">See Also</span></span>  
 [<span data-ttu-id="cc63c-126">DBCC CHECKDB&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc63c-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
