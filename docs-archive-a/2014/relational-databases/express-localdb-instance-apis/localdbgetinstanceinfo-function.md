---
title: LocalDBGetInstanceInfo 함수 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstanceInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc7cbe2c59a7502a1fd0c8b4f92fb14e5defd50b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648395"
---
# <a name="localdbgetinstanceinfo-function"></a><span data-ttu-id="ba89a-102">LocalDBGetInstanceInfo 함수</span><span class="sxs-lookup"><span data-stu-id="ba89a-102">LocalDBGetInstanceInfo Function</span></span>
  <span data-ttu-id="ba89a-103">인스턴스가 존재하는지 여부, 인스턴스가 사용하는 LocalDB 버전, 인스턴스가 실행되는지 여부 등과 같이 지정한 SQL Server Express LocalDB 인스턴스에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-103">Returns information for the specified SQL Server Express LocalDB instance, such as whether it exists, the LocalDB version it uses, whether it is running, and so on.</span></span>  
  
 <span data-ttu-id="ba89a-104">이 정보는 `struct` 다음 정의를 포함 하는 **Localdbinstanceinfo**라는 이름으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-104">The information is returned in a `struct` named **LocalDBInstanceInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 <span data-ttu-id="ba89a-105">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="ba89a-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba89a-106">구문</span><span class="sxs-lookup"><span data-stu-id="ba89a-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba89a-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ba89a-107">Parameters</span></span>  
 <span data-ttu-id="ba89a-108">*wszInstanceName*</span><span class="sxs-lookup"><span data-stu-id="ba89a-108">*wszInstanceName*</span></span>  
 <span data-ttu-id="ba89a-109">[입력] 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-109">[Input] The instance name.</span></span>  
  
 <span data-ttu-id="ba89a-110">*pInstanceInfo*</span><span class="sxs-lookup"><span data-stu-id="ba89a-110">*pInstanceInfo*</span></span>  
 <span data-ttu-id="ba89a-111">[출력] LocalDB 인스턴스에 대한 정보를 저장하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-111">[Output] The buffer to store the information about the LocalDB instance.</span></span>  
  
 <span data-ttu-id="ba89a-112">*dwInstanceInfoSize*</span><span class="sxs-lookup"><span data-stu-id="ba89a-112">*dwInstanceInfoSize*</span></span>  
 <span data-ttu-id="ba89a-113">입력 *Instanceinfo* 버퍼의 크기를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-113">[Input] Holds the size of the *InstanceInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ba89a-114">반환</span><span class="sxs-lookup"><span data-stu-id="ba89a-114">Returns</span></span>  
 <span data-ttu-id="ba89a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba89a-115">S_OK</span></span>  
 <span data-ttu-id="ba89a-116">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="ba89a-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="ba89a-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="ba89a-118">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="ba89a-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="ba89a-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="ba89a-120">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="ba89a-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="ba89a-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="ba89a-122">지정한 인스턴스 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="ba89a-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="ba89a-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="ba89a-124">인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-124">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="ba89a-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="ba89a-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="ba89a-126">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-126">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="ba89a-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="ba89a-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="ba89a-128">인스턴스 폴더에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-128">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="ba89a-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="ba89a-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="ba89a-130">인스턴스 레지스트리에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-130">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="ba89a-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="ba89a-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="ba89a-132">인스턴스 구성이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-132">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="ba89a-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="ba89a-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="ba89a-134">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-134">An unexpected error occurred.</span></span> <span data-ttu-id="ba89a-135">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba89a-135">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ba89a-136">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ba89a-136">Details</span></span>  
 <span data-ttu-id="ba89a-137">`struct`크기 인수 (*Lpinstanceinfosize*)를 도입 하는 이유는 API에서 다른 버전의 **Localdbinstanceinfostruct**를 반환 하 여 이전 버전과 이전 버전과의 호환성을 효과적으로 사용할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-137">The rationale behind the introduction of the `struct` size argument (*lpInstanceInfoSize*) is to enable the API to return different versions of the **LocalDBInstanceInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="ba89a-138">`struct`Size 인수 (*Lpinstanceinfosize*)가 알려진 버전의 **Localdbinstanceinfostruct**크기와 일치 하면 해당 버전의 `struct` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-138">If the `struct` size argument (*lpInstanceInfoSize*) matches the size of a known version of the **LocalDBInstanceInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="ba89a-139">그렇지 않으면 LOCALDB_ERROR_INVALID_PARAMETER가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-139">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="ba89a-140">**Localdbgetinstanceinfo** API 사용의 일반적인 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba89a-140">A typical example of **LocalDBGetInstanceInfo** API usage looks like this:</span></span>  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L"Test", &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 <span data-ttu-id="ba89a-141">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba89a-141">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba89a-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba89a-142">See Also</span></span>  
 [<span data-ttu-id="ba89a-143">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="ba89a-143">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
