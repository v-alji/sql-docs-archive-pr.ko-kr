---
title: 스냅샷으로 구독 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b776e71e9d1197bc174169aee8ccf692884308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646879"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a><span data-ttu-id="a287b-102">스냅샷으로 구독 초기화</span><span class="sxs-lookup"><span data-stu-id="a287b-102">Initialize a Subscription with a Snapshot</span></span>
  <span data-ttu-id="a287b-103">게시가 생성된 후 일반적으로 초기 스냅샷이 생성되어 스냅샷 폴더로 복사됩니다. 이 작업은 새 게시 마법사에서 만든 병합 게시에 대해 기본적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-103">After a publication has been created, an initial snapshot is typically created and copied to the snapshot folder (this occurs by default for merge publications created with the New Publication Wizard).</span></span> <span data-ttu-id="a287b-104">스냅샷은 그런 다음 구독의 초기 동기화 중 배포 에이전트(트랜잭션 및 스냅샷 게시의 경우) 또는 병합 에이전트(병합 게시의 경우)에 의해 구독자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-104">It is then applied to the Subscriber by the Distribution Agent (for transactional and snapshot publications) or the Merge Agent (for merge publications) during the initial synchronization of the subscription.</span></span> <span data-ttu-id="a287b-105">스냅샷 프로세스는 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-105">The snapshot process depends on the type of publication:</span></span>  
  
-   <span data-ttu-id="a287b-106">스냅샷이 스냅샷 게시, 트랜잭션 게시 또는 매개 변수가 있는 필터를 사용하지 않는 병합 게시용인 경우 스냅샷에는 제약 조건, 확장 속성, 인덱스, 트리거 및 복제에 필요한 시스템 테이블뿐만 아니라 스키마 및 데이터가 bcp(대량 복사 프로그램) 파일로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-106">If the snapshot is for a snapshot publication, a transactional publication, or a merge publication that doesn't use parameterized filters, the snapshot contains the schema and data in bulk copy program (bcp) files, as well as constraints, extended properties, indexes, triggers, and the system tables necessary for replication.</span></span> <span data-ttu-id="a287b-107">스냅샷을 만들고 적용하는 방법은 [스냅샷 만들기 및 적용](create-and-apply-the-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-107">For more information about creating and applying the snapshot, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
-   <span data-ttu-id="a287b-108">스냅샷이 매개 변수가 있는 필터를 사용하는 병합 게시용인 경우 2단계 프로세스를 통해 스냅샷이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-108">If the snapshot is for a merge publication that uses parameterized filters, the snapshot is created using a two-part process.</span></span> <span data-ttu-id="a287b-109">먼저 게시된 개체의 데이터를 제외하고 복제 스크립트와 스키마를 포함하는 스키마 스냅샷이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-109">First a schema snapshot is created that contains the replication scripts and the schema of the published objects, but not the data.</span></span> <span data-ttu-id="a287b-110">그런 후 스키마 스냅샷에서 복사된 스크립트 및 스키마를 포함하는 스냅샷과 구독의 파티션에 속해 있는 데이터를 사용하여 구독이 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-110">Each subscription is then initialized with a snapshot that includes the scripts and schema copied from the schema snapshot and the data that belongs to the subscription's partition.</span></span> <span data-ttu-id="a287b-111">자세한 내용은 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-111">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="a287b-112">스냅샷을 구성하는 파일은 복제 유형과 게시의 아티클에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-112">The snapshot consists of different files depending on the type of replication and the articles in your publication.</span></span> <span data-ttu-id="a287b-113">이러한 파일은 배포자를 구성할 때 지정한 기본 스냅샷 폴더나 게시를 만들 때 지정한 대체 스냅샷 폴더에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-113">These files are copied to the default snapshot folder specified when the Distributor was configured or the alternate snapshot folder specified when the publication was created.</span></span>  
  
|<span data-ttu-id="a287b-114">복제 유형</span><span class="sxs-lookup"><span data-stu-id="a287b-114">Type of Replication</span></span>|<span data-ttu-id="a287b-115">일반 스냅샷 파일</span><span class="sxs-lookup"><span data-stu-id="a287b-115">Common Snapshot Files</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="a287b-116">스냅샷 복제 또는 트랜잭션 복제</span><span class="sxs-lookup"><span data-stu-id="a287b-116">Snapshot Replication or Transactional Replication</span></span>|<span data-ttu-id="a287b-117">스키마(.sch), 데이터(.bcp), 제약 조건 및 인덱스(.dri), 제약 조건(.idx), 트리거(.trg)(구독자 업데이트 전용), 압축 스냅샷 파일(.cab)</span><span class="sxs-lookup"><span data-stu-id="a287b-117">schema (.sch); data (.bcp); constraints and indexes (.dri); constraints (.idx); triggers (.trg):for updating Subscribers only; compressed snapshot files (.cab).</span></span>|  
|<span data-ttu-id="a287b-118">병합 복제</span><span class="sxs-lookup"><span data-stu-id="a287b-118">Merge Replication</span></span>|<span data-ttu-id="a287b-119">스키마(.sch), 데이터(.bcp), 제약 조건 및 인덱스(.dri), 트리거(.trg), 시스템 테이블 데이터(.sys), 충돌 테이블(.cft), 압축 스냅샷 파일(.cab)</span><span class="sxs-lookup"><span data-stu-id="a287b-119">schema (.sch); data (.bcp); constraints and indexes (.dri); triggers (.trg); system table data (.sys); conflict tables (.cft); compressed snapshot files (.cab).</span></span>|  
  
 <span data-ttu-id="a287b-120">특정 시점에서 중단된 스냅샷 전송은 자동으로 재개되며 전송이 이미 완료된 파일은 다시 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-120">If the snapshot transfer is interrupted at any point, it will automatically resume and will not resend any files that have already been completely transferred.</span></span> <span data-ttu-id="a287b-121">스냅샷 에이전트의 배달 단위는 각 게시 아티클에 대한 bcp 파일이므로 부분적으로 배달된 파일은 완전히 다시 배달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-121">The unit of delivery for the Snapshot Agent is the bcp file for each publication article, so files that are partially delivered must be completely redelivered.</span></span> <span data-ttu-id="a287b-122">그러나 스냅샷 배달을 재개하면 전송되는 데이터 양이 크게 줄어들 수 있으므로 연결이 불안한 경우에도 스냅샷이 늦지 않게 배달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-122">However, resuming the snapshot can significantly reduce the amount of data transmitted and ensure timely snapshot delivery even if the connection is unreliable.</span></span>  
  
## <a name="snapshot-options"></a><span data-ttu-id="a287b-123">Snapshot Options</span><span class="sxs-lookup"><span data-stu-id="a287b-123">Snapshot Options</span></span>  
 <span data-ttu-id="a287b-124">스냅샷으로 구독을 초기화할 때 사용할 수 있는 옵션에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-124">There are a number of options available when initializing a subscription with a snapshot.</span></span> <span data-ttu-id="a287b-125">다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-125">You can:</span></span>  
  
-   <span data-ttu-id="a287b-126">기본 스냅샷 폴더 위치 대신 또는 기본 스냅샷 폴더 위치에 추가로 대체 스냅샷 폴더 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-126">Specify an alternate snapshot folder location instead of, or in addition, to the default snapshot folder location.</span></span> <span data-ttu-id="a287b-127">자세한 내용은 [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-127">For more information, see [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).</span></span>  
  
-   <span data-ttu-id="a287b-128">이동식 미디어에 스토리지하거나 느린 네트워크를 통해 전송하기 위해 스냅샷을 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-128">Compress snapshots for storage on removable media or for transfer over a slow network.</span></span> <span data-ttu-id="a287b-129">자세한 내용은 [Compressed Snapshots](compressed-snapshots.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-129">For more information, see [Compressed Snapshots](compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="a287b-130">스냅샷 적용 전후에 Transact-SQL 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-130">Execute Transact-SQL scripts before or after the snapshot is applied.</span></span> <span data-ttu-id="a287b-131">자세한 내용은 [스냅샷 적용 전후에 스크립트 실행](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-131">For more information, see [Execute Scripts Before and After the Snapshot Is Applied](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).</span></span>  
  
-   <span data-ttu-id="a287b-132">FTP(파일 전송 프로토콜)를 사용하여 스냅샷 파일을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="a287b-132">Transfer snapshot files using File Transfer Protocol (FTP).</span></span> <span data-ttu-id="a287b-133">자세한 내용은 [FTP를 통해 스냅샷 전송](transfer-snapshots-through-ftp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a287b-133">For more information, see [Transfer Snapshots Through FTP](transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a287b-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a287b-134">See Also</span></span>  
 <span data-ttu-id="a287b-135">[구독 초기화](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a287b-135">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="a287b-136">스냅샷 폴더 보안 설정</span><span class="sxs-lookup"><span data-stu-id="a287b-136">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
