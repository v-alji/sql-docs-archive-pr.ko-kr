---
title: srv_getbindtoken(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_getbindtoken
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_getbindtoken
ms.assetid: c947d011-08ac-4fb8-b925-3da6e0999277
author: rothja
ms.author: jroth
ms.openlocfilehash: d42f95c8a7df87f20ebaa30501b96b5f2a00815a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660576"
---
# <a name="srv_getbindtoken-extended-stored-procedure-api"></a><span data-ttu-id="d7d4e-102">srv_getbindtoken(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="d7d4e-102">srv_getbindtoken (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d7d4e-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d7d4e-104">현재 클라이언트 세션의 트랜잭션에서 확장 저장 프로시저를 호출하는 바인드 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-104">Obtains a bind token of the transaction in the current client session that invokes the extended stored procedure.</span></span>  
  
 <span data-ttu-id="d7d4e-105">바인드 토큰을 가져오면 확장 저장 프로시저는 **sp_bindsession**을 사용하여 같은 서버에 대해 새로 만드는 모든 세션을 기존 트랜잭션에 바인딩할 수 있습니다. 이렇게 하면 새 세션은 확장 저장 프로시저를 호출한 클라이언트 세션과 동일한 트랜잭션 잠금 공간을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-105">The extended stored procedure can then use **sp_bindsession** to bind any new session it creates against the same server to the existing transaction so that the new session can share the same transaction lock space with the client session that invoked the extended stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d4e-106">구문</span><span class="sxs-lookup"><span data-stu-id="d7d4e-106">Syntax</span></span>  
  
```  
  
int srv_getbindtoken (  
SRV_PROC*  
srvproc  
,  
char*  
bindtoken  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7d4e-107">인수</span><span class="sxs-lookup"><span data-stu-id="d7d4e-107">Arguments</span></span>  
 <span data-ttu-id="d7d4e-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="d7d4e-108">*srvproc*</span></span>  
 <span data-ttu-id="d7d4e-109">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="d7d4e-110">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 모든 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-110">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="d7d4e-111">*bindtoken*</span><span class="sxs-lookup"><span data-stu-id="d7d4e-111">*bindtoken*</span></span>  
 <span data-ttu-id="d7d4e-112">바인드 토큰이 복사될 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-112">Is a pointer to a buffer where the bind token will be copied.</span></span> <span data-ttu-id="d7d4e-113">바인드 토큰은 null로 끝나는 문자열로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-113">The bind token is represented as a null-terminated string.</span></span> <span data-ttu-id="d7d4e-114">지정하는 버퍼의 길이는 255바이트 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-114">The buffer you specify should be at least 255 bytes in length.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d7d4e-115">반환</span><span class="sxs-lookup"><span data-stu-id="d7d4e-115">Returns</span></span>  
 <span data-ttu-id="d7d4e-116">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="d7d4e-116">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d4e-117">설명</span><span class="sxs-lookup"><span data-stu-id="d7d4e-117">Remarks</span></span>  
  
### <a name="to-bind-an-extended-stored-procedure-session-to-the-client-session-that-called-it-so-they-share-the-same-transaction-lock-space"></a><span data-ttu-id="d7d4e-118">동일한 트랜잭션 잠금 공간을 공유하도록 확장 저장 프로시저를 호출한 클라이언트 세션에 확장 저장 프로시저 세션을 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="d7d4e-118">To bind an extended stored procedure session to the client session that called it so they share the same transaction lock space</span></span>  
  
1.  <span data-ttu-id="d7d4e-119">확장 저장 프로시저에서 **svr_getbindtoken**을 호출하여 세션의 현재 트랜잭션에 대한 바인드 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-119">The extended stored procedure calls **svr_getbindtoken** to get the bind token for the current transaction in the session.</span></span> <span data-ttu-id="d7d4e-120">토큰은 지정된 *bindtoken* 매개 변수로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-120">The token is returned in the given *bindtoken* parameter.</span></span>  
  
2.  <span data-ttu-id="d7d4e-121">확장 저장 프로시저에서 동일한 서버에 대해 새로운 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-121">The extended stored procedure opens new session(s) against the same server.</span></span> <span data-ttu-id="d7d4e-122">이 세션에서 확장 저장 프로시저는 **sp_bindsession**에 바인드 토큰을 사용하여 새 세션을 동일한 트랜잭션에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-122">Inside that session, the extended stored procedure uses the bind token with **sp_bindsession** to bind the new session to the same transaction.</span></span> <span data-ttu-id="d7d4e-123">확장 저장 프로시저에서는 세션을 여러 개 만든 다음 모든 세션을 같은 트랜잭션에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-123">The extended stored procedure can create multiple sessions and bind all the sessions to the same transaction.</span></span>  
  
3.  <span data-ttu-id="d7d4e-124">외부 저장 프로시저가 반환되거나, 빈 문자열을 사용하여 **sp_bindsession**을 호출하면 바인딩된 세션이 바인딩 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-124">A bound session is unbound when the external stored procedure returns or when **sp_bindsession** is called with an empty string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7d4e-125">한 번에 하나의 바인딩된 세션만 공유 연결에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-125">Only one bound session at a time can have access to a shared connection.</span></span> <span data-ttu-id="d7d4e-126">특정 세션이 서버에서 문을 실행하고 있거나, 서버로부터 보류 중인 결과가 있으면 바인딩된 동일한 연결을 공유하는 다른 세션에서는 현재 세션이 현재 문의 실행을 완료할 때까지 서버에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-126">If one session is currently executing a statement at the server or has results pending from the server, no other sessions sharing the same bound connection can gain access to the server until the current session has finished executing the current statement.</span></span> <span data-ttu-id="d7d4e-127">서버가 작업 중일 때 특정 세션이 연결에 액세스하려고 시도하면 연결이 사용 중이므로 나중에 다시 시도하라는 오류가 해당 세션에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-127">If a session attempts to gain access to the connection while the server is busy, an error is returned to the conflicting session indicating the connection is in use and the session should retry later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d7d4e-128">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-128">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d7d4e-129">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7d4e-129">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d4e-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7d4e-130">See Also</span></span>  
 <span data-ttu-id="d7d4e-131">[sp_bindsession&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d7d4e-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 [<span data-ttu-id="d7d4e-132">sp_getbindtoken&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d7d4e-132">sp_getbindtoken &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)  
  
  
