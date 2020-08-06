---
title: MSSQLSERVER_1461 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6667728b2cc134632ddc538b662d73533ee4d6ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653947"
---
# <a name="mssqlserver_1461"></a><span data-ttu-id="ec23c-102">MSSQLSERVER_1461</span><span class="sxs-lookup"><span data-stu-id="ec23c-102">MSSQLSERVER_1461</span></span>
    
## <a name="details"></a><span data-ttu-id="ec23c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ec23c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec23c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ec23c-104">Product Name</span></span>|<span data-ttu-id="ec23c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ec23c-105">SQL Server</span></span>|  
|<span data-ttu-id="ec23c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ec23c-106">Event ID</span></span>|<span data-ttu-id="ec23c-107">1461</span><span class="sxs-lookup"><span data-stu-id="ec23c-107">1461</span></span>|  
|<span data-ttu-id="ec23c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ec23c-108">Event Source</span></span>|<span data-ttu-id="ec23c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ec23c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ec23c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ec23c-110">Component</span></span>|<span data-ttu-id="ec23c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ec23c-111">SQLEngine</span></span>|  
|<span data-ttu-id="ec23c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ec23c-112">Symbolic Name</span></span>|<span data-ttu-id="ec23c-113">DBM_SAFETY_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="ec23c-113">DBM_SAFETY_MISMATCH</span></span>|  
|<span data-ttu-id="ec23c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ec23c-114">Message Text</span></span>|<span data-ttu-id="ec23c-115">데이터베이스 "%.\*ls"에 대한 데이터베이스 미러링 보안 수준이 서버마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ec23c-115">Different database mirroring safety levels among servers were detected for database "%.\*ls".</span></span> <span data-ttu-id="ec23c-116">FULL 보안 수준이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec23c-116">The FULL safety level will be used.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ec23c-117">설명</span><span class="sxs-lookup"><span data-stu-id="ec23c-117">Explanation</span></span>  
 <span data-ttu-id="ec23c-118">트랜잭션 보안 설정이 주 데이터베이스 및 미러 데이터베이스에서 일관성이 없어 트랜잭션 보안 수준이 수정되는 동안 미러링 연결이 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="ec23c-118">Mirroring connections were broken when the transaction safety level was modified because the transaction safety settings were inconsistent on the principal and mirror databases.</span></span> <span data-ttu-id="ec23c-119">전체 트랜잭션 보안의 기본 보안 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ec23c-119">The default safety setting of full-transaction safety will be used.</span></span> <span data-ttu-id="ec23c-120">세션은 보호 우선 모드에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec23c-120">The session will run in high-safety mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ec23c-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ec23c-121">User Action</span></span>  
 <span data-ttu-id="ec23c-122">트랜잭션 보안 해제를 설정하려면 ALTER DATABASE *database_name* SET PARTNER SAFETY OFF 문을 주 데이터베이스에서 다시 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="ec23c-122">To set transaction safety off, rerun the ALTER DATABASE *database_name* SET PARTNER SAFETY OFF statement on the principal database.</span></span>  
  
  
