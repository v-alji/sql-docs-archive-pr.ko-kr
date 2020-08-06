---
title: srv_rpcnumber(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: 25f30f8288125cf64d6b10a867d6af03c0f8ee91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742115"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a><span data-ttu-id="206cc-102">srv_rpcnumber(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="206cc-102">srv_rpcnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="206cc-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="206cc-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="206cc-104">현재 원격 저장 프로시저 호출에 대한 번호 구성 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-104">Returns the number component for the current remote stored procedure call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="206cc-105">구문</span><span class="sxs-lookup"><span data-stu-id="206cc-105">Syntax</span></span>  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="206cc-106">인수</span><span class="sxs-lookup"><span data-stu-id="206cc-106">Arguments</span></span>  
 <span data-ttu-id="206cc-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="206cc-107">*srvproc*</span></span>  
 <span data-ttu-id="206cc-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저를 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="206cc-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="206cc-110">반환</span><span class="sxs-lookup"><span data-stu-id="206cc-110">Returns</span></span>  
 <span data-ttu-id="206cc-111">현재 원격 저장 프로시저에 대한 번호 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-111">The number component for the current remote stored procedure.</span></span> <span data-ttu-id="206cc-112">클라이언트에서 원격 저장 프로시저를 실행할 때 번호 구성 요소를 사용하지 않거나 현재 원격 저장 프로시저가 없는 경우 -1이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-112">If the client does not use a number component when running the remote stored procedure or if there is no current remote stored procedure, it returns - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="206cc-113">설명</span><span class="sxs-lookup"><span data-stu-id="206cc-113">Remarks</span></span>  
 <span data-ttu-id="206cc-114">이 함수는 원격 저장 프로시저의 번호 구성 요소만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-114">This function returns only the number component of the remote stored procedure.</span></span> <span data-ttu-id="206cc-115">소유자, 원격 저장 프로시저 이름 및 데이터베이스 이름에 대한 선택적 지정자는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-115">It does not include the optional specifiers for owner, remote stored procedure name, and database name.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="206cc-116">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="206cc-116">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="206cc-117">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="206cc-117">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
