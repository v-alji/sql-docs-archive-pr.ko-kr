---
title: 인덱스 작업에 필요한 트랜잭션 로그 디스크 공간 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index disk space [SQL Server]
- space [SQL Server], indexes
- transaction logs [SQL Server], disk space
- disk space [SQL Server], transaction logs
- space [SQL Server], transaction logs
ms.assetid: 4f8a4922-4507-4072-be67-c690528d5c3b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c34c9ff7a9494496d6c60d5920184c0ce86131d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739915"
---
# <a name="transaction-log-disk-space-for-index-operations"></a><span data-ttu-id="dd4b2-102">인덱스 작업에 필요한 트랜잭션 로그 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="dd4b2-102">Transaction Log Disk Space for Index Operations</span></span>
  <span data-ttu-id="dd4b2-103">대량 인덱스 작업은 트랜잭션 로그를 빠르게 채울 수 있는 대량의 데이터 로드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-103">Large-scale index operations can generate large data loads that can cause the transaction log to fill quickly.</span></span> <span data-ttu-id="dd4b2-104">트랜잭션 로그는 인덱스 작업의 롤백을 보장하기 위해 인덱스 작업이 완료된 이후에만 잘릴 수 있지만 트랜잭션 로그 백업은 인덱스 작업 중에도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-104">To make sure that the index operation can be rolled back, the transaction log cannot be truncated until the index operation has completed; however, the log can be backed up during the index operation.</span></span> <span data-ttu-id="dd4b2-105">따라서 인덱스 작업 중에는 인덱스 작업 트랜잭션 및 모든 동시 사용자 트랜잭션을 모두 저장할 수 있는 충분한 트랜잭션 로그 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-105">Therefore, the transaction log must have sufficient room to store both the index operation transactions and any concurrent user transactions for the duration of the index operation.</span></span> <span data-ttu-id="dd4b2-106">이것은 오프라인 인덱스 작업과 온라인 인덱스 작업 모두에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-106">This is true for both offline and online index operations.</span></span> <span data-ttu-id="dd4b2-107">오프라인 인덱스 작업 중에는 기본 테이블에 액세스할 수 없기 때문에 사용자 트랜잭션이 거의 없고 로그가 빠르게 증가하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-107">Because the underlying tables cannot be accessed during an offline index operation, there may be few user transactions and the log may not grow as quickly.</span></span> <span data-ttu-id="dd4b2-108">온라인 인덱스 작업에서는 동시 사용자 작업이 제한되지 않습니다. 따라서 대량의 온라인 인덱스 작업과 대량의 동시 사용자 트랜잭션이 결합하는 경우에는 자를 수 없을 만큼 지속적으로 트랜잭션 로그가 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-108">Online index operations do not prevent concurrent user activity, therefore, large-scale online index operations combined with significant concurrent user transactions can cause continuous growth of the transaction log without an option to truncate the log.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="dd4b2-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="dd4b2-109">Recommendations</span></span>  
 <span data-ttu-id="dd4b2-110">대량 인덱스 작업을 실행할 때는 다음 권장 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-110">When you run large-scale index operations, consider the following recommendations:</span></span>  
  
1.  <span data-ttu-id="dd4b2-111">온라인으로 대량 인덱스 작업을 실행하기 전에 트랜잭션 로그를 백업하고 잘랐는지 확인하고 예상되는 인덱스 및 사용자 트랜잭션을 저장할 트랜잭션 로그 공간이 충분한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-111">Make sure the transaction log has been backed up and truncated before running large-scale index operations online, and that the log has sufficient space to store the projected index and user transactions.</span></span>  
  
2.  <span data-ttu-id="dd4b2-112">인덱스 작업을 위해 SORT_IN_TEMPDB 옵션을 ON으로 설정할 것을 고려해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-112">Consider setting the SORT_IN_TEMPDB option to ON for the index operation.</span></span> <span data-ttu-id="dd4b2-113">이렇게 하면 인덱스 트랜잭션이 동시 사용자 트랜잭션과 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-113">This separates the index transactions from the concurrent user transactions.</span></span> <span data-ttu-id="dd4b2-114">인덱스 트랜잭션은 **tempdb** 트랜잭션 로그에 저장되고 동시 사용자 트랜잭션은 사용자 데이터베이스의 트랜잭션 로그에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-114">The index transactions will be stored in the **tempdb** transaction log, and the concurrent user transactions will be stored in the transaction log of the user database.</span></span> <span data-ttu-id="dd4b2-115">따라서 필요한 경우 인덱스 작업 중에 사용자 데이터베이스의 트랜잭션 로그를 자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-115">This allows for the transaction log of the user database to be truncated during the index operation if it is required.</span></span> <span data-ttu-id="dd4b2-116">또한 **tempdb** 로그가 사용자 데이터베이스 로그와 동일한 디스크에 배치되지 않은 경우에는 두 로그가 동일한 디스크 공간을 차지하려고 경쟁하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-116">Additionally, if the **tempdb** log is not on the same disk as the user database log, the two logs are not competing for the same disk space.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd4b2-117">**tempdb** 데이터베이스 및 트랜잭션 로그에 인덱스 작업을 처리할 충분한 디스크 공간이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-117">Verify that the **tempdb** database and transaction log have sufficient disk space to handle the index operation.</span></span> <span data-ttu-id="dd4b2-118">**tempdb** 트랜잭션 로그는 인덱스 작업이 완료된 이후에만 자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-118">The **tempdb** transaction log cannot be truncated until the index operation is completed.</span></span>  
  
3.  <span data-ttu-id="dd4b2-119">인덱스 작업의 최소 로깅을 허용하는 데이터베이스 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-119">Use a database recovery model that allows for minimal logging of the index operation.</span></span> <span data-ttu-id="dd4b2-120">이렇게 하면 로그 크기가 줄어들고 로그 공간이 로그로 채워지지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-120">This may reduce the size of the log and prevent the log from filling the log space.</span></span>  
  
4.  <span data-ttu-id="dd4b2-121">온라인 인덱스 작업은 명시적 트랜잭션으로 실행하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-121">Do not run the online index operation in an explicit transaction.</span></span> <span data-ttu-id="dd4b2-122">로그는 명시적 트랜잭션이 종료된 이후에만 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="dd4b2-122">The log will not be truncated until the explicit transaction ends.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="dd4b2-123">관련 내용</span><span class="sxs-lookup"><span data-stu-id="dd4b2-123">Related Content</span></span>  
 [<span data-ttu-id="dd4b2-124">인덱스 DDL 작업의 디스크 공간 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dd4b2-124">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="dd4b2-125">인덱스 디스크 공간 예</span><span class="sxs-lookup"><span data-stu-id="dd4b2-125">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
  
