---
title: LocalDBDeleteInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBDeleteInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 37cb2a7e-672a-4223-b6f3-a94d7b8d58cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d4c873e045c5effed476ca9d147270d159ec3b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653401"
---
# <a name="localdbdeleteinstance-function"></a><span data-ttu-id="15b88-102">LocalDBDeleteInstance 함수</span><span class="sxs-lookup"><span data-stu-id="15b88-102">LocalDBDeleteInstance Function</span></span>
  <span data-ttu-id="15b88-103">지정한 SQL Server Express LocalDB 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-103">Removes the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="15b88-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="15b88-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b88-105">구문</span><span class="sxs-lookup"><span data-stu-id="15b88-105">Syntax</span></span>  
  
```  
HRESULT LocalDBDeleteInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15b88-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="15b88-106">Parameters</span></span>  
 <span data-ttu-id="15b88-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="15b88-107">*pInstanceName*</span></span>  
 <span data-ttu-id="15b88-108">[입력] 제거할 LocalDB 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-108">[Input] The name of the LocalDB instance to remove.</span></span>  
  
 <span data-ttu-id="15b88-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="15b88-109">*dwFlags*</span></span>  
 <span data-ttu-id="15b88-110">[입력] 나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="15b88-111">현재 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="15b88-112">반환</span><span class="sxs-lookup"><span data-stu-id="15b88-112">Returns</span></span>  
 <span data-ttu-id="15b88-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="15b88-113">S_OK</span></span>  
 <span data-ttu-id="15b88-114">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="15b88-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="15b88-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="15b88-116">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="15b88-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="15b88-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="15b88-118">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="15b88-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="15b88-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="15b88-120">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="15b88-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="15b88-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="15b88-122">지정한 인스턴스가 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="15b88-123">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="15b88-123">LOCALDB_ERROR_INSTANCE_BUSY</span></span>](../express-localdb-error-messages/localdb-error-instance-busy.md)  
 <span data-ttu-id="15b88-124">지정된 인스턴스가 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-124">The specified instance is running.</span></span>  
  
 [<span data-ttu-id="15b88-125">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15b88-125">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="15b88-126">동기화 잠금을 획득하려고 시도하는 중에 시간 초과가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-126">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
 [<span data-ttu-id="15b88-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="15b88-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="15b88-128">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-128">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="15b88-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="15b88-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="15b88-130">사용자 프로필 폴더를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-130">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="15b88-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="15b88-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="15b88-132">인스턴스 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-132">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="15b88-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="15b88-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="15b88-134">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-134">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="15b88-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="15b88-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="15b88-136">인스턴스 레지스트리를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-136">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="15b88-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="15b88-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="15b88-138">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-138">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="15b88-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15b88-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="15b88-140">API 호출자는 로컬 데이터베이스 인스턴스 소유자가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-140">API caller is not Local Database instance owner.</span></span>  
  
 [<span data-ttu-id="15b88-141">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="15b88-141">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="15b88-142">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="15b88-142">An unexpected error occurred.</span></span> <span data-ttu-id="15b88-143">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15b88-143">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15b88-144">설명</span><span class="sxs-lookup"><span data-stu-id="15b88-144">Remarks</span></span>  
 <span data-ttu-id="15b88-145">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15b88-145">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b88-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15b88-146">See Also</span></span>  
 [<span data-ttu-id="15b88-147">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="15b88-147">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
