---
title: Microsoft DTC(Distributed Transaction Coordinator) 사용 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: f7b7da33066a9f4edd01037738ed91155340e6ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649977"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a><span data-ttu-id="fde28-102">Microsoft Distributed Transaction Coordinator 사용(ODBC)</span><span class="sxs-lookup"><span data-stu-id="fde28-102">Use Microsoft Distributed Transaction Coordinator (ODBC)</span></span>
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a><span data-ttu-id="fde28-103">MS DTC를 사용하여 두 대 이상의 SQL Server를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="fde28-103">To update two or more SQL Servers by using MS DTC</span></span>  
  
1.  <span data-ttu-id="fde28-104">MS DTC OLE DtcGetTransactionManager 함수를 사용하여 MS DTC에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-104">Connect to MS DTC by using the MS DTC OLE DtcGetTransactionManager function.</span></span> <span data-ttu-id="fde28-105">MS DTC에 대한 자세한 내용은 Microsoft Distributed Transaction Coordinator를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fde28-105">For information about MS DTC, see Microsoft Distributed Transaction Coordinator.</span></span>  
  
2.  <span data-ttu-id="fde28-106">설정 하려는 각 Microsoft SQL Server 연결에 대해 SQL DriverConnect를 한 번씩 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-106">Call SQL DriverConnect once for each Microsoft SQL Server connection you want to establish.</span></span>  
  
3.  <span data-ttu-id="fde28-107">MS DTC OLE ITransactionDispenser::BeginTransaction 함수를 호출하여 MS DTC 트랜잭션을 시작하고 해당 트랜잭션을 나타내는 트랜잭션 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-107">Call the MS DTC OLE ITransactionDispenser::BeginTransaction function to begin an MS DTC transaction and obtain a Transaction object that represents the transaction.</span></span>  
  
4.  <span data-ttu-id="fde28-108">MS DTC 트랜잭션에 참여시킬 각 ODBC 연결에 대해 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)을 한 번 이상 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-108">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) one or more times for each ODBC connection you want to enlist in the MS DTC transaction.</span></span> <span data-ttu-id="fde28-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)의 두 번째 매개 변수는 SQL_ATTR_ENLIST_IN_DTC여야 하고 세 번째 매개 변수는 3단계에서 얻은 트랜잭션 개체여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) second parameter must be SQL_ATTR_ENLIST_IN_DTC and third parameter must be the Transaction object (obtained in Step 3).</span></span>  
  
5.  <span data-ttu-id="fde28-110">업데이트할 각 SQL Server에 대해 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)를 한 번씩 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-110">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) once for each SQL Server you want to update.</span></span>  
  
6.  <span data-ttu-id="fde28-111">MS DTC OLE ITransaction::Commit 함수를 호출하여 MS DTC 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-111">Call the MS DTC OLE ITransaction::Commit function to commit the MS DTC transaction.</span></span> <span data-ttu-id="fde28-112">트랜잭션 개체가 더 이상 유효하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-112">The Transaction object is no longer valid.</span></span>  
  
 <span data-ttu-id="fde28-113">일련의 MS DTC 트랜잭션을 수행하려면 3 - 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-113">To perform a series of MS DTC transactions, repeat Steps 3 through 6.</span></span>  
  
 <span data-ttu-id="fde28-114">트랜잭션 개체에 대한 참조를 해제하려면 MS DTC OLE ITransaction::Return 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-114">To release the reference to the Transaction object, call the MS DTC OLE ITransaction::Return function.</span></span>  
  
 <span data-ttu-id="fde28-115">MS DTC 트랜잭션에서 ODBC 연결을 사용한 다음 로컬 SQL Server 트랜잭션에서 같은 연결을 사용하려면 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)을 SQL_DTC_DONE과 함께 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-115">To use an ODBC connection with an MS DTC transaction, and then use the same connection with a local SQL Server transaction, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_DTC_DONE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fde28-116">앞의 4 - 5단계에서 제안한 대로 호출하는 대신 각 SQL Server에 대해 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 및 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)를 차례로 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fde28-116">You can also call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) and [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) in turn for each SQL Server instead of calling them as suggested earlier in Steps 4 and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde28-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fde28-117">See Also</span></span>  
 [<span data-ttu-id="fde28-118">ODBC&#41;&#40;트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="fde28-118">Performing Transactions &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
