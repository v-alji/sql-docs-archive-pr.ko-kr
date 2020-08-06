---
title: 로컬 트랜잭션 지원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653821"
---
# <a name="supporting-local-transactions"></a><span data-ttu-id="7529d-102">로컬 트랜잭션 지원</span><span class="sxs-lookup"><span data-stu-id="7529d-102">Supporting Local Transactions</span></span>
  <span data-ttu-id="7529d-103">세션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 로컬 트랜잭션에 대 한 트랜잭션 범위를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-103">A session delimits transaction scope for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider local transaction.</span></span> <span data-ttu-id="7529d-104">소비자의 방향으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 공급자가 연결 된 인스턴스에 요청을 전송 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 요청은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB 공급자에 대 한 작업 단위를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-104">When, at the direction of a consumer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a request to a connected instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the request constitutes a unit of work for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="7529d-105">로컬 트랜잭션은 항상 단일 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 세션에서 하나 이상의 작업 단위를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-105">Local transactions always wrap one or more units of work on a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session.</span></span>  
  
 <span data-ttu-id="7529d-106">기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 자동 커밋 모드를 사용 하는 경우 단일 작업 단위가 로컬 트랜잭션의 범위로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-106">Using the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode, a single unit of work is treated as the scope of a local transaction.</span></span> <span data-ttu-id="7529d-107">하나의 단위만 로컬 트랜잭션에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-107">Only one unit participates in the local transaction.</span></span> <span data-ttu-id="7529d-108">세션이 만들어질 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 세션에 대 한 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-108">When a session is created, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a transaction for the session.</span></span> <span data-ttu-id="7529d-109">작업 단위가 성공적으로 완료되면 해당 작업이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-109">Upon successful completion of a work unit, the work is committed.</span></span> <span data-ttu-id="7529d-110">실패하면 시작된 모든 작업이 롤백되며 소비자에게 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-110">On failure, any work begun is rolled back and the error is reported to the consumer.</span></span> <span data-ttu-id="7529d-111">두 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 모두 Native Client OLE DB 공급자는 세션에 대 한 새 로컬 트랜잭션을 시작 하 여 트랜잭션 내에서 모든 작업이 수행 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-111">In either case, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a new local transaction for the session so that all work is conducted within a transaction.</span></span>  
  
 <span data-ttu-id="7529d-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 소비자는 **ITransactionLocal** 인터페이스를 사용 하 여 로컬 트랜잭션 범위를 보다 정확 하 게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer can direct more precise control over local transaction scope by using the **ITransactionLocal** interface.</span></span> <span data-ttu-id="7529d-113">소비자 세션이 트랜잭션을 시작하면 트랜잭션 시작점과 결과 **Commit** 또는 **Abort** 메서드 호출 시점 사이에 있는 모든 세션 작업 단위는 원자 단위로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-113">When a consumer session initiates a transaction, all session work units between the transaction start point and the eventual **Commit** or **Abort** method calls are treated as an atomic unit.</span></span> <span data-ttu-id="7529d-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자에 게 전달 될 때 암시적으로 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implicitly begins a transaction when directed to do so by the consumer.</span></span> <span data-ttu-id="7529d-115">소비자가 보존을 요청하지 않으면 세션은 일반적으로 자동 커밋 모드인 부모 트랜잭션 수준 동작으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-115">If the consumer does not request retention, the session reverts to parent transaction-level behavior, most commonly autocommit mode.</span></span>  
  
 <span data-ttu-id="7529d-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 **같이 ITransactionLocal:: starttransaction** 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ITransactionLocal::StartTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="7529d-117">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7529d-117">Parameter</span></span>|<span data-ttu-id="7529d-118">Description</span><span class="sxs-lookup"><span data-stu-id="7529d-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7529d-119">*isoLevel*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-119">*isoLevel*[in]</span></span>|<span data-ttu-id="7529d-120">이 트랜잭션에 사용할 격리 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-120">The isolation level to be used with this transaction.</span></span> <span data-ttu-id="7529d-121">로컬 트랜잭션에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-121">In local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the following:</span></span><br /><br /> <span data-ttu-id="7529d-122">-ISOLATIONLEVEL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="7529d-122">-   ISOLATIONLEVEL_UNSPECIFIED</span></span><br /><span data-ttu-id="7529d-123">-ISOLATIONLEVEL_CHAOS</span><span class="sxs-lookup"><span data-stu-id="7529d-123">-   ISOLATIONLEVEL_CHAOS</span></span><br /><span data-ttu-id="7529d-124">-ISOLATIONLEVEL_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="7529d-124">-   ISOLATIONLEVEL_READUNCOMMITTED</span></span><br /><span data-ttu-id="7529d-125">-ISOLATIONLEVEL_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="7529d-125">-   ISOLATIONLEVEL_READCOMMITTED</span></span><br /><span data-ttu-id="7529d-126">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="7529d-126">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="7529d-127">-ISOLATIONLEVEL_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="7529d-127">-   ISOLATIONLEVEL_CURSORSTABILITY</span></span><br /><span data-ttu-id="7529d-128">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="7529d-128">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="7529d-129">-ISOLATIONLEVEL_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="7529d-129">-   ISOLATIONLEVEL_SERIALIZABLE</span></span><br /><span data-ttu-id="7529d-130">-ISOLATIONLEVEL_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="7529d-130">-   ISOLATIONLEVEL_ISOLATED</span></span><br /><span data-ttu-id="7529d-131">-ISOLATIONLEVEL_SNAPSHOT **Note:** 부터 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 대해 버전 관리가 사용 되는지 여부에 관계 없이 *isoLevel* 인수에 ISOLATIONLEVEL_SNAPSHOT를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-131">-   ISOLATIONLEVEL_SNAPSHOT **Note:**  Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT is valid for the *isoLevel* argument whether or not versioning is enabled for the database.</span></span> <span data-ttu-id="7529d-132">그러나 버전 관리가 설정되어 있지 않거나 데이터베이스가 읽기 전용이 아닌 상태에서 사용자가 문을 실행하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-132">However, an error will occur if the user attempts to execute a statement and versioning is not enabled and/or the database is not read-only.</span></span> <span data-ttu-id="7529d-133">또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 버전에 연결할 때 ISOLATIONLEVEL_SNAPSHOT을 *isoLevel*로 지정하면 XACT_E_ISOLATIONLEVEL 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-133">In addition, the error XACT_E_ISOLATIONLEVEL will occur if ISOLATIONLEVEL_SNAPSHOT is specified as the *isoLevel* when connected to a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>|  
|<span data-ttu-id="7529d-134">*isoFlags*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-134">*isoFlags*[in]</span></span>|<span data-ttu-id="7529d-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 0 이외의 값에 대해 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error for any value other than zero.</span></span>|  
|<span data-ttu-id="7529d-136">*pOtherOptions*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-136">*pOtherOptions*[in]</span></span>|<span data-ttu-id="7529d-137">NULL이 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 인터페이스에서 options 개체를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-137">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="7529d-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션 개체의 *ultimeout* 멤버가 0이 아니면 Native Client OLE DB 공급자가 XACT_E_NOTIMEOUT을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="7529d-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 *szdescription* 멤버의 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
|<span data-ttu-id="7529d-140">*pulTransactionLevel*[out]</span><span class="sxs-lookup"><span data-stu-id="7529d-140">*pulTransactionLevel*[out]</span></span>|<span data-ttu-id="7529d-141">NULL이 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 트랜잭션 중첩 수준을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-141">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns the nested level of the transaction.</span></span>|  
  
 <span data-ttu-id="7529d-142">로컬 트랜잭션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음과 같이 **ITransaction:: Abort** 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-142">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Abort** parameters as follows.</span></span>  
  
|<span data-ttu-id="7529d-143">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7529d-143">Parameter</span></span>|<span data-ttu-id="7529d-144">Description</span><span class="sxs-lookup"><span data-stu-id="7529d-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7529d-145">*pboidReason*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-145">*pboidReason*[in]</span></span>|<span data-ttu-id="7529d-146">설정된 경우 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-146">Ignored if set.</span></span> <span data-ttu-id="7529d-147">NULL이어도 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-147">Can safely be NULL.</span></span>|  
|<span data-ttu-id="7529d-148">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-148">*fRetaining*[in]</span></span>|<span data-ttu-id="7529d-149">TRUE인 경우 해당 세션을 위한 새 트랜잭션이 암시적으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-149">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="7529d-150">이 트랜잭션은 소비자가 커밋 또는 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-150">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="7529d-151">FALSE 이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 세션에 대해 자동 커밋 모드로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-151">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="7529d-152">*fAsync*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-152">*fAsync*[in]</span></span>|<span data-ttu-id="7529d-153">Native Client OLE DB 공급자는 비동기 중단을 지원 하지 않습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7529d-153">Asynchronous abort is not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="7529d-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 값이 FALSE가 아닌 경우 XACT_E_NOTSUPPORTED을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-154">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED if the value is not FALSE.</span></span>|  
  
 <span data-ttu-id="7529d-155">로컬 트랜잭션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다음과 같이 **ITransaction:: Commit** 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-155">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Commit** parameters as follows.</span></span>  
  
|<span data-ttu-id="7529d-156">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7529d-156">Parameter</span></span>|<span data-ttu-id="7529d-157">Description</span><span class="sxs-lookup"><span data-stu-id="7529d-157">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7529d-158">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-158">*fRetaining*[in]</span></span>|<span data-ttu-id="7529d-159">TRUE인 경우 해당 세션을 위한 새 트랜잭션이 암시적으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-159">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="7529d-160">이 트랜잭션은 소비자가 커밋 또는 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-160">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="7529d-161">FALSE 이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 세션에 대해 자동 커밋 모드로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-161">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="7529d-162">*grfTC*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-162">*grfTC*[in]</span></span>|<span data-ttu-id="7529d-163">Native Client OLE DB 공급자는 비동기 및 1 단계 반환을 지원 하지 않습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7529d-163">Asynchronous and phase one returns are not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="7529d-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 XACTTC_SYNC 이외의 값에 대해 XACT_E_NOTSUPPORTED을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED for any value other than XACTTC_SYNC.</span></span>|  
|<span data-ttu-id="7529d-165">*grfRM*[in]</span><span class="sxs-lookup"><span data-stu-id="7529d-165">*grfRM*[in]</span></span>|<span data-ttu-id="7529d-166">0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-166">Must be 0.</span></span>|  
  
 <span data-ttu-id="7529d-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]세션의 Native Client OLE DB 공급자 행 집합은 행 집합 속성 DBPROP_ABORTPRESERVE 및 DBPROP_COMMITPRESERVE의 값에 따라 로컬 커밋 또는 중단 작업에서 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-167">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are preserved on a local commit or abort operation based on the values of the rowset properties DBPROP_ABORTPRESERVE and DBPROP_COMMITPRESERVE.</span></span> <span data-ttu-id="7529d-168">기본적으로 이러한 속성은 모두 VARIANT_FALSE 이며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 세션의 모든 Native Client OLE DB 공급자 행 집합은 중단 또는 커밋 작업 후에 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-168">By default, these properties are both VARIANT_FALSE and all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are lost following an abort or commit operation.</span></span>  
  
 <span data-ttu-id="7529d-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자가 **ITransactionObject** 인터페이스를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-169">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not implement the **ITransactionObject** interface.</span></span> <span data-ttu-id="7529d-170">소비자가 인터페이스에 대한 참조를 얻으려고 하면 E_NOINTERFACE가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-170">A consumer attempt to retrieve a reference on the interface returns E_NOINTERFACE.</span></span>  
  
 <span data-ttu-id="7529d-171">이 예에서는 **ITransactionLocal**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7529d-171">This example uses **ITransactionLocal**.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
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
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="7529d-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7529d-172">See Also</span></span>  
 <span data-ttu-id="7529d-173">[트랜잭션](transactions.md) </span><span class="sxs-lookup"><span data-stu-id="7529d-173">[Transactions](transactions.md) </span></span>  
 [<span data-ttu-id="7529d-174">스냅숏 격리 작업</span><span class="sxs-lookup"><span data-stu-id="7529d-174">Working with Snapshot Isolation</span></span>](../native-client/features/working-with-snapshot-isolation.md)  
  
  
