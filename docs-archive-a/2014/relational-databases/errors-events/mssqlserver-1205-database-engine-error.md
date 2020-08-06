---
title: MSSQLSERVER_1205 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6afa81a05eea37bc67cd2e9ac2433b6c82f35b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638821"
---
# <a name="mssqlserver_1205"></a><span data-ttu-id="c6d00-102">MSSQLSERVER_1205</span><span class="sxs-lookup"><span data-stu-id="c6d00-102">MSSQLSERVER_1205</span></span>
    
## <a name="details"></a><span data-ttu-id="c6d00-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c6d00-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6d00-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c6d00-104">Product Name</span></span>|<span data-ttu-id="c6d00-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6d00-105">SQL Server</span></span>|  
|<span data-ttu-id="c6d00-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c6d00-106">Event ID</span></span>|<span data-ttu-id="c6d00-107">1205</span><span class="sxs-lookup"><span data-stu-id="c6d00-107">1205</span></span>|  
|<span data-ttu-id="c6d00-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c6d00-108">Event Source</span></span>|<span data-ttu-id="c6d00-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c6d00-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c6d00-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c6d00-110">Component</span></span>|<span data-ttu-id="c6d00-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c6d00-111">SQLEngine</span></span>|  
|<span data-ttu-id="c6d00-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c6d00-112">Symbolic Name</span></span>|<span data-ttu-id="c6d00-113">LK_VICTIM</span><span class="sxs-lookup"><span data-stu-id="c6d00-113">LK_VICTIM</span></span>|  
|<span data-ttu-id="c6d00-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c6d00-114">Message Text</span></span>|<span data-ttu-id="c6d00-115">트랜잭션(프로세스 ID %d)이 %.\*ls 리소스에서 다른 프로세스와의 교착 상태가 발생하여 실행이 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-115">Transaction (Process ID %d) was deadlocked on %.\*ls resources with another process and has been chosen as the deadlock victim.</span></span> <span data-ttu-id="c6d00-116">트랜잭션을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="c6d00-116">Rerun the transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6d00-117">설명</span><span class="sxs-lookup"><span data-stu-id="c6d00-117">Explanation</span></span>  
 <span data-ttu-id="c6d00-118">리소스가 별도의 트랜잭션에서 충돌하는 순서대로 액세스되면 교착 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-118">Resources are accessed in conflicting order on separate transactions, causing a deadlock.</span></span> <span data-ttu-id="c6d00-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-119">For example:</span></span>  
  
-   <span data-ttu-id="c6d00-120">Transaction2가 **Table2.Row2**를 업데이트하는 동안 Transaction1이 **Table1.Row1**을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-120">Transaction1 updates **Table1.Row1**, while Transaction2 updates **Table2.Row2**.</span></span>  
  
-   <span data-ttu-id="c6d00-121">Transaction1이 **Table2.Row2**의 업데이트를 시도하지만 Transaction2가 커밋되지 않아 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-121">Transaction1 tries to update **Table2.Row2** but is blocked because Transaction2 has not yet committed.</span></span>  
  
-   <span data-ttu-id="c6d00-122">이제 Transaction2가 **Table1.Row1**의 업데이트를 시도하지만 Transaction1이 커밋되지 않아 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-122">Transaction2 now tries to update **Table1.Row1** but is blocked because Transaction1 has not committed.</span></span>  
  
-   <span data-ttu-id="c6d00-123">Transaction1은 Transaction2가 완료되기를 기다리지만 Transaction2는 Transaction1이 완료되기를 기다리므로 교착 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-123">A deadlock occurs because Transaction1 is waiting for Transaction2 to complete, but Transaction2 is waiting for Transaction1 to complete.</span></span>  
  
 <span data-ttu-id="c6d00-124">시스템에서는 이 '교착 상태'를 감지하면 관련된 트랜잭션 중 하나를 '희생자'로 선택하고 이 메시지를 보낸 후 희생자의 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-124">The system will detect this deadlock and will choose one of the transactions involved as a 'victim' and will issue this message, rolling back the victim's transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6d00-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c6d00-125">User Action</span></span>  
 <span data-ttu-id="c6d00-126">트랜잭션을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="c6d00-126">Execute the transaction again.</span></span> <span data-ttu-id="c6d00-127">교착 상태가 발생하지 않도록 애플리케이션을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-127">You can also revise the application to avoid deadlocks.</span></span> <span data-ttu-id="c6d00-128">교착 상태가 발생한 트랜잭션을 다시 실행하면 동시에 실행 중인 작업이 무엇인지에 따라 성공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-128">The transaction that was chosen as a victim can be retried and will likely succeed, depending on what operations are being executed simultaneously.</span></span>  
  
 <span data-ttu-id="c6d00-129">교착 상태를 방지하거나 발생하지 않도록 하려면 모든 트랜잭션이 동일한 순서(**Table1**에 액세스한 뒤 **Table2**에 액세스)로 행에 액세스하도록 하세요. 이렇게 하면 차단이 발생할 수는 있으나 교착 상태는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d00-129">To prevent or avoid deadlocks from occurring, consider having all transactions access rows in the same order (**Table1**, then **Table2**); this way, although blocking might occur, a deadlock will not occur.</span></span>  
  
  
