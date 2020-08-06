---
title: srv_rpcowner(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: f903870d0ee01256addb1557eb7e9123853b39e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743247"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a><span data-ttu-id="bcbd6-102">srv_rpcowner(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="bcbd6-102">srv_rpcowner (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="bcbd6-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="bcbd6-104">현재 원격 저장 프로시저에 대한 소유자 구성 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-104">Returns the owner component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcbd6-105">구문</span><span class="sxs-lookup"><span data-stu-id="bcbd6-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bcbd6-106">인수</span><span class="sxs-lookup"><span data-stu-id="bcbd6-106">Arguments</span></span>  
 <span data-ttu-id="bcbd6-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="bcbd6-107">*srvproc*</span></span>  
 <span data-ttu-id="bcbd6-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저를 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="bcbd6-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="bcbd6-110">*길이가*</span><span class="sxs-lookup"><span data-stu-id="bcbd6-110">*len*</span></span>  
 <span data-ttu-id="bcbd6-111">소유자 이름의 길이를 받는 정수 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-111">Is a pointer to an integer variable that receives the length of the owner name.</span></span> <span data-ttu-id="bcbd6-112">*len* 매개 변수는 NULL일 수 있으며, 이 경우 소유자 구성 요소의 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-112">The parameter *len* can be NULL, in which case the length of the owner component is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bcbd6-113">반환</span><span class="sxs-lookup"><span data-stu-id="bcbd6-113">Returns</span></span>  
 <span data-ttu-id="bcbd6-114">현재 원격 저장 프로시저의 Null로 끝나는 소유자 구성 요소에 대한 DBCHAR 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-114">A DBCHAR pointer to the null-terminated owner component for the current remote stored procedure.</span></span> <span data-ttu-id="bcbd6-115">현재 원격 저장 프로시저가 없으면 NULL이 반환되고 *len*이 -1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-115">If there is no current remote stored procedure, NULL is returned and *len* is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcbd6-116">설명</span><span class="sxs-lookup"><span data-stu-id="bcbd6-116">Remarks</span></span>  
 <span data-ttu-id="bcbd6-117">이 함수는 원격 저장 프로시저의 소유자 구성 요소만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-117">This function returns only the owner component of the remote stored procedure.</span></span> <span data-ttu-id="bcbd6-118">이름, 원격 저장 프로시저 이름 및 원격 저장 프로시저 번호에 대한 선택적 지정자는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-118">It does not include the optional specifiers for name, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bcbd6-119">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="bcbd6-120">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
