---
title: 커서 트랜잭션 격리 수준 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: rothja
ms.author: jroth
ms.openlocfilehash: 30f3dc8a9136a7cbe1d5897cb0bcc9fff8c35ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738362"
---
# <a name="cursor-transaction-isolation-level"></a><span data-ttu-id="693c0-102">커서 트랜잭션 격리 수준</span><span class="sxs-lookup"><span data-stu-id="693c0-102">Cursor Transaction Isolation Level</span></span>
  <span data-ttu-id="693c0-103">커서의 전체 잠금 동작은 클라이언트에서 설정하는 동시성 특성과 트랜잭션 격리 수준 사이의 상호 작용을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="693c0-103">The complete locking behavior of cursors is based on an interaction between concurrency attributes and the transaction isolation level set by the client.</span></span> <span data-ttu-id="693c0-104">ODBC 클라이언트는 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION 또는 SQL_COPT_SS_TXN_ISOLATION 특성을 사용 하 여 트랜잭션 격리 수준을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="693c0-104">ODBC clients set the transaction isolation level using the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION or SQL_COPT_SS_TXN_ISOLATION attributes.</span></span> <span data-ttu-id="693c0-105">특정 커서 환경의 잠금 동작은 동시성 및 트랜잭션 격리 수준 옵션의 잠금 동작을 통해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="693c0-105">The locking behavior of a specific cursor environment is determined by combining the locking behaviors of the concurrency and transaction isolation level options.</span></span>  
  
 <span data-ttu-id="693c0-106">Native Client ODBC 드라이버에서 지원 되는 커서 트랜잭션 격리 수준은 다음과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 같습니다.</span><span class="sxs-lookup"><span data-stu-id="693c0-106">The following cursor transaction isolation levels are supported by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
-   <span data-ttu-id="693c0-107">커밋된 읽기(SQL_TXN_READ_COMMITTED)</span><span class="sxs-lookup"><span data-stu-id="693c0-107">Read committed (SQL_TXN_READ_COMMITTED)</span></span>  
  
-   <span data-ttu-id="693c0-108">커밋되지 않은 읽기(SQL_TXN_READ_UNCOMMITTED)</span><span class="sxs-lookup"><span data-stu-id="693c0-108">Read uncommitted (SQL_TXN_READ_UNCOMMITTED)</span></span>  
  
-   <span data-ttu-id="693c0-109">반복 읽기(SQL_TXN_REPEATABLE_READ)</span><span class="sxs-lookup"><span data-stu-id="693c0-109">Repeatable read (SQL_TXN_REPEATABLE_READ)</span></span>  
  
-   <span data-ttu-id="693c0-110">직렬화 가능(SQL_TXN_SERIALIZABLE)</span><span class="sxs-lookup"><span data-stu-id="693c0-110">Serializable (SQL_TXN_SERIALIZABLE)</span></span>  
  
-   <span data-ttu-id="693c0-111">스냅샷(SQL_TXN_SS_SNAPSHOT)</span><span class="sxs-lookup"><span data-stu-id="693c0-111">Snapshot (SQL_TXN_SS_SNAPSHOT)</span></span>  
  
 <span data-ttu-id="693c0-112">ODBC API는 추가 트랜잭션 격리 수준을 지정 하지만이는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="693c0-112">Note that the ODBC API specifies additional transaction isolation levels, but these are not supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693c0-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="693c0-113">See Also</span></span>  
 [<span data-ttu-id="693c0-114">커서 속성</span><span class="sxs-lookup"><span data-stu-id="693c0-114">Cursor Properties</span></span>](cursor-properties.md)  
  
  
