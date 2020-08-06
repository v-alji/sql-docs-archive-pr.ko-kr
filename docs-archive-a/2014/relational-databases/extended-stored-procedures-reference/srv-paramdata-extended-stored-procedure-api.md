---
title: srv_paramdata(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramdata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
author: rothja
ms.author: jroth
ms.openlocfilehash: 092ca5b811a12c3e6b199a6041ce6e4f8e02f4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653388"
---
# <a name="srv_paramdata-extended-stored-procedure-api"></a><span data-ttu-id="0a239-102">srv_paramdata(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="0a239-102">srv_paramdata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0a239-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0a239-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="0a239-104">원격 저장 프로시저 호출 매개 변수의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-104">Returns the value of a remote stored procedure call parameter.</span></span> <span data-ttu-id="0a239-105">이 함수는 **srv_paraminfo** 함수로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a239-106">구문</span><span class="sxs-lookup"><span data-stu-id="0a239-106">Syntax</span></span>  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a239-107">인수</span><span class="sxs-lookup"><span data-stu-id="0a239-107">Arguments</span></span>  
 <span data-ttu-id="0a239-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="0a239-108">*srvproc*</span></span>  
 <span data-ttu-id="0a239-109">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="0a239-110">이 구조에는 확장 저장 프로시저 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-110">The structure contains information the Extended Stored Procedure library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="0a239-111">*n*</span><span class="sxs-lookup"><span data-stu-id="0a239-111">*n*</span></span>  
 <span data-ttu-id="0a239-112">매개 변수의 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-112">Is the number of the parameter.</span></span> <span data-ttu-id="0a239-113">첫 번째 매개 변수의 번호는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-113">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0a239-114">반환</span><span class="sxs-lookup"><span data-stu-id="0a239-114">Returns</span></span>  
 <span data-ttu-id="0a239-115">매개 변수 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-115">A pointer to the parameter value.</span></span> <span data-ttu-id="0a239-116">*n*번째 매개 변수가 NULL이거나, *n*번째 매개 변수가 없거나, 원격 저장 프로시저가 없으면 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-116">If the *n*th parameter is NULL, there is no *n*th parameter, or there is no remote stored procedure, returns NULL.</span></span> <span data-ttu-id="0a239-117">매개 변수 값이 문자열이면 Null로 종결되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-117">If the parameter value is a string, it might not be null-terminated.</span></span> <span data-ttu-id="0a239-118">**srv_paramlen**을 사용하여 문자열 길이를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-118">Use **srv_paramlen** to determine the length of the string.</span></span>  
  
 <span data-ttu-id="0a239-119">매개 변수가 데이터 형식 중 하나인 경우이 함수는 다음 값을 반환 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a239-119">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="0a239-120">포인터 데이터에는 데이터 형식에 대한 포인터가 유효(VP), NULL 또는 해당 사항 없음(N/A)인지 여부와 가리키는 데이터 콘텐츠가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-120">Pointer data includes whether the pointer for the data type is valid (VP), NULL, or not applicable (N/A), and the contents of the data pointed to.</span></span>  
  
|<span data-ttu-id="0a239-121">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="0a239-121">New data types</span></span>|<span data-ttu-id="0a239-122">입력 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="0a239-122">Input data length</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="0a239-123">BITN</span><span class="sxs-lookup"><span data-stu-id="0a239-123">BITN</span></span>|<span data-ttu-id="0a239-124">**NULL:** VP, NULL</span><span class="sxs-lookup"><span data-stu-id="0a239-124">**NULL:** VP, NULL</span></span><br /><br /> <span data-ttu-id="0a239-125">**ZERO:** VP, NULL</span><span class="sxs-lookup"><span data-stu-id="0a239-125">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="0a239-126">**>= 255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-126">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="0a239-127">**<255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-127">**<255:** N/A</span></span>|  
|<span data-ttu-id="0a239-128">BIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="0a239-128">BIGVARCHAR</span></span>|<span data-ttu-id="0a239-129">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-129">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-130">**ZERO:** VP, NULL</span><span class="sxs-lookup"><span data-stu-id="0a239-130">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="0a239-131">**>=255:** VP, 255자</span><span class="sxs-lookup"><span data-stu-id="0a239-131">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="0a239-132">**<255:** VP, 실제 데이터</span><span class="sxs-lookup"><span data-stu-id="0a239-132">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="0a239-133">BIGCHAR</span><span class="sxs-lookup"><span data-stu-id="0a239-133">BIGCHAR</span></span>|<span data-ttu-id="0a239-134">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-134">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-135">**ZERO:** VP, 255개 공백</span><span class="sxs-lookup"><span data-stu-id="0a239-135">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="0a239-136">**>=255:** VP, 255자</span><span class="sxs-lookup"><span data-stu-id="0a239-136">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="0a239-137">**<255:** VP, 실제 데이터 + 패딩(최대 255)</span><span class="sxs-lookup"><span data-stu-id="0a239-137">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="0a239-138">BIGBINARY</span><span class="sxs-lookup"><span data-stu-id="0a239-138">BIGBINARY</span></span>|<span data-ttu-id="0a239-139">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-139">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-140">**ZERO:** VP, 255 0x00</span><span class="sxs-lookup"><span data-stu-id="0a239-140">**ZERO:** VP, 255 0x00</span></span><br /><br /> <span data-ttu-id="0a239-141">**>=255:** VP, 255바이트</span><span class="sxs-lookup"><span data-stu-id="0a239-141">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="0a239-142">**<255:** VP, 실제 데이터 + 패딩(최대 255)</span><span class="sxs-lookup"><span data-stu-id="0a239-142">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="0a239-143">BIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="0a239-143">BIGVARBINARY</span></span>|<span data-ttu-id="0a239-144">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-144">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-145">**ZERO:** VP, 0x00</span><span class="sxs-lookup"><span data-stu-id="0a239-145">**ZERO:** VP, 0x00</span></span><br /><br /> <span data-ttu-id="0a239-146">**>=255:** VP, 255바이트</span><span class="sxs-lookup"><span data-stu-id="0a239-146">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="0a239-147">**<255:** VP, 실제 데이터</span><span class="sxs-lookup"><span data-stu-id="0a239-147">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="0a239-148">NCHAR</span><span class="sxs-lookup"><span data-stu-id="0a239-148">NCHAR</span></span>|<span data-ttu-id="0a239-149">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-149">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-150">**ZERO:** VP, 255개 공백</span><span class="sxs-lookup"><span data-stu-id="0a239-150">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="0a239-151">**>=255:** VP, 255자</span><span class="sxs-lookup"><span data-stu-id="0a239-151">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="0a239-152">**<255:** VP, 실제 데이터 + 패딩(최대 255)</span><span class="sxs-lookup"><span data-stu-id="0a239-152">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="0a239-153">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="0a239-153">NVARCHAR</span></span>|<span data-ttu-id="0a239-154">**NULL:** NULL, 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-154">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="0a239-155">**ZERO:** VP, NULL</span><span class="sxs-lookup"><span data-stu-id="0a239-155">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="0a239-156">**>=255:** VP, 255자</span><span class="sxs-lookup"><span data-stu-id="0a239-156">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="0a239-157">**<255:** VP, 실제 데이터</span><span class="sxs-lookup"><span data-stu-id="0a239-157">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="0a239-158">NTEXT</span><span class="sxs-lookup"><span data-stu-id="0a239-158">NTEXT</span></span>|<span data-ttu-id="0a239-159">**NULL:** 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-159">**NULL:** N/A</span></span><br /><br /> <span data-ttu-id="0a239-160">**ZERO:** 해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-160">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="0a239-161">**>= 255:** 해당 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-161">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="0a239-162">\*\* \< 255:\*\* 해당 없음</span><span class="sxs-lookup"><span data-stu-id="0a239-162">**\<255:** N/A</span></span>|  
  
 <span data-ttu-id="0a239-163">\*   데이터가 Null로 종결되지 않으면 255자보다 큰 데이터 잘림에 대한 경고가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-163">\*   data is not null-terminated; no warning is issued on truncation for data >255 characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a239-164">설명</span><span class="sxs-lookup"><span data-stu-id="0a239-164">Remarks</span></span>  
 <span data-ttu-id="0a239-165">매개 변수 이름을 알고 있으면 **srv_paramnumber**를 사용하여 매개 변수 번호를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-165">If you know the parameter name, you can use **srv_paramnumber** to get the parameter number.</span></span> <span data-ttu-id="0a239-166">매개 변수가 NULL인지 여부를 확인하려면 **srv_paramlen**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-166">To determine whether a parameter is NULL, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="0a239-167">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-167">When a remote stored procedure call is made with parameters, the parameters can be passed by name or by position (unnamed).</span></span> <span data-ttu-id="0a239-168">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-168">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="0a239-169">오류가 발생해도 SRV_RPC 처리기는 계속 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams**는 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-169">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a239-170">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a239-170">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="0a239-171">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a239-171">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a239-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a239-172">See Also</span></span>  
 [<span data-ttu-id="0a239-173">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="0a239-173">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
