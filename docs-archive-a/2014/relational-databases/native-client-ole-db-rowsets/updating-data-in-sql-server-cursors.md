---
title: SQL Server 커서의 데이터 업데이트 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: rothja
ms.author: jroth
ms.openlocfilehash: 42e6221a85c30e3adb97df3a11c9cbdc49216b4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648368"
---
# <a name="updating-data-in-sql-server-cursors"></a><span data-ttu-id="03a79-102">SQL Server 커서의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="03a79-102">Updating Data in SQL Server Cursors</span></span>
  <span data-ttu-id="03a79-103">커서를 통해 데이터를 가져오고 업데이트할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 공급자 소비자 응용 프로그램은 다른 클라이언트 응용 프로그램에 적용 되는 것과 동일한 고려 사항과 제약 조건에 의해 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-103">When fetching and updating data through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer application is bound by the same considerations and constraints that apply to any other client application.</span></span>  
  
 <span data-ttu-id="03a79-104">동시 데이터 액세스 제어에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서의 행만 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-104">Only rows in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors participate in concurrent data-access control.</span></span> <span data-ttu-id="03a79-105">소비자가 수정이 가능한 행 집합을 요청하면 DBPROP_LOCKMODE에서 동시성 제어를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-105">When the consumer requests a modifiable rowset, the concurrency control is controlled by DBPROP_LOCKMODE.</span></span> <span data-ttu-id="03a79-106">소비자는 행 집합을 열기 전에 DBPROP_LOCKMODE 속성을 설정하여 동시 액세스 제어의 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-106">To modify the level of concurrent access control, the consumer sets the DBPROP_LOCKMODE property before opening the rowset.</span></span>  
  
 <span data-ttu-id="03a79-107">트랜잭션이 오랫동안 열려 있을 수 있도록 설계된 클라이언트 애플리케이션의 경우 트랜잭션 격리 수준 때문에 행 위치 지정에 상당한 시간 지연이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-107">Transaction isolation levels can cause significant lags in row positioning if client application design lets transactions remain open for long periods of time.</span></span> <span data-ttu-id="03a79-108">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 DBPROPVAL_TI_READCOMMITTED에서 지정 된 커밋된 읽기 격리 수준을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-108">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the read-committed isolation level specified by DBPROPVAL_TI_READCOMMITTED.</span></span> <span data-ttu-id="03a79-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 행 집합 동시성이 읽기 전용일 때 더티 읽기 격리를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports dirty read isolation when the rowset concurrency is read-only.</span></span> <span data-ttu-id="03a79-110">따라서 소비자는 수정이 가능한 행 집합에 더 높은 수준의 격리를 요청할 수 있지만 더 낮은 수준은 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-110">Therefore, the consumer can request a higher level of isolation in a modifiable rowset but cannot request any lower level successfully.</span></span>  
  
## <a name="immediate-and-delayed-update-modes"></a><span data-ttu-id="03a79-111">즉시 및 지연 업데이트 모드</span><span class="sxs-lookup"><span data-stu-id="03a79-111">Immediate and Delayed Update Modes</span></span>  
 <span data-ttu-id="03a79-112">즉시 업데이트 모드에서는 **IRowsetChange::SetData**를 호출할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 왕복이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-112">In immediate update mode, each call to **IRowsetChange::SetData** causes a round trip to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03a79-113">소비자가 단일 행을 여러 번 변경한 경우 **SetData**를 한 번 호출하여 모든 변경 내용을 전송하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-113">If the consumer makes multiple changes to a single row, it is more efficient to submit all changes with a single **SetData** call.</span></span>  
  
 <span data-ttu-id="03a79-114">지연 업데이트 모드에서는 **IRowsetUpdate::Update**의 *cRows* 및 *rghRows* 매개 변수에 지정된 각 행에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로의 왕복이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-114">In delayed update mode, a roundtrip is made to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for each row indicated in the *cRows* and *rghRows* parameters of **IRowsetUpdate::Update**.</span></span>  
  
 <span data-ttu-id="03a79-115">두 모드 모두 왕복은 행 집합에 대해 열려 있는 트랜잭션 개체가 없는 경우 고유한 트랜잭션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-115">In either mode, a roundtrip represents a distinct transaction when no transaction object is open for the rowset.</span></span>  
  
 <span data-ttu-id="03a79-116">**IRowsetUpdate:: Update**를 사용 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 표시 된 각 행을 처리 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-116">When you are using **IRowsetUpdate::Update**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to process each indicated row.</span></span> <span data-ttu-id="03a79-117">모든 행에 대해 잘못 된 데이터, 길이 또는 상태 값 때문에 오류가 발생 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 처리를 중지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-117">An error occurring because of invalid data, length, or status values for any row does not stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processing.</span></span> <span data-ttu-id="03a79-118">업데이트에 참여하는 행은 모두 수정되거나 전혀 수정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-118">All or none of the other rows participating in the update may be modified.</span></span> <span data-ttu-id="03a79-119">Native Client OLE DB 공급자가 DB_S_ERRORSOCCURRED 반환 하는 경우 소비자는 반환 된 *prgRowStatus* 배열을 검사 하 여 특정 행에 대 한 실패를 확인 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="03a79-119">The consumer must examine the returned *prgRowStatus* array to determine failure for any specific row when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_S_ERRORSOCCURRED.</span></span>  
  
 <span data-ttu-id="03a79-120">소비자는 행이 특정한 순서로 처리된다고 가정해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-120">A consumer should not assume that rows are processed in any specific order.</span></span> <span data-ttu-id="03a79-121">소비자가 두 개 이상의 행에서 수정된 데이터를 순서대로 처리해야 하는 경우에는 애플리케이션 논리에서 이러한 순서를 설정하고 트랜잭션을 열어 여기에 프로세스를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03a79-121">If a consumer requires ordered processing of data modification over more than a single row, the consumer should establish that order in the application logic and open a transaction to enclose the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a79-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03a79-122">See Also</span></span>  
 [<span data-ttu-id="03a79-123">행 집합의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="03a79-123">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
