---
title: 병합 복제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7feef9e4debc228d1685c664c072139d60b56c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638697"
---
# <a name="merge-replication"></a><span data-ttu-id="ced9c-102">병합 복제</span><span class="sxs-lookup"><span data-stu-id="ced9c-102">Merge Replication</span></span>
  <span data-ttu-id="ced9c-103">병합 복제는 트랜잭션 복제와 마찬가지로 일반적으로 게시 데이터베이스 개체 및 데이터의 스냅샷으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-103">Merge replication, like transactional replication, typically starts with a snapshot of the publication database objects and data.</span></span> <span data-ttu-id="ced9c-104">게시자 및 구독자에서 발생한 후속 데이터 변경 및 스키마 수정은 트리거로 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-104">Subsequent data changes and schema modifications made at the Publisher and Subscribers are tracked with triggers.</span></span> <span data-ttu-id="ced9c-105">구독자는 네트워크에 연결될 때 게시자와 동기화하여 마지막 동기화 이후 게시자와 구독자 간에 변경된 모든 행을 교환합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-105">The Subscriber synchronizes with the Publisher when connected to the network and exchanges all rows that have changed between the Publisher and Subscriber since the last time synchronization occurred.</span></span>

 <span data-ttu-id="ced9c-106">병합 복제는 일반적으로 서버-클라이언트 간 환경에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-106">Merge replication is typically used in server-to-client environments.</span></span> <span data-ttu-id="ced9c-107">병합 복제는 다음 상황에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-107">Merge replication is appropriate in any of the following situations:</span></span>

-   <span data-ttu-id="ced9c-108">여러 구독자가 다양한 시간에 동일한 데이터를 업데이트하고 그 변경 내용을 게시자 및 다른 구독자에 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-108">Multiple Subscribers might update the same data at various times and propagate those changes to the Publisher and to other Subscribers.</span></span>

-   <span data-ttu-id="ced9c-109">구독자는 데이터를 받아 오프라인 상태에서 변경하여 나중에 게시자 및 다른 구독자와 변경 내용을 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-109">Subscribers need to receive data, make changes offline, and later synchronize changes with the Publisher and other Subscribers.</span></span>

-   <span data-ttu-id="ced9c-110">각 구독자에 서로 다른 데이터 파티션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-110">Each Subscriber requires a different partition of data.</span></span>

-   <span data-ttu-id="ced9c-111">충돌이 발생할 수 있으며 충돌이 발생하면 충돌을 감지하여 해결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-111">Conflicts might occur and, when they do, you need the ability to detect and resolve them.</span></span>

-   <span data-ttu-id="ced9c-112">애플리케이션이 중간 데이터 상태가 아닌 순수한 데이터 변경 내용만 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-112">The application requires net data change rather than access to intermediate data states.</span></span> <span data-ttu-id="ced9c-113">예를 들어 구독자가 게시자와 동기화하기 전에 구독자에서 행이 5번 변경된 경우 게시자에서는 행이 한 번만 변경되어 최종 데이터 변경 내용(5번째 값)을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-113">For example, if a row changes five times at a Subscriber before it synchronizes with a Publisher, the row will change only once at the Publisher to reflect the net data change (that is, the fifth value).</span></span>

 <span data-ttu-id="ced9c-114">병합 복제를 사용하면 여러 사이트에서 자율적으로 작업한 후 나중에 하나의 균일한 결과로 업데이트를 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-114">Merge replication allows various sites to work autonomously and later merge updates into a single, uniform result.</span></span> <span data-ttu-id="ced9c-115">업데이트는 둘 이상의 노드에서 수행되므로 게시자 및 둘 이상의 구독자가 같은 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-115">Because updates are made at more than one node, the same data may have been updated by the Publisher and by more than one Subscriber.</span></span> <span data-ttu-id="ced9c-116">따라서 업데이트가 병합될 때 충돌이 발생할 수 있으며 병합 복제는 충돌을 처리하는 다양한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-116">Therefore, conflicts can occur when updates are merged and merge replication provides a number of ways to handle conflicts.</span></span>

 <span data-ttu-id="ced9c-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 스냅샷 에이전트와 병합 에이전트가 병합 복제를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-117">Merge replication is implemented by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Snapshot Agent and Merge Agent.</span></span> <span data-ttu-id="ced9c-118">게시가 필터링되지 않거나 정적 필터를 사용하면 스냅샷 에이전트는 단일 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-118">If the publication is unfiltered or uses static filters, the Snapshot Agent creates a single snapshot.</span></span> <span data-ttu-id="ced9c-119">게시에서 매개 변수가 있는 필터를 사용하면 스냅샷 에이전트는 각 데이터 파티션에 대한 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-119">If the publication uses parameterized filters, the Snapshot Agent creates a snapshot for each partition of data.</span></span> <span data-ttu-id="ced9c-120">병합 에이전트는 초기 스냅샷을 구독자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-120">The Merge Agent applies the initial snapshots to the Subscribers.</span></span> <span data-ttu-id="ced9c-121">또한 초기 스냅샷이 만들어진 후 게시자 또는 구독자에서 발생한 증분 데이터 변경 내용을 병합하고 사용자가 구성한 규칙에 따라 충돌을 감지하고 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-121">It also merges incremental data changes that occurred at the Publisher or Subscribers after the initial snapshot was created, and detects and resolves any conflicts according to rules you configure.</span></span>

 <span data-ttu-id="ced9c-122">변경 내용을 추적하기 위해 병합 복제와 지연 업데이트 구독이 있는 트랜잭션 복제는 게시된 모든 테이블에 있는 모든 행을 고유하게 식별할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-122">To track changes, merge replication (and transactional replication with queued updating subscriptions) must be able to uniquely identify every row in every published table.</span></span> <span data-ttu-id="ced9c-123">이 병합 복제를 위해서는 테이블에 이미 `rowguid` 속성이 설정된 `uniqueidentifier` 데이터 형식의 열(이 열이 사용되는 경우)이 포함되지 않은 한 모든 테이블에 `ROWGUIDCOL` 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-123">To accomplish this merge replication adds the column `rowguid` to every table, unless the table already has a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set (in which case this column is used).</span></span> <span data-ttu-id="ced9c-124">게시에서 테이블이 삭제되면 `rowguid` 열이 제거됩니다. 추적 작업에 기존 열이 사용되면 해당 열은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-124">If the table is dropped from the publication, the `rowguid` column is removed; if an existing column was used for tracking, the column is not removed.</span></span> <span data-ttu-id="ced9c-125">필터는 행 식별을 위해 복제에 사용된 `rowguidcol`을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-125">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="ced9c-126">`newid()` 함수가 `rowguid` 열에 대한 기본값으로 제공되지만 고객은 필요에 따라 각 행에 대한 GUID를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-126">The `newid()` function is provided as a default for the `rowguid` column, however customers can provide a guid for each row if needed.</span></span> <span data-ttu-id="ced9c-127">그러나 00000000-0000-0000-0000-000000000000 값은 제공하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ced9c-127">However, do not provide value 00000000-0000-0000-0000-000000000000.</span></span>

 <span data-ttu-id="ced9c-128">다음 다이어그램에서는 병합 복제에 사용되는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ced9c-128">The following diagram shows the components used in merge replication.</span></span>

 <span data-ttu-id="ced9c-129">![병합 복제 구성 요소 및 데이터 흐름](../media/merge.gif "병합 복제 구성 요소 및 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="ced9c-129">![Merge replication components and data flow](../media/merge.gif "Merge replication components and data flow")</span></span>


