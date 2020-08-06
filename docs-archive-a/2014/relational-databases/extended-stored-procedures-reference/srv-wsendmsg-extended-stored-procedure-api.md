---
title: srv_wsendmsg(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cc915cce0befccb5c5af58e703c11b750af855b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742107"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a><span data-ttu-id="13a85-102">srv_wsendmsg(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="13a85-102">srv_wsendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="13a85-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="13a85-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="13a85-104">클라이언트에 유니코드 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-104">Sends a Unicode message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a85-105">구문</span><span class="sxs-lookup"><span data-stu-id="13a85-105">Syntax</span></span>  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="13a85-106">인수</span><span class="sxs-lookup"><span data-stu-id="13a85-106">Arguments</span></span>  
 <span data-ttu-id="13a85-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="13a85-107">*srvproc*</span></span>  
 <span data-ttu-id="13a85-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="13a85-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="13a85-110">*Msgnum*</span><span class="sxs-lookup"><span data-stu-id="13a85-110">*Msgnum*</span></span>  
 <span data-ttu-id="13a85-111">4바이트 메시지 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-111">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="13a85-112">*심각도*</span><span class="sxs-lookup"><span data-stu-id="13a85-112">*Severity*</span></span>  
 <span data-ttu-id="13a85-113">오류의 심각도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-113">Specifies the severity of the error.</span></span> <span data-ttu-id="13a85-114">심각도가 10보다 작거나 같으면 정보 메시지로 간주되고 그렇지 않으면 오류로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-114">A severity less than or equal to 10 is considered an informational message; otherwise, it is an error.</span></span>  
  
 <span data-ttu-id="13a85-115">*message*</span><span class="sxs-lookup"><span data-stu-id="13a85-115">*message*</span></span>  
 <span data-ttu-id="13a85-116">클라이언트로 보낼 유니코드 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-116">Is a pointer to a Unicode string to be sent to the client.</span></span>  
  
 <span data-ttu-id="13a85-117">*msglen*</span><span class="sxs-lookup"><span data-stu-id="13a85-117">*msglen*</span></span>  
 <span data-ttu-id="13a85-118">*message*의 길이(문자 수)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-118">Specifies the length, in characters, of *message*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="13a85-119">반환</span><span class="sxs-lookup"><span data-stu-id="13a85-119">Returns</span></span>  
 <span data-ttu-id="13a85-120">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="13a85-120">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a85-121">설명</span><span class="sxs-lookup"><span data-stu-id="13a85-121">Remarks</span></span>  
 <span data-ttu-id="13a85-122">이 함수를 사용하여 유니코드로 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-122">Use this function to send messages in Unicode.</span></span> <span data-ttu-id="13a85-123">**srv_sendmsg**와 비슷하지만 DBCHAR 문자열이 아니라 WCHAR 문자열 형식으로 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-123">It is similar to **srv_sendmsg**, but the message it sends is a WCHAR string rather than type DBCHAR string.</span></span> <span data-ttu-id="13a85-124">메시지 길이는 바이트가 아니라 문자 수로 보고되며 *msglen* 은 SRV_NULLTERM일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-124">Note that message length is reported in characters rather than bytes, and *msglen* will never be equal to SRV_NULLTERM.</span></span>  
  
 <span data-ttu-id="13a85-125">이 함수는 다음과 같은 경우 FAIL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-125">The function returns FAIL when</span></span>  
  
-   <span data-ttu-id="13a85-126">지정된 *msglen* 이 0-32242의 범위를 벗어난 경우</span><span class="sxs-lookup"><span data-stu-id="13a85-126">The *msglen* given is not in the range of 0-32242.</span></span>  
  
-   <span data-ttu-id="13a85-127">*msglen* 이 0으로 지정되어 있지만 메시지 포인터가 NULL인 경우</span><span class="sxs-lookup"><span data-stu-id="13a85-127">The *msglen* given is 0 but the message pointer is NULL.</span></span>  
  
-   <span data-ttu-id="13a85-128">네트워크를 통해 오류 메시지를 보낼 때 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="13a85-128">There is error when sending the error message through network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13a85-129">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13a85-129">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="13a85-130">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13a85-130">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a85-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13a85-131">See Also</span></span>  
 [<span data-ttu-id="13a85-132">srv_sendmsg(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="13a85-132">srv_sendmsg &#40;Extended Stored Procedure API&#41;</span></span>](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
