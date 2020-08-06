---
title: LocalDBFormatMessage 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ece28f19e3488fae248bf26c3a54a018ba6efd0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743263"
---
# <a name="localdbformatmessage-function"></a><span data-ttu-id="6f43c-102">LocalDBFormatMessage 함수</span><span class="sxs-lookup"><span data-stu-id="6f43c-102">LocalDBFormatMessage Function</span></span>
  <span data-ttu-id="6f43c-103">지정한 SQL Server Express LocalDB 오류에 대해 해당 언어의 텍스트 설명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-103">Returns the localized textual description for the specified SQL Server Express LocalDB error.</span></span>  
  
 <span data-ttu-id="6f43c-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="6f43c-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f43c-105">구문</span><span class="sxs-lookup"><span data-stu-id="6f43c-105">Syntax</span></span>  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f43c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6f43c-106">Parameters</span></span>  
 <span data-ttu-id="6f43c-107">*hrLocalDB*</span><span class="sxs-lookup"><span data-stu-id="6f43c-107">*hrLocalDB*</span></span>  
 <span data-ttu-id="6f43c-108">[입력] LocalDB 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-108">[Input] The LocalDB error code.</span></span>  
  
 <span data-ttu-id="6f43c-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="6f43c-109">*dwFlags*</span></span>  
 <span data-ttu-id="6f43c-110">[입력] 이 함수의 동작을 지정하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-110">[Input] The flags specifying the behavior of this function.</span></span>  
  
 <span data-ttu-id="6f43c-111">사용 가능한 플래그:</span><span class="sxs-lookup"><span data-stu-id="6f43c-111">Available flags:</span></span>  
  
 <span data-ttu-id="6f43c-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span><span class="sxs-lookup"><span data-stu-id="6f43c-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span></span>  
 <span data-ttu-id="6f43c-113">입력 버퍼가 너무 짧은 경우 오류 메시지가 버퍼에 맞게 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-113">If the input buffer is too short, the error message will be truncated to fit the buffer.</span></span>  
  
 <span data-ttu-id="6f43c-114">*dwLanguageId*</span><span class="sxs-lookup"><span data-stu-id="6f43c-114">*dwLanguageId*</span></span>  
 <span data-ttu-id="6f43c-115">[입력] 원하는 언어(LANGID) 또는 0입니다. 이 경우 Win32 FormatMessage 언어 순서가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-115">[Input] The language desired (LANGID) or 0, in which case the Win32 FormatMessage language order is used.</span></span>  
  
 <span data-ttu-id="6f43c-116">*wszMessage*</span><span class="sxs-lookup"><span data-stu-id="6f43c-116">*wszMessage*</span></span>  
 <span data-ttu-id="6f43c-117">[출력] LocalDB 오류 메시지를 저장할 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-117">[Output] The buffer to store the LocalDB error message.</span></span>  
  
 <span data-ttu-id="6f43c-118">*lpcchMessage*</span><span class="sxs-lookup"><span data-stu-id="6f43c-118">*lpcchMessage*</span></span>  
 <span data-ttu-id="6f43c-119">[입력/출력] 입력 시 문자의 *wszMessage* 버퍼 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-119">[Input/Output] On input contains the size of the *wszMessage* buffer in characters.</span></span> <span data-ttu-id="6f43c-120">출력 시 지정된 버퍼 크기가 너무 작은 경우 후행 Null을 포함하여 문자에 필요한 버퍼 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-120">On output, if the given buffer size is too small, contains the buffer size required in characters, including any trailing nulls.</span></span> <span data-ttu-id="6f43c-121">함수가 성공하는 경우 후행 Null을 제외하고 메시지의 문자 수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-121">If the function succeeds, contains the number of characters in the message, excluding any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6f43c-122">반환</span><span class="sxs-lookup"><span data-stu-id="6f43c-122">Returns</span></span>  
 <span data-ttu-id="6f43c-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f43c-123">S_OK</span></span>  
 <span data-ttu-id="6f43c-124">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-124">The function succeeded.</span></span>  
  
 [<span data-ttu-id="6f43c-125">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="6f43c-125">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="6f43c-126">SQL Server Express LocalDB가 컴퓨터에 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-126">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="6f43c-127">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="6f43c-127">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="6f43c-128">지정한 입력 매개 변수 중 한 개 이상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-128">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="6f43c-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span><span class="sxs-lookup"><span data-stu-id="6f43c-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span></span>](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 <span data-ttu-id="6f43c-130">요청한 메시지가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-130">The requested message does not exist.</span></span>  
  
 [<span data-ttu-id="6f43c-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="6f43c-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 <span data-ttu-id="6f43c-132">메시지가 요청한 언어로 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-132">The message is not available in the requested language.</span></span>  
  
 [<span data-ttu-id="6f43c-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6f43c-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="6f43c-134">입력된 버퍼 *wszMessage* 가 너무 짧은데 잘림을 요청하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-134">The input buffer *wszMessage* is too short, and truncation is not requested.</span></span>  
  
 [<span data-ttu-id="6f43c-135">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="6f43c-135">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="6f43c-136">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="6f43c-136">An unexpected error occurred.</span></span> <span data-ttu-id="6f43c-137">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f43c-137">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f43c-138">설명</span><span class="sxs-lookup"><span data-stu-id="6f43c-138">Remarks</span></span>  
 <span data-ttu-id="6f43c-139">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f43c-139">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f43c-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f43c-140">See Also</span></span>  
 [<span data-ttu-id="6f43c-141">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="6f43c-141">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
