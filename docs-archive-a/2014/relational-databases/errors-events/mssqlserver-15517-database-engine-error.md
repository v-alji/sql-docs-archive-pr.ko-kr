---
title: MSSQLSERVER_15517 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653943"
---
# <a name="mssqlserver_15517"></a><span data-ttu-id="68025-102">MSSQLSERVER_15517</span><span class="sxs-lookup"><span data-stu-id="68025-102">MSSQLSERVER_15517</span></span>
    
## <a name="details"></a><span data-ttu-id="68025-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="68025-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68025-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="68025-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="68025-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="68025-105">Event ID</span></span>|<span data-ttu-id="68025-106">15517</span><span class="sxs-lookup"><span data-stu-id="68025-106">15517</span></span>|  
|<span data-ttu-id="68025-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="68025-107">Event Source</span></span>|<span data-ttu-id="68025-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="68025-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="68025-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="68025-109">Component</span></span>|<span data-ttu-id="68025-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="68025-110">SQLEngine</span></span>|  
|<span data-ttu-id="68025-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="68025-111">Symbolic Name</span></span>|<span data-ttu-id="68025-112">SEC_CANNOTEXECUTEASUSER</span><span class="sxs-lookup"><span data-stu-id="68025-112">SEC_CANNOTEXECUTEASUSER</span></span>|  
|<span data-ttu-id="68025-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="68025-113">Message Text</span></span>|<span data-ttu-id="68025-114">보안 주체 "*principal*"이(가) 없거나 이 유형의 보안 주체를 가장할 수 없거나 사용 권한이 없기 때문에 데이터베이스 보안 주체로 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68025-114">Cannot execute as the database principal because the principal "*principal*" does not exist, this type of principal cannot be impersonated, or you do not have permission.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="68025-115">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="68025-115">User Action</span></span>  
 <span data-ttu-id="68025-116">기존 보안 주체의 이름을 사용하거나 해당 보안 주체에 대한 IMPERSONATE 권한을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="68025-116">Use the name of an existing principal or get the IMPERSONATE permission on that principal.</span></span>  
  
 <span data-ttu-id="68025-117">15517은 원래 데이터베이스 소유자 이외의 다른 사용자가 데이터베이스 연결 및 복원을 수행한 후에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68025-117">15517 can also occur after performing an attach and restore of a database by someone other than the original database owner.</span></span> <span data-ttu-id="68025-118">이 오류를 해결하려면 다음 명령을 실행해서 db_owner를 서버의 로그인 계정으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="68025-118">To resolve this error, change the db_owner to a login on your server, by running the following command:</span></span>  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a><span data-ttu-id="68025-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68025-119">See Also</span></span>  
 [<span data-ttu-id="68025-120">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="68025-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
