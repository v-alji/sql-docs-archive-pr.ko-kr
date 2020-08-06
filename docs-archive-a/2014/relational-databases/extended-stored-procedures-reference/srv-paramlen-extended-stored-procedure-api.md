---
title: srv_paramlen(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
ms.openlocfilehash: fc2a0fa7f8409767a2afaa9c4c621ea72732b701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742131"
---
# <a name="srv_paramlen-extended-stored-procedure-api"></a><span data-ttu-id="326cf-102">srv_paramlen(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="326cf-102">srv_paramlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="326cf-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="326cf-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="326cf-104">원격 저장 프로시저 호출 매개 변수의 데이터 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-104">Returns the data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="326cf-105">이 함수는 **srv_paraminfo** 함수로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="326cf-106">구문</span><span class="sxs-lookup"><span data-stu-id="326cf-106">Syntax</span></span>  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="326cf-107">인수</span><span class="sxs-lookup"><span data-stu-id="326cf-107">Arguments</span></span>  
 <span data-ttu-id="326cf-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="326cf-108">*srvproc*</span></span>  
 <span data-ttu-id="326cf-109">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="326cf-110">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-110">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="326cf-111">*n*</span><span class="sxs-lookup"><span data-stu-id="326cf-111">*n*</span></span>  
 <span data-ttu-id="326cf-112">매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="326cf-113">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="326cf-114">반환</span><span class="sxs-lookup"><span data-stu-id="326cf-114">Returns</span></span>  
 <span data-ttu-id="326cf-115">매개 변수 데이터의 실제 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-115">The actual length, in bytes, of the parameter data.</span></span> <span data-ttu-id="326cf-116">*n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 -1이 반환되고,</span><span class="sxs-lookup"><span data-stu-id="326cf-116">If there is no *n*th parameter or there is no remote stored procedure, it returns -1.</span></span> <span data-ttu-id="326cf-117">*n*번째 매개 변수가 NULL이면 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-117">If the *n*th parameter is NULL, it returns 0.</span></span>  
  
 <span data-ttu-id="326cf-118">매개 변수가 다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 시스템 데이터 형식 중 하나 이면이 함수는 다음 값을 반환 합니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="326cf-118">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] system data types.</span></span>  
  
|<span data-ttu-id="326cf-119">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="326cf-119">New data types</span></span>|<span data-ttu-id="326cf-120">입력 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="326cf-120">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="326cf-121">**NULL:** 1</span><span class="sxs-lookup"><span data-stu-id="326cf-121">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="326cf-122">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="326cf-122">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="326cf-123">**>= 255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="326cf-123">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="326cf-124">**<255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="326cf-124">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="326cf-125">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-125">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-126">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="326cf-126">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="326cf-127">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-127">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-128">**<255:** 실제 *len*</span><span class="sxs-lookup"><span data-stu-id="326cf-128">**<255:** actual *len*</span></span>|  
|`BIGCHAR`|<span data-ttu-id="326cf-129">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-129">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-130">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-130">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="326cf-131">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-131">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-132">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-132">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="326cf-133">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-133">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-134">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-134">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="326cf-135">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-135">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-136">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-136">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="326cf-137">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-137">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-138">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="326cf-138">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="326cf-139">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-139">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-140">**<255:** 실제 *len*</span><span class="sxs-lookup"><span data-stu-id="326cf-140">**<255:** actual *len*</span></span>|  
|`NCHAR`|<span data-ttu-id="326cf-141">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-141">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-142">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-142">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="326cf-143">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-143">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-144">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-144">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="326cf-145">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="326cf-145">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="326cf-146">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="326cf-146">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="326cf-147">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="326cf-147">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="326cf-148">**<255:** 실제 *len*</span><span class="sxs-lookup"><span data-stu-id="326cf-148">**<255:** actual *len*</span></span>|  
|`NTEXT`|<span data-ttu-id="326cf-149">**NULL:** -1</span><span class="sxs-lookup"><span data-stu-id="326cf-149">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="326cf-150">**ZERO:** -1</span><span class="sxs-lookup"><span data-stu-id="326cf-150">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="326cf-151">**>= 255:** -1</span><span class="sxs-lookup"><span data-stu-id="326cf-151">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="326cf-152">**<255:** -1</span><span class="sxs-lookup"><span data-stu-id="326cf-152">**<255:** -1</span></span>|  
  
 <span data-ttu-id="326cf-153">\*   실제 *len* = 멀티바이트 문자열(cch)의 길이</span><span class="sxs-lookup"><span data-stu-id="326cf-153">\*   actual *len* = Length of multibyte character string (cch)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="326cf-154">설명</span><span class="sxs-lookup"><span data-stu-id="326cf-154">Remarks</span></span>  
 <span data-ttu-id="326cf-155">각 원격 저장 프로시저 매개 변수에는 실제 데이터 길이와 최대 데이터 길이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-155">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="326cf-156">Null 값을 사용할 수 없는 고정 길이의 표준 데이터 형식의 경우 실제 길이와 최대 길이가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-156">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="326cf-157">가변 길이의 데이터 형식의 경우 데이터 길이가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-157">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="326cf-158">예를 들어 `varchar(30)`로 선언한 매개 변수의 데이터 길이는 최대 10바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-158">For example, a parameter declared as `varchar(30)` can have data that is only 10 bytes long.</span></span> <span data-ttu-id="326cf-159">이 매개 변수의 실제 길이는 10이고 최대 길이는 30입니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-159">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="326cf-160">**srv_paramlen** 함수는 원격 저장 프로시저의 실제 데이터 길이(바이트)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-160">The **srv_paramlen** function gets the actual data length, in bytes, of a remote stored procedure.</span></span> <span data-ttu-id="326cf-161">매개 변수의 최대 데이터 길이를 가져오려면 **srv_parammaxlen**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-161">To obtain the maximum data length of a parameter, use **srv_parammaxlen**.</span></span>  
  
 <span data-ttu-id="326cf-162">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-162">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="326cf-163">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-163">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="326cf-164">SRV_RPC 처리기는 계속 호출 되지만 매개 변수가 없고 **srv_rpcparams** 0을 반환 하는 것 처럼 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-164">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="326cf-165">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="326cf-165">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="326cf-166">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="326cf-166">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326cf-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="326cf-167">See Also</span></span>  
 <span data-ttu-id="326cf-168">[srv_paraminfo &#40;확장 저장 프로시저 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="326cf-168">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="326cf-169">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="326cf-169">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
