---
title: 병합 메타데이터 정리(복제 Transact-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736261"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a><span data-ttu-id="c5642-102">병합 메타데이터 정리(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="c5642-102">Clean Up Merge Metadata (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="c5642-103">병합 복제 메타데이터는 게시에 대한 보존 기간 설정에 따라 병합 에이전트에 의해 정기적으로 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-103">Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication.</span></span> <span data-ttu-id="c5642-104">정리 작업은 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)및 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 시스템 테이블의 게시자 및 구독자에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-104">This occurs at the Publisher and Subscriber in the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) system tables.</span></span> <span data-ttu-id="c5642-105">복제 저장 프로시저를 사용하여 이러한 테이블의 데이터를 프로그래밍 방식으로 정리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-105">You can also programmatically clean up the data in these tables using replication stored procedures.</span></span>  
  
### <a name="to-manually-clean-up-merge-metadata"></a><span data-ttu-id="c5642-106">병합 메타데이터를 수동으로 정리하려면</span><span class="sxs-lookup"><span data-stu-id="c5642-106">To manually clean up merge metadata</span></span>  
  
1.  <span data-ttu-id="c5642-107">게시 데이터베이스의 게시자에서 [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-107">At the Publisher on the publication database, execute [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).</span></span>  
  
2.  <span data-ttu-id="c5642-108">필드 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) **@num_genhistory_rows** **@num_contents_rows** 및 **@num_tombstone_rows** 출력 매개 변수에서 각각 반환 되는 MSmerge_genhistory, MSmerge_contents 및 MSmerge_tombstone 시스템 테이블에서 1 단계에서 제거 된 행 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-108">(Optional) Note the number of rows removed in step 1 from the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), and [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) system tables, returned respectively in the **@num_genhistory_rows**, **@num_contents_rows**, and **@num_tombstone_rows** output parameters.</span></span>  
  
3.  <span data-ttu-id="c5642-109">구독자에서 1~2단계를 반복하여 구독 데이터베이스의 메타데이터를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-109">Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5642-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5642-110">See Also</span></span>  
 [<span data-ttu-id="c5642-111">구독 만료 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="c5642-111">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
