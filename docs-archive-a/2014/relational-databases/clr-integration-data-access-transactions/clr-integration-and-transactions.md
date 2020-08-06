---
title: CLR 통합 및 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742300"
---
# <a name="clr-integration-and-transactions"></a><span data-ttu-id="a3ceb-102">CLR 통합 및 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="a3ceb-102">CLR Integration and Transactions</span></span>
  <span data-ttu-id="a3ceb-103">`System.Transactions` 네임스페이스는 이미 통합된 ADO.NET 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR(공용 언어 런타임)과 완전히 통합되는 트랜잭션 프레임워크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="a3ceb-104">`System.Transactions` 및 ADO.NET은 함께 작동하여 관리되는 애플리케이션에서 로컬 및 분산 트랜잭션의 사용을 확장하고 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-104">`System.Transactions` and ADO.NET work together to extend and simplify the use of local and distributed transactions in managed applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3ceb-105">CLR UDP(사용자 정의 프로시저)는 해당 프로시저가 실행되는 서버에 대한 연결(루프백 연결)을 설정할 수 없으며 동일한 트랜잭션에 참여할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-105">A CLR user-defined procedure (UDP) cannot establish a connection to the same server it is running on (a loopback connection) and enlist in the same transaction.</span></span> <span data-ttu-id="a3ceb-106">이러한 작업을 시도하면 연결 시도가 차단되고 제어가 다시 UDP로 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-106">If this is attempted, the connection attempt will be blocked and control will not be passed back to the UDP.</span></span> <span data-ttu-id="a3ceb-107">이 경우 UDP에서 시간 초과 오류(메시지 1206)가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-107">This will result in a timeout error (Msg 1206) on the UDP.</span></span>  
  
 <span data-ttu-id="a3ceb-108">트랜잭션 및 .NET Framework에 대한 자세한 내용은 .NET Framework SDK의 "트랜잭션 수행" 및 "트랜잭션 이용"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-108">For more information about transactions and the .NET Framework, see "Performing Transactions" and "Leveraging Transactions" in the .NET Framework SDK.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3ceb-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a3ceb-109">In This Section</span></span>  
 [<span data-ttu-id="a3ceb-110">트랜잭션 승격</span><span class="sxs-lookup"><span data-stu-id="a3ceb-110">Transaction Promotion</span></span>](transaction-promotion.md)  
 <span data-ttu-id="a3ceb-111">트랜잭션을 승격하는 기능과 이 기능을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-111">Describes the ability to promote transactions, and how to use this feature.</span></span>  
  
 [<span data-ttu-id="a3ceb-112">현재 트랜잭션 액세스</span><span class="sxs-lookup"><span data-stu-id="a3ceb-112">Accessing the Current Transaction</span></span>](accessing-the-current-transaction.md)  
 <span data-ttu-id="a3ceb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 현재 in-process으로 실행 중인 트랜잭션에 액세스하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-113">Describes how to access a transaction currently running in-process on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="a3ceb-114">System.Transactions 사용</span><span class="sxs-lookup"><span data-stu-id="a3ceb-114">Using System.Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="a3ceb-115">관리되는 애플리케이션에서 `System.Transactions` API(응용 프로그래밍 인터페이스)를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-115">Describes how to use the `System.Transactions` application programming interface (API) in your managed application.</span></span>  
  
 [<span data-ttu-id="a3ceb-116">트랜잭션 수명</span><span class="sxs-lookup"><span data-stu-id="a3ceb-116">Transaction Lifetimes</span></span>](transaction-lifetimes.md)  
 <span data-ttu-id="a3ceb-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저에서 시작된 트랜잭션과 CLR 애플리케이션에서 시작된 트랜잭션의 수명 차이에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a3ceb-117">Describes the difference in lifetime between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and transactions started in CLR applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ceb-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3ceb-118">See Also</span></span>  
 [<span data-ttu-id="a3ceb-119">CLR 데이터베이스 개체에서 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="a3ceb-119">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
