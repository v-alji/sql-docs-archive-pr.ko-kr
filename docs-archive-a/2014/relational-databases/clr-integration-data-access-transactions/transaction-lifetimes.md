---
title: 트랜잭션 수명 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742295"
---
# <a name="transaction-lifetimes"></a><span data-ttu-id="7972b-102">트랜잭션 수명</span><span class="sxs-lookup"><span data-stu-id="7972b-102">Transaction Lifetimes</span></span>
  <span data-ttu-id="7972b-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저에서 시작된 트랜잭션과 관리 코드에서 시작된 트랜잭션 사이에는 중요한 차이점이 있습니다. 즉, CLR(공용 언어 런타임) 코드에서는 CLR 호출 시작 또는 종료 시 불균형한 트랜잭션 상태를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-103">There is an important difference between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and those started in managed code: common language runtime (CLR) code cannot unbalance the transaction state on entry or exit of a CLR invocation.</span></span> <span data-ttu-id="7972b-104">이 차이점으로 인해 발생하는 다음과 같은 문제점에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="7972b-104">Be aware of the following implications of this difference:</span></span>  
  
-   <span data-ttu-id="7972b-105">CLR 프레임에서 시작된 트랜잭션을 커밋하거나 롤백하지 않으면 프레임 종료 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-105">A transaction started inside a CLR frame must be committed or rolled back, or else [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generates an error when the frame is exited.</span></span>  
  
-   <span data-ttu-id="7972b-106">외부 트랜잭션은 CLR 코드 내에서 커밋하거나 롤백할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-106">An outer transaction cannot be committed or rolled back inside the CLR code.</span></span>  
  
-   <span data-ttu-id="7972b-107">다른 프로시저에서 시작된 트랜잭션을 커밋하려고 하면 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-107">An attempt to commit a transaction not started in the same procedure causes a run-time error.</span></span>  
  
-   <span data-ttu-id="7972b-108">같은 프로시저에서 시작 되지 않은 트랜잭션을 롤백하려고 하면 트랜잭션이 응답을 중지 하 게 됩니다. 다른 모든 주는 작업이 발생 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-108">An attempt to roll back a transaction not started in the same procedure causes the transaction to stop responding (preventing any other side-effecting operation from happening).</span></span> <span data-ttu-id="7972b-109">트랜잭션은 CLR 코드가 범위를 벗어날 때까지 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-109">The transaction discontinues until the CLR code goes out of scope.</span></span> <span data-ttu-id="7972b-110">프로시저 내에 오류가 있어 전체 트랜잭션을 종료하려는 경우에는 이 동작이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7972b-110">Note that this can be useful when you detect an error inside your procedure and want to make sure the whole transaction terminates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7972b-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7972b-111">See Also</span></span>  
 [<span data-ttu-id="7972b-112">CLR 통합 및 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="7972b-112">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
