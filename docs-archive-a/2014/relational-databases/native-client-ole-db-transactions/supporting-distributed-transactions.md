---
title: 분산 트랜잭션 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a30a44dc007852922aa71685728b26e5bb872c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738247"
---
# <a name="supporting-distributed-transactions"></a><span data-ttu-id="cb2ae-102">분산 트랜잭션 지원</span><span class="sxs-lookup"><span data-stu-id="cb2ae-102">Supporting Distributed Transactions</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="cb2ae-103">Native Client OLE DB 공급자 소비자는 **ITransactionJoin:: JoinTransaction** 메서드를 사용 하 여 MS DTC (Microsoft DTC(Distributed Transaction Coordinator))에서 조정 하는 분산 트랜잭션에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-103">Native Client OLE DB provider consumers can use the **ITransactionJoin::JoinTransaction** method to participate in a distributed transaction coordinated by Microsoft Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="cb2ae-104">MS DTC는 클라이언트가 여러 데이터 저장소에 대한 둘 이상의 연결에서 통합 트랜잭션을 시작하거나 통합 트랜잭션에 참가하는 데 사용할 수 있는 COM 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-104">MS DTC exposes COM objects that allow clients to initiate and participate in coordinated transactions across multiple connections to a variety of data stores.</span></span> <span data-ttu-id="cb2ae-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 소비자는 트랜잭션을 시작 하기 위해 MS DTC **ITransactionDispenser** 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-105">To initiate a transaction, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses the MS DTC **ITransactionDispenser** interface.</span></span> <span data-ttu-id="cb2ae-106">**ITransactionDispenser**의 **BeginTransaction** 멤버는 분산 트랜잭션 개체에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-106">The **BeginTransaction** member of **ITransactionDispenser** returns a reference on a distributed transaction object.</span></span> <span data-ttu-id="cb2ae-107">이 참조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **JoinTransaction**을 사용 하 여 Native Client OLE DB 공급자로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-107">This reference is passed to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider using **JoinTransaction**.</span></span>  
  
 <span data-ttu-id="cb2ae-108">MS DTC는 분산 트랜잭션에 대해 비동기 커밋 및 중단을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-108">MS DTC supports asynchronous commit and abort on distributed transactions.</span></span> <span data-ttu-id="cb2ae-109">비동기 트랜잭션 상태에 대한 알림을 제공하려면 소비자는 **ITransactionOutcomeEvents** 인터페이스를 구현하고 이 인터페이스를 MS DTC 트랜잭션 개체에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-109">For notification on asynchronous transaction status, the consumer implements the **ITransactionOutcomeEvents** interface and connects the interface to an MS DTC transaction object.</span></span>  
  
 <span data-ttu-id="cb2ae-110">분산 트랜잭션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음과 같이 **ITransactionJoin:: JoinTransaction** 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-110">For distributed transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransactionJoin::JoinTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="cb2ae-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cb2ae-111">Parameter</span></span>|<span data-ttu-id="cb2ae-112">설명</span><span class="sxs-lookup"><span data-stu-id="cb2ae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb2ae-113">*punkTransactionCoord*</span><span class="sxs-lookup"><span data-stu-id="cb2ae-113">*punkTransactionCoord*</span></span>|<span data-ttu-id="cb2ae-114">MS DTC 트랜잭션 개체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-114">A pointer to an MS DTC transaction object.</span></span>|  
|<span data-ttu-id="cb2ae-115">*IsoLevel*</span><span class="sxs-lookup"><span data-stu-id="cb2ae-115">*IsoLevel*</span></span>|<span data-ttu-id="cb2ae-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자가 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-116">Ignored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="cb2ae-117">MS DTC 통합 트랜잭션의 격리 수준은 소비자가 MS DTC로부터 트랜잭션 개체를 가져올 때 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-117">The isolation level for MS DTC-coordinated transactions is determined when the consumer acquires a transaction object from MS DTC.</span></span>|  
|<span data-ttu-id="cb2ae-118">*IsoFlags*</span><span class="sxs-lookup"><span data-stu-id="cb2ae-118">*IsoFlags*</span></span>|<span data-ttu-id="cb2ae-119">0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-119">Must be 0.</span></span> <span data-ttu-id="cb2ae-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]소비자가 다른 값을 지정 하는 경우 Native Client OLE DB 공급자는 XACT_E_NOISORETAIN를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOISORETAIN if any other value is specified by the consumer.</span></span>|  
|<span data-ttu-id="cb2ae-121">*POtherOptions*</span><span class="sxs-lookup"><span data-stu-id="cb2ae-121">*POtherOptions*</span></span>|<span data-ttu-id="cb2ae-122">NULL이 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 인터페이스에서 options 개체를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-122">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="cb2ae-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션 개체의 *ultimeout* 멤버가 0이 아니면 Native Client OLE DB 공급자가 XACT_E_NOTIMEOUT을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="cb2ae-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 *szdescription* 멤버의 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
  
 <span data-ttu-id="cb2ae-125">이 예에서는 MS DTC를 사용하여 트랜잭션을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="cb2ae-125">This example coordinates transaction by using MS DTC.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb2ae-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb2ae-126">See Also</span></span>  
 [<span data-ttu-id="cb2ae-127">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="cb2ae-127">Transactions</span></span>](transactions.md)  
  
  
