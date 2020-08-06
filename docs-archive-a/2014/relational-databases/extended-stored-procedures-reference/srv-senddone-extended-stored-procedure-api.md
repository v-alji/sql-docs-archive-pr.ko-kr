---
title: srv_senddone(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 877acdc1b666c7f4cbaab737590a1c55e474eb05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743239"
---
# <a name="srv_senddone-extended-stored-procedure-api"></a><span data-ttu-id="31b34-102">srv_senddone(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="31b34-102">srv_senddone (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="31b34-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="31b34-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="31b34-104">결과 완료 메시지를 클라이언트에게 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-104">Sends a result completion message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b34-105">구문</span><span class="sxs-lookup"><span data-stu-id="31b34-105">Syntax</span></span>  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="31b34-106">인수</span><span class="sxs-lookup"><span data-stu-id="31b34-106">Arguments</span></span>  
 <span data-ttu-id="31b34-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="31b34-107">*srvproc*</span></span>  
 <span data-ttu-id="31b34-108">특정 클라이언트 연결에 대한 핸들(이 경우 언어 요청을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="31b34-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="31b34-110">*status*</span><span class="sxs-lookup"><span data-stu-id="31b34-110">*status*</span></span>  
 <span data-ttu-id="31b34-111">다양한 *status* 플래그에 대한 2바이트 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-111">Is a 2-byte field for various *status* flags.</span></span> <span data-ttu-id="31b34-112">*status* 플래그 값에 AND 및 OR 논리 연산자를 사용하여 여러 플래그를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-112">Multiple flags can be set by using the AND and OR logical operators with *status* flag values.</span></span> <span data-ttu-id="31b34-113">다음 표에서는 가능한 *status* 플래그를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-113">The following table lists possible *status* flags.</span></span>  
  
|<span data-ttu-id="31b34-114">상태 플래그</span><span class="sxs-lookup"><span data-stu-id="31b34-114">Status flag</span></span>|<span data-ttu-id="31b34-115">설명</span><span class="sxs-lookup"><span data-stu-id="31b34-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="31b34-116">SRV_DONE_COUNT</span><span class="sxs-lookup"><span data-stu-id="31b34-116">SRV_DONE_COUNT</span></span>|<span data-ttu-id="31b34-117">*count* 매개 변수에 올바른 개수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-117">The *count* parameter contains a valid count.</span></span>|  
|<span data-ttu-id="31b34-118">SRV_DONE_ERROR</span><span class="sxs-lookup"><span data-stu-id="31b34-118">SRV_DONE_ERROR</span></span>|<span data-ttu-id="31b34-119">현재 클라이언트 명령에 오류가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-119">The current client command received an error.</span></span>|  
  
 <span data-ttu-id="31b34-120">*정보*</span><span class="sxs-lookup"><span data-stu-id="31b34-120">*info*</span></span>  
 <span data-ttu-id="31b34-121">예약된 2바이트 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-121">Is a reserved, 2-byte field.</span></span> <span data-ttu-id="31b34-122">이 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-122">Set this value to 0.</span></span>  
  
 <span data-ttu-id="31b34-123">*count*</span><span class="sxs-lookup"><span data-stu-id="31b34-123">*count*</span></span>  
 <span data-ttu-id="31b34-124">현재 결과 집합의 개수를 나타내는 데 사용되는 4바이트 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-124">Is a 4-byte field used to indicate a count for the current result set.</span></span> <span data-ttu-id="31b34-125">*status* 필드에 SRV_DONE_COUNT 플래그를 설정하면 *count* 에 올바른 개수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-125">If the SRV_DONE_COUNT flag is set in the *status* field, *count* holds a valid count.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="31b34-126">반환</span><span class="sxs-lookup"><span data-stu-id="31b34-126">Returns</span></span>  
 <span data-ttu-id="31b34-127">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="31b34-127">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31b34-128">설명</span><span class="sxs-lookup"><span data-stu-id="31b34-128">Remarks</span></span>  
 <span data-ttu-id="31b34-129">클라이언트 요청으로 인해 서버에서 많은 명령을 실행하고 많은 결과 집합을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-129">A client request can cause the server to execute a number of commands and to return a number of result sets.</span></span> <span data-ttu-id="31b34-130">각 결과 집합에 대해 **srv_senddone** 에서 결과 완료 메시지를 클라이언트에 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-130">For each result set, **srv_senddone** must return a result completion message to the client.</span></span>  
  
 <span data-ttu-id="31b34-131">*count* 필드는 명령의 영향을 받는 행 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-131">The *count* field indicates the number of rows affected by a command.</span></span> <span data-ttu-id="31b34-132">*count* 필드에 개수가 포함되어 있는 경우 *status* 필드에 SRV_DONE_COUNT 플래그를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-132">If the *count* field contains a count, the SRV_DONE_COUNT flag should be set in the *status* field.</span></span> <span data-ttu-id="31b34-133">이 설정을 사용하면 클라이언트에서 *count* 값 0과 사용되지 않은 *count* 필드를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-133">This setting allows the client to distinguish between a *count* value of 0 and an unused *count* field.</span></span>  
  
 <span data-ttu-id="31b34-134">SRV_CONNECT 처리기에서 **srv_senddone** 을 호출하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="31b34-134">Do not call **srv_senddone** from the SRV_CONNECT handler.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="31b34-135">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31b34-135">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="31b34-136">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31b34-136">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
