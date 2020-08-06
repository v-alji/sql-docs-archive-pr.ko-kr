---
title: srv_parammaxlen(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_parammaxlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: b289743b3de4b115a67a029dcc0261854ee3a40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742127"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a><span data-ttu-id="428aa-102">srv_parammaxlen(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="428aa-102">srv_parammaxlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="428aa-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="428aa-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="428aa-104">원격 저장 프로시저 호출 매개 변수의 최대 데이터 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-104">Returns the maximum data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="428aa-105">이 함수는 **srv_paraminfo** 함수로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428aa-106">구문</span><span class="sxs-lookup"><span data-stu-id="428aa-106">Syntax</span></span>  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="428aa-107">인수</span><span class="sxs-lookup"><span data-stu-id="428aa-107">Arguments</span></span>  
 <span data-ttu-id="428aa-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="428aa-108">*srvproc*</span></span>  
 <span data-ttu-id="428aa-109">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="428aa-110">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="428aa-111">*n*</span><span class="sxs-lookup"><span data-stu-id="428aa-111">*n*</span></span>  
 <span data-ttu-id="428aa-112">매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="428aa-113">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="428aa-114">반환</span><span class="sxs-lookup"><span data-stu-id="428aa-114">Returns</span></span>  
 <span data-ttu-id="428aa-115">매개 변수 데이터의 최대 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-115">The maximum length, in bytes, of the parameter data.</span></span> <span data-ttu-id="428aa-116">*n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 -1이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
 <span data-ttu-id="428aa-117">매개 변수가 다음 데이터 형식 중 하나 이면이 함수는 다음 값을 반환 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="428aa-117">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
|<span data-ttu-id="428aa-118">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="428aa-118">New data types</span></span>|<span data-ttu-id="428aa-119">입력 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="428aa-119">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="428aa-120">**NULL:** 1</span><span class="sxs-lookup"><span data-stu-id="428aa-120">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="428aa-121">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="428aa-121">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="428aa-122">**>= 255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="428aa-122">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="428aa-123">**<255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="428aa-123">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="428aa-124">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-124">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-125">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-125">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-126">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-126">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-127">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-127">**<255:** 255</span></span>|  
|`BIGCHAR`|<span data-ttu-id="428aa-128">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-128">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-129">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-129">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-130">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-130">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-131">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-131">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="428aa-132">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-132">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-133">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-133">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-134">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-134">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-135">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-135">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="428aa-136">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-136">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-137">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-137">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-138">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-138">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-139">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-139">**<255:** 255</span></span>|  
|`NCHAR`|<span data-ttu-id="428aa-140">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-140">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-141">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-141">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-142">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-142">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-143">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-143">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="428aa-144">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-144">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="428aa-145">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-145">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="428aa-146">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-146">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="428aa-147">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="428aa-147">**<255:** 255</span></span>|  
|`NTEXT`|<span data-ttu-id="428aa-148">**NULL:** -1</span><span class="sxs-lookup"><span data-stu-id="428aa-148">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="428aa-149">**ZERO:** -1</span><span class="sxs-lookup"><span data-stu-id="428aa-149">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="428aa-150">**>= 255:** -1</span><span class="sxs-lookup"><span data-stu-id="428aa-150">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="428aa-151">\*\* \< 255:\*\* -1</span><span class="sxs-lookup"><span data-stu-id="428aa-151">**\<255:** -1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="428aa-152">설명</span><span class="sxs-lookup"><span data-stu-id="428aa-152">Remarks</span></span>  
 <span data-ttu-id="428aa-153">각 원격 저장 프로시저 매개 변수에는 실제 데이터 길이와 최대 데이터 길이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-153">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="428aa-154">Null 값을 사용할 수 없는 고정 길이의 표준 데이터 형식의 경우 실제 길이와 최대 길이가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-154">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="428aa-155">가변 길이의 데이터 형식의 경우 데이터 길이가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-155">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="428aa-156">예를 들어 **varchar(30)** 로 선언한 매개 변수의 데이터 길이는 최대 10바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-156">For example, a parameter declared as **varchar(30)** can have data that is only 10 bytes long.</span></span> <span data-ttu-id="428aa-157">이 매개 변수의 실제 길이는 10이고 최대 길이는 30입니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-157">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="428aa-158">**srv_parammaxlen** 함수는 원격 저장 프로시저의 최대 데이터 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-158">The **srv_parammaxlen** function gets the maximum data length of a remote stored procedure.</span></span> <span data-ttu-id="428aa-159">매개 변수의 실제 길이를 가져오려면 **srv_paramlen**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-159">To obtain the actual length of a parameter, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="428aa-160">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-160">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="428aa-161">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-161">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="428aa-162">이 경우에도 SRV_RPC 핸들러는 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams**는 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-162">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="428aa-163">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428aa-163">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="428aa-164">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="428aa-164">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428aa-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="428aa-165">See Also</span></span>  
 <span data-ttu-id="428aa-166">[srv_paraminfo &#40;확장 저장 프로시저 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="428aa-166">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="428aa-167">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="428aa-167">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
