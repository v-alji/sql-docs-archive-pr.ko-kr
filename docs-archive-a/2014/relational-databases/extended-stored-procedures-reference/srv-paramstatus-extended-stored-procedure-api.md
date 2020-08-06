---
title: srv_paramstatus(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: d89d4ccbb6a97ff47669ad4ed9c0b4c22ac934eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728240"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a><span data-ttu-id="4bbdf-102">srv_paramstatus(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="4bbdf-102">srv_paramstatus (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="4bbdf-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="4bbdf-104">특정 원격 저장 프로시저 호출 매개 변수의 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-104">Returns the status of a particular remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bbdf-105">구문</span><span class="sxs-lookup"><span data-stu-id="4bbdf-105">Syntax</span></span>  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4bbdf-106">인수</span><span class="sxs-lookup"><span data-stu-id="4bbdf-106">Arguments</span></span>  
 <span data-ttu-id="4bbdf-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="4bbdf-107">*srvproc*</span></span>  
 <span data-ttu-id="4bbdf-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="4bbdf-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="4bbdf-110">*n*</span><span class="sxs-lookup"><span data-stu-id="4bbdf-110">*n*</span></span>  
 <span data-ttu-id="4bbdf-111">매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="4bbdf-112">첫 번째 매개 변수의 번호는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-112">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="4bbdf-113">반환</span><span class="sxs-lookup"><span data-stu-id="4bbdf-113">Returns</span></span>  
 <span data-ttu-id="4bbdf-114">매개 변수의 상태 플래그가 들어 있는 `int`입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-114">An `int` that contains status flags for the parameter.</span></span> <span data-ttu-id="4bbdf-115">현재는 플래그가 하나만 있습니다. 비트 0을 1로 설정하면 매개 변수가 반환 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-115">Currently, there is only one flag: If bit 0 is set to 1, the parameter is a return parameter.</span></span> <span data-ttu-id="4bbdf-116">*n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 -1이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bbdf-117">설명</span><span class="sxs-lookup"><span data-stu-id="4bbdf-117">Remarks</span></span>  
 <span data-ttu-id="4bbdf-118">이 루틴은 원격 저장 프로시저 호출 매개 변수의 상태 플래그를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-118">This routine returns the status flags for a remote stored procedure call parameter.</span></span>  
  
 <span data-ttu-id="4bbdf-119">매개 변수에는 원격 저장 프로시저를 사용하여 클라이언트와 애플리케이션 간에 전달되는 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-119">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="4bbdf-120">클라이언트는 특정 매개 변수를 반환 매개 변수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-120">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="4bbdf-121">이러한 반환 매개 변수에는 애플리케이션이 다시 클라이언트에 전달하는 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-121">These return parameters can contain values that the application passes back to the client.</span></span>  
  
 <span data-ttu-id="4bbdf-122">현재 유일한 상태 플래그는 매개 변수가 반환 매개 변수인지 여부를 나타내는 상태 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-122">Currently, the only status flag is one that indicates whether the parameter is a return parameter.</span></span>  
  
 <span data-ttu-id="4bbdf-123">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="4bbdf-124">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="4bbdf-125">오류가 발생 하면 SRV_RPC 처리기가 계속 호출 되지만 매개 변수가 없는 것 처럼 표시 되 고 **srv_rpcparams** 0을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-125">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4bbdf-126">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="4bbdf-127">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4bbdf-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbdf-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4bbdf-128">See Also</span></span>  
 [<span data-ttu-id="4bbdf-129">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="4bbdf-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
