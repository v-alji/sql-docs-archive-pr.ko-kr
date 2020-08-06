---
title: MSSQLSERVER_7915 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1dc7a69023e49b48a10da9f0388cbd72fbe46be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651708"
---
# <a name="mssqlserver_7915"></a><span data-ttu-id="8726f-102">MSSQLSERVER_7915</span><span class="sxs-lookup"><span data-stu-id="8726f-102">MSSQLSERVER_7915</span></span>
    
## <a name="details"></a><span data-ttu-id="8726f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8726f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8726f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8726f-104">Product Name</span></span>|<span data-ttu-id="8726f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8726f-105">SQL Server</span></span>|  
|<span data-ttu-id="8726f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8726f-106">Event ID</span></span>|<span data-ttu-id="8726f-107">7915</span><span class="sxs-lookup"><span data-stu-id="8726f-107">7915</span></span>|  
|<span data-ttu-id="8726f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8726f-108">Event Source</span></span>|<span data-ttu-id="8726f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8726f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8726f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8726f-110">Component</span></span>|<span data-ttu-id="8726f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8726f-111">SQLEngine</span></span>|  
|<span data-ttu-id="8726f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8726f-112">Symbolic Name</span></span>|<span data-ttu-id="8726f-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span><span class="sxs-lookup"><span data-stu-id="8726f-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span></span>|  
|<span data-ttu-id="8726f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8726f-114">Message Text</span></span>|<span data-ttu-id="8726f-115">복구: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 대한 IAM 체인이 페이지 P_ID 앞에서 잘렸으므로 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8726f-115">Repair: IAM chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), has been truncated before page P_ID and will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8726f-116">설명</span><span class="sxs-lookup"><span data-stu-id="8726f-116">Explanation</span></span>  
 <span data-ttu-id="8726f-117">REPAIR에서 전송한 이 정보 메시지는 지정된 IAM(Index Allocation Map) 체인이 패치되어 다시 작성될 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8726f-117">This is an information message sent by REPAIR that indicates that the specified Index Allocation Map (IAM) chain was patched so that it could be rebuilt.</span></span> <span data-ttu-id="8726f-118">패치 작업은 IAM 체인의 새 헤드를 할당하거나 체인에서 잘못된 페이지를 제거할 때 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8726f-118">This patching may have required the allocation of a new head of the IAM chain or the removal of bad pages from the chain.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8726f-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8726f-119">User Action</span></span>  
 <span data-ttu-id="8726f-120">None</span><span class="sxs-lookup"><span data-stu-id="8726f-120">None</span></span>  
  
  
