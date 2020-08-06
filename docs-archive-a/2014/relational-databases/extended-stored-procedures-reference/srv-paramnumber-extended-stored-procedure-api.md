---
title: srv_paramnumber(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e621101c909ef251c40f38713e438d8e40d08a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653385"
---
# <a name="srv_paramnumber-extended-stored-procedure-api"></a><span data-ttu-id="f5329-102">srv_paramnumber(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="f5329-102">srv_paramnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="f5329-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f5329-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f5329-104">원격 저장 프로시저 호출 매개 변수의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-104">Returns the number of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5329-105">구문</span><span class="sxs-lookup"><span data-stu-id="f5329-105">Syntax</span></span>  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5329-106">인수</span><span class="sxs-lookup"><span data-stu-id="f5329-106">Arguments</span></span>  
 <span data-ttu-id="f5329-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="f5329-107">*srvproc*</span></span>  
 <span data-ttu-id="f5329-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="f5329-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f5329-110">*name*</span><span class="sxs-lookup"><span data-stu-id="f5329-110">*name*</span></span>  
 <span data-ttu-id="f5329-111">*name* 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-111">Is a pointer to the parameter *name*.</span></span>  
  
 <span data-ttu-id="f5329-112">*namelen*</span><span class="sxs-lookup"><span data-stu-id="f5329-112">*namelen*</span></span>  
 <span data-ttu-id="f5329-113">*name*의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-113">Is the length of *name*.</span></span> <span data-ttu-id="f5329-114">*name*이 Null로 끝나는 경우 *namelen*을 SRV_NULLTERM으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-114">If *name* is null-terminated, set *namelen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f5329-115">반환</span><span class="sxs-lookup"><span data-stu-id="f5329-115">Returns</span></span>  
 <span data-ttu-id="f5329-116">명명된 매개 변수의 매개 변수 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-116">The parameter number of the named parameter.</span></span> <span data-ttu-id="f5329-117">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-117">The first parameter is 1.</span></span> <span data-ttu-id="f5329-118">*name*으로 명명된 매개 변수가 없거나 원격 저장 프로시저가 없으면 0이 반환되고 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-118">If there is no parameter named *name* or no remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5329-119">설명</span><span class="sxs-lookup"><span data-stu-id="f5329-119">Remarks</span></span>  
 <span data-ttu-id="f5329-120">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-120">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="f5329-121">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-121">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="f5329-122">이 경우에도 SRV_RPC 핸들러는 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams**는 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-122">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f5329-123">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5329-123">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f5329-124">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f5329-124">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5329-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5329-125">See Also</span></span>  
 [<span data-ttu-id="f5329-126">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="f5329-126">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
