---
title: MSSQLSERVER_1203 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cea816a60ccd1b90d849194766edebd2d64d0b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653435"
---
# <a name="mssqlserver_1203"></a><span data-ttu-id="9f6e5-102">MSSQLSERVER_1203</span><span class="sxs-lookup"><span data-stu-id="9f6e5-102">MSSQLSERVER_1203</span></span>
    
## <a name="details"></a><span data-ttu-id="9f6e5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9f6e5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f6e5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9f6e5-104">Product Name</span></span>|<span data-ttu-id="9f6e5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f6e5-105">SQL Server</span></span>|  
|<span data-ttu-id="9f6e5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9f6e5-106">Event ID</span></span>|<span data-ttu-id="9f6e5-107">1203</span><span class="sxs-lookup"><span data-stu-id="9f6e5-107">1203</span></span>|  
|<span data-ttu-id="9f6e5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9f6e5-108">Event Source</span></span>|<span data-ttu-id="9f6e5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9f6e5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9f6e5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9f6e5-110">Component</span></span>|<span data-ttu-id="9f6e5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9f6e5-111">SQLEngine</span></span>|  
|<span data-ttu-id="9f6e5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9f6e5-112">Symbolic Name</span></span>|<span data-ttu-id="9f6e5-113">LK_NOT</span><span class="sxs-lookup"><span data-stu-id="9f6e5-113">LK_NOT</span></span>|  
|<span data-ttu-id="9f6e5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9f6e5-114">Message Text</span></span>|<span data-ttu-id="9f6e5-115">프로세스 ID %d에서 소유하지 않는 리소스의 잠금을 해제하려고 했습니다: %.\*ls.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-115">Process ID %d attempted to unlock a resource it does not own: %.\*ls.</span></span> <span data-ttu-id="9f6e5-116">이 오류는 타이밍 조건에 의해 발생했을 수 있으므로 트랜잭션을 다시 시도해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-116">Retry the transaction, because this error may be caused by a timing condition.</span></span> <span data-ttu-id="9f6e5-117">문제가 지속되면 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-117">If the problem persists, contact the database administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9f6e5-118">설명</span><span class="sxs-lookup"><span data-stu-id="9f6e5-118">Explanation</span></span>  
 <span data-ttu-id="9f6e5-119">이 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 일반 후처리 정리가 아닌 다른 작업 중이며, 잠금 해제를 시도한 특정 페이지가 이미 잠금 해제되어 있음을 발견했을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-119">This error occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is engaged in some activity other than ordinary post-processing cleanup and it finds that a particular page that it is trying to unlock is already unlocked.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="9f6e5-120">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="9f6e5-120">Possible Causes</span></span>  
 <span data-ttu-id="9f6e5-121">이 오류의 근본 원인은 영향을 받는 데이터베이스 내의 구조적 문제와 관련되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-121">The underlying cause of this error may be related to structural problems within the affected database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9f6e5-122">에서는 페이지의 획득과 해제를 관리하여 다중 사용자 환경에서 동시성 제어를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-122">manages the acquisition and release of pages to maintain concurrency control in the multiuser environment.</span></span> <span data-ttu-id="9f6e5-123">이러한 메커니즘은 페이지와 잠금 유형을 식별하는 다양한 내부 잠금 구조를 통해 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-123">This mechanism is maintained by using various internal lock structures that identify the page and the type of lock present.</span></span> <span data-ttu-id="9f6e5-124">잠금은 영향을 받는 페이지를 처리할 때 획득되고 처리가 완료되면 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-124">Locks are acquired for processing of affected pages and released when the processing is finished.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f6e5-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9f6e5-125">User Action</span></span>  
 <span data-ttu-id="9f6e5-126">개체가 속한 데이터베이스에 대해 DBCC CHECKDB를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-126">Execute DBCC CHECKDB against the database in which the object belongs.</span></span> <span data-ttu-id="9f6e5-127">DBCC CHECKDB에서 오류를 보고하지 않는 경우 다시 연결하여 명령을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-127">If DBCC CHECKDB reports no errors, try to reestablish the connection and execute the command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f6e5-128">인덱스 문제를 해결할 수 없는 REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행 중인 경우, 또는 REPAIR 절을 사용할 때 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f6e5-128">If you are executing DBCC CHECKDB with one of the REPAIR clauses does not correct the index problem, or if you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider.</span></span>  
  
  
