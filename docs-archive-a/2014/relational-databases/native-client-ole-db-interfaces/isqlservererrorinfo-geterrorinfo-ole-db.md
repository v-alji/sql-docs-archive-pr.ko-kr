---
title: ISQLServerErrorInfo::GetErrorInfo(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e325cd99276e04a178b89c19b233289edc09fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734063"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a><span data-ttu-id="ddee4-102">ISQLServerErrorInfo::GetErrorInfo(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ddee4-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="ddee4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]오류 정보가 포함 된 Native Client OLE DB PROVIDER SSERRORINFO 구조체에 대 한 포인터를 반환 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ddee4-103">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure containing the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddee4-104">구문</span><span class="sxs-lookup"><span data-stu-id="ddee4-104">Syntax</span></span>  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a><span data-ttu-id="ddee4-105">인수</span><span class="sxs-lookup"><span data-stu-id="ddee4-105">Arguments</span></span>  
 <span data-ttu-id="ddee4-106">*ppSSErrorInfo*[out]</span><span class="sxs-lookup"><span data-stu-id="ddee4-106">*ppSSErrorInfo*[out]</span></span>  
 <span data-ttu-id="ddee4-107">SSERRORINFO 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-107">A pointer to a SSERRORINFO structure.</span></span> <span data-ttu-id="ddee4-108">메서드가 실패하거나 오류와 연관된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 정보가 없는 경우 공급자는 메모리를 할당하지 않고 출력에서 *ppSSErrorInfo* 인수가 Null 포인터인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-108">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with the error, the provider does not allocate any memory, and ensures that the *ppSSErrorInfo* argument is a null pointer on output.</span></span>  
  
 <span data-ttu-id="ddee4-109">*ppErrorStrings*[out]</span><span class="sxs-lookup"><span data-stu-id="ddee4-109">*ppErrorStrings*[out]</span></span>  
 <span data-ttu-id="ddee4-110">유니코드 문자열 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-110">A pointer to a Unicode character-string pointer.</span></span> <span data-ttu-id="ddee4-111">메서드가 실패하거나 오류와 연관된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 정보가 없는 경우 공급자는 메모리를 할당하지 않고 출력에서 *ppErrorStrings* 인수가 Null 포인터인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-111">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with an error, the provider does not allocate any memory, and ensures that the *ppErrorStrings* argument is a null pointer on output.</span></span> <span data-ttu-id="ddee4-112">**IMalloc::Free** 메서드를 사용하여 *ppErrorStrings* 인수를 해제하면 메모리가 블록에 할당될 때 반환된 SSERRORINFO 구조에 있는 세 개의 각 문자열 멤버가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-112">Freeing the *ppErrorStrings* argument with the **IMalloc::Free** method frees the three individual string members of the returned SSERRORINFO structure, as the memory is allocated in a block.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="ddee4-113">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="ddee4-113">Return Code Values</span></span>  
 <span data-ttu-id="ddee4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddee4-114">S_OK</span></span>  
 <span data-ttu-id="ddee4-115">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-115">The method succeeded.</span></span>  
  
 <span data-ttu-id="ddee4-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ddee4-116">E_INVALIDARG</span></span>  
 <span data-ttu-id="ddee4-117">*ppSSErrorInfo* 또는 *ppErrorStrings* 인수는 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-117">Either the *ppSSErrorInfo* or the *ppErrorStrings* argument was NULL.</span></span>  
  
 <span data-ttu-id="ddee4-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ddee4-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ddee4-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자에서 요청을 완료 하는 데 충분 한 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider could not allocate sufficient memory to complete the request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddee4-120">설명</span><span class="sxs-lookup"><span data-stu-id="ddee4-120">Remarks</span></span>  
 <span data-ttu-id="ddee4-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자가 전달한 포인터를 통해 반환 된 SSERRORINFO 및 OLECHAR 문자열에 대해 메모리를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider allocates memory for the SSERRORINFO and OLECHAR strings returned through the pointers passed by the consumer.</span></span> <span data-ttu-id="ddee4-122">소비자는 오류 데이터에 액세스할 필요가 없게 되면 **IMalloc::Free** 메서드를 사용하여 이 메모리의 할당을 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-122">The consumer must deallocate this memory by using the **IMalloc::Free** method when it no longer requires access to the error data.</span></span>  
  
 <span data-ttu-id="ddee4-123">SSERRORINFO 구조는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-123">The SSERRORINFO structure is defined as follows:</span></span>  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|<span data-ttu-id="ddee4-124">멤버</span><span class="sxs-lookup"><span data-stu-id="ddee4-124">Member</span></span>|<span data-ttu-id="ddee4-125">설명</span><span class="sxs-lookup"><span data-stu-id="ddee4-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ddee4-126">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="ddee4-126">*pwszMessage*</span></span>|<span data-ttu-id="ddee4-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 전달하는 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-127">The error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ddee4-128">이 메시지는 **IErrorInfo::GetDescription** 메서드를 통해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-128">The message is returned through the **IErrorInfo::GetDescription** method.</span></span>|  
|<span data-ttu-id="ddee4-129">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="ddee4-129">*pwszServer*</span></span>|<span data-ttu-id="ddee4-130">오류가 발생한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-130">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which the error occurred.</span></span>|  
|<span data-ttu-id="ddee4-131">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="ddee4-131">*pwszProcedure*</span></span>|<span data-ttu-id="ddee4-132">오류가 저장 프로시저에서 발생한 경우에는 오류를 생성한 저장 프로시저의 이름이고, 그렇지 않으면 빈 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-132">The name of the stored procedure generating the error if the error occurred in a stored procedure; otherwise, an empty string.</span></span>|  
|<span data-ttu-id="ddee4-133">*lNative*</span><span class="sxs-lookup"><span data-stu-id="ddee4-133">*lNative*</span></span>|<span data-ttu-id="ddee4-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number.</span></span> <span data-ttu-id="ddee4-135">오류 번호는 **ISQLErrorInfo::GetSQLInfo** 메서드의 *plNativeError* 매개 변수에 반환되는 번호와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-135">The error number is identical to that returned in the *plNativeError* parameter of the **ISQLErrorInfo::GetSQLInfo** method.</span></span>|  
|<span data-ttu-id="ddee4-136">*bState*</span><span class="sxs-lookup"><span data-stu-id="ddee4-136">*bState*</span></span>|<span data-ttu-id="ddee4-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-137">The state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="ddee4-138">*bClass*</span><span class="sxs-lookup"><span data-stu-id="ddee4-138">*bClass*</span></span>|<span data-ttu-id="ddee4-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류의 심각도입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-139">The severity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="ddee4-140">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="ddee4-140">*wLineNumber*</span></span>|<span data-ttu-id="ddee4-141">해당되는 경우 오류 메시지가 발생한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저의 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-141">When applicable, the line of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure that generated the error message.</span></span> <span data-ttu-id="ddee4-142">저장 프로시저가 연관되지 않은 경우 기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-142">If no procedure is involved, the default value is 1.</span></span>|  
  
 <span data-ttu-id="ddee4-143">*ppErrorStrings* 인수에 반환된 문자열의 구조 참조 주소에 있는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ddee4-143">Pointers in the structure reference addresses in the string returned in the *ppErrorStrings* argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddee4-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddee4-144">See Also</span></span>  
 <span data-ttu-id="ddee4-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="ddee4-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span></span>  
 [<span data-ttu-id="ddee4-146">RAISERROR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ddee4-146">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
