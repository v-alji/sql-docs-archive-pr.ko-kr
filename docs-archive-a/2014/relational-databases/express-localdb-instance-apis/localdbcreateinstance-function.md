---
title: LocalDBCreateInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff822c552176ad8c083a1c8ea6c0f2430f72972f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653406"
---
# <a name="localdbcreateinstance-function"></a><span data-ttu-id="405f6-102">LocalDBCreateInstance 함수</span><span class="sxs-lookup"><span data-stu-id="405f6-102">LocalDBCreateInstance Function</span></span>
  <span data-ttu-id="405f6-103">새 SQL Server Express LocalDB 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-103">Creates a new SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="405f6-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="405f6-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="405f6-105">구문</span><span class="sxs-lookup"><span data-stu-id="405f6-105">Syntax</span></span>  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="405f6-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="405f6-106">Parameters</span></span>  
 <span data-ttu-id="405f6-107">*wszVersion*</span><span class="sxs-lookup"><span data-stu-id="405f6-107">*wszVersion*</span></span>  
 <span data-ttu-id="405f6-108">[입력] 예를 들어 11.0 또는 11.0.1094.2와 같은 LocalDB 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-108">[Input] The LocalDB version, for example 11.0 or 11.0.1094.2.</span></span>  
  
 <span data-ttu-id="405f6-109">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="405f6-109">*pInstanceName*</span></span>  
 <span data-ttu-id="405f6-110">[입력] 만들 LocalDB 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-110">[Input] The name for the LocalDB instance to create.</span></span>  
  
 <span data-ttu-id="405f6-111">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="405f6-111">*dwFlags*</span></span>  
 <span data-ttu-id="405f6-112">[입력] 나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-112">[Input] Reserved for future use.</span></span> <span data-ttu-id="405f6-113">현재 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-113">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="405f6-114">반환</span><span class="sxs-lookup"><span data-stu-id="405f6-114">Returns</span></span>  
 <span data-ttu-id="405f6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="405f6-115">S_OK</span></span>  
 <span data-ttu-id="405f6-116">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="405f6-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="405f6-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="405f6-118">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="405f6-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="405f6-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="405f6-120">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="405f6-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="405f6-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="405f6-122">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="405f6-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="405f6-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="405f6-124">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-124">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="405f6-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="405f6-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 <span data-ttu-id="405f6-126">지정한 인스턴스가 이미 있지만 버전이 요청한 것보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-126">The specified instance already exists but its version is lower than requested.</span></span>  
  
 [<span data-ttu-id="405f6-127">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="405f6-127">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="405f6-128">지정한 버전을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-128">The specified version is not available.</span></span>  
  
 [<span data-ttu-id="405f6-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="405f6-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 <span data-ttu-id="405f6-130">지정한 패치 수준이 설치되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-130">The specified patch level is not installed.</span></span>  
  
 [<span data-ttu-id="405f6-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="405f6-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 <span data-ttu-id="405f6-132">%Userprofile% 아래에 폴더를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-132">A folder cannot be created under %userprofile%.</span></span>  
  
 [<span data-ttu-id="405f6-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="405f6-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="405f6-134">사용자 프로필 폴더를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-134">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="405f6-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="405f6-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="405f6-136">인스턴스 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-136">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="405f6-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="405f6-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="405f6-138">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-138">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="405f6-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="405f6-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="405f6-140">인스턴스 레지스트리를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-140">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="405f6-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="405f6-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="405f6-142">SQL Server 프로세스가 시작되었지만 SQL Server 시작이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-142">A SQL Server process is started but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="405f6-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="405f6-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="405f6-144">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-144">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="405f6-145">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="405f6-145">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="405f6-146">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-146">An unexpected error occurred.</span></span> <span data-ttu-id="405f6-147">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="405f6-147">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="405f6-148">설명</span><span class="sxs-lookup"><span data-stu-id="405f6-148">Remarks</span></span>  
 <span data-ttu-id="405f6-149">지정한 이름으로 완전히 작동하는 LocalDB 인스턴스가 이미 있으며 버전이 요청한 것보다 높거나 같은 경우 결과는 S_OK입니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-149">If a fully functional LocalDB instance with the specified name already exists and its version is equal to or higher than requested, the result is S_OK.</span></span>  
  
 <span data-ttu-id="405f6-150">기존 인스턴스가 손상된 경우 `LocalDBCreateInstance` API 메서드에 대한 후속 요청이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-150">In cases when an existing instance becomes corrupted, subsequent calls to the `LocalDBCreateInstance` API method will fail.</span></span> <span data-ttu-id="405f6-151">손상된 인스턴스를 다시 사용하려면 수동으로 수정하거나 명시적으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="405f6-151">Corrupted instances must be fixed manually or explicitly deleted before they can be used again.</span></span>  
  
 <span data-ttu-id="405f6-152">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="405f6-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405f6-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="405f6-153">See Also</span></span>  
 [<span data-ttu-id="405f6-154">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="405f6-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
