---
title: srv_rpcparams(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 443b9ea8a67341afdb92f0c384148c8b1b42f752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743240"
---
# <a name="srv_rpcparams-extended-stored-procedure-api"></a><span data-ttu-id="d6067-102">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="d6067-102">srv_rpcparams (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d6067-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d6067-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d6067-104">현재 원격 저장 프로시저의 매개 변수 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-104">Returns the number of parameters for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6067-105">구문</span><span class="sxs-lookup"><span data-stu-id="d6067-105">Syntax</span></span>  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6067-106">인수</span><span class="sxs-lookup"><span data-stu-id="d6067-106">Arguments</span></span>  
 <span data-ttu-id="d6067-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="d6067-107">*srvproc*</span></span>  
 <span data-ttu-id="d6067-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저를 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="d6067-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d6067-110">반환</span><span class="sxs-lookup"><span data-stu-id="d6067-110">Returns</span></span>  
 <span data-ttu-id="d6067-111">원격 저장 프로시저의 매개 변수 수.</span><span class="sxs-lookup"><span data-stu-id="d6067-111">The number of parameters in the remote stored procedure.</span></span> <span data-ttu-id="d6067-112">현재 원격 저장 프로시저가 없거나 원격 저장 프로시저에 매개 변수가 없으면 -1이 반환되고 알림 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-112">If there are no parameters in the remote stored procedure or if there is not a current remote stored procedure, -1 is returned and an information error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6067-113">설명</span><span class="sxs-lookup"><span data-stu-id="d6067-113">Remarks</span></span>  
 <span data-ttu-id="d6067-114">이 함수는 현재 원격 저장 프로시저의 매개 변수의 수를 반환하며</span><span class="sxs-lookup"><span data-stu-id="d6067-114">This function returns the number of parameters in the current remote stored procedure.</span></span> <span data-ttu-id="d6067-115">일반적으로 원격 저장 프로시저에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-115">It is usually called from the remote stored procedure.</span></span>  
  
 <span data-ttu-id="d6067-116">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-116">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="d6067-117">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-117">If the remote stored procedure call was made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="d6067-118">이 오류가 발생하면 원격 저장 프로시저 처리기가 호출되지만 이 처리기에 매개 변수가 전달되지 않고 **srv_rpcparams**가 0을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-118">When this error occurs, the remote stored procedure handler is called, but it does not receive the parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d6067-119">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6067-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d6067-120">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6067-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
