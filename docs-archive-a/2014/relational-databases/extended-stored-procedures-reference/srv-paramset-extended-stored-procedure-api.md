---
title: srv_paramset(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramset
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ebe308e5e0c8fc24382582fb71db2f48c77541e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647014"
---
# <a name="srv_paramset-extended-stored-procedure-api"></a><span data-ttu-id="41a95-102">srv_paramset(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="41a95-102">srv_paramset (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="41a95-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="41a95-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="41a95-104">원격 저장 프로시저 호출 반환 매개 변수의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-104">Sets the value of a remote stored procedure call return parameter.</span></span> <span data-ttu-id="41a95-105">이 함수는 **srv_paramsetoutput** 함수로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-105">This function has been superseded by the **srv_paramsetoutput** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a95-106">구문</span><span class="sxs-lookup"><span data-stu-id="41a95-106">Syntax</span></span>  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="41a95-107">인수</span><span class="sxs-lookup"><span data-stu-id="41a95-107">Arguments</span></span>  
 <span data-ttu-id="41a95-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="41a95-108">*srvproc*</span></span>  
 <span data-ttu-id="41a95-109">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="41a95-110">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="41a95-111">*n*</span><span class="sxs-lookup"><span data-stu-id="41a95-111">*n*</span></span>  
 <span data-ttu-id="41a95-112">설정할 매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-112">Indicates the number of the parameter to set.</span></span> <span data-ttu-id="41a95-113">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="41a95-114">*data*</span><span class="sxs-lookup"><span data-stu-id="41a95-114">*data*</span></span>  
 <span data-ttu-id="41a95-115">원격 저장 프로시저에서 매개 변수를 반환할 때 다시 클라이언트로 전달될 데이터 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-115">Is a pointer to the data value to be sent back to the client as the remote stored procedure return parameter.</span></span>  
  
 <span data-ttu-id="41a95-116">*길이가*</span><span class="sxs-lookup"><span data-stu-id="41a95-116">*len*</span></span>  
 <span data-ttu-id="41a95-117">반환할 데이터의 실제 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-117">Specifies the actual length of the data to be returned.</span></span> <span data-ttu-id="41a95-118">매개 변수의 데이터 형식이 상수 길이이고 Null 값을 허용하지 않는 경우(예: *srvbit* 또는 *srvint1*) *len*이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-118">If the data type of the parameter is of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *len* is ignored.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="41a95-119">반환</span><span class="sxs-lookup"><span data-stu-id="41a95-119">Returns</span></span>  
 <span data-ttu-id="41a95-120">매개 변수 값이 성공적으로 설정된 경우 SUCCEED이고, 그렇지 않으면 FAIL입니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-120">SUCCEED if the parameter value was successfully set; otherwise, FAIL.</span></span> <span data-ttu-id="41a95-121">현재 원격 저장 프로시저가 없는 경우, *n*번째 원격 저장 프로시저 매개 변수가 없는 경우, 매개 변수가 반환 매개 변수가 아닌 경우 및 *len* 인수가 유효하지 않은 경우 FAIL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-121">FAIL is returned when there is no current remote stored procedure, when there is no *n*th remote stored procedure parameter, when the parameter is not a return parameter, and when the *len* argument is not legal.</span></span>  
  
 <span data-ttu-id="41a95-122">*len*이 0이면 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-122">If *len*is 0, it returns NULL.</span></span> <span data-ttu-id="41a95-123">*len*을 0으로 설정해야만 클라이언트에 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-123">Setting *len* to 0 is the only way to return NULL to the client.</span></span>  
  
 <span data-ttu-id="41a95-124">매개 변수가 데이터 형식 중 하나인 경우이 함수는 다음 값을 반환 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="41a95-124">This function returns the following values, if the parameter is one of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="41a95-125">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="41a95-125">New data types</span></span>|<span data-ttu-id="41a95-126">반환 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="41a95-126">Return data length</span></span>|  
|--------------------|------------------------|  
|`BITN`|<span data-ttu-id="41a95-127">**NULL:** *len* = 0, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-127">**NULL:** *len* = 0, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-128">**ZERO:** 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="41a95-128">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="41a95-129">**>= 255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="41a95-129">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="41a95-130">**<255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="41a95-130">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="41a95-131">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-131">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-132">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-132">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-133">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-133">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-134">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-134">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGCHAR`|<span data-ttu-id="41a95-135">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-135">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-136">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-136">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-137">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-137">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-138">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-138">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGBINARY`|<span data-ttu-id="41a95-139">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-139">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-140">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-140">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-141">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-141">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-142">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-142">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="41a95-143">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-143">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-144">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-144">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-145">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-145">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-146">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-146">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="41a95-147">NCHAR</span><span class="sxs-lookup"><span data-stu-id="41a95-147">NCHAR</span></span>|<span data-ttu-id="41a95-148">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-148">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-149">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-149">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-150">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-150">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-151">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-151">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="41a95-152">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="41a95-152">NVARCHAR</span></span>|<span data-ttu-id="41a95-153">**NULL:** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-153">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="41a95-154">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-154">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-155">**>=255:** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-155">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-156">**<255:** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="41a95-156">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`NTEXT`|<span data-ttu-id="41a95-157">**NULL:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-157">**NULL:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-158">**ZERO:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-158">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-159">**>=255:** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-159">**>=255:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="41a95-160">\*\* \< 255:\*\* *len* = ig, data = ig, RET = 0</span><span class="sxs-lookup"><span data-stu-id="41a95-160">**\<255:** *len* = IG, data = IG, RET = 0</span></span>|  
|<span data-ttu-id="41a95-161">RET = srv_paramset의 반환 값</span><span class="sxs-lookup"><span data-stu-id="41a95-161">RET = Return value of srv_paramset</span></span>||  
|<span data-ttu-id="41a95-162">IG = 값이 무시됨</span><span class="sxs-lookup"><span data-stu-id="41a95-162">IG = Value will be ignored</span></span>||  
|<span data-ttu-id="41a95-163">valid = 데이터에 대한 유효한 포인터</span><span class="sxs-lookup"><span data-stu-id="41a95-163">valid = Any valid pointer to data</span></span>||  
  
## <a name="remarks"></a><span data-ttu-id="41a95-164">설명</span><span class="sxs-lookup"><span data-stu-id="41a95-164">Remarks</span></span>  
 <span data-ttu-id="41a95-165">매개 변수에는 원격 저장 프로시저를 사용하여 클라이언트와 애플리케이션 간에 전달되는 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-165">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="41a95-166">클라이언트는 특정 매개 변수를 반환 매개 변수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-166">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="41a95-167">이러한 반환 매개 변수에는 개방형 Data Services 서버 애플리케이션이 다시 클라이언트에 전달하는 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-167">These return parameters can contain values that the Open Data Services server application passes back to the client.</span></span> <span data-ttu-id="41a95-168">반환 매개 변수를 사용하는 것은 참조로 매개 변수를 전달하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-168">Using return parameters is analogous to passing parameters by reference.</span></span>  
  
 <span data-ttu-id="41a95-169">반환 매개 변수로 호출되지 않은 매개 변수에 대해서는 반환 값을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-169">You cannot set the return value for a parameter that wasn't invoked as a return parameter.</span></span> <span data-ttu-id="41a95-170">**srv_paramstatus**를 사용하여 매개 변수가 호출된 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-170">You can use **srv_paramstatus** to determine how the parameter was invoked.</span></span>  
  
 <span data-ttu-id="41a95-171">이 함수는 매개 변수의 반환 값을 설정하지만 실제로 반환 값을 클라이언트에 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-171">This function sets the return value for a parameter but it does not actually send the return value to the client.</span></span> <span data-ttu-id="41a95-172">**srv_paramset**으로 반환 값이 설정되었는지 여부에 관계없이 상태 플래그 SRV_DONE_FINAL이 설정된 상태로 **srv_senddone**을 호출하면 모든 반환 매개 변수가 자동으로 클라이언트에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-172">All return parameters, whether their return values have been set with **srv_paramset** or not, are automatically sent to the client when **srv_senddone** is called with the status flag SRV_DONE_FINAL set.</span></span>  
  
 <span data-ttu-id="41a95-173">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-173">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="41a95-174">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-174">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="41a95-175">이 경우에도 SRV_RPC 핸들러는 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams**는 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-175">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="41a95-176">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a95-176">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="41a95-177">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="41a95-177">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a95-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41a95-178">See Also</span></span>  
 [<span data-ttu-id="41a95-179">srv_paramsetoutput(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="41a95-179">srv_paramsetoutput &#40;Extended Stored Procedure API&#41;</span></span>](srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
