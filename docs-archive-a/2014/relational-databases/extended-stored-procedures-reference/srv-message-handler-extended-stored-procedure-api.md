---
title: srv_message_handler(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e7b6472ed4fabb6dc2d545eb51a1e026635ce19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648392"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a><span data-ttu-id="46cef-102">srv_message_handler(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="46cef-102">srv_message_handler (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="46cef-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="46cef-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="46cef-104">설치된 확장 저장 프로시저 API 메시지 처리기를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-104">Calls the installed Extended Stored Procedure API message handler.</span></span> <span data-ttu-id="46cef-105">이 함수는 일반적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 저장 프로시저에서를 호출 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그 파일이 나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 응용 프로그램 로그에 확장 저장 프로시저에 정의 된 오류를 기록 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-105">This function is usually used to call [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an extended stored procedure to log an error (defined by the extended stored procedure) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log file or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46cef-106">구문</span><span class="sxs-lookup"><span data-stu-id="46cef-106">Syntax</span></span>  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="46cef-107">인수</span><span class="sxs-lookup"><span data-stu-id="46cef-107">Arguments</span></span>  
 <span data-ttu-id="46cef-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="46cef-108">*srvproc*</span></span>  
 <span data-ttu-id="46cef-109">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="46cef-110">*srvproc* 매개 변수에는 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용되는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-110">The *srvproc* parameter contains information that is used to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="46cef-111">*errornum*</span><span class="sxs-lookup"><span data-stu-id="46cef-111">*errornum*</span></span>  
 <span data-ttu-id="46cef-112">확장 저장 프로시저에 정의된 오류 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-112">Is an error number defined by the extended stored procedure.</span></span> <span data-ttu-id="46cef-113">이 숫자는 50,001과 2,147,483,647 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-113">This number must be from 50,001 through 2,147,483,647.</span></span>  
  
 <span data-ttu-id="46cef-114">*severity*</span><span class="sxs-lookup"><span data-stu-id="46cef-114">*severity*</span></span>  
 <span data-ttu-id="46cef-115">오류의 표준 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 심각도 값입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-115">Is a standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] severity value for the error.</span></span> <span data-ttu-id="46cef-116">이 숫자는 0과 24 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-116">This number must be from 0 through 24.</span></span>  
  
 <span data-ttu-id="46cef-117">*상태*</span><span class="sxs-lookup"><span data-stu-id="46cef-117">*state*</span></span>  
 <span data-ttu-id="46cef-118">오류의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 상태 값입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-118">Is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] state value for the error.</span></span>  
  
 <span data-ttu-id="46cef-119">*oserrnum*</span><span class="sxs-lookup"><span data-stu-id="46cef-119">*oserrnum*</span></span>  
 <span data-ttu-id="46cef-120">운영 체제 오류 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-120">Is the operating-system error number.</span></span> <span data-ttu-id="46cef-121">이 인수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-121">This argument is ignored.</span></span>  
  
 <span data-ttu-id="46cef-122">*errtext*</span><span class="sxs-lookup"><span data-stu-id="46cef-122">*errtext*</span></span>  
 <span data-ttu-id="46cef-123">확장 저장 프로시저 오류 *errornum*에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-123">Is the description of the extended stored procedure error *errornum*.</span></span>  
  
 <span data-ttu-id="46cef-124">*errtextlen*</span><span class="sxs-lookup"><span data-stu-id="46cef-124">*errtextlen*</span></span>  
 <span data-ttu-id="46cef-125">확장 저장 프로시저 오류 문자열 *errtext*의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-125">Is the length of the extended stored procedure error string *errtext*.</span></span>  
  
 <span data-ttu-id="46cef-126">*oserrtext*</span><span class="sxs-lookup"><span data-stu-id="46cef-126">*oserrtext*</span></span>  
 <span data-ttu-id="46cef-127">운영 체제 오류 *oserrnum*에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-127">Is the description of the operating-system error *oserrnum*.</span></span> <span data-ttu-id="46cef-128">이 인수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-128">This argument is ignored.</span></span>  
  
 <span data-ttu-id="46cef-129">*oserrtextlen*</span><span class="sxs-lookup"><span data-stu-id="46cef-129">*oserrtextlen*</span></span>  
 <span data-ttu-id="46cef-130">운영 체제 오류 문자열 *oserrtext*의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-130">Is the length of the operating-system error string *oserrtext*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="46cef-131">반환</span><span class="sxs-lookup"><span data-stu-id="46cef-131">Returns</span></span>  
 <span data-ttu-id="46cef-132">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="46cef-132">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46cef-133">설명</span><span class="sxs-lookup"><span data-stu-id="46cef-133">Remarks</span></span>  
 <span data-ttu-id="46cef-134">**srv_message_handler** 함수를 사용하면 확장 저장 프로시저가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 중앙 집중식 오류 로깅 및 보고 기능과 통합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-134">The **srv_message_handler** function enables an extended stored procedure to integrate with the centralized error logging and reporting features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46cef-135">확장 저장 프로시저의 이벤트에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 경고를 설정할 수 있으며, SQL Server 에이전트가 이러한 경고 조건을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts can be established for events from extended stored procedures, and SQL Server Agent will monitor for these alert conditions.</span></span>  
  
 <span data-ttu-id="46cef-136">오류 메시지가 더 길면 412바이트로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-136">If the error message is longer, it is truncated to 412 bytes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46cef-137">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46cef-137">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="46cef-138">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="46cef-138">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
