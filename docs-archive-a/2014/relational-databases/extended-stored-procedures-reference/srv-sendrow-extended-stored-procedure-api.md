---
title: srv_sendrow(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: df40348b8792a70f84719abfb42152fda9487e6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743232"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a><span data-ttu-id="a2b3e-102">srv_sendrow(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="a2b3e-102">srv_sendrow (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a2b3e-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="a2b3e-104">데이터 행을 클라이언트로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-104">Transmits a row of data to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b3e-105">구문</span><span class="sxs-lookup"><span data-stu-id="a2b3e-105">Syntax</span></span>  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2b3e-106">인수</span><span class="sxs-lookup"><span data-stu-id="a2b3e-106">Arguments</span></span>  
 <span data-ttu-id="a2b3e-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="a2b3e-107">*srvproc*</span></span>  
 <span data-ttu-id="a2b3e-108">특정 클라이언트 연결에 대한 핸들(이 경우 언어 요청을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="a2b3e-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a2b3e-110">반환</span><span class="sxs-lookup"><span data-stu-id="a2b3e-110">Returns</span></span>  
 <span data-ttu-id="a2b3e-111">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="a2b3e-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2b3e-112">설명</span><span class="sxs-lookup"><span data-stu-id="a2b3e-112">Remarks</span></span>  
 <span data-ttu-id="a2b3e-113">클라이언트로 보내는 각 행에 대해 한 번씩 **srv_sendrow** 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-113">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="a2b3e-114">**srv_sendmsg**, **srv_status**또는 **srv_senddone**을 사용하여 각각 메시지, 상태 값 또는 완료 상태를 보내기 전에 모든 행을 클라이언트로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-114">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, **srv_status**, or **srv_senddone**.</span></span>  
  
 <span data-ttu-id="a2b3e-115">**srv_describe** 를 사용하여 정의되지 않은 열이 포함된 행을 보내면 확장 저장 프로시저 API 애플리케이션에서 정보 오류 메시지를 발생시키고 클라이언트에 FAIL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-115">Sending a row that has not had all its columns defined with **srv_describe** causes the Extended Stored Procedure API application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="a2b3e-116">이 경우 행이 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-116">In this case, the row is not sent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2b3e-117">확장 저장 프로시저 API를 통해서는 컴퓨팅 행을 클라이언트로 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-117">The Extended Stored Procedure API does not support sending compute rows to the client.</span></span> <span data-ttu-id="a2b3e-118">또한 `ntext`, `text` 또는 `image` 데이터가 있는 행을 클라이언트로 보내는 경우 텍스트 포인터와 텍스트 타임스탬프는 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-118">Also, if a row containing `ntext`, `text`, or `image` data is sent to the client, the text pointer and text timestamp are not included.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2b3e-119">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="a2b3e-120">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2b3e-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b3e-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2b3e-121">See Also</span></span>  
 [<span data-ttu-id="a2b3e-122">srv_describe &#40;확장 저장 프로시저 API&#41;</span><span class="sxs-lookup"><span data-stu-id="a2b3e-122">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
