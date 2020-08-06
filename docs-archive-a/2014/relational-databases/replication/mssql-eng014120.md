---
title: MSSQL_ENG014120 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7f3484d9344a203ca8c44fee6b79605163ea069
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638682"
---
# <a name="mssql_eng014120"></a><span data-ttu-id="95186-102">MSSQL_ENG014120</span><span class="sxs-lookup"><span data-stu-id="95186-102">MSSQL_ENG014120</span></span>
    
## <a name="message-details"></a><span data-ttu-id="95186-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="95186-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95186-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="95186-104">Product Name</span></span>|<span data-ttu-id="95186-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="95186-105">SQL Server</span></span>|  
|<span data-ttu-id="95186-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="95186-106">Event ID</span></span>|<span data-ttu-id="95186-107">14120</span><span class="sxs-lookup"><span data-stu-id="95186-107">14120</span></span>|  
|<span data-ttu-id="95186-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="95186-108">Event Source</span></span>|<span data-ttu-id="95186-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="95186-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="95186-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="95186-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="95186-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="95186-111">Symbolic Name</span></span>||  
|<span data-ttu-id="95186-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="95186-112">Message Text</span></span>|<span data-ttu-id="95186-113">배포 데이터베이스 '%s'을(를) 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95186-113">Could not drop the distribution database '%s'.</span></span> <span data-ttu-id="95186-114">이 배포자 데이터베이스가 게시자와 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95186-114">This distributor database is associated with a Publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95186-115">설명</span><span class="sxs-lookup"><span data-stu-id="95186-115">Explanation</span></span>  
 <span data-ttu-id="95186-116">배포 데이터베이스는 트랜잭션 복제에 대한 모든 유형의 복제 및 트랜잭션에 대한 메타데이터와 기록 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="95186-116">The distribution database stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="95186-117">이 오류는 하나 이상의 게시자와 연결된 배포 데이터베이스를 삭제하려고 할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="95186-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95186-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="95186-118">User Action</span></span>  
 <span data-ttu-id="95186-119">배포 데이터베이스를 삭제하려면 먼저 배포자와 게시자 간 연결을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95186-119">To drop a distribution database you must first drop the association between the Distributor and the Publisher.</span></span> <span data-ttu-id="95186-120">자세한 내용은 [sp_dropdistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95186-120">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95186-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95186-121">See Also</span></span>  
 <span data-ttu-id="95186-122">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="95186-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="95186-123">배포 구성</span><span class="sxs-lookup"><span data-stu-id="95186-123">Configure Distribution</span></span>](configure-distribution.md)  
  
  
