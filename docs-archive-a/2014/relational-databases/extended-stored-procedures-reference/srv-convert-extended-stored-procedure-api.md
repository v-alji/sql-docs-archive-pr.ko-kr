---
title: srv_convert(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660578"
---
# <a name="srv_convert-extended-stored-procedure-api"></a><span data-ttu-id="7d6a4-102">srv_convert(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="7d6a4-102">srv_convert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="7d6a4-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="7d6a4-104">한 데이터 형식에서 다른 데이터 형식으로 데이터를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-104">Changes data from one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6a4-105">구문</span><span class="sxs-lookup"><span data-stu-id="7d6a4-105">Syntax</span></span>  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d6a4-106">인수</span><span class="sxs-lookup"><span data-stu-id="7d6a4-106">Arguments</span></span>  
 <span data-ttu-id="7d6a4-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-107">*srvproc*</span></span>  
 <span data-ttu-id="7d6a4-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="7d6a4-109">이 구조에는 확장 저장 프로시저 API가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 모든 제어 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-109">The structure contains all the control information that the Extended Stored Procedure API uses to manage communications and data between the application and the client.</span></span> <span data-ttu-id="7d6a4-110">*srvproc* 핸들을 제공하면 오류가 발생할 경우 확장 저장 프로시저 API 오류 처리기로 해당 핸들이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-110">If the *srvproc* handle is supplied, it is passed to the Extended Stored Procedure API error handler function when an error occurs.</span></span>  
  
 <span data-ttu-id="7d6a4-111">*srctype*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-111">*srctype*</span></span>  
 <span data-ttu-id="7d6a4-112">변환할 데이터의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-112">Specifies the data type of the data to be converted.</span></span> <span data-ttu-id="7d6a4-113">이 매개 변수는 임의의 확장 저장 프로시저 API 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-113">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="7d6a4-114">*src*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-114">*src*</span></span>  
 <span data-ttu-id="7d6a4-115">변환할 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-115">Is a pointer to the data to be converted.</span></span> <span data-ttu-id="7d6a4-116">이 매개 변수는 임의의 확장 저장 프로시저 API 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-116">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="7d6a4-117">*srclen*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-117">*srclen*</span></span>  
 <span data-ttu-id="7d6a4-118">변환할 데이터의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-118">Specifies the length, in bytes, of the data to be converted.</span></span> <span data-ttu-id="7d6a4-119">*srclen*이 0이면 **srv_convert**는 대상 변수에 Null 값을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-119">If *srclen* is 0, **srv_convert** places a null value in the destination variable.</span></span> <span data-ttu-id="7d6a4-120">0이 아니면 고정 길이 데이터 형식의 경우 이 매개 변수가 무시되며, 이때 원본 데이터는 NULL인 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-120">Unless it is 0, this parameter is ignored for fixed-length data types, in which case the source data is assumed to be NULL.</span></span> <span data-ttu-id="7d6a4-121">SRVCHAR 데이터 형식의 데이터에서 길이 -1은 문자열이 Null로 종결됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-121">For data of the SRVCHAR data type, a length of -1 indicates the string is null-terminated.</span></span>  
  
 <span data-ttu-id="7d6a4-122">*desttype*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-122">*desttype*</span></span>  
 <span data-ttu-id="7d6a4-123">원본을 변환할 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-123">Specifies the data type to convert the source to.</span></span> <span data-ttu-id="7d6a4-124">이 매개 변수는 임의의 확장 저장 프로시저 API 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-124">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="7d6a4-125">*dest*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-125">*dest*</span></span>  
 <span data-ttu-id="7d6a4-126">변환된 데이터를 받는 대상 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-126">Is a pointer to the destination variable that receives converted data.</span></span> <span data-ttu-id="7d6a4-127">이 포인터가 NULL이면 **srv_convert**에서 사용자가 제공한 오류 처리기(있는 경우)를 호출하고 -1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-127">If this pointer is NULL, **srv_convert** calls the user-supplied error handler ,if any, and returns -1.</span></span>  
  
 <span data-ttu-id="7d6a4-128">*desttype*이 SRVDECIMAL이나 SRVNUMERIC인 경우 *dest* 매개 변수는 구조의 전체 자릿수 및 소수 자릿수 필드가 원하는 값으로 설정되어 있는 DBNUMERIC 또는 DBDECIMAL 구조에 대한 포인터여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-128">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *dest* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the desired values.</span></span> <span data-ttu-id="7d6a4-129">DEFAULTPRECISION을 사용하여 기본 전체 자릿수를 지정하고 DEFAULTSCALE을 사용하여 기본 소수 자릿수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-129">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
 <span data-ttu-id="7d6a4-130">*destlen*</span><span class="sxs-lookup"><span data-stu-id="7d6a4-130">*destlen*</span></span>  
 <span data-ttu-id="7d6a4-131">대상 변수의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-131">Specifies the length, in bytes, of the destination variable.</span></span> <span data-ttu-id="7d6a4-132">고정 길이 데이터 형식의 경우 이 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-132">This parameter is ignored for fixed-length data types.</span></span> <span data-ttu-id="7d6a4-133">SRVCHAR 유형의 대상 변수에서 *destlen* 값은 대상 버퍼 공간의 총 길이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-133">For a destination variable of type SRVCHAR, the value of *destlen* must be the total length of the destination buffer space.</span></span> <span data-ttu-id="7d6a4-134">SRVCHAR 또는 SRVBINARY 유형의 대상 변수에서 길이 -1은 사용 가능한 충분한 공간이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-134">A length of -1 for a destination variable of type SRVCHAR or SRVBINARY indicates there is sufficient space available.</span></span> <span data-ttu-id="7d6a4-135">*srvchar* 유형의 대상 변수에서 길이가 -1이면 문자열이 Null로 종결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-135">For a destination variable of type *srvchar*, a length of -1 causes the character string to be null-terminated.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7d6a4-136">반환</span><span class="sxs-lookup"><span data-stu-id="7d6a4-136">Returns</span></span>  
 <span data-ttu-id="7d6a4-137">데이터 형식 변환에 성공할 경우 변환된 데이터의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-137">The length of the converted data, in bytes, if the data type conversion succeeds.</span></span> <span data-ttu-id="7d6a4-138">**srv_convert**에서 지원하지 않는 변환 요청을 발견하면 개발자가 제공한 오류 처리기(있는 경우)를 호출하며, 전역 오류 번호를 설정하고 -1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-138">When **srv_convert** encounters a request for a conversion it does not support, it calls the developer-supplied error handler, if any, sets a global error number, and returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6a4-139">설명</span><span class="sxs-lookup"><span data-stu-id="7d6a4-139">Remarks</span></span>  
 <span data-ttu-id="7d6a4-140">**srv_willconvert** 함수는 특정 변환의 허용 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-140">The **srv_willconvert** function determines whether a particular conversion is allowed.</span></span>  
  
 <span data-ttu-id="7d6a4-141">근사치 데이터 형식 SRVFLT4 또는 SRVFLT8로 변환하면 전체 자릿수 손실이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-141">Converting to the approximate numeric data types SRVFLT4 or SRVFLT8 can result in some loss of precision.</span></span> <span data-ttu-id="7d6a4-142">근사치 데이터 형식 SRVFLT4 또는 SRVFLT8을 SRVCHAR 또는 SRVTEXT로 변환하는 경우에도 전체 자릿수 손실이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-142">Converting from the approximate numeric data types SRVFLT4 or SRVFLT8 to SRVCHAR or SRVTEXT can also result in some loss of precision.</span></span>  
  
 <span data-ttu-id="7d6a4-143">SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL 또는 SRVNUMERIC으로 변환하면 숫자가 대상의 최대값보다 클 경우 오버플로가 발생하고, 숫자가 대상의 최소값보다 작을 경우 언더플로가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-143">Converting to SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL, or SRVNUMERIC can result in overflow if the number is larger than the maximum value of the destination, or in underflow if the number is smaller than the minimum value of the destination.</span></span> <span data-ttu-id="7d6a4-144">SRVCHAR 또는 SRVTEXT로 변환할 때 오버플로가 발생하면 결과 값의 첫 문자에 오류를 나타내는 별표(\*)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-144">If overflow occurs when converting to SRVCHAR or SRVTEXT, the first character of the resulting value contains an asterisk (\*) to indicate the error.</span></span>  
  
 <span data-ttu-id="7d6a4-145">SRVCHAR를 SRVBINARY로 변환하는 경우 **srv_convert**는 문자열에 선행 0이 포함되어 있는지 여부에 관계없이 SRVCHAR를 16진수로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-145">When converting SRVCHAR to SRVBINARY, **srv_convert** interprets SRVCHAR as hexadecimal, whether or not the string contains a leading 0.</span></span> <span data-ttu-id="7d6a4-146">SRVBINARY를 SRVCHAR로 변환하는 경우에는 **srv_convert**에서 선행 0 없이 16진수 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-146">When converting SRVBINARY to SRVCHAR, **srv_convert** creates a hexadecimal string without a leading 0.</span></span> <span data-ttu-id="7d6a4-147">다른 모든 경우에서 SRVBINARY 데이터 형식과의 변환은 단순한 비트 복사입니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-147">In all other cases, a conversion to or from the SRVBINARY data type is a straight bit-copy.</span></span>  
  
 <span data-ttu-id="7d6a4-148">경우에 따라 데이터 형식을 동일한 데이터 형식으로 변환하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-148">In certain cases, it can be useful to convert a data type to itself.</span></span> <span data-ttu-id="7d6a4-149">예를 들어 *destlen*을 -1로 설정하여 SRVCHAR를 SRVCHAR로 변환하면 문자열에 Null 종결자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-149">For example, converting SRVCHAR to SRVCHAR with a *destlen* of -1 adds a null terminator to a string.</span></span>  
  
 <span data-ttu-id="7d6a4-150">데이터 형식 및 확장 저장 프로시저 API 데이터 형식 변환에 대한 설명은 [데이터 형식(확장 저장 프로시저 API)](data-types-extended-stored-procedure-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-150">For a description of data types and Extended Store Procedure API data type conversions, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="7d6a4-151">**srv_convert** 함수는 여러 가지 이유로 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-151">The **srv_convert** function can fail for several reasons:</span></span>  
  
-   <span data-ttu-id="7d6a4-152">요청된 변환을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-152">The requested conversion is not available.</span></span>  
  
-   <span data-ttu-id="7d6a4-153">변환으로 인해 대상 변수에서 잘림, 오버플로 또는 전체 자릿수 손실이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-153">The conversion resulted in truncation, overflow, or loss of precision in the destination variable.</span></span>  
  
-   <span data-ttu-id="7d6a4-154">문자열을 숫자 데이터 형식으로 변환하는 동안 구문 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-154">A syntax error occurred while converting a character string to a numeric data type.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7d6a4-155">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-155">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="7d6a4-156">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d6a4-156">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6a4-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d6a4-157">See Also</span></span>  
 <span data-ttu-id="7d6a4-158">[srv_setutype &#40;확장 저장 프로시저 API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="7d6a4-158">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="7d6a4-159">srv_willconvert(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="7d6a4-159">srv_willconvert &#40;Extended Stored Procedure API&#41;</span></span>](srv-willconvert-extended-stored-procedure-api.md)  
  
  
