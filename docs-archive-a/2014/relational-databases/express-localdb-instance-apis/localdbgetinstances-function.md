---
title: LocalDBGetInstances 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a6f758bd647fd69a14f72a0651bb3e2e33a7c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728256"
---
# <a name="localdbgetinstances-function"></a><span data-ttu-id="b9b3d-102">LocalDBGetInstances 함수</span><span class="sxs-lookup"><span data-stu-id="b9b3d-102">LocalDBGetInstances Function</span></span>
  <span data-ttu-id="b9b3d-103">지정된 버전의 모든 SQL Server Express LocalDB 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-103">Returns all SQL Server Express LocalDB instances with the given version.</span></span>  
  
 <span data-ttu-id="b9b3d-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="b9b3d-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b3d-105">구문</span><span class="sxs-lookup"><span data-stu-id="b9b3d-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9b3d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b9b3d-106">Parameters</span></span>  
 <span data-ttu-id="b9b3d-107">*pInstanceNames*</span><span class="sxs-lookup"><span data-stu-id="b9b3d-107">*pInstanceNames*</span></span>  
 <span data-ttu-id="b9b3d-108">출력 이 함수가 반환 될 때 사용자 워크스테이션의 명명 된 LocalDB 인스턴스 및 기본 LocalDB 인스턴스 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-108">[Output] When this function returns, contains the names of both named and default LocalDB instances on the user's workstation.</span></span>  
  
 <span data-ttu-id="b9b3d-109">*lpdwNumberOfInstances*</span><span class="sxs-lookup"><span data-stu-id="b9b3d-109">*lpdwNumberOfInstances*</span></span>  
 <span data-ttu-id="b9b3d-110">[입력/출력] 입력 시 *pInstanceNames* 버퍼의 인스턴스 이름에 대한 슬롯 수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-110">[Input/Output] On input, contains the number of slots for instance names in the *pInstanceNames* buffer.</span></span> <span data-ttu-id="b9b3d-111">출력 시 사용자의 워크스테이션에서 발견 된 LocalDB 인스턴스 수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-111">On output, contains the number of LocalDB instances found on the user's workstation.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b9b3d-112">반환</span><span class="sxs-lookup"><span data-stu-id="b9b3d-112">Returns</span></span>  
 <span data-ttu-id="b9b3d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9b3d-113">S_OK</span></span>  
 <span data-ttu-id="b9b3d-114">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="b9b3d-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="b9b3d-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="b9b3d-116">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="b9b3d-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="b9b3d-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="b9b3d-118">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="b9b3d-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b9b3d-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="b9b3d-120">입력 버퍼가 너무 짧은데 잘림이 요청되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="b9b3d-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="b9b3d-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="b9b3d-122">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-122">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="b9b3d-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="b9b3d-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="b9b3d-124">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-124">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="b9b3d-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="b9b3d-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="b9b3d-126">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-126">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="b9b3d-127">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="b9b3d-127">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="b9b3d-128">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-128">An unexpected error occurred.</span></span> <span data-ttu-id="b9b3d-129">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-129">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9b3d-130">설명</span><span class="sxs-lookup"><span data-stu-id="b9b3d-130">Remarks</span></span>  
 <span data-ttu-id="b9b3d-131">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9b3d-131">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b3d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9b3d-132">See Also</span></span>  
 [<span data-ttu-id="b9b3d-133">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="b9b3d-133">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
