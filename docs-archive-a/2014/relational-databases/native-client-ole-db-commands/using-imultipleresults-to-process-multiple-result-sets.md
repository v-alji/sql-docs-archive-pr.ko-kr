---
title: IMultipleResults를 사용하여 여러 결과 집합 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: rothja
ms.author: jroth
ms.openlocfilehash: c7acac7e6ce75189e522b503707e101c0a13c345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740884"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a><span data-ttu-id="f1d1c-102">IMultipleResults를 사용하여 여러 결과 집합 처리</span><span class="sxs-lookup"><span data-stu-id="f1d1c-102">Using IMultipleResults to Process Multiple Result Sets</span></span>
  <span data-ttu-id="f1d1c-103">소비자는 **IMultipleResults** 인터페이스를 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 명령 실행에 의해 반환 된 결과를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-103">Consumers use the **IMultipleResults** interface to process results returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution.</span></span> <span data-ttu-id="f1d1c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자가 실행을 위해 명령을 전송할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문을 실행 하 고 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-104">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a command for execution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statements and returns any results.</span></span>  
  
 <span data-ttu-id="f1d1c-105">클라이언트는 명령 실행을 통해 반환된 모든 결과를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-105">A client must process all results from command execution.</span></span> <span data-ttu-id="f1d1c-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 명령 실행은 여러 행 집합 개체를 결과로 생성할 수 있으므로 **IMultipleResults** 인터페이스를 사용 하 여 응용 프로그램 데이터 검색이 클라이언트에서 시작한 왕복을 완료 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-106">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution can generate multiple-rowset objects as results, use the **IMultipleResults** interface to ensure that application data retrieval completes the client-initiated round trip.</span></span>  
  
 <span data-ttu-id="f1d1c-107">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 여러 행 집합을 생성합니다. 이 중에는 **OrderDetails** 테이블의 행 데이터 집합도 있고, COMPUTE BY 절의 결과 집합도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-107">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple rowsets, some containing row data from the **OrderDetails** table and some containing results of the COMPUTE BY clause:</span></span>  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 <span data-ttu-id="f1d1c-108">소비자가 이 텍스트를 포함하는 명령을 실행하고 반환되는 결과 인터페이스로 행 집합을 요청하면 첫 번째 행 집합만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-108">If a consumer executes a command containing this text and requests a rowset as the returned results interface, only the first set of rows is returned.</span></span> <span data-ttu-id="f1d1c-109">이 경우 소비자는 반환되는 행 집합에 있는 모든 행을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-109">The consumer may process all rows in the rowset returned.</span></span> <span data-ttu-id="f1d1c-110">그러나 DBPROP_MULTIPLECONNECTIONS 데이터 원본 속성이 VARIANT_FALSE로 설정 되 고 MARS가 연결에 대해 사용 하도록 설정 되어 있지 않은 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명령이 취소 될 때까지 세션 개체 (Native Client OLE DB 공급자는 다른 연결을 만들지 않음)에서 다른 명령을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-110">But, if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_FALSE, and MARS is not enabled on the connection, no other commands can be executed on the session object (the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will not create another connection) until the command is canceled.</span></span> <span data-ttu-id="f1d1c-111">연결에 MARS가 설정 되어 있지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE 경우 DB_E_OBJECTOPEN 오류를 반환 하 고 활성 트랜잭션이 있는 경우 E_FAIL를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-111">If MARS is not enabled on the connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns a DB_E_OBJECTOPEN error if DBPROP_MULTIPLECONNECTIONS is VARIANT_FALSE and returns E_FAIL if there is an active transaction.</span></span>  
  
 <span data-ttu-id="f1d1c-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 스트리밍된 출력 매개 변수를 사용 하 고 **IMultipleResults:: GetResults** 를 호출 하 여 다음 결과 집합을 가져오기 전에 응용 프로그램에서 반환 된 출력 매개 변수 값을 모두 사용 하지 않은 경우에도 DB_E_OBJECTOPEN을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will also return DB_E_OBJECTOPEN when using streamed output parameters and the application has not consumed all the returned output parameter values before calling **IMultipleResults::GetResults** to get the next result set.</span></span> <span data-ttu-id="f1d1c-113">MARS가 설정되어 있지 않은 상태에서 연결이 행 집합을 생성하지 않는 명령 또는 서버 커서가 아닌 행 집합을 생성하는 명령을 실행 중이고 DBPROP_MULTIPLECONNECTIONS 데이터 원본 속성이 VARIANT_TRUE로 설정되어 있는 경우, 트랜잭션이 오류를 반환하는 활성 상태가 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 동시 명령 개체를 지원하기 위해 추가 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-113">If MARS is not enabled and the connection is busy running a command that does not produce a rowset or that produces a rowset that is not a server cursor, and if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates additional connections to support concurrent command objects, unless a transaction is active, in which case it returns an error.</span></span> <span data-ttu-id="f1d1c-114">트랜잭션 및 잠금은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 연결별로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-114">Transactions and locking are managed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a per connection basis.</span></span> <span data-ttu-id="f1d1c-115">두 번째 연결이 생성되면 개별 연결의 명령이 잠금을 공유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-115">If a second connection is generated, the command on the separate connections does not share locks.</span></span> <span data-ttu-id="f1d1c-116">한 명령이 다른 명령을 차단하지 않도록 다른 명령이 요청한 행의 잠금이 유지되도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-116">Care must be taken to ensure that one command does not block another by holding locks on rows requested by the other command.</span></span> <span data-ttu-id="f1d1c-117">MARS가 설정되어 있는 경우 연결에 여러 명령을 활성화할 수 있으며 명시적 트랜잭션이 사용 중인 경우 모든 명령이 공통 트랜잭션을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-117">If MARS is enabled, multiple commands can be active on the connections and if explicit transactions are being used, the commands all share a common transaction.</span></span>  
  
 <span data-ttu-id="f1d1c-118">소비자는 [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md)를 사용하거나 명령 개체 및 파생 행 집합에서 유지하는 모든 참조를 해제하는 방식으로 명령을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-118">The consumer can cancel the command either by using [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) or by releasing all references held on the command object and the derived rowset.</span></span>  
  
 <span data-ttu-id="f1d1c-119">소비자는 모든 인스턴스에서 **IMultipleResults**를 사용하여 명령 실행을 통해 생성된 모든 행 집합을 얻을 수 있으며, 명령 실행을 취소하여 다른 명령에서 사용할 수 있도록 세션 개체를 해제할 적절한 시점을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-119">Using **IMultipleResults** in all instances allows the consumer to get all rowsets generated by command execution and allows consumers to appropriately determine when to cancel command execution and free a session object for use by other commands.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1d1c-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서를 사용할 때 명령을 실행하면 커서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-120">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, command execution creates the cursor.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="f1d1c-121">는 커서 생성에 대한 성공이나 실패를 반환하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 왕복은 명령 실행 결과가 반환되면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-121">returns success or failure on the cursor creation; therefore, the round trip to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is complete upon the return from command execution.</span></span> <span data-ttu-id="f1d1c-122">**GetNextRows**를 호출할 때마다 왕복이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-122">Each **GetNextRows** call then becomes a round trip.</span></span> <span data-ttu-id="f1d1c-123">따라서 여러 활성 명령 개체가 존재할 수 있으며, 이러한 각각의 개체가 서버 커서에서 인출한 결과 행 집합을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-123">In this way, multiple active command objects can exist, each processing a rowset that is the result of a fetch from the server cursor.</span></span> <span data-ttu-id="f1d1c-124">자세한 내용은 [행 집합 및 SQL Server 커서](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f1d1c-124">For more information, see [Rowsets and SQL Server Cursors](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d1c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1d1c-125">See Also</span></span>  
 [<span data-ttu-id="f1d1c-126">명령</span><span class="sxs-lookup"><span data-stu-id="f1d1c-126">Commands</span></span>](commands.md)  
  
  
