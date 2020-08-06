---
title: MSSQLSERVER_1204 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ca03c19552b88e391d2de053193a70531571ece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650077"
---
# <a name="mssqlserver_1204"></a><span data-ttu-id="1ebb4-102">MSSQLSERVER_1204</span><span class="sxs-lookup"><span data-stu-id="1ebb4-102">MSSQLSERVER_1204</span></span>
    
## <a name="details"></a><span data-ttu-id="1ebb4-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1ebb4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ebb4-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1ebb4-104">Product Name</span></span>|<span data-ttu-id="1ebb4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ebb4-105">SQL Server</span></span>|  
|<span data-ttu-id="1ebb4-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1ebb4-106">Event ID</span></span>|<span data-ttu-id="1ebb4-107">1204</span><span class="sxs-lookup"><span data-stu-id="1ebb4-107">1204</span></span>|  
|<span data-ttu-id="1ebb4-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1ebb4-108">Event Source</span></span>|<span data-ttu-id="1ebb4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1ebb4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1ebb4-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1ebb4-110">Component</span></span>|<span data-ttu-id="1ebb4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1ebb4-111">SQLEngine</span></span>|  
|<span data-ttu-id="1ebb4-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1ebb4-112">Symbolic Name</span></span>|<span data-ttu-id="1ebb4-113">LK_OUTOF</span><span class="sxs-lookup"><span data-stu-id="1ebb4-113">LK_OUTOF</span></span>|  
|<span data-ttu-id="1ebb4-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1ebb4-114">Message Text</span></span>|<span data-ttu-id="1ebb4-115">SQL Server 데이터베이스 엔진 인스턴스에서 지금 LOCK 리소스를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-115">The instance of the SQL Server Database Engine cannot obtain a LOCK resource at this time.</span></span> <span data-ttu-id="1ebb4-116">활성 사용자가 적을 때 문을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-116">Rerun your statement when there are fewer active users.</span></span> <span data-ttu-id="1ebb4-117">데이터베이스 관리자에게 이 인스턴스의 잠금 및 메모리 구성이나 장기 실행 트랜잭션을 확인하도록 요청하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-117">Ask the database administrator to check the lock and memory configuration for this instance, or to check for long-running transactions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1ebb4-118">설명</span><span class="sxs-lookup"><span data-stu-id="1ebb4-118">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1ebb4-119">에서 리소스를 잠글 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-119">cannot obtain a lock resource.</span></span> <span data-ttu-id="1ebb4-120">이 오류는 다음과 같은 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-120">This can be caused by either of the following reasons:</span></span>  
  
-   <span data-ttu-id="1ebb4-121">다른 프로세스가 사용 중이거나 서버가 **max server memory** 옵션이 구성된 상태로 동작 중이어서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 운영 체제에서 더 많은 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot allocate more memory from the operating system, either because other processes are using it, or because the server is operating with the **max server memory** option configured.</span></span>  
  
-   <span data-ttu-id="1ebb4-122">잠금 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용 가능한 메모리의 60% 이상을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-122">The lock manager will not use more than 60 percent of the memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ebb4-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1ebb4-123">User Action</span></span>  
 <span data-ttu-id="1ebb4-124">SQL Server에 충분한 메모리를 할당할 수 없는 경우 다음을 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-124">If you suspect that SQL Server cannot allocate sufficient memory, try the following:</span></span>  
  
-   <span data-ttu-id="1ebb4-125">SQL Server 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-125">If applications besides SQL Server are consuming resources, try stopping these applications or consider running them on a separate server.</span></span> <span data-ttu-id="1ebb4-126">이렇게 하면 다른 프로세스에서 사용하는 메모리를 해제하여 SQL Server에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-126">This will remove release memory from other processes for SQL Server.</span></span>  
  
-   <span data-ttu-id="1ebb4-127">max server memory를 구성한 경우 설정값을 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-127">If you have configured max server memory, increase max server memory setting.</span></span>  
  
 <span data-ttu-id="1ebb4-128">잠금 관리자가 최대 가용 메모리 양을 사용한 경우 가장 많은 잠금을 보유한 트랜잭션을 확인하여 이를 종료하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-128">If you suspect that the lock manager has used the maximum amount of available memory identify the transaction that is holding the most locks and terminate it.</span></span> <span data-ttu-id="1ebb4-129">다음 스크립트를 사용하여 가장 많은 잠금을 보유한 트랜잭션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-129">The following script will identify the transaction with the most locks:</span></span>  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 <span data-ttu-id="1ebb4-130">가장 높은 세션 ID를 확인하고 KILL 명령을 사용하여 종료하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-130">Take the highest session id, and terminate it using the KILL command.</span></span>  
  
  
