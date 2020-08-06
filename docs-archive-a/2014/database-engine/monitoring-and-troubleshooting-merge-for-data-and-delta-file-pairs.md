---
title: 데이터 및 델타 파일 쌍에 대 한 병합 모니터링 및 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5dc57d08f3db1792a9359b3aa79aaceecd03a025
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660135"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a><span data-ttu-id="61e19-102">데이터 및 델타 파일 쌍에 대한 병합 모니터링 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="61e19-102">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>
  <span data-ttu-id="61e19-103">메모리 내 OLTP는 병합 정책을 사용하여 인접한 데이터 및 델타 파일 쌍을 자동으로 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-103">In-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically.</span></span> <span data-ttu-id="61e19-104">병합 작업은 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-104">You cannot disable merge activity.</span></span>  
  
 <span data-ttu-id="61e19-105">다음과 같이 데이터 및 델타 파일 쌍을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-105">You can monitor data and delta file pairs, as follows:</span></span>  
  
-   <span data-ttu-id="61e19-106">메모리 내 스토리지의 크기와 스토리지의 전체 크기를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-106">Compare the size of in-memory storage to overall size of storage.</span></span> <span data-ttu-id="61e19-107">스토리지가 지나치게 크면 병합이 트리거되지 않고 있을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-107">If the storage is dis-proportionately large, then it is likely that merge is not getting triggered.</span></span> <span data-ttu-id="61e19-108">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="61e19-108">For information</span></span>  
  
-   <span data-ttu-id="61e19-109">Dm_db_xtp_checkpoint_files를 사용 하 여 데이터 및 델타 파일에서 사용 되는 공간을 확인 하 [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) 사용 하 여 병합이 필요할 때 트리거되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-109">Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) to see if merge is not getting triggered when it should.</span></span>  
  
## <a name="performing-a-manual-merge"></a><span data-ttu-id="61e19-110">수동 병합 수행</span><span class="sxs-lookup"><span data-stu-id="61e19-110">Performing a Manual Merge</span></span>  
 <span data-ttu-id="61e19-111">[Sp_xtp_merge_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) 를 사용 하 여 수동 병합을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-111">You can use [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) to perform a manual merge.</span></span>  
  
 <span data-ttu-id="61e19-112">다음 쿼리를 사용하여 데이터 및 델타 파일에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-112">Use the following query to retrieve information about the data and delta files,</span></span>  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 <span data-ttu-id="61e19-113">병합되지 않은 세 개의 데이터 파일을 발견했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-113">Assume that you found three data files that have not been merged.</span></span> <span data-ttu-id="61e19-114">첫 번째 데이터 파일의 `lower_bound_tsn` 값과 마지막 데이터 파일의 `upper_bound_tsn` 값을 사용하여 다음 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-114">Using the `lower_bound_tsn` value of the first data file and the `upper_bound_tsn` of the last data file, you can issue the following command:</span></span>  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 <span data-ttu-id="61e19-115">3개의 데이터 및 델타 파일 쌍에 각각 15,836개의 행과 5,279개의 삭제된 행이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-115">Assume that the three data and delta file pairs each had 15,836 rows and 5,279 deleted rows.</span></span> <span data-ttu-id="61e19-116">병합 후 새로운 데이터 파일에는 31,872개의 행과 0개의 삭제된 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-116">After the merge, the new data file has 31,872 rows and 0 deleted rows.</span></span> <span data-ttu-id="61e19-117">새로운 데이터 파일의 크기는 처음에 할당된 크기인 128MB보다 훨씬 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-117">The size of the new data file can be much larger than the initially allocated size of 128MB.</span></span> <span data-ttu-id="61e19-118">이는 수동 병합이 병합 정책을 재정의하고 요청된 파일의 병합을 강제로 수행하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-118">This is because manual merge overrides the merge policy and forces the merge of the requested files.</span></span>  
  
 <span data-ttu-id="61e19-119">메모리 액세스에 [최적화 된 테이블이 있는 데이터베이스의 검사점 파일에 대 한 블로그 상태 전환은](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/) 개시에서 가비지 수집으로의 데이터 및 델타 파일 쌍의 상태 전환에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="61e19-119">The blog [State Transition of Checkpoint Files in Databases with Memory-Optimized Tables](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/) describes state transition of data and delta file pairs from inception to garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e19-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61e19-120">See Also</span></span>  
 [<span data-ttu-id="61e19-121">메모리 최적화 개체에 대한 스토리지 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="61e19-121">Creating and Managing Storage for Memory-Optimized Objects</span></span>](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
