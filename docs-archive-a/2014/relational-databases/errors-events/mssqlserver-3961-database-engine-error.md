---
title: MSSQLSERVER_3961 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f55be9288b3c2e559633d0f67709829466fc8815
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659982"
---
# <a name="mssqlserver_3961"></a><span data-ttu-id="1579e-102">MSSQLSERVER_3961</span><span class="sxs-lookup"><span data-stu-id="1579e-102">MSSQLSERVER_3961</span></span>
    
## <a name="details"></a><span data-ttu-id="1579e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1579e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1579e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1579e-104">Product Name</span></span>|<span data-ttu-id="1579e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1579e-105">SQL Server</span></span>|  
|<span data-ttu-id="1579e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1579e-106">Event ID</span></span>|<span data-ttu-id="1579e-107">3961</span><span class="sxs-lookup"><span data-stu-id="1579e-107">3961</span></span>|  
|<span data-ttu-id="1579e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1579e-108">Event Source</span></span>|<span data-ttu-id="1579e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1579e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1579e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1579e-110">Component</span></span>|<span data-ttu-id="1579e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1579e-111">SQLEngine</span></span>|  
|<span data-ttu-id="1579e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1579e-112">Symbolic Name</span></span>|<span data-ttu-id="1579e-113">XACT_METADATA_INVALID</span><span class="sxs-lookup"><span data-stu-id="1579e-113">XACT_METADATA_INVALID</span></span>|  
|<span data-ttu-id="1579e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1579e-114">Message Text</span></span>|<span data-ttu-id="1579e-115">"문에서 액세스한 개체가 이 트랜잭션이 시작된 후 다른 동시 트랜잭션의 DDL 문에 의해 수정되어 데이터베이스 '%.\*ls'에서 스냅샷 격리 트랜잭션이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-115">Snapshot isolation transaction failed in database '%.\*ls' because the object accessed by the statement has been modified by a DDL statement in another concurrent transaction since the start of this transaction.</span></span>  <span data-ttu-id="1579e-116">메타데이터 버전이 관리되지 않기 때문에 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-116">It is disallowed because the metadata is not versioned.</span></span> <span data-ttu-id="1579e-117">메타데이터에 대한 동시 업데이트로 인해 스냅샷 격리와 혼합된 경우 불일치가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-117">A concurrent update to metadata can lead to inconsistency if mixed with snapshot isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1579e-118">설명</span><span class="sxs-lookup"><span data-stu-id="1579e-118">Explanation</span></span>  
 <span data-ttu-id="1579e-119">이 오류는 스냅샷 격리에서 메타데이터를 쿼리하는 경우 스냅샷 격리 하에 액세스되는 메타데이터를 업데이트하는 동시 DDL 문이 있으면 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-119">This error can occur if you are querying metadata under snapshot isolation and there is a concurrent DDL statement that updates the metadata that is being accessed under snapshot isolation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1579e-120">에서는 메타데이터의 버전 관리를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-120">does not support versioning of metadata.</span></span> <span data-ttu-id="1579e-121">따라서, 스냅샷 격리 하에 실행되는 명시적 트랜잭션 내에서 수행할 수 있는 DDL 작업에 대한 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-121">For this reason, there are restrictions on what DDL operations can be performed within an explicit transaction running under snapshot isolation.</span></span> <span data-ttu-id="1579e-122">암시적 트랜잭션은, 정의상, DDL 문과 함께 스냅샷 격리의 의미 체계를 적용할 수 있는 단일 명령문입니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-122">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span> <span data-ttu-id="1579e-123">ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME 또는 CLR(공용 언어 런타임) DDL 문과 같은 DDL 문은 BEGIN TRANSACTION 문 다음에 스냅샷 격리에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-123">The following DDL statements are not permitted under snapshot isolation after a BEGIN TRANSACTION statement: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, or any common language runtime (CLR) DDL statement.</span></span> <span data-ttu-id="1579e-124">다음 명령문은 암시적 트랜잭션 내에서 스냅샷 격리를 사용하는 경우 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-124">These statements are permitted when you are using snapshot isolation within implicit transactions.</span></span> <span data-ttu-id="1579e-125">암시적 트랜잭션은, 정의상, DDL 문과 함께 스냅샷 격리의 의미 체계를 적용할 수 있는 단일 명령문입니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-125">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1579e-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1579e-126">User Action</span></span>  
 <span data-ttu-id="1579e-127">메타데이터를 쿼리하기 전에 스냅샷 격리 수준을 커밋된 읽기와 같은 비스냅샷 격리 수준으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1579e-127">Change the snapshot isolation level to a non-snapshot isolation level such as read committed before querying metadata.</span></span>  
  
  
