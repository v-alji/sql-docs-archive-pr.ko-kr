---
title: LocalDBUnshareInstance 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBUnshareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 54012ccb-eded-43f7-8ea5-da5ce79224c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77ebf8cad9d410b047fccede4360ca0041637986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647023"
---
# <a name="localdbunshareinstance-function"></a><span data-ttu-id="e9ace-102">LocalDBUnshareInstance 함수</span><span class="sxs-lookup"><span data-stu-id="e9ace-102">LocalDBUnshareInstance Function</span></span>
  <span data-ttu-id="e9ace-103">지정한 SQL Server Express LocalDB 인스턴스의 공유를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-103">Stops the sharing of the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="e9ace-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="e9ace-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ace-105">구문</span><span class="sxs-lookup"><span data-stu-id="e9ace-105">Syntax</span></span>  
  
```  
HRESULT LocalDBUnShareInstance(  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9ace-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e9ace-106">Parameters</span></span>  
 <span data-ttu-id="e9ace-107">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="e9ace-107">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="e9ace-108">[입력] 공유를 해제할 LocalDB 인스턴스의 공유 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-108">[Input] The shared name for the LocalDB instance to unshare.</span></span>  
  
 <span data-ttu-id="e9ace-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="e9ace-109">*dwFlags*</span></span>  
 <span data-ttu-id="e9ace-110">[입력] 나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="e9ace-111">현재 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="e9ace-112">반환</span><span class="sxs-lookup"><span data-stu-id="e9ace-112">Returns</span></span>  
 <span data-ttu-id="e9ace-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9ace-113">S_OK</span></span>  
 <span data-ttu-id="e9ace-114">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="e9ace-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="e9ace-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="e9ace-116">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="e9ace-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="e9ace-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="e9ace-118">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="e9ace-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="e9ace-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="e9ace-120">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="e9ace-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="e9ace-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="e9ace-122">지정한 인스턴스가 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="e9ace-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="e9ace-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="e9ace-124">이 작업을 실행하려면 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-124">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="e9ace-125">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="e9ace-125">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="e9ace-126">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ace-126">An unexpected error occurred.</span></span> <span data-ttu-id="e9ace-127">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9ace-127">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9ace-128">설명</span><span class="sxs-lookup"><span data-stu-id="e9ace-128">Remarks</span></span>  
 <span data-ttu-id="e9ace-129">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9ace-129">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ace-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9ace-130">See Also</span></span>  
 [<span data-ttu-id="e9ace-131">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="e9ace-131">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
