---
title: 트랜잭션 수행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: f431191a-5762-4f0b-85bb-ac99aff29724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8abc09c9395225dd653a072fd6c25dadce0849b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741236"
---
# <a name="performing-transactions-odbc"></a><span data-ttu-id="f015a-102">트랜잭션 수행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="f015a-102">Performing Transactions (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="f015a-103">와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 ODBC API 트랜잭션 관리 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f015a-103">and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver support the ODBC API transaction management functions.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f015a-104">는 개별 서버에서의 로컬 트랜잭션을 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f015a-104">offers full support for local transactions on an individual server.</span></span> <span data-ttu-id="f015a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 트랜잭션을 관리하는 ODBC API 함수를 지원하는 데 이러한 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f015a-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses these features to support the ODBC API functions that manage transactions.</span></span>  
  
 <span data-ttu-id="f015a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 MS DTC(Microsoft Distributed Transaction Coordinator)를 사용하여 여러 서버에 걸친 분산 트랜잭션에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f015a-106">Through the use of the Microsoft Distributed Transaction Coordinator (MS DTC), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver can participate in distributed transactions spanning multiple servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f015a-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f015a-107">In This Section</span></span>  
  
-   [<span data-ttu-id="f015a-108">ODBC의 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="f015a-108">Transactions in ODBC</span></span>](../../relational-databases/native-client/odbc/performing-transactions-in-odbc.md)  
  
-   [<span data-ttu-id="f015a-109">분산 트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="f015a-109">Performing Distributed Transactions</span></span>](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
