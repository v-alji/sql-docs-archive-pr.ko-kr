---
title: 격리 수준(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: rothja
ms.author: jroth
ms.openlocfilehash: c7f6cbff4e68eaedd3e78a82cddd872ba5f8f19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652076"
---
# <a name="isolation-levels-ole-db"></a><span data-ttu-id="53168-102">격리 수준(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="53168-102">Isolation Levels (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="53168-103">클라이언트는 연결에 대한 트랜잭션 격리 수준을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53168-103">clients can control transaction-isolation levels for a connection.</span></span> <span data-ttu-id="53168-104">Native Client OLE DB 공급자 소비자는 트랜잭션 격리 수준을 제어 하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 다음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-104">To control transaction-isolation level, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses:</span></span>  
  
-   <span data-ttu-id="53168-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 기본 자동 커밋 모드의 DBPROPSET_SESSION 속성 DBPROP_SESS_AUTOCOMMITISOLEVELS입니다.</span><span class="sxs-lookup"><span data-stu-id="53168-105">DBPROPSET_SESSION property DBPROP_SESS_AUTOCOMMITISOLEVELS for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default autocommit mode.</span></span>  
  
     <span data-ttu-id="53168-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]수준에 대 한 Native Client OLE DB 공급자 기본값은 DBPROPVAL_TI_READCOMMITTED입니다.</span><span class="sxs-lookup"><span data-stu-id="53168-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default for the level is DBPROPVAL_TI_READCOMMITTED.</span></span>  
  
-   <span data-ttu-id="53168-107">로컬 수동 커밋 트랜잭션에 대한 **ITransactionLocal::StartTransaction** 메서드의 *isoLevel* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-107">The *isoLevel* parameter of the **ITransactionLocal::StartTransaction** method for local manual-commit transactions.</span></span>  
  
-   <span data-ttu-id="53168-108">MS DTC 통합 분산 트랜잭션에 대해 **ITransactionDispenser::BeginTransaction** 메서드의 *isoLevel* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-108">The *isoLevel* parameter of the **ITransactionDispenser::BeginTransaction** method for MS DTC-coordinated distributed transactions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="53168-109">를 사용하면 커밋되지 않은 읽기 격리 수준에서 읽기 전용으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53168-109">allows read-only access at the dirty read isolation level.</span></span> <span data-ttu-id="53168-110">이외의 다른 모든 수준은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체에 잠금을 적용하므로 동시성을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-110">All other levels restrict concurrency by applying locks to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="53168-111">클라이언트에 더 높은 동시성 수준이 필요한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 데이터 동시 액세스에 대해 더 높은 수준의 제한을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-111">As the client requires greater concurrency levels, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies greater restrictions on concurrent access to data.</span></span> <span data-ttu-id="53168-112">데이터에 대 한 동시 액세스의 최고 수준을 유지 하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 소비자는 특정 동시성 수준에 대 한 요청을 지능적으로 제어 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53168-112">To maintain the highest level of concurrent access to data, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer should intelligently control its requests for specific concurrency levels.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53168-113">스냅샷 격리 수준은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53168-113">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] introduced snapshot isolation level.</span></span> <span data-ttu-id="53168-114">자세한 내용은 [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53168-114">For more information, see [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53168-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53168-115">See Also</span></span>  
 [<span data-ttu-id="53168-116">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="53168-116">Transactions</span></span>](transactions.md)  
  
  
