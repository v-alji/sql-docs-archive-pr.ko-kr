---
title: srv_describe(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_describe
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
author: rothja
ms.author: jroth
ms.openlocfilehash: 52a397b79f4fcecaa2ccacde7500cb852ae793fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660577"
---
# <a name="srv_describe-extended-stored-procedure-api"></a><span data-ttu-id="9bc12-102">srv_describe(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="9bc12-102">srv_describe (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="9bc12-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9bc12-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="9bc12-104">행의 특정 열에 대해 열 이름과 원본 및 대상 데이터 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-104">Defines the column name and source and destination data types for a specific column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc12-105">구문</span><span class="sxs-lookup"><span data-stu-id="9bc12-105">Syntax</span></span>  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="9bc12-106">인수</span><span class="sxs-lookup"><span data-stu-id="9bc12-106">Arguments</span></span>  
 <span data-ttu-id="9bc12-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="9bc12-107">*srvproc*</span></span>  
 <span data-ttu-id="9bc12-108">특정 클라이언트 연결에 대한 핸들(이 경우 행을 보내는 클라이언트)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the client sending the row).</span></span> <span data-ttu-id="9bc12-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 모든 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-109">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="9bc12-110">*colnumber*</span><span class="sxs-lookup"><span data-stu-id="9bc12-110">*colnumber*</span></span>  
 <span data-ttu-id="9bc12-111">현재 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-111">Is currently not supported.</span></span> <span data-ttu-id="9bc12-112">순서대로 열을 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-112">Columns must be described in order.</span></span> <span data-ttu-id="9bc12-113">**srv_sendrow**가 호출되기 전에 모든 열을 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-113">All columns must be described before **srv_sendrow** is called.</span></span>  
  
 <span data-ttu-id="9bc12-114">*column_name*</span><span class="sxs-lookup"><span data-stu-id="9bc12-114">*column_name*</span></span>  
 <span data-ttu-id="9bc12-115">데이터가 속하는 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-115">Specifies the name of the column to which the data belongs.</span></span> <span data-ttu-id="9bc12-116">열에 이름이 없어도 되기 때문에 이 매개 변수는 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-116">This parameter can be NULL because a column is not required to have a name.</span></span>  
  
 <span data-ttu-id="9bc12-117">*namelen*</span><span class="sxs-lookup"><span data-stu-id="9bc12-117">*namelen*</span></span>  
 <span data-ttu-id="9bc12-118">*column_name*의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-118">Specifies the length, in bytes, of *column_name*.</span></span> <span data-ttu-id="9bc12-119">*namelen*이 SRV_NULLTERM이면 *column_name*이 null로 종결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-119">If *namelen* is SRV_NULLTERM, then *column_name* must be null-terminated.</span></span>  
  
 <span data-ttu-id="9bc12-120">*desttype*</span><span class="sxs-lookup"><span data-stu-id="9bc12-120">*desttype*</span></span>  
 <span data-ttu-id="9bc12-121">대상 행 열의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-121">Specifies the data type of the destination row column.</span></span> <span data-ttu-id="9bc12-122">클라이언트로 전송되는 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-122">This is the data type sent to the client.</span></span> <span data-ttu-id="9bc12-123">데이터가 NULL인 경우에도 데이터 형식을 지정해야 합니다. 자세한 내용은 [데이터 형식(확장 저장 프로시저 API)](data-types-extended-stored-procedure-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bc12-123">The data type must be specified even if the data is NULL, for more information, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="9bc12-124">*destlen*</span><span class="sxs-lookup"><span data-stu-id="9bc12-124">*destlen*</span></span>  
 <span data-ttu-id="9bc12-125">클라이언트로 전송할 데이터의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-125">Specifies the length, in bytes, of the data to be sent to the client.</span></span> <span data-ttu-id="9bc12-126">Null 값을 허용하지 않는 고정 길이 데이터 형식의 경우 *destlen*이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-126">For fixed-length data types that do not allow null values, *destlen* is ignored.</span></span> <span data-ttu-id="9bc12-127">Null 값을 허용하는 고정 길이 데이터 형식 및 가변 길이 데이터 형식의 경우 *destlen*은 대상 데이터의 최대 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-127">For variable-length data types and fixed-length data types that allow null values, *destlen* specifies the maximum length the destination data can be.</span></span>  
  
 <span data-ttu-id="9bc12-128">*srctype*</span><span class="sxs-lookup"><span data-stu-id="9bc12-128">*srctype*</span></span>  
 <span data-ttu-id="9bc12-129">원본 데이터의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-129">Specifies the data type of the source data.</span></span>  
  
 <span data-ttu-id="9bc12-130">*srclen*</span><span class="sxs-lookup"><span data-stu-id="9bc12-130">*srclen*</span></span>  
 <span data-ttu-id="9bc12-131">원본 데이터의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-131">Specifies the length, in bytes, of the source data.</span></span> <span data-ttu-id="9bc12-132">고정 길이 데이터 형식의 경우 이 값이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-132">This value is ignored for fixed-length data types.</span></span>  
  
 <span data-ttu-id="9bc12-133">*srcdata*</span><span class="sxs-lookup"><span data-stu-id="9bc12-133">*srcdata*</span></span>  
 <span data-ttu-id="9bc12-134">특정 열에 대한 원본 데이터 주소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-134">Provides the source data address for a particular column.</span></span> <span data-ttu-id="9bc12-135">**srv_sendrow**가 호출되면 *srcdata*에서 *colnumber*의 데이터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-135">When **srv_sendrow** is called, it looks for the data for *colnumber* at *srcdata*.</span></span> <span data-ttu-id="9bc12-136">따라서 **srv_sendrow**를 호출하기 전에 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-136">Therefore it should not be freed before a call to **srv_sendrow**.</span></span> <span data-ttu-id="9bc12-137">**srv_setcoldata**를 사용하여 **srv_sendrow** 호출 사이에 원본 데이터 주소를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-137">The source data address can be changed between calls to **srv_sendrow** by using **srv_setcoldata**.</span></span> <span data-ttu-id="9bc12-138">**srv_setcoldata**에 대한 다른 호출에 의해 열 데이터가 바뀌거나 **srv_senddone**이 호출될 때까지 *srcdata*에 할당된 메모리를 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-138">Memory allocated for *srcdata* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
 <span data-ttu-id="9bc12-139">*desttype*이 SRVDECIMAL이나 SRVNUMERIC인 경우 *srcdata* 매개 변수는 구조의 전체 자릿수 및 소수 자릿수 필드가 원하는 값으로 설정되어 있는 DBNUMERIC 또는 DBDECIMAL 구조에 대한 포인터여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-139">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *srcdata* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the values you want.</span></span> <span data-ttu-id="9bc12-140">DEFAULTPRECISION을 사용하여 기본 전체 자릿수를 지정하고 DEFAULTSCALE을 사용하여 기본 소수 자릿수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-140">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="9bc12-141">반환</span><span class="sxs-lookup"><span data-stu-id="9bc12-141">Returns</span></span>  
 <span data-ttu-id="9bc12-142">설명되는 열 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-142">The number of the column described.</span></span> <span data-ttu-id="9bc12-143">첫 번째 열은 열 1입니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-143">The first column is column 1.</span></span> <span data-ttu-id="9bc12-144">오류가 발생하면 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-144">If an error occurs, returns 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bc12-145">설명</span><span class="sxs-lookup"><span data-stu-id="9bc12-145">Remarks</span></span>  
 <span data-ttu-id="9bc12-146">**srv_sendrow**를 처음 호출하기 전에 행의 각 열에 대해 한 번씩, **srv_describe** 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-146">The **srv_describe** function must be called once for each column in the row before the first call to **srv_sendrow**.</span></span> <span data-ttu-id="9bc12-147">순서에 관계없이 행의 열을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-147">The columns of a row can be described in any order.</span></span>  
  
 <span data-ttu-id="9bc12-148">전체 결과 집합이 전송되기 전에 열 행의 원본 데이터 위치와 길이를 변경하려면 각각 **srv_setcoldata** 및 **srv_setcollen**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-148">To change the location and length of the source data in column rows before the complete result set has been sent, use **srv_setcoldata** and **srv_setcollen**, respectively.</span></span>  
  
 <span data-ttu-id="9bc12-149">데이터 형식 및 확장 저장 프로시저 API 데이터 형식 변환에 대한 설명은 [데이터 형식(확장 저장 프로시저 API)](data-types-extended-stored-procedure-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bc12-149">For a description of data types and Extended Store Procedure API data type conversions, see[Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="9bc12-150">애플리케이션의 열 이름이 유니코드로 되어 있으면 **srv_describe**를 호출하기 전에 서버의 멀티바이트 코드 페이지로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-150">If the column name in your application is in Unicode, you need to convert it to the multibyte code page of the server before calling **srv_describe**.</span></span> <span data-ttu-id="9bc12-151">자세한 내용은 [유니코드 데이터 및 서버 코드 페이지](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9bc12-151">For more information, see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9bc12-152">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bc12-152">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="9bc12-153">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9bc12-153">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc12-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bc12-154">See Also</span></span>  
 <span data-ttu-id="9bc12-155">[srv_sendrow &#40;확장 저장 프로시저 API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="9bc12-155">[srv_sendrow &#40;Extended Stored Procedure API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span></span>  
 <span data-ttu-id="9bc12-156">[srv_setutype &#40;확장 저장 프로시저 API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="9bc12-156">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="9bc12-157">srv_setcoldata(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="9bc12-157">srv_setcoldata &#40;Extended Stored Procedure API&#41;</span></span>](srv-setcoldata-extended-stored-procedure-api.md)  
  
  
