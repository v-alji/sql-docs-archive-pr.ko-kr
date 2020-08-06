---
title: srv_rpcoptions(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: f5ebe4ab48721002e679ce149293b474a934e348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743248"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a><span data-ttu-id="4344e-102">srv_rpcoptions(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="4344e-102">srv_rpcoptions (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="4344e-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="4344e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="4344e-104">현재 원격 저장 프로시저에 대한 런타임 옵션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-104">Returns run-time options for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4344e-105">구문</span><span class="sxs-lookup"><span data-stu-id="4344e-105">Syntax</span></span>  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4344e-106">인수</span><span class="sxs-lookup"><span data-stu-id="4344e-106">Arguments</span></span>  
 <span data-ttu-id="4344e-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="4344e-107">*srvproc*</span></span>  
 <span data-ttu-id="4344e-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저를 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="4344e-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="4344e-110">반환</span><span class="sxs-lookup"><span data-stu-id="4344e-110">Returns</span></span>  
 <span data-ttu-id="4344e-111">현재 원격 저장 프로시저에 대한 논리 OR로 결합된 런타임 플래그가 들어 있는 비트맵.</span><span class="sxs-lookup"><span data-stu-id="4344e-111">A bitmap that contains the run-time flags joined in a logical OR for the current remote stored procedure.</span></span> <span data-ttu-id="4344e-112">현재 원격 저장 프로시저가 없으면 0이 반환되고 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-112">If there is not a current remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4344e-113">설명</span><span class="sxs-lookup"><span data-stu-id="4344e-113">Remarks</span></span>  
 <span data-ttu-id="4344e-114">다음 표에서는 각 런타임 플래그에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-114">The following table describes each run-time flag.</span></span>  
  
|<span data-ttu-id="4344e-115">런타임 플래그</span><span class="sxs-lookup"><span data-stu-id="4344e-115">Run-time flag</span></span>|<span data-ttu-id="4344e-116">설명</span><span class="sxs-lookup"><span data-stu-id="4344e-116">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4344e-117">SRV_NOMETADATA</span><span class="sxs-lookup"><span data-stu-id="4344e-117">SRV_NOMETADATA</span></span>|<span data-ttu-id="4344e-118">클라이언트가 메타데이터 정보를 사용하지 않고 결과를 요청했습니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-118">The client has requested results without metadata information.</span></span> <span data-ttu-id="4344e-119">이 플래그는 클라이언트가 인스턴스와 통신 하는 경우에만 사용 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4344e-119">This flag is only used when the client is communicating with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4344e-120">확장 저장 프로시저 API 애플리케이션은 메타데이터 정보를 생략할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-120">An Extended Stored Procedure API application cannot omit metadata information.</span></span>|  
|<span data-ttu-id="4344e-121">SRV_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="4344e-121">SRV_RECOMPILE</span></span>|<span data-ttu-id="4344e-122">클라이언트가 원격 저장 프로시저를 실행하기 전에 재컴파일하도록 요청했습니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-122">The client has requested to recompile the remote stored procedure before executing it.</span></span> <span data-ttu-id="4344e-123">이 플래그는 확장 저장 프로시저 API 애플리케이션에 적용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-123">This flag may not apply to an Extended Stored Procedure API application.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4344e-124">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4344e-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="4344e-125">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4344e-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
