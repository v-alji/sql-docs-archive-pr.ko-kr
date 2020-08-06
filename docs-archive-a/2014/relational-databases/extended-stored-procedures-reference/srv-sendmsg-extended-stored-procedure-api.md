---
title: srv_sendmsg(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 0821ad88f48313cfadea634a489def9b242a49f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743235"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a><span data-ttu-id="3af41-102">srv_sendmsg(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="3af41-102">srv_sendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="3af41-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3af41-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="3af41-104">클라이언트에 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-104">Sends a message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af41-105">구문</span><span class="sxs-lookup"><span data-stu-id="3af41-105">Syntax</span></span>  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="3af41-106">인수</span><span class="sxs-lookup"><span data-stu-id="3af41-106">Arguments</span></span>  
 <span data-ttu-id="3af41-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="3af41-107">*srvproc*</span></span>  
 <span data-ttu-id="3af41-108">특정 클라이언트 연결에 대한 핸들(이 경우 언어 요청을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="3af41-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="3af41-110">*msgtype*</span><span class="sxs-lookup"><span data-stu-id="3af41-110">*msgtype*</span></span>  
 <span data-ttu-id="3af41-111">서버에서 정보 메시지 또는 오류 메시지를 보내는지에 따라 SRV_MSG_INFO 또는 SRV_MSG_ERROR가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-111">Is either SRV_MSG_INFO or SRV_MSG_ERROR, depending on whether the server is sending an informational or error message.</span></span>  
  
 <span data-ttu-id="3af41-112">*msgnum*</span><span class="sxs-lookup"><span data-stu-id="3af41-112">*msgnum*</span></span>  
 <span data-ttu-id="3af41-113">4바이트 메시지 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-113">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="3af41-114">*class*</span><span class="sxs-lookup"><span data-stu-id="3af41-114">*class*</span></span>  
 <span data-ttu-id="3af41-115">오류 심각도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-115">Specifies the error severity.</span></span> <span data-ttu-id="3af41-116">심각도가 10보다 작거나 같으면 정보 메시지로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-116">A severity less than or equal to 10 is considered an informational message.</span></span>  
  
 <span data-ttu-id="3af41-117">*상태*</span><span class="sxs-lookup"><span data-stu-id="3af41-117">*state*</span></span>  
 <span data-ttu-id="3af41-118">현재 메시지의 오류 상태 번호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-118">Provides the error state number for the current message.</span></span> <span data-ttu-id="3af41-119">이 오류 상태 번호는 오류의 컨텍스트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-119">The error state number provides information about the context of the error.</span></span> <span data-ttu-id="3af41-120">유효한 상태 번호는 0에서 255까지입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-120">Valid state numbers are from 0 through 255.</span></span>  
  
 <span data-ttu-id="3af41-121">*rpcname*</span><span class="sxs-lookup"><span data-stu-id="3af41-121">*rpcname*</span></span>  
 <span data-ttu-id="3af41-122">현재 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-122">Is currently not supported.</span></span>  
  
 <span data-ttu-id="3af41-123">*rpcnamelen*</span><span class="sxs-lookup"><span data-stu-id="3af41-123">*rpcnamelen*</span></span>  
 <span data-ttu-id="3af41-124">현재 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-124">Is currently not supported.</span></span>  
  
 <span data-ttu-id="3af41-125">*linenum*</span><span class="sxs-lookup"><span data-stu-id="3af41-125">*linenum*</span></span>  
 <span data-ttu-id="3af41-126">언어 명령 일괄 처리에서 메시지가 적용되는 줄 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-126">Is the line number in the language command batch where the message applies.</span></span> <span data-ttu-id="3af41-127">줄 번호는 1부터 시작하며</span><span class="sxs-lookup"><span data-stu-id="3af41-127">Line numbers start at 1.</span></span> <span data-ttu-id="3af41-128">메시지에 *linenum*이 적용되지 않으면 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-128">If *linenum* does not apply to the message, set to 0.</span></span>  
  
 <span data-ttu-id="3af41-129">*message*</span><span class="sxs-lookup"><span data-stu-id="3af41-129">*message*</span></span>  
 <span data-ttu-id="3af41-130">클라이언트로 보낼 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-130">Is a pointer to the character string to be sent to the client.</span></span>  
  
 <span data-ttu-id="3af41-131">*msglen*</span><span class="sxs-lookup"><span data-stu-id="3af41-131">*msglen*</span></span>  
 <span data-ttu-id="3af41-132">*message*의 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-132">Specifies the length, in bytes, of *message*.</span></span> <span data-ttu-id="3af41-133">*message*가 Null로 끝나는 경우 *msglen*을 SRV_NULLTERM으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-133">If *message* is null-terminated, set *msglen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="3af41-134">반환</span><span class="sxs-lookup"><span data-stu-id="3af41-134">Returns</span></span>  
 <span data-ttu-id="3af41-135">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="3af41-135">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3af41-136">설명</span><span class="sxs-lookup"><span data-stu-id="3af41-136">Remarks</span></span>  
 <span data-ttu-id="3af41-137">클라이언트에 오류 메시지 또는 정보 메시지를 보내는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-137">This function sends error or informational messages to the client.</span></span> <span data-ttu-id="3af41-138">보낼 각 메시지에 대해 한 번씩 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-138">It is called once for each message to be sent.</span></span>  
  
 <span data-ttu-id="3af41-139">**srv_sendrow**를 사용하여 모든 행(있는 경우)을 보내기 전후에 **srv_sendmsg**를 사용하여 순서에 상관없이 클라이언트에 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-139">Messages can be sent to the client with **srv_sendmsg** in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="3af41-140">**srv_senddone**을 사용하여 완료 상태를 보내기 전에는 모든 메시지(있는 경우)를 클라이언트로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-140">All messages, if any, must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
 <span data-ttu-id="3af41-141">메시지를 유니코드로 보내려면 **srv_sendmsg** 대신 **srv_wsendmsg**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-141">To send messages in Unicode, use **srv_wsendmsg** rather than **srv_sendmsg**.</span></span>  
  
 <span data-ttu-id="3af41-142">자세한 내용은 [유니코드 데이터 및 서버 코드 페이지](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3af41-142">For more information see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3af41-143">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3af41-143">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="3af41-144">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3af41-144">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
