---
title: LocalDBStartInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 748bc373e8b0dbad0a91247e068d21b67f2dbc1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660591"
---
# <a name="localdbstartinstance-function"></a><span data-ttu-id="689a9-102">LocalDBStartInstance 함수</span><span class="sxs-lookup"><span data-stu-id="689a9-102">LocalDBStartInstance Function</span></span>
  <span data-ttu-id="689a9-103">지정한 SQL Server Express LocalDB 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-103">Starts the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="689a9-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="689a9-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="689a9-105">구문</span><span class="sxs-lookup"><span data-stu-id="689a9-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="689a9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="689a9-106">Parameters</span></span>  
 <span data-ttu-id="689a9-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="689a9-107">*pInstanceName*</span></span>  
 <span data-ttu-id="689a9-108">[입력] 시작할 LocalDB 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-108">[Input] The name of the LocalDB instance to start.</span></span>  
  
 <span data-ttu-id="689a9-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="689a9-109">*dwFlags*</span></span>  
 <span data-ttu-id="689a9-110">[입력] 나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="689a9-111">현재 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-111">Currently should be set to 0.</span></span>  
  
 <span data-ttu-id="689a9-112">*wszSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="689a9-112">*wszSqlConnection*</span></span>  
 <span data-ttu-id="689a9-113">[출력] LocalDB 인스턴스에 연결 문자열을 저장할 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-113">[Output] The buffer to store the connection string to the LocalDB instance.</span></span>  
  
 <span data-ttu-id="689a9-114">*lpcchSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="689a9-114">*lpcchSqlConnection*</span></span>  
 <span data-ttu-id="689a9-115">[입력/출력] 출력 시 후행 Null을 포함하여 문자의 *wszSqlConnection* 버퍼 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-115">[Input/Output] On input contains the size of the *wszSqlConnection* buffer in characters, including any trailing nulls.</span></span> <span data-ttu-id="689a9-116">출력 시 지정된 버퍼 크기가 너무 작은 경우 후행 Null을 포함하여 문자에 필요한 버퍼 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-116">On output, if the given buffer size is too small, contains the required buffer size in characters, including any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="689a9-117">반환</span><span class="sxs-lookup"><span data-stu-id="689a9-117">Returns</span></span>  
 <span data-ttu-id="689a9-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="689a9-118">S_OK</span></span>  
 <span data-ttu-id="689a9-119">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-119">The function succeeded.</span></span>  
  
 [<span data-ttu-id="689a9-120">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="689a9-120">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="689a9-121">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-121">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="689a9-122">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="689a9-122">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="689a9-123">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-123">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="689a9-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="689a9-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="689a9-125">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-125">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="689a9-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="689a9-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="689a9-127">인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-127">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="689a9-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="689a9-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="689a9-129">지정한 버퍼 *wszSqlConnection* 이 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-129">The specified buffer *wszSqlConnection* is too small.</span></span>  
  
 [<span data-ttu-id="689a9-130">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="689a9-130">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="689a9-131">동기화 잠금을 획득하려고 시도하는 동안 제한 시간이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-131">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="689a9-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="689a9-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="689a9-133">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-133">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="689a9-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="689a9-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="689a9-135">사용자 프로필 폴더를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-135">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="689a9-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="689a9-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="689a9-137">인스턴스 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-137">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="689a9-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="689a9-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="689a9-139">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-139">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="689a9-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="689a9-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="689a9-141">인스턴스 레지스트리를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-141">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="689a9-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="689a9-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 <span data-ttu-id="689a9-143">SQL Server에 대한 프로세스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-143">A process for SQL Server cannot be created.</span></span>  
  
 [<span data-ttu-id="689a9-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="689a9-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="689a9-145">SQL Server 프로세스가 시작되었지만 SQL Server 시작이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-145">A SQL Server process was started, but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="689a9-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="689a9-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="689a9-147">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-147">An instance configuration was corrupted.</span></span>  
  
 [<span data-ttu-id="689a9-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="689a9-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span></span>](../express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 <span data-ttu-id="689a9-149">자동 인스턴스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-149">Cannot create an automatic instance.</span></span> <span data-ttu-id="689a9-150">자세한 오류 정보는 Windows 애플리케이션 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="689a9-150">See the Windows Application event log for error details.</span></span>  
  
 [<span data-ttu-id="689a9-151">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="689a9-151">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="689a9-152">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-152">An unexpected error occurred.</span></span> <span data-ttu-id="689a9-153">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="689a9-153">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="689a9-154">세부 정보</span><span class="sxs-lookup"><span data-stu-id="689a9-154">Details</span></span>  
 <span data-ttu-id="689a9-155">연결 버퍼 인수(*wszSqlConnection*) 및 연결 버퍼 크기 인수(*lpcchSqlConnection*)는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-155">Both the connection buffer argument (*wszSqlConnection*) and the connection buffer size argument (*lpcchSqlConnection*) are optional.</span></span> <span data-ttu-id="689a9-156">다음 표에서는 이러한 인수를 사용하기 위한 옵션과 해당 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-156">The following table shows options for using these arguments and their results.</span></span>  
  
|<span data-ttu-id="689a9-157">Buffer</span><span class="sxs-lookup"><span data-stu-id="689a9-157">Buffer</span></span>|<span data-ttu-id="689a9-158">버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="689a9-158">Buffer size</span></span>|<span data-ttu-id="689a9-159">이유</span><span class="sxs-lookup"><span data-stu-id="689a9-159">Rationale</span></span>|<span data-ttu-id="689a9-160">작업</span><span class="sxs-lookup"><span data-stu-id="689a9-160">Action</span></span>|  
|------------|-----------------|---------------|------------|  
|<span data-ttu-id="689a9-161">NULL</span><span class="sxs-lookup"><span data-stu-id="689a9-161">NULL</span></span>|<span data-ttu-id="689a9-162">NULL</span><span class="sxs-lookup"><span data-stu-id="689a9-162">NULL</span></span>|<span data-ttu-id="689a9-163">사용자가 인스턴스를 시작 하려고 하며 파이프 이름이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-163">User wants to start the instance and doesn't need a pipe name.</span></span>|<span data-ttu-id="689a9-164">인스턴스를 시작합니다(파이프 반환 없음, 필요한 버퍼 크기 반환 없음).</span><span class="sxs-lookup"><span data-stu-id="689a9-164">Starts an instance (no pipe return and no required buffer size return).</span></span>|  
|<span data-ttu-id="689a9-165">NULL</span><span class="sxs-lookup"><span data-stu-id="689a9-165">NULL</span></span>|<span data-ttu-id="689a9-166">표시</span><span class="sxs-lookup"><span data-stu-id="689a9-166">Present</span></span>|<span data-ttu-id="689a9-167">사용자가 출력 버퍼 크기를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-167">User asks for the output buffer size.</span></span> <span data-ttu-id="689a9-168">다음 호출에서 사용자는 실제 시작을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-168">(In the next call the user will probably ask for an actual start.)</span></span>|<span data-ttu-id="689a9-169">필요한 버퍼 크기를 반환합니다(시작 없음, 파이프 반환 없음).</span><span class="sxs-lookup"><span data-stu-id="689a9-169">Returns a required buffer size (no start and no pipe return).</span></span> <span data-ttu-id="689a9-170">결과는 S_OK입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-170">Result is S_OK.</span></span>|  
|<span data-ttu-id="689a9-171">표시</span><span class="sxs-lookup"><span data-stu-id="689a9-171">Present</span></span>|<span data-ttu-id="689a9-172">NULL</span><span class="sxs-lookup"><span data-stu-id="689a9-172">NULL</span></span>|<span data-ttu-id="689a9-173">허용되지 않으며 잘못된 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-173">Not allowed; incorrect input.</span></span>|<span data-ttu-id="689a9-174">반환된 결과는 LOCALDB_ERROR_INVALID_PARAMETER입니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-174">Returned result is LOCALDB_ERROR_INVALID_PARAMETER.</span></span>|  
|<span data-ttu-id="689a9-175">표시</span><span class="sxs-lookup"><span data-stu-id="689a9-175">Present</span></span>|<span data-ttu-id="689a9-176">표시</span><span class="sxs-lookup"><span data-stu-id="689a9-176">Present</span></span>|<span data-ttu-id="689a9-177">사용자가 인스턴스를 시작하려고 하며 인스턴스가 시작된 후 인스턴스에 연결하기 위해 파이프 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-177">User wants to start the instance and needs the pipe name to connect to it after it is started.</span></span>|<span data-ttu-id="689a9-178">버퍼 크기를 검사하고, 인스턴스를 시작하며 버퍼의 파이프 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-178">Checks the buffer size, starts the instance, and returns the pipe name in the buffer.</span></span> <br /><span data-ttu-id="689a9-179">버퍼 크기 인수는 종료 null을 포함 하지 않는 "server =" 문자열의 길이를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="689a9-179">The buffer size argument returns the length of the "server=" string, not including terminating nulls.</span></span>|  
  
 <span data-ttu-id="689a9-180">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="689a9-180">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689a9-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="689a9-181">See Also</span></span>  
 [<span data-ttu-id="689a9-182">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="689a9-182">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
