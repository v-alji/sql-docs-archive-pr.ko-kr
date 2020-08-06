---
title: LocalDBStopInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 4bd73187-0aac-4f03-ac54-2b78e41917e5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48b014e65e0a02a5f866e5301b12dae3cd255b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728255"
---
# <a name="localdbstopinstance-function"></a><span data-ttu-id="b4681-102">LocalDBStopInstance 함수</span><span class="sxs-lookup"><span data-stu-id="b4681-102">LocalDBStopInstance Function</span></span>
  <span data-ttu-id="b4681-103">지정한 SQL Server Express LocalDB 인스턴스의 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-103">Stops the specified SQL Server Express LocalDB instance from running.</span></span>  
  
 <span data-ttu-id="b4681-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="b4681-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4681-105">구문</span><span class="sxs-lookup"><span data-stu-id="b4681-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           ULONG ulTimeout   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4681-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b4681-106">Parameters</span></span>  
 <span data-ttu-id="b4681-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="b4681-107">*pInstanceName*</span></span>  
 <span data-ttu-id="b4681-108">[입력] 중지할 LocalDB 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-108">[Input] The name of the LocalDB instance to stop.</span></span>  
  
 <span data-ttu-id="b4681-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="b4681-109">*dwFlags*</span></span>  
 <span data-ttu-id="b4681-110">[입력] 인스턴스를 중지할 방법을 지정하는 플래그 값 중 하나 또는 값의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-110">[Input] One or a combination of the flag values specifying the way to stop the instance.</span></span>  
  
 <span data-ttu-id="b4681-111">사용 가능한 플래그:</span><span class="sxs-lookup"><span data-stu-id="b4681-111">Available flags:</span></span>  
  
 <span data-ttu-id="b4681-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="b4681-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span></span>  
 <span data-ttu-id="b4681-113">프로세스 중지 운영 체제 명령을 사용하여 즉시 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-113">Shut down immediately using the kill process operating system command.</span></span>  
  
 <span data-ttu-id="b4681-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span><span class="sxs-lookup"><span data-stu-id="b4681-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span></span>  
 <span data-ttu-id="b4681-115">WITH NOWAIT 옵션 Transact-SQL 명령을 사용하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-115">Shut down using the WITH NOWAIT option Transact-SQL command.</span></span>  
  
 <span data-ttu-id="b4681-116">플래그를 설정하지 않은 경우 LocalDB 인스턴스는 SHUTDOWN Transact-SQL 명령을 사용하여 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-116">If none of the flags is set, the LocalDB instance will be shut down using the SHUTDOWN Transact-SQL command.</span></span> <span data-ttu-id="b4681-117">두 플래그를 모두 설정한 경우 LOCALDB_SHUTDOWN_KILL_PROCESS 플래그가 우선적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-117">If both flags are set, the LOCALDB_SHUTDOWN_KILL_PROCESS flag takes precedence.</span></span>  
  
 <span data-ttu-id="b4681-118">*ulTimeout*</span><span class="sxs-lookup"><span data-stu-id="b4681-118">*ulTimeout*</span></span>  
 <span data-ttu-id="b4681-119">[입력] 이 작업이 완료될 때까지 대기할 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-119">[Input] The time in seconds to wait for this operation to complete.</span></span> <span data-ttu-id="b4681-120">이 값이 0인 경우 이 함수는 LocalDB 인스턴스가 중지될 때까지 대기하지 않고 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-120">If this value is 0, this function will return immediately without waiting for the LocalDB instance to stop.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b4681-121">반환</span><span class="sxs-lookup"><span data-stu-id="b4681-121">Returns</span></span>  
 <span data-ttu-id="b4681-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4681-122">S_OK</span></span>  
 <span data-ttu-id="b4681-123">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-123">The function succeeded.</span></span>  
  
 [<span data-ttu-id="b4681-124">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="b4681-124">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="b4681-125">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-125">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="b4681-126">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="b4681-126">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="b4681-127">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-127">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="b4681-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="b4681-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="b4681-129">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-129">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="b4681-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="b4681-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="b4681-131">인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-131">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="b4681-132">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4681-132">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="b4681-133">동기화 잠금을 획득하려고 시도하는 동안 제한 시간이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-133">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="b4681-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span><span class="sxs-lookup"><span data-stu-id="b4681-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-instance-stop-failed.md)  
 <span data-ttu-id="b4681-135">지정된 시간 내에 중지 작업을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-135">The stop operation failed to complete within the given time.</span></span>  
  
 [<span data-ttu-id="b4681-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="b4681-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="b4681-137">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-137">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="b4681-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="b4681-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="b4681-139">사용자 프로필 폴더를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-139">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="b4681-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="b4681-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="b4681-141">인스턴스 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-141">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="b4681-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="b4681-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="b4681-143">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-143">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="b4681-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="b4681-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="b4681-145">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-145">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="b4681-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4681-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="b4681-147">API 호출자는 LocalDB 인스턴스 소유자가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-147">API caller is not LocalDB instance owner.</span></span>  
  
 [<span data-ttu-id="b4681-148">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="b4681-148">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="b4681-149">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4681-149">An unexpected error occurred.</span></span> <span data-ttu-id="b4681-150">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4681-150">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4681-151">설명</span><span class="sxs-lookup"><span data-stu-id="b4681-151">Remarks</span></span>  
 <span data-ttu-id="b4681-152">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4681-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4681-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4681-153">See Also</span></span>  
 [<span data-ttu-id="b4681-154">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="b4681-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
