---
title: LocalDBGetVersions 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37d2a927346252f1b126f5e3a4ec78ea03cde0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741056"
---
# <a name="localdbgetversions-function"></a><span data-ttu-id="9ac72-102">LocalDBGetVersions 함수</span><span class="sxs-lookup"><span data-stu-id="9ac72-102">LocalDBGetVersions Function</span></span>
  <span data-ttu-id="9ac72-103">컴퓨터에서 사용할 수 있는 모든 SQL Server Express LocalDB 버전을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-103">Returns all SQL Server Express LocalDB versions available on the computer.</span></span>  
  
 <span data-ttu-id="9ac72-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="9ac72-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac72-105">구문</span><span class="sxs-lookup"><span data-stu-id="9ac72-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac72-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9ac72-106">Parameters</span></span>  
 <span data-ttu-id="9ac72-107">*pVersionNames*</span><span class="sxs-lookup"><span data-stu-id="9ac72-107">*pVersionNames*</span></span>  
 <span data-ttu-id="9ac72-108">출력 사용자의 워크스테이션에서 사용할 수 있는 LocalDB 버전의 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-108">[Output] Contains names of the LocalDB versions that are available on the user's workstation.</span></span>  
  
 <span data-ttu-id="9ac72-109">*lpdwNumberOfVersions*</span><span class="sxs-lookup"><span data-stu-id="9ac72-109">*lpdwNumberOfVersions*</span></span>  
 <span data-ttu-id="9ac72-110">[입력/출력] 입력 시 *pVersionNames* 버퍼의 버전에 대한 슬롯 수를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-110">[Input/Output] On input holds the number of slots for versions in the *pVersionNames* buffer.</span></span>   
<span data-ttu-id="9ac72-111">출력 시 기존 LocalDB 버전의 수를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-111">On output, holds the number of existing LocalDB versions.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="9ac72-112">반환</span><span class="sxs-lookup"><span data-stu-id="9ac72-112">Returns</span></span>  
 <span data-ttu-id="9ac72-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ac72-113">S_OK</span></span>  
 <span data-ttu-id="9ac72-114">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="9ac72-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="9ac72-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="9ac72-116">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="9ac72-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="9ac72-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="9ac72-118">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="9ac72-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9ac72-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="9ac72-120">입력 버퍼가 너무 짧은데 잘림이 요청되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="9ac72-121">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="9ac72-121">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="9ac72-122">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac72-122">An unexpected error occurred.</span></span> <span data-ttu-id="9ac72-123">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ac72-123">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac72-124">설명</span><span class="sxs-lookup"><span data-stu-id="9ac72-124">Remarks</span></span>  
 <span data-ttu-id="9ac72-125">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ac72-125">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac72-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ac72-126">See Also</span></span>  
 [<span data-ttu-id="9ac72-127">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="9ac72-127">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
