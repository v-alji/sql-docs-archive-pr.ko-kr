---
title: srv_paramname(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2227ac3d46efe7d09abc05964248229f3533d42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742124"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a><span data-ttu-id="605f2-102">srv_paramname(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="605f2-102">srv_paramname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="605f2-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="605f2-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="605f2-104">원격 저장 프로시저 호출 매개 변수의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-104">Returns the name of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605f2-105">구문</span><span class="sxs-lookup"><span data-stu-id="605f2-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="605f2-106">인수</span><span class="sxs-lookup"><span data-stu-id="605f2-106">Arguments</span></span>  
 <span data-ttu-id="605f2-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="605f2-107">*srvproc*</span></span>  
 <span data-ttu-id="605f2-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="605f2-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="605f2-110">*n*</span><span class="sxs-lookup"><span data-stu-id="605f2-110">*n*</span></span>  
 <span data-ttu-id="605f2-111">매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="605f2-112">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="605f2-113">*길이가*</span><span class="sxs-lookup"><span data-stu-id="605f2-113">*len*</span></span>  
 <span data-ttu-id="605f2-114">매개 변수 이름의 길이(바이트)를 포함하는 `int` 변수에 대한 포인터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-114">Provides a pointer to an `int` variable that contains the length, in bytes, of the parameter name.</span></span> <span data-ttu-id="605f2-115">*len*이 NULL이면 원격 저장 프로시저 매개 변수 이름의 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-115">If *len* is NULL, the length of the remote stored procedure parameter name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="605f2-116">반환</span><span class="sxs-lookup"><span data-stu-id="605f2-116">Returns</span></span>  
 <span data-ttu-id="605f2-117">매개 변수 이름을 포함하는 null로 끝나는 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-117">A pointer to a null-terminated character string that contains the parameter name.</span></span> <span data-ttu-id="605f2-118">매개 변수 이름의 길이는 *len*에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-118">The length of the parameter name is stored in *len*.</span></span> <span data-ttu-id="605f2-119">*n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 NULL을 반환하고 *len*이 -1로 설정되며 정보 오류 메시지가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-119">If there is no *n*th parameter or no remote stored procedure, it returns NULL, *len* is set to -1, and an informational error message is sent.</span></span> <span data-ttu-id="605f2-120">매개 변수 이름이 NULL이면 *len*이 0으로 설정되고 null로 끝나는 빈 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-120">If the parameter name is NULL, *len* is set to 0 and a null-terminated empty string is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="605f2-121">설명</span><span class="sxs-lookup"><span data-stu-id="605f2-121">Remarks</span></span>  
 <span data-ttu-id="605f2-122">이 함수는 원격 저장 프로시저 호출 매개 변수의 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-122">This function gets the name of a remote stored procedure call parameter.</span></span> <span data-ttu-id="605f2-123">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="605f2-124">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="605f2-125">이 경우에도 SRV_RPC 핸들러는 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams**는 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-125">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="605f2-126">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="605f2-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="605f2-127">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="605f2-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605f2-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="605f2-128">See Also</span></span>  
 [<span data-ttu-id="605f2-129">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="605f2-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
