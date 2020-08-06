---
title: FILESTREAM 애플리케이션에서 데이터베이스 작업과의 충돌 방지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32 and Transact-SQL Conflicts
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ac7e681766396d3a3b4412d91a968b4cdc653c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659496"
---
# <a name="avoid-conflicts-with-database-operations-in-filestream-applications"></a><span data-ttu-id="5ee6d-102">FILESTREAM 애플리케이션에서 데이터베이스 작업과의 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="5ee6d-102">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>
  <span data-ttu-id="5ee6d-103">FILESTREAM BLOB 데이터를 읽거나 쓰기 위해 SqlOpenFilestream()을 사용하여 Win32 파일 핸들을 여는 애플리케이션은 공통된 트랜잭션에서 관리되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과의 충돌 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-103">Applications that use SqlOpenFilestream() to open Win32 file handles for reading or writing FILESTREAM BLOB data can encounter conflict errors with [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are managed in a common transaction.</span></span> <span data-ttu-id="5ee6d-104">여기에는 실행 시간이 오래 걸리는 MARS 쿼리 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-104">This includes [!INCLUDE[tsql](../../includes/tsql-md.md)] or MARS queries that take a long time to finish execution.</span></span> <span data-ttu-id="5ee6d-105">이러한 유형의 충돌을 방지하도록 애플리케이션을 신중하게 디자인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-105">Applications must be carefully designed to help avoid these types of conflicts.</span></span>  
  
 <span data-ttu-id="5ee6d-106">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 또는 애플리케이션이 FILESTREAM BLOB를 열려고 하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 연결된 트랜잭션 컨텍스트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-106">When [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or applications try to open FILESTREAM BLOBs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] checks the associated transaction context.</span></span> <span data-ttu-id="5ee6d-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 열기 작업이 DDL 문, DML 문, 데이터 검색 또는 트랜잭션 관리 등을 사용하는지에 따라 요청을 허용하거나 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] allows or denies the request based on whether the open operation is working with DDL statements, DML statements, retrieving data, or managing transactions.</span></span> <span data-ttu-id="5ee6d-108">다음 표에서는 트랜잭션에서 열려 있는 파일 유형에 따라 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 허용 또는 거부할지를 결정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-108">The following table shows how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines whether a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will be allowed or denied based on the type of files that are open in the transaction.</span></span>  
  
|<span data-ttu-id="5ee6d-109">Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="5ee6d-109">Transact-SQL statements</span></span>|<span data-ttu-id="5ee6d-110">읽기 권한으로 열림</span><span class="sxs-lookup"><span data-stu-id="5ee6d-110">Opened for read</span></span>|<span data-ttu-id="5ee6d-111">쓰기 권한으로 열림</span><span class="sxs-lookup"><span data-stu-id="5ee6d-111">Opened for write</span></span>|  
|------------------------------|---------------------|----------------------|  
|<span data-ttu-id="5ee6d-112">CREATE TABLE, CREATE INDEX, DROP TABLE 및 ALTER TABLE과 같은 데이터베이스 메타데이터를 사용하는 DDL 문</span><span class="sxs-lookup"><span data-stu-id="5ee6d-112">DDL statements that work with database metadata, such as CREATE TABLE, CREATE INDEX, DROP TABLE, and ALTER TABLE.</span></span>|<span data-ttu-id="5ee6d-113">허용됨</span><span class="sxs-lookup"><span data-stu-id="5ee6d-113">Allowed</span></span>|<span data-ttu-id="5ee6d-114">차단되고 시간 초과 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-114">Are blocked and fail with a time-out.</span></span>|  
|<span data-ttu-id="5ee6d-115">UPDATE, DELETE 및 INSERT와 같이 데이터베이스에 저장된 데이터를 사용하는 DML 문</span><span class="sxs-lookup"><span data-stu-id="5ee6d-115">DML statements that work with the data that is stored in the database, such as UPDATE, DELETE, and INSERT.</span></span>|<span data-ttu-id="5ee6d-116">허용됨</span><span class="sxs-lookup"><span data-stu-id="5ee6d-116">Allowed</span></span>|<span data-ttu-id="5ee6d-117">거부됨</span><span class="sxs-lookup"><span data-stu-id="5ee6d-117">Denied</span></span>|  
|<span data-ttu-id="5ee6d-118">SELECT</span><span class="sxs-lookup"><span data-stu-id="5ee6d-118">SELECT</span></span>|<span data-ttu-id="5ee6d-119">허용됨</span><span class="sxs-lookup"><span data-stu-id="5ee6d-119">Allowed</span></span>|<span data-ttu-id="5ee6d-120">허용됨</span><span class="sxs-lookup"><span data-stu-id="5ee6d-120">Allowed</span></span>|  
|<span data-ttu-id="5ee6d-121">COMMIT TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="5ee6d-121">COMMIT TRANSACTION</span></span>|<span data-ttu-id="5ee6d-122">거부됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-122">Denied\*</span></span>|<span data-ttu-id="5ee6d-123">거부됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-123">Denied\*.</span></span>|  
|<span data-ttu-id="5ee6d-124">SAVE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="5ee6d-124">SAVE TRANSACTION</span></span>|<span data-ttu-id="5ee6d-125">거부됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-125">Denied\*</span></span>|<span data-ttu-id="5ee6d-126">거부됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-126">Denied\*</span></span>|  
|<span data-ttu-id="5ee6d-127">ROLLBACK</span><span class="sxs-lookup"><span data-stu-id="5ee6d-127">ROLLBACK</span></span>|<span data-ttu-id="5ee6d-128">허용됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-128">Allowed\*</span></span>|<span data-ttu-id="5ee6d-129">허용됨\*</span><span class="sxs-lookup"><span data-stu-id="5ee6d-129">Allowed\*</span></span>|  
  
 <span data-ttu-id="5ee6d-130">\* 트랜잭션이 취소되고 트랜잭션 컨텍스트의 열린 핸들이 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-130">\* The transaction is canceled, and open handles for the transaction context are invalidated.</span></span> <span data-ttu-id="5ee6d-131">애플리케이션은 열려 있는 모든 핸들을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-131">The application must close all open handles.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5ee6d-132">예</span><span class="sxs-lookup"><span data-stu-id="5ee6d-132">Examples</span></span>  
 <span data-ttu-id="5ee6d-133">다음 예에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 및 FILESTREAM Win32 액세스 권한이 충돌을 발생시키는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-133">The following examples show how [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and FILESTREAM Win32 access can cause conflicts.</span></span>  
  
### <a name="a-opening-a-filestream-blob-for-write-access"></a><span data-ttu-id="5ee6d-134">A.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-134">A.</span></span> <span data-ttu-id="5ee6d-135">쓰기 권한으로 FILESTREAM BLOB 열기</span><span class="sxs-lookup"><span data-stu-id="5ee6d-135">Opening a FILESTREAM BLOB for write access</span></span>  
 <span data-ttu-id="5ee6d-136">다음 예에서는 쓰기 전용 권한으로 파일을 열었을 때 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-136">The following example shows the effect of opening a file for write access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, ...);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, ...).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### <a name="b-opening-a-filestream-blob-for-read-access"></a><span data-ttu-id="5ee6d-137">B.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-137">B.</span></span> <span data-ttu-id="5ee6d-138">읽기 권한으로 FILESTREAM BLOB 열기</span><span class="sxs-lookup"><span data-stu-id="5ee6d-138">Opening a FILESTREAM BLOB for read access</span></span>  
 <span data-ttu-id="5ee6d-139">다음 예에서는 읽기 전용 권한으로 파일을 열었을 때 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-139">The following example shows the effect of opening a file for read access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="c-opening-and-closing-multiple-filestream-blob-files"></a><span data-ttu-id="5ee6d-140">C.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-140">C.</span></span> <span data-ttu-id="5ee6d-141">여러 FILESTREAM BLOB 파일 열기 및 닫기</span><span class="sxs-lookup"><span data-stu-id="5ee6d-141">Opening and closing multiple FILESTREAM BLOB files</span></span>  
 <span data-ttu-id="5ee6d-142">여러 파일이 열린 경우 가장 제한적인 규칙이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-142">If multiple files are open, the most restrictive rule is used.</span></span> <span data-ttu-id="5ee6d-143">다음 예에서는 두 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-143">The following example opens two files.</span></span> <span data-ttu-id="5ee6d-144">첫 번째 파일은 읽기 권한으로 열리고 두 번째 파일은 쓰기 권한으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-144">The first file is opened for read and the second for write.</span></span> <span data-ttu-id="5ee6d-145">두 번째 파일이 열리기 전까지 DML 문은 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-145">DML statements will be denied until the second file is opened.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="d-failing-to-close-a-cursor"></a><span data-ttu-id="5ee6d-146">D.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-146">D.</span></span> <span data-ttu-id="5ee6d-147">커서 닫기 실패</span><span class="sxs-lookup"><span data-stu-id="5ee6d-147">Failing to close a cursor</span></span>  
 <span data-ttu-id="5ee6d-148">다음 예에서는 닫히지 않은 문 커서가 `OpenSqlFilestream()` 에서 쓰기 권한으로 BLOB를 열지 못하게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee6d-148">The following example shows how a statement cursor that is not closed can prevent `OpenSqlFilestream()` from opening the BLOB for write access.</span></span>  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ee6d-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ee6d-149">See Also</span></span>  
 <span data-ttu-id="5ee6d-150">[OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="5ee6d-150">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="5ee6d-151">MARS&#40;Multiple Active Result Sets&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="5ee6d-151">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](../native-client/features/using-multiple-active-result-sets-mars.md)  
  
  
