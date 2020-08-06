---
title: srv_got_attention(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
ms.openlocfilehash: bb5432e2f5e259187e506237842fbb9110e27a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742140"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a><span data-ttu-id="0d3ed-102">srv_got_attention(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="0d3ed-102">srv_got_attention (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0d3ed-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="0d3ed-104">현재 연결 또는 태스크를 중단해야 하는지 확인하고 연결이 끊기거나 일괄 처리가 중단되면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-104">Checks whether the current connection or task needs to be aborted and returns TRUE if the connection is killed or the batch is aborted</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d3ed-105">구문</span><span class="sxs-lookup"><span data-stu-id="0d3ed-105">Syntax</span></span>  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d3ed-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0d3ed-106">Parameters</span></span>  
 <span data-ttu-id="0d3ed-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="0d3ed-107">*srvproc*</span></span>  
 <span data-ttu-id="0d3ed-108">데이터베이스 연결을 식별하는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-108">Pointer identifying a database connection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d3ed-109">Return Value</span><span class="sxs-lookup"><span data-stu-id="0d3ed-109">Return Value</span></span>  
 <span data-ttu-id="0d3ed-110">연결이 끊기거나 일괄 처리가 중단되면 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-110">TRUE if the connection is killed or the batch is aborted.</span></span> <span data-ttu-id="0d3ed-111">연결 또는 일괄 처리가 활성 상태이면 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-111">FALSE if the connection or batch is active.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d3ed-112">설명</span><span class="sxs-lookup"><span data-stu-id="0d3ed-112">Remarks</span></span>  
 <span data-ttu-id="0d3ed-113">장기 실행 확장 저장 프로시저는 연결이 끊기거나 일괄 처리가 중단될 경우 프로시저가 자동으로 종료될 수 있도록 주기적으로 **srv_got_attention**을 호출하여 서버 상태를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-113">A long-running extended stored procedure should check the server attention by calling **srv_got_attention** periodically so that the procedure may terminate itself when the connection is killed or the batch is aborted.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0d3ed-114">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-114">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="0d3ed-115">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d3ed-115">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
