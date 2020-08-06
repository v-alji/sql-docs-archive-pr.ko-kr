---
title: LocalDBGetVersionInfo 함수 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e30bb4dcd4c258db899883f650dbfe7100171ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742148"
---
# <a name="localdbgetversioninfo-function"></a><span data-ttu-id="5f920-102">LocalDBGetVersionInfo 함수</span><span class="sxs-lookup"><span data-stu-id="5f920-102">LocalDBGetVersionInfo Function</span></span>
  <span data-ttu-id="5f920-103">버전이 존재하는지 여부, 전체 LocalDB 버전 번호(빌드 및 릴리스 번호 포함)와 같이 지정한 SQL Server Express LocalDB 버전에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-103">Returns information for the specified SQL Server Express LocalDB version, such as whether it exists and the full LocalDB version number (including build and release numbers).</span></span>  
  
 <span data-ttu-id="5f920-104">정보는 다음 정의를 포함 하는 명명 된 LocalDBVersionInfo 형식으로 반환 됩니다 `struct` . **LocalDBVersionInfo**</span><span class="sxs-lookup"><span data-stu-id="5f920-104">The information is returned in the form of a `struct` named **LocalDBVersionInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 <span data-ttu-id="5f920-105">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="5f920-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f920-106">구문</span><span class="sxs-lookup"><span data-stu-id="5f920-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f920-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f920-107">Parameters</span></span>  
 <span data-ttu-id="5f920-108">*wszVersionName*</span><span class="sxs-lookup"><span data-stu-id="5f920-108">*wszVersionName*</span></span>  
 <span data-ttu-id="5f920-109">[입력] LocalDB 버전 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-109">[Input] The LocalDB version name.</span></span>  
  
 <span data-ttu-id="5f920-110">*pVersionInfo*</span><span class="sxs-lookup"><span data-stu-id="5f920-110">*pVersionInfo*</span></span>  
 <span data-ttu-id="5f920-111">[출력] LocalDB 버전에 대한 정보를 저장하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-111">[Output] The buffer to store the information about the LocalDB version.</span></span>  
  
 <span data-ttu-id="5f920-112">*dwVersionInfoSize*</span><span class="sxs-lookup"><span data-stu-id="5f920-112">*dwVersionInfoSize*</span></span>  
 <span data-ttu-id="5f920-113">입력 *VersionInfo* 버퍼의 크기를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-113">[Input] Holds the size of the *VersionInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5f920-114">반환</span><span class="sxs-lookup"><span data-stu-id="5f920-114">Returns</span></span>  
 <span data-ttu-id="5f920-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f920-115">S_OK</span></span>  
 <span data-ttu-id="5f920-116">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="5f920-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="5f920-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="5f920-118">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="5f920-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="5f920-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="5f920-120">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="5f920-121">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="5f920-121">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="5f920-122">지정된 LocalDB 버전이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-122">The specified LocalDB version does not exist.</span></span>  
  
 [<span data-ttu-id="5f920-123">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="5f920-123">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="5f920-124">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-124">An unexpected error occurred.</span></span> <span data-ttu-id="5f920-125">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5f920-125">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f920-126">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5f920-126">Details</span></span>  
 <span data-ttu-id="5f920-127">`struct`크기 인수 (*lpVersionInfoSize*)를 도입 하는 이유는 API에서 다른 버전의 **LocalDBVersionInfostruct**를 반환할 수 있도록 하 여 전달 및 이전 버전과의 호환성을 효과적으로 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-127">The rationale behind the introduction of the `struct` size argument (*lpVersionInfoSize*) is to enable the API to return different versions of the **LocalDBVersionInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="5f920-128">`struct`Size 인수 (*lpVersionInfoSize*)가 알려진 버전의 **LocalDBVersionInfostruct**크기와 일치 하면 해당 버전의 `struct` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-128">If the `struct` size argument (*lpVersionInfoSize*) matches the size of a known version of the **LocalDBVersionInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="5f920-129">그렇지 않으면 LOCALDB_ERROR_INVALID_PARAMETER가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-129">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="5f920-130">**LocalDBGetVersionInfo** API 사용의 일반적인 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5f920-130">A typical example of **LocalDBGetVersionInfo** API usage looks like this:</span></span>  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f920-131">설명</span><span class="sxs-lookup"><span data-stu-id="5f920-131">Remarks</span></span>  
 <span data-ttu-id="5f920-132">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5f920-132">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f920-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f920-133">See Also</span></span>  
 [<span data-ttu-id="5f920-134">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="5f920-134">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
