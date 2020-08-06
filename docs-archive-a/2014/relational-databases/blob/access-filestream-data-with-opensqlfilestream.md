---
title: OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
api_name:
- OpenSqlFilestream
api_location:
- sqlncli11.dll
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1a1416c0104e07c7bd228a723192ecb35bbe9216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734167"
---
# <a name="access-filestream-data-with-opensqlfilestream"></a><span data-ttu-id="c70cb-102">OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="c70cb-102">Access FILESTREAM Data with OpenSqlFilestream</span></span>
  <span data-ttu-id="c70cb-103">OpenSqlFilestream API는 파일 시스템에 저장 된 FILESTREAM BLOB (binary large object)에 대 한 Win32 호환 파일 핸들을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-103">The OpenSqlFilestream API obtains a Win32 compatible file handle for a FILESTREAM binary large object (BLOB) that is stored in the file system.</span></span> <span data-ttu-id="c70cb-104">이 핸들은 다음 Win32 API 중 하나로 전달될 수 있습니다. [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426) 또는 [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427).</span><span class="sxs-lookup"><span data-stu-id="c70cb-104">The handle can be passed to any of the following Win32 APIs: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427).</span></span> <span data-ttu-id="c70cb-105">이 핸들을 다른 Win32 API에 전달하면 ERROR_ACCESS_DENIED 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-105">If you pass this handle to any other Win32 API, the error ERROR_ACCESS_DENIED is returned.</span></span> <span data-ttu-id="c70cb-106">핸들은 트랜잭션이 커밋 또는 롤백되기 전에 Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API에 전달하는 방식으로 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-106">The handle must be closed by passing it to the Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API before the transaction is committed or rolled back.</span></span> <span data-ttu-id="c70cb-107">핸들을 닫지 못하면 서버 쪽 리소스 노출이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-107">Failing to close the handle will cause server-side resource leaks.</span></span>  
  
 <span data-ttu-id="c70cb-108">모든 FILESTREAM 데이터 컨테이너 액세스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 트랜잭션에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-108">All FILESTREAM data container access must be performed in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="c70cb-109">문도 동일한 트랜잭션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-109">statements can also be executed in the same transaction.</span></span> <span data-ttu-id="c70cb-110">이를 통해 SQL 데이터와 FILESTREAM BLOB 데이터 간의 일관성을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-110">This maintains consistency between the SQL data and FILESTREAM BLOB data.</span></span>  
  
 <span data-ttu-id="c70cb-111">Win32를 사용하여 FILESTREAM BLOB에 액세스하려면 [Windows 인증](../security/choose-an-authentication-mode.md) 을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-111">To access the FILESTREAM BLOB by using Win32, [Windows Authorization](../security/choose-an-authentication-mode.md) must be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c70cb-112">파일이 쓰기 액세스 권한으로 열린 경우 트랜잭션은 FILESTREAM 에이전트의 소유입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-112">When the file is opened for write access, the transaction is owned by the FILESTREAM agent.</span></span> <span data-ttu-id="c70cb-113">트랜잭션이 해제되기 전까지는 Win32 파일 I/O만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-113">Only Win32 file I/O is allowed until the transaction is released.</span></span> <span data-ttu-id="c70cb-114">트랜잭션을 해제하려면 쓰기 핸들을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-114">To release the transaction, the write handle must be closed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c70cb-115">구문</span><span class="sxs-lookup"><span data-stu-id="c70cb-115">Syntax</span></span>  
  
```  
  
  HANDLE OpenSqlFilestream (  
  LPCWSTR  
  FilestreamPath  
  ,  
  SQL_FILESTREAM_DESIRED_ACCESS  
  DesiredAccess,  
ULONGOpenOptions,LPBYTEFilestreamTransactionContext,SIZE_TFilestreamTransactionContextLength,PLARGE_INTEGERAllocationSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c70cb-116">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c70cb-116">Parameters</span></span>  
 <span data-ttu-id="c70cb-117">*FilestreamPath*</span><span class="sxs-lookup"><span data-stu-id="c70cb-117">*FilestreamPath*</span></span>  
 <span data-ttu-id="c70cb-118">진행 `nvarchar(max)` [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) 함수에서 반환 하는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-118">[in] Is the `nvarchar(max)` path that is returned by the [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) function.</span></span> <span data-ttu-id="c70cb-119">PathName은 FILESTREAM 테이블 및 열에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT 또는 UPDATE 권한이 있는 계정의 컨텍스트에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-119">PathName must be called from the context of an account that has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT or UPDATE permissions on the FILESTREAM table and column.</span></span>  
  
 <span data-ttu-id="c70cb-120">*DesiredAccess*</span><span class="sxs-lookup"><span data-stu-id="c70cb-120">*DesiredAccess*</span></span>  
 <span data-ttu-id="c70cb-121">[in] FILESTREAM BLOB 데이터에 액세스하는 데 사용되는 모드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-121">[in] Sets the mode used to access FILESTREAM BLOB data.</span></span> <span data-ttu-id="c70cb-122">이 값은 [DeviceIoControl Function](https://go.microsoft.com/fwlink/?LinkId=105527)(DeviceIoControl 함수)에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-122">This value is passed to the [DeviceIoControl Function](https://go.microsoft.com/fwlink/?LinkId=105527).</span></span>  
  
|<span data-ttu-id="c70cb-123">Name</span><span class="sxs-lookup"><span data-stu-id="c70cb-123">Name</span></span>|<span data-ttu-id="c70cb-124">값</span><span class="sxs-lookup"><span data-stu-id="c70cb-124">Value</span></span>|<span data-ttu-id="c70cb-125">의미</span><span class="sxs-lookup"><span data-stu-id="c70cb-125">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="c70cb-126">SQL_FILESTREAM_READ</span><span class="sxs-lookup"><span data-stu-id="c70cb-126">SQL_FILESTREAM_READ</span></span>|<span data-ttu-id="c70cb-127">0</span><span class="sxs-lookup"><span data-stu-id="c70cb-127">0</span></span>|<span data-ttu-id="c70cb-128">데이터를 파일에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-128">Data can be read from the file.</span></span>|  
|<span data-ttu-id="c70cb-129">SQL_FILESTREAM_WRITE</span><span class="sxs-lookup"><span data-stu-id="c70cb-129">SQL_FILESTREAM_WRITE</span></span>|<span data-ttu-id="c70cb-130">1</span><span class="sxs-lookup"><span data-stu-id="c70cb-130">1</span></span>|<span data-ttu-id="c70cb-131">데이터를 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-131">Data can be written to the file.</span></span>|  
|<span data-ttu-id="c70cb-132">SQL_FILESTREAM_READWRITE</span><span class="sxs-lookup"><span data-stu-id="c70cb-132">SQL_FILESTREAM_READWRITE</span></span>|<span data-ttu-id="c70cb-133">2</span><span class="sxs-lookup"><span data-stu-id="c70cb-133">2</span></span>|<span data-ttu-id="c70cb-134">데이터를 파일에서 읽고 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-134">Data can be read and written from the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c70cb-135">이러한 값은 sqlncli.h의 SQL_FILESTREAM_DESIRED_ACCESS 열거에서 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-135">These values are defined in the SQL_FILESTREAM_DESIRED_ACCESS enumeration in sqlncli.h.</span></span>  
  
 <span data-ttu-id="c70cb-136">*OpenOptions*</span><span class="sxs-lookup"><span data-stu-id="c70cb-136">*OpenOptions*</span></span>  
 <span data-ttu-id="c70cb-137">[in] 파일 특성 및 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-137">[in] The file attributes and flags.</span></span> <span data-ttu-id="c70cb-138">이 매개 변수는 다음 플래그의 조합을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-138">This parameter can also include any combination of the following flags.</span></span>  
  
|<span data-ttu-id="c70cb-139">플래그</span><span class="sxs-lookup"><span data-stu-id="c70cb-139">Flag</span></span>|<span data-ttu-id="c70cb-140">값</span><span class="sxs-lookup"><span data-stu-id="c70cb-140">Value</span></span>|<span data-ttu-id="c70cb-141">의미</span><span class="sxs-lookup"><span data-stu-id="c70cb-141">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="c70cb-142">SQL_FILESTREAM_OPEN_NONE</span><span class="sxs-lookup"><span data-stu-id="c70cb-142">SQL_FILESTREAM_OPEN_NONE</span></span>|<span data-ttu-id="c70cb-143">0x00000000:</span><span class="sxs-lookup"><span data-stu-id="c70cb-143">0x00000000:</span></span>|<span data-ttu-id="c70cb-144">특별한 옵션 없이 파일을 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-144">The file is being opened or created with no special options.</span></span>|  
|<span data-ttu-id="c70cb-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span><span class="sxs-lookup"><span data-stu-id="c70cb-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span></span>|<span data-ttu-id="c70cb-146">0x00000001L</span><span class="sxs-lookup"><span data-stu-id="c70cb-146">0x00000001L</span></span>|<span data-ttu-id="c70cb-147">비동기 I/O를 위해 파일을 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-147">The file is being opened or created for asynchronous I/O.</span></span>|  
|<span data-ttu-id="c70cb-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span><span class="sxs-lookup"><span data-stu-id="c70cb-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span></span>|<span data-ttu-id="c70cb-149">0x00000002L</span><span class="sxs-lookup"><span data-stu-id="c70cb-149">0x00000002L</span></span>|<span data-ttu-id="c70cb-150">시스템에서 시스템 캐싱을 사용하지 않고 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-150">The system opens the file by using no system caching.</span></span>|  
|<span data-ttu-id="c70cb-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span><span class="sxs-lookup"><span data-stu-id="c70cb-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span></span>|<span data-ttu-id="c70cb-152">0x00000004L</span><span class="sxs-lookup"><span data-stu-id="c70cb-152">0x00000004L</span></span>|<span data-ttu-id="c70cb-153">시스템에서 중간 캐시를 통해 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-153">The system does not write through an intermediate cache.</span></span> <span data-ttu-id="c70cb-154">쓰기는 디스크에 바로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-154">Writes go directly to disk.</span></span>|  
|<span data-ttu-id="c70cb-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span><span class="sxs-lookup"><span data-stu-id="c70cb-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span></span>|<span data-ttu-id="c70cb-156">0x00000008L</span><span class="sxs-lookup"><span data-stu-id="c70cb-156">0x00000008L</span></span>|<span data-ttu-id="c70cb-157">처음부터 끝까지 순차적으로 파일에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-157">A file is accessed sequentially from beginning to end.</span></span> <span data-ttu-id="c70cb-158">시스템에서는 이 필드를 힌트로 사용하여 파일 캐싱을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-158">The system can use this as a hint to optimize file caching.</span></span> <span data-ttu-id="c70cb-159">애플리케이션에서 임의 액세스를 위해 파일 포인터를 이동하는 경우 최적 캐싱이 수행되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-159">If an application moves the file pointer for random access, optimal caching may not occur.</span></span>|  
|<span data-ttu-id="c70cb-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span><span class="sxs-lookup"><span data-stu-id="c70cb-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span></span>|<span data-ttu-id="c70cb-161">0x00000010L</span><span class="sxs-lookup"><span data-stu-id="c70cb-161">0x00000010L</span></span>|<span data-ttu-id="c70cb-162">파일에 임의로 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-162">A file is accessed randomly.</span></span> <span data-ttu-id="c70cb-163">시스템에서는 이 필드를 힌트로 사용하여 파일 캐싱을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-163">The system can use this as a hint to optimize file caching.</span></span>|  
  
 <span data-ttu-id="c70cb-164">*FilestreamTransactionContext*</span><span class="sxs-lookup"><span data-stu-id="c70cb-164">*FilestreamTransactionContext*</span></span>  
 <span data-ttu-id="c70cb-165">[in] [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) 함수에서 반환하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-165">[in] The value that is returned by the [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) function.</span></span>  
  
 <span data-ttu-id="c70cb-166">*FilestreamTransactionContextLength*</span><span class="sxs-lookup"><span data-stu-id="c70cb-166">*FilestreamTransactionContextLength*</span></span>  
 <span data-ttu-id="c70cb-167">[in] GET_FILESTREAM_TRANSACTION_CONTEXT 함수에서 반환하는 `varbinary(max)` 데이터의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-167">[in] Number of bytes in the `varbinary(max)` data that is returned by the GET_FILESTREAM_TRANSACTION_CONTEXT function.</span></span> <span data-ttu-id="c70cb-168">이 함수는 N바이트의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-168">The function returns an array of N bytes.</span></span> <span data-ttu-id="c70cb-169">N은 함수에 의해 결정되며, 반환되는 바이트 배열의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-169">N is determined by the function and is a property of the byte array that is returned.</span></span>  
  
 <span data-ttu-id="c70cb-170">*AllocationSize*</span><span class="sxs-lookup"><span data-stu-id="c70cb-170">*AllocationSize*</span></span>  
 <span data-ttu-id="c70cb-171">[in] 데이터 파일의 처음 할당 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-171">[in] Specifies the initial allocation size of the data file in bytes.</span></span> <span data-ttu-id="c70cb-172">읽기 모드에서는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-172">It is ignored in read mode.</span></span> <span data-ttu-id="c70cb-173">이 매개 변수는 NULL일 수 있으며, 이 경우 기본 파일 시스템 동작이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-173">This parameter can be NULL, in which case the default file system behavior is used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c70cb-174">Return Value</span><span class="sxs-lookup"><span data-stu-id="c70cb-174">Return Value</span></span>  
 <span data-ttu-id="c70cb-175">이 함수가 성공적으로 실행되면 지정된 파일에 대해 열린 핸들이 반환되고</span><span class="sxs-lookup"><span data-stu-id="c70cb-175">If the function succeeds, the return value is an open handle to a specified file.</span></span> <span data-ttu-id="c70cb-176">함수가 실패하면 INVALID_HANDLE_VALUE가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-176">If the function fails, the return value is INVALID_HANDLE_VALUE.</span></span> <span data-ttu-id="c70cb-177">확장 오류 정보를 보려면 GetLastError()를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-177">For extended error information, call GetLastError().</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c70cb-178">예제</span><span class="sxs-lookup"><span data-stu-id="c70cb-178">Examples</span></span>  
 <span data-ttu-id="c70cb-179">다음 예에서는 `OpenSqlFilestream` API를 사용하여 Win32 핸들을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-179">The following examples show you how to use the `OpenSqlFilestream` API to obtain a Win32 handle.</span></span>  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
## <a name="remarks"></a><span data-ttu-id="c70cb-180">설명</span><span class="sxs-lookup"><span data-stu-id="c70cb-180">Remarks</span></span>  
 <span data-ttu-id="c70cb-181">이 API를 사용하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-181">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client must be installed to use this API.</span></span> <span data-ttu-id="c70cb-182">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 도구와 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70cb-182">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client tools.</span></span> <span data-ttu-id="c70cb-183">자세한 내용은 [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)(SQL Server Native Client 설치)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c70cb-183">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70cb-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c70cb-184">See Also</span></span>  
 <span data-ttu-id="c70cb-185">[Binary Large Object &#40;Blob&#41; 데이터 &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c70cb-185">[Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span></span>  
 <span data-ttu-id="c70cb-186">[FILESTREAM 데이터 부분 업데이트](make-partial-updates-to-filestream-data.md) </span><span class="sxs-lookup"><span data-stu-id="c70cb-186">[Make Partial Updates to FILESTREAM Data](make-partial-updates-to-filestream-data.md) </span></span>  
 [<span data-ttu-id="c70cb-187">FILESTREAM 애플리케이션에서 데이터베이스 작업과의 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="c70cb-187">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
