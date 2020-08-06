---
title: 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
ms.openlocfilehash: 1067820e80f9c7a4e1af2c8a14c85bc9dbfdd6aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653819"
---
# <a name="transactions"></a><span data-ttu-id="0d0c4-102">의</span><span class="sxs-lookup"><span data-stu-id="0d0c4-102">Transactions</span></span>
  <span data-ttu-id="0d0c4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 로컬 트랜잭션 지원을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements local transaction support.</span></span> <span data-ttu-id="0d0c4-104">소비자는 MS DTC(Microsoft Distributed Transaction Coordinator)를 사용하여 분산 또는 통합 트랜잭션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-104">The consumer can use distributed or coordinated transactions by using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="0d0c4-105">여러 세션에 걸친 트랜잭션 제어를 요구 하는 소비자의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 MS DTC에서 시작 및 유지 관리 되는 트랜잭션을 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-105">For consumers requiring transaction control that spans multiple sessions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can join transactions initiated and maintained by MS DTC.</span></span>  
  
 <span data-ttu-id="0d0c4-106">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 자동 커밋 트랜잭션 모드를 사용 합니다. 여기서 소비자 세션의 각 불연속 동작은 인스턴스에 대해 전체 트랜잭션을 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-106">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses an autocommit transaction mode, where each discrete action on a consumer session comprises a complete transaction against an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d0c4-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 자동 커밋 모드는 로컬 이며 자동 커밋 트랜잭션은 단일 세션 이상으로 확장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode is local, and autocommit transactions never span more than a single session.</span></span>  
  
 <span data-ttu-id="0d0c4-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자가 인스턴스에 대 한 단일 연결에서 명시적 및 암시적으로 트랜잭션을 사용할 수 있도록 **ITransactionLocal** 인터페이스를 노출 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0d0c4-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITransactionLocal** interface, allowing the consumer to use explicitly and implicitly start transactions on a single connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d0c4-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 중첩 된 로컬 트랜잭션을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c4-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support nested local transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d0c4-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0d0c4-110">In This Section</span></span>  
  
-   [<span data-ttu-id="0d0c4-111">로컬 트랜잭션 지원</span><span class="sxs-lookup"><span data-stu-id="0d0c4-111">Supporting Local Transactions</span></span>](supporting-local-transactions.md)  
  
-   [<span data-ttu-id="0d0c4-112">분산 트랜잭션 지원</span><span class="sxs-lookup"><span data-stu-id="0d0c4-112">Supporting Distributed Transactions</span></span>](supporting-distributed-transactions.md)  
  
-   [<span data-ttu-id="0d0c4-113">격리 수준&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0d0c4-113">Isolation Levels &#40;OLE DB&#41;</span></span>](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="0d0c4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d0c4-114">See Also</span></span>  
 [<span data-ttu-id="0d0c4-115">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0d0c4-115">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
