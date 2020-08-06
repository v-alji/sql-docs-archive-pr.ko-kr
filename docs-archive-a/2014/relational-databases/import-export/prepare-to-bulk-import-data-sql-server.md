---
title: 대량 데이터 가져오기 준비(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03d45d9c79082b255e9b8b0e4804c50855a3ad7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741047"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a><span data-ttu-id="5438f-102">대량 데이터 가져오기 준비(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5438f-102">Prepare to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="5438f-103">**bcp** 명령, BULK INSERT 문 또는 OPENROWSET(BULK) 함수를 사용하여 데이터 파일의 데이터만 대량으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-103">You can use the **bcp** command, BULK INSERT statement, or OPENROWSET(BULK) function to bulk import data from a data file only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5438f-104">텍스트 파일이 아닌 개체의 데이터를 대량으로 가져오는 사용자 지정 애플리케이션을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-104">It is possible to write a custom application that bulk imports data from objects other than a text file.</span></span> <span data-ttu-id="5438f-105">메모리 버퍼에서 데이터를 대량으로 가져오려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client(ODBC) API(애플리케이션 프로그래밍 인터페이스) 또는 OLE DB **IRowsetFastLoad** 인터페이스에 bcp 확장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-105">To bulk import data from memory buffers, use either the bcp extensions to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) application programming interface (API) or the OLE DB **IRowsetFastLoad** interface.</span></span>  <span data-ttu-id="5438f-106">C# 데이터 테이블에서 데이터를 대량으로 가져오려면 ADO.NET 대량 복사 API인 **SqlBulkCopy**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-106">To bulk import data from a C# data table, use the ADO.NET bulk-copy API, **SqlBulkCopy**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5438f-107">원격 테이블로 데이터를 대량으로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-107">Bulk importing data into a remote table is not supported.</span></span>  
  
 <span data-ttu-id="5438f-108">데이터 파일에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 데이터를 대량 가져오는 경우 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-108">Use the following guidelines when you bulk import data from a data file to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="5438f-109">사용자 계정에 대해 필요한 권한 가져오기</span><span class="sxs-lookup"><span data-stu-id="5438f-109">Obtain required permissions for your user account.</span></span>  
  
     <span data-ttu-id="5438f-110">**bcp** 유틸리티, BULK INSERT 문 또는 INSERT ... SELECT \* FROM OPENROWSET(BULK...) 문을 사용하는 사용자 계정에는 테이블에 대해 필요한 권한(테이블 소유자가 할당)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-110">The user account in which you use the **bcp** utility, the BULK INSERT statement, or the INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement must have the required permissions on the table, which are assigned by the table owner.</span></span> <span data-ttu-id="5438f-111">각 방법에 필요한 사용 권한에 대한 자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)및 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-111">For more information about permissions that are required by each method, see [bcp Utility](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="5438f-112">대량 로그 복구 모델 사용</span><span class="sxs-lookup"><span data-stu-id="5438f-112">Use the bulk-logged recovery model.</span></span>  
  
     <span data-ttu-id="5438f-113">이 지침은 전체 복구 모델을 사용하는 데이터베이스에 대한 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-113">This guideline is for a database that uses the full recovery model.</span></span> <span data-ttu-id="5438f-114">대량 로그된 복구 모델은 인덱싱되지 않은 테이블( *힙*)로 대량 작업을 수행할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-114">The bulk-logged recovery model is useful when performing bulk operations into an unindexed table (a *heap*).</span></span> <span data-ttu-id="5438f-115">대량 로그 복구는 로그 행 삽입을 수행하지 않으므로 대량 로그 복구를 사용하면 트랜잭션 로그의 공간 부족 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-115">Using bulk-logged recovery helps prevent the transaction log from running out of space because bulk-logged recovery does not perform log row inserts.</span></span> <span data-ttu-id="5438f-116">대량 로그된 복구 모델에 대한 자세한 내용은 [복구 모델&#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-116">For more information about the bulk-logged recovery model, see [Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).</span></span>  
  
     <span data-ttu-id="5438f-117">대량 가져오기 작업을 수행하기 바로 전에 대량 로그 복구 모델을 사용하여 데이터베이스를 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-117">We recommend that you change the database to use the bulk-logged recovery model immediately before the bulk import operation.</span></span> <span data-ttu-id="5438f-118">변경한 직후에는 데이터베이스를 전체 복구 모델로 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-118">Immediately afterwards, you should reset the database to the full recovery model.</span></span> <span data-ttu-id="5438f-119">자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-119">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5438f-120">대량 가져오기 작업 동안의 로깅을 최소화하는 방법은 [대량 가져오기의 최소 로깅을 위한 선행 조건](prerequisites-for-minimal-logging-in-bulk-import.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-120">more information about how to minimize logging during bulk import operations, see [Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
-   <span data-ttu-id="5438f-121">데이터를 대량으로 가져온 후 백업</span><span class="sxs-lookup"><span data-stu-id="5438f-121">Back up after bulk importing data.</span></span>  
  
     <span data-ttu-id="5438f-122">단순 복구 모델을 사용하는 데이터베이스의 경우 대량 가져오기 작업이 완료된 후 전체 또는 차등 백업을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-122">For a database that uses the simple recovery model, we recommend that you take a full or differential backup after the bulk-import operation finishes.</span></span> <span data-ttu-id="5438f-123">자세한 내용은 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) 또는 [차등 데이터베이스 백업 만들기&#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-123">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) or [Create a Differential Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
     <span data-ttu-id="5438f-124">대량 로그 복구 모델 또는 전체 복구 모델의 경우에는 로그 백업으로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-124">For the bulk-logged recovery model or full recovery model, a log backup is enough.</span></span> <span data-ttu-id="5438f-125">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5438f-125">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5438f-126">대규모 대량 가져오기의 성능 향상을 위해 테이블 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="5438f-126">Drop table indexes to improve performance for large bulk imports.</span></span>  
  
     <span data-ttu-id="5438f-127">이 지침은 이미 테이블에 있는 데이터에 비해 많은 양의 데이터를 가져오는 경우에 대한 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-127">This guideline is for when you are importing a large amount of data compared to the amount of data that is already in the table.</span></span> <span data-ttu-id="5438f-128">이 경우 대량 가져오기 작업을 수행하기 전에 테이블의 인덱스를 삭제하면 성능이 매우 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-128">In this case, dropping the indexes from the table before you perform the bulk-import operation can significantly increase performance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5438f-129">이미 테이블에 있는 데이터에 비해 적은 양의 데이터를 로드하는 경우에는 인덱스를 삭제하면 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-129">If you are loading a small amount of data compared to the amount of data already in the table, dropping the indexes is counterproductive.</span></span> <span data-ttu-id="5438f-130">인덱스를 다시 작성하는 데 필요한 시간이 대량 가져오기 작업 동안 절약된 시간보다 길 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-130">The time required to rebuild the indexes might be longer than the time saved during the bulk-import operation.</span></span>  
  
-   <span data-ttu-id="5438f-131">데이터 파일의 숨겨진 문자 찾기 및 제거</span><span class="sxs-lookup"><span data-stu-id="5438f-131">Find and remove hidden characters in the data file.</span></span>  
  
     <span data-ttu-id="5438f-132">주로 데이터 파일의 끝 부분에 있는 숨겨진 문자는 다양한 유틸리티와 텍스트 편집기를 사용하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-132">Many utilities and text editors display hidden characters, which are usually at the end of the data file.</span></span> <span data-ttu-id="5438f-133">대량 가져오기 작업 동안 ASCII 데이터 파일에 있는 숨겨진 문자가 문제를 일으켜 "예기치 않은 Null 발견" 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-133">During a bulk-import operation, hidden characters in an ASCII data file can cause problems that cause an error of "unexpected null found".</span></span> <span data-ttu-id="5438f-134">이 경우 숨겨진 문자를 모두 찾아서 제거하면 이 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="5438f-134">Finding and removing all the hidden characters should help prevent this problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5438f-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5438f-135">See Also</span></span>  
 <span data-ttu-id="5438f-136">[bcp 유틸리티를 사용하여 대량 데이터 가져오기 및 내보내기&#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5438f-136">[Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span></span>  
 <span data-ttu-id="5438f-137">[BULK INSERT 또는 OPENROWSET&#40;BULK...&#41;를 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5438f-137">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="5438f-138">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5438f-138">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="5438f-139">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5438f-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="5438f-140">[대량 가져오기 또는 대량 내보내기를 위한 데이터 형식&#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5438f-140">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="5438f-141">OPENROWSET&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5438f-141">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
