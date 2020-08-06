---
title: LocalDBShareInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBShareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 21eb3b9a-7d32-455b-89bb-f624198cd202
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 238bff0b3512ceb03ead186dc001165274bd4e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649997"
---
# <a name="localdbshareinstance-function"></a><span data-ttu-id="7cecd-102">LocalDBShareInstance 함수</span><span class="sxs-lookup"><span data-stu-id="7cecd-102">LocalDBShareInstance Function</span></span>
  <span data-ttu-id="7cecd-103">지정된 공유 이름을 사용하여 컴퓨터의 다른 사용자와 함께 지정된 SQL Server Express LocalDB 인스턴스를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-103">Shares the specified SQL Server Express LocalDB instance with other users of the computer, using the specified shared name.</span></span>  
  
 <span data-ttu-id="7cecd-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="7cecd-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cecd-105">구문</span><span class="sxs-lookup"><span data-stu-id="7cecd-105">Syntax</span></span>  
  
```  
HRESULT LocalDBShareInstance(  
           PSID pOwnerSID,  
           PCWSTR pInstancePrivateName,  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cecd-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7cecd-106">Parameters</span></span>  
 <span data-ttu-id="7cecd-107">*pOwnerSID*</span><span class="sxs-lookup"><span data-stu-id="7cecd-107">*pOwnerSID*</span></span>  
 <span data-ttu-id="7cecd-108">[입력] 인스턴스 소유자의 SID입니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-108">[Input] The SID of the instance owner.</span></span>  
  
 <span data-ttu-id="7cecd-109">*pInstancePrivateName*</span><span class="sxs-lookup"><span data-stu-id="7cecd-109">*pInstancePrivateName*</span></span>  
 <span data-ttu-id="7cecd-110">[입력] 공유할 LocalDB 인스턴스의 프라이빗 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-110">[Input] The private name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="7cecd-111">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="7cecd-111">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="7cecd-112">[입력] 공유할 LocalDB 인스턴스의 공유 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-112">[Input] The shared name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="7cecd-113">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="7cecd-113">*dwFlags*</span></span>  
 <span data-ttu-id="7cecd-114">[입력] 나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-114">[Input] Reserved for future use.</span></span> <span data-ttu-id="7cecd-115">현재 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-115">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7cecd-116">반환</span><span class="sxs-lookup"><span data-stu-id="7cecd-116">Returns</span></span>  
 <span data-ttu-id="7cecd-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cecd-117">S_OK</span></span>  
 <span data-ttu-id="7cecd-118">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-118">The function succeeded.</span></span>  
  
 [<span data-ttu-id="7cecd-119">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="7cecd-119">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="7cecd-120">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-120">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="7cecd-121">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="7cecd-121">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="7cecd-122">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-122">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="7cecd-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="7cecd-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="7cecd-124">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-124">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="7cecd-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="7cecd-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="7cecd-126">지정한 인스턴스가 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-126">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="7cecd-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="7cecd-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="7cecd-128">이 작업을 실행하려면 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-128">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="7cecd-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span><span class="sxs-lookup"><span data-stu-id="7cecd-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span></span>](../express-localdb-error-messages/localdb-error-shared-name-taken.md)  
 <span data-ttu-id="7cecd-130">지정한 공유 이름이 이미 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-130">The specified shared name is already taken.</span></span>  
  
 [<span data-ttu-id="7cecd-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="7cecd-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>](../express-localdb-error-messages/localdb-error-instance-already-shared.md)  
 <span data-ttu-id="7cecd-132">지정된 인스턴스가 이미 공유되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-132">The specified instance is already shared.</span></span>  
  
 [<span data-ttu-id="7cecd-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="7cecd-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="7cecd-134">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cecd-134">An unexpected error occurred.</span></span> <span data-ttu-id="7cecd-135">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7cecd-135">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cecd-136">설명</span><span class="sxs-lookup"><span data-stu-id="7cecd-136">Remarks</span></span>  
 <span data-ttu-id="7cecd-137">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7cecd-137">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cecd-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7cecd-138">See Also</span></span>  
 [<span data-ttu-id="7cecd-139">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="7cecd-139">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
