---
title: srv_rpcname(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
author: rothja
ms.author: jroth
ms.openlocfilehash: 21530b3e7b8aaa8c5a3f8770762cde7e258e3a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742116"
---
# <a name="srv_rpcname-extended-stored-procedure-api"></a><span data-ttu-id="76201-102">srv_rpcname(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="76201-102">srv_rpcname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="76201-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="76201-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="76201-104">현재 원격 저장 프로시저에 대한 프로시저 이름 구성 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76201-104">Returns the procedure name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76201-105">구문</span><span class="sxs-lookup"><span data-stu-id="76201-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="76201-106">인수</span><span class="sxs-lookup"><span data-stu-id="76201-106">Arguments</span></span>  
 <span data-ttu-id="76201-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="76201-107">*srvproc*</span></span>  
 <span data-ttu-id="76201-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저를 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="76201-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="76201-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76201-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="76201-110">*길이가*</span><span class="sxs-lookup"><span data-stu-id="76201-110">*len*</span></span>  
 <span data-ttu-id="76201-111">데이터베이스 이름의 길이를 받는 정수 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="76201-111">Is a pointer to an integer variable that receives the length of the database name.</span></span> <span data-ttu-id="76201-112">*len* 이 NULL이면 원격 저장 프로시저 이름의 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76201-112">If *len* is NULL, the length of the remote stored procedure name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="76201-113">반환</span><span class="sxs-lookup"><span data-stu-id="76201-113">Returns</span></span>  
 <span data-ttu-id="76201-114">현재 원격 저장 프로시저의 원격 저장 프로시저 이름 구성 요소의 null로 끝나는 문자열에 대한 DBCHAR 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="76201-114">A DBCHAR pointer to the null-terminated string for the remote stored procedure name component of the current remote stored procedure.</span></span> <span data-ttu-id="76201-115">현재 원격 저장 프로시저가 없으면 NULL이 반환되고 *len* 이 -1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="76201-115">If there is not a current remote stored procedure, NULL is returned and *len* is set to -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76201-116">설명</span><span class="sxs-lookup"><span data-stu-id="76201-116">Remarks</span></span>  
 <span data-ttu-id="76201-117">이 함수는 원격 저장 프로시저의 이름만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76201-117">This function returns only the name of the remote stored procedure.</span></span> <span data-ttu-id="76201-118">소유자, 데이터베이스 이름 및 원격 저장 프로시저 번호에 대한 선택적 지정자는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76201-118">It does not include the optional specifiers for owner, database name, and remote stored procedure number.</span></span>  
  
 <span data-ttu-id="76201-119">원격 저장 프로시저가 없는 경우에도 **srv_rpcname** 을 호출할 수 있으므로(정보 오류가 발생하지 않음) 이 함수를 사용하여 원격 저장 프로시저가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76201-119">Because it is valid to call **srv_rpcname** when there is not a remote stored procedure (no informational error occurs), this function provides a method for determining whether a remote stored procedure exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="76201-120">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76201-120">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="76201-121">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="76201-121">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
