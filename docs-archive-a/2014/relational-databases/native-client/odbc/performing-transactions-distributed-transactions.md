---
title: 분산 트랜잭션 수행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648352"
---
# <a name="performing-distributed-transactions"></a><span data-ttu-id="503aa-102">분산 트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="503aa-102">Performing Distributed Transactions</span></span>
  <span data-ttu-id="503aa-103">MS DTC(Microsoft Distributed Transaction Coordinator)를 사용하면 애플리케이션이 둘 이상의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 트랜잭션을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-103">The Microsoft Distributed Transaction Coordinator (MS DTC) allows applications to extend transactions across two or more instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="503aa-104">또한 애플리케이션이 Open Group DTP XA 표준을 준수하는 트랜잭션 관리자가 관리하는 트랜잭션에 참가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-104">It also allows applications to participate in transactions managed by transaction managers that comply with the Open Group DTP XA standard.</span></span>  
  
 <span data-ttu-id="503aa-105">일반적으로 모든 트랜잭션 관리 명령은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버를 통해 서버로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-105">Normally, all transaction management commands are sent through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to the server.</span></span> <span data-ttu-id="503aa-106">응용 프로그램은 자동 커밋 모드가 해제 된 상태에서 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-106">The application starts a transaction by calling [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) with the autocommit mode turned off.</span></span> <span data-ttu-id="503aa-107">그런 다음 응용 프로그램은 트랜잭션을 구성 하는 업데이트를 수행 하 고 SQL_COMMIT 또는 SQL_ROLLBACK 옵션을 사용 하 여 [Sqlendtran](../../native-client-odbc-api/sqlendtran.md) 을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-107">The application then performs the updates comprising the transaction and calls [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) with either the SQL_COMMIT or SQL_ROLLBACK option.</span></span>  
  
 <span data-ttu-id="503aa-108">그러나 MS DTC를 사용 하는 경우 MS DTC는 트랜잭션 관리자가 되며 응용 프로그램은 더 이상 **Sqlendtran**을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-108">When using MS DTC, however, MS DTC becomes the transaction manager and the application no longer uses **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="503aa-109">분산 트랜잭션에 등록된 경우 두 번째 분산 트랜잭션에 등록하고 원분 분산 트랜잭션의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버 결함을 새 트랜잭션에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="503aa-109">When enlisted in a distributed transaction, and then enlist in a second distributed transaction, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver defects from the original distributed transaction and enlists in the new transaction.</span></span> <span data-ttu-id="503aa-110">자세한 내용은 [DTC 프로그래머 참조](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="503aa-110">For more information, see [DTC Programmer's Reference](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503aa-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="503aa-111">See Also</span></span>  
 [<span data-ttu-id="503aa-112">ODBC&#41;&#40;트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="503aa-112">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
