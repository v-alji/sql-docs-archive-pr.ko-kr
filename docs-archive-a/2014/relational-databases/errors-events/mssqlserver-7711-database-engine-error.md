---
title: MSSQLSERVER_7711 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e29b2ea993e8e5332ef03b05f628dc791e20aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651014"
---
# <a name="mssqlserver_7711"></a><span data-ttu-id="e1d34-102">MSSQLSERVER_7711</span><span class="sxs-lookup"><span data-stu-id="e1d34-102">MSSQLSERVER_7711</span></span>
    
## <a name="details"></a><span data-ttu-id="e1d34-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e1d34-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1d34-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e1d34-104">Product Name</span></span>|<span data-ttu-id="e1d34-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1d34-105">SQL Server</span></span>|  
|<span data-ttu-id="e1d34-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e1d34-106">Event ID</span></span>|<span data-ttu-id="e1d34-107">7711</span><span class="sxs-lookup"><span data-stu-id="e1d34-107">7711</span></span>|  
|<span data-ttu-id="e1d34-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e1d34-108">Event Source</span></span>|<span data-ttu-id="e1d34-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e1d34-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e1d34-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e1d34-110">Component</span></span>|<span data-ttu-id="e1d34-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e1d34-111">SQLEngine</span></span>|  
|<span data-ttu-id="e1d34-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e1d34-112">Symbolic Name</span></span>|<span data-ttu-id="e1d34-113">PRT_RANGE_OVERLAP</span><span class="sxs-lookup"><span data-stu-id="e1d34-113">PRT_RANGE_OVERLAP</span></span>|  
|<span data-ttu-id="e1d34-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e1d34-114">Message Text</span></span>|<span data-ttu-id="e1d34-115">DATA_COMPRESSION 옵션이 테이블이나 인덱스 또는 해당 파티션 중 하나에 대해 두 번 이상 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1d34-115">The DATA_COMPRESSION option was specified more than once for the table or index or one of its partitions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1d34-116">설명</span><span class="sxs-lookup"><span data-stu-id="e1d34-116">Explanation</span></span>  
 <span data-ttu-id="e1d34-117">다음 문 중 하나에서 DATA_COMPRESSION 옵션을 사용할 때 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="e1d34-117">An error occurred in the DATA_COMPRESSION option in one of the following statements:</span></span>  
  
-   <span data-ttu-id="e1d34-118">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="e1d34-118">CREATE TABLE</span></span>  
  
-   <span data-ttu-id="e1d34-119">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="e1d34-119">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="e1d34-120">CREATE  INDEX</span><span class="sxs-lookup"><span data-stu-id="e1d34-120">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="e1d34-121">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="e1d34-121">ALTER INDEX</span></span>  
  
 <span data-ttu-id="e1d34-122">해당 테이블이나 인덱스가 분할된 경우 DATA_COMPRESSION 옵션이 최소한 하나 이상의 파티션에 대해 두 번 이상 나열되었고,</span><span class="sxs-lookup"><span data-stu-id="e1d34-122">If the table or index cited is partitioned, the DATA_COMPRESSION option was listed more than one time for at least one of the partitions.</span></span> <span data-ttu-id="e1d34-123">테이블이나 인덱스가 분할되지 않은 경우 DATA_COMPRESSION 옵션이 두 번 이상 나열되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1d34-123">If the table or index is not partitioned, the DATA_COMPRESSION option was cited more than one time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1d34-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e1d34-124">User Action</span></span>  
 <span data-ttu-id="e1d34-125">분할된 테이블이나 인덱스의 경우 DATA_COMPRESSION 옵션이 각 파티션에 대해 한 번만 지정되었는지 확인하고,</span><span class="sxs-lookup"><span data-stu-id="e1d34-125">For a partitioned table or index, make sure that the DATA_COMPRESSION option is specified only one time for each partition.</span></span> <span data-ttu-id="e1d34-126">분할되지 않은 테이블이나 인덱스의 경우 문에서 DATA_COMPRESSION 옵션을 한 번만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1d34-126">For a table or index that is not partitioned, use the DATA_COMPRESSION option only one time in the statement.</span></span>  
  
  
